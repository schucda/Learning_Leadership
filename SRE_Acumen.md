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

* **Evernote's SLO Story**
 * Evernote had a desire to increase engineering velocity and maintain quality.
 
 * Goals:
  * Eliminate undifferentiated heavy lifting... Move away from datacenters to public cloud. The heavy lifting of maintaining infrastrcture and data centers was not a diferentiator for the company.
  * Improve the working model of Ops and Development.
  * Revamp how SLAs are used
 
 * **Why Adopt the SRE Model?**
  * Reasons are similiar to the story of DevOps... Dev and Ops teams are seperate, competing objectives - OPS: Stabality, Dev: New Features. These don't work well as new capabilites will introduce some stability issues, but if designed right you fail-forward and minimize the disruption.
  * **SRE doesn't necessarily mean that Ops and Dev are on the same team.** However it introduces languange and agreement that both ops and dev can relate to and a common goal. You still have ops and dev engineers. By using error budgets /SLO both teams make similiar decisions when presented with the same information. Removes subjectivity.
  * SLO will change, its not a set and forget. Evernote went through 3 versions of their SLOs in 9 months.
  * SLOs should be started from customer point of view *What promise are you trying to uphold?*
  * Not going to write a lot of notes, for examples of how they defined the SLO go back to the [book](https://landing.google.com/sre/workbook/chapters/slo-engineering-case-studies/).
  * What you need:
    * Definition of the SLO
    * What to measure and how
    * How to calculate SLOs from the data we measure *Maintenace for Evernote is considered downtime*
  * SLOs are used to focus what work needs to be done. Can we do new stuff or do we need to focus on improvements, bug-fix and other technical debt. **Guiding principle - "Perfect is the enemy of good"**
  * SLOs won't cover everything, so they won't be perfect. 
  * Don't change SLOs too frequently. You dont want them to go stale, but you cant constantly change. Evernote uses a 6-month time period to review and adjust SLOs.
  * **With GCP, the SLOs are shared and the customer helps Google understand where to focus to acheive the customers reliability needs**
  * **Just cause a cloud provider offers a 99.95% reliability and their measures across 100's of thousands of servers is green that doesnt mean our SLO is good. Customers have a much smaller footprint and a regional impact that might not hurt the cloud SLO could hurt the customer SLO. By sharing this, the provider can then report out specifics about your environment SLO.

* **Home Depot SLO Story**
 * Moved to a full stack ownership model based on a "freedom and responsibility culture". This means that developers can push code when they want, but they are jointly responsible for availability along with the ops team. 
 * The team must understand and know things like, service reliability (how many 9's is the service built for?, what is the upperbound latency?, Can you handle my volume, how do you handle overload and what is your SLO measurement over time?)
 * *If every service could provide transparent and consistent answers to these questions, teams would have a clear view into their dependencies, which allows for better communication and increased trust and accountability between teams.*
 * To build reliable services, a common culture of SLO is needed. THis requires an overarching strategy to influence people, process and technology. Home Depots effort spanned four areas:
  * Common Vernaculat - Define SLOs in the context of the company and define how to consistently measure them
  * Evangelism - Tell people why its good
  * Automation - Develop an easy to consume solution for measuring SLIs which can later be wrapped into the SLO
  * Incentive - Establish goals for your leaders to be held accountable to and rewarded.
  
 * You will find that a lot of teams are already measuring the right things from the Google Golden Four, but they are not discussed in a consistent way, arent related to each other and have inssuficent data.

 * Home Depot's first set of SLOs:
  * Availability and latency for API calls
  * Infrastructure utilization - no SLO for this, measured for capacity planning only
  * Traffic volume - measure things like connections per second
  * Errors
   * Errors were somewhat complicated to account for. Since we were primarily dealing with web services, we had to standardize what constitutes an error and how to return errors. If a web service encountered an error, we naturally standardized on HTTP response codes:

   * A service should not indicate an error in the body of a 2xx response; rather, it should throw either a 4xx or a 5xx.
   * An error caused by a problem with the service (for example, out of memory) should throw a 5xx error.
   * An error caused by the client (for example, sending a malformed request) should throw a 4xx error.
   * After much deliberation, we decided to track both 4xx and 5xx errors, but used 5xx errors only to set SLOs. Similar to our approach for other SLO-related elements, we kept this dimension generic so that different applications could leverage it for different contexts. For example, in addition to HTTP errors, errors for a batch processing service might be the number of records that failed to process.
  * Tickets
 
 * SLOs form acronym Valet
  * VALET - We summed up our new SLOs into a handy acronym: VALET.

    * Volume (traffic) - How much business volume can my service handle?
    * Availability - Is the service up when I need it?
    * Latency - Does the service respond fast when I use it?
    * Errors - Does the service throw an error when I use it?
    * Tickets - Does the service require manual intervention to complete my request?
 * Home Depot aurtomated collection and reporting, see article
 * Home Depot built the Vallet dashboard
 
 * Applying VALET to Batch Applications - As we developed robust reporting around SLOs, we discovered some additional uses for VALET. With a little adjusting, batch applications can fit into this framework as follows:

  * Volume - The volume of records processed
  * Availability - How often (as a percentage) the job completed by a certain time
  * Latency - The amount of time it takes for the job to run
  * Errors - The records that failed to process
  * Tickets - The number of times an operator has to manually fix data and reprocess a job
  
 * When ready to execute, go back to article for reference, too many notes to capture...
 
 
 
  
  
 
    
