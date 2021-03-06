## `MySQL`主从复制场景问题
* 基础
    * 主库开启`binlog`日志 
    * 主从`server-id`不同
    * 从库服务器能连通主库

* 过程 
    * 从库
        * 一个`I/O`线程，一个`SQL`线程 
        * `i/o`线程去请求主库 的`binlog`，并将得到的`binlog`日志写到`relay log`（中继日志） 文件中
        * `SQL` 线程，会读取`relay log`文件中的日志，并解析成具体操作，来实现主从的操作一致，而最终数据一致
    * 主库 
        * 主库会生成一个 `log dump` 线程，用来给从库` i/o`线程传`binlog` 


* 优化：
    * 半同步复制
    
        *  `log dump` 保证写到`relay log`日志以后的`ack`响应
    * 并行复制 
        * 增加`i/o`线程的数目

