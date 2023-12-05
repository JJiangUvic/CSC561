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

