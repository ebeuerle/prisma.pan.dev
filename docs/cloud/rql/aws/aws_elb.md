---
id: aws_elb
title: AWS ELB RQL Queries
sidebar_label: AWS RQL Queries
description: AWS RQL Queries
---

# Sample RQL Queries

:::note
The following guide will walk you AWS ELB RQL Query Examples
:::

## List ELBv2 that have TLSv1 enabled

```bash
config where api.name = 'aws-elbv2-describe-load-balancers' as X; config where api.name = 'aws-describe-ssl-policies' as Y; filter '$.Y.sslProtocols[*] equals TLSv1 and $.X.listeners[*].sslPolicy equals $.Y.name'; show X;
```

## List ELBv1 that has TLSv1 enabled

```bash
config where cloud.type = 'aws' AND api.name = 'aws-elb-describe-load-balancers' AND json.rule = "policies[*].policyAttributeDescriptions[?(@.attributeName=='Protocol-TLSv1')].attributeValue equals true"
```
