#c#课时01
##c#与java对比
###创建：
	文件-新建-项目-VisualC#-控制台应用程序。
###结构:
C#:

	using System;
	namespace HelloWorld
	{
    	class Hello 
    	{
        	static void Main() 
        	{
            	Console.WriteLine("Hello World!");
            	Console.WriteLine("Press any key to exit.");
            	Console.ReadKey();
        	}
    	}
	}

JAVA:

	import java.io.*;
	package cn.easycomm.test;
	public class HelloWorld{ 
		public static void main(String[] args) {  
  			System.out.println("Hello World!"); 
  		}
	}

1. `namespace`与`package`
2. `using`与`import` 

> 注：using有另一种用法

3. `Main`与`main`

###数据类型：

1. C# 提供 Java 中可用的所有数据类型，并增加了对无符号数字和新的 	128 位高精度浮点类型的支持。
2. Java 的 `boolean` 在 C# 中称为 `bool`
3. 常量，Java 使用 `final` 字段修饰符声明此类变量，而 C# 则使用 	`const` 关键字
		
		const int NUM = 1; //c#
		public static final int NUM = 1; //java
4. 字符串，Java用`equals`,C#可以直接用`==`或`!=`
5. 转义字符，都使用 `\` ，C#中字符串开始前使用 `@` 声明字符串则不需转义字符

###运算符

1. C# 提供 Java 支持的所有适用的运算符
2. C# 中可用但 Java 中没有的一些新运算符（`checked`,`unchecked`...）

###流控制

1. 在 Java 和 C# 这两种语言中，`if` `else` 完全相同
2. switch,C# 要求在每个 `case` 的末尾都使用 `break`, `case` 	中可以使用字符串变量
3. 在 C# 和 Java 中，`for` 循环的语法和操作相同
4. C#中引入了`foreach` ,Java中使用的是`for`
	
	C#

		static void Main()
		{
    		string[] arr= new string[] {"Jan", "Feb", "Mar"};

    		foreach (string s in arr)
    		{
        		System.Console.WriteLine(s);
    		}
		}
	Java

		for (String x : list) { 
             System.out.println(x); 
         } 
5. `while` 和 `do...while` 语句的语法和操作是相同的

###参数传递
1. 在 Java 和 C# 中，引用对象的方法参数始终都是通过引用传递的，而基元数据类型参数（C# 中的值类型）是通过值传递的。
2. 在 C# 中，若要通过引用传递值类型，需要指定关键字 `ref` 或  `out`
 
	ref

		class TestRef
		{
    		private static void Add(int i, ref int result)
    		{
        	result += i;
        	return;
    		}

    		static void Main()
    		{
        		int total = 20;
        		System.Console.WriteLine("Original value of 'total': {0}", total);

        		Add(10, ref total);
        		System.Console.WriteLine("Value after calling Add(): {0}", total);
    		}
		}

		Original value of 'total': 20
		Value after calling Add(): 30
	out

		class TestOut
		{
    		private static void Add(int i, int j, out int result)
    		{
        	// The following line would cause a compile error:
        	// System.Console.WriteLine("Initial value inside method: {0}", result);

        	result = i + j;
        	return;
    	}

    		static void Main()
    		{
        		int total = 20;
        		System.Console.WriteLine("Original value of 'total': {0}", total);

        		Add(33, 77, out total);
       			System.Console.WriteLine("Value after calling Add(): {0}", total);
    		}
		}

		Original value of 'total': 20
		Value after calling Add(): 110

###属性
1. `get` ，`set`方法

		public class Animal
		{
			public string Age { get; set; }
    		private string name;

    		public string Species
    		{
       			get
        		{
           			return name;
        		}
        		set
        		{
            		name = value;
        		}
    		}
		}
2. 访问属性

		animal.Species = "Lion";                   // set accessor
        System.Console.WriteLine(animal.Species);  // get accessor

###数组
	
1. 定义初始化

		int[] arr2Lines; 
		//int arr2[];  //compile error
		arr2Lines = new int[5] {1, 2, 3, 4, 5};
		int[] arr1Line = {1, 2, 3, 4, 5};

###继承与接口

1. 在 C# 中，继承及接口实现均由 : 运算符定义，此运算符与 Java 中的 extends 和 implements 等效 
2. base与super，访问基类

###异常

1. C# 中的异常处理与 Java 中的异常处理非常相似
2. Exception 为所有异常类的基类

		try
		{
    		// code to open and read a file
		}
		catch (System.IO.FileNotFoundException e)
		{
    		// handle the file not found exception first
		}
		catch (System.IO.IOException e)
		{
    		// handle any other IO exceptions second
		}
		catch
		{
    		// a catch block without a parameter
    		// handle all other exceptions last
		}
		finally
		{
    		// this is executed whether or not an exception occurs
    		// use to release any external resources
		}

###C#高级技术

1. 属性（类似Java中的批注）

		[System.Serializable()] //可以被序列化
		public class Employee  
		{
    		public int ID;
    		public string Name;        
    		[System.NonSerialized()] public int Salary; 
		}

2. 事件与委托(把方法当成类型，传递方法)
3. LINQ查询表达式
4. Lambda表达式


##2、c#常用操作

###常用集合
1. ArrayList
	
	[http://msdn.microsoft.com/zh-cn/library/vstudio/system.collections.arraylist_methods(v=vs.90).aspx](http://msdn.microsoft.com/zh-cn/library/vstudio/system.collections.arraylist_methods(v=vs.90).aspx "http://msdn.microsoft.com/zh-cn/library/vstudio/system.collections.arraylist_methods(v=vs.90).aspx")
2. Hashtable
 
	[http://msdn.microsoft.com/zh-cn/library/vstudio/system.collections.hashtable(v=vs.100).aspx](http://msdn.microsoft.com/zh-cn/library/vstudio/system.collections.hashtable(v=vs.100).aspx "http://msdn.microsoft.com/zh-cn/library/vstudio/system.collections.hashtable(v=vs.100).aspx")
3. Dictionary
	
	[http://msdn.microsoft.com/zh-cn/library/vstudio/ms132468(v=vs.90).aspx](http://msdn.microsoft.com/zh-cn/library/vstudio/ms132468(v=vs.90).aspx "http://msdn.microsoft.com/zh-cn/library/vstudio/ms132468(v=vs.90).aspx")
###文件操作
1. 文件读写

		class TestFileIO
		{
		    static void Main() 
		    {
		        string fileName = "test.txt";  // a sample file name
		
		        // Delete the file if it exists.
		        if (System.IO.File.Exists(fileName))
		        {
		            System.IO.File.Delete(fileName);
		        }
		
		        // Create the file.
		        using (System.IO.FileStream fs = System.IO.File.Create(fileName, 1024)) 
		        {
		            // Add some information to the file.
		            byte[] info = new System.Text.UTF8Encoding(true).GetBytes("This is some text in the file.");
		            fs.Write(info, 0, info.Length);
		        }
		
		        // Open the file and read it back.
		        using (System.IO.StreamReader sr = System.IO.File.OpenText(fileName)) 
		        {
		            string s = "";
		            while ((s = sr.ReadLine()) != null) 
		            {
		                System.Console.WriteLine(s);
		            }
		        }
		    }
		}
###数据库

1. 连接数据库


		using System;
		using System.Data;
		using System.Data.SqlClient;
		
		class Program
		{
		    static void Main()
		    {
		        string connectionString = "Data Source=(local);Initial Catalog=Northwind;"
		            + "Integrated Security=SSPI";
		        string queryString = 
		            "SELECT CategoryID, CategoryName FROM dbo.Categories;";
		        using (SqlConnection connection = 
		                   new SqlConnection(connectionString))
		        {
		            SqlCommand command = connection.CreateCommand();
		            command.CommandText = queryString;
		
		            try
		            {
		                connection.Open();
		
		                SqlDataReader reader = command.ExecuteReader();
		
		                while (reader.Read())
		                {
		                    Console.WriteLine("\t{0}\t{1}",
		                        reader[0], reader[1]);
		                }
		                reader.Close();
		            }
		            catch (Exception ex)
		            {
		                Console.WriteLine(ex.Message);
		            }
		        }
		    }
		}
###Links
1. C#(针对Java开放人员)
 
	[http://msdn.microsoft.com/zh-cn/library/ms228358(v=vs.90).aspx](http://msdn.microsoft.com/zh-cn/library/ms228358(v=vs.90).aspx)
2. C#编程指南

	[http://msdn.microsoft.com/zh-cn/library/67ef8sbd.aspx](http://msdn.microsoft.com/zh-cn/library/67ef8sbd.aspx)

