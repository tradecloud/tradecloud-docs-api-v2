---
description: Tradecloud services and portal open pull requests and changelog (Fri Sep 4 09:31:18 CEST 2020)
---


## Open Pull Requests

1. [TC-6217](https://tradecloud.atlassian.net/browse/TC-6217) Buyer/supplier company &amp; contact links in the Buyer/supplier tap on the order detail page work, while the shouldn&#39;t.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Sep-2020 09:30:53 CEST | [#475](https://github.com/tradecloud/tradecloud-portal-angular/pull/475) |  rewrite links to company and user into simple text | @bohdantrc |  |

2. [TC-6044](https://tradecloud.atlassian.net/browse/TC-6044) company settings cannot be changed anymore after you change &#34;integration&#34; to webhook.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Sep-2020 08:50:25 CEST | [#1311](https://github.com/tradecloud/tradecloud-microservices/pull/1311) | : Fixed credentials issue when saving webhook integration settings at company pr | @dmytrozheliuk |  |

3. [TC-6153](https://tradecloud.atlassian.net/browse/TC-6153) Company search box on the Tasks page does not work. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 03-Sep-2020 15:05:25 CEST | [#1307](https://github.com/tradecloud/tradecloud-microservices/pull/1307) | : Search workflow tasks by multiple suppliers/buyers | @dmytrozheliuk |  |

4. [TC-6314](https://tradecloud.atlassian.net/browse/TC-6314) Use next MessageMeta everywhere 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 03-Sep-2020 12:57:25 CEST | [#1313](https://github.com/tradecloud/tradecloud-microservices/pull/1313) |  Use next MessageMeta where needed | @roy-tc |  |

5. [TC-5282](https://tradecloud.atlassian.net/browse/TC-5282) As a customer I would like to select the order events sent to my ERP system [Planned release 28-Aug-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 02-Sep-2020 17:11:39 CEST | [#327](https://github.com/tradecloud/tradecloud-microservices-go/pull/327) | [TC-6292]: Filtering events based on enabled event names | @dmytrozheliuk |  |
| 2 | Services (Scala) | 02-Sep-2020 09:15:18 CEST | [#1298](https://github.com/tradecloud/tradecloud-microservices/pull/1298) | [TC-6293]: Added `enabledEventNames` field to `CompanyIntegrationSettings` | @dmytrozheliuk |  |

6. [TC-6294](https://tradecloud.atlassian.net/browse/TC-6294) Implement UI View for configuring enabled event names 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 02-Sep-2020 16:50:22 CEST | [#479](https://github.com/tradecloud/tradecloud-portal-angular/pull/479) |  add checkboxes with events into settings form | @bohdantrc |  |

7. [TC-4220](https://tradecloud.atlassian.net/browse/TC-4220) As a supplier I want to accept, reject and propose order lines changes using my integration [Planned release 28-Aug-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 02-Sep-2020 16:24:29 CEST | [#1301](https://github.com/tradecloud/tradecloud-microservices/pull/1301) |  supplier order response | @olegtradecloud |  |

8. [TC-6145](https://tradecloud.atlassian.net/browse/TC-6145)  As SSO Enabled company, after I login with on AD page, I should be kept logged in 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 02-Sep-2020 13:12:26 CEST | [#478](https://github.com/tradecloud/tradecloud-portal-angular/pull/478) |  exchange jwt token for access token(refresh scenario) | @RobinNagpal |  |

9. [TC-5639](https://tradecloud.atlassian.net/browse/TC-5639) buyer/supplier filter box in the Orders/Task page remembers filters but does not show them when coming back on the orders page    
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 31-Aug-2020 15:38:24 CEST | [#476](https://github.com/tradecloud/tradecloud-portal-angular/pull/476) |  add possibility see initial filters in the connection box | @bohdantrc |  |

10. [TC-6297](https://tradecloud.atlassian.net/browse/TC-6297) Implement and refactor multiple mixpanel events 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 27-Aug-2020 17:01:44 CEST | [#477](https://github.com/tradecloud/tradecloud-portal-angular/pull/477) |  sent mixpanel event after attach document in order or order… | @bohdantrc |  |

11. [TC-6278](https://tradecloud.atlassian.net/browse/TC-6278) Add UI support of new order lines updated. by supplier activity 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 18-Aug-2020 16:13:30 CEST | [#467](https://github.com/tradecloud/tradecloud-portal-angular/pull/467) |  add updated statuses in activity for supplier | @bohdantrc |  |

12. [TC-6162](https://tradecloud.atlassian.net/browse/TC-6162) SPIKE: JIT Data Migration for Protobuf with proper code examples 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 12-Aug-2020 12:59:13 CEST | [#1288](https://github.com/tradecloud/tradecloud-microservices/pull/1288) | [TC-6165] DO NOT MERGE - PoC Data model refactoring with JIT Data Migration and  | @roy-tc |  |

## Changelog

1. [TC-6296](https://tradecloud.atlassian.net/browse/TC-6296) As a SSO users, I should not see the security setting under profile and should not be able to reset password 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 03-Sep-2020 08:59:45 CEST | [#480](https://github.com/tradecloud/tradecloud-portal-angular/pull/480) |  update env variables | @RobinNagpal |  |
| 2 | Web Portal | 02-Sep-2020 09:28:32 CEST | [#472](https://github.com/tradecloud/tradecloud-portal-angular/pull/472) |  add identity provider | @RobinNagpal |  |
| 3 | Services (Scala) | 02-Sep-2020 09:27:44 CEST | [#1299](https://github.com/tradecloud/tradecloud-microservices/pull/1299) |  add identity provider | @RobinNagpal |  |

2. [TC-6271](https://tradecloud.atlassian.net/browse/TC-6271) Split SendOrderResponseBySupplier command 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 02-Sep-2020 16:16:00 CEST | [#1312](https://github.com/tradecloud/tradecloud-microservices/pull/1312) |  split supplier order command | @olegtradecloud |  |

3. [TC-6144](https://tradecloud.atlassian.net/browse/TC-6144) As SSO Enabled company, after I login with on AD page, I should be logged in to tradecloud portal 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 31-Aug-2020 21:26:11 CEST | [#1310](https://github.com/tradecloud/tradecloud-microservices/pull/1310) |  Fix tcinfra.sh auth0 parameters | @marcmatt |  |
| 2 | Services (Scala) | 31-Aug-2020 19:48:27 CEST | [#1309](https://github.com/tradecloud/tradecloud-microservices/pull/1309) |  trigger build | @RobinNagpal |  |
| 3 | Services (Scala) | 31-Aug-2020 18:19:38 CEST | [#1308](https://github.com/tradecloud/tradecloud-microservices/pull/1308) |  - fix the typo in environment variable | @RobinNagpal |  |
| 4 | Services (Scala) | 31-Aug-2020 16:53:54 CEST | [#1297](https://github.com/tradecloud/tradecloud-microservices/pull/1297) |  create identity and user based on auth0 user | @RobinNagpal |  |
| 5 | Web Portal | 31-Aug-2020 16:35:54 CEST | [#468](https://github.com/tradecloud/tradecloud-portal-angular/pull/468) |  create auth0 identity and user | @RobinNagpal |  |

4. [TC-6303](https://tradecloud.atlassian.net/browse/TC-6303) Order header is not updated when the buyer sends an order without lines 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 26-Aug-2020 19:14:15 CEST | [#1306](https://github.com/tradecloud/tradecloud-microservices/pull/1306) | : Be able to update order data when lines is empty | @dmytrozheliuk |  |

5. [TC-6304](https://tradecloud.atlassian.net/browse/TC-6304) Cannot add new line to confirmed order when the buyer sents an updated order 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 26-Aug-2020 16:20:23 CEST | [#1304](https://github.com/tradecloud/tradecloud-microservices/pull/1304) | : Reissueing `Confirmed` order. Moving status to `InProgress` | @dmytrozheliuk |  |

6. [TC-6163](https://tradecloud.atlassian.net/browse/TC-6163) Add buf breaking change checker to CI pipelines 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 26-Aug-2020 15:15:42 CEST | [#1305](https://github.com/tradecloud/tradecloud-microservices/pull/1305) |  Minor typo fixes, bump messages | @vovinacci |  |
| 2 | Services (Scala) | 26-Aug-2020 10:03:20 CEST | [#1303](https://github.com/tradecloud/tradecloud-microservices/pull/1303) |  Add Protobuf breaking changes detection | @vovinacci |  |
| 3 | Services (Scala) | 26-Aug-2020 09:25:13 CEST | [#1302](https://github.com/tradecloud/tradecloud-microservices/pull/1302) |  Add buf configuration | @vovinacci |  |

7. [TC-6266](https://tradecloud.atlassian.net/browse/TC-6266) Add multiple event to Mixpanel  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 25-Aug-2020 09:55:03 CEST | [#469](https://github.com/tradecloud/tradecloud-portal-angular/pull/469) |  rewrite calling mixpanel events | @bohdantrc |  |

8. [TC-5555](https://tradecloud.atlassian.net/browse/TC-5555) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 21-Aug-2020 12:47:01 CEST | [#473](https://github.com/tradecloud/tradecloud-portal-angular/pull/473) |  Trigger build | @bohdantrc |  |
| 2 | Services (Go) | 18-Aug-2020 11:00:06 CEST | [#326](https://github.com/tradecloud/tradecloud-microservices-go/pull/326) |  Update Go to 1.15, update deps | @vovinacci |  |

9. [TC-6265](https://tradecloud.atlassian.net/browse/TC-6265) FE: Storage for updated Tasks 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 21-Aug-2020 11:41:35 CEST | [#470](https://github.com/tradecloud/tradecloud-portal-angular/pull/470) |  Add closedIds and filter tasks | @bohdantrc |  |

10. [TC-6267](https://tradecloud.atlassian.net/browse/TC-6267) Order performance metrics broken when you leave the Dashboard page and return to it 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 21-Aug-2020 11:41:07 CEST | [#471](https://github.com/tradecloud/tradecloud-portal-angular/pull/471) |  give one value from stream to avoiding que streams | @bohdantrc |  |

11. [TC-5640](https://tradecloud.atlassian.net/browse/TC-5640) As product management I want to show product info on the dashboard page 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 21-Aug-2020 11:40:32 CEST | [#400](https://github.com/tradecloud/tradecloud-portal-angular/pull/400) |  Change aside part in dashboard | @bohdantrc |  |

12. [TC-6142](https://tradecloud.atlassian.net/browse/TC-6142) As SSO Enabled company, after I login with specific email domain, I should see AD login page 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-Aug-2020 15:59:03 CEST | [#454](https://github.com/tradecloud/tradecloud-portal-angular/pull/454) |  redirect to Azure AD for sso email domain | @RobinNagpal |  |

13. [TC-6290](https://tradecloud.atlassian.net/browse/TC-6290) Create new supplier commands 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Aug-2020 11:03:30 CEST | [#1296](https://github.com/tradecloud/tradecloud-microservices/pull/1296) |  supplier order commands | @olegtradecloud |  |

14. [TC-5351](https://tradecloud.atlassian.net/browse/TC-5351) Tasks page does not add a new task at the bottom of the que after a task is completed.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-Aug-2020 09:57:26 CEST | [#465](https://github.com/tradecloud/tradecloud-portal-angular/pull/465) |  Add extra limit in task query request | @bohdantrc |  |

15. [TC-6180](https://tradecloud.atlassian.net/browse/TC-6180) Refactor OrderLinesReissuedByBuyer to OrderLinesUpdatedByBuyer when the line is not Issued 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 18-Aug-2020 12:48:18 CEST | [#466](https://github.com/tradecloud/tradecloud-portal-angular/pull/466) |  add order and order line status for activity | @bohdantrc |  |
| 2 | Services (Scala) | 18-Aug-2020 12:47:22 CEST | [#1295](https://github.com/tradecloud/tradecloud-microservices/pull/1295) |  Order updated by buyer | @olegtradecloud |  |

16. [N/A](#)  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 13-Aug-2020 13:30:04 CEST | [#1293](https://github.com/tradecloud/tradecloud-microservices/pull/1293) | [TС-6226] Order updating | @olegtradecloud |  |

17. [TC-6224](https://tradecloud.atlassian.net/browse/TC-6224) Create activity for OrderLinesUpdatedByBuyer event 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 13-Aug-2020 12:37:57 CEST | [#1294](https://github.com/tradecloud/tradecloud-microservices/pull/1294) |  Order update activity | @olegtradecloud |  |

18. [TC-6030](https://tradecloud.atlassian.net/browse/TC-6030) Attach Document dialog does not provide feedback if a file is uploaded that is too large 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 12-Aug-2020 09:32:10 CEST | [#463](https://github.com/tradecloud/tradecloud-portal-angular/pull/463) |  Add notification with error about upload file | @bohdantrc |  |

19. [TC-6221](https://tradecloud.atlassian.net/browse/TC-6221) Add missed logistics status business rules to order service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Aug-2020 17:33:30 CEST | [#1291](https://github.com/tradecloud/tradecloud-microservices/pull/1291) |   Logistic status missing rules | @olegtradecloud |  |

20. [TC-6090](https://tradecloud.atlassian.net/browse/TC-6090) When doing a proposal/request with more as 2 digits, prices are automatically rounded on 2 digits in the UI   
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 11-Aug-2020 15:19:55 CEST | [#464](https://github.com/tradecloud/tradecloud-portal-angular/pull/464) |  Add format for money and discount | @bohdantrc |  |

21. [TC-6226](https://tradecloud.atlassian.net/browse/TC-6226) Refactor order-service to use new OrderLinesUpdatedByBuyer event 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 10-Aug-2020 11:39:23 CEST | [#1292](https://github.com/tradecloud/tradecloud-microservices/pull/1292) |  Refactor order service | @olegtradecloud |  |

22. [TC-6029](https://tradecloud.atlassian.net/browse/TC-6029) Attach Document dialog seems to hang when uploading large files (smaller than 100MB) 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 06-Aug-2020 16:34:44 CEST | [#462](https://github.com/tradecloud/tradecloud-portal-angular/pull/462) |  set correct import | @bohdantrc |  |
| 2 | Web Portal | 06-Aug-2020 15:55:53 CEST | [#458](https://github.com/tradecloud/tradecloud-portal-angular/pull/458) |  add progress bar when uploading file and disable close events | @bohdantrc |  |

23. [TC-6176](https://tradecloud.atlassian.net/browse/TC-6176) Add logistics status business rules to order service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 06-Aug-2020 14:21:38 CEST | [#1287](https://github.com/tradecloud/tradecloud-microservices/pull/1287) |  Logistics status | @olegtradecloud |  |

24. [TC-6162](https://tradecloud.atlassian.net/browse/TC-6162) SPIKE: JIT Data Migration for Protobuf with proper code examples 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 05-Aug-2020 14:28:48 CEST | [#1290](https://github.com/tradecloud/tradecloud-microservices/pull/1290) |  Update scalapb and remove flatPackage flag | @roy-tc |  |

25. [TC-6046](https://tradecloud.atlassian.net/browse/TC-6046) As DevOps I want to address portal linter warnings 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 05-Aug-2020 13:12:58 CEST | [#461](https://github.com/tradecloud/tradecloud-portal-angular/pull/461) |  Fix all warnings replaced switchMap operator | @bohdantrc |  |

26. [TC-6049](https://tradecloud.atlassian.net/browse/TC-6049) Blank page after entering expired 2FA code in verify dailog 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 05-Aug-2020 11:52:11 CEST | [#457](https://github.com/tradecloud/tradecloud-portal-angular/pull/457) |   add back button and fix bug | @RobinNagpal |  |

27. [TC-6047](https://tradecloud.atlassian.net/browse/TC-6047) As DevOps I want to update portal dependencies (node/typescript) 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Aug-2020 15:35:28 CEST | [#460](https://github.com/tradecloud/tradecloud-portal-angular/pull/460) |  set new version node.js in .nvmrc file | @bohdantrc |  |
| 2 | Web Portal | 04-Aug-2020 13:26:11 CEST | [#451](https://github.com/tradecloud/tradecloud-portal-angular/pull/451) |  update portal angular and dependencies  | @bohdantrc |  |

28. [TC-5662](https://tradecloud.atlassian.net/browse/TC-5662) As Gazelle I only want to receive an order line confirmation when the line is agreed and has no goods received 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Aug-2020 10:54:51 CEST | [#456](https://github.com/tradecloud/tradecloud-portal-angular/pull/456) |  update orderLines from storage if websocket updated order | @bohdantrc |  |

