---
title: java 中用到的jdbc 调用存储过程与hibernate 调用存储过程 
date: 2016-06-12 10:51:11
tags: java
---
## jdbc 中调用存储过程  
其实都是用是的Connection 来得到CallableStatement ,用CallableStatement的对像来查询，然后得到ResultSet 后面的就一样了，
那说一个要注意的问题吧，有的时候用java的jdbc 中调用存储过程与hibernate 调用存储过程，会遇到没有返回结果集的问题，其实只要在存储过程中 加上一句 
````set nocount on
````
这样就ok了，
下面是jdbc 调用存储过程 
 
```
import java.sql.CallableStatement;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;

/**
 * Created by Geek on 2016/6/15.
 */
public class JDBCTest {


        private String driverName = "com.microsoft.sqlserver.jdbc.SQLServerDriver";//加载驱动程序
        private String url = "jdbc:sqlserver://10.1.42.34:1433;DatabaseName=HS_BI";//设置数据库连接串
        private String user = "sa";//数据库登录用户名
        private String password = "Wonders2009";//数据库登录密码
        private static String message = "恭喜，数据库连接正常！";
        public void setDriverName(String newDriverName) {
            driverName = newDriverName;
        }
        public String getDriverName() {
            return driverName;
        }

        public void setUrl(String newUrl) {
            url = newUrl;
        }
        public String getUrl() {
            return url;
        }
        public void setUser(String newUser) {
            user = newUser;
        }
        public String getUser() {
            return user;
        }
        public void setPassword(String newPassword) {
            password = newPassword;
        }
        public String getPassword() {
            return password;
        }
        public Connection getConnection() {
            try {
                Class.forName(driverName);
                return DriverManager.getConnection(url, user, password);
            } catch (Exception e) {
                e.printStackTrace();
                message = "数据库连接失败！";
                return null;
            }
        }
        public static void main(String[] args) {
            try{
                JDBCTest dcm = new JDBCTest();
                Connection conn = dcm.getConnection();
                CallableStatement cs= conn.prepareCall("{call usp_showrecordtest}");
                cs.execute();
                ResultSet rs=cs.getResultSet();

                System.out.println(rs);
                System.out.println(message);
            }catch(Exception e){
                e.printStackTrace();
            }

    }
}

```
### 后续跟进hibernate来调用存储过程