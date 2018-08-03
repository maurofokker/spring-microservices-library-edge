# Spring microservice library edge service (Zuul)

* This service is part of the simple library microservices project and includes
  * [library configuration server](https://github.com/maurofokker/spring-microservices-library-config)
  * [library reservation](https://github.com/maurofokker/spring-microservices-library-reservation)
  * [library catalog](https://github.com/maurofokker/spring-microservices-library-catalog)
  * [library ui](https://github.com/maurofokker/spring-microservices-library-ui)
  * [library discovery & registry](https://github.com/maurofokker/spring-microservices-library-registry)
  * [library edge service](https://github.com/maurofokker/spring-microservices-library-edge)
* Microservices reference can be found [here](https://github.com/maurofokker/microservices-demo)
* `Zuul Edge Service` perform a Load Balancing with `Ribbon` by default without additional configuration
  * For this example `library reservation` has 2 instances running on ports 5006 and 5007 
  * Edge service logs contain `Ribbon` doing a Load balancing for services
  ```
    o.s.c.n.zuul.web.ZuulHandlerMapping      : Mapped URL path [/catalog/**] onto handler of type [class org.springframework.cloud.netflix.zuul.web.ZuulController]
    s.c.a.AnnotationConfigApplicationContext : Refreshing SpringClientFactory-reservation: startup date [Fri Aug 03 09:58:56 CLT 2018]; parent: org.springframework.boot.web.servlet.context.AnnotationConfigServletWebServerApplicationContext@6e01f9b0
    f.a.AutowiredAnnotationBeanPostProcessor : JSR-330 'javax.inject.Inject' annotation found and supported for autowiring
    c.netflix.config.ChainedDynamicProperty  : Flipping property: reservation.ribbon.ActiveConnectionsLimit to use NEXT property: niws.loadbalancer.availabilityFilteringRule.activeConnectionsLimit = 2147483647
    c.n.u.concurrent.ShutdownEnabledTimer    : Shutdown hook installed for: NFLoadBalancer-PingTimer-reservation
    c.netflix.loadbalancer.BaseLoadBalancer  : Client: reservation instantiated a LoadBalancer: DynamicServerListLoadBalancer:{NFLoadBalancer:name=reservation,current list of Servers=[],Load balancer stats=Zone stats: {},Server stats: []}ServerList:null
    c.n.l.DynamicServerListLoadBalancer      : Using serverListUpdater PollingServerListUpdater
    c.netflix.config.ChainedDynamicProperty  : Flipping property: reservation.ribbon.ActiveConnectionsLimit to use NEXT property: niws.loadbalancer.availabilityFilteringRule.activeConnectionsLimit = 2147483647
    c.n.l.DynamicServerListLoadBalancer      : DynamicServerListLoadBalancer for client reservation initialized: DynamicServerListLoadBalancer:{NFLoadBalancer:name=reservation,current list of Servers=[mgaldames-ntbk:5007, mgaldames-ntbk:5006],Load balancer stats=Zone stats: {defaultzone=[Zone:defaultzone;	Instance count:2;	Active connections count: 0;	Circuit breaker tripped count: 0;	Active connections per server: 0.0;]
},Server stats: [[Server:mgaldames-ntbk:5006;	Zone:defaultZone;	Total Requests:0;	Successive connection failure:0;	Total blackout seconds:0;	Last connection made:Wed Dec 31 21:00:00 CLST 1969;	First connection made: Wed Dec 31 21:00:00 CLST 1969;	Active Connections:0;	total failure count in last (1000) msecs:0;	average resp time:0.0;	90 percentile resp time:0.0;	95 percentile resp time:0.0;	min resp time:0.0;	max resp time:0.0;	stddev resp time:0.0]
, [Server:mgaldames-ntbk:5007;	Zone:defaultZone;	Total Requests:0;	Successive connection failure:0;	Total blackout seconds:0;	Last connection made:Wed Dec 31 21:00:00 CLST 1969;	First connection made: Wed Dec 31 21:00:00 CLST 1969;	Active Connections:0;	total failure count in last (1000) msecs:0;	average resp time:0.0;	90 percentile resp time:0.0;	95 percentile resp time:0.0;	min resp time:0.0;	max resp time:0.0;	stddev resp time:0.0]
]}ServerList:org.springframework.cloud.netflix.ribbon.eureka.DomainExtractingServerList@7470b699
    c.netflix.config.ChainedDynamicProperty  : Flipping property: reservation.ribbon.ActiveConnectionsLimit to use NEXT property: niws.loadbalancer.availabilityFilteringRule.activeConnectionsLimit = 2147483647
  ```
  