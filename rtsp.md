- RTSP RTP RTCP TCP UDP 的关系概述  
  RTSP（Real-Time Streaming Protocol）、RTP（Real-time Transport Protocol）和RTCP（Real-Time Control Protocol）是一组用于实时音视频流传输的协议，它们通常一起使用以支持有效的流媒体通信。

  RTSP（Real-Time Streaming Protocol）: 
  
  RTSP是一个用于控制实时流媒体传输的应用层协议。它允许客户端控制流媒体的播放，暂停，停止，定位等操作。RTSP本身并不传输实际的音视频数据，而是负责建立和维护会话。

  RTP（Real-time Transport Protocol）:
  
  RTP是一个用于在网络上传输实时数据的协议。它负责将音视频数据分成小的数据包，并在网络上传输这些数据包。RTP提供时间戳和序列号等机制，以确保接收端可以按照正确的顺序和时间重组数据。

  RTCP（Real-Time Control Protocol）:
  
  RTCP是RTP的控制协议，用于监控和控制RTP会话。RTCP通过周期性地发送控制数据包，提供有关网络状况、媒体流的质量和参与者信息的反馈。RTCP也负责协商带宽的分配和流控制。

  关系概括：

  RTSP 主要用于建立和控制媒体会话，以及在需要时定位和调整流。RTP 用于传输实际的音视频数据，提供时间戳和序列号以保证正确的数据重组。RTCP 用于监控和控制RTP会话，提供反馈信息，帮助维护流的质量和性能。在一个典型的流媒体会话中，RTSP首先被用来建立会话和协商参数，然后RTP用于传输媒体数据，而RTCP用于监控和控制流的质量。这三个协议共同工作，使得实时音视频流能够在网络上传输和播放。

  RTSP通信是基于TCP的。RTP和RTCP视为数据包。数据包的传输可以通过TCP或者UDP。

- RTSP信令交互过程  
  推流：announce setup record
  
  拉流：setup play

- RTSP OVER TCP 的报文及通信细节    
  直接用信令链接通信。4字节分隔符 
  
  magic number：   RTP数据标识符，"$" 一个字节

  channel number： 信道数字 - 1个字节，用来指示信道
  
  data length ：   数据长度 - 2个字节，用来指示插入数据长度

- RTSP OVER UDP 的报文及通信细节    
   需要确定发送端和接收端的端口，所以一共有2对端口。RTP是偶数  RTCP是奇数
   数据从发送端口发送到接收端口。  端口对应端口。
   和一般的UDP不同，一般的UDP发送端口没有指定。

- RTSP MULTICAST 的报文及通信细节    
  同UDP 只不过有在sdp中指定组播IP 和 端口

- RTSP 鉴权  
  一般在option就鉴权了。   BASIC 和 DIGIST

- RTCP 概述   
  质量监控： RTCP用于监控实时传输的质量。通过定期发送RTCP包，参与者可以了解会话的网络状况、数据包丢失率、延迟等信息。这有助于识别潜在的问题，并采取措施来改善传输质量。

  带宽管理： RTCP可以提供关于当前网络带宽的信息。这有助于调整实时通信的传输速率，以适应网络条件的变化，以及确保适当的带宽使用。

  参与者识别： RTCP包含有关参与实时通信的各方（例如，会话中的用户）的信息。这对于识别并管理参与者的存在和状态非常有用。

  会话控制： RTCP还可以用于一些会话控制功能，例如指示参与者加入或离开会话，或者提供一些其他与会话相关的信息。

  网络适应性： 借助RTCP，系统可以动态调整实时通信的参数，以适应网络的变化。这包括调整编码器参数、重新路由数据流等。

  总体而言，RTCP通过提供实时通信的有关统计信息和控制信息，帮助确保高质量的实时通信体验。
- RFC   
  RFC 2326 - "Real Time Streaming Protocol (RTSP)"
这是RTSP的基本规范，定义了RTSP协议的基本特征、消息格式、状态码等。

  RFC 2327 - "SDP: Session Description Protocol"
SDP（Session Description Protocol）是用于描述多媒体会话的协议，它与RTSP一起使用，描述了会话中的媒体流信息。

  RFC 7826 - "Real-Time Streaming Protocol 2.0 (RTSP 2.0)"
这个RFC更新了RFC 2326，引入了RTSP的版本2.0，增加了一些新特性和改进。

  RFC 4566 - "SDP: Session Description Protocol"
这个RFC更新了RFC 2327，对SDP进行了一些修订和扩展。

  RFC 4145 - "TCP-Based Media Transport in the Session Description Protocol (SDP)"
该文档描述了SDP中TCP传输的一些特性，这对于RTSP的TCP传输是相关的。