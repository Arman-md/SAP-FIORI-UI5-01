# MODEL VIEW CONTROLLER


<img width="1236" height="693" alt="image" src="https://github.com/user-attachments/assets/5b36e7ea-cc6d-4067-9dc9-77b27c20fdee" />


# VIEW

<img width="1252" height="405" alt="image" src="https://github.com/user-attachments/assets/cc1943ff-834c-45e3-8b0c-f40618309c8d" />


" main.view.js


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
                               }'></script>
    <script>

        // create object of view class using predefined function 
        var oView = new sap.ui.view({
            viewName: "jerry.view.main",
            type: "JS"
        })

        // add the button in DOM
        oView.placeAt("content");
    </script>
</head>
<!-- class name should be same...! "sapUiBody"  -->

<body class="sapUiBody">
    <div id="content">
    </div>
</body>

</html>

```



``` js

sap.ui.jsview("jerry.view.main", {
    // a JS view contains 2 built in functions with exact same name
    // getcontroller returns the name of controller where the processing logic
    // is there
    getControllerName: function () {
        return "";
    },
    // returns the object of the UI Controls
    createContent: function () {

        // sap.m is the library, which has the button class
        var oBtn = new sap.m.Button("idBtn", {
            // PROPERTY
            text: "Click me",
            icon: "sap-icon://add-employee",
            // EVENT
            press: function () {
                $("#idBtn").fadeOut(3000);
            }
        });
        return oBtn;

    }
})

```

# SCAFFOLDING SyntaX : AMD( Asynchronous Module Definition ) Like Syntax

-> Every JS File except views in SAP UI5 Starts with a special syntax called "scaffolding syntax"
-> used to define a new module/class

-> usually in a big software our code is distributed in multiple classes which work in synchronization, so that the data exchange is possible....


<img width="1279" height="654" alt="image" src="https://github.com/user-attachments/assets/cb2ea780-69ee-455d-b980-2aad35b314c9" />



# CONTROLLERS -> Always created using JS

## Scaffolding SyntaX

``` js
sap.ui.define([],
    function () {
        return {

        };
    }
);

```

<img width="1647" height="822" alt="image" src="https://github.com/user-attachments/assets/3924243a-966b-4447-809b-a0f37da41dcc" />


### JS VIEW 
``` JS

sap.ui.jsview("jerry.view.main", {
    // a JS view contains 2 built in functions with exact same name
    // getcontroller returns the name of controller where the processing logic
    // is there
    getControllerName: function () {
        return "jerry.controller.main";
    },
    // returns the object of the UI Controls( or controller as a callback)
    // sap ui5 automatically gives us object of the controllee
    createContent: function (oController) {

        // sap.m is the library, which has the button class
        var oBtn = new sap.m.Button("idBtn", {
            // PROPERTY
            text: "Click me",
            icon: "sap-icon://add-employee",
            // EVENT handler 1 -> superman 
            press: oController.superman
        });
        return oBtn;

    }
})


```

### JS CONTROLLER


<img width="1221" height="385" alt="image" src="https://github.com/user-attachments/assets/ee67efc8-f922-4da4-a153-521502513b8f" />


``` JS

// scaffolding syntax/ AMD ayntax
// current class(module) is a controller module
// this module, to work like cotroller, we add a parent module/class "sap/ui/core/mvc/Controller"( dependency module 1 )
sap.ui.define(["sap/ui/core/mvc/Controller"],

    // here we recieve the object of dependency module 1( like a json tree)
    function (Controller) {
        return Controller.extend("jerry.controller.main", {

            // a class usually has a constructor ( method )-> ours onInit
            onInit: function () {
                alert("the controller object gets created");
            },
            // what click me button does
            superman: function () {
                $("#idBtn").fadeOut(3000);
            }
        });

    }
);


```










