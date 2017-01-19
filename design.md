# Require
* 灰度测试（流量控制）  
    根据请求（header, cookie, ip ...）信息控制该请求后续访问资源(upstream)  
    <b>关键点：</b> 线上请求无感知、性能损耗越小越好  
    
* 蓝绿上线（动态上线）  
    线上机器分两组，上线时借组两个组的概念可以保证线上服务不停机  
    <b>关键点：</b> 动态 upstream、流量在两组内自动切换  
    
# Design
  针对HTTP请求，从入口开始改造，So 也就是Nginx 改造。   
  
  针对 nginx 的改造有两种途径：    
  | \方法  | 直接改动 nginx 源码 | Openresty 加 Lua 代码 |    
  | ------------- | ------------- | ------------- |   
  | 优点  | 想干啥就干啥  | Nginx 没修改，可以平滑升级 |   
  | 缺点  | 定制了，难以升级  | 依赖 Openresty， 不少功能受限，还得增加 Nginx module |   
  
  
# Sample