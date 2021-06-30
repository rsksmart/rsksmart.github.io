---
layout: rsk
title: RIF Scheduler - SDK - Querying Plans
---

### Querying a plan

To schedule a transaction you need to purchase a plan. Plans are paid in tokens or RBTC.

First of all, you need to get a plan from the service provider, which will give you the price per execution, the payment token,the execution window in seconds, the maximum gas that an execution can spend and its status.

```javascript
import { RIFScheduler } from "@rsksmart/rif-scheduler-sdk";

const RIFScheduler = new RIFScheduler(serviceProviderContractAddress, provider);

const planIndex = 0;
const plan = await RIFScheduler.getPlan(planIndex);

//  {
//    pricePerExecution: 10000000000000;
//    window: 300;
//    gasLimit: 200000;
//    token: 0x...;
//    active: true;
//  }
```

### Querying ALL plans

If you want to obtain all plans from the service provider, you must first get the plans count and then get the plans one by one.

```javascript
import { RIFScheduler } from "@rsksmart/rif-scheduler-sdk";

const rifScheduler = new RIFScheduler(serviceProviderContractAddress, provider);

const plansCount = await rifScheduler.getPlansCount();

let allPlans = []

for (let i = 0; i < plansCount; i++) {
    const plan = await rifScheduler.getPlan(i);
    allPlans.push(plan)
}

//  [{
//    pricePerExecution: 10000000000000;
//    window: 300;
//    gasLimit: 200000;
//    token: 0x...;
//    active: true;
//  },
//  {
//    pricePerExecution: 50000000000000;
//    window: 600;
//    gasLimit: 400000;
//    token: 0x...;
//    active: true;
//  }]
```

What you can do with this sdk?

- [Getting Started](../)
- [Query plans](../query-plans)
- [Purchase one of this plans](../purchasing-plan)
- [Schedule a transaction for the next minutes](../scheduling)
- [Get status](../states)