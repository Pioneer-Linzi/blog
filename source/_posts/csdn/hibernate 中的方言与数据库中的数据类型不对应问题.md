---
title: hibernate 中的方言与数据库中的数据类型不对应问题
date: 2016-06-12 10:51:11
tags: java
---
有时候会遇到 hibernate  no mapping Dialect type -9 之类的，这个就是方言与数据库中的数据类型不对应问题 ，那先说一下解决思路
## 解决思路
－ 换方言
－数据库中表类型换了
－继承hibernate 中的方言，重写hibernate 的数据类型对应关系
在第一个方法不可以的情况下，第二个显然是最好的解决方法!
```
import org.hibernate.dialect.SQLServerDialect;

/**
 * 自定义方言的类，用于解决hibernate中方言与数据库不类型不对的问题
 */

public class SqlServer2008Dialect extends SQLServerDialect {

    public SqlServer2008Dialect() {
        super();
        registerHibernateType(1, "string");
        registerHibernateType(-9, "string");
        registerHibernateType(-16, "string");
        registerHibernateType(3, "double");
    }
}
```
最后在改写一下hibernate 中方言类的配置就可以了!
