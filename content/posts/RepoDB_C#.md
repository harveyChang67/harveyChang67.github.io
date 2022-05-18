---
title: "RepoDB_C#"
date: 2022-04-27T11:21:06Z
draft: false
---


RepoDB 在 Generic Repository Pattern 中很好用，
免去使用 Dapper 去自建 SQL 產生器，
但是有幾個限制 [RepoDB Limitations](https://github.com/mikependon/RepoDb/blob/master/RepoDb.Docs/limitations.md)，
其中一個令人訝異 -> Composite Keys。

## Composite Keys

RepoDB 只會處理 1 個 Primary Key....
這邊紀錄兩個相關的資訊

### Update + condition

```c#
termsList.Add(
    new QueryField('Id', Operation.Equal, '10095')
);
termsList.Add(
    new QueryField('Name', Operation.Equal, 'John')
);

ret = dbConn.Update(entity, new QueryGroup(termsList, Conjunction.And));
```

### Primary Properties

Model 中標註 Mapping，

```c#
    public class FMRMUSRT
    {
        [Primary] // Primary decoration
        public string Id { get; set; }
        [Primary] // Primary decoration
        public string item_cd { get; set; }
        public string? remark { get; set; }
    }
```

在 Repo. 中是可以抓取判斷：

```c#
    if (property.GetPrimaryAttribute() != null) // This property is primary
```
