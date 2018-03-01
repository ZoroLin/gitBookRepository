# something about my first work #  

- entryTime:  
  
**projectLog:**  
1. tgy(特高压中心精益化管控平台)    

	*from 2016-07-25 to 2016-10-09*  
	> tgy移动端：org.apache.cordova + jQueryMobile + sqlite  
	> tgy服务端：Spring + SpringMVC + Hibernate + Oracle + Maven + Jetty
	> tgy网页端：jsp + easyUI + HighCharts + plupload(文件上传插件) + portal(拖拽插件) + json2(json转换插件) + 其他控件插件  
	> 实习期，负责页面样式调整、移动端全部的开发学习，最后好像为采用。
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
2. hdyn(区域公司综合业务管理系统)    

	*from 2016-12-01 to 2017-10-20; after后期维护*  
	> hdnx服务端 Struts2 + Spring + jdbc + db2 + Websphere(server)  
	> hdnx网页端 jsp + ExtJs + HighCharts + runqian(润乾报表) + swiper(滑动插件) + 其他插件  
	> hdnx开发环境 Rational Application Developer8.5 + Websphere Application Server 8.5 + runqian4.0  
	> 全程参与，负责功能页面、报表、数据库等等好多啊。
```
webServer：
	// 发送第三服务接口查询，由第三方返回xml
	@Override
	public String loadSendAndGetXml(int year,int month,int day,String orgCode)throws Exception{
		String result = "";
		String xml = "<?xml version=\"1.0\" encoding=\"UTF-8\" ?>" +
	    		"<request>" +
	    		"	<year_time>"+year+"</year_time>" +
	    		"	<month_time>"+month+"</month_time>" +
	    		"	<day_time>"+month+"</day_time>" +
	    		"	<org_code>"+orgCode+"</org_code>" +
	    		"</request>";

		String soapaction = "http://webservice.service.marketing.sac.com";
        //你的webservice地址
        String endpoint = "http://day.hdpi.cn/services/ConfiguerService";
        Service service = new Service();
        try {
            Call call = (Call) service.createCall();
            call.setTimeout(new Integer(60000));
            call.setTargetEndpointAddress(new URL(endpoint));
            //你需要远程调用的方法
            call.setOperationName(new QName(soapaction,"loadConfiguer"));
            //方法参数，如果没有参数请无视
            call.addParameter(new QName(soapaction,"xml"), XMLType.XSD_STRING, ParameterMode.IN);
            //设置返回类型，对方接口返回的json，我就用string接收了,自定义类型另贴一个代码
            call.setReturnType(XMLType.XSD_STRING);
            //调用方法并传递参数，没有参数的话： call.invoke(new Object[] { null});
            result = (String) call.invoke(new Object[]{xml});
            System.out.println(result);
        } catch (Exception e) {
            e.printStackTrace();
        }
		return result;
	}
	
	//处理返回的结果
	@Override
	public JSONArray xmlAnalysis(String xml){
		
		JSONArray result = new JSONArray();
		
		//创建一个新的字符串
        StringReader read = new StringReader(xml);
        //创建新的输入源SAX 解析器将使用 InputSource 对象来确定如何读取 XML 输入
        InputSource source = new InputSource(read);
        //创建一个新的SAXBuilder
        SAXBuilder sb = new SAXBuilder();
        try {
            //通过输入源构造一个Document
            Document doc = sb.build(source);
            //取的根元素
            Element root = doc.getRootElement();
            //System.out.println(root.getName());//输出根元素的名称（测试）
            //得到根元素所有子元素的集合
            List jiedian = root.getChildren();
            //获得XML中的命名空间（XML中未定义可不写）
            Namespace ns = root.getNamespace();
            Element et = null;
            for(int i=0;i<jiedian.size();i++){
                et = (Element) jiedian.get(i);//循环依次得到子元素
               
                String note_code = et.getChild("note_code",ns).getText();
                String theValue = et.getChild("daypro_dayComp",ns).getText();
                Map<String,String> elecTypeList = Constants.ELEC_TYPE_CODE;
                
                System.out.println(note_code+"--"+elecTypeList.get(note_code)+":"+theValue);
                
                JSONObject json = new JSONObject();
                json.put("note_code", note_code);
                json.put("elecType", elecTypeList.get(note_code));
                json.put("theValue", theValue==null?0:theValue);
                result.add(json);
            }
           
            //所有节点字段
            /*et = (Element) jiedian.get(0);
            List zjiedian = et.getChildren();
            for(int j=0;j<zjiedian.size();j++){
                Element xet = (Element) zjiedian.get(j);
                System.out.println(xet.getName());
            }*/
            
        } catch (Exception e) {
            // TODO 自动生成 catch 块
            e.printStackTrace();
        }
		return result;
	}
	
	********************************************
	// 发送第三服务接口查询，由第三方返回json
	@Override
	public String loadSendAndGetJson(String fgs_orgcode,String dc_orgcode) throws Exception {
		String result = "";

		String soapaction = "http://eemp.webserver.Evaluate/";
		// 你的webservice地址
		String endpoint = "http://10.158.190.51:8081/eemp/webservice/evaluate?wsdl";
		Service service = new Service();
		try {
			Call call = (Call) service.createCall();
			call.setTimeout(new Integer(60000));
			call.setTargetEndpointAddress(new URL(endpoint));
			// 你需要远程调用的方法
			call.setOperationName(new QName(soapaction, "getTargetValue"));
			// 方法参数，如果没有参数请无视
			call.addParameter(new QName("arg0"), XMLType.XSD_STRING,
					ParameterMode.IN);
			call.addParameter(new QName("arg1"), XMLType.XSD_STRING,
					ParameterMode.IN);
			// 设置返回类型，对方接口返回的json，我就用string接收了,自定义类型另贴一个代码
			call.setReturnType(XMLType.XSD_STRING);
			// 调用方法并传递参数，没有参数的话： call.invoke(new Object[] { null});
			result = (String) call.invoke(new Object[] { fgs_orgcode,
					dc_orgcode });
			System.out.println("------------------------结果：" + result);
		} catch (Exception e) {
			e.printStackTrace();
		}
		return result;
	}
----------------------------------------------------------------------------------------------
文件格式转pdf:
[pdf转换功能配置：
	jacob-1.17-M2-x64.dll （32位）放置在Program Files\Java\jdk1.7.0\jre\bin 和Program Files\Java\jdk1.7.0\bin下
	C:\Windows\System32\config\systemprofile\Desktop文件夹创建
	jacob.jar包导入项目
	office安装
]
@Override
	public String loadAttachCache(String attachId,String parentId,String addr){
		JSONObject attachInfo = assessmentListDao.getAttachInfo(attachId,parentId);
		if(attachInfo!=null&&attachInfo.get("attachAddr")!=null&&attachInfo.get("attachName")!=null){
			String attachName = attachInfo.get("attachName").toString();
			String attachAddr = attachInfo.get("attachAddr").toString();
			try {
				File file = new File(attachAddr + attachName);
				// 如果文件不存在
				if (!file.exists()) {
					log.info("无文件信息");
					return "1";
				}
				String fileName=file.getName();
			    String prefix=fileName.substring(fileName.lastIndexOf(".")+1);
			    String theName = fileName.substring(0,fileName.lastIndexOf("."));
				/*if(prefix.equals("pdf")){
					System.out.println("PDF not need to convert!");
					
				}*/
			    FileConvert fileConvert = new FileConvert();
			    deleteFile(new File(addr+"hdnx/fileCache/")); 
			    if(prefix.equals("doc")||prefix.equals("docx")||prefix.equals("txt")||prefix.equals("ppt")||prefix.equals("pptx")||prefix.equals("xls")||prefix.equals("xlsx")){
					//当文件是office格式时，转成pdf到项目文件夹下展示
				    boolean isSuccess = fileConvert.convert2PDF(attachAddr + attachName, addr+"hdnx/fileCache/"+theName+".pdf");
				    if(isSuccess==true){
				    	return theName+".pdf";
				    }
				}else{
					System.out.println("文件格式不支持转换!");
					boolean isSuccess = fileConvert.copyFile(attachAddr + attachName, addr+"hdnx/fileCache/"+fileName);
					if(isSuccess==true){
				    	return fileName;
				    }
				}
			    
			    
			} catch (Exception e) {
				log.error(e);
				return "2";
			}
		}
		return "1";
	}
	
	/**
	 * 清空pdf的文件夹
	 * @param oldPath
	 */
	 public void deleteFile(File oldPath) {
         if (oldPath.isDirectory()) {
          System.out.println(oldPath + "是文件夹--");
          File[] files = oldPath.listFiles();
          for (File file : files) {
            deleteFile(file);
          }
         }else{
           oldPath.delete();
         }
       }
```
3. idev2(iDeveloper)    

	*from 2017-05-26 to 2017-07-21*  
	> iDeveloper服务端 NodeJs + express + mongoDB + (微服务?)  
	> iDeveloper前端 antDesign + Redux + React + ES6 + less  
	> iDeveloper开发环境 Git + NodeJs + Visual Studio Code(非必需) 
	> 负责【业务功能管理】模块，功能菜单的管理及权限管理，断断续续修改学习，系统为初行版。
```
idev2开发
新页面配置：
	D:\idev2NewCode\dev\client\src\route\routes.js --------------页面请求路由
		import detail和list
		Switch中PrivateRoute配置path
	D:\idev2NewCode\dev\server\src\services\menuData.js----------菜单配置
		link中对应其路由
	D:\idev2NewCode\dev\client\src\index.js----------------------redux的sagas
		import detail和list的sagas
		store.runSaga(对应saga)
	D:\idev2NewCode\dev\client\src\reducers\index.js-------------redux的reducers
		import detail和list的reducers
		const rootReducer = combineReducers({对应reducers})
	D:\idev2NewCode\dev\client\src\actions\index.js--------------action配置
		export * as ...


页面交互及状态
	config.js---------------------
		mapStateToProps里添加某个状态,指向reducers.js里的方法
	reducers.js-------------------	
		对应config里定义的方法，根据action里操作名称做出反应
	action.js---------------------
		定义操作名称；调用操作的方法,与sagaDetail里参数对应
	sagaDetail~.js	
		定义操作调用参数方法，在传递props时给页面组件
	
方法的配置：
	sagas.js里调用api接口请求数据，并根据结果调用reducers.js改变页面状态
	reducers.js里根据操作类型参数改变页面某个状态返回
	action.js里定义操作名称和方法供其他页面判断调用，方法内action()指向reducers.js操作状态或指向sagas.js请求数据
	config.js里buildProps将action.js里的方法传给sagaDetail~.js组件
	sagaDetail~.js	里通过render接收参数，自定义函数调用参数方法，最后通过React.cloneElement传给页面组件
	页面组件里方法通过props传参，页面调用
状态参数
	reducers.js里根据操作类型参数改变页面某个状态返回
	config.js里mapStateToProps定义状态名称，并指向reducers.js里方法的返回值
	sagaDetail~.js接收状态传给子组件
	页面组件通过参数获取状态，值改变组件刷新
---------------------------------------------------------------------------
git操作记录
git clone git@***.**.***.150:/srv/dev.git
git checkout dev
ls
cd dev
git checkout dev
	
	git pull
	git stash
	git stash pop stash@{0}
先按 i 切换到insert模式，就可以输入了，输入完之后先按esc，再输入:wq,回车
```
4. 其他  
	- yccs(远程测试平台) 
	- lsny(电能绿色管理系统),lsny_jsjd(上海市并网电厂技术监督网)  
	- dwxb(电网谐波数据状态分析)  
	- tqjc(上海市电力公司运行月报)
