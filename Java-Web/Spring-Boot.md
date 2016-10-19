##Spring Boot

##Java配置
* @Configuration：声明当前类是一个配置类，相当于一个xml配置文件。
* @Bean：注解在方法上，声明当前方法返回一个Bean。
* @ComponentScan：自动扫描包。
* Java配置和注解配置混合使用的原则：全局配置实用Java配置（如数据库相关配置、MVC相关配置），业务Bean配置使用注解配置（@Service、@Component、@Repository、@Controller）。

##ASP
* 使用@Aspect声明一个切面。
* 使用@After、@Before、@Around定义建言（advice），可直接将拦截规则（切点）作为参数。
* 其中使用@After、@Before、@Around参数的拦截规则为切点（PointCut），为了使切点复用，可以使用@After、@Before、@Around的参数中调用。
* 其中符合条件的每一个被拦截处为连接点（JoinPoint）。
* 注解式拦截比基于方法规则拦截，更好控制要拦截的粒度和获得更丰富的信息，Spring本身在事务处理（@Transcational）和数据缓存（@Cacheable）上面都是使用此种形式的拦截。
