# ADR: Choosing Between OLAP and Data Warehouse for Clearview Platform

## Status
Accepted

## Context
The Clearview platform needs to provide analytics for both platform administrators and employers. Platform administrators require analytics to generate reports on system-wide metrics like the number of candidates hired, demographic statistics, employer activity, and time-to-hire etc. These metrics do not require real-time processing and can be generated periodically. On the other hand, employers may want real-time insights into their specific data, such as job engagement and candidate activity. 

Using a separate system for each (OLAP for employers and Data Warehouse for platform admins) would introduce unnecessary complexity and cost. Therefore, a single solution must be selected that provides both periodic batch analytics for platform admins and the option for near-real-time insights when necessary.

### Alternatives
1. **OLAP (Looker + BigQuery)** for both platform and employer analytics.
2. **BigQuery Data Warehouse** for both platform and employer analytics.

### PrOACT

| Criteria                       | OLAP with Looker + BigQuery                              | BigQuery Data Warehouse                                          | Clearview Requirement                                                                                        |
|---------------------------------|---------------------------------------------------------|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| **Real-Time Analytics**         | Near-real-time analytics for both platform admin and employers. | Primarily suited for batch analytics, can support near-real-time with streaming. | Real-time analytics is not required platform-wide, but is needed for employers' data. OLAP provides better real-time insights. |
| **Cost Efficiency**             | More expensive due to real-time processing for all queries. | More cost-effective, especially for batch analytics.            | Cost-efficiency is key, and batch analytics for platform admins will reduce costs.                            |
| **Complexity**                  | Simpler for real-time analytics but adds complexity for batch reports. | Simpler for batch processing, more complex for real-time insights. | Complexity must be minimized; employers need occasional real-time analytics but platform-wide analytics can be batch. |
| **Scalability**                 | Highly scalable for real-time and multidimensional queries. | Scales well for batch analytics, can handle large datasets.      | Scalability is important, but real-time processing should be limited to reduce costs.                          |
| **Integration with Logs**       | Integrates well with real-time log-based metrics.        | Integrates with logs for batch and some real-time processing.    | Log-based metrics will be useful, especially for employer insights (real-time and batch).                     |
| **Reporting & Dashboards**      | Provides interactive, real-time dashboards for all users. | Provides dashboards, primarily batch-oriented, with options for near-real-time. | Employers need interactive dashboards for near-real-time data; platform admin reports can be batch-generated.  |
| **Data Freshness**              | Always up-to-date with near-real-time capabilities.      | Freshness depends on streaming or batch setup.                   | Platform-wide reports can be slightly delayed, but employer insights should be as fresh as possible.           |
| **Cost Control**                | More difficult to control costs due to real-time processing. | Easier to control costs with batch and occasional streaming.     | Cost control is a major concern, and batch processing is more economical for platform-wide analytics.           |

### Decision
**BigQuery Data Warehouse** will be used for both platform-wide analytics and employer-specific insights. While OLAP provides strong real-time capabilities, it introduces additional costs that are not justified given Clearview’s need for cost efficiency. BigQuery's batch processing capabilities will handle platform-wide analytics efficiently, and its ability to support streaming allows it to meet the real-time needs of employers where necessary.

### Trade-offs
- **Real-Time Limitations**: Employers may not receive immediate real-time data, but near-real-time insights can be provided with streaming mechanisms in BigQuery.
- **Complex Queries**: Complex, multidimensional queries for real-time insights may require careful optimization, but BigQuery supports most of these operations with proper setup.
- **Cost**: Using BigQuery’s batch-oriented system will help manage costs, but adding streaming for real-time insights for employers may slightly increase costs.

### Mitigation Strategies
- **Optimized Streaming**: Use streaming inserts for employers that need real-time insights, but limit their use to critical areas to reduce costs.
- **Scheduled Queries**: Set up periodic batch queries for platform-level analytics, allowing platform admins to have up-to-date information without real-time processing costs.
- **Monitoring and Tuning**: Monitor query usage and performance in BigQuery to ensure that costs and performance are optimized, especially for near-real-time use cases.

### References
- https://cloud.google.com/bigquery
- https://cloud.google.com/solutions/bigquery-real-time-analytics
