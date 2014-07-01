#c#课时03
##MVC4（MVC模式）
###创建MVC4工程
1. 文件-模板-Visual C#-Web-ASP.NET MVC4 Web 应用程序-Internet应用程序(模板引擎"Razor")

###创建Controller
		
		using System;
		using System.Collections.Generic;
		using System.Linq;
		using System.Web;
		using System.Web.Mvc;

		namespace MvcApplication1.Controllers
		{
    		public class HomeController : Controller
    		{
        		public ActionResult Index()
        		{
            		ViewBag.Message = "修改此模板以快速启动你的 ASP.NET MVC 应用程序。";

           			return View();
        		}

        		public ActionResult About()
        		{
            		ViewBag.Message = "你的应用程序说明页。";

            		return View();
        		}

        		public ActionResult Contact()
        		{
            		ViewBag.Message = "你的联系方式页。";

            		return View();
        		}
    		}
		}

	访问：

	- http://localhost:30626/
	- http://localhost:30626/Home
	- http://localhost:30626/Home/About

###创建View
1. html+css+js
2. Razor语法

		@{string productName = "台灯";} //c#代码
    	<span>@productName</span>
		<span>@model.name</span>
    	<span>@DateTime.Now.ToString("yyyy-MM-hh")</span>

3. 使用Model中的数据

		@model Models.HomeModel //cshtml文件开始
		......
		<span>@model.name</span> //使用

###创建Model
1. 创建属性

		public属性可以在View中访问
2. 其他方法

		访问数据库等逻

###Links

1. mvc4 

	[http://www.asp.net/mvc/tutorials/mvc-4/getting-started-with-aspnet-mvc4/intro-to-aspnet-mvc-4](http://www.asp.net/mvc/tutorials/mvc-4/getting-started-with-aspnet-mvc4/intro-to-aspnet-mvc-4)

##Unity.Mvc4(三层架构)
###目录结构
	BLL //逻辑
	Common //工具类
	DAL //数据库逻辑
	Lib //第三方库
	Model //数据库对应Model，与数据库字段映射
	Web 
		-Controllers //Controller
		-Models //View上使用的Model
		-Views //页面
###重要文件说明
	WEB
		-Web.config //配置数据库
		-Bootstrapper.cs //配置DAL，BLL，注入
	Common
		-OperateMessage.cs //公共跳转页面
	DAL
		-DBHelper
			-DBHeloerSqlServer.cs //数据库操作方法
###创建页面流程
1. 在对应文件夹创建Controller
2. 创建页面View
3. 创建View上使用的Model
4. 在BLL下创建IXXXBLL接口，XXXBLL实现
5. 在DAL下创建IXXXDAL接口，XXXDLL实现，XXXDLL中操作数据库
6. 在Bootstrapper.cs中配置对应关系

