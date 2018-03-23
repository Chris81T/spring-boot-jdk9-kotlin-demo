# UPDATE - Is fixed
Check the post at https://stackoverflow.com/questions/49454359/spring-boot-2-kotlin-jdk9-caused-by-java-lang-classnotfoundexception-jav

# spring-boot-jdk9-kotlin-demo
A sample project, that will fail with JDK 9.0.4 on Arch Linux

Used JDK version:
java version "9.0.4"
Java(TM) SE Runtime Environment (build 9.0.4+11)
Java HotSpot(TM) 64-Bit Server VM (build 9.0.4+11, mixed mode)

Used Maven version:
Apache Maven 3.5.2 (NON-CANONICAL_2017-10-25T13:09:52+03:00_root; 2017-10-25T12:09:52+02:00)
Java version: 9.0.4, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-9-jdk
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "4.15.6-1-arch", arch: "amd64", family: "unix"


How to reproduce:

Got to https://start.spring.io/ and select 

"Generate a [Maven Project] with [Kotlin] and Spring Boot [2.0.0]"

Also select following modules:

* Actuator
* JPA
* H2
* Security

Download the project, unzip it and try to build it with maven

Then following Error is coming:

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.0.0.RELEASE)

2018-03-23 20:03:43.212  INFO 4716 --- [           main] de.example.demo.DemoApplicationTests     : Starting DemoApplicationTests on jarvis with PID 4716 (started by christian in /ct_home/development/github/spring-boot-jdk9-kotlin-demo)
2018-03-23 20:03:43.212  INFO 4716 --- [           main] de.example.demo.DemoApplicationTests     : No active profile set, falling back to default profiles: default
2018-03-23 20:03:43.214  INFO 4716 --- [           main] s.c.a.AnnotationConfigApplicationContext : Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@2721044: startup date [Fri Mar 23 20:03:43 CET 2018]; root of context hierarchy
2018-03-23 20:03:43.446  INFO 4716 --- [           main] trationDelegate$BeanPostProcessorChecker : Bean 'org.springframework.transaction.annotation.ProxyTransactionManagementConfiguration' of type [org.springframework.transaction.annotation.ProxyTransactionManagementConfiguration$$EnhancerBySpringCGLIB$$2da77b1] is not eligible for getting processed by all BeanPostProcessors (for example: not eligible for auto-proxying)
2018-03-23 20:03:43.552  INFO 4716 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-2 - Starting...
2018-03-23 20:03:43.557  INFO 4716 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-2 - Start completed.
2018-03-23 20:03:43.573  INFO 4716 --- [           main] j.LocalContainerEntityManagerFactoryBean : Building JPA container EntityManagerFactory for persistence unit 'default'
2018-03-23 20:03:43.574  WARN 4716 --- [           main] s.c.a.AnnotationConfigApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Invocation of init method failed; nested exception is java.lang.NoClassDefFoundError: Could not initialize class org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl
2018-03-23 20:03:43.574  INFO 4716 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-2 - Shutdown initiated...
2018-03-23 20:03:43.575  INFO 4716 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-2 - Shutdown completed.
2018-03-23 20:03:43.581  INFO 4716 --- [           main] ConditionEvaluationReportLoggingListener : 

Error starting ApplicationContext. To display the conditions report re-run your application with 'debug' enabled.
2018-03-23 20:03:43.583 ERROR 4716 --- [           main] o.s.boot.SpringApplication               : Application run failed

org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Invocation of init method failed; nested exception is java.lang.NoClassDefFoundError: Could not initialize class org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1710) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:583) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:502) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:312) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:228) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:310) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1085) ~[spring-context-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:858) ~[spring-context-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:549) ~[spring-context-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:752) ~[spring-boot-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:388) ~[spring-boot-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:327) ~[spring-boot-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:138) [spring-boot-test-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContextInternal(DefaultCacheAwareContextLoaderDelegate.java:99) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:117) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.support.DefaultTestContext.getApplicationContext(DefaultTestContext.java:107) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.boot.test.autoconfigure.SpringBootDependencyInjectionTestExecutionListener.outputConditionEvaluationReport(SpringBootDependencyInjectionTestExecutionListener.java:54) [spring-boot-test-autoconfigure-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.boot.test.autoconfigure.SpringBootDependencyInjectionTestExecutionListener.prepareTestInstance(SpringBootDependencyInjectionTestExecutionListener.java:47) [spring-boot-test-autoconfigure-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.test.context.TestContextManager.prepareTestInstance(TestContextManager.java:242) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.createTest(SpringJUnit4ClassRunner.java:227) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner$1.runReflectiveCall(SpringJUnit4ClassRunner.java:289) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12) [junit-4.12.jar:4.12]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.methodBlock(SpringJUnit4ClassRunner.java:291) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.runChild(SpringJUnit4ClassRunner.java:246) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.runChild(SpringJUnit4ClassRunner.java:97) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.junit.runners.ParentRunner$3.run(ParentRunner.java:290) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:71) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:288) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner.access$000(ParentRunner.java:58) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:268) [junit-4.12.jar:4.12]
        at org.springframework.test.context.junit4.statements.RunBeforeTestClassCallbacks.evaluate(RunBeforeTestClassCallbacks.java:61) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.statements.RunAfterTestClassCallbacks.evaluate(RunAfterTestClassCallbacks.java:70) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.junit.runners.ParentRunner.run(ParentRunner.java:363) [junit-4.12.jar:4.12]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.run(SpringJUnit4ClassRunner.java:190) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.apache.maven.surefire.junit4.JUnit4Provider.execute(JUnit4Provider.java:369) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.junit4.JUnit4Provider.executeWithRerun(JUnit4Provider.java:275) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.junit4.JUnit4Provider.executeTestSet(JUnit4Provider.java:239) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.junit4.JUnit4Provider.invoke(JUnit4Provider.java:160) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.invokeProviderInSameClassLoader(ForkedBooter.java:373) [surefire-booter-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.runSuitesInProcess(ForkedBooter.java:334) [surefire-booter-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.execute(ForkedBooter.java:119) [surefire-booter-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.main(ForkedBooter.java:407) [surefire-booter-2.20.1.jar:2.20.1]
Caused by: java.lang.NoClassDefFoundError: Could not initialize class org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:51) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:365) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:388) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:377) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:341) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1769) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1706) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        ... 42 common frames omitted

2018-03-23 20:03:43.584 ERROR 4716 --- [           main] o.s.test.context.TestContextManager      : Caught exception while allowing TestExecutionListener [org.springframework.boot.test.autoconfigure.SpringBootDependencyInjectionTestExecutionListener@5f354bcf] to prepare test instance [de.example.demo.DemoApplicationTests@484094a5]

java.lang.IllegalStateException: Failed to load ApplicationContext
        at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:125) ~[spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.support.DefaultTestContext.getApplicationContext(DefaultTestContext.java:107) ~[spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.support.DependencyInjectionTestExecutionListener.injectDependencies(DependencyInjectionTestExecutionListener.java:117) ~[spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.support.DependencyInjectionTestExecutionListener.prepareTestInstance(DependencyInjectionTestExecutionListener.java:83) ~[spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.boot.test.autoconfigure.SpringBootDependencyInjectionTestExecutionListener.prepareTestInstance(SpringBootDependencyInjectionTestExecutionListener.java:44) ~[spring-boot-test-autoconfigure-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.test.context.TestContextManager.prepareTestInstance(TestContextManager.java:242) ~[spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.createTest(SpringJUnit4ClassRunner.java:227) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner$1.runReflectiveCall(SpringJUnit4ClassRunner.java:289) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12) [junit-4.12.jar:4.12]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.methodBlock(SpringJUnit4ClassRunner.java:291) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.runChild(SpringJUnit4ClassRunner.java:246) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.runChild(SpringJUnit4ClassRunner.java:97) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.junit.runners.ParentRunner$3.run(ParentRunner.java:290) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:71) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:288) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner.access$000(ParentRunner.java:58) [junit-4.12.jar:4.12]
        at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:268) [junit-4.12.jar:4.12]
        at org.springframework.test.context.junit4.statements.RunBeforeTestClassCallbacks.evaluate(RunBeforeTestClassCallbacks.java:61) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.junit4.statements.RunAfterTestClassCallbacks.evaluate(RunAfterTestClassCallbacks.java:70) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.junit.runners.ParentRunner.run(ParentRunner.java:363) [junit-4.12.jar:4.12]
        at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.run(SpringJUnit4ClassRunner.java:190) [spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.apache.maven.surefire.junit4.JUnit4Provider.execute(JUnit4Provider.java:369) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.junit4.JUnit4Provider.executeWithRerun(JUnit4Provider.java:275) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.junit4.JUnit4Provider.executeTestSet(JUnit4Provider.java:239) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.junit4.JUnit4Provider.invoke(JUnit4Provider.java:160) [surefire-junit4-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.invokeProviderInSameClassLoader(ForkedBooter.java:373) [surefire-booter-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.runSuitesInProcess(ForkedBooter.java:334) [surefire-booter-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.execute(ForkedBooter.java:119) [surefire-booter-2.20.1.jar:2.20.1]
        at org.apache.maven.surefire.booter.ForkedBooter.main(ForkedBooter.java:407) [surefire-booter-2.20.1.jar:2.20.1]
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Invocation of init method failed; nested exception is java.lang.NoClassDefFoundError: javax/transaction/SystemException
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1710) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:583) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:502) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:312) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:228) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:310) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1085) ~[spring-context-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:858) ~[spring-context-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:549) ~[spring-context-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:752) ~[spring-boot-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:388) ~[spring-boot-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:327) ~[spring-boot-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:138) ~[spring-boot-test-2.0.0.RELEASE.jar:2.0.0.RELEASE]
        at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContextInternal(DefaultCacheAwareContextLoaderDelegate.java:99) ~[spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:117) ~[spring-test-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        ... 28 common frames omitted
Caused by: java.lang.NoClassDefFoundError: javax/transaction/SystemException
        at java.base/java.lang.Class.forName0(Native Method) ~[na:na]
        at java.base/java.lang.Class.forName(Class.java:375) ~[na:na]
        at org.jboss.logging.Logger$1.run(Logger.java:2554) ~[jboss-logging-3.3.2.Final.jar:3.3.2.Final]
        at java.base/java.security.AccessController.doPrivileged(Native Method) ~[na:na]
        at org.jboss.logging.Logger.getMessageLogger(Logger.java:2529) ~[jboss-logging-3.3.2.Final.jar:3.3.2.Final]
        at org.jboss.logging.Logger.getMessageLogger(Logger.java:2516) ~[jboss-logging-3.3.2.Final.jar:3.3.2.Final]
        at org.hibernate.internal.HEMLogging.messageLogger(HEMLogging.java:28) ~[hibernate-core-5.2.14.Final.jar:5.2.14.Final]
        at org.hibernate.internal.HEMLogging.messageLogger(HEMLogging.java:24) ~[hibernate-core-5.2.14.Final.jar:5.2.14.Final]
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.<clinit>(EntityManagerFactoryBuilderImpl.java:116) ~[hibernate-core-5.2.14.Final.jar:5.2.14.Final]
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:51) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:365) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:388) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:377) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:341) ~[spring-orm-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1769) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1706) ~[spring-beans-5.0.4.RELEASE.jar:5.0.4.RELEASE]
        ... 43 common frames omitted
Caused by: java.lang.ClassNotFoundException: javax.transaction.SystemException
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:582) ~[na:na]
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:185) ~[na:na]
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:496) ~[na:na]
        ... 59 common frames omitted

[ERROR] Tests run: 1, Failures: 0, Errors: 1, Skipped: 0, Time elapsed: 2.255 s <<< FAILURE! - in de.example.demo.DemoApplicationTests
[ERROR] contextLoads(de.example.demo.DemoApplicationTests)  Time elapsed: 0.006 s  <<< ERROR!
java.lang.IllegalStateException: Failed to load ApplicationContext
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Invocation of init method failed; nested exception is java.lang.NoClassDefFoundError: javax/transaction/SystemException
Caused by: java.lang.NoClassDefFoundError: javax/transaction/SystemException
Caused by: java.lang.ClassNotFoundException: javax.transaction.SystemException

[INFO] 
[INFO] Results:
[INFO] 
[ERROR] Errors: 
[ERROR]   DemoApplicationTests.contextLoads ? IllegalState Failed to load ApplicationCon...
[INFO] 
[ERROR] Tests run: 1, Failures: 0, Errors: 1, Skipped: 0
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 7.110 s
[INFO] Finished at: 2018-03-23T20:03:43+01:00
[INFO] Final Memory: 36M/120M
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.20.1:test (default-test) on project spring-boot-jdk9-kotlin-demo: There are test failures.
[ERROR] 
[ERROR] Please refer to /ct_home/development/github/spring-boot-jdk9-kotlin-demo/target/surefire-reports for the individual test results.
[ERROR] Please refer to dump files (if any exist) [date]-jvmRun[N].dump, [date].dumpstream and [date]-jvmRun[N].dumpstream.
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException

