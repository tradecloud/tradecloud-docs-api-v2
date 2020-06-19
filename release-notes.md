---
description: Tradecloud services and portal open pull requests and changelog (Fri Jun 19 09:31:23 CEST 2020)
---


## Open Pull Requests

1. [TC-5805](https://tradecloud.atlassian.net/browse/TC-5805) Unrestrict 2FA by superuser and admin 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2020 20:48:57 CEST | [#1219](https://github.com/tradecloud/tradecloud-microservices/pull/1219) |  Unrestrict 2FA | @RobinNagpal |  |
| 2 | Web Portal | 18-Jun-2020 19:11:00 CEST | [#402](https://github.com/tradecloud/tradecloud-portal-angular/pull/402) |  Unrestrict 2fa | @RobinNagpal |  |

2. [TC-6035](https://tradecloud.atlassian.net/browse/TC-6035) Check for authenticated status during websocket connection 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2020 19:50:21 CEST | [#1236](https://github.com/tradecloud/tradecloud-microservices/pull/1236) |  update shared version(check authentication status) | @RobinNagpal |  |

3. [TC-6042](https://tradecloud.atlassian.net/browse/TC-6042) BE: process cancelled indicator in order service, persist, publish event, create activity, close order line tasks 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2020 17:51:39 CEST | [#1235](https://github.com/tradecloud/tradecloud-microservices/pull/1235) | : Added order lines cancelling functionality | @dmytrozheliuk |  |

4. [TC-6002](https://tradecloud.atlassian.net/browse/TC-6002) FE: As a supplier I want approve or reject a reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 18-Jun-2020 16:20:32 CEST | [#416](https://github.com/tradecloud/tradecloud-portal-angular/pull/416) |  add approve/reject from supplier | @bohdantrc |  |

5. [TC-6006](https://tradecloud.atlassian.net/browse/TC-6006) Activity event is created on bulk actions even if action is not allowed 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2020 15:43:48 CEST | [#1234](https://github.com/tradecloud/tradecloud-microservices/pull/1234) |  Create optional event on order bulk accept | @olegtradecloud |  |

6. [TC-4467](https://tradecloud.atlassian.net/browse/TC-4467) As a DevOps I want to be able to re-build a search index [Planned release 05-Jun-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2020 12:56:48 CEST | [#1229](https://github.com/tradecloud/tradecloud-microservices/pull/1229) |  Remove CompanyUserSynced | @roy-tc |  |

7. [TC-5640](https://tradecloud.atlassian.net/browse/TC-5640) As product management I want to show product info on the dashboard page 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-May-2020 11:36:19 CEST | [#400](https://github.com/tradecloud/tradecloud-portal-angular/pull/400) |  Change aside part in dashboard | @bohdantrc |  |

8. [TC-5789](https://tradecloud.atlassian.net/browse/TC-5789) Some SAP fetch requests are lost and not retried in case of SAP 503 Service Unavailable. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-May-2020 11:04:10 CEST | [#1138](https://github.com/tradecloud/tradecloud-microservices/pull/1138) |  Restructure SOAP logging statements to fix alerting | @roy-tc |  |

## Changelog

1. [TC-5956](https://tradecloud.atlassian.net/browse/TC-5956) As Damen security officer I want the TOTP verification to use 2 time windows. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2020 22:32:21 CEST | [#1237](https://github.com/tradecloud/tradecloud-microservices/pull/1237) |   update 2FA window size to 2 | @RobinNagpal |  |

2. [TC-5997](https://tradecloud.atlassian.net/browse/TC-5997) FE: As a buyer I want approve or reject a reopen request by supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 18:16:11 CEST | [#410](https://github.com/tradecloud/tradecloud-portal-angular/pull/410) |  Add approve reject for buyer in workflow task | @bohdantrc |  |

3. [TC-5874](https://tradecloud.atlassian.net/browse/TC-5874) BE: refactor line proposal to LineRequests 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 17-Jun-2020 16:38:42 CEST | [#315](https://github.com/tradecloud/tradecloud-microservices-go/pull/315) |  Fix webhook API specs semantic error | @marcmatt |  |

4. [TC-6024](https://tradecloud.atlassian.net/browse/TC-6024) When request is “reopenRequest” the confirm/propose changes/reject buttons should not be visible for the supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 15:49:44 CEST | [#413](https://github.com/tradecloud/tradecloud-portal-angular/pull/413) |  Disable the ability to see buttons for a proposal entity like &#34;Confirm&#34;, &#34;Propo | @bohdantrc |  |

5. [TC-6025](https://tradecloud.atlassian.net/browse/TC-6025) supplierLine reopenRequest values are shown after a Buyer has rejected the reopen reqeust.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 14:57:58 CEST | [#414](https://github.com/tradecloud/tradecloud-portal-angular/pull/414) |  Show order line details from SupplierLine reopenRequest when reopen with status | @bohdantrc |  |

6. [TC-5555](https://tradecloud.atlassian.net/browse/TC-5555) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 09:07:15 CEST | [#415](https://github.com/tradecloud/tradecloud-portal-angular/pull/415) |  Add env variable for show/hide reopen button | @bohdantrc |  |
| 2 | Web Portal | 11-Jun-2020 23:05:25 CEST | [#409](https://github.com/tradecloud/tradecloud-portal-angular/pull/409) |  fix model workflow | @bohdantrc |  |
| 3 | Web Portal | 11-Jun-2020 14:21:57 CEST | [#407](https://github.com/tradecloud/tradecloud-portal-angular/pull/407) |  fix RFQ imports for correct build | @bohdantrc |  |
| 4 | Services (Scala) | 11-Jun-2020 10:32:33 CEST | [#1231](https://github.com/tradecloud/tradecloud-microservices/pull/1231) |  Catch NotFound and properly log. Also enhance spec to avoid exceptions | @roy-tc |  |
| 5 | Services (Go) | 05-Jun-2020 18:49:36 CEST | [#311](https://github.com/tradecloud/tradecloud-microservices-go/pull/311) |  Fix Kafka group logging (this time for real) | @vovinacci |  |
| 6 | Services (Go) | 05-Jun-2020 12:21:42 CEST | [#310](https://github.com/tradecloud/tradecloud-microservices-go/pull/310) |  Fix Kafka group logging | @vovinacci |  |
| 7 | Services (Go) | 21-May-2020 19:48:10 CEST | [#302](https://github.com/tradecloud/tradecloud-microservices-go/pull/302) |  Packages: Update dependencies | @vovinacci |  |
| 8 | Services (Scala) | 20-May-2020 13:27:54 CEST | [#1221](https://github.com/tradecloud/tradecloud-microservices/pull/1221) | : Bump messages | @dmytrozheliuk |  |
| 9 | Services (Go) | 20-May-2020 10:23:48 CEST | [#299](https://github.com/tradecloud/tradecloud-microservices-go/pull/299) |  - Remove direct kitLogger usage | @denys-kondartiuk |  |
| 10 | Services (Go) | 19-May-2020 13:39:22 CEST | [#298](https://github.com/tradecloud/tradecloud-microservices-go/pull/298) |  - Remove kitLogger from makeRoutes | @denys-kondartiuk |  |
| 11 | Services (Go) | 19-May-2020 10:34:14 CEST | [#296](https://github.com/tradecloud/tradecloud-microservices-go/pull/296) |  - Remove unnecessary wrapper for logging | @denys-kondartiuk |  |

7. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2020 19:19:37 CEST | [#406](https://github.com/tradecloud/tradecloud-portal-angular/pull/406) | Bump websocket-extensions from 0.1.3 to 0.1.4 | @dependabot[bot] |  |
| 2 | Web Portal | 22-May-2020 13:37:25 CEST | [#393](https://github.com/tradecloud/tradecloud-portal-angular/pull/393) | testing refresh | @bohdantrc |  |

8. [TC-6023](https://tradecloud.atlassian.net/browse/TC-6023) &#34;Reopen request&#34; button should have the same color as the &#34;propose changes&#34; button 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2020 17:15:27 CEST | [#412](https://github.com/tradecloud/tradecloud-portal-angular/pull/412) |  change color refresh button | @bohdantrc |  |

9. [TC-5958](https://tradecloud.atlassian.net/browse/TC-5958) Refactor OrderEvents.id to orderId 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 16-Jun-2020 16:00:45 CEST | [#312](https://github.com/tradecloud/tradecloud-microservices-go/pull/312) |  Rename OrderEvent.id to orderId | @roy-tc |  |
| 2 | Services (Scala) | 16-Jun-2020 16:00:35 CEST | [#1222](https://github.com/tradecloud/tradecloud-microservices/pull/1222) |  Rename OrderEvent.id to orderId | @roy-tc |  |

10. [TC-6022](https://tradecloud.atlassian.net/browse/TC-6022) VMI bug fix: Tasks and Order (line) detail pages are not updated automatically after an action.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2020 14:13:05 CEST | [#411](https://github.com/tradecloud/tradecloud-portal-angular/pull/411) |   update and fix the booting sequence after login | @RobinNagpal |  |
| 2 | Web Portal | 11-Jun-2020 22:29:45 CEST | [#408](https://github.com/tradecloud/tradecloud-portal-angular/pull/408) |  call setIdentify with listening ws instead authSetIdentityW… | @bohdantrc |  |

11. [TC-5883](https://tradecloud.atlassian.net/browse/TC-5883) As integrated user, I want to get order updates if a reopen request is accepted 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Jun-2020 12:02:22 CEST | [#1233](https://github.com/tradecloud/tradecloud-microservices/pull/1233) | : Added listeners for outgoing events for approve/reject reopen requests actions | @dmytrozheliuk |  |
| 2 | Services (Go) | 16-Jun-2020 12:02:18 CEST | [#314](https://github.com/tradecloud/tradecloud-microservices-go/pull/314) | : Added webhooks for approve/reject reopen request by buyer/… | @dmytrozheliuk |  |

12. [TC-5867](https://tradecloud.atlassian.net/browse/TC-5867) Process reopen request in order service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 11-Jun-2020 17:55:14 CEST | [#308](https://github.com/tradecloud/tradecloud-microservices-go/pull/308) |  Buyer reopen request | @olegtradecloud |  |
| 2 | Services (Scala) | 11-Jun-2020 17:47:04 CEST | [#1213](https://github.com/tradecloud/tradecloud-microservices/pull/1213) |  Buyer reopen request | @olegtradecloud |  |

13. [TC-5869](https://tradecloud.atlassian.net/browse/TC-5869) BE: approve / reject reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 16:57:58 CEST | [#404](https://github.com/tradecloud/tradecloud-portal-angular/pull/404) |  buyer approve reject | @bohdantrc |  |
| 2 | Services (Scala) | 10-Jun-2020 10:32:07 CEST | [#1223](https://github.com/tradecloud/tradecloud-microservices/pull/1223) | : Added approve/reject functionality by buyer/supplier | @dmytrozheliuk |  |

14. [TC-5996](https://tradecloud.atlassian.net/browse/TC-5996) FE: reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 16:57:56 CEST | [#405](https://github.com/tradecloud/tradecloud-portal-angular/pull/405) |  add buyer reopen request show in ORDER LINE DETAILS column | @bohdantrc |  |

15. [TC-5957](https://tradecloud.atlassian.net/browse/TC-5957) Create Mockup for RFQ / Proposal process 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 12:43:38 CEST | [#403](https://github.com/tradecloud/tradecloud-portal-angular/pull/403) |  Provide RFQ mockups | @bohdantrc |  |

16. [TC-6007](https://tradecloud.atlassian.net/browse/TC-6007) Remove `order-integration` service completely 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Jun-2020 10:34:13 CEST | [#1230](https://github.com/tradecloud/tradecloud-microservices/pull/1230) |  Remove &#39;order-integration&#39; service | @vovinacci |  |

17. [TC-5701](https://tradecloud.atlassian.net/browse/TC-5701) As DevOps I want to upgrade &#39;gokit&#39; to latest version 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 10-Jun-2020 20:29:43 CEST | [#313](https://github.com/tradecloud/tradecloud-microservices-go/pull/313) |  Update go-kit to &#39;0.10.0&#39; | @vovinacci |  |

18. [TC-5786](https://tradecloud.atlassian.net/browse/TC-5786) BE: reopen request support  in activity service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jun-2020 10:59:06 CEST | [#1227](https://github.com/tradecloud/tradecloud-microservices/pull/1227) |  Activity reopen request | @olegtradecloud |  |

19. [TC-5868](https://tradecloud.atlassian.net/browse/TC-5868) Workflow tasks for reopen requests 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 09-Jun-2020 16:40:26 CEST | [#1228](https://github.com/tradecloud/tradecloud-microservices/pull/1228) |  Workflow reopen requests | @olegtradecloud |  |
| 2 | Services (Scala) | 01-Jun-2020 18:12:36 CEST | [#1225](https://github.com/tradecloud/tradecloud-microservices/pull/1225) |   - workflow reopen requests | @olegtradecloud |  |

20. [TC-5784](https://tradecloud.atlassian.net/browse/TC-5784) FE: Reopen request by supplier  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Jun-2020 13:53:12 CEST | [#395](https://github.com/tradecloud/tradecloud-portal-angular/pull/395) |  add reopen request dialog | @bohdantrc |  |

21. [TC-4478](https://tradecloud.atlassian.net/browse/TC-4478) As a supplier I want to reopen order lines 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Jun-2020 13:49:22 CEST | [#1206](https://github.com/tradecloud/tradecloud-microservices/pull/1206) | [TC-5782] Reopen request by supplier | @roy-tc |  |

22. [TC-5803](https://tradecloud.atlassian.net/browse/TC-5803) Enforce 2FA by superuser and admin for new users  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 03-Jun-2020 14:39:41 CEST | [#1217](https://github.com/tradecloud/tradecloud-microservices/pull/1217) |  enforce 2fa new users | @RobinNagpal |  |
| 2 | Web Portal | 03-Jun-2020 14:08:45 CEST | [#401](https://github.com/tradecloud/tradecloud-portal-angular/pull/401) |  Enforce 2fa new users | @RobinNagpal |  |

23. [TC-5804](https://tradecloud.atlassian.net/browse/TC-5804) Enforce 2FA by superuser and admin for existing users  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 03-Jun-2020 13:59:41 CEST | [#1185](https://github.com/tradecloud/tradecloud-microservices/pull/1185) |  Enforce 2FA company level | @RobinNagpal |  |
| 2 | Services (Go) | 03-Jun-2020 13:59:13 CEST | [#297](https://github.com/tradecloud/tradecloud-microservices-go/pull/297) |  - add enforce2FA setting | @RobinNagpal |  |
| 3 | Web Portal | 03-Jun-2020 13:53:35 CEST | [#390](https://github.com/tradecloud/tradecloud-portal-angular/pull/390) |  Enforce 2FA company level | @RobinNagpal |  |

24. [TC-5702](https://tradecloud.atlassian.net/browse/TC-5702) As DevOps I want to update Go to 1.14 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 03-Jun-2020 07:57:54 CEST | [#307](https://github.com/tradecloud/tradecloud-microservices-go/pull/307) |  Update to Go 1.14, refactor messages handling | @vovinacci |  |

25. [TC-5993](https://tradecloud.atlassian.net/browse/TC-5993) As DevOps I want to log Kafka consumer name in Go services 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 02-Jun-2020 09:39:36 CEST | [#306](https://github.com/tradecloud/tradecloud-microservices-go/pull/306) |  Log Kafka consumer group name | @vovinacci |  |

26. [TC-5771](https://tradecloud.atlassian.net/browse/TC-5771) As DevOps I want deployment environmental variables to be consistent beween Go and Scala services. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 01-Jun-2020 19:11:39 CEST | [#305](https://github.com/tradecloud/tradecloud-microservices-go/pull/305) |  Make env variables naming consistent | @vovinacci |  |

27. [TC-4661](https://tradecloud.atlassian.net/browse/TC-4661) Email links have blue text on blue buttons in Gmail 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 28-May-2020 10:12:32 CEST | [#304](https://github.com/tradecloud/tradecloud-microservices-go/pull/304) |  Set white color for button text | @bohdantrc |  |

28. [TC-5950](https://tradecloud.atlassian.net/browse/TC-5950) Remove the &#34;approve proposal&#34; button after a buyer has rejected the proposal.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-May-2020 15:19:24 CEST | [#399](https://github.com/tradecloud/tradecloud-portal-angular/pull/399) |  change condition for approve proposal by a buyer | @bohdantrc |  |

29. [TC-5737](https://tradecloud.atlassian.net/browse/TC-5737) Incorrect line id if position contains special symbols 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-May-2020 11:33:03 CEST | [#388](https://github.com/tradecloud/tradecloud-portal-angular/pull/388) |  Development: Add encoded id in GET requests | @bohdantrc |  |
| 2 | Services (Scala) | 26-May-2020 11:32:41 CEST | [#1117](https://github.com/tradecloud/tradecloud-microservices/pull/1117) |  Incorrect line id if position contains special symbols | @denys-kondartiuk |  |

30. [TC-5491](https://tradecloud.atlassian.net/browse/TC-5491) As a QA I want refresh tokens to be tested by Portal unit tests 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-May-2020 17:48:16 CEST | [#397](https://github.com/tradecloud/tradecloud-portal-angular/pull/397) |  enable and fix spec files, clean code | @bohdantrc |  |

31. [TC-5782](https://tradecloud.atlassian.net/browse/TC-5782) BE: reopen order request by supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-May-2020 15:21:11 CEST | [#396](https://github.com/tradecloud/tradecloud-portal-angular/pull/396) |  add check prices in proposal | @bohdantrc |  |
| 2 | Services (Scala) | 25-May-2020 15:20:35 CEST | [#1220](https://github.com/tradecloud/tradecloud-microservices/pull/1220) |  Revert &#34;Make Prices required everywhere&#34; | @marcmatt |  |

32. [TC-5925](https://tradecloud.atlassian.net/browse/TC-5925) Go lang services must check JWT token status 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 21-May-2020 14:44:22 CEST | [#300](https://github.com/tradecloud/tradecloud-microservices-go/pull/300) |  2FA: Fix JWT token status | @TizianoPerrucci |  |

33. [TC-5968](https://tradecloud.atlassian.net/browse/TC-5968) Implement addition function for service actions logs 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 21-May-2020 10:46:16 CEST | [#301](https://github.com/tradecloud/tradecloud-microservices-go/pull/301) |  Use &#39;LogfWithTime&#39; instead &#39;Err&#39; for services actions logs | @denys-kondartiuk |  |

34. [TC-5961](https://tradecloud.atlassian.net/browse/TC-5961) Align the Confirm, reject and propose changes buttons in the Order and line detail pages 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 20-May-2020 16:17:42 CEST | [#394](https://github.com/tradecloud/tradecloud-portal-angular/pull/394) |  Set same sequence actions in order and order line detail page | @bohdantrc |  |

35. [TC-5861](https://tradecloud.atlassian.net/browse/TC-5861) NEEDS DATA WIPE  - BE: Add changes to the domain model for new activity design 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-May-2020 14:39:03 CEST | [#392](https://github.com/tradecloud/tradecloud-portal-angular/pull/392) | [TC-5863] Change model for activity and disable required field in confirm dialog | @bohdantrc |  |
| 2 | Services (Scala) | 19-May-2020 14:38:46 CEST | [#1189](https://github.com/tradecloud/tradecloud-microservices/pull/1189) | : Optimizing activity model by replacing string json content | @dmytrozheliuk |  |

