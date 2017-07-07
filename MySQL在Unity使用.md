# Uniyt3D-
## MySQL在Unity中的使用
### 第一步
打开Unity ————> 点击File————>点击 Build Settings ————> 选择Splash Image ————>选择 Api Compatibility Level 中的.NET 2.0

![](http://i4.piimg.com/1949/27fdc0134157c3b1.png)

### 第二步

将mysql.data.dll插件放到Unity中，创建一个文件夹Plugins，将插件放到文件夹中

### 第三步
创建脚本，挂载到摄像机上，然后进行脚本编辑

```c#
using UnityEngine;
using System.Collections;
using MySql.Data;
using MySql.Data.MySqlClient;

public class MySQLOpen : MonoBehaviour {

	  //所连接数据库的服务器IP
    public string ServerIP = "localhost";
    //数据库名称
    public string dataName = "dong";
    //用户名
    public string UserID = "root";
    //密码
    public string Password = "djf123456";

    MySqlConnection mySqlconnection;

    //连接数据库的字符串
    string connetionStr = "";

    //执行的命令
    string select = "Select* From user;";

    string insert = "Insert into user values(1007,'军',21);";

    string dele = "Delete from user where ID = 1007;";

    string update = "Update user set ID = 1005 where ID = 1007;";
	void Start () {
        
        connetionStr = string.Format("Server = {0}; Database = {1};User ID = {2}; Password = {3}", ServerIP, dataName, UserID, Password);
        //打开数据库
        mySqlconnection = new MySqlConnection(connetionStr);
        if(mySqlconnection != null)
        {
            mySqlconnection.Open();
        }
        //Insert(insert);
        Update1(update);
        Select(select);
        
	}
	
	void Insert(string insert)
    {
        //向User表中插入内容
        MySqlCommand command = new MySqlCommand(insert, mySqlconnection);

        int hasRows = command.ExecuteNonQuery();    //修改函数调用ExecuteNonQuery方法

        print(hasRows);    //打印作用了几行；
    }
    
    void Delete(string delete)
    {
        //删除表中的列
        MySqlCommand command2 = new MySqlCommand(dele, mySqlconnection);
        int delRows = command2.ExecuteNonQuery();
    }

    void Select(string select)
    {
        //MySQL命令查询内容
        MySqlCommand command1 = new MySqlCommand(select, mySqlconnection);

        MySqlDataReader reader = command1.ExecuteReader();   // //反馈信息调用ExecuteReader

        if (reader.HasRows)  //判断是否还有行数
        {
            while (reader.Read())   //是否正在读取内容
            {
                string dataStr = "";
                dataStr += reader["ID"] + ",";
                print(dataStr);
            }
        }
    }
     
    void Update1(string update)
    {
        MySqlCommand command = new MySqlCommand(update, mySqlconnection);
        int delrows = command.ExecuteNonQuery();
    }
}

```
