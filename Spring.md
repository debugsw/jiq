##### Spring AOP底层原理
     AOP 解释：
     通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。AOP是OOP（面向对象编程）的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，是函数式编程的一种衍生范型。
     利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高开发的效率。
     
     AOP 底层是采用动态代理机制实现的：接口+实现类
     1、基于JDK的动态代理
       如果要代理的对象，实现了某个接口，那么 Spring AOP 会使用 JDK Proxy，去创建代理对象。
     
     2、基于CGLIB动态代理
       没有实现接口的对象，就无法使用 JDK Proxy 去进行代理了，这时候 Spring AOP 会使用 Cglib 生成一个被代理对象的子类来作为代理。
     
     就是由代理创建出一个和 impl 实现类平级的一个对象，但是这个对象不是一个真正的对象，
     只是一个代理对象，但它可以实现和 impl 相同的功能，这个就是 aop 的横向机制原理，这
     样就不需要修改源代码

##### 什么是 Spring 的依赖注入
      依赖注入，是 IOC 的一个方面，是个通常的概念，它有多种解释。这概念是说你不用创建对象，而只需要描述它如何被创建。你不在代码里直接组装你的组件和服务，但是要在配置文件里描述哪些组件需要哪
      些服务，之后一个容器（IOC 容器）负责把他们组装起来

##### 什么是 Spring IOC 容器
      Spring IOC 负责创建对象，管理对象（通过依赖注入（DI），装配对象，配置对象，并且管理这些对象的整个生命周期。
      
##### 什么是 Spring 的依赖注入
      依赖注入，是 IOC 的一个方面，是个通常的概念，它有多种解释。这概念是说你不用创建对象，而只需要描述它如何被创建。你不在代码里直接组装你的组件和服务，但是要在配置文件里描述哪些组件需要
      哪些服务，之后一个容器（IOC 容器）负责把他们组装起来
      
##### 有哪些不同类型的 IOC（依赖注入）方式
      1、构造器依赖注入：构造器依赖注入通过容器触发一个类的构造器来实现的，该类有一系列参数，每个参数代表一个对其他类的依赖。
      2、Setter 方法注入：Setter 方法注入是容器通过调用无参构造器或无参 static 工厂方法实例化bean之后，调用该bean的setter方法，即实现了基于setter的依赖注入。

##### 什么是 Spring Beans?
      Spring beans是那些形成Spring应用的主干的java对象。它们被 Spring IOC容器初始化，装配，和管理。这些 beans 通过容器中配置的元数据创建。比如以XML文件中的形式定义。Spring框架定
      义的beans都是单件beans。在bean tag中有个属性”singleton”，如果它被赋为 TRUE，bean 就是单件，否则就是一个 prototypebean。默认是TRUE，所以所有在 Spring 框架中的beans缺省
      都是单件。
      
##### 解释 Spring 框架中 Bean 的生命周期
      1、Spring容器从XML文件中读取bean的定义，并实例化bean。
      2、Spring根据bean 的定义填充所有的属性。
      3、如果bean实现了BeanNameAware接口，Spring传递bean的ID到setBeanName 方法。
      4、如果Bean实现了BeanFactoryAware接口，Spring传递beanfactory给setBeanFactory方法。
      5、如果有任何与bean相关联的BeanPostProcessors，Spring会在postProcesserBeforeInitialization()方法内调用它们。
      6、如果bean实现IntializingBean了，调用它的afterPropertySet方法，如果bean声明了初始化方法，调用此初始化方法。
      7、如果有BeanPostProcessors和bean关联，这些bean的postProcessAfterInitialization() 方法将被调用。
      8、如果bean实现了DisposableBean，它将调用destroy()方法。
