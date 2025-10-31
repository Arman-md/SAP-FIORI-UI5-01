#

<img width="1206" height="676" alt="image" src="https://github.com/user-attachments/assets/f435392c-6fd3-4c99-a29a-9970695844d8" />


#

<img width="1174" height="599" alt="image" src="https://github.com/user-attachments/assets/9fb2738b-82f7-4705-9578-bc0ffba594ea" />


<img width="329" height="475" alt="image" src="https://github.com/user-attachments/assets/685c0501-75ca-4d2a-a03c-2d6d425f8b62" />

## app.conroller.js

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

                    alert("now we have the app contorller for fiori like app");
                }
            }
        )
    });
```


## base controller

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


## app.view.xml


``` xml

<mvc:View xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.App">
    <!-- Put container control( contains other controls ) -->
    <App id="idAppCon"></App>
</mvc:View>
```


## Component.js


``` js

//scaffolding
sap.ui.define(
    [
        "sap/ui/core/UIComponent"
    ],

    function (UIComponent) {
        'use strict';
        return UIComponent.extend("com.plansee.coc.bc.Component", {
            // Component.js has 4 parts
            // meta data
            metadata: {
                manifest: "json" // connects componentjs with manifest.json
            },
            // initialize
            init: function () {
                // here we will call parent class consructor ( SAP UI5 Module)
                UIComponent.prototype.init.apply(this);
            },
            // create content
            createContent: function () {
                // create root view
                var oRootView = new sap.ui.view({
                    viewName: "com.plansee.coc.bc.view.App",
                    type: "XML",
                    id: "idAppView"
                });
                return oRootView;

            },
            // destroy
            destroy: function () {


            }
        });
    });


```



## index.html

``` html

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Employee Data</title>

    <!-- Load UI5 and map namespace to folder -->
    <script src="https://ui5.sap.com/resources/sap-ui-core.js"
            data-sap-ui-theme="sap_horizon_dark"
            data-sap-ui-libs="sap.m" 
            data-sap-ui-resourceroots='{"com.plansee.coc.bc": "./"}'
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


## manifest.json

``` json
{
    "sap.app": {
        "id": "com.plansee.coc.bc"
    }
}

```
