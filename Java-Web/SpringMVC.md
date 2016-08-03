##Spring MVC
###Spring MVC的总体设计
* 在web.xml中配置一个DispatchServlet
* 再定义一个dispatcherServlet-servlet.xml配置文件（定义、配置Mapping, View, Control的bean）
* 3个重要组件功能：
  * 定义URL映射规则
  * 实现业务逻辑的Handler实例对象
  * 渲染模板资源

###Spring MVC初始化
* HttpServletBean的init()方法获取初始化参数，并创建BeanWrapper对象
* FrameworkServlet的initServeltBean()方法创建WebApplicationContext对象，并初始化Spring容器
* 调用WebApplicationContext的onApplicationEvent(), onRefresh()方法完成配置文件的加载
* DispatcherServlet的initStrategies()方法，初始化8个组件（即8个Bean）
  * initMultipartResolver，用于处理文件上传服务
  * initLocaleResolver：用于处理应用的国际化问题（字符编码问题）
  * initThemeResolver：用于定义一个主题
  * initHandlerMappings：用于定义用户设置的请求映射关系
  * initHandlerAdapters：用于根据Handler的类型定义不同的处理规则
  * initHandlerExceptionResolver
  * initRequestToViewNameTranslator
  * initViewResolver：用于将View解析成页面（可以根据JSP解析，或者按照Velocity模板解析）

###Control设计
* Control主要由HandlerMapping和HandlerAdapters两个组件提供
* HandlerMapping初始化：
  * 将一个或多个URL映射到一个或多个Spring Bean中
  * 把interceptor对象包装成HandlerInterceptor对象，保存在adapterdInterceptors数组中
  * 将URL与Handler的对应关系保存到handlerMap集合中
* Control的调用逻辑
  * DispatcherServlet的doService()方法，将对象放入request中
  * doDispatch()方法，处理用户请求
  * checkMultipart方法
  * 在HandlerMap集合中依次匹配getHandler(request)方法，返回HandlerExecutionChain对象
  * getInterceptors()获取该Handler中定义的HandlerInterceptor对象，执行preHandle，postHandle，afterCompletion方法
  * 在handlerAdapters集合中调用getHandlerAdapter()方法，执行handler方法

###IntelliJ Idea使用技巧
* 在部署web应用时，选择war exploded，这样才不会出错，war实测下来是不行的
* Spring MVC对静态资源的处理：将文件夹放入webapp下面（在servlet.xml中添加<resources mapping="/resources/**" location="/images/" />）
