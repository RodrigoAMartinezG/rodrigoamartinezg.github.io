---
layout: post
title: Best Azure resource part 1
subtitle: A couple of examples to show why Azure Logic Apps might be the best resource of Azure
cover-img: /assets/img/undraw_Online_calendar_re_wk3t.svg
thumbnail-img: /assets/img/10201-icon-service-Logic-Apps.svg
share-img: /assets/img/undraw_Online_calendar_re_wk3t.svg
gh-badge: [star, fork, follow]
gh-repo: RodrigoAMartinezG/rodrigoamartinezg.github.io
tags: [Azure, LogicApps]
comments: true
---

I'm not a developer, and although I'm doing courses and trainings, I'm really bad, mostly because of lack of creativity.

Thats why I had to find and use a tool that can provided me flexibility to integrate systems and implement logic at the same time.

And that's where I found Logic Apps, and oh boy, what a journey has been!

So, below you will find some examples that I implemented in real use cases.

## Support Requests Forms

I had to find a way that people can create support cases to an specific team, but that team didn't have the budget.

Using the existing cloud solutions, like Azure DevOps, Microsoft Forms and Logic Apps we where able to deploy a Support Request flow.

### Required Resources
-   MS forms
-   Logic Apps
-   Azure DevOps project

<div class="mermaid">
graph TD;
  A(User create case in MS Forms)-->B(Logic App initializer is triggered);
  B-->C(Logic App create a new Work Item in Azure DevOps);
  C-->D(User take the ownership of the Work Item and update the status);
  D-->E(Azure HTTP Service Hook is triggered and pointing to another Logic App)
  E-->F(Logic App nº2 update the user about the case)
</div>
<script async src="https://unpkg.com/mermaid@8.2.3/dist/mermaid.min.js"></script>

<br>

## Azure Subscription provissioning

Like in the previous case, all SaaS/PaaS solution already in the landscape.

So the background for this is that we had to find a way to provide a central place to provide Azure Subscriptions and deploy Blueprints.

### Required Resources
-   Azure enrolment account
-   [Service Principal with permission to create subscriptions](https://docs.microsoft.com/en-us/azure/cost-management-billing/manage/programmatically-create-subscription-enterprise-agreement?tabs=rest)
-   Logic App
-   KeyVault
-   Azure DevOps Project
-   MS Forms

<div class="mermaid">
graph TD;
  A(User request in MS Forms)-->B(Logic App initializer is triggered);
  B--> |Option A| C(Logic Apps trigger<br> a HTTPs request and create the subscription);
  B-->|Option B| D(Logic Apps trigger<br> a Azure DevOps pipelines to create the subscription);
  C-->G(Trigger others logic app to add tags, and so on);
  D-->E(ADO pipeline creates the subscriptions,<br> and deploy landing zone blueprint)
  E-->F(Logic App commnicate to the user the creation of the subcription <br>I usually use Teams connector+Adaptive Cards)
  G-->F

</div>
<script async src="https://unpkg.com/mermaid@8.2.3/dist/mermaid.min.js"></script>

<br>

In the part 2 I will add more examples like and Url-shortener services and also I will try to add the technicall details of the Logic Apps (ARM temlates)

Cheers!