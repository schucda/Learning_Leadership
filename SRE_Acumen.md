Increase SRE Acumen

**Tasks:**
- [x] [Google SRE - 4 Golden Signals/Metrics](https://victorops.com/blog/sre-golden-signals-of-monitoring)
- [ ] [SLO Engineering Case Studies, includes Home Depot SLO Story](https://landing.google.com/sre/workbook/chapters/slo-engineering-case-studies/)
- [ ] [One Stop Shop for SRE](https://github.com/dastergon/awesome-sre/blob/master/README.md)
- [ ] [Nick Shine SRE Conference Report](https://www.yammer.com/statefarm.com/threads/411541455986688)
- [ ] [Google Engineer SRE Conference](https://www.youtube.com/watch?v=c-w_GYvi0eA)
- [ ] [Site Reliability vs. DevOps](https://cloud.google.com/blog/products/gcp/sre-vs-devops-competing-standards-or-close-friends?source=post_page-----40b823b18e08----------------------&m=1)
- [ ] [Google - Implementing SLOs](https://landing.google.com/sre/workbook/chapters/how-sre-relates/)
- [ ] [DevOps Days Chicago 2019 - SRE](https://www.youtube.com/watch?v=fWvNzDVOJDE)
- [ ] [Chaos Engineering](https://victorops.com/blog/chaos-engineering/)
- [ ] [Game Days](https://victorops.com/blog/september-roundup-a-gameday-recap)
- [ ] [Synthetic Monitoring](https://en.wikipedia.org/wiki/Synthetic_monitoring)

**Notes**

**4 Golden Signals**
* According to SRE's Wikipedia entry, SRE is what happens when a software engineer is tasked with what used to be called operations. Basically, development teams need to monitor the services they are dependent on in order to ensure they build a reliable solution.
*  The four golden signals:
  * **Latency:** How long does it take to service a request? Define a benchmark for the latency associated with successful requests and monitor that against the latency of failed requests. Tracking the latency of errors allows you to address any concerns around the speed of identifying an incident and how quickly you can dive into incident response.

  * **Traffic:** Traffic is fairly self-explanatory. How much stress is your system taking on from the number of users or transactions running through your service? Depending on the functionality of your service, measuring traffic can look quite different from company to company. By monitoring real-user interactions and traffic you can better understand the way end-users experience your service and create visibility into how your systems hold up under stress.

  * **Errors:** Of course, every team needs to monitor for errors. Whether those errors are defined based on manually defined logic or they’re explicit errors such as a failed HTTP request, SRE teams need to monitor for them. Many SRE teams use incident management software to alert on critical errors, take action to identify why an error is happening, and work toward incident remediation.

  * **Saturation:** Every team needs to monitor the utilization of their system. It’s important for SRE teams to define a metric for saturation that means the service is maxed out. Most services start to degrade before utilization hits 100%, so understanding the functionality of your own system is important to defining a saturation benchmark that makes sense.

* Getting the right monitoring in place is great and you can build on it as you mature. The next step is to introduce things like **Chaos Engineering** - break things and see how the system responds, **Game Days** - simulate events and challenge your team, determine how you can improve and **Synthetic Monitoring** - Simulating traffic to test services.

**SLO Engineering Case Studies**

*