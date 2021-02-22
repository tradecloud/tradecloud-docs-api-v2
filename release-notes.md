---
description: Tradecloud services and portal open pull requests and changelog (Mon Feb 22 20:30:45 CET 2021)
---


## Open Pull Requests

1. [TC-6767](https://tradecloud.atlassian.net/browse/TC-6767) BE: Company acknowledge settings 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Feb-2021 18:27:57 CET | [#1443](https://github.com/tradecloud/tradecloud-microservices/pull/1443) | [TC-6245]: Acknowledge tasks | @dmytrozheliuk |  |
| 2 | Services (Scala) | 19-Feb-2021 09:16:10 CET | [#1428](https://github.com/tradecloud/tradecloud-microservices/pull/1428) | : Acknowledge settings model and new API endpoints to get settings and modify it | @dmytrozheliuk |  |

2. [TC-4420](https://tradecloud.atlassian.net/browse/TC-4420) Create IDoc connector components and sequence diagrams 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Feb-2021 16:26:05 CET | [#1289](https://github.com/tradecloud/tradecloud-microservices/pull/1289) |  Draft to illustrate how we can simplify the order behavior and decent… | @roy-tc |  |

3. [TC-6775](https://tradecloud.atlassian.net/browse/TC-6775) Separate reindexing of OrderViews from the processing of regular OrderViews 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Feb-2021 14:39:35 CET | [#1433](https://github.com/tradecloud/tradecloud-microservices/pull/1433) |  Publish views to prefixed topic for reindexing | @roy-tc |  |
| 2 | Services (Go) | 22-Feb-2021 14:21:23 CET | [#374](https://github.com/tradecloud/tradecloud-microservices-go/pull/374) |  Extend consumers to listen to separate reindexing topics | @roy-tc |  |

4. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 22-Feb-2021 10:06:42 CET | [#580](https://github.com/tradecloud/tradecloud-portal-angular/pull/580) | Tc 6597 avatar | @bohdantrc |  |

5. [TC-6695](https://tradecloud.atlassian.net/browse/TC-6695) Implement per-buyer-supplier authentication and persistence of configured credentials 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Feb-2021 17:18:36 CET | [#1439](https://github.com/tradecloud/tradecloud-microservices/pull/1439) |  Move ActorPersistence and AggregateRootActor to shared lib | @roy-tc |  |

6. [TC-6535](https://tradecloud.atlassian.net/browse/TC-6535) Add possibility generate locales files and update/merge after update tokens 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Feb-2021 20:27:13 CET | [#530](https://github.com/tradecloud/tradecloud-portal-angular/pull/530) |  local build and merge i18n files | @bohdantrc |  |

7. [TC-5769](https://tradecloud.atlassian.net/browse/TC-5769) Do not persist and publish order events when the entity state does not change. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 20:25:49 CET | [#1234](https://github.com/tradecloud/tradecloud-microservices/pull/1234) |  Optional events | @olegtradecloud |  |

8. [TC-6483](https://tradecloud.atlassian.net/browse/TC-6483) The OrderReissuedByBuyer event should be renamed to OrderLinesReissuedByBuyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 20:22:21 CET | [#1432](https://github.com/tradecloud/tradecloud-microservices/pull/1432) |  Refactor to OrderLinesReissuedByBuyer event and ActivityType | @marcmatt |  |

9. [TC-4540](https://tradecloud.atlassian.net/browse/TC-4540) Load test with MRP-based batch of orders and order responses 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 20:22:08 CET | [#1384](https://github.com/tradecloud/tradecloud-microservices/pull/1384) |  Test PR | @roy-tc |  |

10. [TC-4371](https://tradecloud.atlassian.net/browse/TC-4371) As a DevOps I would like to trace messages over and in services to solve issues faster 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 20:22:07 CET | [#1370](https://github.com/tradecloud/tradecloud-microservices/pull/1370) | : Kamon init | @dmytrozheliuk |  |

11. [TC-5789](https://tradecloud.atlassian.net/browse/TC-5789) Some SAP fetch requests are lost and not retried in case of SAP 503 Service Unavailable. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 20:22:06 CET | [#1138](https://github.com/tradecloud/tradecloud-microservices/pull/1138) |  Restructure SOAP logging statements to fix alerting | @roy-tc |  |

12. [TC-6811](https://tradecloud.atlassian.net/browse/TC-6811) PoC for using the Java Tensorflow API for evaluating order lines based on a saved model 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 20:22:05 CET | [#1430](https://github.com/tradecloud/tradecloud-microservices/pull/1430) |  PoC for running RiskIndicator as a Scala Microservice | @roy-tc |  |

13. [TC-6521](https://tradecloud.atlassian.net/browse/TC-6521) As a user I want that contacts in the Orders &amp; Tasks page are sorted alphabetically  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 11-Feb-2021 20:21:59 CET | [#355](https://github.com/tradecloud/tradecloud-microservices-go/pull/355) |  - user search sorting  | @olegtradecloud |  |

14. [TC-6359](https://tradecloud.atlassian.net/browse/TC-6359) As a company admin and superuser, I want to remove a user, in the portal 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 20:21:56 CET | [#1336](https://github.com/tradecloud/tradecloud-microservices/pull/1336) |  Remove user | @marcmatt |  |

## Changelog

1. [TC-6822](https://tradecloud.atlassian.net/browse/TC-6822) order line header does show the line position when there is a `row` value available  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 22-Feb-2021 11:01:33 CET | [#579](https://github.com/tradecloud/tradecloud-portal-angular/pull/579) |  add row info into order line detail page | @bohdantrc |  |

2. [TC-6852](https://tradecloud.atlassian.net/browse/TC-6852) BE: Manually close acknowledge tasks 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Feb-2021 06:59:13 CET | [#1444](https://github.com/tradecloud/tradecloud-microservices/pull/1444) | : Adding functionality to manually close acknowledge tasks | @dmytrozheliuk |  |

3. [TC-6630](https://tradecloud.atlassian.net/browse/TC-6630) As a integrated supplier I want to process reopen requests by buyer in my ERP instead of TC  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Feb-2021 14:08:19 CET | [#1429](https://github.com/tradecloud/tradecloud-microservices/pull/1429) |  - supplier reopen request via integration | @olegtradecloud |  |
| 2 | Services (Scala) | 15-Feb-2021 14:21:51 CET | [#1435](https://github.com/tradecloud/tradecloud-microservices/pull/1435) |  - implement supplier reopen request tests | @olegtradecloud |  |

4. [TC-6827](https://tradecloud.atlassian.net/browse/TC-6827) BE: refactor workflow state to support multiple tasks for 1 order line 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Feb-2021 09:11:43 CET | [#1441](https://github.com/tradecloud/tradecloud-microservices/pull/1441) | : Workflow refactoring to support multiple tasks | @dmytrozheliuk |  |

5. [TC-6759](https://tradecloud.atlassian.net/browse/TC-6759) Enable Damen SSO in PROD 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 18-Feb-2021 14:33:58 CET | [#578](https://github.com/tradecloud/tradecloud-portal-angular/pull/578) |  Enable Damen SSO on production | @marcmatt |  |

6. [TC-6824](https://tradecloud.atlassian.net/browse/TC-6824) Make portal SSO configurable per environment for Damen  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Feb-2021 15:45:40 CET | [#577](https://github.com/tradecloud/tradecloud-portal-angular/pull/577) |  move config to env files | @bohdantrc |  |

7. [TC-6619](https://tradecloud.atlassian.net/browse/TC-6619) As DevOps, I want to migrate Mesos based test environment to GCP, so that I have better platform availability 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 16-Feb-2021 11:44:51 CET | [#375](https://github.com/tradecloud/tradecloud-microservices-go/pull/375) |  PR cleanup as separate stage | @denys-kondartiuk |  |
| 2 | Services (Scala) | 15-Feb-2021 16:27:28 CET | [#1440](https://github.com/tradecloud/tradecloud-microservices/pull/1440) |  Add afterTests for UAT Run | @denys-kondartiuk |  |
| 3 | Services (Scala) | 15-Feb-2021 13:00:26 CET | [#1438](https://github.com/tradecloud/tradecloud-microservices/pull/1438) |  Fix CI group deployment | @denys-kondartiuk |  |
| 4 | Services (Scala) | 12-Feb-2021 17:28:28 CET | [#1437](https://github.com/tradecloud/tradecloud-microservices/pull/1437) |  Move PR group cleanup to the separate stage | @denys-kondartiuk |  |
| 5 | Web Portal | 12-Feb-2021 16:48:46 CET | [#576](https://github.com/tradecloud/tradecloud-portal-angular/pull/576) |  - PR cleanup add label | @denys-kondartiuk |  |
| 6 | Web Portal | 12-Feb-2021 16:32:55 CET | [#575](https://github.com/tradecloud/tradecloud-portal-angular/pull/575) |  PR cleanup as a separate stage | @denys-kondartiuk |  |

8. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Feb-2021 14:36:12 CET | [#1436](https://github.com/tradecloud/tradecloud-microservices/pull/1436) | Remove findUserByEmail route from user service | @marcmatt |  |
| 2 | Web Portal | 10-Feb-2021 21:43:39 CET | [#565](https://github.com/tradecloud/tradecloud-portal-angular/pull/565) | Provide a meaningful error message to the user | @bohdantrc |  |

9. [TC-6766](https://tradecloud.atlassian.net/browse/TC-6766) Choose either credentials or token in the company webhook integration settings in the portal. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 14-Feb-2021 22:27:10 CET | [#573](https://github.com/tradecloud/tradecloud-portal-angular/pull/573) |  Add new field token into integration settings. | @bohdantrc |  |

10. [TC-6823](https://tradecloud.atlassian.net/browse/TC-6823) Marcel Terlouw can not log in on production, after he tested SSO on acceptance 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 12-Feb-2021 12:05:48 CET | [#574](https://github.com/tradecloud/tradecloud-portal-angular/pull/574) |  Remove Damen users from SSO connections config | @marcmatt |  |

11. [TC-6767](https://tradecloud.atlassian.net/browse/TC-6767) BE: Company acknowledge settings 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Feb-2021 11:10:03 CET | [#1434](https://github.com/tradecloud/tradecloud-microservices/pull/1434) |  Alternative default solution | @marcmatt |  |

12. [TC-6781](https://tradecloud.atlassian.net/browse/TC-6781) As a SSO user I am logged out when browser is closed for 10 minutes 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Feb-2021 17:39:21 CET | [#572](https://github.com/tradecloud/tradecloud-portal-angular/pull/572) |  use local storage instead of session so that token are retined | @RobinNagpal |  |

13. [TC-6000](https://tradecloud.atlassian.net/browse/TC-6000) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Feb-2021 10:44:20 CET | [#1431](https://github.com/tradecloud/tradecloud-microservices/pull/1431) |  Fix master deployment for multiple services | @denys-kondartiuk |  |
| 2 | Services (Go) | 10-Feb-2021 10:12:57 CET | [#373](https://github.com/tradecloud/tradecloud-microservices-go/pull/373) |  Fix bash array usage. Add dummy changes to rebuild the services. | @denys-kondartiuk |  |
| 3 | Services (Go) | 10-Feb-2021 09:56:19 CET | [#372](https://github.com/tradecloud/tradecloud-microservices-go/pull/372) |  Additional logging to investigate deployment issues | @denys-kondartiuk |  |
| 4 | Services (Go) | 01-Feb-2021 14:27:21 CET | [#361](https://github.com/tradecloud/tradecloud-microservices-go/pull/361) |  Fix case with missing variable | @denys-kondartiuk |  |
| 5 | Services (Scala) | 28-Jan-2021 12:02:59 CET | [#1422](https://github.com/tradecloud/tradecloud-microservices/pull/1422) |  Disable UI tests for builds | @denys-kondartiuk |  |

14. [TC-6798](https://tradecloud.atlassian.net/browse/TC-6798) Go services cannot connect to Elasticsearch if any of Elasticsearch nodes are not available 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 09-Feb-2021 18:25:53 CET | [#371](https://github.com/tradecloud/tradecloud-microservices-go/pull/371) |  Configure Elasticsearch client, improve error handling | @marcmatt |  |

15. [TC-6709](https://tradecloud.atlassian.net/browse/TC-6709) Refactor workflow event to not use domain command as a payload 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 05-Feb-2021 09:36:39 CET | [#1426](https://github.com/tradecloud/tradecloud-microservices/pull/1426) |   - workflow refactoring v2 | @olegtradecloud |  |

16. [TC-6330](https://tradecloud.atlassian.net/browse/TC-6330) As A B software I would like to use a static webhook bearer token to scale customer onboarding and reduce maintenance 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 04-Feb-2021 16:26:32 CET | [#360](https://github.com/tradecloud/tradecloud-microservices-go/pull/360) |  Add webhook bearer token | @marcmatt |  |
| 2 | Services (Scala) | 04-Feb-2021 16:02:16 CET | [#1424](https://github.com/tradecloud/tradecloud-microservices/pull/1424) |  Add company settings integration endpoint token | @marcmatt |  |

17. [TC-6670](https://tradecloud.atlassian.net/browse/TC-6670) E2E tests for Azure AD  SSO integration 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Feb-2021 14:59:51 CET | [#571](https://github.com/tradecloud/tradecloud-portal-angular/pull/571) |  Fix issue  with npm | @denys-kondartiuk |  |

18. [TC-6682](https://tradecloud.atlassian.net/browse/TC-6682) As DevOps I want to migrate cd/monit/grafana/influx to GCP, so that I would be able to operate things efficiently 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 02-Feb-2021 18:06:09 CET | [#1415](https://github.com/tradecloud/tradecloud-microservices/pull/1415) |  Split build and deploy | @denys-kondartiuk |  |
| 2 | Web Portal | 02-Feb-2021 13:53:22 CET | [#570](https://github.com/tradecloud/tradecloud-portal-angular/pull/570) |  Fix services list for master deployment | @denys-kondartiuk |  |
| 3 | Web Portal | 02-Feb-2021 13:23:08 CET | [#569](https://github.com/tradecloud/tradecloud-portal-angular/pull/569) |  Add additional logging to investigate issue with master deploy | @denys-kondartiuk |  |
| 4 | Web Portal | 02-Feb-2021 12:55:28 CET | [#568](https://github.com/tradecloud/tradecloud-portal-angular/pull/568) |  Fix unbound variable | @denys-kondartiuk |  |
| 5 | Web Portal | 02-Feb-2021 12:35:19 CET | [#567](https://github.com/tradecloud/tradecloud-portal-angular/pull/567) |  Split build and deploy | @denys-kondartiuk |  |
| 6 | Services (Go) | 01-Feb-2021 17:44:42 CET | [#369](https://github.com/tradecloud/tradecloud-microservices-go/pull/369) |  Trigger build | @denys-kondartiuk |  |
| 7 | Services (Go) | 01-Feb-2021 17:39:10 CET | [#368](https://github.com/tradecloud/tradecloud-microservices-go/pull/368) |   Fix master deploy | @denys-kondartiuk |  |
| 8 | Services (Go) | 01-Feb-2021 17:26:10 CET | [#367](https://github.com/tradecloud/tradecloud-microservices-go/pull/367) |  Finalize changes related to split build and deploy | @denys-kondartiuk |  |
| 9 | Services (Go) | 01-Feb-2021 17:15:39 CET | [#366](https://github.com/tradecloud/tradecloud-microservices-go/pull/366) |  Add additional logging to investigate the issues | @denys-kondartiuk |  |
| 10 | Services (Go) | 01-Feb-2021 16:42:55 CET | [#365](https://github.com/tradecloud/tradecloud-microservices-go/pull/365) |  Experiment with conditions in shell scripts | @denys-kondartiuk |  |
| 11 | Services (Go) | 01-Feb-2021 15:34:39 CET | [#364](https://github.com/tradecloud/tradecloud-microservices-go/pull/364) |  Fix master build | @denys-kondartiuk |  |
| 12 | Services (Go) | 01-Feb-2021 15:18:20 CET | [#363](https://github.com/tradecloud/tradecloud-microservices-go/pull/363) |  Dummy commit to trigger build | @denys-kondartiuk |  |
| 13 | Services (Go) | 01-Feb-2021 15:05:03 CET | [#362](https://github.com/tradecloud/tradecloud-microservices-go/pull/362) |  Fix way to skip unnecessary deployment | @denys-kondartiuk |  |
| 14 | Services (Go) | 01-Feb-2021 13:33:42 CET | [#359](https://github.com/tradecloud/tradecloud-microservices-go/pull/359) |  Split build and deploy | @denys-kondartiuk |  |
| 15 | Web Portal | 25-Jan-2021 12:38:19 CET | [#560](https://github.com/tradecloud/tradecloud-portal-angular/pull/560) |  Restore CI files to unblock master builds | @denys-kondartiuk |  |
| 16 | Web Portal | 25-Jan-2021 12:02:20 CET | [#558](https://github.com/tradecloud/tradecloud-portal-angular/pull/558) |  Split build and deploy fixes | @denys-kondartiuk |  |
| 17 | Web Portal | 25-Jan-2021 11:41:09 CET | [#557](https://github.com/tradecloud/tradecloud-portal-angular/pull/557) |  Split prod and test service versions | @denys-kondartiuk |  |
| 18 | Web Portal | 25-Jan-2021 10:07:47 CET | [#554](https://github.com/tradecloud/tradecloud-portal-angular/pull/554) |  - Split build and deploy | @denys-kondartiuk |  |

19. [TC-6712](https://tradecloud.atlassian.net/browse/TC-6712) As a buyer I want to send attached documents embedded in the order/line using the API connector 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 01-Feb-2021 15:03:16 CET | [#1421](https://github.com/tradecloud/tradecloud-microservices/pull/1421) |  - attach documents refactoring | @olegtradecloud |  |

20. [TC-6754](https://tradecloud.atlassian.net/browse/TC-6754) Configure Damen SSO in ACCP 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 01-Feb-2021 10:18:32 CET | [#566](https://github.com/tradecloud/tradecloud-portal-angular/pull/566) |  Add Marcel Terlouw to SSO Damen ACCP config | @marcmatt |  |
| 2 | Web Portal | 27-Jan-2021 14:11:24 CET | [#564](https://github.com/tradecloud/tradecloud-portal-angular/pull/564) |  SSO Damen ACCP config | @marcmatt |  |
| 3 | Services (Scala) | 27-Jan-2021 14:10:17 CET | [#1420](https://github.com/tradecloud/tradecloud-microservices/pull/1420) |  SSO Damen ACCP config | @marcmatt |  |

21. [TC-6647](https://tradecloud.atlassian.net/browse/TC-6647) Portal should get the actual order when reconnected to the order websocket 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jan-2021 19:17:42 CET | [#556](https://github.com/tradecloud/tradecloud-portal-angular/pull/556) |  after connection to WS each time fetch (opened/current) order, order line if po | @bohdantrc |  |

22. [TC-6679](https://tradecloud.atlassian.net/browse/TC-6679) when doing a bulk proposal and after that a proposal, then the dialog is only prefilled with the proposed delivery date.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jan-2021 19:15:01 CET | [#561](https://github.com/tradecloud/tradecloud-portal-angular/pull/561) |  add fileds prices into dialog | @bohdantrc |  |

23. [TC-6753](https://tradecloud.atlassian.net/browse/TC-6753) Make sure no order (line) search request is send to the backend when an WS &#34;orders are outdated&#34; event comes in 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jan-2021 17:57:39 CET | [#563](https://github.com/tradecloud/tradecloud-portal-angular/pull/563) |  delete search request after WS event that orders outdated | @bohdantrc |  |

24. [TC-6247](https://tradecloud.atlassian.net/browse/TC-6247) Add the event that triggered a Task in the tasks itself.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jan-2021 15:44:32 CET | [#1423](https://github.com/tradecloud/tradecloud-microservices/pull/1423) |  - fix eventName deserialization | @olegtradecloud |  |
| 2 | Services (Scala) | 28-Jan-2021 14:01:09 CET | [#1411](https://github.com/tradecloud/tradecloud-microservices/pull/1411) |  - add `eventName` to workflow model and view | @olegtradecloud |  |

25. [TC-6697](https://tradecloud.atlassian.net/browse/TC-6697) Indicators do not work when a line, with an indicator on True, is added later to an existing order.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 27-Jan-2021 14:17:16 CET | [#1416](https://github.com/tradecloud/tradecloud-microservices/pull/1416) | : Handling order indicators during order reissuing | @dmytrozheliuk |  |

26. [TC-6562](https://tradecloud.atlassian.net/browse/TC-6562) As Alfen I want to send orders to tradecloud 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 26-Jan-2021 16:32:56 CET | [#1401](https://github.com/tradecloud/tradecloud-microservices/pull/1401) |  Update support for order(line) documents, merge documents | @roy-tc |  |

27. [TC-6747](https://tradecloud.atlassian.net/browse/TC-6747) orders search box breaks the order overview. When used 500 error is received.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 26-Jan-2021 12:35:11 CET | [#1417](https://github.com/tradecloud/tradecloud-microservices/pull/1417) |  - update shared to use new ES fixes | @olegtradecloud |  |

28. [TC-6711](https://tradecloud.atlassian.net/browse/TC-6711) Support document urls in order and line detail pages 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jan-2021 11:22:26 CET | [#555](https://github.com/tradecloud/tradecloud-portal-angular/pull/555) |  show title for link | @bohdantrc |  |

29. [TC-6615](https://tradecloud.atlassian.net/browse/TC-6615) As portal user I want to search order(line)s on multiple order fields 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jan-2021 09:09:15 CET | [#549](https://github.com/tradecloud/tradecloud-portal-angular/pull/549) |  add search component into orders and task pages | @bohdantrc |  |
| 2 | Services (Scala) | 25-Jan-2021 09:07:42 CET | [#1398](https://github.com/tradecloud/tradecloud-microservices/pull/1398) |  - improve order search | @olegtradecloud |  |

30. [TC-6653](https://tradecloud.atlassian.net/browse/TC-6653) Portal should check and refresh access token when invalid before web socket reconnect 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-Jan-2021 17:36:11 CET | [#551](https://github.com/tradecloud/tradecloud-portal-angular/pull/551) | [TC-6651] change settings into backoff and retry | @bohdantrc |  |

