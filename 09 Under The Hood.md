# Under the hood : how entire application is wokring behind the scenes in runtime

<img width="1220" height="649" alt="image" src="https://github.com/user-attachments/assets/91cc6ba5-b031-43fb-921c-5487f14399fb" />


#
<img width="1278" height="602" alt="image" src="https://github.com/user-attachments/assets/431c192e-cf6c-4181-88e0-8b03bb69c228" />


# VIEW

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
        // add a new button on ui 
        var oInput = new sap.m.Input("idInp", {
            description: "enter something to be checked",
            autocomplete: true,
            width: "30%"

        });

        // another button
        var oBtn2 = new sap.m.Button("idBtn2", {
            text: "Check Value",
            icon: "sap-icon://checklist-item-2",
            // define and call event handler
            press: [oController.showValue, oController]
        });

        // sap.m is the library, which has the button class
        var btnName1 = "Button Name1";
        var oBtn = new sap.m.Button("idBtn", {
            // PROPERTY
            text: btnName1,
            icon: "sap-icon://add-employee",
            // EVENT handler 1 -> superman 
            press: [oController.superman, oController]
        });
        return [oBtn, oInput, oBtn2];

    }
})

```


# CONTROLLER

``` JS

// scaffolding syntax/ AMD ayntax
// current class(module) is a controller module
// this module, to work like cotroller, we add a parent module/class "sap/ui/core/mvc/Controller"( dependency module 1 )
sap.ui.define(["sap/ui/core/mvc/Controller"],

    // here we recieve the object of dependency module 1( like a json tree)

    // extend means -> inhertance in JS
    function (Controller) {
        return Controller.extend("jerry.controller.main", {
            arman: 0,
            // a class usually has a constructor ( method )-> ours onInit
            onInit: function () {
                // arman is a global variable ( accessible within controller class)
                // this : is the pointer of current class object (of controller )manually we need r
                this.arman = 5000;
                this.btnName2 = "Button Name2";
                alert("the controller object gets created");
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
        });

    }
);

```

<img width="921" height="155" alt="image" src="https://github.com/user-attachments/assets/4f8fc547-9ffa-4a63-868e-3561b6ebd972" />


<img width="1242" height="241" alt="image" src="https://github.com/user-attachments/assets/4a06d107-efb0-49fd-9eee-cf83b8c30442" />


# Control Hierarchy

<img width="1158" height="676" alt="image" src="https://github.com/user-attachments/assets/b33f6a17-e0d4-429f-b3cc-1e553cca4e45" />

# Basics of OOPS

Inheritance,
Association -> Aggregation and Composition

<img width="1191" height="644" alt="image" src="https://github.com/user-attachments/assets/9f864990-bb91-449c-8475-8425099687c3" />










