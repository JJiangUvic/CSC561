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


<br /><br />

### 2.Addition of experimental personnel and instructions

For the objectivity of the experiment, four college students with video game experience have been invited, each one of them with notable sensitivity to frame rates and image quality. They will fill out the following survey after viewing.
Ex. Response measures the video's loading speed. During the viewing, I will randomly skip to a particular segment, such as fast-forwarding.

###### Survey

1. Quality:__/10
2. FrameRate:__/10
3. Response:__/10

### Experiment Progress
#### HD Graphics 530



