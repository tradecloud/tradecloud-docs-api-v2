---
description: Tradecloud services and portal open pull requests and changelog (Mon Jun 29 13:31:02 CEST 2020)
---


## Open Pull Requests

1. [TC-5929](https://tradecloud.atlassian.net/browse/TC-5929) When a user authenticates with 2FA validate, a new refresh token is created 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 28-Jun-2020 22:26:50 CEST | [#428](https://github.com/tradecloud/tradecloud-portal-angular/pull/428) |  set auth token even if refresh token is not there | @RobinNagpal |  |
| 2 | Services (Scala) | 26-Jun-2020 09:15:08 CEST | [#1243](https://github.com/tradecloud/tradecloud-microservices/pull/1243) |  Do not set refresh token until fully authenticated | @TizianoPerrucci |  |

2. [TC-6042](https://tradecloud.atlassian.net/browse/TC-6042) BE: process cancelled indicator in order service, persist, publish event, create activity, close order line tasks 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 26-Jun-2020 15:29:49 CEST | [#1244](https://github.com/tradecloud/tradecloud-microservices/pull/1244) |  Send cancel order as separate command | @roy-tc |  |
| 2 | Services (Scala) | 25-Jun-2020 13:31:26 CEST | [#1235](https://github.com/tradecloud/tradecloud-microservices/pull/1235) | : Added order lines cancelling functionality | @dmytrozheliuk |  |

3. [TC-6088](https://tradecloud.atlassian.net/browse/TC-6088) The confirm/reject/propose changes buttons are not visible anymore for supplier when &#34;proposal&#34; is in open or rejected status. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 14:29:59 CEST | [#426](https://github.com/tradecloud/tradecloud-portal-angular/pull/426) |  change condition for show confirm actions | @bohdantrc |  |

4. [TC-6043](https://tradecloud.atlassian.net/browse/TC-6043) FE: Display line level activities with ActivityType OrderLineCancelledByBuyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:10:31 CEST | [#427](https://github.com/tradecloud/tradecloud-portal-angular/pull/427) |  Add new type `order-line-cancelled-by-buyer` in activity | @bohdantrc |  |

5. [TC-6054](https://tradecloud.atlassian.net/browse/TC-6054) Damen feedback related to Item details 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jun-2020 13:14:01 CEST | [#424](https://github.com/tradecloud/tradecloud-portal-angular/pull/424) |  change title in item details component and update countries | @bohdantrc |  |

6. [TC-6062](https://tradecloud.atlassian.net/browse/TC-6062) QA: 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jun-2020 13:10:25 CEST | [#425](https://github.com/tradecloud/tradecloud-portal-angular/pull/425) |  rename text in link | @bohdantrc |  |

7. [TC-5944](https://tradecloud.atlassian.net/browse/TC-5944) Centralize business rules in order service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-Jun-2020 12:00:09 CEST | [#1242](https://github.com/tradecloud/tradecloud-microservices/pull/1242) |  - multiple events  | @olegtradecloud |  |

8. [TC-5916](https://tradecloud.atlassian.net/browse/TC-5916) Use enumeratum for enums to avoid JSON deserialization issues 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 25-Jun-2020 11:57:24 CEST | [#1241](https://github.com/tradecloud/tradecloud-microservices/pull/1241) |  Use Enumeratum lib for enums | @roy-tc |  |

9. [TC-6006](https://tradecloud.atlassian.net/browse/TC-6006) Activity event is created on bulk actions even if action is not allowed 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 17-Jun-2020 15:43:48 CEST | [#1234](https://github.com/tradecloud/tradecloud-microservices/pull/1234) |  Create optional event on order bulk accept | @olegtradecloud |  |

## Changelog

1. [TC-6102](https://tradecloud.atlassian.net/browse/TC-6102) IncomingOrderDocumentsAttachedByBuyer is retried forever when the purchase order number cannot be found 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jun-2020 21:26:33 CEST | [#1245](https://github.com/tradecloud/tradecloud-microservices/pull/1245) |  Commit when order/line is not found | @marcmatt |  |

2. [TC-6036](https://tradecloud.atlassian.net/browse/TC-6036) As a supplier I cannot enter a quantity decimal number in proposal and reopen request dialog 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:59:55 CEST | [#423](https://github.com/tradecloud/tradecloud-portal-angular/pull/423) |  Set decimal number for quantity and price unit quantity in requests | @bohdantrc |  |

3. [TC-6018](https://tradecloud.atlassian.net/browse/TC-6018) &#34;create your password&#34; screen is shown when a new user refresh the &#34;enable 2FA page&#34;  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:59:15 CEST | [#420](https://github.com/tradecloud/tradecloud-portal-angular/pull/420) |  create secret on 2fa screen when refreshed | @RobinNagpal |  |

4. [TC-6037](https://tradecloud.atlassian.net/browse/TC-6037) Reopen request by supplier is not visible in supplier tab in order line detail page 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:57:22 CEST | [#419](https://github.com/tradecloud/tradecloud-portal-angular/pull/419) |  add in supplier tab info about open reopen request | @bohdantrc |  |

5. [TC-6074](https://tradecloud.atlassian.net/browse/TC-6074) Show exceptionReason value, in case of a reopen request, in workflow and activity 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jun-2020 22:15:28 CEST | [#422](https://github.com/tradecloud/tradecloud-portal-angular/pull/422) |  show `reopen request reason` if it was created by buyer | @bohdantrc |  |

6. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-Jun-2020 13:08:47 CEST | [#421](https://github.com/tradecloud/tradecloud-portal-angular/pull/421) | bugfix(2fa setup):[TC-6018]  fix spelling | @RobinNagpal |  |
| 2 | Web Portal | 16-Jun-2020 19:19:37 CEST | [#406](https://github.com/tradecloud/tradecloud-portal-angular/pull/406) | Bump websocket-extensions from 0.1.3 to 0.1.4 | @dependabot[bot] |  |

7. [TC-6051](https://tradecloud.atlassian.net/browse/TC-6051) BE: Add confirmedLine in activity model 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 24-Jun-2020 13:00:25 CEST | [#1239](https://github.com/tradecloud/tradecloud-microservices/pull/1239) | : version bump | @dmytrozheliuk |  |

8. [TC-5794](https://tradecloud.atlassian.net/browse/TC-5794) FE: reopen request by buyer activities 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-Jun-2020 09:21:27 CEST | [#418](https://github.com/tradecloud/tradecloud-portal-angular/pull/418) |  add activity types for buyer reopen request activities | @bohdantrc |  |

9. [TC-5787](https://tradecloud.atlassian.net/browse/TC-5787) FE: reopen request by supplier activities 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 23-Jun-2020 15:44:38 CEST | [#417](https://github.com/tradecloud/tradecloud-portal-angular/pull/417) |  add activity for supplier reopen request activities | @bohdantrc |  |

10. [TC-6042](https://tradecloud.atlassian.net/browse/TC-6042) BE: process cancelled indicator in order service, persist, publish event, create activity, close order line tasks 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Jun-2020 11:18:30 CEST | [#1238](https://github.com/tradecloud/tradecloud-microservices/pull/1238) |  Improvements to Added order lines cancelling functionality | @roy-tc |  |

11. [TC-5805](https://tradecloud.atlassian.net/browse/TC-5805) Unrestrict 2FA by superuser and admin 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-Jun-2020 14:51:23 CEST | [#402](https://github.com/tradecloud/tradecloud-portal-angular/pull/402) |  Unrestrict 2fa | @RobinNagpal |  |
| 2 | Services (Scala) | 19-Jun-2020 14:50:44 CEST | [#1219](https://github.com/tradecloud/tradecloud-microservices/pull/1219) |  Unrestrict 2FA | @RobinNagpal |  |

12. [TC-6002](https://tradecloud.atlassian.net/browse/TC-6002) FE: As a supplier I want approve or reject a reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-Jun-2020 13:31:15 CEST | [#416](https://github.com/tradecloud/tradecloud-portal-angular/pull/416) |  add approve/reject from supplier | @bohdantrc |  |

13. [TC-4467](https://tradecloud.atlassian.net/browse/TC-4467) As a DevOps I want to be able to re-build a search index 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Jun-2020 11:06:16 CEST | [#1229](https://github.com/tradecloud/tradecloud-microservices/pull/1229) |  Remove CompanyUserSynced | @roy-tc |  |

14. [TC-6035](https://tradecloud.atlassian.net/browse/TC-6035) Check for authenticated status during websocket connection 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Jun-2020 09:47:16 CEST | [#1236](https://github.com/tradecloud/tradecloud-microservices/pull/1236) |  update shared version(check authentication status) | @RobinNagpal |  |

15. [TC-5956](https://tradecloud.atlassian.net/browse/TC-5956) As Damen security officer I want the TOTP verification to use 2 time windows. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2020 22:32:21 CEST | [#1237](https://github.com/tradecloud/tradecloud-microservices/pull/1237) |   update 2FA window size to 2 | @RobinNagpal |  |

16. [TC-5997](https://tradecloud.atlassian.net/browse/TC-5997) FE: As a buyer I want approve or reject a reopen request by supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 18:16:11 CEST | [#410](https://github.com/tradecloud/tradecloud-portal-angular/pull/410) |  Add approve reject for buyer in workflow task | @bohdantrc |  |

17. [TC-5874](https://tradecloud.atlassian.net/browse/TC-5874) BE: refactor line proposal to LineRequests 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 17-Jun-2020 16:38:42 CEST | [#315](https://github.com/tradecloud/tradecloud-microservices-go/pull/315) |  Fix webhook API specs semantic error | @marcmatt |  |

18. [TC-6024](https://tradecloud.atlassian.net/browse/TC-6024) When request is “reopenRequest” the confirm/propose changes/reject buttons should not be visible for the supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 15:49:44 CEST | [#413](https://github.com/tradecloud/tradecloud-portal-angular/pull/413) |  Disable the ability to see buttons for a proposal entity like &#34;Confirm&#34;, &#34;Propo | @bohdantrc |  |

19. [TC-6025](https://tradecloud.atlassian.net/browse/TC-6025) supplierLine reopenRequest values are shown after a Buyer has rejected the reopen reqeust.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 14:57:58 CEST | [#414](https://github.com/tradecloud/tradecloud-portal-angular/pull/414) |  Show order line details from SupplierLine reopenRequest when reopen with status | @bohdantrc |  |

20. [TC-5555](https://tradecloud.atlassian.net/browse/TC-5555) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 09:07:15 CEST | [#415](https://github.com/tradecloud/tradecloud-portal-angular/pull/415) |  Add env variable for show/hide reopen button | @bohdantrc |  |
| 2 | Web Portal | 11-Jun-2020 23:05:25 CEST | [#409](https://github.com/tradecloud/tradecloud-portal-angular/pull/409) |  fix model workflow | @bohdantrc |  |
| 3 | Web Portal | 11-Jun-2020 14:21:57 CEST | [#407](https://github.com/tradecloud/tradecloud-portal-angular/pull/407) |  fix RFQ imports for correct build | @bohdantrc |  |
| 4 | Services (Scala) | 11-Jun-2020 10:32:33 CEST | [#1231](https://github.com/tradecloud/tradecloud-microservices/pull/1231) |  Catch NotFound and properly log. Also enhance spec to avoid exceptions | @roy-tc |  |
| 5 | Services (Go) | 05-Jun-2020 18:49:36 CEST | [#311](https://github.com/tradecloud/tradecloud-microservices-go/pull/311) |  Fix Kafka group logging (this time for real) | @vovinacci |  |
| 6 | Services (Go) | 05-Jun-2020 12:21:42 CEST | [#310](https://github.com/tradecloud/tradecloud-microservices-go/pull/310) |  Fix Kafka group logging | @vovinacci |  |

21. [TC-6023](https://tradecloud.atlassian.net/browse/TC-6023) &#34;Reopen request&#34; button should have the same color as the &#34;propose changes&#34; button 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2020 17:15:27 CEST | [#412](https://github.com/tradecloud/tradecloud-portal-angular/pull/412) |  change color refresh button | @bohdantrc |  |

22. [TC-5958](https://tradecloud.atlassian.net/browse/TC-5958) Refactor OrderEvents.id to orderId 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 16-Jun-2020 16:00:45 CEST | [#312](https://github.com/tradecloud/tradecloud-microservices-go/pull/312) |  Rename OrderEvent.id to orderId | @roy-tc |  |
| 2 | Services (Scala) | 16-Jun-2020 16:00:35 CEST | [#1222](https://github.com/tradecloud/tradecloud-microservices/pull/1222) |  Rename OrderEvent.id to orderId | @roy-tc |  |

23. [TC-6022](https://tradecloud.atlassian.net/browse/TC-6022) VMI bug fix: Tasks and Order (line) detail pages are not updated automatically after an action.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2020 14:13:05 CEST | [#411](https://github.com/tradecloud/tradecloud-portal-angular/pull/411) |   update and fix the booting sequence after login | @RobinNagpal |  |
| 2 | Web Portal | 11-Jun-2020 22:29:45 CEST | [#408](https://github.com/tradecloud/tradecloud-portal-angular/pull/408) |  call setIdentify with listening ws instead authSetIdentityW… | @bohdantrc |  |

24. [TC-5883](https://tradecloud.atlassian.net/browse/TC-5883) As integrated user, I want to get order updates if a reopen request is accepted 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Jun-2020 12:02:22 CEST | [#1233](https://github.com/tradecloud/tradecloud-microservices/pull/1233) | : Added listeners for outgoing events for approve/reject reopen requests actions | @dmytrozheliuk |  |
| 2 | Services (Go) | 16-Jun-2020 12:02:18 CEST | [#314](https://github.com/tradecloud/tradecloud-microservices-go/pull/314) | : Added webhooks for approve/reject reopen request by buyer/… | @dmytrozheliuk |  |

25. [TC-5867](https://tradecloud.atlassian.net/browse/TC-5867) Process reopen request in order service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 11-Jun-2020 17:55:14 CEST | [#308](https://github.com/tradecloud/tradecloud-microservices-go/pull/308) |  Buyer reopen request | @olegtradecloud |  |
| 2 | Services (Scala) | 11-Jun-2020 17:47:04 CEST | [#1213](https://github.com/tradecloud/tradecloud-microservices/pull/1213) |  Buyer reopen request | @olegtradecloud |  |

26. [TC-5869](https://tradecloud.atlassian.net/browse/TC-5869) BE: approve / reject reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 16:57:58 CEST | [#404](https://github.com/tradecloud/tradecloud-portal-angular/pull/404) |  buyer approve reject | @bohdantrc |  |
| 2 | Services (Scala) | 10-Jun-2020 10:32:07 CEST | [#1223](https://github.com/tradecloud/tradecloud-microservices/pull/1223) | : Added approve/reject functionality by buyer/supplier | @dmytrozheliuk |  |

27. [TC-5996](https://tradecloud.atlassian.net/browse/TC-5996) FE: reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 16:57:56 CEST | [#405](https://github.com/tradecloud/tradecloud-portal-angular/pull/405) |  add buyer reopen request show in ORDER LINE DETAILS column | @bohdantrc |  |

28. [TC-5957](https://tradecloud.atlassian.net/browse/TC-5957) Create Mockup for RFQ / Proposal process 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 12:43:38 CEST | [#403](https://github.com/tradecloud/tradecloud-portal-angular/pull/403) |  Provide RFQ mockups | @bohdantrc |  |

29. [TC-6007](https://tradecloud.atlassian.net/browse/TC-6007) Remove `order-integration` service completely 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Jun-2020 10:34:13 CEST | [#1230](https://github.com/tradecloud/tradecloud-microservices/pull/1230) |  Remove &#39;order-integration&#39; service | @vovinacci |  |

30. [TC-5701](https://tradecloud.atlassian.net/browse/TC-5701) As DevOps I want to upgrade &#39;gokit&#39; to latest version 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 10-Jun-2020 20:29:43 CEST | [#313](https://github.com/tradecloud/tradecloud-microservices-go/pull/313) |  Update go-kit to &#39;0.10.0&#39; | @vovinacci |  |

31. [TC-5786](https://tradecloud.atlassian.net/browse/TC-5786) BE: reopen request support  in activity service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jun-2020 10:59:06 CEST | [#1227](https://github.com/tradecloud/tradecloud-microservices/pull/1227) |  Activity reopen request | @olegtradecloud |  |

32. [TC-5868](https://tradecloud.atlassian.net/browse/TC-5868) Workflow tasks for reopen requests 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 09-Jun-2020 16:40:26 CEST | [#1228](https://github.com/tradecloud/tradecloud-microservices/pull/1228) |  Workflow reopen requests | @olegtradecloud |  |
| 2 | Services (Scala) | 01-Jun-2020 18:12:36 CEST | [#1225](https://github.com/tradecloud/tradecloud-microservices/pull/1225) |   - workflow reopen requests | @olegtradecloud |  |

33. [TC-5784](https://tradecloud.atlassian.net/browse/TC-5784) FE: Reopen request by supplier  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Jun-2020 13:53:12 CEST | [#395](https://github.com/tradecloud/tradecloud-portal-angular/pull/395) |  add reopen request dialog | @bohdantrc |  |

34. [TC-4478](https://tradecloud.atlassian.net/browse/TC-4478) As a supplier I want to reopen order lines 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Jun-2020 13:49:22 CEST | [#1206](https://github.com/tradecloud/tradecloud-microservices/pull/1206) | [TC-5782] Reopen request by supplier | @roy-tc |  |

35. [TC-5803](https://tradecloud.atlassian.net/browse/TC-5803) Enforce 2FA by superuser and admin for new users  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 03-Jun-2020 14:39:41 CEST | [#1217](https://github.com/tradecloud/tradecloud-microservices/pull/1217) |  enforce 2fa new users | @RobinNagpal |  |
| 2 | Web Portal | 03-Jun-2020 14:08:45 CEST | [#401](https://github.com/tradecloud/tradecloud-portal-angular/pull/401) |  Enforce 2fa new users | @RobinNagpal |  |

36. [TC-5804](https://tradecloud.atlassian.net/browse/TC-5804) Enforce 2FA by superuser and admin for existing users  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 03-Jun-2020 13:59:41 CEST | [#1185](https://github.com/tradecloud/tradecloud-microservices/pull/1185) |  Enforce 2FA company level | @RobinNagpal |  |
| 2 | Services (Go) | 03-Jun-2020 13:59:13 CEST | [#297](https://github.com/tradecloud/tradecloud-microservices-go/pull/297) |  - add enforce2FA setting | @RobinNagpal |  |
| 3 | Web Portal | 03-Jun-2020 13:53:35 CEST | [#390](https://github.com/tradecloud/tradecloud-portal-angular/pull/390) |  Enforce 2FA company level | @RobinNagpal |  |

37. [TC-5702](https://tradecloud.atlassian.net/browse/TC-5702) As DevOps I want to update Go to 1.14 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 03-Jun-2020 07:57:54 CEST | [#307](https://github.com/tradecloud/tradecloud-microservices-go/pull/307) |  Update to Go 1.14, refactor messages handling | @vovinacci |  |

38. [TC-5993](https://tradecloud.atlassian.net/browse/TC-5993) As DevOps I want to log Kafka consumer name in Go services 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 02-Jun-2020 09:39:36 CEST | [#306](https://github.com/tradecloud/tradecloud-microservices-go/pull/306) |  Log Kafka consumer group name | @vovinacci |  |

39. [TC-5771](https://tradecloud.atlassian.net/browse/TC-5771) As DevOps I want deployment environmental variables to be consistent beween Go and Scala services. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 01-Jun-2020 19:11:39 CEST | [#305](https://github.com/tradecloud/tradecloud-microservices-go/pull/305) |  Make env variables naming consistent | @vovinacci |  |

