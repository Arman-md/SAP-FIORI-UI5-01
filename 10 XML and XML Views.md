# XML - eXtensible Markup Language

<img width="1203" height="640" alt="image" src="https://github.com/user-attachments/assets/4464aec0-1764-486b-ae32-1fcdcb1d2776" />

<img width="1343" height="602" alt="image" src="https://github.com/user-attachments/assets/2c89903e-e5e7-4bd9-afc0-e0e2b6f8c481" />

<img width="1785" height="840" alt="image" src="https://github.com/user-attachments/assets/b169e4e9-55b7-45ff-8159-d139048c30fe" />


<img width="1156" height="382" alt="image" src="https://github.com/user-attachments/assets/a0ae8746-7505-4b87-8733-f1818cb876a9" />


## <img width="1168" height="608" alt="image" src="https://github.com/user-attachments/assets/3b942713-84c9-4983-96fc-c68e3e2c4197" />

<img width="1549" height="541" alt="image" src="https://github.com/user-attachments/assets/818f40ae-38ea-4981-a97f-f443b77eb502" />


# XML VIEW 

``` HTML

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

        // Create Object of the XML View
        var oViewXML = new sap.ui.view({
            //UI5Basics\webapp\view\MyXML.view.xml
            viewName: "jerry.view.Myxml",
            type: "XML",
            id: "idXMLV"
        })

        // add the button in DOM(js)
        oView.placeAt("body");

        // add to container ( body)
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

## MyXML.View.xml

``` XML

<!-- Name Space -->
<!-- xmlns="sap.m" meaning we are telling which is our default and 1 namespace -->
<arman:View
  xmlns:arman="sap.ui.core.mvc"
  xmlns="sap.m"
  controllerName="jerry.controller.Main">
    <!-- Your UI elements go here -->
    <Button text="Click button from xml"
            icon="sap-icon://checklist-item-1"
            press="batman"
            ></Button>
    <Image id="vengence"
    src="https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcQyimUBddMR3wzeCn4w7Jz9THokAnIhxX9TnSsdlugfLZjsGJV2_vbXyBTtvte8_y_ipADO3ZrTP8_4CE-O1w393hNL7AjMBBXPp5Qidg" 
    width="10%" 
    height="10%"> </Image>
</arman:View>

```


## main.controller.js

``` js
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
        });

    }
);



```









