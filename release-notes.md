---
description: Tradecloud services and portal open pull requests and changelog (Tue Jul 14 13:31:04 CEST 2020)
---


## Open Pull Requests

1. [TC-6130](https://tradecloud.atlassian.net/browse/TC-6130) Hide reject order (line) buttons for suppliers  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 14-Jul-2020 13:21:49 CEST | [#440](https://github.com/tradecloud/tradecloud-portal-angular/pull/440) |  add feature toggle for reject button | @bohdantrc |  |

2. [TC-6108](https://tradecloud.atlassian.net/browse/TC-6108) As Eriks I want to test the integration by resending an order to my ERP system [Planned release 10-Jul-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jul-2020 13:21:05 CEST | [#1256](https://github.com/tradecloud/tradecloud-microservices/pull/1256) |  Resend order | @dmytrozheliuk |  |
| 2 | Services (Go) | 14-Jul-2020 13:14:24 CEST | [#318](https://github.com/tradecloud/tradecloud-microservices-go/pull/318) |  Add OutgoingOrderResentByBuyer and OutgoingOrderResentBySupplier events handlin | @vovinacci |  |
| 3 | Web Portal | 14-Jul-2020 09:02:35 CEST | [#435](https://github.com/tradecloud/tradecloud-portal-angular/pull/435) |  Add resend action and activity types | @bohdantrc |  |

3. [TC-6095](https://tradecloud.atlassian.net/browse/TC-6095) As buyer/supplier I want that documents are never removed from the buyer/supplier order/line 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jul-2020 13:14:23 CEST | [#1261](https://github.com/tradecloud/tradecloud-microservices/pull/1261) |  - preserve order and line documents | @olegtradecloud |  |

4. [TC-5936](https://tradecloud.atlassian.net/browse/TC-5936) Lower password link expiration timeout to 15 mins. [Planned release 17-Jul-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jul-2020 13:08:56 CEST | [#1269](https://github.com/tradecloud/tradecloud-microservices/pull/1269) |  Password reset expiration timeout | @olegtradecloud |  |

5. [TC-6099](https://tradecloud.atlassian.net/browse/TC-6099) Reissuing a line with less deliverySchedule positions will not trigger a reopen request.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jul-2020 11:34:41 CEST | [#1267](https://github.com/tradecloud/tradecloud-microservices/pull/1267) |  Fix delivery schedule rules for reopen request | @olegtradecloud |  |

6. [TC-5930](https://tradecloud.atlassian.net/browse/TC-5930) Broken accept connection permissions check [Planned release 24-Jul-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jul-2020 11:01:41 CEST | [#1265](https://github.com/tradecloud/tradecloud-microservices/pull/1265) |  - fix connection accept | @olegtradecloud |  |

7. [TC-5916](https://tradecloud.atlassian.net/browse/TC-5916) Use enumeratum for enums to avoid JSON deserialization issues 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 13-Jul-2020 17:11:25 CEST | [#1260](https://github.com/tradecloud/tradecloud-microservices/pull/1260) |  Use refactored enums in services | @roy-tc |  |
| 2 | Services (Scala) | 13-Jul-2020 17:06:36 CEST | [#1266](https://github.com/tradecloud/tradecloud-microservices/pull/1266) |  DO NOT MERGE - Test enum refactoring | @roy-tc |  |
| 3 | Services (Scala) | 09-Jul-2020 20:55:59 CEST | [#1259](https://github.com/tradecloud/tradecloud-microservices/pull/1259) |  Use refactored messages enums | @roy-tc |  |

8. [TC-5769](https://tradecloud.atlassian.net/browse/TC-5769) Do not persist and publish order events when the entity state does not change. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 13-Jul-2020 13:03:19 CEST | [#1234](https://github.com/tradecloud/tradecloud-microservices/pull/1234) |  Optional events | @olegtradecloud |  |

9. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 13-Jul-2020 11:29:57 CEST | [#437](https://github.com/tradecloud/tradecloud-portal-angular/pull/437) | A9 update | @bohdantrc |  |

10. [TC-5929](https://tradecloud.atlassian.net/browse/TC-5929) When a user authenticates with 2FA validate, a new refresh token is created 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 08-Jul-2020 14:35:20 CEST | [#1243](https://github.com/tradecloud/tradecloud-microservices/pull/1243) |  Do not set refresh token until fully authenticated | @TizianoPerrucci |  |
| 2 | Web Portal | 08-Jul-2020 00:25:41 CEST | [#428](https://github.com/tradecloud/tradecloud-portal-angular/pull/428) |  set auth token even if refresh token is not there | @RobinNagpal |  |

11. [TC-6102](https://tradecloud.atlassian.net/browse/TC-6102) IncomingOrderDocumentsAttachedByBuyer is retried forever when the purchase order number cannot be found [Planned release 30-Jun-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jul-2020 15:06:59 CEST | [#1246](https://github.com/tradecloud/tradecloud-microservices/pull/1246) |  Cleanup EventListener and log warnings in case of acknowledged errors | @roy-tc |  |

12. [TC-4927](https://tradecloud.atlassian.net/browse/TC-4927) Portal delivery schedule position is missing in proposal dialog 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jul-2020 11:29:34 CEST | [#430](https://github.com/tradecloud/tradecloud-portal-angular/pull/430) |  Add logic send position and edit position in dialog | @bohdantrc |  |

## Changelog

1. [TC-5555](https://tradecloud.atlassian.net/browse/TC-5555) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 14-Jul-2020 09:49:44 CEST | [#1268](https://github.com/tradecloud/tradecloud-microservices/pull/1268) |  Fix UAT status reporting | @vovinacci |  |
| 2 | Services (Go) | 14-Jul-2020 09:48:35 CEST | [#319](https://github.com/tradecloud/tradecloud-microservices-go/pull/319) |  Fix UAT status reporting | @vovinacci |  |
| 3 | Services (Scala) | 08-Jul-2020 11:40:23 CEST | [#1258](https://github.com/tradecloud/tradecloud-microservices/pull/1258) |  Fix scalastyle errors | @vovinacci |  |
| 4 | Services (Scala) | 02-Jul-2020 11:52:12 CEST | [#1251](https://github.com/tradecloud/tradecloud-microservices/pull/1251) |  - Fix tests run | @denys-kondartiuk |  |
| 5 | Web Portal | 17-Jun-2020 09:07:15 CEST | [#415](https://github.com/tradecloud/tradecloud-portal-angular/pull/415) |  Add env variable for show/hide reopen button | @bohdantrc |  |

2. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Jul-2020 22:10:04 CEST | [#434](https://github.com/tradecloud/tradecloud-portal-angular/pull/434) | [TС-6101] changed condition for showing action and differences reopen request | @bohdantrc |  |
| 2 | Web Portal | 24-Jun-2020 13:08:47 CEST | [#421](https://github.com/tradecloud/tradecloud-portal-angular/pull/421) | bugfix(2fa setup):[TC-6018]  fix spelling | @RobinNagpal |  |
| 3 | Web Portal | 16-Jun-2020 19:19:37 CEST | [#406](https://github.com/tradecloud/tradecloud-portal-angular/pull/406) | Bump websocket-extensions from 0.1.3 to 0.1.4 | @dependabot[bot] |  |

3. [TC-6103](https://tradecloud.atlassian.net/browse/TC-6103) contact filter shows only up to 10 users.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Jul-2020 15:06:58 CEST | [#439](https://github.com/tradecloud/tradecloud-portal-angular/pull/439) |  set limit 200 in contact user request | @bohdantrc |  |

4. [TC-5238](https://tradecloud.atlassian.net/browse/TC-5238) As Damen I want a separate system integration API account 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jul-2020 10:57:27 CEST | [#1264](https://github.com/tradecloud/tradecloud-microservices/pull/1264) |  Force auth and user services deployment on accp and prod, s… | @marcmatt |  |
| 2 | Services (Scala) | 10-Jul-2020 10:31:05 CEST | [#1263](https://github.com/tradecloud/tradecloud-microservices/pull/1263) |  Force auth and user services deployment on accp and prod | @marcmatt |  |
| 3 | Services (Scala) | 10-Jul-2020 10:14:48 CEST | [#1262](https://github.com/tradecloud/tradecloud-microservices/pull/1262) |  Make depressed scalastyle a bit happier | @marcmatt |  |

5. [TC-6116](https://tradecloud.atlassian.net/browse/TC-6116) BE: Add integration user role 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Jul-2020 09:47:48 CEST | [#1257](https://github.com/tradecloud/tradecloud-microservices/pull/1257) |  Integration user role | @olegtradecloud |  |

6. [TC-6124](https://tradecloud.atlassian.net/browse/TC-6124) In progress lines because of an reopen request can be selected for Bulk actions (confirm/reject/propose)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 10-Jul-2020 09:43:30 CEST | [#438](https://github.com/tradecloud/tradecloud-portal-angular/pull/438) |  add pipe for checking open status in reopen request | @bohdantrc |  |

7. [TC-6042](https://tradecloud.atlassian.net/browse/TC-6042) BE: process cancelled indicator in order service, persist, publish event, create activity, close order line tasks 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 07-Jul-2020 14:34:40 CEST | [#1255](https://github.com/tradecloud/tradecloud-microservices/pull/1255) |  Refactor to SendOrderByBuyer command | @marcmatt |  |
| 2 | Services (Scala) | 03-Jul-2020 13:25:25 CEST | [#1253](https://github.com/tradecloud/tradecloud-microservices/pull/1253) |  Bump shared | @marcmatt |  |
| 3 | Services (Scala) | 03-Jul-2020 12:48:43 CEST | [#1235](https://github.com/tradecloud/tradecloud-microservices/pull/1235) | : Added order lines cancelling functionality | @dmytrozheliuk |  |
| 4 | Services (Scala) | 03-Jul-2020 12:48:40 CEST | [#1244](https://github.com/tradecloud/tradecloud-microservices/pull/1244) |  Send cancel order as separate command | @roy-tc |  |
| 5 | Services (Scala) | 22-Jun-2020 11:18:30 CEST | [#1238](https://github.com/tradecloud/tradecloud-microservices/pull/1238) |  Improvements to Added order lines cancelling functionality | @roy-tc |  |

8. [TC-6050](https://tradecloud.atlassian.net/browse/TC-6050) Bulk confirm sales order dialog shown all selected order line positions.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jul-2020 14:04:14 CEST | [#433](https://github.com/tradecloud/tradecloud-portal-angular/pull/433) |  show amount positions in bulk confirm dialog | @bohdantrc |  |

9. [TC-6001](https://tradecloud.atlassian.net/browse/TC-6001) Review cancel request business logic and discus solutions for edge cases 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Jul-2020 13:56:46 CEST | [#432](https://github.com/tradecloud/tradecloud-portal-angular/pull/432) |  navigation links | @bohdantrc |  |

10. [TC-5916](https://tradecloud.atlassian.net/browse/TC-5916) Use enumeratum for enums to avoid JSON deserialization issues 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 06-Jul-2020 12:31:28 CEST | [#1241](https://github.com/tradecloud/tradecloud-microservices/pull/1241) |  Use Enumeratum lib for enums | @roy-tc |  |

11. [TC-6084](https://tradecloud.atlassian.net/browse/TC-6084) Create accptance, system and security tests for implemented stories 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 03-Jul-2020 13:26:12 CEST | [#317](https://github.com/tradecloud/tradecloud-microservices-go/pull/317) |  - Increase number of workers for tests run | @denys-kondartiuk |  |
| 2 | Services (Scala) | 03-Jul-2020 13:26:05 CEST | [#1252](https://github.com/tradecloud/tradecloud-microservices/pull/1252) |  - Increase number of workers for tests run | @denys-kondartiuk |  |

12. [TC-6043](https://tradecloud.atlassian.net/browse/TC-6043) FE: Display line level activities with ActivityType OrderLineCancelledByBuyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 03-Jul-2020 11:44:34 CEST | [#427](https://github.com/tradecloud/tradecloud-portal-angular/pull/427) |  Add type `line-cancelled-by-buyer` and `lines-cancelled-by-buyer` in activity a | @bohdantrc |  |

13. [TC-6087](https://tradecloud.atlassian.net/browse/TC-6087) FE: show &#34;cancelled&#34; status in UI  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 02-Jul-2020 11:40:37 CEST | [#431](https://github.com/tradecloud/tradecloud-portal-angular/pull/431) |  Add cancelled in order line and order progress | @bohdantrc |  |

14. [TC-6083](https://tradecloud.atlassian.net/browse/TC-6083) Split up CompanyOrderIssuedByBuyer event into multiple commands 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 01-Jul-2020 17:44:11 CEST | [#1247](https://github.com/tradecloud/tradecloud-microservices/pull/1247) |  - split commands | @olegtradecloud |  |

15. [TC-4558](https://tradecloud.atlassian.net/browse/TC-4558) As DevOps I want to move all deployment secrets to Ansible Vault 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 30-Jun-2020 14:51:20 CEST | [#316](https://github.com/tradecloud/tradecloud-microservices-go/pull/316) |  Use Mandrill API key as secret | @vovinacci |  |
| 2 | Services (Scala) | 30-Jun-2020 14:49:41 CEST | [#1248](https://github.com/tradecloud/tradecloud-microservices/pull/1248) |  Remove unencrypted Mandrill API key mentions | @vovinacci |  |

16. [TC-6062](https://tradecloud.atlassian.net/browse/TC-6062) QA: 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jun-2020 16:23:37 CEST | [#425](https://github.com/tradecloud/tradecloud-portal-angular/pull/425) |  rename text in link | @bohdantrc |  |

17. [TC-6054](https://tradecloud.atlassian.net/browse/TC-6054) Damen feedback related to Item details 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jun-2020 16:23:17 CEST | [#424](https://github.com/tradecloud/tradecloud-portal-angular/pull/424) |  change title in item details component and update countries | @bohdantrc |  |

18. [TC-6088](https://tradecloud.atlassian.net/browse/TC-6088) The confirm/reject/propose changes buttons are not visible anymore for supplier when &#34;proposal&#34; is in open or rejected status. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 29-Jun-2020 14:57:57 CEST | [#426](https://github.com/tradecloud/tradecloud-portal-angular/pull/426) |  show confirmed actions in case of open ReopenRequest actions | @bohdantrc |  |

19. [TC-6102](https://tradecloud.atlassian.net/browse/TC-6102) IncomingOrderDocumentsAttachedByBuyer is retried forever when the purchase order number cannot be found 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Jun-2020 21:26:33 CEST | [#1245](https://github.com/tradecloud/tradecloud-microservices/pull/1245) |  Commit when order/line is not found | @marcmatt |  |

20. [TC-6036](https://tradecloud.atlassian.net/browse/TC-6036) As a supplier I cannot enter a quantity decimal number in proposal and reopen request dialog 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:59:55 CEST | [#423](https://github.com/tradecloud/tradecloud-portal-angular/pull/423) |  Set decimal number for quantity and price unit quantity in requests | @bohdantrc |  |

21. [TC-6018](https://tradecloud.atlassian.net/browse/TC-6018) &#34;create your password&#34; screen is shown when a new user refresh the &#34;enable 2FA page&#34;  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:59:15 CEST | [#420](https://github.com/tradecloud/tradecloud-portal-angular/pull/420) |  create secret on 2fa screen when refreshed | @RobinNagpal |  |

22. [TC-6037](https://tradecloud.atlassian.net/browse/TC-6037) Reopen request by supplier is not visible in supplier tab in order line detail page 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 26-Jun-2020 13:57:22 CEST | [#419](https://github.com/tradecloud/tradecloud-portal-angular/pull/419) |  add in supplier tab info about open reopen request | @bohdantrc |  |

23. [TC-6074](https://tradecloud.atlassian.net/browse/TC-6074) Show exceptionReason value, in case of a reopen request, in workflow and activity 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Jun-2020 22:15:28 CEST | [#422](https://github.com/tradecloud/tradecloud-portal-angular/pull/422) |  show `reopen request reason` if it was created by buyer | @bohdantrc |  |

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

39. [TC-5883](https://tradecloud.atlassian.net/browse/TC-5883) As integrated user, I want to get order updates if a reopen request is accepted 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 16-Jun-2020 12:02:22 CEST | [#1233](https://github.com/tradecloud/tradecloud-microservices/pull/1233) | : Added listeners for outgoing events for approve/reject reopen requests actions | @dmytrozheliuk |  |
| 2 | Services (Go) | 16-Jun-2020 12:02:18 CEST | [#314](https://github.com/tradecloud/tradecloud-microservices-go/pull/314) | : Added webhooks for approve/reject reopen request by buyer/… | @dmytrozheliuk |  |

