## 数据库连接
* 左连接
    * 以左边的表为基准，左边有`n`行数据
    
    * 至少会有`n`行记录，可以为`NULL`，具体数目需要右表中是否对单条记录存在重复记录
    
    * http://www.cnblogs.com/eflylab/archive/2007/06/25/794278.html
* 右连接
* 全连接
    * 回字段`ID` 同时存在于两个表的记录
* 内连接
    * 会将字段`ID` 同时存在于两个表的记录展出
* 自连接
    * 自身表的一个镜像当作另一个表来对待
* 实现原理
    * 嵌套循环连接
    * 通过**驱动表**的结果集，作为**循环基础数据**，然后逐条通过该结果集中的数据作为过滤条件到下一个表中查询数据，然后合并结果    
    * 索引嵌套联系由于被驱动表上有**索引**，所以比较的时候不再需要**逐条进行比较**，而可以通过拿**两个表关联字段**的索引来进行比较，从而加速查询
    * 使用**小表**做为驱动
    * 没有索引的时候使用`BLJ`算法
        * 增加了一个`JOIN BUFFER`的过程 
        * 将多次比较合并

