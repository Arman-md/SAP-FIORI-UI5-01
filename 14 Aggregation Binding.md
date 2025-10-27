# Agggregation BINDING

## Absolute Path annd relative Path


<img width="1184" height="672" alt="image" src="https://github.com/user-attachments/assets/f092097a-308e-4638-8091-0b6c0074a899" />

## Use case

<img width="1178" height="553" alt="image" src="https://github.com/user-attachments/assets/0b1a571f-8c7f-4d0f-b263-2a3fbc93fe7a" />

## Element Binding




<img width="1203" height="689" alt="image" src="https://github.com/user-attachments/assets/2f0b0424-2219-4aaa-bd95-1959dde898d4" />


<img width="1189" height="442" alt="image" src="https://github.com/user-attachments/assets/f2a8937f-6009-4be3-894e-a47b00da62f0" />


### Row selection event upon UI-Row selection

<img width="1704" height="791" alt="image" src="https://github.com/user-attachments/assets/39c28327-d64c-4e51-a941-15fe22900982" />


### and how to get the address of the model data selected in UI ?

<img width="1885" height="979" alt="image" src="https://github.com/user-attachments/assets/3ab0bfae-bfdc-46de-9ff5-28e726fc054e" />


## Solution: use element binding

### XML View
``` XML

<!-- Name Space -->
<!-- xmlns="sap.m" meaning we are telling which is our default and 1 namespace -->
<arman:View
  xmlns:arman="sap.ui.core.mvc"
  xmlns="sap.m"
  xmlns:core="sap.ui.core"
  xmlns:t="sap.ui.table"
  xmlns:f="sap.ui.layout.form"
  controllerName="jerry.controller.Main">
    <t:Table rows="{/empTab}" selectionMode="Single" visibleRowCount="6" rowSelectionChange="onRowSel">
        <t:columns>
            <t:Column label="Emp Id">
                <t:template>
                    <Text text="{empId}"></Text>
                </t:template>
            </t:Column>
            <t:Column label="Emp Name">
                <t:template>
                    <Input value="{empName}"></Input>
                </t:template>
            </t:Column>
            <t:Column label="Salary">
                <t:template>
                    <HBox >
                        <Text text="{salary}"></Text>
                        <Text text="{currency}"></Text>
                    </HBox>
                </t:template>
            </t:Column>
            <t:Column label="Smoker">
                <t:template>
                    <CheckBox selected="{smoker}"></CheckBox>
                </t:template>
            </t:Column>
            <t:Column label="Gender">
                <t:template>
                    <Image src="{gender}" width="30%"></Image>
                </t:template>
            </t:Column>
            <t:Column label="Marital Status" >
                <t:template>
                    <Select selectedKey="{mStatus}" >
                        <items>
                            <core:Item key="M" text="Married"></core:Item>
                            <core:Item key="U" text="Unmarried"></core:Item>
                            <core:Item key="O" text="Other"></core:Item>
                        </items>
                    </Select>
                </t:template>
            </t:Column>
            <t:Column label="Rating">
                <t:template>
                    <RatingIndicator value="{Rating}"></RatingIndicator>
                </t:template>
            </t:Column>
        </t:columns>
    </t:Table>
    <!-- Task : Simple layout -->
    <!-- Parent  -->
    <f:SimpleForm  editable="true" id="idSimpleForm">
        <!-- aggregation(child) parent + camelcase -->
        <f:content>
            <!-- syntax of ending a tag can be both <***></> also <***/> -->
            <Label  text="Employee ID"></Label>
            <!-- different ways of property binding -->
            <!-- data-sap-ui-bindingSyntax="complex"-> mandatory in index.html -->
            <Input id="idEmpid"  value="{empId}" width="15%" enabled="{/empStr/editable}"/>
            <Label text="Employee Name"></Label>
            <Input id="idEmpname" value="{empName}" width="30%"  enabled="{/empStr/editable}"/>
            <Label text="Employee Salary"></Label>
            <!-- If we wanna use the another expression, we use $ symbol -->
            <Input id="idEmpsal" value="{salary}"  width="20%"  enabled="{= ${/empStr/empName} === 'Arman' ? false : true}"/>
            <Label text="Currency"></Label>
            <Input id="idEmpcurr"  value="{currency}" width="8%"  enabled="{/empStr/editable}"/>
            <!-- add a button -->
            <Label ></Label>
            <HBox width="130%" alignContent="Stretch">
                <Button text="Show Data" press="onShow" icon="sap-icon://display" ></Button>
                <Button text="Change the data" press="onChange" icon="sap-icon://edit" ></Button>
                <Button text="Flip Flop" press="onFlip" icon="sap-icon://arrow-left" ></Button>
                <Switch state="true" 
                        change="onChangeMode" 
                        customTextOn="Edit mode" 
                        customTextOff="Display mode">
                </Switch>
            </HBox>
        </f:content>
    </f:SimpleForm>
</arman:View>

```

### controller:


``` js
// scaffolding syntax/ AMD ayntax
// current class(module) is a controller module
// this module, to work like cotroller, we add a parent module/class "sap/ui/core/mvc/Controller"( dependency module 1 )
sap.ui.define(["sap/ui/core/mvc/Controller",
    "jerry/model/models"],

    // here we recieve the object of dependency module 1( like a json tree)

    // extend means -> inhertance in JS
    function (Controller, models) {
        return Controller.extend("jerry.controller.main", {
            arman: 0,
            // a class usually has a constructor ( method )-> ours onInit
            onInit: function () {
                // arman is a global variable ( accessible within controller class)
                // this : is the pointer of current class object (of controller )manually we need r
                this.arman = 5000;
                this.btnName2 = "Button Name2";

                // use multiple models object
                var oJSONModel = models.createJSONModel("model/mockdata/sample.json");
                var oJSONModel2 = models.createJSONModel("model/mockdata/dataset1.json");
                // var oJSONModel = models.createJSONModel("model/mockdata/sample.json");

                // Step 3: Make the app aware of the model( set the model as default data souce for the app)
                // default/fallback model( nameless)
                sap.ui.getCore().setModel(oJSONModel);

                // naming another model( named model)
                sap.ui.getCore().setModel(oJSONModel2, "dc");

                // // learning syntax property binding : 1
                // // emp id
                // var oEmpid = this.getView().byId("idEmpid");
                // oEmpid.bindValue("/empStr/empId");

                // // emp name
                // var oEmpname = this.getView().byId("idEmpname");
                // oEmpname.bindValue("/empStr/empName");

                // var oSalary = this.getView().byId("idEmpsal");
                // oSalary.bindValue("/empStr/salary");

                // // learning syntax property binding : 2
                // var oCurr = this.getView().byId("idEmpcurr");
                // oCurr.bindProperty("value", "/empStr/currency");

            },

            batman: function () {
                // alert("I AM Vengence");
                // this.superman();

                // change width and height of our image
                // on click

                // get object of view
                var oView = this.getView();
                var oBatman = oView.byId("vengence");

                // change width and height
                oBatman.setWidth("25%").setHeight("40%");
            },

            // what click me button does
            superman: function () {
                console.log(this.arman);
                // logic to fade out button on click
                //$("#idBtn").fadeOut(3000);

                // change the text on the button dynamically on the click
                // we need button object from view( ui5 object )

                // 1st method  -> get object of the UI5 runtime application
                var oApp = sap.ui.getCore();
                // get button object by id
                var oBtn = oApp.byId("idBtn");

                // or var oBtn = sap.ui.getCore().byId("idBtn"); 
                // get the current text
                var cText = oBtn.getText();

                // change text
                if (cText === "Button Name2") {
                    oBtn.setText("Button Name1");
                    oBtn.setIcon("sap-icon://female");
                } else {
                    oBtn.setText("Button Name2");
                    oBtn.setIcon("sap-icon://male");
                }
            },

            showValue: function () {
                // GET OBJECT OF APPLICATION
                var oApp = sap.ui.getCore();

                // get object of control
                var oInp = oApp.byId("idInp");

                // read the value and print on the UI.
                var sVal = oInp.getValue();

                // print value to the user
                alert(sVal);
            },


            // ID Based coding has disavantages such as :
            // number of lines of code is higher.
            // logic is risky.. ( logic is tightly coupled to "id" if any change in id name, results in dumpls in dependency logic)
            // hence we use the concept of "Models"
            onFlip: function () {
                // this function is to flip flop the model on click of button

                // get default model object (get current model)
                var oModel = sap.ui.getCore().getModel();

                // get named model object
                var oDCModel = sap.ui.getCore().getModel("dc");

                // FLIP Models
                sap.ui.getCore().setModel(oDCModel);
                sap.ui.getCore().setModel(oModel, "dc");


            },

            // on row selection 
            onRowSel: function (oEvent) {
                // debugger;

                // get address of the row selected in UI 
                var sAdress = oEvent.getParameter("rowContext").sPath;
                // get the object of the simple for 
                var oSimpleForm = this.getView().byId("idSimpleForm");

                // bind the selected element to the simple form
                oSimpleForm.bindElement(sAdress);
            },
            // change the edit/disp modes
            onChangeMode: function () {
                // this function is to flip flop the model on click of button

                // get default model object (get current model)
                var oModel = sap.ui.getCore().getModel();
                var sBool = oModel.getProperty("/empStr/editable");
                if (sBool === true) {
                    // FLIP Models
                    oModel.setProperty("/empStr/editable", false);
                } else {
                    // FLIP Models
                    oModel.setProperty("/empStr/editable", true);
                }


            },

            onChange: function () {
                // step 1 : get the object of model
                var oModel = sap.ui.getCore().getModel();

                // CHANGE The data for emp str ( one way change )
                oModel.setProperty("/empStr/empName", "Rock");
                oModel.setProperty("/empStr/salary", "454544454");

            },

            onShow: function () {
                // // step 1 get the control objects
                // var oEmpid = this.getView().byId("idEmpid");
                // var oEmpname = this.getView().byId("idEmpname");
                // var oEmpsal = this.getView().byId("idEmpsal");
                // var oEmpcurr = this.getView().byId("idEmpcurr");


                // // get the values of input fields
                // var sEmpid = oEmpid.getValue();
                // var sEmpname = oEmpname.getValue();
                // var sEmpsal = oEmpsal.getValue();
                // var sEmpcurr = oEmpcurr.getValue();

                // or ( get rid of id based coding )

                //get model object
                var oModel = sap.ui.getCore().getModel();

                //from the model object, we can access the data in just one line..!
                var oEmpData = oModel.getProperty("/empStr");

                // show data
                // console.log(`Employee with Id: ${sEmpid} name:${sEmpname} has a salary of ${sEmpsal} ${sEmpcurr}.`);
                console.log(oEmpData);

            }
        });

    }
);


```


### model.js


``` js

// scaffolding syntax
sap.ui.define([
    'sap/ui/model/json/JSONModel'
], function (JSONModel) {
    'use strict';
    return {
        createJSONModel: function (sFilePath) {
            // step : 1 Create a new JSON model object
            var oJSONModel = new sap.ui.model.json.JSONModel();

            oJSONModel.loadData(sFilePath);

            // we can manually set the default binding mode to one way
            // oJSONModel.setDefaultBindingMode("OneWay");
            return oJSONModel;
        }
    }
})



```

### sample data 


``` json

{
    "empStr": {
        "empId": 90001,
        "empName": "Spiderman",
        "salary": 9200,
        "currency": "INR",
        "smoker": false,
        "editable": true
    },
    "empTab": [
        {
            "empId": 90003,
            "empName": "Green Lantern",
            "salary": 600,
            "currency": "INR",
            "smoker": true,
            "gender": "https://cdn-icons-png.flaticon.com/512/3233/3233508.png",
            "mStatus": "M",
            "Rating": 3
        },
        {
            "empId": 90004,
            "empName": "Blue Lantern",
            "salary": 5500,
            "currency": "INR",
            "smoker": true,
            "gender": "https://png.pngtree.com/png-vector/20190411/ourmid/pngtree-vector-woman-icon-png-image_927239.jpg",
            "mStatus": "U",
            "Rating": 1.9
        },
        {
            "empId": 90005,
            "empName": "Yellow Lantern",
            "salary": 450,
            "currency": "INR",
            "smoker": true,
            "gender": "https://cdn-icons-png.flaticon.com/512/3233/3233508.png",
            "mStatus": "M",
            "Rating": 2.5
        },
        {
            "empId": 90006,
            "empName": "Black Lantern",
            "salary": 40,
            "currency": "INR",
            "smoker": true,
            "gender": "https://png.pngtree.com/png-vector/20190411/ourmid/pngtree-vector-woman-icon-png-image_927239.jpg",
            "mStatus": "U",
            "Rating": 5
        },
        {
            "empId": 90007,
            "empName": "Red Lantern",
            "salary": 5000,
            "currency": "INR",
            "smoker": true,
            "gender": "https://png.pngtree.com/png-vector/20190411/ourmid/pngtree-vector-woman-icon-png-image_927239.jpg",
            "mStatus": "M",
            "Rating": 1
        }
    ]
}

```

### index.html


``` html

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://ui5.sap.com/resources/sap-ui-core.js" data-sap-ui-libs="sap.m"
        data-sap-ui-theme="sap_horizon_dark" data-sap-ui-resourceroots='{
                                            "jerry": "./" 
                               }' data-sap-ui-bindingSyntax="complex"></script>
    <script>

        // // create object of view class using predefined function 
        // var oView = new sap.ui.view({
        //     viewName: "jerry.view.main",
        //     type: "JS"
        // })

        // Create Object of the XML View
        var oViewXML = new sap.ui.view({
            //UI5Basics\webapp\view\MyXML.view.xml
            viewName: "jerry.view.Myxml",
            type: "XML",
            id: "idXMLV"
        })

        // add the button in DOM(js)
        //oView.placeAt("body");

        // add to container ( body(xml))
        oViewXML.placeAt("container");
    </script>
</head>
<!-- class name should be same...! "sapUiBody"  -->

<body class="sapUiBody">
    <div id="body">
    </div>

    <div id="container"></div>
</body>

</html>
```


### Output:

<img width="1904" height="904" alt="image" src="https://github.com/user-attachments/assets/f28b30cb-faa5-4316-b9ba-31f289b51150" />


