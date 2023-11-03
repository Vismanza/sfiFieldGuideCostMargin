# SFI Field Guide: Cost and Margin

Cost and Margin is a pricing feature of [Salesforce Industries CPQ](https://help.salesforce.com/s/articleView?id=ind.comms_industries_configure__price__quote__cpq_.htm&type=5). The functionality allows the creation of costs as well as prices against products. Margin calculations and rollups are included out of the box for:
 - One Time Charges
 - Monthly Recurring Charges
 - Usage Pricing

It is possible to configure cost and margin for custom pricing variables but that is beyond the scope of this field guide for now.

## What is Covered?

1. [How to set up Cost & Margin with basic mechanics explained](/docs/pages/1-setup-basics.md)
2. [Setting Costs using Matrices](/docs/pages/2-costs-matrices.md)
3. [Setting Prices based on Costs (target pricing / goal seek)](/docs/pages/3-prices-dynamic.md)
4. [Allowing Price Adjustments while defending Margin](/docs/pages/4-defending-margin.md)

## How to use this field guid

This field guide offers **opinionated** configuration for the cost and margin feature. This means that there may well be reasons to deviate from the patterns in this field guide. This field guide is not official documentation and is not supoprted in any way.

The goal of this field guide is to offer confiration examples and explanations for how to use the Cost and Margin feature.

### Issues / Pull Requests

Feel free to log issues and issue pull requests. This Field Guide is intended to be unofficial and community maintained.

### Opinions

**Attribute Based Pricing V2** is configured as a starting point (provides assumed functionality for pricing logic).

**Business Rules Engine** (Expression Sets and Decision Matrices) is being used (most of the config should be possibole using Calculation Procedures and Calculation Matrices but it is not tested).

**[LWC Cart](https://help.salesforce.com/s/articleView?id=ind.comms_t_industries_cpq_in_lwc_176340.htm&type=5)** is being used.

[Vlocity Product Desginer](https://help.salesforce.com/s/articleView?id=ind.comms_the_vlocity_product_designer.htm&type=5) and [Vlocity Designer](https://help.salesforce.com/s/articleView?id=ind.comms_vlocity_pricing_designer.htm&type=5) are being used wherever possible. If it is not used where possible reasons will be provided.

Wherever possible, **Salesforce Metadata** is used. If it is not used where possible reasons will be provided.

### Repo Structure

- Docs are all nested under /docs
- Salesforce Metadata in /force-app
- Vlocity Metadata in /vlocity

## Requirements

In order to deploy / test / play with any of the confiugration in this field guide you will need a Salesforce Org with Salesforce Energy and Utilties Cloud installed (note that this config **may** also apply to Communications Cloud or Media Cloud). As a starting point this Field Guide is based on the [Customer Acquisition Application for Energy & Utillities](https://help.salesforce.com/s/articleView?id=ind.energy_t_set_up_the_customer_acquisition_managementapplication_for_energyutilities_290247.htm&type=5).

It is assumed that LWC Cart is already deployed (this Field Guide does not cover [installing LWC Cart](https://help.salesforce.com/s/articleView?id=ind.comms_deploy_industries_cpq_in_lwc_with_omnistudio_enabled.htm&type=5)).

## Read All About It

- [Energy & Utilities Cloud](https://help.salesforce.com/s/articleView?language=en_US&id=ind.energy_energyutilities_cloud_258980.htm&type=5)
- [Industries Configure, Price, Quote (CPQ)](https://help.salesforce.com/s/articleView?id=ind.comms_industries_configure__price__quote__cpq_.htm&type=5)
- [Industries CPQ Attribute Based Pricing Library](https://github.com/Salesforce-Industries-Process-Library/Industries-CPQ)
- [Industries CPQ for Energy & Utilities Cloud](https://help.salesforce.com/s/articleView?id=ind.comms_industries_cpq_for_energy_utilities_cloud.htm&type=5)
- [Cost and Margin in EPC](https://help.salesforce.com/s/articleView?id=ind.comms_cost_and_margin_in_epc.htm&type=5)
