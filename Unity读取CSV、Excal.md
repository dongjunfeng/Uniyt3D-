# Uniyt3D-

## 使用Unity读取CSV文件

### 1.建个空的项目

![](http://images.cnitblog.com/blog2015/506960/201505/110955218927902.png)

### 2.建议text.csv的文件录入数据

![](http://images.cnitblog.com/blog2015/506960/201505/111203366732336.png)

录入数据：

![](http://images.cnitblog.com/blog2015/506960/201505/111432045327369.png)

### 3.读取csv文件

#### 方法一：将CSV文件强制转换为txt格式，在Unity中使用TextAsset直接读取文本信息。

```c#
using UnityEngine;
using System.Collections;
using System.IO;

public class read : MonoBehaviour
{
    public TextAsset txtCSV;
    public GUIText guitext;
    void Start()
    {
        guitext.text = txtCSV.text;
        print(txtCSV.text);

    }
}
```
运行结果：

![](http://images.cnitblog.com/blog2015/506960/201505/111529400957941.png)

#### 方法二

```c#
using UnityEngine;
using System.Collections;
using System.IO;

public class read : MonoBehaviour
{public GUIText guitext;
    void Start()
    {
        readCSV();
    }
    /// <summary>
    /// 读取CSV文件
    /// </summary>
    void readCSV()
    {
        //读取csv二进制文件
        TextAsset binAsset = Resources.Load("csv", typeof(TextAsset)) as TextAsset;
        //显示在GUITexture中
        guitext.text = binAsset.text;

        string[] data = binAsset.text.Split("|"[0]);
        foreach (var dat in data)
        {
            Debug.Log(dat);
        }

        ////读取每一行的内容
        string[] lineArray = binAsset.text.Split("\r"[0]);
        ////按‘|’进行拆分
        string[] lineArray1 = binAsset.text.Split("|"[0]);

        //创建二维数组
        string[][] Array = new string[lineArray.Length][];

        //把csv中的数据储存在二位数组中
        for (int i = 0; i < lineArray.Length; i++)
        {
            Array[i] = lineArray[i].Split("\r"[0]);
            Debug.Log(Array[i][0].ToString());

        }
    }
}
```

运行结果：

![](http://images.cnitblog.com/blog2015/506960/201505/111550159236422.png)

## Unity读取Excel

注意Excel文档的后缀名为.xslx格式的
需要的三个插件：

![](http://images.cnitblog.com/blog2015/506960/201505/111614482827642.png)

代码如下：
```c#
using UnityEngine;
using System.Collections;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Text.RegularExpressions;
using System.IO;
using Excel;
using System.Data;
using UnityEngine.UI;

public class NewBehaviourScript : MonoBehaviour 
{
    public Text readData;
    void Start () 
    {        
        XLSX();
    }
    
    void XLSX()
    {
        FileStream stream = File.Open(Application.dataPath + "/UserLevel.xlsx", FileMode.Open, FileAccess.Read);//打开Excel文档
        IExcelDataReader excelReader = ExcelReaderFactory.CreateOpenXmlReader(stream);
    
        DataSet result = excelReader.AsDataSet();         //作为数据集进行存储
    
        int columns = result.Tables[0].Columns.Count;   //取得数据集中第一张表格的列的数目
        int rows = result.Tables[0].Rows.Count;         //取得数据集中第一张表格的行的数目
        
        
        for(int i = 0;  i< rows; i++)      //遍历
        {
            for (int j = 0; j < columns; j++)
            {
                string nvalue = result.Tables[0].Rows[i][j].ToString();    //直接对行列操作:
                Debug.Log(nvalue);
                if (i > 0)
                {
                    readData.text += "\t\t" + nvalue;
                }
                else
                {
                    readData.text +="   \t" + nvalue;                    
                }
            }
            readData.text += "\n";
        }    
    }
}

运行结果：

![](http://images.cnitblog.com/blog2015/506960/201505/111613104851986.jpg)

三个插件的下载地址：
百度网盘：http://pan.baidu.com/s/1kTGIGS3












