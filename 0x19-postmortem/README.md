Postmortem: Web Stack Outage

Issue Summary

- Duration: 2 hours 15 minutes (14:00 - 16:15 UTC-7)
- Impact: 30% of users experienced slow loading times and errors on our e-commerce platform, resulting in a significant increase in support tickets and a revenue loss of $10,000

Timeline

- 14:00 - Issue detected by monitoring alert for high latency on our API gateway
- 14:05 - Engineer noticed high CPU usage on the affected servers
- 14:10 - Initial investigation focused on database performance, assuming a query optimization issue
- 14:30 - Misleading path: Investigation shifted to network congestion, delaying the root cause identification
- 15:00 - Escalated to senior engineer and DevOps team for assistance
- 15:45 - Root cause identified: Memory leak in Nginx server due to a recent configuration change
- 16:15 - Issue resolved by rolling back the configuration change and implementing a temporary fix

Root Cause and Resolution

The root cause was a memory leak in the Nginx server, triggered by a recent configuration change. The leak caused the server to consume excessive memory, leading to slow loading times and errors. The issue was resolved by rolling back the configuration change and implementing a temporary fix to limit memory usage.

Corrective and Preventative Measures

- Improve configuration change review process to catch potential issues
- Add monitoring for server memory usage
- Implement automated rollbacks for failed configuration changes
- Schedule a task to patch Nginx server with a permanent fix
- Review and optimize database queries to prevent similar issues

This postmortem highlights the importance of swift detection, accurate investigation, and effective communication during outages. By addressing the identified corrective and preventative measures, we can minimize the likelihood and impact of similar incidents in the future.
https://github.com/MROH/alx-system_engineering-devops/tree/master/0x0E-web_stack_debugging_1
