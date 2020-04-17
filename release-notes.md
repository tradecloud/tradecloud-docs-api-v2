---
description: API and webhook connector changelog and release notes (Fri Apr 17 09:24:00 CEST 2020)
---


## Breaking changes

1. [TC-4467](#) As a DevOps I want to be able to re-build a search index (Story - Must Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 16-Apr-2020 16:09:13 CEST | #278 |  [TC-5840] Listen to user-view topic instead of user-updated topic | @roy-tc |  BREAKING CHANGE! |

## Open Pull Requests

1. [TC-5048](#) As Damen I want to display part data in the order line detail page (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Apr-2020 07:54:12 CEST | #1152 |  add update order line item API | @olegtradecloud |  |

2. [TC-4467](#) As a DevOps I want to be able to re-build a search index (Story - Must Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Apr-2020 19:00:47 CEST | #1158 |  [TC-5840] Support reindexing of users | @roy-tc |  |
| 2 | Services (Go) | 16-Apr-2020 16:09:13 CEST | #278 |  [TC-5840] Listen to user-view topic instead of user-updated topic | @roy-tc |  BREAKING CHANGE! |

3. [TC-5743](#) FE: Support bulk actions for multiple order lines (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Apr-2020 12:24:56 CEST | #374 |  Development: create checkbox column with possibility select… | @bohdantrc |  |

4. [TC-5698](#) As DevOps I want persistent Scala services to handle Cassandra keyspace being unavailable (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Apr-2020 16:27:06 CEST | #1161 |  Investigate service stability when keyspaces are missing | @roy-tc |  |

5. [](#)  ()
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Apr-2020 14:37:24 CEST | #1162 | DO NOT MERGE | @denys-kondartiuk |  |

6. [TC-5800](#) Disable 2FA API (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Apr-2020 12:16:53 CEST | #1153 |  disable 2fa | @TizianoPerrucci |  |

7. [TC-4751](#) Add a flattened line event index usable by Kibana (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Apr-2020 11:00:30 CEST | #772 |  add a flattened event index for kibana | @snevyd |  |

8. [TC-4862](#) Remove `/` path in API&#39;s (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 13-Apr-2020 15:58:03 CEST | #989 |  Proposal for routes cleanup | @roy-tc |  |

9. [TC-5767](#) As DevOps I want to stop misbehaved companies syncing legacy orders to Tradecloud1 (Bug - Critical)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 09-Apr-2020 13:40:02 CEST | #1143 |  Add migration whitelist, remove roles based rules | @marcmatt |  |

10. [TC-5789](#) Some SAP fetch requests are lost and not retried in case of SAP 503 Service Unavailable. (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 06-Apr-2020 15:15:29 CEST | #1138 |  Restructure SOAP logging statements to fix alerting | @roy-tc |  |

11. [TC-5737](#) Incorrect line id if position contains special symbols (Bug - Critical)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 30-Mar-2020 10:38:21 CEST | #1117 |  - Incorrect line id if position contains special symbols | @denys-kondartiuk |  |

## Changelog

1. [TC-5798](#) 2FA login api (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Apr-2020 21:24:21 CEST | #373 |  enable login 2fa | @TizianoPerrucci |  |
| 2 | Services (Scala) | 16-Apr-2020 21:15:18 CEST | #1151 |  enable login 2fa | @TizianoPerrucci |  |

2. [TC-5814](#) GitHub PR label flow: When PR approved first and then someone requires changes, &#39;ready: merge&#39; label is not unset (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 16-Apr-2020 12:29:55 CEST | #280 |  - Fix &#39;ready:merge&#39; logic | @denys-kondartiuk |  |
| 2 | Services (Scala) | 16-Apr-2020 12:28:21 CEST | #1163 |  - Fix &#39;ready:merge&#39; logic | @denys-kondartiuk |  |
| 3 | Web Portal | 16-Apr-2020 12:28:06 CEST | #375 |  - Fix &#39;merge:ready&#39; logic | @denys-kondartiuk |  |

3. [TC-4467](#) As a DevOps I want to be able to re-build a search index (Story - Must Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Apr-2020 14:29:36 CEST | #1157 |  Remove WorkflowTaskViewUpdated and add superuser OpenAPI specs | @roy-tc |  |
| 2 | Services (Scala) | 13-Apr-2020 08:56:18 CEST | #1122 | [TC-5739] Reindex persisted entities | @roy-tc |  |
| 3 | Services (Scala) | 03-Apr-2020 12:02:19 CEST | #1133 |  Simplify signature of TestKit | @roy-tc |  |

4. [TC-5783](#) Refactor existing Python deployment scripts to be part of &#39;tcinfra&#39; (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 15-Apr-2020 13:18:08 CEST | #279 |  - Move PR group scale to &#39;tcinfra&#39; | @denys-kondartiuk |  |
| 2 | Services (Scala) | 15-Apr-2020 13:18:01 CEST | #1160 |  - Move PR group scale to &#39;tcinfra&#39; | @denys-kondartiuk |  |

5. [TC-4946](#) As a supplier I want to add my sales order number to an order in the propose dialog (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 14-Apr-2020 11:09:29 CEST | #369 |  Add sales order number in propose changes | @bohdantrc |  |
| 2 | Services (Scala) | 30-Mar-2020 13:59:59 CEST | #1106 | : Added salesOrderNumber to accept and propose line changes. | @dmytrozheliuk |  |

6. [TC-5776](#) Documents are uploaded twice  (Bug - Blocker)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 14-Apr-2020 10:59:01 CEST | #371 | : Fixing bug related to double attaching document | @dmytrozheliuk |  |

7. [TC-5586](#) As a supplier I want to add my sales order number to a PO in the portal when accepting an order line (Story - Must Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 14-Apr-2020 10:55:28 CEST | #372 |  Development: create confirm modal with input | @bohdantrc |  |

8. [TC-5746](#) BE: Bulk action events (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Apr-2020 10:04:13 CEST | #1150 | : Adjusted activity for bulk order action events | @dmytrozheliuk |  |

9. [TC-5555](#) Continuous delivery and operations (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Apr-2020 09:11:03 CEST | #1159 |  Rename sbt project &#39;shared&#39; to &#39;microservices-shared&#39; | @vovinacci |  |
| 2 | Services (Go) | 09-Apr-2020 10:35:39 CEST | #274 |  Reflect new shared/util package function naming | @vovinacci |  |
| 3 | Services (Scala) | 08-Apr-2020 10:32:23 CEST | #1146 |  Deployment: simplify secrets | @vovinacci |  |
| 4 | Services (Scala) | 19-Mar-2020 12:37:35 CET | #1104 |  UAT: Fix concurrency issue | @vovinacci |  |
| 5 | Services (Go) | 19-Mar-2020 12:37:12 CET | #258 |  UAT: Fix concurrency issue | @vovinacci |  |
| 6 | Services (Go) | 18-Mar-2020 19:55:55 CET | #257 |  Deployment: Fix service version in proper place | @vovinacci |  |
| 7 | Services (Scala) | 18-Mar-2020 19:53:13 CET | #1103 |  Deployment: Fix service version in proper place | @vovinacci |  |
| 8 | Web Portal | 18-Mar-2020 18:52:05 CET | #356 |  Deployment: Fix service version in proper place | @vovinacci |  |
| 9 | Services (Scala) | 18-Mar-2020 18:10:29 CET | #1102 |  Deployment: Fix allowed character set in service version | @vovinacci |  |
| 10 | Web Portal | 18-Mar-2020 18:10:09 CET | #354 |  Deployment: Fix allowed character set in service version | @vovinacci |  |
| 11 | Services (Go) | 18-Mar-2020 18:09:52 CET | #256 |  Deployment: Fix allowed character set in service version | @vovinacci |  |

10. [TC-5839](#) As Devops, I want shared microservices code to be in microservices.shared package (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 13-Apr-2020 15:44:08 CEST | #1156 |  Renamed shared module to microservices-shared | @aShevc |  |
| 2 | Services (Scala) | 13-Apr-2020 11:27:15 CEST | #1154 |  Renamed com.tradecloud1.shared to com.tradecloud1.microservices.shared | @aShevc |  |

11. [TC-4218](#) As a supplier I want to receive incoming orders via the webhook connector (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 13-Apr-2020 15:16:43 CEST | #276 |  Updated logging mechanism for services | @aShevc |  |
| 2 | Services (Scala) | 10-Apr-2020 10:52:57 CEST | #1119 |  Enrich supplier side order events in company service | @aShevc |  |
| 3 | Services (Go) | 09-Apr-2020 17:24:51 CEST | #262 |  Supplier webhook | @marcmatt |  |
| 4 | Services (Go) | 01-Apr-2020 16:24:07 CEST | #265 |  Updated Kafka env variables | @aShevc |  |
| 5 | Services (Scala) | 01-Apr-2020 16:15:08 CEST | #1126 |  Update Kafka env variables | @aShevc |  |

12. [TC-5494](#) Basic 2FA (Story - Must Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Apr-2020 17:27:28 CEST | #368 |  enable 2fa | @RobinNagpal |  |

13. [](#)  ()
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Apr-2020 13:25:39 CEST | #1108 | TC-5494 enable 2fa | @TizianoPerrucci |  |
| 2 | Web Portal | 26-Mar-2020 10:30:20 CET | #359 | Logout user if refresh token fails. | @jpuri |  |
| 3 | Web Portal | 24-Mar-2020 11:33:16 CET | #353 | Fix issue with application not loading data after short inactive period. | @jpuri |  |
| 4 | Web Portal | 19-Mar-2020 12:04:03 CET | #351 | Style improvements in task chat. | @jpuri |  |
| 5 | Web Portal | 18-Mar-2020 19:00:21 CET | #350 | Bump acorn from 6.1.1 to 6.4.1 | @dependabot[bot] |  |

14. [TC-5834](#) As Vandeputte when I split a partial delivered line, the splitted line does not split the delivery correctly (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Apr-2020 12:30:56 CEST | #1149 |  SAP confirm: remove delivered filter | @marcmatt |  |

15. [TC-5777](#) Move ~/.sbt/.credentials to ~/.sbt/tradecloud-artifactory.credentials (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Apr-2020 10:03:09 CEST | #1148 |  - update readme | @olegtradecloud |  |
| 2 | Services (Scala) | 09-Apr-2020 13:09:02 CEST | #1145 |  sbt credentials | @olegtradecloud |  |

16. [TC-5770](#) Invalid time format for &#39;closedAt&#39; field (Bug - Blocker)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 09-Apr-2020 15:23:13 CEST | #1147 |  - remove retry on failure ES response | @olegtradecloud |  |
| 2 | Services (Scala) | 08-Apr-2020 14:04:47 CEST | #1140 |  - fix workflow closedAt format | @olegtradecloud |  |

17. [TC-5738](#) BE: Support bulk actions for multiple order lines (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 09-Apr-2020 09:58:42 CEST | #1121 | [TC-5465]: Bulk actions API specs and implementation | @dmytrozheliuk |  |

18. [TC-5660](#) As DevOps I want to use latest Debian version in Go services docker containers (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 09-Apr-2020 08:51:28 CEST | #275 |  Fix &#39;x509: certificate signed by unknown authority&#39; | @vovinacci |  |

19. [TC-5812](#) As DevOps I want to have automated changelog per service repository (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 08-Apr-2020 21:55:15 CEST | #273 |  Kafka: Update Confluent Kafka to 1.4.0 | @vovinacci |  |

20. [TC-5775](#) Supplier cannot download attached order document (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 08-Apr-2020 12:05:53 CEST | #1144 | : Commit OrderDocumentsEvent when trying to authorize document which doesn&#39;t exi | @dmytrozheliuk |  |

21. [TC-4391](#) As DevOps I want to make Golang microservices use Kafka client SSL connection (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 07-Apr-2020 23:36:27 CEST | #271 |  Fix missing accp/prod Kafka secrets, remove unused cmd flag parsing | @vovinacci |  |
| 2 | Services (Go) | 07-Apr-2020 22:32:16 CEST | #270 |  Use newline when printing SSL related files | @vovinacci |  |
| 3 | Services (Go) | 07-Apr-2020 22:20:49 CEST | #268 |  Kafka: Add SSL support | @vovinacci |  |

22. [TC-5688](#) As user I want that downloaded documents are named after the fileName instead of the document: ObjectId (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 06-Apr-2020 17:58:16 CEST | #1141 | : Settings downloaded file name though the amazon api headers | @dmytrozheliuk |  |

23. [TC-5642](#) As DevOps I want to migrate to tcinfra for accp and prod deployments (Story - Must Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 03-Apr-2020 13:14:07 CEST | #267 |  - Fix &#39;tcinfra&#39; usage | @denys-kondartiuk |  |
| 2 | Services (Scala) | 03-Apr-2020 13:04:06 CEST | #1137 |  Deployment: Remove debugging | @vovinacci |  |
| 3 | Services (Scala) | 03-Apr-2020 12:52:49 CEST | #1136 |  Deployment: Simplify quotation | @vovinacci |  |
| 4 | Services (Scala) | 03-Apr-2020 12:42:41 CEST | #1135 |  Deployment: Fix quoting | @vovinacci |  |
| 5 | Web Portal | 03-Apr-2020 11:59:32 CEST | #367 |  - Fix &#39;tcinfra&#39; call | @denys-kondartiuk |  |
| 6 | Web Portal | 03-Apr-2020 11:39:45 CEST | #366 |  - Reverse order for tcinfra arguments | @denys-kondartiuk |  |
| 7 | Web Portal | 03-Apr-2020 11:06:42 CEST | #365 |  - Portal Regression | @denys-kondartiuk |  |
| 8 | Services (Go) | 01-Apr-2020 19:33:30 CEST | #266 |  - Use &#39;tcinfra&#39; instead fo &#39;deploy_microservices.py&#39; to dep… | @denys-kondartiuk |  |
| 9 | Web Portal | 01-Apr-2020 19:25:24 CEST | #364 |  - Use &#39;tcinfra&#39; instead fo &#39;deploy_microservices.py&#39; to dep… | @denys-kondartiuk |  |
| 10 | Services (Scala) | 01-Apr-2020 19:10:24 CEST | #1128 |  - Use &#39;tcinfra&#39; instead of &#39;deploy_microservices.py&#39; for ac… | @denys-kondartiuk |  |

24. [TC-5773](#) Object filename and contentType are switched in meta data (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 02-Apr-2020 22:01:39 CEST | #1129 | : Fixed bug related to mixed up contentType and filename | @dmytrozheliuk |  |

25. [TC-5574](#) Order data doesn&#39;t update in activity service (Bug - Critical)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 02-Apr-2020 20:21:13 CEST | #1132 |  Fix order-integration example | @roy-tc |  |

26. [TC-5274](#) recovery link (for passwords) does not work (Bug - Critical)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 02-Apr-2020 17:24:04 CEST | #363 |  Deployment: set correct API path for reset and recovery pas… | @bohdantrc |  |

27. [TC-4591](#) As Delaware SAP consultant I want to rearrange Voortman&#39;s SAP function modules (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 01-Apr-2020 16:55:13 CEST | #1127 |  Re-enable Voortman ztradecloud_interfaces in prod env | @marcmatt |  |

28. [TC-5480](#) As DevOps, I want messages to be an sbt project (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 31-Mar-2020 16:54:41 CEST | #1001 |  - add messages as library dependencies | @olegtradecloud |  |

29. [TC-5741](#) Document recommended usage of Mockito (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 30-Mar-2020 16:44:11 CEST | #1120 |  Provide simpler Mockito helper functions with an example of how to use | @roy-tc |  |

30. [TC-5703](#) As DevOps I want to fix shimmering failing portal test (Bug - Blocker)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 27-Mar-2020 13:48:27 CET | #360 |  unit test case issue | @jpuri |  |

31. [TC-5616](#) Rename Local currency to Transaction Currency and make Base currency mandatory in integration API (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 27-Mar-2020 10:57:16 CET | #357 |  Rename priceInLocalCurrency to priceInTransactionCurrency | @roy-tc |  |
| 2 | Services (Scala) | 27-Mar-2020 10:55:53 CET | #1105 |  Rename *LocalCurrency to *TransactionCurrency | @roy-tc |  |

32. [TC-5704](#) Cassandra: Reduce amount of traffic between nodes (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 26-Mar-2020 19:57:42 CET | #1118 |  Add 4th C* node support | @vovinacci |  |

33. [TC-5644](#) As DevOps I want to simplify GitHub PR flow (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 25-Mar-2020 15:16:41 CET | #263 |  - Fix regression | @denys-kondartiuk |  |
| 2 | Services (Scala) | 25-Mar-2020 15:15:59 CET | #1112 |  - Fix regression | @denys-kondartiuk |  |
| 3 | Web Portal | 25-Mar-2020 15:14:41 CET | #361 |  - Fix regression | @denys-kondartiuk |  |
| 4 | Services (Go) | 24-Mar-2020 20:07:46 CET | #261 |  - GitHub labels PR flow | @denys-kondartiuk |  |
| 5 | Services (Scala) | 24-Mar-2020 19:44:08 CET | #1111 |  - New GitHub PR flow | @denys-kondartiuk |  |
| 6 | Web Portal | 24-Mar-2020 19:28:37 CET | #358 |  - New GitHub labels PR flow | @denys-kondartiuk |  |

34. [TC-5712](#) Make service versions consistent when running accp tests on Jenkins (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 20-Mar-2020 17:22:45 CET | #259 |  - Make service versions consistent when running accp tests on Jenkins | @denys-kondartiuk |  |
| 2 | Services (Scala) | 20-Mar-2020 17:22:09 CET | #1107 |  - Make service versions consistent when running accp tests on Jenkins | @denys-kondartiuk |  |

35. [TC-5714](#) Webhook HTTP POST/PUT should send HTTP header Content-Type application/json (Bug - Critical)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 20-Mar-2020 16:33:07 CET | #260 |  - set webhook request content type | @olegtradecloud |  |

36. [TC-5658](#) Order service receives unknown message EnrichConversation (Bug - Critical)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-Mar-2020 12:55:47 CET | #1098 |  Support order line positions with hyphens | @roy-tc |  |

37. [TC-5655](#) BE: improve tests and implementation for document attachments (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Mar-2020 16:26:06 CET | #1100 | : Added implementation based on *ing patterns. Extended tests | @dmytrozheliuk |  |

38. [TC-5524](#) BE: implement webhook trigger for attached documents (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Mar-2020 14:44:37 CET | #1084 |  - add enrichment of OrderDocumentsEvent in company service | @olegtradecloud |  |
| 2 | Services (Go) | 19-Mar-2020 14:41:43 CET | #251 | - handle OutgoingOrderDocumentsAttached events | @olegtradecloud |  |

39. [TC-5665](#) Workflow IndexRequest failed for large documents (Bug - Critical)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Mar-2020 17:48:21 CET | #1099 |  IndexRequest exception logging | @roy-tc |  |

40. [TC-5641](#) As DevOps I want to resolve TODO list in service repositories related to deployment (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Mar-2020 11:51:10 CET | #1101 |  Deployment: Address TODO list | @vovinacci |  |
| 2 | Web Portal | 17-Mar-2020 16:32:57 CET | #352 |  Deployment: Address TODO list | @vovinacci |  |
| 3 | Services (Go) | 17-Mar-2020 14:17:52 CET | #255 |  Deployment: Address TODO list | @vovinacci |  |

41. [TC-5526](#) FE: Support attach document activities for order(line)s (Story - Should Have)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Mar-2020 11:56:26 CET | #349 |  Add details of attached document to activity. | @jpuri |  |

42. [TC-5659](#) Refactor Kafka tests in shared library to use with Confluent Kafka (Bug - High)
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 17-Mar-2020 11:17:39 CET | #254 |  Kafka: Bump shared package, chores | @vovinacci |  |

