---
description: 'Tradecloud API environments available'
---

# Environments

Tradecloud has two physical separated infrastructure:

- test infrastructure
- production infrastructure

Tradecloud has three environments:

- [Environments](#environments)
  - [Test environments](#test-environments)
  - [Acceptance test environment](#acceptance-test-environment)
  - [Production environment](#production-environment)
  - [Planned maintenance](#planned-maintenance)

## Test environments

There are multiple test environments which are deployed to develop and test a feature, have a short dynamic life cycle and have NO availability SLA. The test environments are deployed on the test infrastructure which has a lower availability.

Available [test environments API page](https://api.test.tradecloud1.com)

Each test environment starts with a header, such as `master` (which is the latest version) and some `tc-1234-description` which are new features starting with the Tradecloud JIRA ticket number.

## Acceptance test environment

There is one [acceptance test environment](https://api.accp.tradecloud1.com) which is targetted on Tradecloud customers. Buyers and suppliers can test new features and develop and test their Tradecloud API integration. It has an availability SLA of 95% per month, measured 8:00-18:00 CE(S)T on working days (10/5), except for [planned maintenance](#planned-maintenance)

## Production environment

There is one [production environment](https://api.tradecloud1.com/) a.k.a. LIVE environment. It has an availability SLA of 99,5% per month, measured 24/7, except for [planned maintenance](#planned-maintenance)

## Planned maintenance

Maintenance can be planned on working days after 20:00 CE(S)T or in weekends and will be announced at least 3 working days ahead on the [Tradecloud status page](http://status.tradecloud1.com)
