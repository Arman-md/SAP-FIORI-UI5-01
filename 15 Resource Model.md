# Resource  Model

<img width="1207" height="646" alt="image" src="https://github.com/user-attachments/assets/4518b4cf-d807-4f86-b234-9c647f103030" />

<img width="1840" height="924" alt="image" src="https://github.com/user-attachments/assets/dc5ee35d-7c56-470f-bcfd-f4007e7c3ebe" />

## XML View
``` xml
<!-- Name Space -->
<!-- xmlns="sap.m" meaning we are telling which is our default and 1 namespace -->
<arman:View
  xmlns:arman="sap.ui.core.mvc"
  xmlns="sap.m"
  xmlns:core="sap.ui.core"
  xmlns:t="sap.ui.table"
  xmlns:f="sap.ui.layout.form"
  controllerName="jerry.controller.Main">
    <t:Table rows="{/empTab/row}" selectionMode="Single" visibleRowCount="6" rowSelectionChange="onRowSel">
        <t:columns>
            <t:Column label="{i18n>XFLD_EMPID}">
                <t:template>
                    <Text text="{empId}"></Text>
                </t:template>
            </t:Column>
            <t:Column label="{i18n>XFLD_EMPNAME}">
                <t:template>
                    <Input value="{empName}"></Input>
                </t:template>
            </t:Column>
            <t:Column label="{i18n>XFLD_SAL}">
                <t:template>
                    <HBox >
                        <Text text="{salary}"></Text>
                        <Text text="{currency}"></Text>
                    </HBox>
                </t:template>
            </t:Column>
            <t:Column label="{i18n>XFLD_SMK}">
                <t:template>
                    <CheckBox selected="{= ${smoker} === 'true' ? true : false"></CheckBox>
                </t:template>
            </t:Column>
            <t:Column label="{i18n>XFLD_GEN}">
                <t:template>
                    <Image src="{gender}" width="30%"></Image>
                </t:template>
            </t:Column>
            <t:Column label="{i18n>XFLD_MSTAT}" >
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
            <t:Column label="{i18n>XFLD_RATE}">
                <t:template>
                    <RatingIndicator ></RatingIndicator>
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
            <Label  text="{i18n>XFLD_EMPID}"></Label>
            <!-- different ways of property binding -->
            <!-- data-sap-ui-bindingSyntax="complex"-> mandatory in index.html -->
            <Input id="idEmpid"  value="{empId}" width="15%" enabled="{dc>/empStr/editable}"/>
            <Label text="{i18n>XFLD_EMPNAME}"></Label>
            <Input id="idEmpname" value="{empName}" width="30%"  enabled="{dc>/empStr/editable}"/>
            <Label text="{i18n>XFLD_SAL}"></Label>
            <!-- If we wanna use the another expression, we use $ symbol -->
            <Input id="idEmpsal" value="{salary}"  width="20%"  enabled="{= ${dc>/empStr/empName} === 'Arman' ? false : true}"/>
            <Label text="Currency"></Label>
            <Input id="idEmpcurr"  value="{currency}" width="8%"  enabled="{dc>/empStr/editable}"/>
            <!-- add a button -->
            <Label ></Label>
            <HBox width="130%" alignContent="Stretch">
                <Button text="{i18n>XBUT_SHOW}" press="onShow" icon="sap-icon://display" ></Button>
                <Button text="{i18n>XBUT_CHANGE}" press="onChange" icon="sap-icon://edit" ></Button>
                <Button text="{i18n>XBUT_FF}" press="onFlip" icon="sap-icon://arrow-left" ></Button>
                <Switch state="true" 
                        change="onChangeMode" 
                        customTextOn="Edit mode" 
                        customTextOff="Display mode">
                </Switch>
            </HBox>
            <Select change="onLangChange">
                <items>
                    <core:Item key="en" text="English" />
                    <core:Item key="de" text="German" />
                    <core:Item key="hi" text="Hindi" />
                </items>
            </Select>
        </f:content>
    </f:SimpleForm>
</arman:View>

```


## index.html

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


## xml data

``` xml
<?xml version="1.0"?>
<data>
    <empTab>
        <row>
            <empId>10001</empId>
            <empName>Rahim</empName>
            <salary>9800</salary>
            <currency>AED</currency>
            <smoker>true</smoker>
            <gender>M</gender>
            <mStatus>U</mStatus>
            <rating>4</rating>
        </row>
        <row>
            <empId>10002</empId>
            <empName>Sara</empName>
            <salary>12000</salary>
            <currency>USD</currency>
            <smoker>true</smoker>
            <gender>F</gender>
            <mStatus>M</mStatus>
            <rating>1</rating>
        </row>
        <row>
            <empId>10003</empId>
            <empName>Ruksana</empName>
            <salary>9800</salary>
            <currency>AED</currency>
            <smoker>false</smoker>
            <gender>F</gender>
            <mStatus>O</mStatus>
            <rating>4</rating>
        </row>
        <row>
            <empId>10004</empId>
            <empName>Riyaz</empName>
            <salary>9800</salary>
            <currency>INR</currency>
            <smoker>true</smoker>
            <gender>M</gender>
            <mStatus>M</mStatus>
            <rating>1</rating>
        </row>
        <row>
            <empId>10005</empId>
            <empName>Salman</empName>
            <salary>800000</salary>
            <currency>GBP</currency>
            <smoker>false</smoker>
            <gender>M</gender>
            <mStatus>U</mStatus>
            <rating>5</rating>
        </row>
    </empTab>
</data>

```

## controller.js

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
                var oXMLModel = models.createXMLModel();
                sap.ui.getCore().getConfiguration().setLanguage("en"); // or "hi", "en"

                // Reload the i18n model
                var oResourceModel = new sap.ui.model.resource.ResourceModel({
                    bundleName: "jerry.i18n.i18n"
                });

                // var oJSONModel = models.createJSONModel("model/mockdata/sample.json");

                // Step 3: Make the app aware of the model( set the model as default data souce for the app)
                // default/fallback model( nameless)
                sap.ui.getCore().setModel(oJSONModel); // SET AS DEFAULT MODEL
                sap.ui.getCore().setModel(oXMLModel); // SET AS DEFAULT MODEL

                // naming another model( named model)
                sap.ui.getCore().setModel(oJSONModel2, "dc");

                // set resource model as default model
                // sap.ui.getCore().setModel(oResource, "i18n");
                sap.ui.getCore().setModel(oResourceModel, "i18n");

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
            onLangChange: function (oEvent) {
                var sLang = oEvent.getParameter("selectedItem").getKey();
                sap.ui.getCore().getConfiguration().setLanguage(sLang);

                var oResourceModel = new sap.ui.model.resource.ResourceModel({
                    bundleName: "jerry.i18n.i18n"
                });
                sap.ui.getCore().setModel(oResourceModel, "i18n");
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

## model.js


``` js
// scaffolding syntax
sap.ui.define([
    'sap/ui/model/json/JSONModel',
    'sap/ui/model/xml/XMLModel',
    'sap/ui/model/resource/ResourceModel'
], function (JSONModel, XMLModel, ResourceModel) {
    'use strict';
    return {
        createJSONModel: function (sFilePath) {
            // step : 1 Create a new JSON model object
            var oJSONModel = new sap.ui.model.json.JSONModel();

            oJSONModel.loadData(sFilePath);

            // we can manually set the default binding mode to one way
            // oJSONModel.setDefaultBindingMode("OneWay");
            return oJSONModel;
        },
        createXMLModel: function () {
            var oXMLModel = new XMLModel();
            oXMLModel.loadData("model/mockdata/myxmldata.xml");
            return oXMLModel;
        },
        createResourceModel: function () {
            var oResource = new ResourceModel({
                bundleName: "jerry.i18n.i18n"
            });
            return oResource;
        }

    }
})

```

## i18n_hi.properties
``` properties

XFLD_EMPID=कर्मचारी आईडी  
XFLD_EMPNAME=कर्मचारी नाम  
XFLD_SAL=वेतन  
XFLD_CURR=मुद्रा  
XFLD_MSTAT=वैवाहिक स्थिति  
XFLD_SMK=धूम्रपान करने वाला  
XFLD_RATE=रेटिंग  
XFLD_GEN=लिंग  
XBUT_SHOW=डेटा दिखाएँ  
XBUT_CHANGE=डेटा बदलें  
XBUT_FF=फ्लिप फ्लॉप  
XBUT_LOAD=डेटा लोड करें  
XTIT_EMP=कर्मचारी प्रबंधन प्रणाली 

```

## i18n.properties

``` properties

XFLD_EMPID=Employee Id
XFLD_EMPNAME=Employee Name
XFLD_SAL=Salary
XFLD_CURR=Currency
XFLD_MSTAT=Marital Status
XFLD_SMK=Smoker
XFLD_RATE=Rating
XFLD_GEN=Gender
XBUT_SHOW=Show Data
XBUT_CHANGE=Change Data
XBUT_FF=Flip Flop
XBUT_LOAD=Load Data
XTIT_EMP=Employee Management System

```


## i18n_de.properties


``` properties
XFLD_EMPID=Mitarbeiter-ID  
XFLD_EMPNAME=Mitarbeitername  
XFLD_SAL=Gehalt  
XFLD_CURR=Währung  
XFLD_MSTAT=Familienstand  
XFLD_SMK=Raucher  
XFLD_RATE=Bewertung  
XFLD_GEN=Geschlecht  
XBUT_SHOW=Daten anzeigen  
XBUT_CHANGE=Daten ändern  
XBUT_FF=Umschalten  
XBUT_LOAD=Daten laden  
XTIT_EMP=Mitarbeiterverwaltungssystem 

```



