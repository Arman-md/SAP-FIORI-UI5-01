# Continuation of FIORI Like app


<img width="1186" height="639" alt="image" src="https://github.com/user-attachments/assets/f6a9f87f-5e85-44ae-b659-0c448a7e394e" />



<img width="1722" height="873" alt="image" src="https://github.com/user-attachments/assets/797435a6-e2b2-4618-a817-69b200e5ace3" />


<img width="1636" height="745" alt="image" src="https://github.com/user-attachments/assets/2746e399-8192-4190-abf1-0e78e0318e1a" />


<img width="1727" height="790" alt="image" src="https://github.com/user-attachments/assets/5bc7a7de-405a-4fdb-bd99-0821e3038983" />



<img width="1779" height="818" alt="image" src="https://github.com/user-attachments/assets/f7d7a3d3-9c97-4154-83c6-d5b9109e7caf" />


## index.html 

``` html

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Employee Data</title>

    <!-- Load UI5 and map namespace to folder -->
    <script src="https://ui5.sap.com/resources/sap-ui-core.js" data-sap-ui-theme="sap_horizon_dark"
        data-sap-ui-libs="sap.m" data-sap-ui-resourceroots='{"com.plansee.coc.bc": "./"}'
        data-sap-ui-bindingSyntax="complex">
        </script>

    <script>
        // Create and place the ComponentContainer
        var oCompContainer = new sap.ui.core.ComponentContainer({
            name: "com.plansee.coc.bc"
        });
        oCompContainer.placeAt("content");
    </script>
</head>

<body class="sapUiBody">
    <div id="content"></div>
</body>

</html>
```


## Package.json

``` json
{
  "name": "fiorilikeapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


```


## ui5.yaml

``` yaml

specVersion: "4.0"
metadata:
  name: fiorilikeapp
type: application

```


# webapp

## Controller


### App.controller.js


``` js

//scaffolding
sap.ui.define(

    [
        'com/plansee/coc/bc/controller/BaseController'
    ], function (Controller) {
        'use strict';
        return Controller.extend("com.plansee.coc.bc.controller.App",
            {
                onInit: function () {

                    // alert("now we have the app contorller for fiori like app");
                }
            }
        )
    });


```


### Base.controller.js

``` js

//scaffolding
sap.ui.define(

    [
        "sap/ui/core/mvc/Controller"
    ], function (Controller) {
        'use strict';
        return Controller.extend("com.plansee.coc.bc.controller.BaseController",
            {

            }
        )
    });
```

### view1.controller.js

``` js

//scaffolding
sap.ui.define(

    [
        'com/plansee/coc/bc/controller/BaseController'
    ], function (Controller) {
        'use strict';
        return Controller.extend("com.plansee.coc.bc.controller.View1",
            {
                onInit: function () {

                    // alert("now we have the app contorller for fiori like app");
                },

                onNext: function () {
                    // navigation is only possible between child views by parent only....!

                    // step 1 : get the object of the currnet view
                    var oView = this.getView();

                    // step 2 : get the object of the parent view (App) where view1 has been added as child
                    var oAppCon = oView.getParent();

                    // step 3 : Use this container to navigate to 2nd view by passing id of 2nd view
                    oAppCon.to("idView2");

                }
            }
        )
    });

```

### view2.controller.js


``` js

//scaffolding
sap.ui.define(

    [
        'com/plansee/coc/bc/controller/BaseController',
        'sap/m/MessageBox',
        'sap/m/MessageToast'
    ], function (Controller, MessageBox, MessageToast) {
        'use strict';
        return Controller.extend("com.plansee.coc.bc.controller.View2",
            {
                onInit: function () {

                    // alert("now we have the app contorller for fiori like app");
                },

                onBack: function () {
                    // navigation is only possible between child views by parent only....!

                    // step 1 : get the object of the currnet view
                    var oView = this.getView();

                    // step 2 : get the object of the parent view (App) where view1 has been added as child
                    var oAppCon = oView.getParent();

                    // step 3 : Use this container to navigate to 1nd view by passing id of 1 view
                    oAppCon.to("idView1");

                },

                onSave: function () {
                    MessageBox.confirm("Would you like to save ?", {
                        title: " Arman's Confirmation",
                        onClose: this.onHandleMessage
                    });
                },

                onHandleMessage: function (status) {
                    // console.log(status);
                    if (status === "OK") {
                        MessageToast.show("Wow, the  order has been saved");
                    } else {
                        MessageBox.error("Ooops..! There was an error..!");
                    }
                }
            }
        )
    });


```



## VIEW

### app.view

``` xml

<mvc:View xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.App">
    <!-- Put APP container control( contains other controls ) -->
    <App id="idAppCon"></App>
</mvc:View>

```


### view1.view.xml


``` xml

<mvc:View xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.View1">
    <!-- Put APP container control( contains other controls ) -->
    <Page title="First View" >
        <content>
            <!-- <Button text="Next Page" press="onNext"></Button> -->
            <SearchField id="idSearch"></SearchField>
            <List id="idList"></List>
        </content>
        <headerContent>
            <Button icon="sap-icon://initiative" press="onNext" tooltip="Navigate to next sceen"></Button>
        </headerContent>
    </Page>
</mvc:View>

```


### View2.view.xml


``` xml

<mvc:View xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.View2">
    <!-- Put APP container control( contains other controls ) -->
    <Page title="Second View" showNavButton="true" navButtonPress="onBack">
        <content>
            <!-- <Button text="Back" press="onBack"></Button> -->
        </content>
        <headerContent>
            <Button icon="sap-icon://nav-back" press="onBack" tooltip="Navigate to last sceen"></Button>
        </headerContent>
        <footer>
            <Toolbar >
                <ToolbarSpacer />
                <Button text="Save" type="Accept" press="onSave" tooltip="click to save"/>
                <Button text="Cancel" type="Reject" press="onCancel"/>
            </Toolbar>
        </footer>
    </Page>
</mvc:View>

```


# output :

## View 1

<img width="853" height="326" alt="image" src="https://github.com/user-attachments/assets/f77d0123-a1f7-453e-a035-54aa3641d319" />


## View 2

<img width="872" height="1042" alt="image" src="https://github.com/user-attachments/assets/d0002b2f-3bd3-497c-88d5-5835fc372ecb" />
<img width="859" height="1019" alt="image" src="https://github.com/user-attachments/assets/57b4b12f-6552-4910-abfd-d89c96d8fe7f" />

<img width="851" height="1029" alt="image" src="https://github.com/user-attachments/assets/b860225b-cf69-408a-9c4a-0c6b076bfd7f" />












