---
description: Tradecloud services and portal open pull requests and changelog (Thu Nov 5 19:30:54 CET 2020)
---


## Open Pull Requests

1. [TC-5864](https://tradecloud.atlassian.net/browse/TC-5864) API&#39;s should not use sensitive information in the URL [Planned release 30-Oct-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 05-Nov-2020 19:14:25 CET | [#1352](https://github.com/tradecloud/tradecloud-microservices/pull/1352) |  Don&#39;t use sensitive data in GET URL parameters | @roy-tc |  |
| 2 | Web Portal | 04-Nov-2020 17:06:14 CET | [#508](https://github.com/tradecloud/tradecloud-portal-angular/pull/508) |  add auth token into ws request header protocol key | @bohdantrc |  |

2. [TC-6251](https://tradecloud.atlassian.net/browse/TC-6251) As a buyer, I want to complete lines in Tradecloud using a Completed indicator 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 05-Nov-2020 16:46:13 CET | [#1361](https://github.com/tradecloud/tradecloud-microservices/pull/1361) |  - complete order lines | @olegtradecloud |  |
| 2 | Web Portal | 05-Nov-2020 16:07:01 CET | [#517](https://github.com/tradecloud/tradecloud-portal-angular/pull/517) | [TC-6262][TC-6254] Add new status into progress bar and activity | @bohdantrc |  |

3. [TC-6465](https://tradecloud.atlassian.net/browse/TC-6465) Add id(token) for each tag with text in TASK module 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 05-Nov-2020 16:43:41 CET | [#519](https://github.com/tradecloud/tradecloud-portal-angular/pull/519) |  add i18n tokens for TASK module and common tokens for buttons | @bohdantrc |  |

4. [TC-6499](https://tradecloud.atlassian.net/browse/TC-6499) Add webhook for OrderLinesIssuedByBuyer event 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 05-Nov-2020 15:39:49 CET | [#351](https://github.com/tradecloud/tradecloud-microservices-go/pull/351) | : Added OutgoingOrderLinesIssuedEvent for buyer and supplier | @dmytrozheliuk |  |
| 2 | Services (Scala) | 05-Nov-2020 15:35:07 CET | [#1366](https://github.com/tradecloud/tradecloud-microservices/pull/1366) | : Added OutgoingOrderLinesIssuedByBuyer event | @dmytrozheliuk |  |

5. [TC-5934](https://tradecloud.atlassian.net/browse/TC-5934) Make username case insensitive [Planned release 31-Aug-2020]
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Nov-2020 18:08:25 CET | [#1349](https://github.com/tradecloud/tradecloud-microservices/pull/1349) |  Make routing of email address-based commands case-insensitive in IdentityActor  | @roy-tc |  |

6. [TC-6429](https://tradecloud.atlassian.net/browse/TC-6429) Refactor findUserByEmail route to a POST route in user-search 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Nov-2020 11:31:27 CET | [#515](https://github.com/tradecloud/tradecloud-portal-angular/pull/515) |  replace GET request with POST into user service | @bohdantrc |  |

7. [TC-6309](https://tradecloud.atlassian.net/browse/TC-6309) Add puppeteer project and super user test  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 21-Oct-2020 12:23:03 CEST | [#490](https://github.com/tradecloud/tradecloud-portal-angular/pull/490) |  Add e2e tests (puppeteer) | @RobinNagpal |  |

8. [TC-6359](https://tradecloud.atlassian.net/browse/TC-6359) As a company admin and superuser, I want to remove a user  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 11-Oct-2020 17:48:01 CEST | [#1336](https://github.com/tradecloud/tradecloud-microservices/pull/1336) |  Remove user | @marcmatt |  |

## Changelog

1. [TC-6251](https://tradecloud.atlassian.net/browse/TC-6251) As a buyer, I want to complete lines in Tradecloud using a Completed indicator 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 05-Nov-2020 16:18:55 CET | [#1367](https://github.com/tradecloud/tradecloud-microservices/pull/1367) |  - fix completeAt event dates | @olegtradecloud |  |

2. [TC-6434](https://tradecloud.atlassian.net/browse/TC-6434) Allow enabling SSO on a user level  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 05-Nov-2020 12:33:44 CET | [#518](https://github.com/tradecloud/tradecloud-portal-angular/pull/518) |  Remove Marcel Terlouw from SSO connections | @marcmatt |  |
| 2 | Web Portal | 02-Nov-2020 21:17:32 CET | [#501](https://github.com/tradecloud/tradecloud-portal-angular/pull/501) |   add option to enable sso by specific email | @RobinNagpal |  |

3. [TC-6222](https://tradecloud.atlassian.net/browse/TC-6222) Introduce &#34;OrderLinesIssuedByBuyer&#34; as an event 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Nov-2020 20:05:48 CET | [#1360](https://github.com/tradecloud/tradecloud-microservices/pull/1360) | : Introduced OrderLinesIssuedByBuyer event | @dmytrozheliuk |  |
| 2 | Services (Scala) | 04-Nov-2020 10:54:33 CET | [#1363](https://github.com/tradecloud/tradecloud-microservices/pull/1363) | : PoC to handle multiple order issuing | @dmytrozheliuk |  |

4. [TC-6480](https://tradecloud.atlassian.net/browse/TC-6480) BE: Implement closing confirmed task in workflow 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Nov-2020 18:29:18 CET | [#1364](https://github.com/tradecloud/tradecloud-microservices/pull/1364) |  - close tasks on complete order lines | @olegtradecloud |  |

5. [TC-6478](https://tradecloud.atlassian.net/browse/TC-6478) BE: Create activities for completed order/lines 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Nov-2020 18:28:46 CET | [#1365](https://github.com/tradecloud/tradecloud-microservices/pull/1365) |  - add activities for complete order lines | @olegtradecloud |  |

6. [TC-5555](https://tradecloud.atlassian.net/browse/TC-5555) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Nov-2020 16:23:27 CET | [#516](https://github.com/tradecloud/tradecloud-portal-angular/pull/516) |  Delete symbol | @bohdantrc |  |

7. [TC-6464](https://tradecloud.atlassian.net/browse/TC-6464) Add id(token) for each tag with text in USER module 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Nov-2020 13:06:42 CET | [#514](https://github.com/tradecloud/tradecloud-portal-angular/pull/514) |  add i18n tokens for USER module | @bohdantrc |  |

8. [TC-6489](https://tradecloud.atlassian.net/browse/TC-6489) Add &#34;OrderLinesIssuedByBuyer&#34; to the integration settings.   
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Nov-2020 13:05:31 CET | [#511](https://github.com/tradecloud/tradecloud-portal-angular/pull/511) |  add new item into integration settings | @bohdantrc |  |

9. [TC-5328](https://tradecloud.atlassian.net/browse/TC-5328) As user, I want to be sure that only secure webhook endpoints are used 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Nov-2020 12:36:07 CET | [#1358](https://github.com/tradecloud/tradecloud-microservices/pull/1358) |  - webhook url validation | @olegtradecloud |  |
| 2 | Services (Go) | 04-Nov-2020 12:35:34 CET | [#350](https://github.com/tradecloud/tradecloud-microservices-go/pull/350) |  Allow skip webhook SSL certificate validation | @vovinacci |  |

10. [TC-6454](https://tradecloud.atlassian.net/browse/TC-6454) As portal supplier, I want that the net price is calculated automatically based on the gross price and discount I put in.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 04-Nov-2020 12:02:32 CET | [#512](https://github.com/tradecloud/tradecloud-portal-angular/pull/512) |  add net price in dialog as computed field | @bohdantrc |  |

11. [TC-6477](https://tradecloud.atlassian.net/browse/TC-6477) BE: Implement complete order and lines flow in order service 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 04-Nov-2020 11:54:50 CET | [#1362](https://github.com/tradecloud/tradecloud-microservices/pull/1362) |  - complete order lines by indicators | @olegtradecloud |  |

12. [TC-6472](https://tradecloud.atlassian.net/browse/TC-6472) Add id(token) for each tag with text in DASHBOARD and CONVERSATION modules 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 03-Nov-2020 17:37:55 CET | [#513](https://github.com/tradecloud/tradecloud-portal-angular/pull/513) |  add i18n tokens for DASHBOARD and CONVERSATION module | @bohdantrc |  |

13. [TC-6468](https://tradecloud.atlassian.net/browse/TC-6468) Add id(token) for each tag with text in SHARED module 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 03-Nov-2020 15:39:47 CET | [#510](https://github.com/tradecloud/tradecloud-portal-angular/pull/510) |  add i18n tokens for SHARED module | @bohdantrc |  |

14. [TC-6429](https://tradecloud.atlassian.net/browse/TC-6429) Refactor findUserByEmail route to a POST route in user-search 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Go) | 03-Nov-2020 14:59:38 CET | [#345](https://github.com/tradecloud/tradecloud-microservices-go/pull/345) |  Add findUserByEmail route to user-search | @roy-tc |  |

15. [TC-6449](https://tradecloud.atlassian.net/browse/TC-6449) Logout SSO user in Auth0 also so that tokens can be removed 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 02-Nov-2020 21:29:26 CET | [#500](https://github.com/tradecloud/tradecloud-portal-angular/pull/500) |  logout user in auth0 | @RobinNagpal |  |

16. [TC-6462](https://tradecloud.atlassian.net/browse/TC-6462) Add id(token) for each tag with text in COMPANY module 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 02-Nov-2020 15:27:50 CET | [#509](https://github.com/tradecloud/tradecloud-portal-angular/pull/509) |  add i18n tokens for company and common tokens for button | @bohdantrc |  |

17. [TC-6461](https://tradecloud.atlassian.net/browse/TC-6461) Add id(token) for each tag with text in CATALOG module 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 30-Oct-2020 15:08:17 CET | [#507](https://github.com/tradecloud/tradecloud-portal-angular/pull/507) |  add tokens into template for catalog module | @bohdantrc |  |

18. [TC-6463](https://tradecloud.atlassian.net/browse/TC-6463) Add id(token) for each tag with text in ANALYTICS and ACTIVITY modules 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 28-Oct-2020 11:32:02 CET | [#505](https://github.com/tradecloud/tradecloud-portal-angular/pull/505) |  add tokens for analytics and activity modules | @bohdantrc |  |

19. [TC-6354](https://tradecloud.atlassian.net/browse/TC-6354) Item details are not updated when re-issueing order line 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 28-Oct-2020 09:32:05 CET | [#1348](https://github.com/tradecloud/tradecloud-microservices/pull/1348) |  Update order details | @roy-tc |  |

20. [TC-6415](https://tradecloud.atlassian.net/browse/TC-6415) As DevOps I want to push git tag on master builds only when it is required, so that it&#39;s more clean 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 27-Oct-2020 16:51:02 CET | [#1359](https://github.com/tradecloud/tradecloud-microservices/pull/1359) |  Push git tag on master builds only when it is required, so that it&#39;s more clean | @denys-kondartiuk |  |
| 2 | Services (Go) | 27-Oct-2020 16:24:02 CET | [#349](https://github.com/tradecloud/tradecloud-microservices-go/pull/349) |  - Add additional logging | @denys-kondartiuk |  |
| 3 | Services (Go) | 27-Oct-2020 14:51:54 CET | [#348](https://github.com/tradecloud/tradecloud-microservices-go/pull/348) |  - Investigating issue with pushing tag | @denys-kondartiuk |  |
| 4 | Services (Go) | 27-Oct-2020 14:39:00 CET | [#347](https://github.com/tradecloud/tradecloud-microservices-go/pull/347) |  - Investigating issue with pushing tag | @denys-kondartiuk |  |
| 5 | Services (Go) | 27-Oct-2020 14:24:37 CET | [#346](https://github.com/tradecloud/tradecloud-microservices-go/pull/346) |  - Push git tag on master builds only when it is required, so that it&#39;s more cle | @denys-kondartiuk |  |

21. [TC-5957](https://tradecloud.atlassian.net/browse/TC-5957) Create Mockup for RFQ / Proposal process 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 27-Oct-2020 12:38:38 CET | [#488](https://github.com/tradecloud/tradecloud-portal-angular/pull/488) |  add mock data for testing and change structure | @bohdantrc |  |

22. [TC-5935](https://tradecloud.atlassian.net/browse/TC-5935) Do not allow to use previous password as new password 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 27-Oct-2020 12:02:47 CET | [#1357](https://github.com/tradecloud/tradecloud-microservices/pull/1357) |  - previous passwords validation | @olegtradecloud |  |
| 2 | Web Portal | 27-Oct-2020 11:00:38 CET | [#504](https://github.com/tradecloud/tradecloud-portal-angular/pull/504) |  add correct showing errors | @bohdantrc |  |

23. [TC-6416](https://tradecloud.atlassian.net/browse/TC-6416) Add id(token) for each word in AUTH module 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 27-Oct-2020 10:44:27 CET | [#497](https://github.com/tradecloud/tradecloud-portal-angular/pull/497) |  i18n auth | @bohdantrc |  |

24. [TC-6437](https://tradecloud.atlassian.net/browse/TC-6437) Place Notes above Documents in the order &amp; order line buyer &amp; supplier tap 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 23-Oct-2020 11:32:08 CEST | [#503](https://github.com/tradecloud/tradecloud-portal-angular/pull/503) |  move Notes fields in the order and order line buyer &amp; suppl… | @bohdantrc |  |

25. [TC-6383](https://tradecloud.atlassian.net/browse/TC-6383) Create and configure environment variables for backend SSO domain to companyId mapping 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Oct-2020 17:41:45 CEST | [#1341](https://github.com/tradecloud/tradecloud-microservices/pull/1341) |   add domain to company id mapping for tradecloud1 and damen | @RobinNagpal |  |
| 2 | Web Portal | 07-Oct-2020 10:38:28 CEST | [#494](https://github.com/tradecloud/tradecloud-portal-angular/pull/494) |   add domain sso configuration | @RobinNagpal |  |

26. [TC-6440](https://tradecloud.atlassian.net/browse/TC-6440) As an integrated buyer/supplier I want to use \n  in order and lines notes and properties to apply a line feed in the portal 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 22-Oct-2020 14:27:28 CEST | [#502](https://github.com/tradecloud/tradecloud-portal-angular/pull/502) |  add style for saving formatted text | @bohdantrc |  |

27. [TC-6410](https://tradecloud.atlassian.net/browse/TC-6410) As buyer or supplier I want that the net price is calculated and saved, when I do not send the net price 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 22-Oct-2020 14:06:32 CEST | [#1355](https://github.com/tradecloud/tradecloud-microservices/pull/1355) |   - net price calculation | @olegtradecloud |  |

28. [TC-6268](https://tradecloud.atlassian.net/browse/TC-6268) As user I want proposed &amp; requested prices and deliverySchedule are highlighted clearly throughout the UI. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 21-Oct-2020 17:41:41 CEST | [#496](https://github.com/tradecloud/tradecloud-portal-angular/pull/496) |  add order line info highlight | @bohdantrc |  |

29. [TC-5932](https://tradecloud.atlassian.net/browse/TC-5932) Remove password reset username enumeration 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 21-Oct-2020 15:59:32 CEST | [#1350](https://github.com/tradecloud/tradecloud-microservices/pull/1350) |  Avoid username enumeration | @roy-tc |  |

30. [TC-6405](https://tradecloud.atlassian.net/browse/TC-6405) SSO users how are created as Non-SSO users have Tradecloud as identityProvider 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 21-Oct-2020 12:33:43 CEST | [#1354](https://github.com/tradecloud/tradecloud-microservices/pull/1354) |   fix identiy provider | @RobinNagpal |  |

31. [TC-5121](https://tradecloud.atlassian.net/browse/TC-5121) As buyer I want to send a delivered indicator to Tradecloud. 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 20-Oct-2020 17:57:18 CEST | [#1346](https://github.com/tradecloud/tradecloud-microservices/pull/1346) | [TC-6076][TC-6075][TC-6389]: Handling delivery status within corresponding event | @dmytrozheliuk |  |

32. [TC-6399](https://tradecloud.atlassian.net/browse/TC-6399) Add UI changes to show new activity OrderLinesMarkedAsDeliveredBySupplier/Buyer 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 20-Oct-2020 16:56:12 CEST | [#495](https://github.com/tradecloud/tradecloud-portal-angular/pull/495) | [TC-5121] Add new statuses(marked as delivered) into activity | @bohdantrc |  |

33. [TC-6432](https://tradecloud.atlassian.net/browse/TC-6432) Damen ACCP order line N612060 01-002 cannot be confirmed by the supplier.  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 19-Oct-2020 13:14:23 CEST | [#1353](https://github.com/tradecloud/tradecloud-microservices/pull/1353) |  Confirm order line with rejected proposal | @roy-tc |  |

34. [TC-6424](https://tradecloud.atlassian.net/browse/TC-6424) FE: Update password recovery link sent confirmation 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 19-Oct-2020 09:36:34 CEST | [#498](https://github.com/tradecloud/tradecloud-portal-angular/pull/498) | [TC-5932] change recovery text | @bohdantrc |  |

35. [TC-6406](https://tradecloud.atlassian.net/browse/TC-6406) As a buyer, only able to process gross price and discount in my ERP, I want to calculate and save the confirmed gross price 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 15-Oct-2020 16:38:05 CEST | [#1351](https://github.com/tradecloud/tradecloud-microservices/pull/1351) |  Supplier gross prices | @olegtradecloud |  |

36. [TC-6375](https://tradecloud.atlassian.net/browse/TC-6375) As a buyer, I want that prices of supplier proposals are compared based on Net price and the highest PUQ  
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 13-Oct-2020 14:03:57 CEST | [#1342](https://github.com/tradecloud/tradecloud-microservices/pull/1342) |  - add price comparison based on business rules | @olegtradecloud |  |

37. [TC-6390](https://tradecloud.atlassian.net/browse/TC-6390) As a buyer/supplier, I want that prices of reopen requests are compared based on Net price and the highest PUQ 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 08-Oct-2020 13:30:35 CEST | [#1347](https://github.com/tradecloud/tradecloud-microservices/pull/1347) |  reopen request prices comparison | @olegtradecloud |  |

38. [TC-6145](https://tradecloud.atlassian.net/browse/TC-6145)  As SSO Enabled company, after I login with on AD page, I should be kept logged in 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Web Portal | 07-Oct-2020 14:07:48 CEST | [#478](https://github.com/tradecloud/tradecloud-portal-angular/pull/478) |  exchange jwt token for access token(refresh scenario) | @RobinNagpal |  |
| 2 | Services (Scala) | 07-Oct-2020 14:07:16 CEST | [#1316](https://github.com/tradecloud/tradecloud-microservices/pull/1316) |  don&#39;t return refresh access token if identity provided is Auth0 | @RobinNagpal |  |

39. [TC-6000](https://tradecloud.atlassian.net/browse/TC-6000) Continuous delivery and operations 
| #    | Repository | Last Updated | PR#  | Title | Username | Comments |
| :--- | :---       | :---         | :--- | :---  | :---     | :--- |
| 1 | Services (Scala) | 06-Oct-2020 15:31:08 CEST | [#1345](https://github.com/tradecloud/tradecloud-microservices/pull/1345) |  Hotfix: Use exact buf version | @denys-kondartiuk |  |

