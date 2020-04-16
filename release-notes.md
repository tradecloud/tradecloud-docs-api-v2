---
description: API and webhook connector changelog and release notes (Thu Apr 16 22:56:51 CEST 2020)
---


## Breaking changes

1. [](#) As a DevOps I want to be able to re-build a search index
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 16-Apr-2020 16:09:13 CEST | #278 |  [TC-5840] Listen to user-view topic instead of user-updated topic | @roy-tc |  BREAKING CHANGE! |

## Open Pull Requests

1. [](#) Incorrect line id if position contains special symbols
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Apr-2020 19:00:47 CEST | #1158 |  [TC-5840] Support reindexing of users | @roy-tc |  |
| 2 | Services (Go) | 16-Apr-2020 16:09:13 CEST | #278 |  [TC-5840] Listen to user-view topic instead of user-updated topic | @roy-tc |  BREAKING CHANGE! |
| 3 | Services (Scala) | 16-Apr-2020 14:51:00 CEST | #1152 |  add update order line item API | @olegtradecloud |  |
| 4 | Web Portal | 16-Apr-2020 12:24:56 CEST | #374 |  Development: create checkbox column with possibility select… | @bohdantrc |  |
| 5 | Services (Scala) | 15-Apr-2020 16:27:06 CEST | #1161 |  Investigate service stability when keyspaces are missing | @roy-tc |  |
| 6 | Services (Scala) | 15-Apr-2020 14:37:24 CEST | #1162 | DO NOT MERGE | @denys-kondartiuk |  |
| 7 | Services (Scala) | 15-Apr-2020 12:16:53 CEST | #1153 |  disable 2fa | @TizianoPerrucci |  |
| 8 | Services (Scala) | 15-Apr-2020 11:00:30 CEST | #772 |  add a flattened event index for kibana | @snevyd |  |
| 9 | Services (Scala) | 13-Apr-2020 15:58:03 CEST | #989 |  Proposal for routes cleanup | @roy-tc |  |
| 10 | Services (Scala) | 09-Apr-2020 13:40:02 CEST | #1143 |  Add migration whitelist, remove roles based rules | @marcmatt |  |
| 11 | Services (Scala) | 06-Apr-2020 15:15:29 CEST | #1138 |  Restructure SOAP logging statements to fix alerting | @roy-tc |  |
| 12 | Services (Scala) | 30-Mar-2020 10:38:21 CEST | #1117 |  - Incorrect line id if position contains special symbols | @denys-kondartiuk |  |

## Changelog

1. [](#) Refactor Kafka tests in shared library to use with Confluent Kafka
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Apr-2020 21:24:21 CEST | #373 |  enable login 2fa | @TizianoPerrucci |  |
| 2 | Services (Scala) | 16-Apr-2020 21:15:18 CEST | #1151 |  enable login 2fa | @TizianoPerrucci |  |
| 3 | Services (Go) | 16-Apr-2020 12:29:55 CEST | #280 |  - Fix &#39;ready:merge&#39; logic | @denys-kondartiuk |  |
| 4 | Services (Scala) | 16-Apr-2020 12:28:21 CEST | #1163 |  - Fix &#39;ready:merge&#39; logic | @denys-kondartiuk |  |
| 5 | Web Portal | 16-Apr-2020 12:28:06 CEST | #375 |  - Fix &#39;merge:ready&#39; logic | @denys-kondartiuk |  |
| 6 | Services (Scala) | 15-Apr-2020 14:29:36 CEST | #1157 |  Remove WorkflowTaskViewUpdated and add superuser OpenAPI specs | @roy-tc |  |
| 7 | Services (Go) | 15-Apr-2020 13:18:08 CEST | #279 |  - Move PR group scale to &#39;tcinfra&#39; | @denys-kondartiuk |  |
| 8 | Services (Scala) | 15-Apr-2020 13:18:01 CEST | #1160 |  - Move PR group scale to &#39;tcinfra&#39; | @denys-kondartiuk |  |
| 9 | Web Portal | 14-Apr-2020 11:09:29 CEST | #369 |  Add sales order number in propose changes | @bohdantrc |  |
| 10 | Web Portal | 14-Apr-2020 10:59:01 CEST | #371 | : Fixing bug related to double attaching document | @dmytrozheliuk |  |
| 11 | Web Portal | 14-Apr-2020 10:55:28 CEST | #372 |  Development: create confirm modal with input | @bohdantrc |  |
| 12 | Services (Scala) | 14-Apr-2020 10:04:13 CEST | #1150 | : Adjusted activity for bulk order action events | @dmytrozheliuk |  |
| 13 | Services (Scala) | 14-Apr-2020 09:11:03 CEST | #1159 |  Rename sbt project &#39;shared&#39; to &#39;microservices-shared&#39; | @vovinacci |  |
| 14 | Services (Scala) | 13-Apr-2020 15:44:08 CEST | #1156 |  Renamed shared module to microservices-shared | @aShevc |  |
| 15 | Services (Go) | 13-Apr-2020 15:16:43 CEST | #276 |  Updated logging mechanism for services | @aShevc |  |
| 16 | Services (Scala) | 13-Apr-2020 11:27:15 CEST | #1154 |  Renamed com.tradecloud1.shared to com.tradecloud1.microservices.shared | @aShevc |  |
| 17 | Services (Scala) | 13-Apr-2020 08:56:18 CEST | #1122 | [TC-5739] Reindex persisted entities | @roy-tc |  |
| 18 | Web Portal | 10-Apr-2020 17:27:28 CEST | #368 |  enable 2fa | @RobinNagpal |  |
| 19 | Services (Scala) | 10-Apr-2020 13:25:39 CEST | #1108 | TC-5494 enable 2fa | @TizianoPerrucci |  |
| 20 | Services (Scala) | 10-Apr-2020 12:30:56 CEST | #1149 |  SAP confirm: remove delivered filter | @marcmatt |  |
| 21 | Services (Scala) | 10-Apr-2020 10:52:57 CEST | #1119 |  Enrich supplier side order events in company service | @aShevc |  |
| 22 | Services (Scala) | 10-Apr-2020 10:03:09 CEST | #1148 |  - update readme | @olegtradecloud |  |
| 23 | Services (Go) | 09-Apr-2020 17:24:51 CEST | #262 |  Supplier webhook | @marcmatt |  |
| 24 | Services (Scala) | 09-Apr-2020 15:23:13 CEST | #1147 |  - remove retry on failure ES response | @olegtradecloud |  |
| 25 | Services (Scala) | 09-Apr-2020 13:09:02 CEST | #1145 |  sbt credentials | @olegtradecloud |  |
| 26 | Services (Go) | 09-Apr-2020 10:35:39 CEST | #274 |  Reflect new shared/util package function naming | @vovinacci |  |
| 27 | Services (Scala) | 09-Apr-2020 09:58:42 CEST | #1121 | [TC-5465]: Bulk actions API specs and implementation | @dmytrozheliuk |  |
| 28 | Services (Go) | 09-Apr-2020 08:51:28 CEST | #275 |  Fix &#39;x509: certificate signed by unknown authority&#39; | @vovinacci |  |
| 29 | Services (Go) | 08-Apr-2020 21:55:15 CEST | #273 |  Kafka: Update Confluent Kafka to 1.4.0 | @vovinacci |  |
| 30 | Services (Scala) | 08-Apr-2020 14:04:47 CEST | #1140 |  - fix workflow closedAt format | @olegtradecloud |  |
| 31 | Services (Scala) | 08-Apr-2020 12:05:53 CEST | #1144 | : Commit OrderDocumentsEvent when trying to authorize document which doesn&#39;t exi | @dmytrozheliuk |  |
| 32 | Services (Scala) | 08-Apr-2020 10:32:23 CEST | #1146 |  Deployment: simplify secrets | @vovinacci |  |
| 33 | Services (Go) | 07-Apr-2020 23:36:27 CEST | #271 |  Fix missing accp/prod Kafka secrets, remove unused cmd flag parsing | @vovinacci |  |
| 34 | Services (Go) | 07-Apr-2020 22:32:16 CEST | #270 |  Use newline when printing SSL related files | @vovinacci |  |
| 35 | Services (Go) | 07-Apr-2020 22:20:49 CEST | #268 |  Kafka: Add SSL support | @vovinacci |  |
| 36 | Services (Scala) | 06-Apr-2020 17:58:16 CEST | #1141 | : Settings downloaded file name though the amazon api headers | @dmytrozheliuk |  |
| 37 | Services (Go) | 03-Apr-2020 13:14:07 CEST | #267 |  - Fix &#39;tcinfra&#39; usage | @denys-kondartiuk |  |
| 38 | Services (Scala) | 03-Apr-2020 13:04:06 CEST | #1137 |  Deployment: Remove debugging | @vovinacci |  |
| 39 | Services (Scala) | 03-Apr-2020 12:52:49 CEST | #1136 |  Deployment: Simplify quotation | @vovinacci |  |
| 40 | Services (Scala) | 03-Apr-2020 12:42:41 CEST | #1135 |  Deployment: Fix quoting | @vovinacci |  |
| 41 | Services (Scala) | 03-Apr-2020 12:02:19 CEST | #1133 |  Simplify signature of TestKit | @roy-tc |  |
| 42 | Web Portal | 03-Apr-2020 11:59:32 CEST | #367 |  - Fix &#39;tcinfra&#39; call | @denys-kondartiuk |  |
| 43 | Web Portal | 03-Apr-2020 11:39:45 CEST | #366 |  - Reverse order for tcinfra arguments | @denys-kondartiuk |  |
| 44 | Web Portal | 03-Apr-2020 11:06:42 CEST | #365 |  - Portal Regression | @denys-kondartiuk |  |
| 45 | Services (Scala) | 02-Apr-2020 22:01:39 CEST | #1129 | : Fixed bug related to mixed up contentType and filename | @dmytrozheliuk |  |
| 46 | Services (Scala) | 02-Apr-2020 20:21:13 CEST | #1132 |  Fix order-integration example | @roy-tc |  |
| 47 | Web Portal | 02-Apr-2020 17:24:04 CEST | #363 |  Deployment: set correct API path for reset and recovery pas… | @bohdantrc |  |
| 48 | Services (Go) | 01-Apr-2020 19:33:30 CEST | #266 |  - Use &#39;tcinfra&#39; instead fo &#39;deploy_microservices.py&#39; to dep… | @denys-kondartiuk |  |
| 49 | Web Portal | 01-Apr-2020 19:25:24 CEST | #364 |  - Use &#39;tcinfra&#39; instead fo &#39;deploy_microservices.py&#39; to dep… | @denys-kondartiuk |  |
| 50 | Services (Scala) | 01-Apr-2020 19:10:24 CEST | #1128 |  - Use &#39;tcinfra&#39; instead of &#39;deploy_microservices.py&#39; for ac… | @denys-kondartiuk |  |
| 51 | Services (Scala) | 01-Apr-2020 16:55:13 CEST | #1127 |  Re-enable Voortman ztradecloud_interfaces in prod env | @marcmatt |  |
| 52 | Services (Go) | 01-Apr-2020 16:24:07 CEST | #265 |  Updated Kafka env variables | @aShevc |  |
| 53 | Services (Scala) | 01-Apr-2020 16:15:08 CEST | #1126 |  Update Kafka env variables | @aShevc |  |
| 54 | Services (Scala) | 31-Mar-2020 16:54:41 CEST | #1001 |  - add messages as library dependencies | @olegtradecloud |  |
| 55 | Services (Scala) | 30-Mar-2020 16:44:11 CEST | #1120 |  Provide simpler Mockito helper functions with an example of how to use | @roy-tc |  |
| 56 | Services (Scala) | 30-Mar-2020 13:59:59 CEST | #1106 | : Added salesOrderNumber to accept and propose line changes. | @dmytrozheliuk |  |
| 57 | Web Portal | 27-Mar-2020 13:48:27 CET | #360 |  unit test case issue | @jpuri |  |
| 58 | Web Portal | 27-Mar-2020 10:57:16 CET | #357 |  Rename priceInLocalCurrency to priceInTransactionCurrency | @roy-tc |  |
| 59 | Services (Scala) | 27-Mar-2020 10:55:53 CET | #1105 |  Rename *LocalCurrency to *TransactionCurrency | @roy-tc |  |
| 60 | Services (Scala) | 26-Mar-2020 19:57:42 CET | #1118 |  Add 4th C* node support | @vovinacci |  |
| 61 | Web Portal | 26-Mar-2020 10:30:20 CET | #359 | Logout user if refresh token fails. | @jpuri |  |
| 62 | Services (Go) | 25-Mar-2020 15:16:41 CET | #263 |  - Fix regression | @denys-kondartiuk |  |
| 63 | Services (Scala) | 25-Mar-2020 15:15:59 CET | #1112 |  - Fix regression | @denys-kondartiuk |  |
| 64 | Web Portal | 25-Mar-2020 15:14:41 CET | #361 |  - Fix regression | @denys-kondartiuk |  |
| 65 | Services (Go) | 24-Mar-2020 20:07:46 CET | #261 |  - GitHub labels PR flow | @denys-kondartiuk |  |
| 66 | Services (Scala) | 24-Mar-2020 19:44:08 CET | #1111 |  - New GitHub PR flow | @denys-kondartiuk |  |
| 67 | Web Portal | 24-Mar-2020 19:28:37 CET | #358 |  - New GitHub labels PR flow | @denys-kondartiuk |  |
| 68 | Web Portal | 24-Mar-2020 11:33:16 CET | #353 | Fix issue with application not loading data after short inactive period. | @jpuri |  |
| 69 | Services (Go) | 20-Mar-2020 17:22:45 CET | #259 |  - Make service versions consistent when running accp tests on Jenkins | @denys-kondartiuk |  |
| 70 | Services (Scala) | 20-Mar-2020 17:22:09 CET | #1107 |  - Make service versions consistent when running accp tests on Jenkins | @denys-kondartiuk |  |
| 71 | Services (Go) | 20-Mar-2020 16:33:07 CET | #260 |  - set webhook request content type | @olegtradecloud |  |
| 72 | Services (Scala) | 20-Mar-2020 12:55:47 CET | #1098 |  Support order line positions with hyphens | @roy-tc |  |
| 73 | Services (Scala) | 19-Mar-2020 16:26:06 CET | #1100 | : Added implementation based on *ing patterns. Extended tests | @dmytrozheliuk |  |
| 74 | Services (Scala) | 19-Mar-2020 14:44:37 CET | #1084 |  - add enrichment of OrderDocumentsEvent in company service | @olegtradecloud |  |
| 75 | Services (Go) | 19-Mar-2020 14:41:43 CET | #251 | - handle OutgoingOrderDocumentsAttached events | @olegtradecloud |  |
| 76 | Services (Scala) | 19-Mar-2020 12:37:35 CET | #1104 |  UAT: Fix concurrency issue | @vovinacci |  |
| 77 | Services (Go) | 19-Mar-2020 12:37:12 CET | #258 |  UAT: Fix concurrency issue | @vovinacci |  |
| 78 | Web Portal | 19-Mar-2020 12:04:03 CET | #351 | Style improvements in task chat. | @jpuri |  |
| 79 | Services (Go) | 18-Mar-2020 19:55:55 CET | #257 |  Deployment: Fix service version in proper place | @vovinacci |  |
| 80 | Services (Scala) | 18-Mar-2020 19:53:13 CET | #1103 |  Deployment: Fix service version in proper place | @vovinacci |  |
| 81 | Web Portal | 18-Mar-2020 19:00:21 CET | #350 | Bump acorn from 6.1.1 to 6.4.1 | @dependabot[bot] |  |
| 82 | Web Portal | 18-Mar-2020 18:52:05 CET | #356 |  Deployment: Fix service version in proper place | @vovinacci |  |
| 83 | Services (Scala) | 18-Mar-2020 18:10:29 CET | #1102 |  Deployment: Fix allowed character set in service version | @vovinacci |  |
| 84 | Web Portal | 18-Mar-2020 18:10:09 CET | #354 |  Deployment: Fix allowed character set in service version | @vovinacci |  |
| 85 | Services (Go) | 18-Mar-2020 18:09:52 CET | #256 |  Deployment: Fix allowed character set in service version | @vovinacci |  |
| 86 | Services (Scala) | 18-Mar-2020 17:48:21 CET | #1099 |  IndexRequest exception logging | @roy-tc |  |
| 87 | Services (Scala) | 18-Mar-2020 11:51:10 CET | #1101 |  Deployment: Address TODO list | @vovinacci |  |
| 88 | Web Portal | 17-Mar-2020 16:32:57 CET | #352 |  Deployment: Address TODO list | @vovinacci |  |
| 89 | Services (Go) | 17-Mar-2020 14:17:52 CET | #255 |  Deployment: Address TODO list | @vovinacci |  |
| 90 | Web Portal | 17-Mar-2020 11:56:26 CET | #349 |  Add details of attached document to activity. | @jpuri |  |
| 91 | Services (Go) | 17-Mar-2020 11:17:39 CET | #254 |  Kafka: Bump shared package, chores | @vovinacci |  |

