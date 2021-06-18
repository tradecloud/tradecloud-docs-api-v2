---
description: Tradecloud services and portal open pull requests and changelog (Fri Jun 18 17:30:43 CEST 2021)
---


## Open Pull Requests

1. [TC-7135](https://tradecloud.atlassian.net/browse/TC-7135) BE: authorize for (re)assigning a contact to an order 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2021 17:27:03 CEST | [#1531](https://github.com/tradecloud/tradecloud-microservices/pull/1531) |  authorize user for reassigning contacts | @OlehVasylyshyn |  |

2. [TC-6585](https://tradecloud.atlassian.net/browse/TC-6585) As a supplier I want to download a CSV file with only the data i&#39;m interested in of the orders.    [Planned release 05-Jul-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 18-Jun-2021 17:24:23 CEST | [#619](https://github.com/tradecloud/tradecloud-portal-angular/pull/619) |  add structure folders | @bohdantrc |  |

3. [TC-7097](https://tradecloud.atlassian.net/browse/TC-7097) Upgrade to latest ScalaTest so we can use PrettyPair 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2021 15:13:55 CEST | [#1538](https://github.com/tradecloud/tradecloud-microservices/pull/1538) |  Updated scalatest to 3.2.9 | @OlehVasylyshyn |  |

4. [TC-5667](https://tradecloud.atlassian.net/browse/TC-5667) As buyer I want to see order lines receive the logistical status &#39;&#39;Shipped&#39;&#39; when they have the status &#34;shipped&#34; in my ERP system.  [Planned release 07-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2021 15:09:32 CEST | [#1537](https://github.com/tradecloud/tradecloud-microservices/pull/1537) |  Add Shipped to incoming delivery line status | @marcmatt |  |

5. [TC-6828](https://tradecloud.atlassian.net/browse/TC-6828) As a buyer I want to reopen Completed lines.  [Planned release 24-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 18-Jun-2021 11:57:23 CEST | [#634](https://github.com/tradecloud/tradecloud-portal-angular/pull/634) | [TC-6961] add new integration group &#39;Contacts&#39; | @bohdantrc |  |

6. [TC-7064](https://tradecloud.atlassian.net/browse/TC-7064) As supplier I want to add an ETD (Estimated Time of Departure) when change delivery line statuses to Shipped. [Planned release 30-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2021 17:23:22 CEST | [#1536](https://github.com/tradecloud/tradecloud-microservices/pull/1536) |  [TC-7066] Add ETD to delivery line | @marcmatt |  |
| 2 | Services (Go) | 17-Jun-2021 15:35:19 CEST | [#405](https://github.com/tradecloud/tradecloud-microservices-go/pull/405) |  [TC-7066] Add ETD to delivery line | @marcmatt |  |

7. [TC-6974](https://tradecloud.atlassian.net/browse/TC-6974)  As Coulisse I want particular order lines to become proposals when accepted by the supplier [Planned release 28-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2021 16:03:42 CEST | [#1535](https://github.com/tradecloud/tradecloud-microservices/pull/1535) |  - propose when accepted  | @olegtradecloud |  |

8. [TC-7132](https://tradecloud.atlassian.net/browse/TC-7132) Support Base64-encoded documents in object-storage 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2021 14:55:14 CEST | [#1526](https://github.com/tradecloud/tradecloud-microservices/pull/1526) |  Support Base64-encoded documents in Object Storage | @roy-tc |  |

9. [TC-6958](https://tradecloud.atlassian.net/browse/TC-6958) As ERP system, I want to be updated via the webhook connector when a contact of an order is (re)assigned.   [Planned release 24-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Jun-2021 17:02:53 CEST | [#1533](https://github.com/tradecloud/tradecloud-microservices/pull/1533) |  updated messages dependency | @OlehVasylyshyn |  |
| 2 | Services (Go) | 16-Jun-2021 15:28:05 CEST | [#400](https://github.com/tradecloud/tradecloud-microservices-go/pull/400) |  Implemented webhook from reassigning contacts | @OlehVasylyshyn |  |

## Changelog

1. [TC-7000](https://tradecloud.atlassian.net/browse/TC-7000) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 17-Jun-2021 21:29:06 CEST | [#406](https://github.com/tradecloud/tradecloud-microservices-go/pull/406) |  Update golangci-lint to 1.41.0 | @vovinacci |  |
| 2 | Services (Go) | 09-Jun-2021 09:14:33 CEST | [#399](https://github.com/tradecloud/tradecloud-microservices-go/pull/399) |  Add bash to the requirements | @vovinacci |  |
| 3 | Web Portal | 08-Jun-2021 15:50:46 CEST | [#629](https://github.com/tradecloud/tradecloud-portal-angular/pull/629) |  Add dependabot config to ignore highcharts | @roy-tc |  |
| 4 | Web Portal | 07-Jun-2021 18:54:19 CEST | [#626](https://github.com/tradecloud/tradecloud-portal-angular/pull/626) |  Dummy changes to trigger build | @denys-kondartiuk |  |
| 5 | Web Portal | 07-Jun-2021 14:01:11 CEST | [#625](https://github.com/tradecloud/tradecloud-portal-angular/pull/625) |  Investigate build issue: Clean up docker images after build | @denys-kondartiuk |  |

2. [TC-6828](https://tradecloud.atlassian.net/browse/TC-6828) As a buyer I want to reopen Completed lines.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2021 15:10:56 CEST | [#1523](https://github.com/tradecloud/tradecloud-microservices/pull/1523) |  Revert completed order lines | @roy-tc |  |
| 2 | Web Portal | 17-Jun-2021 15:10:49 CEST | [#628](https://github.com/tradecloud/tradecloud-portal-angular/pull/628) | [TC-6831] add new activity type &#39;completed-order-line-reverted-by-buyer&#39; | @bohdantrc |  |
| 3 | Services (Go) | 17-Jun-2021 15:04:29 CEST | [#398](https://github.com/tradecloud/tradecloud-microservices-go/pull/398) |  Add support for sending OutgoingCompletedOrderLinesRevertedByBuyer | @roy-tc |  |
| 4 | Services (Scala) | 04-Jun-2021 12:33:00 CEST | [#1524](https://github.com/tradecloud/tradecloud-microservices/pull/1524) |  Refactor the OrderSentByBuyerSplitting | @roy-tc |  |

3. [TC-7155](https://tradecloud.atlassian.net/browse/TC-7155) Some lines do not have a `deliverySchedule` after the release of &#34;basic logistical status&#34; 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Jun-2021 19:38:46 CEST | [#1534](https://github.com/tradecloud/tradecloud-microservices/pull/1534) |  Add basic logistics model.OrderLine snapshot JIT migration | @marcmatt |  |

4. [TC-7145](https://tradecloud.atlassian.net/browse/TC-7145) Make sure TC-6733 is available in accp &amp; prod 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2021 17:53:22 CEST | [#633](https://github.com/tradecloud/tradecloud-portal-angular/pull/633) |  Refresh Docker image build and publish process | @vovinacci |  |
| 2 | Web Portal | 16-Jun-2021 13:37:03 CEST | [#632](https://github.com/tradecloud/tradecloud-portal-angular/pull/632) |  Refresh Docker image build and publish process, add docker image labels | @vovinacci |  |

5. [TC-700](https://tradecloud.atlassian.net/browse/TC-700) Migrate to ZeroMQ 3 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 17-Jun-2021 21:29:06 CEST | [#406](https://github.com/tradecloud/tradecloud-microservices-go/pull/406) |  Update golangci-lint to 1.41.0 | @vovinacci |  |
| 2 | Services (Go) | 16-Jun-2021 10:25:24 CEST | [#404](https://github.com/tradecloud/tradecloud-microservices-go/pull/404) |  Don&#39;t always tag docker with latest tag | @vovinacci |  |
| 3 | Services (Go) | 09-Jun-2021 09:14:33 CEST | [#399](https://github.com/tradecloud/tradecloud-microservices-go/pull/399) |  Add bash to the requirements | @vovinacci |  |
| 4 | Web Portal | 08-Jun-2021 15:50:46 CEST | [#629](https://github.com/tradecloud/tradecloud-portal-angular/pull/629) |  Add dependabot config to ignore highcharts | @roy-tc |  |
| 5 | Web Portal | 07-Jun-2021 18:54:19 CEST | [#626](https://github.com/tradecloud/tradecloud-portal-angular/pull/626) |  Dummy changes to trigger build | @denys-kondartiuk |  |
| 6 | Web Portal | 07-Jun-2021 14:01:11 CEST | [#625](https://github.com/tradecloud/tradecloud-portal-angular/pull/625) |  Investigate build issue: Clean up docker images after build | @denys-kondartiuk |  |

6. [TC-6949](https://tradecloud.atlassian.net/browse/TC-6949) As portal user, I want to (Re)assign orders to users  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2021 09:53:28 CEST | [#623](https://github.com/tradecloud/tradecloud-portal-angular/pull/623) | [TC-6952] add assign and reassign logic | @bohdantrc |  |
| 2 | Services (Scala) | 15-Jun-2021 14:10:37 CEST | [#1532](https://github.com/tradecloud/tradecloud-microservices/pull/1532) |  message dependecy version fix | @OlehVasylyshyn |  |
| 3 | Services (Scala) | 15-Jun-2021 13:13:23 CEST | [#1518](https://github.com/tradecloud/tradecloud-microservices/pull/1518) |  (Re)assign orders to users | @OlehVasylyshyn |  |

7. [TC-7059](https://tradecloud.atlassian.net/browse/TC-7059) acknowledge &amp; conversation tasks are not reassigned when the contact of the related order header is updated.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Jun-2021 12:16:33 CEST | [#1520](https://github.com/tradecloud/tradecloud-microservices/pull/1520) |  - update task contact | @olegtradecloud |  |

8. [TC-6316](https://tradecloud.atlassian.net/browse/TC-6316) Add support of starting buf check locally 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Jun-2021 11:58:16 CEST | [#1513](https://github.com/tradecloud/tradecloud-microservices/pull/1513) |  Support running buf breaking changes locally | @roy-tc |  |

9. [TC-6941](https://tradecloud.atlassian.net/browse/TC-6941) As buyer I want that suppliers can set logistical status using the portal - BASIC  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 14-Jun-2021 16:24:29 CEST | [#631](https://github.com/tradecloud/tradecloud-portal-angular/pull/631) |  fix typo | @bohdantrc |  |
| 2 | Services (Go) | 14-Jun-2021 16:22:02 CEST | [#402](https://github.com/tradecloud/tradecloud-microservices-go/pull/402) |  [TC-7098] Fix deliverySchedule copy-pasta | @marcmatt |  |
| 3 | Services (Scala) | 13-Jun-2021 22:42:25 CEST | [#1529](https://github.com/tradecloud/tradecloud-microservices/pull/1529) |  Touch user service | @marcmatt |  |
| 4 | Web Portal | 11-Jun-2021 15:53:56 CEST | [#605](https://github.com/tradecloud/tradecloud-portal-angular/pull/605) |  basic delivery line logistics | @bohdantrc |  |
| 5 | Services (Go) | 11-Jun-2021 15:53:43 CEST | [#396](https://github.com/tradecloud/tradecloud-microservices-go/pull/396) |  [TC-7098] Basic delivery line logistics | @marcmatt |  |
| 6 | Services (Scala) | 11-Jun-2021 15:53:17 CEST | [#1483](https://github.com/tradecloud/tradecloud-microservices/pull/1483) |  Basic delivery line logistics | @marcmatt |  |

10. [TC-6693](https://tradecloud.atlassian.net/browse/TC-6693) As DevOps, I want to migrate Mesos based production environment to GCP, so that I have better platform availability 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 14-Jun-2021 09:36:40 CEST | [#401](https://github.com/tradecloud/tradecloud-microservices-go/pull/401) |  Remove double deployment | @vovinacci |  |
| 2 | Services (Scala) | 08-Jun-2021 13:29:55 CEST | [#1525](https://github.com/tradecloud/tradecloud-microservices/pull/1525) |  Add GCP deployment | @vovinacci |  |
| 3 | Web Portal | 08-Jun-2021 12:41:54 CEST | [#627](https://github.com/tradecloud/tradecloud-portal-angular/pull/627) |  Add GCP deployment | @vovinacci |  |
| 4 | Services (Go) | 08-Jun-2021 08:44:58 CEST | [#397](https://github.com/tradecloud/tradecloud-microservices-go/pull/397) |  Add GCP deployment | @vovinacci |  |

11. [TC-7144](https://tradecloud.atlassian.net/browse/TC-7144) GCP: post-migration cleanup 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jun-2021 09:36:21 CEST | [#1530](https://github.com/tradecloud/tradecloud-microservices/pull/1530) |  Remove double deployment | @vovinacci |  |
| 2 | Web Portal | 14-Jun-2021 09:23:36 CEST | [#630](https://github.com/tradecloud/tradecloud-portal-angular/pull/630) |  Remove double deployment | @vovinacci |  |

12. [TC-7029](https://tradecloud.atlassian.net/browse/TC-7029) As legacy customer I want that migrated legacy orders to only overwrite TC One orders when the order is not changed in TC One 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jun-2021 16:09:32 CEST | [#1509](https://github.com/tradecloud/tradecloud-microservices/pull/1509) |  added new field - origin | @OlehVasylyshyn |  |

13. [TC-6733](https://tradecloud.atlassian.net/browse/TC-6733) As a portal user, I want to see how many attempts I have left to login and see the time for how long I am banned if my last attempt failed.   
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jun-2021 10:46:45 CEST | [#624](https://github.com/tradecloud/tradecloud-portal-angular/pull/624) |  just change code for trigger rebuild | @bohdantrc |  |

14. [TC-7073](https://tradecloud.atlassian.net/browse/TC-7073) Stress test reindexing process 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jun-2021 09:46:26 CEST | [#1517](https://github.com/tradecloud/tradecloud-microservices/pull/1517) |  Unthrottle reindexing and increase parallelism | @roy-tc |  |

15. [TC-7104](https://tradecloud.atlassian.net/browse/TC-7104) Move Go shared package to the main repository 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 01-Jun-2021 14:44:54 CEST | [#395](https://github.com/tradecloud/tradecloud-microservices-go/pull/395) |  Fix service name generation for non-test environments | @vovinacci |  |
| 2 | Services (Go) | 01-Jun-2021 14:19:21 CEST | [#393](https://github.com/tradecloud/tradecloud-microservices-go/pull/393) |  Reorganise Go code | @vovinacci |  |

16. [TC-7106](https://tradecloud.atlassian.net/browse/TC-7106) QA: Investigate flaky `test_order_resend_by_buyer_webhook_and_activity` 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 31-May-2021 14:24:08 CEST | [#394](https://github.com/tradecloud/tradecloud-microservices-go/pull/394) |  Fix &#39;webhook is not enabled&#39; error for Supplier webhooks | @vovinacci |  |

17. [TC-7101](https://tradecloud.atlassian.net/browse/TC-7101) Account code misaligned and edit button partial visible on network page using Firefox. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 31-May-2021 13:37:08 CEST | [#622](https://github.com/tradecloud/tradecloud-portal-angular/pull/622) |  fix cell align for connection table | @bohdantrc |  |

18. [TC-6883](https://tradecloud.atlassian.net/browse/TC-6883) Save if an search box or filter box in the portal is folded or unfolded.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 31-May-2021 13:31:09 CEST | [#620](https://github.com/tradecloud/tradecloud-portal-angular/pull/620) |  add expand store and selectors for tracking expanded panels | @bohdantrc |  |

19. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 31-May-2021 10:14:40 CEST | [#621](https://github.com/tradecloud/tradecloud-portal-angular/pull/621) | Bump dns-packet from 1.3.1 to 1.3.4 | @dependabot[bot] |  |
| 2 | Web Portal | 26-May-2021 14:44:24 CEST | [#618](https://github.com/tradecloud/tradecloud-portal-angular/pull/618) | Bump browserslist from 4.13.0 to 4.16.6 | @dependabot[bot] |  |

20. [TC-6431](https://tradecloud.atlassian.net/browse/TC-6431) Webhook POST body contains JSON numbers with quotes 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 27-May-2021 17:20:33 CEST | [#390](https://github.com/tradecloud/tradecloud-microservices-go/pull/390) |  Refactor Protobuf to JSON serialisation | @vovinacci |  |

21. [TC-7096](https://tradecloud.atlassian.net/browse/TC-7096) Use LOCAL_QUORUM for Scala persisted services 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 27-May-2021 10:44:36 CEST | [#1515](https://github.com/tradecloud/tradecloud-microservices/pull/1515) |  Use LOCAL_QUORUM to use C* nodes from LOCAL DC only | @roy-tc |  |

22. [TC-7081](https://tradecloud.atlassian.net/browse/TC-7081) Incoming order without lines is silently ignored and not persisted. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 24-May-2021 18:04:03 CEST | [#1511](https://github.com/tradecloud/tradecloud-microservices/pull/1511) |  - issue order without lines fix | @olegtradecloud |  |

23. [TC-6957](https://tradecloud.atlassian.net/browse/TC-6957) As Eichholtz (GAC) I want to cancel lines by removing them from the order update 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 21-May-2021 11:14:46 CEST | [#1505](https://github.com/tradecloud/tradecloud-microservices/pull/1505) |  - cancel missing lines | @olegtradecloud |  |

24. [TC-7036](https://tradecloud.atlassian.net/browse/TC-7036) As Exact Globe integrator I need migrated Exact Globe delivery schedule position to be set to the line position. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-May-2021 19:08:09 CEST | [#1508](https://github.com/tradecloud/tradecloud-microservices/pull/1508) |  Delivery position for ExactGlobeCustomers from line code | @OlehVasylyshyn |  |

25. [TC-6789](https://tradecloud.atlassian.net/browse/TC-6789) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-May-2021 18:37:17 CEST | [#1514](https://github.com/tradecloud/tradecloud-microservices/pull/1514) |  Remove unsupported imgix parameters | @marcmatt |  |

26. [TC-6213](https://tradecloud.atlassian.net/browse/TC-6213)  Connection can be requested to company itself 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-May-2021 17:47:26 CEST | [#1507](https://github.com/tradecloud/tradecloud-microservices/pull/1507) |  Connection to company itself | @OlehVasylyshyn |  |

27. [TC-6882](https://tradecloud.atlassian.net/browse/TC-6882) UAT: Verify an acknowledge task results in a contact notification 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-May-2021 17:21:29 CEST | [#1510](https://github.com/tradecloud/tradecloud-microservices/pull/1510) |  Add optional UserSettings to AddUser super user API | @marcmatt |  |

28. [TC-7058](https://tradecloud.atlassian.net/browse/TC-7058) The portal shows be default 2 decimals (.00) when the priceUnitQuantity ≠ 1 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-May-2021 16:42:34 CEST | [#617](https://github.com/tradecloud/tradecloud-portal-angular/pull/617) |  allow format 10-&gt;10 instead of 10-&gt;10.00 | @bohdantrc |  |

