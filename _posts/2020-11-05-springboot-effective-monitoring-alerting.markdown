---
layout: post
title:  "Spring boot - Effective monitoring and alerting"
date:   2020-11-05 13:55:23 +0530
categories: MicroServices
---

# Monitoring and Alerting your spring boot

While developing micro services is one thing, monitoring (and alerting in serious issues)post deployment and in production is equally important for an effective DevOps operation. In this blog, I am going to discuss some of the best practices that I have learnt and hence would recommend in monitoring critical Spring Boot based micro services in production:
  
  - **Enable Metrics** : Firstly as you might already know that Spring Boot has moved out from actuator (which it used in Spring boot 1) and now uses Micrometer in Spring Boot 2. So we no longer have a single end point like /actuator/metrics in Spring boot 2. Reason is the introduction of dimensional metrics like @Timer which can’t be simply rendered in a single view or payload. But also it means a plethora of metrics are now available and hence the first step is to disable all and enable only those which you want. Below example configuration means that only the http requests related and cache related metrics are available. Note these are out of the box metrics in spring boot. If you want any custom metrics, you will also have to enable the corresponding tag.
{% highlight ruby %}
management:
  metrics:
    enable:
      all: false
      http.server.requests: true
      api: true
{ endhighlight }
- **Collect Metrics** : Secondly we need to collect the metrics in a dimensional metrics system like Prometheus or SignalFX. I would recommend using Prometheus which is very simple to setup locally. Below is an example configuration which can be used by prometheus to scrape the endpoint /management/prometheus. Note that it is different from the endpoint used in Spring boot 1 which was /actuator/prometheus. So you need to change your prometheus configuration if you migrate from Springboot 1 to 2.
{% highlight ruby %}
management:
  endpoints:
    web:
      base-path: /management
      exposure:
        include: info, health, metrics, prometheus
{ endhighlight }    
- **Enable @Timed on controllers** : Annotate the controllers with @Timed annotation and with percentiles. This gives an almost out of the box end to end (because we are annotating the controllers) latency in percentiles of the incoming http requests. I would say that this is a very good starting point.

- **Count Errors** : For any other API errors which you want to monitor - use custom error counts like below. So every time an error is encountered, the error count is increased and you can set an alert which can be triggered when the error count crosses a daily threshold. But please note that in order ro enable this metrics, you will have to exclusively enable this tag first.      
{% highlight ruby %}
Counter apiErrors = meterRegistry.counter(“api.errors", tags);
apiErrors.increment();
{ endhighlight }  
- **Time critical operations** : Also apart from timing the controllers, if you also want to monitor the latency of some important time taking methods - consider using the @Timer annotation like this
{% highlight ruby %}
Timer apiTimer = meterRegistry.timer(“api.timers”, tags);
apiTimer.record ()
{ endhighlight }  

- **Effective Alerting** : Following are 2 effective alerting strategies in production and you can employ any one of them based on convenience:
  - Monitoring critical error counts as mentioned above and triggering the alert when the daily count crosses a threshold
  - Only error truly technical log message in production and monitor the logbackk events and you can also trigger an alert when the count of logbook events cross a threshold
