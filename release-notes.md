---
description: Tradecloud services and portal open pull requests and changelog (Mon Jun 28 19:30:38 CEST 2021)
---


## Open Pull Requests

1. [TC-7148](https://tradecloud.atlassian.net/browse/TC-7148) Sequence number [1] still missing after [10.00 s], saw unexpected seqNr [21] for persistenceId 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jun-2021 10:43:31 CEST | [#1542](https://github.com/tradecloud/tradecloud-microservices/pull/1542) |  DO NOT MERGE Trigger build | @roy-tc |  |

2. [TC-7135](https://tradecloud.atlassian.net/browse/TC-7135) BE: authorize for (re)assigning a contact to an order 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-Jun-2021 17:23:51 CEST | [#1531](https://github.com/tradecloud/tradecloud-microservices/pull/1531) |  authorize user for reassigning contacts | @OlehVasylyshyn |  |

3. [TC-6958](https://tradecloud.atlassian.net/browse/TC-6958) As ERP system, I want to be updated via the webhook connector when a contact of an order is (re)assigned.   [Planned release 24-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 25-Jun-2021 15:31:31 CEST | [#400](https://github.com/tradecloud/tradecloud-microservices-go/pull/400) |  Implemented webhook from reassigning contacts | @OlehVasylyshyn |  |
| 2 | Services (Scala) | 24-Jun-2021 16:37:12 CEST | [#1533](https://github.com/tradecloud/tradecloud-microservices/pull/1533) |  enrichment in Company service for reassigning contacts flow | @OlehVasylyshyn |  |

4. [TC-6585](https://tradecloud.atlassian.net/browse/TC-6585) As a supplier I want to download a CSV file with only the data i&#39;m interested in of the orders.    [Planned release 05-Jul-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-Jun-2021 14:24:02 CEST | [#619](https://github.com/tradecloud/tradecloud-portal-angular/pull/619) |  add structure folders | @bohdantrc |  |

5. [TC-7100](https://tradecloud.atlassian.net/browse/TC-7100) As a buyer integrator I want to merge a new buyer delivery schedule position into the order line &amp; confirmed delivery schedule&#39;s 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 24-Jun-2021 13:26:25 CEST | [#1540](https://github.com/tradecloud/tradecloud-microservices/pull/1540) |  Merge incoming delivery schedule | @marcmatt |  |

6. [TC-7064](https://tradecloud.atlassian.net/browse/TC-7064) As supplier I want to add an ETD (Estimated Time of Departure) when change delivery line statuses to Shipped. [Planned release 30-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 23-Jun-2021 15:14:28 CEST | [#637](https://github.com/tradecloud/tradecloud-portal-angular/pull/637) |  [TC-7067] Add ETD | @marcmatt |  |
| 2 | Services (Scala) | 17-Jun-2021 17:23:22 CEST | [#1536](https://github.com/tradecloud/tradecloud-microservices/pull/1536) |  [TC-7066] Add ETD to delivery line | @marcmatt |  |
| 3 | Services (Go) | 17-Jun-2021 15:35:19 CEST | [#405](https://github.com/tradecloud/tradecloud-microservices-go/pull/405) |  [TC-7066] Add ETD to delivery line | @marcmatt |  |

7. [TC-5667](https://tradecloud.atlassian.net/browse/TC-5667) As buyer I want to see order lines receive the logistical status &#39;&#39;Shipped&#39;&#39; when they have the status &#34;shipped&#34; in my ERP system.  [Planned release 07-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Jun-2021 11:03:16 CEST | [#1537](https://github.com/tradecloud/tradecloud-microservices/pull/1537) |  Add Shipped to incoming delivery line status | @marcmatt |  |

8. [TC-6828](https://tradecloud.atlassian.net/browse/TC-6828) As a buyer I want to reopen Completed lines.  [Planned release 24-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 21-Jun-2021 09:00:45 CEST | [#634](https://github.com/tradecloud/tradecloud-portal-angular/pull/634) | [TC-6961] add new integration group &#39;Contacts&#39; | @bohdantrc |  |

## Changelog

1. [TC-7000](https://tradecloud.atlassian.net/browse/TC-7000) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jun-2021 14:02:18 CEST | [#1543](https://github.com/tradecloud/tradecloud-microservices/pull/1543) |  Use original user and company when transforming Activity to ActivityView | @roy-tc |  |
| 2 | Web Portal | 28-Jun-2021 14:02:06 CEST | [#641](https://github.com/tradecloud/tradecloud-portal-angular/pull/641) |  Use activity createdAt field | @roy-tc |  |
| 3 | Web Portal | 24-Jun-2021 21:53:50 CEST | [#639](https://github.com/tradecloud/tradecloud-portal-angular/pull/639) |  Fix sourcemap upload user | @vovinacci |  |
| 4 | Web Portal | 22-Jun-2021 10:27:53 CEST | [#635](https://github.com/tradecloud/tradecloud-portal-angular/pull/635) |  SSL: Remove HSTS headers | @vovinacci |  |
| 5 | Services (Go) | 17-Jun-2021 21:29:06 CEST | [#406](https://github.com/tradecloud/tradecloud-microservices-go/pull/406) |  Update golangci-lint to 1.41.0 | @vovinacci |  |
| 6 | Services (Go) | 09-Jun-2021 09:14:33 CEST | [#399](https://github.com/tradecloud/tradecloud-microservices-go/pull/399) |  Add bash to the requirements | @vovinacci |  |
| 7 | Web Portal | 08-Jun-2021 15:50:46 CEST | [#629](https://github.com/tradecloud/tradecloud-portal-angular/pull/629) |  Add dependabot config to ignore highcharts | @roy-tc |  |
| 8 | Web Portal | 07-Jun-2021 18:54:19 CEST | [#626](https://github.com/tradecloud/tradecloud-portal-angular/pull/626) |  Dummy changes to trigger build | @denys-kondartiuk |  |
| 9 | Web Portal | 07-Jun-2021 14:01:11 CEST | [#625](https://github.com/tradecloud/tradecloud-portal-angular/pull/625) |  Investigate build issue: Clean up docker images after build | @denys-kondartiuk |  |

2. [TC-7131](https://tradecloud.atlassian.net/browse/TC-7131) Increase support large request bodies in SCI Connector 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jun-2021 11:41:58 CEST | [#1539](https://github.com/tradecloud/tradecloud-microservices/pull/1539) |  Default document size limit to 256MB | @roy-tc |  |

3. [TC-7008](https://tradecloud.atlassian.net/browse/TC-7008) As portal user I want that TC maps SCSN unit codes to human readable unit names 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jun-2021 15:50:08 CEST | [#638](https://github.com/tradecloud/tradecloud-portal-angular/pull/638) |  add mapping unit code for purchaseUnitOfMeasureIso and prices | @bohdantrc |  |

4. [TC-7127](https://tradecloud.atlassian.net/browse/TC-7127) Later added lines do not trigger an &#34;await confirmation&#34; task  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-Jun-2021 14:11:14 CEST | [#1541](https://github.com/tradecloud/tradecloud-microservices/pull/1541) |  - fix workflow tasks on new lines issuing | @olegtradecloud |  |

5. [TC-7168](https://tradecloud.atlassian.net/browse/TC-7168) Update Certification UI  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-Jun-2021 15:25:49 CEST | [#636](https://github.com/tradecloud/tradecloud-portal-angular/pull/636) |  update showing certification fields | @bohdantrc |  |

6. [TC-6974](https://tradecloud.atlassian.net/browse/TC-6974)  As Coulisse I want particular order lines to become proposals when accepted by the supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 23-Jun-2021 16:34:09 CEST | [#1535](https://github.com/tradecloud/tradecloud-microservices/pull/1535) |  - propose when accepted  | @olegtradecloud |  |

7. [TC-7097](https://tradecloud.atlassian.net/browse/TC-7097) Upgrade to latest ScalaTest so we can use PrettyPair 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 23-Jun-2021 11:47:58 CEST | [#1538](https://github.com/tradecloud/tradecloud-microservices/pull/1538) |  Updated scalatest to 3.2.9 | @OlehVasylyshyn |  |

8. [TC-7132](https://tradecloud.atlassian.net/browse/TC-7132) Support Base64-encoded documents in object-storage 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 23-Jun-2021 08:16:49 CEST | [#1526](https://github.com/tradecloud/tradecloud-microservices/pull/1526) |  Support Base64-encoded documents in Object Storage | @roy-tc |  |

9. [TC-6828](https://tradecloud.atlassian.net/browse/TC-6828) As a buyer I want to reopen Completed lines.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2021 15:10:56 CEST | [#1523](https://github.com/tradecloud/tradecloud-microservices/pull/1523) |  Revert completed order lines | @roy-tc |  |
| 2 | Web Portal | 17-Jun-2021 15:10:49 CEST | [#628](https://github.com/tradecloud/tradecloud-portal-angular/pull/628) | [TC-6831] add new activity type &#39;completed-order-line-reverted-by-buyer&#39; | @bohdantrc |  |
| 3 | Services (Go) | 17-Jun-2021 15:04:29 CEST | [#398](https://github.com/tradecloud/tradecloud-microservices-go/pull/398) |  Add support for sending OutgoingCompletedOrderLinesRevertedByBuyer | @roy-tc |  |
| 4 | Services (Scala) | 04-Jun-2021 12:33:00 CEST | [#1524](https://github.com/tradecloud/tradecloud-microservices/pull/1524) |  Refactor the OrderSentByBuyerSplitting | @roy-tc |  |

10. [TC-7155](https://tradecloud.atlassian.net/browse/TC-7155) Some lines do not have a `deliverySchedule` after the release of &#34;basic logistical status&#34; 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Jun-2021 19:38:46 CEST | [#1534](https://github.com/tradecloud/tradecloud-microservices/pull/1534) |  Add basic logistics model.OrderLine snapshot JIT migration | @marcmatt |  |

11. [TC-7145](https://tradecloud.atlassian.net/browse/TC-7145) Make sure TC-6733 is available in accp &amp; prod 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2021 17:53:22 CEST | [#633](https://github.com/tradecloud/tradecloud-portal-angular/pull/633) |  Refresh Docker image build and publish process | @vovinacci |  |
| 2 | Web Portal | 16-Jun-2021 13:37:03 CEST | [#632](https://github.com/tradecloud/tradecloud-portal-angular/pull/632) |  Refresh Docker image build and publish process, add docker image labels | @vovinacci |  |

12. [TC-700](https://tradecloud.atlassian.net/browse/TC-700) Migrate to ZeroMQ 3 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jun-2021 14:02:18 CEST | [#1543](https://github.com/tradecloud/tradecloud-microservices/pull/1543) |  Use original user and company when transforming Activity to ActivityView | @roy-tc |  |
| 2 | Web Portal | 28-Jun-2021 14:02:06 CEST | [#641](https://github.com/tradecloud/tradecloud-portal-angular/pull/641) |  Use activity createdAt field | @roy-tc |  |
| 3 | Web Portal | 25-Jun-2021 15:50:08 CEST | [#638](https://github.com/tradecloud/tradecloud-portal-angular/pull/638) |  add mapping unit code for purchaseUnitOfMeasureIso and prices | @bohdantrc |  |
| 4 | Web Portal | 24-Jun-2021 21:53:50 CEST | [#639](https://github.com/tradecloud/tradecloud-portal-angular/pull/639) |  Fix sourcemap upload user | @vovinacci |  |
| 5 | Web Portal | 22-Jun-2021 10:27:53 CEST | [#635](https://github.com/tradecloud/tradecloud-portal-angular/pull/635) |  SSL: Remove HSTS headers | @vovinacci |  |
| 6 | Services (Go) | 17-Jun-2021 21:29:06 CEST | [#406](https://github.com/tradecloud/tradecloud-microservices-go/pull/406) |  Update golangci-lint to 1.41.0 | @vovinacci |  |
| 7 | Services (Go) | 16-Jun-2021 10:25:24 CEST | [#404](https://github.com/tradecloud/tradecloud-microservices-go/pull/404) |  Don&#39;t always tag docker with latest tag | @vovinacci |  |
| 8 | Services (Go) | 09-Jun-2021 09:14:33 CEST | [#399](https://github.com/tradecloud/tradecloud-microservices-go/pull/399) |  Add bash to the requirements | @vovinacci |  |
| 9 | Web Portal | 08-Jun-2021 15:50:46 CEST | [#629](https://github.com/tradecloud/tradecloud-portal-angular/pull/629) |  Add dependabot config to ignore highcharts | @roy-tc |  |
| 10 | Web Portal | 07-Jun-2021 18:54:19 CEST | [#626](https://github.com/tradecloud/tradecloud-portal-angular/pull/626) |  Dummy changes to trigger build | @denys-kondartiuk |  |
| 11 | Web Portal | 07-Jun-2021 14:01:11 CEST | [#625](https://github.com/tradecloud/tradecloud-portal-angular/pull/625) |  Investigate build issue: Clean up docker images after build | @denys-kondartiuk |  |

13. [TC-6949](https://tradecloud.atlassian.net/browse/TC-6949) As portal user, I want to (Re)assign orders to users  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2021 09:53:28 CEST | [#623](https://github.com/tradecloud/tradecloud-portal-angular/pull/623) | [TC-6952] add assign and reassign logic | @bohdantrc |  |
| 2 | Services (Scala) | 15-Jun-2021 14:10:37 CEST | [#1532](https://github.com/tradecloud/tradecloud-microservices/pull/1532) |  message dependecy version fix | @OlehVasylyshyn |  |
| 3 | Services (Scala) | 15-Jun-2021 13:13:23 CEST | [#1518](https://github.com/tradecloud/tradecloud-microservices/pull/1518) |  (Re)assign orders to users | @OlehVasylyshyn |  |

14. [TC-7059](https://tradecloud.atlassian.net/browse/TC-7059) acknowledge &amp; conversation tasks are not reassigned when the contact of the related order header is updated.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Jun-2021 12:16:33 CEST | [#1520](https://github.com/tradecloud/tradecloud-microservices/pull/1520) |  - update task contact | @olegtradecloud |  |

15. [TC-6316](https://tradecloud.atlassian.net/browse/TC-6316) Add support of starting buf check locally 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Jun-2021 11:58:16 CEST | [#1513](https://github.com/tradecloud/tradecloud-microservices/pull/1513) |  Support running buf breaking changes locally | @roy-tc |  |

16. [TC-6941](https://tradecloud.atlassian.net/browse/TC-6941) As buyer I want that suppliers can set logistical status using the portal - BASIC  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 14-Jun-2021 16:24:29 CEST | [#631](https://github.com/tradecloud/tradecloud-portal-angular/pull/631) |  fix typo | @bohdantrc |  |
| 2 | Services (Go) | 14-Jun-2021 16:22:02 CEST | [#402](https://github.com/tradecloud/tradecloud-microservices-go/pull/402) |  [TC-7098] Fix deliverySchedule copy-pasta | @marcmatt |  |
| 3 | Services (Scala) | 13-Jun-2021 22:42:25 CEST | [#1529](https://github.com/tradecloud/tradecloud-microservices/pull/1529) |  Touch user service | @marcmatt |  |
| 4 | Web Portal | 11-Jun-2021 15:53:56 CEST | [#605](https://github.com/tradecloud/tradecloud-portal-angular/pull/605) |  basic delivery line logistics | @bohdantrc |  |
| 5 | Services (Go) | 11-Jun-2021 15:53:43 CEST | [#396](https://github.com/tradecloud/tradecloud-microservices-go/pull/396) |  [TC-7098] Basic delivery line logistics | @marcmatt |  |
| 6 | Services (Scala) | 11-Jun-2021 15:53:17 CEST | [#1483](https://github.com/tradecloud/tradecloud-microservices/pull/1483) |  Basic delivery line logistics | @marcmatt |  |

17. [TC-6693](https://tradecloud.atlassian.net/browse/TC-6693) As DevOps, I want to migrate Mesos based production environment to GCP, so that I have better platform availability 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 14-Jun-2021 09:36:40 CEST | [#401](https://github.com/tradecloud/tradecloud-microservices-go/pull/401) |  Remove double deployment | @vovinacci |  |
| 2 | Services (Scala) | 08-Jun-2021 13:29:55 CEST | [#1525](https://github.com/tradecloud/tradecloud-microservices/pull/1525) |  Add GCP deployment | @vovinacci |  |
| 3 | Web Portal | 08-Jun-2021 12:41:54 CEST | [#627](https://github.com/tradecloud/tradecloud-portal-angular/pull/627) |  Add GCP deployment | @vovinacci |  |
| 4 | Services (Go) | 08-Jun-2021 08:44:58 CEST | [#397](https://github.com/tradecloud/tradecloud-microservices-go/pull/397) |  Add GCP deployment | @vovinacci |  |

18. [TC-7144](https://tradecloud.atlassian.net/browse/TC-7144) GCP: post-migration cleanup 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jun-2021 09:36:21 CEST | [#1530](https://github.com/tradecloud/tradecloud-microservices/pull/1530) |  Remove double deployment | @vovinacci |  |
| 2 | Web Portal | 14-Jun-2021 09:23:36 CEST | [#630](https://github.com/tradecloud/tradecloud-portal-angular/pull/630) |  Remove double deployment | @vovinacci |  |

19. [TC-7029](https://tradecloud.atlassian.net/browse/TC-7029) As legacy customer I want that migrated legacy orders to only overwrite TC One orders when the order is not changed in TC One 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jun-2021 16:09:32 CEST | [#1509](https://github.com/tradecloud/tradecloud-microservices/pull/1509) |  added new field - origin | @OlehVasylyshyn |  |

20. [TC-6733](https://tradecloud.atlassian.net/browse/TC-6733) As a portal user, I want to see how many attempts I have left to login and see the time for how long I am banned if my last attempt failed.   
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jun-2021 10:46:45 CEST | [#624](https://github.com/tradecloud/tradecloud-portal-angular/pull/624) |  just change code for trigger rebuild | @bohdantrc |  |

21. [TC-7073](https://tradecloud.atlassian.net/browse/TC-7073) Stress test reindexing process 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jun-2021 09:46:26 CEST | [#1517](https://github.com/tradecloud/tradecloud-microservices/pull/1517) |  Unthrottle reindexing and increase parallelism | @roy-tc |  |

22. [TC-7104](https://tradecloud.atlassian.net/browse/TC-7104) Move Go shared package to the main repository 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 01-Jun-2021 14:44:54 CEST | [#395](https://github.com/tradecloud/tradecloud-microservices-go/pull/395) |  Fix service name generation for non-test environments | @vovinacci |  |
| 2 | Services (Go) | 01-Jun-2021 14:19:21 CEST | [#393](https://github.com/tradecloud/tradecloud-microservices-go/pull/393) |  Reorganise Go code | @vovinacci |  |

23. [TC-7106](https://tradecloud.atlassian.net/browse/TC-7106) QA: Investigate flaky `test_order_resend_by_buyer_webhook_and_activity` 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 31-May-2021 14:24:08 CEST | [#394](https://github.com/tradecloud/tradecloud-microservices-go/pull/394) |  Fix &#39;webhook is not enabled&#39; error for Supplier webhooks | @vovinacci |  |

24. [TC-7101](https://tradecloud.atlassian.net/browse/TC-7101) Account code misaligned and edit button partial visible on network page using Firefox. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 31-May-2021 13:37:08 CEST | [#622](https://github.com/tradecloud/tradecloud-portal-angular/pull/622) |  fix cell align for connection table | @bohdantrc |  |

25. [TC-6883](https://tradecloud.atlassian.net/browse/TC-6883) Save if an search box or filter box in the portal is folded or unfolded.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 31-May-2021 13:31:09 CEST | [#620](https://github.com/tradecloud/tradecloud-portal-angular/pull/620) |  add expand store and selectors for tracking expanded panels | @bohdantrc |  |

26. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 31-May-2021 10:14:40 CEST | [#621](https://github.com/tradecloud/tradecloud-portal-angular/pull/621) | Bump dns-packet from 1.3.1 to 1.3.4 | @dependabot[bot] |  |

