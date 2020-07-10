---
description: Tradecloud services and portal open pull requests and changelog (Fri Jul 10 19:30:58 CEST 2020)
---


## Open Pull Requests

1. [TC-6006](https://tradecloud.atlassian.net/browse/TC-6006) Activity event is created on bulk actions even if action is not allowed 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jul-2020 19:09:07 CEST | [#1234](https://github.com/tradecloud/tradecloud-microservices/pull/1234) |  Create optional event on order bulk accept | @olegtradecloud |  |

2. [TC-5930](https://tradecloud.atlassian.net/browse/TC-5930) Broken accept connection permissions check [Planned release 24-Jul-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jul-2020 14:18:00 CEST | [#1265](https://github.com/tradecloud/tradecloud-microservices/pull/1265) |  - fix connection accept | @olegtradecloud |  |

3. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Jul-2020 11:01:03 CEST | [#434](https://github.com/tradecloud/tradecloud-portal-angular/pull/434) | [TС-6101] changed condition for showing action and differences reopen request | @bohdantrc |  |
| 2 | Web Portal | 09-Jul-2020 15:47:07 CEST | [#437](https://github.com/tradecloud/tradecloud-portal-angular/pull/437) | A9 update | @bohdantrc |  |

4. [TC-6095](https://tradecloud.atlassian.net/browse/TC-6095) As buyer/supplier I want that documents are never removed from the buyer/supplier order/line 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jul-2020 10:02:17 CEST | [#1261](https://github.com/tradecloud/tradecloud-microservices/pull/1261) |  - preserve order and line documents | @olegtradecloud |  |

5. [TC-5916](https://tradecloud.atlassian.net/browse/TC-5916) Use enumeratum for enums to avoid JSON deserialization issues 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 09-Jul-2020 20:55:59 CEST | [#1259](https://github.com/tradecloud/tradecloud-microservices/pull/1259) |  Use refactored messages enums | @roy-tc |  |
| 2 | Services (Scala) | 09-Jul-2020 10:55:43 CEST | [#1260](https://github.com/tradecloud/tradecloud-microservices/pull/1260) |  Use refactored enums in services | @roy-tc |  |

6. [TC-6108](https://tradecloud.atlassian.net/browse/TC-6108) As Eriks I want to test the integration by resending an order to my ERP system [Planned release 10-Jul-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 09-Jul-2020 13:26:08 CEST | [#1256](https://github.com/tradecloud/tradecloud-microservices/pull/1256) |  Resend order | @dmytrozheliuk |  |
| 2 | Web Portal | 09-Jul-2020 11:06:56 CEST | [#435](https://github.com/tradecloud/tradecloud-portal-angular/pull/435) |  Add resend action and activity types | @bohdantrc |  |
| 3 | Services (Go) | 08-Jul-2020 13:07:29 CEST | [#318](https://github.com/tradecloud/tradecloud-microservices-go/pull/318) |  Add OutgoingOrderResentByBuyer and OutgoingOrderResentBySupplier events handlin | @vovinacci |  |

7. [TC-5929](https://tradecloud.atlassian.net/browse/TC-5929) When a user authenticates with 2FA validate, a new refresh token is created 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 08-Jul-2020 14:35:20 CEST | [#1243](https://github.com/tradecloud/tradecloud-microservices/pull/1243) |  Do not set refresh token until fully authenticated | @TizianoPerrucci |  |
| 2 | Web Portal | 08-Jul-2020 00:25:41 CEST | [#428](https://github.com/tradecloud/tradecloud-portal-angular/pull/428) |  set auth token even if refresh token is not there | @RobinNagpal |  |

8. [TC-6102](https://tradecloud.atlassian.net/browse/TC-6102) IncomingOrderDocumentsAttachedByBuyer is retried forever when the purchase order number cannot be found [Planned release 30-Jun-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jul-2020 15:06:59 CEST | [#1246](https://github.com/tradecloud/tradecloud-microservices/pull/1246) |  Cleanup EventListener and log warnings in case of acknowledged errors | @roy-tc |  |

9. [TC-4927](https://tradecloud.atlassian.net/browse/TC-4927) Portal delivery schedule position is missing in proposal dialog 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jul-2020 11:29:34 CEST | [#430](https://github.com/tradecloud/tradecloud-portal-angular/pull/430) |  Add logic send position and edit position in dialog | @bohdantrc |  |

## Changelog

1. [TC-6103](https://tradecloud.atlassian.net/browse/TC-6103) contact filter shows only up to 10 users.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Jul-2020 15:06:58 CEST | [#439](https://github.com/tradecloud/tradecloud-portal-angular/pull/439) |  set limit 200 in contact user request | @bohdantrc |  |

2. [TC-5238](https://tradecloud.atlassian.net/browse/TC-5238) As Damen I want a separate system integration API account 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jul-2020 10:57:27 CEST | [#1264](https://github.com/tradecloud/tradecloud-microservices/pull/1264) |  Force auth and user services deployment on accp and prod, s… | @marcmatt |  |
| 2 | Services (Scala) | 10-Jul-2020 10:31:05 CEST | [#1263](https://github.com/tradecloud/tradecloud-microservices/pull/1263) |  Force auth and user services deployment on accp and prod | @marcmatt |  |
| 3 | Services (Scala) | 10-Jul-2020 10:14:48 CEST | [#1262](https://github.com/tradecloud/tradecloud-microservices/pull/1262) |  Make depressed scalastyle a bit happier | @marcmatt |  |

3. [TC-6116](https://tradecloud.atlassian.net/browse/TC-6116) BE: Add integration user role 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jul-2020 09:47:48 CEST | [#1257](https://github.com/tradecloud/tradecloud-microservices/pull/1257) |  Integration user role | @olegtradecloud |  |

4. [TC-6124](https://tradecloud.atlassian.net/browse/TC-6124) In progress lines because of an reopen request can be selected for Bulk actions (confirm/reject/propose)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Jul-2020 09:43:30 CEST | [#438](https://github.com/tradecloud/tradecloud-portal-angular/pull/438) |  add pipe for checking open status in reopen request | @bohdantrc |  |

5. [TC-5555](https://tradecloud.atlassian.net/browse/TC-5555) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 08-Jul-2020 11:40:23 CEST | [#1258](https://github.com/tradecloud/tradecloud-microservices/pull/1258) |  Fix scalastyle errors | @vovinacci |  |
| 2 | Services (Scala) | 02-Jul-2020 11:52:12 CEST | [#1251](https://github.com/tradecloud/tradecloud-microservices/pull/1251) |  - Fix tests run | @denys-kondartiuk |  |
| 3 | Web Portal | 17-Jun-2020 09:07:15 CEST | [#415](https://github.com/tradecloud/tradecloud-portal-angular/pull/415) |  Add env variable for show/hide reopen button | @bohdantrc |  |
| 4 | Web Portal | 11-Jun-2020 23:05:25 CEST | [#409](https://github.com/tradecloud/tradecloud-portal-angular/pull/409) |  fix model workflow | @bohdantrc |  |
| 5 | Web Portal | 11-Jun-2020 14:21:57 CEST | [#407](https://github.com/tradecloud/tradecloud-portal-angular/pull/407) |  fix RFQ imports for correct build | @bohdantrc |  |
| 6 | Services (Scala) | 11-Jun-2020 10:32:33 CEST | [#1231](https://github.com/tradecloud/tradecloud-microservices/pull/1231) |  Catch NotFound and properly log. Also enhance spec to avoid exceptions | @roy-tc |  |

6. [TC-6042](https://tradecloud.atlassian.net/browse/TC-6042) BE: process cancelled indicator in order service, persist, publish event, create activity, close order line tasks 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jul-2020 14:34:40 CEST | [#1255](https://github.com/tradecloud/tradecloud-microservices/pull/1255) |  Refactor to SendOrderByBuyer command | @marcmatt |  |
| 2 | Services (Scala) | 03-Jul-2020 13:25:25 CEST | [#1253](https://github.com/tradecloud/tradecloud-microservices/pull/1253) |  Bump shared | @marcmatt |  |
| 3 | Services (Scala) | 03-Jul-2020 12:48:43 CEST | [#1235](https://github.com/tradecloud/tradecloud-microservices/pull/1235) | : Added order lines cancelling functionality | @dmytrozheliuk |  |
| 4 | Services (Scala) | 03-Jul-2020 12:48:40 CEST | [#1244](https://github.com/tradecloud/tradecloud-microservices/pull/1244) |  Send cancel order as separate command | @roy-tc |  |
| 5 | Services (Scala) | 22-Jun-2020 11:18:30 CEST | [#1238](https://github.com/tradecloud/tradecloud-microservices/pull/1238) |  Improvements to Added order lines cancelling functionality | @roy-tc |  |

7. [TC-6050](https://tradecloud.atlassian.net/browse/TC-6050) Bulk confirm sales order dialog shown all selected order line positions.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jul-2020 14:04:14 CEST | [#433](https://github.com/tradecloud/tradecloud-portal-angular/pull/433) |  show amount positions in bulk confirm dialog | @bohdantrc |  |

8. [TC-6001](https://tradecloud.atlassian.net/browse/TC-6001) Review cancel request business logic and discus solutions for edge cases 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jul-2020 13:56:46 CEST | [#432](https://github.com/tradecloud/tradecloud-portal-angular/pull/432) |  navigation links | @bohdantrc |  |

9. [TC-5916](https://tradecloud.atlassian.net/browse/TC-5916) Use enumeratum for enums to avoid JSON deserialization issues 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 06-Jul-2020 12:31:28 CEST | [#1241](https://github.com/tradecloud/tradecloud-microservices/pull/1241) |  Use Enumeratum lib for enums | @roy-tc |  |

10. [TC-6084](https://tradecloud.atlassian.net/browse/TC-6084) Create accptance, system and security tests for implemented stories 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 03-Jul-2020 13:26:12 CEST | [#317](https://github.com/tradecloud/tradecloud-microservices-go/pull/317) |  - Increase number of workers for tests run | @denys-kondartiuk |  |
| 2 | Services (Scala) | 03-Jul-2020 13:26:05 CEST | [#1252](https://github.com/tradecloud/tradecloud-microservices/pull/1252) |  - Increase number of workers for tests run | @denys-kondartiuk |  |

11. [TC-6043](https://tradecloud.atlassian.net/browse/TC-6043) FE: Display line level activities with ActivityType OrderLineCancelledByBuyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 03-Jul-2020 11:44:34 CEST | [#427](https://github.com/tradecloud/tradecloud-portal-angular/pull/427) |  Add type `line-cancelled-by-buyer` and `lines-cancelled-by-buyer` in activity a | @bohdantrc |  |

12. [TC-6087](https://tradecloud.atlassian.net/browse/TC-6087) FE: show &#34;cancelled&#34; status in UI  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 02-Jul-2020 11:40:37 CEST | [#431](https://github.com/tradecloud/tradecloud-portal-angular/pull/431) |  Add cancelled in order line and order progress | @bohdantrc |  |

13. [TC-6083](https://tradecloud.atlassian.net/browse/TC-6083) Split up CompanyOrderIssuedByBuyer event into multiple commands 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 01-Jul-2020 17:44:11 CEST | [#1247](https://github.com/tradecloud/tradecloud-microservices/pull/1247) |  - split commands | @olegtradecloud |  |

14. [TC-4558](https://tradecloud.atlassian.net/browse/TC-4558) As DevOps I want to move all deployment secrets to Ansible Vault 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 30-Jun-2020 14:51:20 CEST | [#316](https://github.com/tradecloud/tradecloud-microservices-go/pull/316) |  Use Mandrill API key as secret | @vovinacci |  |
| 2 | Services (Scala) | 30-Jun-2020 14:49:41 CEST | [#1248](https://github.com/tradecloud/tradecloud-microservices/pull/1248) |  Remove unencrypted Mandrill API key mentions | @vovinacci |  |

15. [TC-6062](https://tradecloud.atlassian.net/browse/TC-6062) QA: 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jun-2020 16:23:37 CEST | [#425](https://github.com/tradecloud/tradecloud-portal-angular/pull/425) |  rename text in link | @bohdantrc |  |

16. [TC-6054](https://tradecloud.atlassian.net/browse/TC-6054) Damen feedback related to Item details 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jun-2020 16:23:17 CEST | [#424](https://github.com/tradecloud/tradecloud-portal-angular/pull/424) |  change title in item details component and update countries | @bohdantrc |  |

17. [TC-6088](https://tradecloud.atlassian.net/browse/TC-6088) The confirm/reject/propose changes buttons are not visible anymore for supplier when &#34;proposal&#34; is in open or rejected status. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jun-2020 14:57:57 CEST | [#426](https://github.com/tradecloud/tradecloud-portal-angular/pull/426) |  show confirmed actions in case of open ReopenRequest actions | @bohdantrc |  |

18. [TC-6102](https://tradecloud.atlassian.net/browse/TC-6102) IncomingOrderDocumentsAttachedByBuyer is retried forever when the purchase order number cannot be found 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jun-2020 21:26:33 CEST | [#1245](https://github.com/tradecloud/tradecloud-microservices/pull/1245) |  Commit when order/line is not found | @marcmatt |  |

19. [TC-6036](https://tradecloud.atlassian.net/browse/TC-6036) As a supplier I cannot enter a quantity decimal number in proposal and reopen request dialog 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:59:55 CEST | [#423](https://github.com/tradecloud/tradecloud-portal-angular/pull/423) |  Set decimal number for quantity and price unit quantity in requests | @bohdantrc |  |

20. [TC-6018](https://tradecloud.atlassian.net/browse/TC-6018) &#34;create your password&#34; screen is shown when a new user refresh the &#34;enable 2FA page&#34;  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:59:15 CEST | [#420](https://github.com/tradecloud/tradecloud-portal-angular/pull/420) |  create secret on 2fa screen when refreshed | @RobinNagpal |  |

21. [TC-6037](https://tradecloud.atlassian.net/browse/TC-6037) Reopen request by supplier is not visible in supplier tab in order line detail page 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:57:22 CEST | [#419](https://github.com/tradecloud/tradecloud-portal-angular/pull/419) |  add in supplier tab info about open reopen request | @bohdantrc |  |

22. [TC-6074](https://tradecloud.atlassian.net/browse/TC-6074) Show exceptionReason value, in case of a reopen request, in workflow and activity 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jun-2020 22:15:28 CEST | [#422](https://github.com/tradecloud/tradecloud-portal-angular/pull/422) |  show `reopen request reason` if it was created by buyer | @bohdantrc |  |

23. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-Jun-2020 13:08:47 CEST | [#421](https://github.com/tradecloud/tradecloud-portal-angular/pull/421) | bugfix(2fa setup):[TC-6018]  fix spelling | @RobinNagpal |  |
| 2 | Web Portal | 16-Jun-2020 19:19:37 CEST | [#406](https://github.com/tradecloud/tradecloud-portal-angular/pull/406) | Bump websocket-extensions from 0.1.3 to 0.1.4 | @dependabot[bot] |  |

24. [TC-6051](https://tradecloud.atlassian.net/browse/TC-6051) BE: Add confirmedLine in activity model 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 24-Jun-2020 13:00:25 CEST | [#1239](https://github.com/tradecloud/tradecloud-microservices/pull/1239) | : version bump | @dmytrozheliuk |  |

25. [TC-5794](https://tradecloud.atlassian.net/browse/TC-5794) FE: reopen request by buyer activities 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 24-Jun-2020 09:21:27 CEST | [#418](https://github.com/tradecloud/tradecloud-portal-angular/pull/418) |  add activity types for buyer reopen request activities | @bohdantrc |  |

26. [TC-5787](https://tradecloud.atlassian.net/browse/TC-5787) FE: reopen request by supplier activities 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 23-Jun-2020 15:44:38 CEST | [#417](https://github.com/tradecloud/tradecloud-portal-angular/pull/417) |  add activity for supplier reopen request activities | @bohdantrc |  |

27. [TC-5805](https://tradecloud.atlassian.net/browse/TC-5805) Unrestrict 2FA by superuser and admin 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-Jun-2020 14:51:23 CEST | [#402](https://github.com/tradecloud/tradecloud-portal-angular/pull/402) |  Unrestrict 2fa | @RobinNagpal |  |
| 2 | Services (Scala) | 19-Jun-2020 14:50:44 CEST | [#1219](https://github.com/tradecloud/tradecloud-microservices/pull/1219) |  Unrestrict 2FA | @RobinNagpal |  |

28. [TC-6002](https://tradecloud.atlassian.net/browse/TC-6002) FE: As a supplier I want approve or reject a reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-Jun-2020 13:31:15 CEST | [#416](https://github.com/tradecloud/tradecloud-portal-angular/pull/416) |  add approve/reject from supplier | @bohdantrc |  |

29. [TC-4467](https://tradecloud.atlassian.net/browse/TC-4467) As a DevOps I want to be able to re-build a search index 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Jun-2020 11:06:16 CEST | [#1229](https://github.com/tradecloud/tradecloud-microservices/pull/1229) |  Remove CompanyUserSynced | @roy-tc |  |

30. [TC-6035](https://tradecloud.atlassian.net/browse/TC-6035) Check for authenticated status during websocket connection 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Jun-2020 09:47:16 CEST | [#1236](https://github.com/tradecloud/tradecloud-microservices/pull/1236) |  update shared version(check authentication status) | @RobinNagpal |  |

31. [TC-5956](https://tradecloud.atlassian.net/browse/TC-5956) As Damen security officer I want the TOTP verification to use 2 time windows. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 18-Jun-2020 22:32:21 CEST | [#1237](https://github.com/tradecloud/tradecloud-microservices/pull/1237) |   update 2FA window size to 2 | @RobinNagpal |  |

32. [TC-5997](https://tradecloud.atlassian.net/browse/TC-5997) FE: As a buyer I want approve or reject a reopen request by supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 18:16:11 CEST | [#410](https://github.com/tradecloud/tradecloud-portal-angular/pull/410) |  Add approve reject for buyer in workflow task | @bohdantrc |  |

33. [TC-5874](https://tradecloud.atlassian.net/browse/TC-5874) BE: refactor line proposal to LineRequests 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 17-Jun-2020 16:38:42 CEST | [#315](https://github.com/tradecloud/tradecloud-microservices-go/pull/315) |  Fix webhook API specs semantic error | @marcmatt |  |

34. [TC-6024](https://tradecloud.atlassian.net/browse/TC-6024) When request is “reopenRequest” the confirm/propose changes/reject buttons should not be visible for the supplier 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 15:49:44 CEST | [#413](https://github.com/tradecloud/tradecloud-portal-angular/pull/413) |  Disable the ability to see buttons for a proposal entity like &#34;Confirm&#34;, &#34;Propo | @bohdantrc |  |

35. [TC-6025](https://tradecloud.atlassian.net/browse/TC-6025) supplierLine reopenRequest values are shown after a Buyer has rejected the reopen reqeust.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 17-Jun-2020 14:57:58 CEST | [#414](https://github.com/tradecloud/tradecloud-portal-angular/pull/414) |  Show order line details from SupplierLine reopenRequest when reopen with status | @bohdantrc |  |

36. [TC-6023](https://tradecloud.atlassian.net/browse/TC-6023) &#34;Reopen request&#34; button should have the same color as the &#34;propose changes&#34; button 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2020 17:15:27 CEST | [#412](https://github.com/tradecloud/tradecloud-portal-angular/pull/412) |  change color refresh button | @bohdantrc |  |

37. [TC-5958](https://tradecloud.atlassian.net/browse/TC-5958) Refactor OrderEvents.id to orderId 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 16-Jun-2020 16:00:45 CEST | [#312](https://github.com/tradecloud/tradecloud-microservices-go/pull/312) |  Rename OrderEvent.id to orderId | @roy-tc |  |
| 2 | Services (Scala) | 16-Jun-2020 16:00:35 CEST | [#1222](https://github.com/tradecloud/tradecloud-microservices/pull/1222) |  Rename OrderEvent.id to orderId | @roy-tc |  |

38. [TC-6022](https://tradecloud.atlassian.net/browse/TC-6022) VMI bug fix: Tasks and Order (line) detail pages are not updated automatically after an action.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 16-Jun-2020 14:13:05 CEST | [#411](https://github.com/tradecloud/tradecloud-portal-angular/pull/411) |   update and fix the booting sequence after login | @RobinNagpal |  |
| 2 | Web Portal | 11-Jun-2020 22:29:45 CEST | [#408](https://github.com/tradecloud/tradecloud-portal-angular/pull/408) |  call setIdentify with listening ws instead authSetIdentityW… | @bohdantrc |  |

39. [TC-5883](https://tradecloud.atlassian.net/browse/TC-5883) As integrated user, I want to get order updates if a reopen request is accepted 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Jun-2020 12:02:22 CEST | [#1233](https://github.com/tradecloud/tradecloud-microservices/pull/1233) | : Added listeners for outgoing events for approve/reject reopen requests actions | @dmytrozheliuk |  |
| 2 | Services (Go) | 16-Jun-2020 12:02:18 CEST | [#314](https://github.com/tradecloud/tradecloud-microservices-go/pull/314) | : Added webhooks for approve/reject reopen request by buyer/… | @dmytrozheliuk |  |

40. [TC-5867](https://tradecloud.atlassian.net/browse/TC-5867) Process reopen request in order service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 11-Jun-2020 17:55:14 CEST | [#308](https://github.com/tradecloud/tradecloud-microservices-go/pull/308) |  Buyer reopen request | @olegtradecloud |  |
| 2 | Services (Scala) | 11-Jun-2020 17:47:04 CEST | [#1213](https://github.com/tradecloud/tradecloud-microservices/pull/1213) |  Buyer reopen request | @olegtradecloud |  |

41. [TC-5869](https://tradecloud.atlassian.net/browse/TC-5869) BE: approve / reject reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 16:57:58 CEST | [#404](https://github.com/tradecloud/tradecloud-portal-angular/pull/404) |  buyer approve reject | @bohdantrc |  |

42. [TC-5996](https://tradecloud.atlassian.net/browse/TC-5996) FE: reopen request by buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 16:57:56 CEST | [#405](https://github.com/tradecloud/tradecloud-portal-angular/pull/405) |  add buyer reopen request show in ORDER LINE DETAILS column | @bohdantrc |  |

43. [TC-5957](https://tradecloud.atlassian.net/browse/TC-5957) Create Mockup for RFQ / Proposal process 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Jun-2020 12:43:38 CEST | [#403](https://github.com/tradecloud/tradecloud-portal-angular/pull/403) |  Provide RFQ mockups | @bohdantrc |  |

44. [TC-6007](https://tradecloud.atlassian.net/browse/TC-6007) Remove `order-integration` service completely 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Jun-2020 10:34:13 CEST | [#1230](https://github.com/tradecloud/tradecloud-microservices/pull/1230) |  Remove &#39;order-integration&#39; service | @vovinacci |  |

45. [TC-5701](https://tradecloud.atlassian.net/browse/TC-5701) As DevOps I want to upgrade &#39;gokit&#39; to latest version 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 10-Jun-2020 20:29:43 CEST | [#313](https://github.com/tradecloud/tradecloud-microservices-go/pull/313) |  Update go-kit to &#39;0.10.0&#39; | @vovinacci |  |

