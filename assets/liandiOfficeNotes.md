# something about my first work #  

- entryTime:  
  
**projectLog:**  
1. tgy(特高压中心精益化管控平台)    

	*from 2016-07-25 to 2016-10-09*  
	> tgy移动端：org.apache.cordova + jQueryMobile + sqlite  
	> tgy服务端：Spring + SpringMVC + Hibernate
	> tgy网页端：jsp + easyUI + HighCharts + plupload(文件上传插件) + portal(拖拽插件) + json2(json转换插件) + 其他控件插件
```
src\main\java\cn.com.xxx.xxx\web(moblie)\common
				      	      \dao	持久层(存储层),对数据库操作
								@Repository(value="userDao")        对应数据访问层Bean,方便Spring创建实例
				              \entity
				              \service  业务层,对DAO查询结果操作
								@Service("userService")	            对应的是业务层Bean,方便spring实例化(控制反转/依赖注入,Action原来主动创建类,现在等待spring创建后注入)
								@Resource(name = "userDao")         spring实例化后注入Service,可直接使用private BaseDao<User> userDao;(1.与@Autowired区别)
				              \vo
				              \web	表现层(展示层),即Action
								@Controller 			    对应表现层的Bean，也就是Action(可设value,默认为类名,首字母小写)
								@Scope("prototype")		    保证每一个请求有一个单独的Action来处理(默认为"singleton"),scope定义一个Bean的作用范围(2.可有的值)
								@RequestMapping(value="/user")	    可以声明在类和方法上(可加上 params = { "modify=false" }, method =POST;return 页面名)
								@Resource(name = "userService")     spring实例化后注入Action,避免UserService userService = new UserServiceImpl();只需private UserService userService;
src\main\resources\application.properties   数据库连接属性配置文件(由spring配置文件指定  <context:property-placeholder location="classpath:application.properties" />)
		  \ehcache-local.xml        缓存的配置文件(由spring配置文件配置)
		  \applicationContext.xml   spring的配置文件(由web.xml配置),扫描包中注解<context:component-scan base-package="cn.com.liandisys">
		  \log4j.properties         日志配置文件(由web.xml配置)
		  \...
src\main\webapp\javascript
	       \static
	       \WEB-INF\tags
		       \views		    jsp页面文件夹(和springMVC中配置的地址一致 <property name="prefix" value="/WEB-INF/views/"/> )
		       \spring-mvc.xml      springMVC的配置文件(由web.xml配置)
		       \web.xml
		       \...
pom.xml
...
----------------------------------------------------------------------------------------------
其他注解:
@Autowired					根据bean 类型从spring 上线文中进行查找，注册类型必须唯一，否则报异常.(1.与@Resource区别)
@Cacheable(cacheName="userCache")		缓存数据
@TriggersRemove(cacheName="userCache",removeAll=true) 清除缓存
@Transactional(readOnly = false)		事务管理器,可以标注在类和方法上,可在spring配置文件中配置
@RequestBody 					将HTTP请求正文转换为适合的HttpMessageConverter对象
@ResponseBody					将内容或对象作为 HTTP 响应正文返回,并调用适合HttpMessageConverter的Adapter转换对象，写入输出流
@ModelAttribute("doctypesEntity")               作用域：request
@Query
@PathVariable
1.@Autowired与@Resource区别:http://bbs.51cto.com/thread-1136892-1.html
2.@Scope中可以指定如下值：
       singleton:定义bean的范围为每个spring容器一个实例（默认值）
       prototype:定义bean可以被多次实例化（使用一次就创建一次）
       request:定义bean的范围是http请求（springMVC中有效）
       session:定义bean的范围是http会话（springMVC中有效）
       global-session:定义bean的范围是全局http会话（portlet中有效）

---------------------------------------------------------------------------------------------
存储过程:procedure
	执行存储过程：CALL productpricing(@pricelow,@pricehigh,@priceaverage);
		      SELECT @pricelow,@pricehigh,@priceaverage;
	创建存储过程：CREATE PROCEDURE productpricing()
		      BEGIN
			SELECT AVG(prod_price) AS priceaverage FROM products;
		      END
	删除存储过程：DROP PROCEDURE productpricting; /DROP PROCEDURE IF EXISTS
	

触发器：只有DELETE、INSERT、UPDATE支持触发器(只有表支持)，每个表每个事件只有一个触发器
	创建触发器：CREATE TRIGGER 触发器名 AFTER INSERT ON 表名 FOR EACH ROW SELECT...
	删除触发器: DROP TRIGGER 触发器名(不能更新或覆盖，只能删了重建)
	INSERT触发器中，NEW虚拟表访问被插入的行
	DELETE触发器中，OLD的虚拟表访问被删除的行 
	  Oracle中，:NEW :OLD 来访问更新前后的数据

---------------------------------------------------------------------------------------------
更多工具-开发者工具-iphone6
http://www.duanliang920.com/learn/web/html5/304.html
viewport标签:
	<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" />
	width  ----  viewport的宽度（width=device-width意思是：宽度等于设备宽度）
	height ------  viewport的高度（height=device-height意思是：高度等于设备宽度）
	initial-scale ----- 初始的缩放比例
	minimum-scale ----- 允许用户缩放到的最小比例
	maximum-scale ----- 允许用户缩放到的最大比例
	user-scalable ----- 用户是否可以手动缩放
```  
2. ()    

	*from  to*  
	>   
	> 
	> 
```

```
