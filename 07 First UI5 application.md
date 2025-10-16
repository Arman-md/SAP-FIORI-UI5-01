# What is UI5 ??

<img width="1179" height="555" alt="image" src="https://github.com/user-attachments/assets/7f3db598-4dd8-47f7-ac53-3e3bef159ae0" />


## Architecture UI5

<img width="1206" height="583" alt="image" src="https://github.com/user-attachments/assets/77bf355c-77f2-49b6-9708-0968ab53440d" />

#
<img width="1188" height="466" alt="image" src="https://github.com/user-attachments/assets/3ebcdcb7-fd49-4866-8b50-96c52fbce2fc" />


# Boot strap code : Its a code to initialize SAP UI5 Libraries ( on demand and pre load ) whenever the application starts:

ex:

<img width="1174" height="646" alt="image" src="https://github.com/user-attachments/assets/fbddf656-7d7b-4b92-bf6e-95c91e804734" />

# UI5 SDK

<img width="1656" height="833" alt="image" src="https://github.com/user-attachments/assets/98e88e1c-3d75-4440-b7e6-da005c23ef7d" />



``` JS

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://ui5.sap.com/resources/sap-ui-core.js" 
    data-sap-ui-libs="sap.m"
    data-sap-ui-theme="sap_horizon_dark" 
    data-sap-ui-resourceroots='{
                                            "jerry": "./" 
                               }'></script>
    <script>
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

        // add the button in DOM
        oBtn.placeAt("content");
    </script>
</head>
<!-- class name should be same...! "sapUiBody"  -->

<body class="sapUiBody">
    <div id="content">
    </div>
</body>

</html>

```

<img width="772" height="307" alt="image" src="https://github.com/user-attachments/assets/ee34866d-4072-49e8-9b41-7bacf2c3314f" />

<img width="853" height="343" alt="image" src="https://github.com/user-attachments/assets/23966e7f-8055-429d-b9cf-41aad39ac38e" />

