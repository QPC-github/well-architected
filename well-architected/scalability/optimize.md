---
title: Optimize scalability and reliability of cloud applications
description: Learn how to determine options for improvement based on the monitored data.
author: PageWriter-MSFT
ms.author: martinek
ms.date: 4/28/2023
ms.topic: conceptual
categories:
  - management-and-governance
ms.custom:
  - fasttrack-edit
---
# Optimize for scalability and reliability

Resolving performance issues requires time and patience&mdash;not just in discovery and investigation, but also in resolution. Code enhancements might be accomplished by deploying a new build, but enhancements to infrastructure might involve many teams. Some services might require updated configurations while others might need to be deprecated in favor of more-appropriate solutions. Regardless, it's critical that you understand the scope of your planned resolution so that all necessary stakeholders are informed.

## Checklist
>
> [!div class="checklist"]
>
> - Use caching whenever possible, whether it is client-side caching, view caching, or data caching.
> - Partition data to optimize performance, improve scalability, and reduce contention by lowering the taxation of database operations.
> - Prevent a system from attempting to scale out excessively. Gracefully degrading the functionality that the system provides if the maximum number of instances have been deployed, and the system is still overloaded.
> - Improve the reliability of your workloads by implementing high availability, disaster recovery, backup, and monitoring in Azure.

## In this section

Follow these questions to assess the workload at a deeper level.

|Assessment|Description|
|---|---|
|[**Has caching and queuing been considered to handle varying load?**](optimize-cache.md)|Caching and queuing offers ways to handle heavy load in read and write scenarios, respectively. However, their usage must be carefully considered as caching might mean that data isn't fresh and writes don't happen instantly. Older data could create a scenario of eventual consistency and stale data.|
|[**Are you using database replicas and data partitioning?**](optimize-partition.md)|Collect platform metrics and logs to get visibility into the health and performance of services that are part of the architecture.|
|[**Has autoscaling been tested under sustained load?**](optimize-sustain.md)|Implement a unified solution to aggregate and query application and resource level logs, such as Azure Log Analytics.|
|[**Are the right sizes and SKUs used for workload services?**](design-capacity.md#choose-the-right-resources)|The required performance and infrastructure utilization are key factors that define the 'size' of Azure resources to be used, but there can be hidden aspects that affect cost too. After the purchased SKUs have been identified, determine if they purchased resources have the capabilities of supporting anticipated load.|
|[**Is the application implemented with strategies for resiliency and self-healing?**](performance-efficiency-patterns.md)|Consider implementing strategies and capabilities for resiliency and self-healing needed to achieve workload availability targets. Programming paradigms such as retry patterns, request timeouts, and circuit breaker patterns can improve application resiliency by automatically recovering from transient faults.|

## Capacity considerations

- **Technology & SKU service limits:** For disaster recovery, it's important that you choose [_paired regions_](/azure/best-practices-availability-paired-regions) for deploying your application. Paired regions ensure that your application operates at maximum uptime. Additionally, it's critical that your chosen regions support the necessary service SKUs and limits to support load if one region should fail. If a single region fails, your services should be able to scale to the appropriate levels for accommodating increased demand from the rerouted requests. Your performance testing should occasionally include testing during a simulated failover to ensure application efficiency under those conditions. If it's determined that a service's limits in a single region can't support the increased load, more services should be deployed in your regions, or other regions should be added to your load balancer.

- **SLAs:** When determining which services to use within your application, you should also consider the SLAs of those services as their SLAs can affect your application's performance. When the _functional_ capabilities of two services overlap, then the SLAs of those services could be the determining factor behind why one is chosen over the other.

- **Costs:** Costs can be another factor in performance efficiency. Surprisingly, however, greater costs don't necessarily always mean increased performance. But, when observing how close your application comes to meeting business KPIs, you must consider how much improvement is realized in the application if costs are increased. Then, you must evaluate if the cost-benefit is worth the investment. Sometimes, small changes in the application logic, caching, or adding an index to a database can dramatically improve performance while not affecting costs whatsoever (certain improvements can even help reduce costs).

## Next section

Compare your code to proven architectures. By referencing the design patterns, you can avoid common mistakes by developers who are deploying applications into the cloud. Finally, you might consider other Azure services that might be more appropriate for your objectives. While Azure has many services that seem to overlap in capabilities, often there are specific use-cases for which the services are designed.

> [!div class="nextstepaction"]
> [Performance Efficiency patterns](performance-efficiency-patterns.md)

## Related links
>
> [Back to the main article](overview.md)
