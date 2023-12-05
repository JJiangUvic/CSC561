# Analysis of Streaming Protocols in YouTube Video Transmission Performance and Quality Assessment

Nowadays, online video streaming has become a fundamental application of multimedia systems, and its
quality and experience depend on two key factors: decoding capability and network environment. These
factors are crucial in terms of loading speed, frame quality, and effective utilization of bandwidth. On the other
hand, for modern computers, the GPUs provide major video decoding capabilities. Therefore, this project aims
to provide a comprehensive assessment of the network environment and GPU decoding capability applicable
to YouTube video transmission.


This study relies on both controlled experiments and real-world testing to offer a comprehensive analysis.
Analyzing objective performance data paints a comprehensive picture of how the network environment and
GPU decoding capability influence streaming quality and the user experience.

## INTRODUCTION
In the modern era of digital communication, online video content revolutionizes the way we access
and consume multimedia. Platforms like YouTube emerge as ubiquitous sources of information,
entertainment, and education, seamlessly delivering video content to a global audience. However,
the seamless and high-quality experience that users enjoy is not a mere coincidence but the result
of a complex interplay of technology, infrastructure, and protocols.

On another front, the physical network infrastructure bears the responsibility of carrying and
transporting these protocols. A multitude of servers and backbone networks transmit video data to
end-users with the assistance of transmission protocols. Given that network devices operate in
the real world, packet loss, latency, and limited bandwidth are inevitable. These circumstances can
significantly impact both the transmission process and the quality of the video.

Additionally, the process of translating transmission protocols and compressed data into signals
perceptible by human senses is a significant undertaking. In this context, video decoding holds
particular importance, especially in terms of decoding speed and quality. For modern computers,
the GPU takes the most of the workload. It’s noteworthy that, with the rapid advancement of
technology, both the performance and prices of GPUs have significantly increased. This situation
has led to the continued use of some older devices that have not been phased out. The question
arises as to whether these GPUs can keep pace with the progress in modern video technology,
specifically concerning aspects such as playing 4K or higher resolution videos.

In conclusion, the video experience for end-users is significantly influenced by both the network
environment and GPU performance. Therefore, the objective of this project is to conduct a comprehensive evaluation of YouTube video streaming performance and quality by analyzing various
factors that impact the viewing experience. This research is crucial due to the increasing reliance
on online video content and the need for optimized video streaming technologies. The factors to be
investigated include:

• Network environment parameters (latency and packet loss)
• Live or Stored Video
• GPU performance
• Video quality(4K-8K)

While various studies are exploring aspects of video streaming performance, there is limited
research that combines GPU decoding, network parameters, video quality, and codec analysis
within a controlled virtual environment. Previous efforts often focus on isolated factors or lack
comprehensive assessments.

The approach involves setting up a simplified hardware environment to manipulate and monitor
selected variables, including GPU decoding performance: assembling the environment with different
GPU models. Standardized video streams are utilized to assess GPU decoding efficiency. Monitoring
tools measure GPU utilization, decoding speed, and potential bottlenecks. The evaluation also
utilizes tools similar to the tc (Traffic Control) tools for network parameter control. The final step 
involves storing videos and live streaming, divided into different control groups. Each control group is shown to four participants who watch for 10 minutes and then fill out a pre-prepared survey.
Finally, all survey responses are analyzed and evaluated.

## BACKGROUND
While YouTube, being one of the globe’s foremost video-sharing platforms, has been at the forefront
of enhancing the viewer experience through the judicious selection of appropriate streaming
protocols. In a bid to meet the diverse needs of its vast user base, YouTube has conducted extensive
experimentation with an array of protocols and adaptive streaming mechanisms. This endeavor
aims to ensure that video playback remains seamless and uninterrupted. Nonetheless, the choice of
the most suitable protocol is contingent on a multitude of factors, including prevailing network
conditions, the capabilities of the viewer’s device, and individual user preferences. Consequently,
YouTube’s approach to protocol selection is a dynamic and adaptive one, attuned to the ever-shifting
landscape of online video streaming.

## YouTube Transmission

YouTube employs a progressive download method for video transmission, allowing users to stream
content seamlessly. When a user initiates playback, the video file is delivered in small chunks,
with the first segment downloading immediately. Simultaneously, subsequent portions are fetched
in the background, ensuring a continuous stream while minimizing buffering interruptions. This
adaptive streaming technique adjusts the quality of the video based on the viewer’s internet speed,
guaranteeing a smoother experience. Additionally, YouTube employs various codecs to compress
and optimize video files for efficient transmission[9]

## Network Protocols
In the realm of online video websites like YouTube, the backbone of seamless streaming experiences
lies in specific network protocols. At the forefront is HTTP (Hypertext Transfer Protocol), which
facilitates the transfer of video content over the web. YouTube leverages HTTP-based protocols such
as HTTP Live Streaming (HLS) or Dynamic Adaptive Streaming over HTTP (DASH) to efficiently
deliver videos. These protocols enable YouTube to dynamically adjust the video quality based on the viewer’s internet speed, ensuring uninterrupted playback and a smoother streaming experience.
Additionally, HTTPS (Hypertext Transfer Protocol Secure) plays a pivotal role in securing the
transmission of video content, encrypting data exchanged between users and YouTube servers to
enhance overall security during video streaming.

In the context of live streaming on platforms like YouTube, Real-Time Control Protocol (RTCP)
and Real-Time Transport Protocol (RTP) come into play. RTCP provides valuable feedback on
the quality of the streaming session, aiding in the optimization of the viewer’s experience. This
combination of protocols not only ensures the efficient delivery of on-demand video content but
also contributes to the real-time adaptability required for live-streaming scenarios. For a deeper
understanding of the intricacies involved, one can explore technical documentation provided by
YouTube or delve into resources related to streaming protocols and online video delivery systems.

## RELATED WORK
### Low Latency Live Video Streaming over HTTP 2.0
In HTTP streaming, clients experienced latency due to the segment duration, making it unsuitable
for low-latency live streaming. Reducing segment duration, while a solution, led to increased HTTP
requests and inefficient cache usage. To address this, the study introduced a low-latency live video
streaming technique with HTTP 2.0. It actively streamed live video from the web server to the client
as soon as video segments were available. The approach was implemented in an MPEG-DASH
prototype. Experimental results showed improved live latency and addressed the request explosion
issue while reducing segment duration[8].

### Towards Optimal Low-Latency Live Video Streaming
The study presented an exploration of the low-latency live-streaming design space by developing
dynamic models and optimal adaptation strategies. These strategies aimed to establish upper
bounds on Quality of Experience (QoE) as a function of allowable end-to-end latency. To achieve
this, practical live streaming algorithms were developed within the frameworks of iterative Linear
Quadratic Regulator (iLQR)-based Model Predictive Control and Deep Reinforcement Learning[5].

### Content delivery networks: status and trends
Content Delivery Networks (CDNs) significantly enhanced network performance and application
reliability by strategically distributing content to cache servers located near users. The rapid growth
of the internet elevated the importance of speed, accuracy, and availability of web-delivered content.
Proxy servers played a crucial role in quick content delivery by providing shared cache locations
for multiple clients. CDNs acted as trusted overlay networks, efficiently delivering common web
objects, static data, and multimedia content by distributing the content load among servers close to
users. This approach reduced the origin server load, minimized latency for end users, and enhanced
overall throughput[1].

### Analysis of YouTube DASH Traffic
Efficient resource allocation algorithms, crucial for meeting users’ quality of service requirements,
relied on accurate knowledge or estimation of traffic characteristics. With video streams constituting
70% of internet traffic and on a continual rise, understanding the properties of these streams was
essential. This paper presented findings from a study on the characteristics of the most popular
videos on YouTube, a major contributor to video traffic. The study explored the impact of the
Dynamic Adaptive Streaming over HTTP (DASH) technology used by platforms like YouTube and
Netflix[4].

## RESEARCH STRATEGY
### Experimental Design:
Describe the experimental design, including protocol choices, network environment conditions
control, methods for measuring performance metrics, and the experiment schedule.

### Data Analysis:
Analyze the collected data using statistical methods to compare the performance of different
protocols and assess the significance of the results.

### Conclusion and Recommendations:
Summarize the main findings of the research, conclude the performance of different protocols, and
offer practical optimization recommendations.

### Real-life Testing and Survey:
Implementing experiments in real-world scenarios entails inviting participants to actively engage
and collect their feedback. Crafting tailored survey questionnaires serves the purpose of quantifying
user experiences effectively. The testing will involve separate evaluations for both live and stored
videos.

## RESEARCH METHOD
### Network Performance Testing
Experimental Environment Setup: Simulate network conditions, by setting up a Linux-based router
that allows the TC (Traffic Control) to configure a low bandwidth, high latency, and network
congestion, for the environment set up. Performance Metrics: Measure the latency, and stability of
each protocol under different network conditions. This can be achieved using network analysis
tools such as Wireshark or other performance testing tools[2].

1. Packet Loss Threshold. Packet loss can significantly impact the quality of video streaming.
In this phase of the research, we aim to determine the lowest acceptable packet loss rate that still
maintains a satisfactory user experience. The experimental setup will involve introducing varying
levels of packet loss while measuring the impact on video playback, buffering, and overall stability

2. Latency Threshold. Low latency is crucial for real-time interactions and a seamless streaming
experience. This investigation aims to identify the lowest acceptable latency levels for different
streaming protocols under diverse network conditions.

3. Bandwidth Threshold. The bandwidth threshold effect in online video refers to the critical
point at which available internet bandwidth significantly impacts the quality of streaming. Below
this threshold, users may experience issues such as buffering, reduced resolution, and interruptions.

### Live and Stored Videos

Live video streams events in real-time with immediate engagement, while stored video offers
on-demand access to pre-recorded content. Live video is dynamic, fostering a sense of community,
while stored video provides flexibility for users to watch at their own pace. Together, they enrich
the digital content landscape, serving diverse preferences and use cases.

## EXPERIMENTAL ENVIRONMENT ARCHITECTURE
![Layout](https://github.com/JJiangUvic/CSC561/assets/49337962/3b7959ce-ec76-4d35-aac0-12e8feb2e771)
