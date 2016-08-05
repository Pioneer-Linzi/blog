---
title: hibernate 调用存储过程
date: 2016-06-12 10:51:11
tags: java
---

## 思路
1. 可以用hibernate 里面的CreateSqlQuery 来执行，这个比较明显，其实就是跟jdbc调用是一样的
2. 可以用hibernate 里面的session.doWork()方法来执行，那个估计不常用吧， 
## 具体实现
1.用createSqlQuery 来查询
```
String sql="{call 存储过程名(?,?)}"
SQLQuery query = session.createSQLQuery(sql);
```
? 问号中是要传的参数，跟jdbc调用存储过程一样的jdbc 可以参看我的另一个博文
2.用session.doWork();来执行，这个我想的比较复杂，看看你们用什么方法，
这个没有现成的代码了，我就说一下思路，
session.doWork();里面要传一个参数是Work 这个类的实例
那Work 是一个抽像类，这里我先写一个内部类，实现了Work 类，再重写execute()方法，再定义sql 跟ResultSet,这里还是贴上简单的代码吧
```
	public class DoWork implements Work {

		private String sql;
		private ResultSet rs;

		public String getSql() {
			return sql;
		}

		public void setSql(String sql) {
			this.sql = sql;
		}

		public ResultSet getRs() {
			return rs;
		}

		public void setRs(ResultSet rs) {
			this.rs = rs;
		}

		@Override
		public void execute(Connection connection) throws SQLException {
				CallableStatement cs=connection.prepareCall(sql);
				cs.execute();
				this.setRs(cs.getResultSet());
		}
	}
```

这样，在session.doWork()前定义Dowork对像，再SetSql 
再Session.doWork(doWork)之后，再doWork.getRs()来获取结果集，
如果要传入参数 ，那就写一个数组吧，这个不再研究!
