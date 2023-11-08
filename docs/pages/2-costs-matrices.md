# Price and Cost Matrices

This section covers using Attribute Based Pricing to define both prices and costs from a Decision Matrix.

## Initial Setup

Configure ABP as per the [Process Library](https://github.com/Salesforce-Industries-Process-Library/Industries-CPQ).

### Create Matrix

In this case we will set prices and costs using a Decision Matrix.

Navigate to Business Rules Engine > Lookup Tables and click on 'New'.

Selct 'Decision MAtrix and click 'Next'.

![Price Cost Matrix][Price Cost Matrix]

Click on the matrix version and upload the (/data/Price Cost Matrix.csv).

Map the columns as per the screenshot below:

![Matrix Columns][Matrix Columns]

Activate the matrix version.

### Create Expression Set

Navigate to Business Rules Engine > Express Sets and click 'New'.

![Price Cost Expression Set][Price Cost Expression Set]

Click on the Express Set version to open the Expression Set Builder.

Add a rank to the Expression Set Version. Note that generally speaking the rank will be equal to the version. The lower the rank the higher the priority if multiple versions are active.

![Rank][Rank]

Add a Lookup Table element and map it to the Matrix you just created.

![Expression Set Build 1][Expression Set Build 1]

Notice that the input and output columns are mapped automatically. The next step is to create a resource of type variable for each pricing variable using the pricing variabnle code as the name of the resource.

![Resources][Resources]

Next add a Calculation Step for each resource and map the matching output column from the matrix.

![Calculation Example][Calculation Example]

Make sure to tick the 'Include in Output' flag.

![Output Flag][Output Flag]

Repeat for each resource added.

![All Calculations][All Calculations]

Save and then click on 'Simulate'

Type in Input values that exist in the matrix and click on Simulate. There should be a response calculation for each resource createad.

![Simulate][Simulate]

Click on back and activate this Expression Set Version.

### Create Pricing Plan Step

Navigate to Vlocity PRicing Designer > Pricing Plans > Default Pricing Plan and click on 'New' under the Pricing Plan Steps section.

- Name: Field Guide - Price and Cost
- Sequence: 2
- Implementation Name: CustomPricingPlanStepImpl
- Method Name: GetMatrixPrice
- Active: True
- Parameters:

```
{"ProcedureName":"Field Guide Price Cost Set","MatrixName":"Field Guide - Cost and Margin Matrix","DecisionMatrix":"true"}
```

Run the CMT Administration CPQ Jobs (Product Hierarchy Maintenance, Clear Managed Platform Cache, Refresh Platform Cache).

### Test in Cart

Create an order and add the Test Attribute product to the cart. Notice that PLEs are still present. Now click on configure and set an attribute value for Distribution Region. Notice that prices and costs are now set according to the matrix values.

![Order Product Detail][Order Product Detail]

[Matrix Columns]: ../images/2-matrix-columns.png
[Price Cost Matrix]: ../images/2-price-cost-matrix.png
[Price Cost Expression Set]: ../images/2-price-cost-expression-set.png
[Expression Set Build 1]: ../images/2-price-cost-set-build-1.png
[Resources]: ../images/2-price-cost-set-build-2.png
[Calculation Example]: ../images/2-calculation-example.png
[Output Flag]: ../images/2-output-flag.png
[All Calculations]: ../images/2-price-cost-set-build-3.png
[Simulate]: ../images/2-price-cost-simulate.png
[Rank]: ../images/2-price-cost-rank.png
[Order Product Detail]: ../images/2-price-cost-orderitem-detail.png