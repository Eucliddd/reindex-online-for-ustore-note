## 参数
- `Oid relationOid
- `Oid relationPartOid`
- `List** rt_heapRelationIds`
- `List** rt_heapPartitionIds`
- `List** rt_indexIds`: 需要重建的索引列表（包括toast索引）
- `List** rt_indexPartIds`: 需要重建的partition索引列表
- `MemoryContext private_context`
## 打开关系
上`ShareUpdateExclusiveLock`锁
## 检查数据表是否可以被concurrent reindex
调用[[checkTableForReindexConcurrently]]判断
