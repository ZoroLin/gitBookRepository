# something about my first work #  

- entryTime:  
  
**projectLog:**  
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
```  
