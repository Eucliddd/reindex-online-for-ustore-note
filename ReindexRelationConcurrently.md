## 参数
- `Oid relationOid`
- `Oid relationPartOid`: partition OID，如果valid，则只reindex该partition；否则需要reindex所有partition的索引。
- `AdaptMem* memInfo`
- `bool dbWide`
## 创建memory context
## Phase 1
### 根据`relationOid`判断表的类型
- 如果关系是表、数据视图、TOAST值，调用[[prepareReindexTableConcurrently]]，将关系的所有索引、partition索引、toast加入到待重建索引链表`indexIds`和`indexPartIds`中。
- 如果关系是索引，调用[[prepareReindexIndexConcurrently]]，将索引加入`indexIds`，partition索引加入`indexPartIds`中。
- 如果关系是全局索引或是其它类型，报错。
