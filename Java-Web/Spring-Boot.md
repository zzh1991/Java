##Spring Boot

##Java配置
* @Configuration：声明当前类是一个配置类，相当于一个xml配置文件。
* @Bean：注解在方法上，声明当前方法返回一个Bean。
* @ComponentScan：自动扫描包。
* Java配置和注解配置混合使用的原则：全局配置实用Java配置（如数据库相关配置、MVC相关配置），业务Bean配置使用注解配置（@Service、@Component、@Repository、@Controller）。

##AOP
* 使用@Aspect声明一个切面。
* 使用@After、@Before、@Around定义建言（advice），可直接将拦截规则（切点）作为参数。
* 其中使用@After、@Before、@Around参数的拦截规则为切点（PointCut），为了使切点复用，可以使用@After、@Before、@Around的参数中调用。
* 其中符合条件的每一个被拦截处为连接点（JoinPoint）。
* 注解式拦截比基于方法规则拦截，更好控制要拦截的粒度和获得更丰富的信息，Spring本身在事务处理（@Transcational）和数据缓存（@Cacheable）上面都是使用此种形式的拦截。

##Spring EL和资源调用
* 注入普通字符：@Value("I Love You")。
* 注入操作系统属性：@Value("#{systemProperties['os.name']}")。
* 注入表达式运算结果：@Value("#{ T(java.lang.Math).random() * 100.0 }")。
* 注入其他Bean属性：@Value("#{demoService.another}")。
* 注入文件内容：@Value("classpath:com/github/sawyersun/resources/test.txt")。
* 注入网址内容：@Value("http://www.baidu.com")。
* 注入属性文件：@Value("${book.name}")。

##Spring Aware
* BeanNameAware：获得容器中bean名称。
* BeanFactoryAware：获得当前bean factory，可以调用容器的服务。
* ApplicationContextAware：当前application context，可以容器的服务。
* MessageSourceAware：message source，可以获得文本信息。
* ApplicationEventPublisherAware：应用事件发布器，可以发布事件。
* ResourceLoaderAware：获得资源加载器，可以获得外部资源
* ApplicationContext接口继承了MessageSource接口、ApplicationEventPublisher接口、ResourceLoader接口，可以获得Spring容器的全部服务。

##多线程
* Spring通过任务执行器（TaskExecutor）来实现多线程和并发编程。使用ThreadPoolTaskExecutor可实现一个机遇线程池的TaskEXecutor。在配置类通过@EnableAsync开启异步任务支持，在实际执行的bean方法中使用@Async注解申明其是一个异步任务。

##计划任务
* 首先在配置类通过@EnableScheduling开启计划任务的支持，然后在要执行的计划任务上注解@Scheduled，声明这是一个计划任务。Spring支持多种类型的计划任务，包含cron、fixDay、fixRate等。

##Spring MVC
常用注解：
* @Controller：控制器类。
* @RequestMapping：映射web请求到处理类和方法。
* @ResponseBody：支持将返回值放在response内，而不是返回界面。
* @RequestBody：允许request的参数在resuest体中，而不是直接链接在地址后面。
* @PathVariable：路径参数。
* @RestController：组合@Controller和@ResponseBody注解。
<br>
<br>
继承WebMvcConfigurerAdapter完成我们自己的配置类，并通过@EnableWebMvc开启对Spring MVC的支持。
<br>
拦截器（Interceptor）实现对每个请求处理前后进行相关的业务处理，类似于Servlet的Filter。继承HanderInterceptorAdapter或者实现HandlerInterceptor接口来实现自定义拦截器。重写WebMvcConfigurerAdapter的addInterceptors来注册自定义拦截器。
