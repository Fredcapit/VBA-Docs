---
title: Application.DLookup method (Access)
keywords: vbaac10.chm12529
f1_keywords:
- vbaac10.chm12529
ms.prod: access
api_name:
- Access.Application.DLookup
ms.assetid: cbe1fc56-e4d7-cb74-02df-48fc379cf432
ms.date: 12/17/2019
ms.localizationpriority: medium
---


# Application.DLookup method (Access)

Use the **DLookup** function to get the value of a particular field from a specified set of records (a domain).


## Syntax

_expression_.**DLookup** (_Expr_, _Domain_, _Criteria_)

_expression_ A variable that represents an **[Application](Access.Application.md)** object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
| _Expr_|Required|**String**|An expression that identifies the field whose value you want to return. It can be a string expression identifying a field in a table or query, or it can be an expression that performs a [calculation on data in that field](../access/Concepts/Criteria-Expressions/calculate-fields-in-domain-aggregate-functions.md). In _expr_, you can include the name of a field in a table, a control on a form, a constant, or a function. If _expr_ includes a function, it can be either built-in or user-defined, but not another domain aggregate or SQL aggregate function.|
| _Domain_|Required|**String**|A string expression identifying the set of records that constitutes the domain. It can be a table name or a query name for a query that does not require a parameter.|
| _Criteria_|Optional|**Variant**|An optional string expression used to restrict the range of data on which the **DLookup** function is performed. For example, _criteria_ is often equivalent to the WHERE clause in an SQL expression, without the word WHERE. If _criteria_ is omitted, the **DLookup** function evaluates _expr_ against the entire domain. Any field that is included in _criteria_ must also be a field in _domain_; otherwise, the **DLookup** function returns a **Null**.|

## Return value

Variant


## Remarks

Use the **DLookup** function to display the value of a field that isn't in the record source for your form or report. For example, suppose you have a form based on an Order Details table. The form displays the **OrderID**, **ProductID**, **UnitPrice**, **Quantity**, and **Discount** fields. However, the **ProductName** field is in another table, the Products table. You could use the **DLookup** function in a calculated control to display the **ProductName** on the same form.

The **DLookup** function returns a single field value based on the information specified in _criteria_. Although  _criteria_ is an optional argument, if you don't supply a value for _criteria_, the **DLookup** function returns a random value in the domain.

If no record satisfies _criteria_, or if _domain_ contains no records, the **DLookup** function returns a **Null**.

If more than one field meets _criteria_, the **DLookup** function returns the first occurrence. You should specify criteria that will ensure that the field value returned by the **DLookup** function is unique. You may want to use a primary key value for your criteria, such as `[EmployeeID]` in the following example, to ensure that the **DLookup** function returns a unique value:

```vb
Dim varX As Variant 
varX = DLookup("[LastName]", "Employees", "[EmployeeID] = 1")
```

Whether you use the **DLookup** function in a macro or module, a query expression, or a calculated control, you must construct the _criteria_ argument carefully to ensure that it will be evaluated correctly.

Use the **DLookup** function to specify criteria in the **Criteria** row of a query, within a calculated field expression in a query, or in the **Update To** row in an update query.

You can also use the **DLookup** function in an expression in a calculated control on a form or report if the field that you need to display isn't in the record source on which your form or report is based. For example, suppose you have an Order Details form based on an Order Details table with a text box called ProductID that displays the **ProductID** field. To look up **ProductName** from a Products table based on the value in the text box, you could create another text box and set its **ControlSource** property to the following expression:

```vb
=DLookup("[ProductName]", "Products", "[ProductID] =" _ 
     & Forms![Order Details]!ProductID)
```

> [!TIP] 
> - Although you can use the **DLookup** function to display a value from a field in a foreign table, it may be more efficient to create a query that contains the fields that you need from both tables and then to base your form or report on that query.
> - You can also use the Lookup Wizard to find values in a foreign table.
    

## Example

The following example returns name information from the **CompanyName** field of the record satisfying  _criteria_. The domain is a Shippers table. The _criteria_ argument restricts the resulting set of records to those for which ShipperID equals 1.

```vb
Dim varX As Variant 
varX = DLookup("[CompanyName]", "Shippers", "[ShipperID] = 1")
```

<br/>

The next example from the Shippers table uses the form control ShipperID to provide criteria for the **DLookup** function. Note that the reference to the control isn't included in the quotation marks that denote the strings. This ensures that each time the **DLookup** function is called, Microsoft Access will obtain the current value from the control.

```vb
Dim varX As Variant 
varX = DLookup("[CompanyName]", "Shippers", "[ShipperID] = " _ 
    & Forms!Shippers!ShipperID)
```

<br/>

The next example uses a variable, `intSearch`, to get the value.

```vb
Dim intSearch As Integer 
Dim varX As Variant 
 
intSearch = 1 
varX = DLookup("[CompanyName]", "Shippers", _ 
    "[ShipperID] = " & intSearch)
```

<br/>

The following examples show how to use various types of criteria with the **DLookup** function.

```vb
    ' ***************************
    ' Typical Use
    ' Numerical values. Replace "number" with the number to use.
    variable = DLookup("[FieldName]", "TableName", "[Criteria] = number")

    ' Strings.
    ' Numerical values. Replace "string" with the string to use.
    variable = DLookup("[FieldName]", "TableName", "[Criteria]= 'string'")

    ' Dates. Replace "date" with the string to use.
    variable = DLookup("[FieldName]", "TableName", "[Criteria]= #date#")
    ' ***************************

    ' ***************************
    ' Referring to a control on a form
    ' Numerical values
    variable = DLookup("[FieldName]", "TableName", "[Criteria] = " & Forms!FormName!ControlName)

    ' Strings
    variable = DLookup("[FieldName]", "TableName", "[Criteria] = '" & Forms!FormName!ControlName & "'")

    ' Dates
    variable = DLookup("[FieldName]", "TableName", "[Criteria] = #" & Forms!FormName!ControlName & "#")
    ' ***************************

    ' ***************************
    ' Combinations
    ' Multiple types of criteria
    variable = DLookup("[FieldName]", "TableName", "[Criteria1] = " & Forms![FormName]![Control1] _
             & " AND [Criteria2] = '" & Forms![FormName]![Control2] & "'" _
            & " AND [Criteria3] =#" & Forms![FormName]![Control3] & "#")
    
    ' Use two fields from a single record.
    variable = DLookup("[LastName] & ', ' & [FirstName]", "tblPeople", "[PrimaryKey] = 7")
            
    ' Expressions
    variable = DLookup("[Field1] + [Field2]", "tableName", "[PrimaryKey] = 7")
    
    ' Control Structures
    variable = DLookup("IIf([LastName] Like 'Smith', 'True', 'False')", "tableName", "[PrimaryKey] = 7")
    ' ***************************
```
<br/>
The following example shows how to use **DLookUp** in a Do Loop. It demonstrates how to build the Criteria string on each pass through the loop.

```vba
' The loop verifies data from an input data set, in this case Operating System names, 
' against those contained in a Master List.

Do Until I1 &gt; NRec1
    ' An apostrophe is concatenated at the beginning and at the end of a datum referenced by "rs1!OS", 
    ' which is then concatenated to build the entire criteria string.
    Str_2 = "'" & rs1!OS & "'"
    Str_1 = "[OS] = " & Str_2
    
    J1 = DLookup("[ID]", "tbl_81_Operating_Systems_Master_List", Str_1)
    
    If IsNull(J1) = True Then
        ' If an OS name is not found, then a flag is set and the name of the unknown OS is output to a table.
        rs3.AddNew
        rs3.OS = rs1!OS
        rs3.Update
        Err_Fl = False

    End If

    rs1.MoveNext
    I1 = I1 + 1

Loop
```



[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
