# Crawler
网络爬虫
网络爬虫定义:一端抓取数据的程序
  爬虫分为两部分:
     发送请求,(抓取数据,)
     解析页面(页面解析)
     
应用场景:     
     搜索引擎(用户-->全文检索    后台原始文档-->爬虫)
        例:360导航 爬360  获得360HTML-->解析页面-->根据a标签-->获取页面的链接网址-->放进队列-->获取页面HTML-->解析页面
     大数据分析(爬取数据-->大数据分析)
     SEO优化(和爬虫没有卵关系)
        基于搜索引擎,进行标题密度等技术,争取排名,
     采集感兴趣的数据:
        财经,
        图片,
        视频,
        商品,
爬虫的实现:
  发送请求,
    使用工具包 HttpClient
      httpClient(客户端)
        可以模仿浏览器 发送请求,接收请求,
         get请求
          (maven jar工程-->导入依赖-->测试类-->)
          创建一个HttpCLIENT对象,CloseHttpClient对象使用HttpClients工具类进行创建(打开了浏览器)
          创建GET/POST请求 含url参数,(如果带参数,直接?跟在连接后)
            new HttpGet(url)
          使用httpclient对象发送请求(点击页面超链接)
          接收服务端响应,html(页面响应)
            获取响应头,状态行,状态码
          打印html(展示页面)
          关资源(结束)
          
          
          
         post
         创建HttpClient对象
         创建Post对象
         创建HTTPentity对象封装成表单,
         使用httpclient对象发送请求(点击页面超链接)
         接收服务端响应,html(页面响应)
           获取响应头,状态行,状态码
         打印html(展示页面)
         关资源(结束)
        
      httpCore(服务端)
      
     连接池
     创建client对象时创建,
  jsuop(一般不实用jsoup获取页面,client更专业,jsoup擅长解析,所以client抓页面,jsoup解析)
    直接使用jsoup工具类.静态方法,parse(可以解析url 本地HTML html字符串)
    得到decument对象
    使用document对象提供的方法解析Html页面
      getElementById/ByTag
      根据css选择器提取
     document的API 
      getElementById/ByTag通过ID  /标签 获取 
      .text获取标签内的文本
     也可以使用CSS选择器
      select方法
      selector组合
        el#id
       
      
      
        
  解析页面
    使用工具包Jsoup(可以像使用Jquery一样解析)
    功能分析
    
    
 案例解析
  爬取京东商品
  创建工程(springBoot)
  添加j
  
  
爬虫第二天  
WebMagic 框架,国产框架,参考python的
dawnlader下载数据  封装成page  发给PageProcesser   解析页面地址 发送给Scheduler队列
1.Downloader
Downloader负责从互联网上下载页面，以便后续处理。WebMagic默认使用了Apache HttpClient作为下载工具。

2.PageProcessor
PageProcessor负责解析页面，抽取有用信息，以及发现新的链接。WebMagic使用Jsoup作为HTML解析工具，并基于其开发了解析XPath的工具Xsoup。

在这四个组件中，PageProcessor对于每个站点每个页面都不一样，是需要使用者定制的部分。

3.Scheduler
Scheduler负责管理待抓取的URL，以及一些去重的工作。WebMagic默认提供了JDK的内存队列来管理URL，并用集合来进行去重。也支持使用Redis进行分布式管理。

除非项目有一些特殊的分布式需求，否则无需自己定制Scheduler。

4.Pipeline
Pipeline负责抽取结果的处理，包括计算、持久化到文件、数据库等。WebMagic默认提供了“输出到控制台”和“保存到文件”两种结果处理方案。

Pipeline定义了结果保存的方式，如果你要保存到指定数据库，则需要编写对应的Pipeline。对于一类需求一般只需编写一个Pipeline。



WebMagic入门程序
  工程搭建 
  引入依赖
  创建PageProcessor组件,实现PageProcessor接口(自己定义配置请求参数,站点编码格式,超时时间,抓取的间隔事件)
     Pipeline默认向控制台输出,如需持久化自己定义Pipeline
  在PageProcessor组ujianzhong实现页面解析
  启动爬虫
  
  

  
 
    
    
      
