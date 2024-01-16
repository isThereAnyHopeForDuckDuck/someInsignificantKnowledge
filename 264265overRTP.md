- RTP 头    
  需要关注的4个参数：  负载类型PT 时间戳TS 源SSRC 序列号SEQ
  
- 打包方式就3种：单个 分片 聚合 
  
  单个：RTP HDR + NALU

  分片：RTP HDR + FU HDR(包含NALU HDR + 当前片的位置) + NALU DATA

  聚合：RTP HDR + STAP HDR + SIZE + NALU