---
description: Tradecloud services and portal open pull requests and changelog (Tue May 25 15:30:38 CEST 2021)
---


## Open Pull Requests

1. [TC-7029](https://tradecloud.atlassian.net/browse/TC-7029) As legacy customer I want that migrated legacy orders to only overwrite TC One orders when the order is not changed in TC One 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-May-2021 15:22:32 CEST | [#1509](https://github.com/tradecloud/tradecloud-microservices/pull/1509) |  added new field - origin | @OlehVasylyshyn |  |

2. [TC-6431](https://tradecloud.atlassian.net/browse/TC-6431) Webhook POST body contains JSON numbers with quotes 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 25-May-2021 13:46:34 CEST | [#390](https://github.com/tradecloud/tradecloud-microservices-go/pull/390) |  Refactor Protobuf to JSON serialisation | @vovinacci |  |

3. [TC-6949](https://tradecloud.atlassian.net/browse/TC-6949) As portal user, I want to (Re)assign orders to users  [Planned release 24-Jun-2021]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-May-2021 13:13:04 CEST | [#1518](https://github.com/tradecloud/tradecloud-microservices/pull/1518) |  (Re)assign orders to users | @OlehVasylyshyn |  |

4. [TC-7073](https://tradecloud.atlassian.net/browse/TC-7073) Stress test reindexing process 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-May-2021 11:57:50 CEST | [#1517](https://github.com/tradecloud/tradecloud-microservices/pull/1517) |  Unthrottle reindexing and increase parallelism | @roy-tc |  |

5. [TC-6941](https://tradecloud.atlassian.net/browse/TC-6941) As buyer I want that suppliers can set logistical status using the portal - BASIC  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-May-2021 11:09:59 CEST | [#605](https://github.com/tradecloud/tradecloud-portal-angular/pull/605) |  basic delivery line logistics | @bohdantrc |  |
| 2 | Services (Scala) | 25-May-2021 09:24:09 CEST | [#1516](https://github.com/tradecloud/tradecloud-microservices/pull/1516) |  Add new LogisticsStatus values | @marcmatt |  |
| 3 | Services (Scala) | 24-May-2021 22:24:26 CEST | [#1483](https://github.com/tradecloud/tradecloud-microservices/pull/1483) |  Basic delivery line logistics | @marcmatt |  |
| 4 | Services (Go) | 12-May-2021 17:09:01 CEST | [#384](https://github.com/tradecloud/tradecloud-microservices-go/pull/384) |  Basic delivery line logistics | @marcmatt |  |

6. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-May-2021 23:22:18 CEST | [#618](https://github.com/tradecloud/tradecloud-portal-angular/pull/618) | Bump browserslist from 4.13.0 to 4.16.6 | @dependabot[bot] |  |
| 2 | Web Portal | 18-May-2021 11:46:55 CEST | [#613](https://github.com/tradecloud/tradecloud-portal-angular/pull/613) | Bump highcharts from 7.0.3 to 9.0.0 | @dependabot[bot] |  |

7. [TC-7096](https://tradecloud.atlassian.net/browse/TC-7096) Use LOCAL_QUORUM for Scala persisted services 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 21-May-2021 15:24:07 CEST | [#1515](https://github.com/tradecloud/tradecloud-microservices/pull/1515) |  Use LOCAL_QUORUM to use C* nodes from LOCAL DC only | @roy-tc |  |

8. [TC-6316](https://tradecloud.atlassian.net/browse/TC-6316) Add support of starting buf check locally 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-May-2021 14:26:23 CEST | [#1513](https://github.com/tradecloud/tradecloud-microservices/pull/1513) |  Support running buf breaking changes locally | @roy-tc |  |

## Changelog

1. [TC-7081](https://tradecloud.atlassian.net/browse/TC-7081) Incoming order without lines is silently ignored and not persisted. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 24-May-2021 18:04:03 CEST | [#1511](https://github.com/tradecloud/tradecloud-microservices/pull/1511) |  - issue order without lines fix | @olegtradecloud |  |

2. [TC-6957](https://tradecloud.atlassian.net/browse/TC-6957) As Eichholtz (GAC) I want to cancel lines by removing them from the order update 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 21-May-2021 11:14:46 CEST | [#1505](https://github.com/tradecloud/tradecloud-microservices/pull/1505) |  - cancel missing lines | @olegtradecloud |  |

3. [TC-7036](https://tradecloud.atlassian.net/browse/TC-7036) As Exact Globe integrator I need migrated Exact Globe delivery schedule position to be set to the line position. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-May-2021 19:08:09 CEST | [#1508](https://github.com/tradecloud/tradecloud-microservices/pull/1508) |  Delivery position for ExactGlobeCustomers from line code | @OlehVasylyshyn |  |

4. [TC-6789](https://tradecloud.atlassian.net/browse/TC-6789) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-May-2021 18:37:17 CEST | [#1514](https://github.com/tradecloud/tradecloud-microservices/pull/1514) |  Remove unsupported imgix parameters | @marcmatt |  |
| 2 | Web Portal | 11-May-2021 11:43:19 CEST | [#616](https://github.com/tradecloud/tradecloud-portal-angular/pull/616) |  Update job URL | @denys-kondartiuk |  |
| 3 | Services (Scala) | 11-May-2021 11:38:36 CEST | [#1504](https://github.com/tradecloud/tradecloud-microservices/pull/1504) |  Update job URL | @denys-kondartiuk |  |
| 4 | Services (Go) | 03-May-2021 18:21:11 CEST | [#392](https://github.com/tradecloud/tradecloud-microservices-go/pull/392) |  Remove broken link from email footer | @vovinacci |  |

5. [TC-6213](https://tradecloud.atlassian.net/browse/TC-6213)  Connection can be requested to company itself 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-May-2021 17:47:26 CEST | [#1507](https://github.com/tradecloud/tradecloud-microservices/pull/1507) |  Connection to company itself | @OlehVasylyshyn |  |

6. [TC-6882](https://tradecloud.atlassian.net/browse/TC-6882) UAT: Verify an acknowledge task results in a contact notification 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-May-2021 17:21:29 CEST | [#1510](https://github.com/tradecloud/tradecloud-microservices/pull/1510) |  Add optional UserSettings to AddUser super user API | @marcmatt |  |

7. [TC-7058](https://tradecloud.atlassian.net/browse/TC-7058) The portal shows be default 2 decimals (.00) when the priceUnitQuantity ≠ 1 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-May-2021 16:42:34 CEST | [#617](https://github.com/tradecloud/tradecloud-portal-angular/pull/617) |  allow format 10-&gt;10 instead of 10-&gt;10.00 | @bohdantrc |  |

8. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-May-2021 12:40:42 CEST | [#615](https://github.com/tradecloud/tradecloud-portal-angular/pull/615) | Bump hosted-git-info from 2.7.1 to 2.8.9 | @dependabot[bot] |  |
| 2 | Web Portal | 07-May-2021 09:04:58 CEST | [#614](https://github.com/tradecloud/tradecloud-portal-angular/pull/614) | Bump url-parse from 1.4.7 to 1.5.1 | @dependabot[bot] |  |
| 3 | Web Portal | 26-Apr-2021 11:36:33 CEST | [#606](https://github.com/tradecloud/tradecloud-portal-angular/pull/606) | Bump ssri from 6.0.1 to 6.0.2 | @dependabot[bot] |  |

9. [TC-6733](https://tradecloud.atlassian.net/browse/TC-6733) As a portal user, I want to see how many attempts I have left to login and see the time for how long I am banned if my last attempt failed.   
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 12-May-2021 16:37:51 CEST | [#612](https://github.com/tradecloud/tradecloud-portal-angular/pull/612) |  login attempts | @bohdantrc |  |
| 2 | Services (Scala) | 12-May-2021 16:37:24 CEST | [#1503](https://github.com/tradecloud/tradecloud-microservices/pull/1503) |  Added banned time in seconds to login response | @OlehVasylyshyn |  |

10. [TC-5534](https://tradecloud.atlassian.net/browse/TC-5534) As buyer I want to send the supplier contact with my order 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-May-2021 11:43:41 CEST | [#1500](https://github.com/tradecloud/tradecloud-microservices/pull/1500) | [TC-7004] add supplierOrder.contact with status | @roy-tc |  |

11. [TC-6131](https://tradecloud.atlassian.net/browse/TC-6131) As integrated partner I would like to use a polling integration pattern for updated orders 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 07-May-2021 16:26:09 CEST | [#391](https://github.com/tradecloud/tradecloud-microservices-go/pull/391) |  Extend and fix webhook API specs, bump messages | @marcmatt |  |
| 2 | Services (Scala) | 07-May-2021 16:13:34 CEST | [#1492](https://github.com/tradecloud/tradecloud-microservices/pull/1492) |  - updated order search | @olegtradecloud |  |
| 3 | Services (Scala) | 26-Apr-2021 15:23:22 CEST | [#1495](https://github.com/tradecloud/tradecloud-microservices/pull/1495) |  [TC-7013] Order search service changes | @olegtradecloud |  |

12. [TC-7057](https://tradecloud.atlassian.net/browse/TC-7057) Remove akka-cluster-custom-downing dependency 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-May-2021 13:42:27 CEST | [#1501](https://github.com/tradecloud/tradecloud-microservices/pull/1501) |  - akka custom downing  | @olegtradecloud |  |

13. [TC-6924](https://tradecloud.atlassian.net/browse/TC-6924) As Isah, I want to be able to disable my SCI Integration 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 03-May-2021 11:31:42 CEST | [#611](https://github.com/tradecloud/tradecloud-portal-angular/pull/611) |  add disabling sci integration | @bohdantrc |  |

14. [TC-6906](https://tradecloud.atlassian.net/browse/TC-6906) Activity proposal/reopen request comparison in portal does not take currencies into account   
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Apr-2021 12:58:21 CEST | [#608](https://github.com/tradecloud/tradecloud-portal-angular/pull/608) |  check and highlight priceInTransactionCurrency | @bohdantrc |  |

15. [TC-6315](https://tradecloud.atlassian.net/browse/TC-6315) As an SSO user I want to change my profile in Tradecloud 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Apr-2021 15:59:46 CEST | [#610](https://github.com/tradecloud/tradecloud-portal-angular/pull/610) |  change method and add possibility change user settings | @bohdantrc |  |

16. [TC-6431](https://tradecloud.atlassian.net/browse/TC-6431) Webhook POST body contains JSON numbers with quotes 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 26-Apr-2021 14:39:32 CEST | [#389](https://github.com/tradecloud/tradecloud-microservices-go/pull/389) |  Cleanup | @vovinacci |  |

