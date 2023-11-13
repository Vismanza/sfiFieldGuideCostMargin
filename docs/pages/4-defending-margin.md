# Defending Margin

This secion covers setting up margin upper and lower bounds. This results in runtime validation on a cart where margin needs to be in a defined range.

The range is defined in a matrix at a product level.

Separate to the margin bounds you can define limits on adjustments using vistual context scope on AdjustmentData. This allows you limit the % adjustment (or total discount) on any transaction.

These two feature in conjunction offer fine grained control in order to ensure order capture does not result in bad deals.

## Initial Setup

Follow the steps [here](https://help.salesforce.com/s/articleView?id=ind.comms_define_and_validate_margin_ranges.htm&type=5):
- Create  Dataraptor (Cost and Margin DR)
- Create Vlocity Calculation Matrix ()




Set up a virtual context scope for [AdjustmentData](https://help.salesforce.com/s/articleView?id=ind.comms_virtual_context_scopes.htm&type=5).

Navigate to CMT Administration > EPC Jobs and click Start on the Create Default Contextual Adjustment Data.

Navigate to Vlocity Product Console > Context Scope and click the '+' icon. Create a Context Scope as follows:

![Virtual Context Scope][Virtual Context Scope]

https://help.salesforce.com/s/articleView?id=ind.comms_qualification_rules_for_pricing_adjustments___assigning_or_deleting_to_the_adjustmentdata_virtual_object.htm&type=5

https://help.salesforce.com/s/articleView?id=ind.comms_qualification_rules_for_pricing_adjustments__contextual_adjustments_.htm&type=5

https://help.salesforce.com/s/articleView?id=ind.comms_creating_context_mappings.htm&type=5

[Virtual Context Scope]: ../images/4-virtual-context-scope.png