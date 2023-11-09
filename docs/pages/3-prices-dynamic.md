# Dynamic Pricing

This secion covers using costs from a matrix and a target margin attribute value to create dynamic prices.

There is also some additional logic to make costs dynamic underneath the goal seek pricing behaviour.

## Initial Setup

Building on from the section on Prices and Costs this section will use a new attribute, product, matrix, expression set and pricing plan step.

> Scenario: A product has a cost that varies based on whether it is shipped directly or via a third party. If it is shipped directly warehousing costs are added to the product, if it shipped via a thirdy party a marketing fee is to the cost. The price of this product is set based on a target margin %. This means the price will be dynamic based on the calculated cost and target margin.


### Create Attribute

Create a new attribute category called: Cost Management.

![Attribute Category][Attribute Category]

Now create a picklist and attribute called Distribution Method with values for Direct and Indirect.

![Picklist][Picklist]

![Attribute Creation][Attribute Creation]

![Attribute Created][Attribute Created]

Now create an attribute called Target Margin.

![Margin Attribute][Margin Attribute]


### Create Object Type and Associate Attribute

Clone the Field Guide - Attribute Object Type and create a new child called Field Guide - Attributes.

![Object Type][Object Type]

Now add the new Attribute to the layout.

![Object Type Attribute][Object Type Attribute]

Note that the Margin attribute is defined to be Run-time confiogurable and required. This means we will have an error in the cart until a value is defined. This is important as we have priced the product at 0!

### Create Target Price Product

![Target Price Product][Target Price Product]

![Target Price Product Record][Target Price Product Record]

Now add an arbitrary 0 price to One Time Cost. This is to ensure that the product is available through CPQ but will not be used in this scenario. The price and cost data will all come from the matrix.

![Zero Price][Zero Price]

### Create Matrix

Create a new Lookup Table (Decision Matrix) called 'Field Guide - Target Margin Matrix'.

![Create Matrix][Create Matrix]

Upload the 'Target Price Matrix.csv' csv file on the matrix version and map the columns.

![Column Mapping][Column Mapping]

![Matrix Version][Matrix Version]

Activate the Matrix Version.

### Create Expression Set

Create an Expression Set called 'Field Guide Target Margin'. Click on the version record to open the Express Set Designer.

Define the  rank for the ES Version.

![Rank][Rank]

Add a Lookup Table element and map it to the 'Field Guide - Target Margin Matrix' Matrix.

![Lookup Table][Lookup Table]

Add a resource per Pricing Variable and for Distribution Method and Target Margin. The Pricing Variable resources should have the same name as the Pricing Variable Code, the resources for the attributes we will be using are the Attribute name (without spaces). This will allow us to use the attribute values in our cost and pricing logic.

![Resources][Resources]

Add a branch to the  Expression Set. We will set up one branch for Distribution Method (Direct) and one for Distribution Method (Indirect).

![Branch][Branch]

Under the Direct branch, create a calculation for each price and cost that defines cost as Warehousing Cost and defines price as Warehouse Cost with Target Margin.

Under the Indirect branch, create a calculation for each price and cost that defines cost as Marketing Cost and defines price as Warehouse Cost with Target Margin.

![Configured Target Pricing][Configured Target Pricing]

Run a Simulate to ensure that no calculations are left out of  either scenario. There are six calculations expected for both Direct and Indirect.

![Simulate Direct][Simulate Direct]

![Simulate Indirect][Simulate Indirect]

Once everything is being returned activate the Expression Set version.

### Create Pricing Plan Step


- Name: Field Guide - Price and Cost
- Sequence: 2
- Implementation Name: CustomPricingPlanStepImpl
- Method Name: GetMatrixPrice
- Active: True
- Parameters:

```
{"ProcedureName":"Field Guide Target Margin","MatrixName":"Field Guide - Target Margin Matrix","InputAttributeMap":"Distribution Method,Target Margin","DecisionMatrix":"true"}
```

> Note: **InputAttributeMap** is used here to enabled the use of Distribution  Method and Target Margin from the Express Set.

---



> To Add: Store these costs against attribute values on the product

> To Add: Use attribute rule to control visbility of target margin

[Attribute Category]: ../images/3-create-att-cat.png
[Attribute Creation]: ../images/3-attribute-dist-method.png
[Picklist]: ../images/3-create-picklist.png
[Attribute Created]: ../images/3-attribute-done.png
[Object Type]: ../images/3-object-type.png
[Object Type Attribute]: ../images/3-object-type-attribute.png
[Target Price Product]: ../images/3-create-product.png
[Target Price Product Record]: ../images/3-created-product.png
[Margin Attribute]: ../images/3-attribute-margin.png
[Zero Price]: ../images/3-zero-price.png
[Create Matrix]: ../images/3-create-matrix.png
[Column Mapping]: ../images/3-matrix-version-column-mapping.png
[Matrix Version]: ../images/3-matrix-version.png
[Lookup Table]: ../images/3-es-lookup-table.png
[Resources]: ../images/3-es-resources.png
[Rank]: ../images/3-es-rank.png
[Branch]: ../images/3-es-branch.png
[Configured Target Pricing]: ../images/3-es-configured.png
[Simulate Direct]: ../images/3-es-simulate-direct.png
[Simulate Indirect]: ../images/3-es-simulate-indirect.png