# Pager的特性
1.页一般情况下不可复写。

2.页面内容被写进回滚日志，要匹配回滚日志被写入时和事务开始时，数据库中的内容。

3.被写入数据库的文件为页面大小的整数倍，并且在页边界上对齐。

4.从数据库中读取的文件要再页边界上对齐，并且为页面大小的整数倍，或者取于数据库文件的前100个字节。

5.所有写入数据库文件的内容，需要同步到回滚日志被删除，截短，归零之前。

6.如果一个主日志被使用，所有写进数据库文件的内容需要同步到主日志文件被删除之前。

7.在每个事务开始和结束的时候，数据库文件都格式必须正确。

8.当向数据库里写入文件时，需要在数据库文件上加独占锁。

9.当从数据库里读取文件时，需要在数据库上加共享锁。两个数据库逻辑上等效是指两个数据对所有查询给出的答案是相同的。
