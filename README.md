## Spring Boot 2.x + Orient DB 3.x test

This is a test/showcase project trying to integrate Spring Boot 2.x with Orient DB 3.x in relation to a bug at:
https://github.com/orientechnologies/spring-data-orientdb/issues/79

To run the project just run `./gradlew bootRun` (or just `gradlew bootRun` on Windows)
at the root of the project. Or `./gradlew clean bootRun` for a clean build each time you start the app.

The app should crash with:

```
org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'helloApplication': Unsatisfied dependency expressed through field 'repository'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'personRepository': Invocation of init method failed; nested exception is java.lang.IllegalStateException: You have defined query method in the repository but you don't have any query lookup strategy defined. The infrastructure apparently does not support query methods!
	at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:587) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.annotation.InjectionMetadata.inject(InjectionMetadata.java:91) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessPropertyValues(AutowiredAnnotationBeanPostProcessor.java:373) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1350) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:580) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:503) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:317) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:315) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:199) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:760) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:869) ~[spring-context-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:550) ~[spring-context-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:140) ~[spring-boot-2.0.3.RELEASE.jar:2.0.3.RELEASE]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:759) [spring-boot-2.0.3.RELEASE.jar:2.0.3.RELEASE]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:395) [spring-boot-2.0.3.RELEASE.jar:2.0.3.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:327) [spring-boot-2.0.3.RELEASE.jar:2.0.3.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1255) [spring-boot-2.0.3.RELEASE.jar:2.0.3.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1243) [spring-boot-2.0.3.RELEASE.jar:2.0.3.RELEASE]
	at org.springframework.boot.orientdb.hello.HelloApplication.main(HelloApplication.java:33) [main/:na]
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'personRepository': Invocation of init method failed; nested exception is java.lang.IllegalStateException: You have defined query method in the repository but you don't have any query lookup strategy defined. The infrastructure apparently does not support query methods!
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1708) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:581) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:503) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:317) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:315) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:199) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:251) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1138) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1065) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:584) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	... 19 common frames omitted
Caused by: java.lang.IllegalStateException: You have defined query method in the repository but you don't have any query lookup strategy defined. The infrastructure apparently does not support query methods!
	at org.springframework.data.repository.core.support.RepositoryFactorySupport$QueryExecutorMethodInterceptor.<init>(RepositoryFactorySupport.java:532) ~[spring-data-commons-2.0.8.RELEASE.jar:2.0.8.RELEASE]
	at org.springframework.data.repository.core.support.RepositoryFactorySupport.getRepository(RepositoryFactorySupport.java:317) ~[spring-data-commons-2.0.8.RELEASE.jar:2.0.8.RELEASE]
	at org.springframework.data.repository.core.support.RepositoryFactoryBeanSupport.lambda$afterPropertiesSet$3(RepositoryFactoryBeanSupport.java:287) ~[spring-data-commons-2.0.8.RELEASE.jar:2.0.8.RELEASE]
	at org.springframework.data.util.Lazy.getNullable(Lazy.java:141) ~[spring-data-commons-2.0.8.RELEASE.jar:2.0.8.RELEASE]
	at org.springframework.data.util.Lazy.get(Lazy.java:63) ~[spring-data-commons-2.0.8.RELEASE.jar:2.0.8.RELEASE]
	at org.springframework.data.repository.core.support.RepositoryFactoryBeanSupport.afterPropertiesSet(RepositoryFactoryBeanSupport.java:290) ~[spring-data-commons-2.0.8.RELEASE.jar:2.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1767) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1704) ~[spring-beans-5.0.7.RELEASE.jar:5.0.7.RELEASE]
	... 29 common frames omitted
```

Dependencies:

- springBootVersion = '2.0.3.RELEASE'
- orientDB_version = '3.0.2'
- spring_boot_orientDB_version = '0.14-3.0.1-SNAPSHOT'
