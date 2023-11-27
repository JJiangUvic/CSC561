# YouTube Video Streaming Performance and Quality Assessment
The objective of this project is to conduct a comprehensive evaluation of YouTube video streaming performance and quality by analyzing various factors that impact the viewing experience. This research is crucial due to the increasing reliance on online video content and the need for optimized video streaming technologies. The factors to be investigated include:

•	GPU decoding performance

•	Network environment parameters (latency and packet loss)

•	Video quality(4K-8K)

•	Impact of modern video codecs (AV1 and VP9)

While various studies have explored aspects of video streaming performance, there is limited research that combines GPU decoding, network parameters, video quality, and codec analysis within a controlled virtual environment. Previous efforts have often focused on isolated factors or lacked comprehensive assessments.

The approach will involve setting up a simplified hardware environment to manipulate and monitor the selected variables, including GPU decoding performance: Assembly of the environment to with different GPU models. A set of standardized video streams will be utilized to assess GPU decoding efficiency. Monitoring tools will be employed to measure GPU utilization, decoding speed, and any potential bottlenecks. On the other hand, the evaluation also utilizes tools similar to the tc (Traffic Control) tools for network parameter control and configure YouTube settings to use AV1 and VP9 codecs. The project focuses on a rapid but rigorous analysis of these factors. 

Expected Deliverables and Timeline

Week 1: Project setup, virtual machine configuration, and network parameter control

Week 2: GPU decoding performance assessment and preliminary video quality analysis

Week 3: Final video quality assessment, codec analysis, and report preparation

Week 4: Reports

This project aims to provide initial insights into YouTube video streaming performance and quality within a tight three-week timeline. While the scope is limited, the rapid assessment will yield valuable data on GPU decoding, network parameters, and codec impact. The results will contribute to our understanding of these critical factors in online video streaming.

References:

[1]: https://www.youtube.com
[Youtube](https://www.youtube.com)


*****

**Update[Oct.20 2023]**

In the process of implementing the plan, modify the plan by replacing virtual machines with temporarily assembled computers. To better control the network, use a software router separately to run Linux Traffic Control.

1. Set up three test equipments:

```
  |  CPU    |   RAM  |          GPU           | SSD |
  | 6700k   |   8G   | Intel® HD Graphics 530 | 1T  |
  | 6700k   |   8G   | GeForce GT 1030        | 1T  |
  | 6700k   |   8G   | GeForce GTX 750 Ti     | 1T  |
  | 6700k   |   8G   | GeForce GTX 3090       | 1T  |
```

2.Traffic Control Manual

```
tc qdisc add dev eth1 root netem delay 100ms ## add 100ms delay
tc qdisc add dev eth1 root netem loss 25% ## add 25% packet loss
```

TCP (Transmission Control Protocol) is capable of retransmitting lost packets to ensure data integrity. When a packet is lost, TCP initiates a retransmission to recover the missing data, thereby maintaining the continuity of the data stream. However, this recovery process does introduce some slowdown in the network. Even though TCP can recover lost packets, the time it takes to retransmit them can make the network feel slower.

Additionally, TCP responds to packet loss by reducing its throughput and introducing extra delays. This reduction in throughput and the added delay persist as long as the current data transfer rate does not meet the sending rate of the data flow. In other words, TCP adapts its transmission speed to account for network congestion or packet loss, which can lead to a temporary decrease in performance and responsiveness until the network stabilizes.

 If a packet is lost, TCP can retransmit it. The second transmission picks up lost packets and reconstructs the data stream. However, this does not mean there is no slowdown involved. The network may feel slower, as it still takes time to retransmit data. On the other hand, After a packet drop, TCP reduces its throughput and introduces additional delay for as long as the throughput it provides does not satisfy the sending rate of the flow.

 Considering real-world usage scenarios, experiments will be conducted with packet loss rates of 25%, 50%, and 70%, as well as latency values of 100ms, 300ms, and 500ms. Each test will be repeated three times, lasting for 5 minutes, and the results will be averaged. Each experiment will record smoothness, GPU, and CPU frequencies.

 *****

**Update[Nov.11 2023]**


## Index for the project update.
- [The specific details for setting up the experimental platform]()
  - [Experimental environment architecture]()
  - [Addition of experimental personnel and instructions]()
- [Experiment Progress]()
  - [HD Graphics 530]()
- [Improving and Some Plans]()
- [Problems and Some Solutions]()


### The specific details for setting up the experimental platform
#### 1. Experimental environment architecture
![Layout](https://github.com/JJiangUvic/CSC561/assets/49337962/3b7959ce-ec76-4d35-aac0-12e8feb2e771)
#### Hardware Explain:
•	***Master Router***: The router is used to connect the local network to the local area network provider Shaw. It is responsible for signal modulation and provides services such as DHCP and packet transport for devices operating at layer 2.

•	***Control PC***: The PC running in a Windows 10 environment is used for receiving signals from a capture card and sending commands to the PC router in the experimental platform. The commands include configuring and modifying Linux router settings, as well as adjusting latency and packet loss rates.

• ***Client Monitor***: Providing video output for the participants in the experiment.

•	***Capture card***: Used to replicate video signals and provide data to the software installed on the Control PC.

•	***PC Router***: A PC running in an Ubuntu environment, installed with an SSH server for remote login and control by the Control PC to achieve the experiment's objectives. It also installed TC (Traffic Control) for configuring network latency and packet loss rates. One of the physical network ports of this PC is directly point-to-point connected to a physical network port on the Control PC, with manual configuration to ensure communication for SSH login. Another port of this PC is connected to the Master Router, which provides IP and internet services through DHCP. Meanwhile, TC is used to adjust parameters like latency and packet loss on this port. Finally, the last port is connected to the Experiment PC to provide port forwarding for it.

•	***Experiment PC***: A PC running in a Windows 10 environment is used to test various graphics cards, primarily through YouTube browsing. Additionally, this PC will provide video output to a monitor to provide data to the experimenters.

<br />

### 2.Addition of experimental personnel and instructions

For the objectivity of the experiment, four college students with video game experience have been invited, each one of them with notable sensitivity to frame rates and image quality. They will fill out the following survey after viewing.
Ex. Response measures the video's loading speed. During the viewing, I will randomly skip to a particular segment, such as fast-forwarding.

###### Survey

1. Quality:__/9
2. FrameRate:__/9
3. Response:__/9

<br /><br />
### Experiment Progress
#### HD Graphics 530
The experiment is expected to last approximately two hours, including a 20-minute break. The experiment steps are as follows:  

Step 1: Remotely log in to the PC Router through the Control PC using SSH and set the TC parameters. Command (cmd):
```
tc qdisc change dev eth1 root netem delay 0ms loss 0%
```
In the real experiment, data from the experimental table will be used for configuration.  

Step 2: Perform ping tests to ensure that the correct latency and packet loss conditions are in place at that time

Step 3: Four participants watch YouTube videos, each lasting 5 minutes, and then response tests (randomly jumping to different times in the video)

Step 4: Filled out the Survey, and calculate the average score  

Data table
| Package Loss | Delay | Quality Ave Rating | FrameRate Ave Rating | Response Ave Rating | 
| :----: | :----: | :----: | :----: | :----: |
| 0% | 0 | 7 | 4 | 8 | 
| 0% | 100 | 7 | 4 | 8 |  
| 0% | 200 | 7 | 3 | 6 | 
| 0% | 500 | 6 | 2 | 1 | 
| 5% | 0 | 7 | 5 | 7 | 
| 5% | 100 | 7 | 4 | 8 |  
| 5% | 200 | 6 | 4 | 6 | 
| 5% | 500 | 6 | 2 | 2 | 
| 10% | 0 | 6 | 4 | 8 | 
| 10% | 100 | 6 | 4 | 6 |  
| 10% | 200 | 7 | 3 | 6 | 
| 10% | 500 | 6 | 1 | 2 | 
| 20% | 0 | 7 | 4 | 5 | 
| 20% | 100 | 6 | 4 | 8 |  
| 20% | 200 | 7 | 3 | 6 | 
| 20% | 500 | 6 | 1 | 1 | 

Some Analysis:  
1. During the ping test, some interesting observations were made. When setting the ping test to 50 packets, packet loss, and latency would occasionally overlap. For instance, when setting a 5% packet loss rate and a 100ms latency, there were instances where the packet loss rate exceeded 5% and approached 10%. This phenomenon only occurred when sending 50 packets. However, when increasing the test packet count to 1000, this issue did not occur again.

2. It seems that playing 4K videos doesn't impose a significant load on the GPU. Interestingly, while playing videos, there doesn't appear the work load on the decoding aspect. On the other hand, there is some load on the 3D aspect, but it's not particularly high.

3. Latency and packet loss don't seem to have a significant impact on the video quality but do affect the frame rate. A 120fps video might feel less smooth than a 30fps one, which requires further testing to confirm if it's related to GPU performance. However, it is indeed associated with latency and packet loss rates.

4. Latency significantly affects loading speed, especially when loading video for the first time. It also affects the speed of skipping. On the other hand, packet loss has a much smaller impact on the video, possibly because the transmission protocol has some special mechanisms at the application layer.

5. These tests are based on stored videos, not live streams. It's expected that in a live-streaming scenario, latency and packet loss would have a more significant impact.


<br /><br />
### Improving and Some Plans

1. Surprisingly, based on the current results, it appears that GPU performance is not the primary influencing factor. Perhaps there is a need to adjust the testing approach, such as reducing the number of GPU comparison groups and increasing the comparison groups for stored and live videos.

2. An investigation into the relationship between 3D and video playback is needed.

3. Improving the experimental equipment, if possible, by upgrading to high-resolution displays and using better cables.

4. Increasing the analysis of the network component.

<br /><br />
### Problems and Some Solutions

1. In the initial attempt, I tried to meet all the requirements on the Experiential PC but failed to control the network environment variables, primarily due to a lack of experience in setting port parameters on Windows. To fix this issue, I made the above changes, as shown in the previous image: I separated the router and the client into two devices. The reason for this improvement is that Windows is better suited for experimenting with YouTube, while Linux is more suitable for operating TC. With the redesigned setup, I can SSH into the router for control.(solved)

2. In the initial setup, I attempted to record the screen while playing YouTube to facilitate data recording. However, the screen recording software had an impact on the experimental results. The solution was to use a capture card: After implementing the capture card, screen recording is done on another PC and doesn't affect the experiment (resolved).

3. Bitrates and physical monitors have different rules; for example, playing a 1080P video on a 1080P monitor is different from playing a 4K video on a 1080P monitor. Further research is needed.

4. So far, it is considered that the monitor may have an impact on the experimental results (issue not resolved).

5. In the previous updates, I mentioned a new direction for the experiment and will be modifying the proposal after taking advice into consideration.

 *****

**Update[Nov.20 2023]**
### More Experiments 
For some improvements to the experiment: we reduced certain unreasonable experimental groups to make the experiment more reasonable.
Data table(GT 1030)
| Package Loss | Delay | Quality Ave Rating | FrameRate Ave Rating | Response Ave Rating | 
| :----: | :----: | :----: | :----: | :----: |
| 0% | 0 | 7 | 7 | 9 | 
| 0% | 200 | 8 | 6 | 6 | 
| 5% | 0 | 8 | 5 | 9 | 
| 5% | 200 | 8 | 6 | 6 | 
| 10% | 0 | 8 | 6 | 8 | 
| 10% | 200 | 8 | 5 | 6 | 


Data table(GTX 750 Ti)
| Package Loss | Delay | Quality Ave Rating | FrameRate Ave Rating | Response Ave Rating | 
| :----: | :----: | :----: | :----: | :----: |
| 0% | 0 | 8 | 8 | 9 | 
| 0% | 200 | 8 | 3 | 6 | 
| 5% | 0 | 8 | 5 | 8 | 
| 5% | 200 | 8 | 5 | 7 | 
| 10% | 0 | 8 | 5 | 8 | 
| 10% | 200 | 7 | 5 | 6 | 

#### Next step plan
The supplementary experiment: testing increased bandwidth for different experimental groups, with 10MB and 100MB.


#### Some Thoughts
1. The monitor may have some impact. Try changing the monitor to gather more data.
2. YouTube's algorithm is already very effective, and in the vast majority of cases, bandwidth is not a significant consideration (more experiments will be conducted in this regard in the next steps). Latency and packet loss have minimal impact on the storage type of videos. In some cases, it may only affect the frame rate. Research will be conducted in this area.
3. Small-scale experiments will be conducted with live-streaming videos, focusing specifically on testing with the 750 Ti. Emphasis will be on bandwidth, latency, and packet loss.

Data table(GTX 750 Ti) Extended with bandwidth
| Package Loss | Delay | Bandwidth | Quality Ave Rating | FrameRate Ave Rating | Response Ave Rating | 
| :----: | :----: | :----: | :----: | :----: | :----: |
| 0% | 0 | 8 | 8 | 9 | 
| 0% | 200 | 8 | 3 | 6 | 
| 5% | 0 | 8 | 5 | 8 | 
| 5% | 200 | 8 | 5 | 7 | 
| 10% | 0 | 8 | 5 | 8 | 
| 10% | 200 | 7 | 5 | 6 | 
