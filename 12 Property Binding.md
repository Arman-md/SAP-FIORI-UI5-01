# Property binding & Modularization


<img width="1729" height="923" alt="image" src="https://github.com/user-attachments/assets/f69c2795-77ca-4732-b594-57e71314a0eb" />

<img width="1901" height="961" alt="image" src="https://github.com/user-attachments/assets/f1618ccc-390c-4e74-b7fb-ce2a09920694" />

<img width="1159" height="279" alt="image" src="https://github.com/user-attachments/assets/5cbfa926-c3a2-4511-a422-038319901b16" />


<img width="1185" height="584" alt="image" src="https://github.com/user-attachments/assets/c772ded0-3e86-43a3-a42b-5834d4f32a60" />

<img width="1162" height="303" alt="image" src="https://github.com/user-attachments/assets/3f94e849-f3b6-4a74-8714-9cc3c54797c8" />


<img width="1138" height="379" alt="image" src="https://github.com/user-attachments/assets/2535439d-329b-4bfd-8524-18900e607a29" />




# MVC 
<img width="615" height="565" alt="image" src="https://github.com/user-attachments/assets/65911030-4981-4c88-9e40-155fae3650b0" />

# MODEL 

## MODEL.JS
``` JS

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

            return oJSONModel;
        }
    }
})

```

## DATASET1.JSON


``` JSON

{
    "empStr": {
        "empId": 90002,
        "empName": "Superman",
        "salary": 8200,
        "currency": "AED",
        "smoker": true
    },
    "empTab": []
}

```


## SAMPLE.JSON

``` JSON

{
    "empStr": {
        "empId": 90001,
        "empName": "Spiderman",
        "salary": 9200,
        "currency": "INR",
        "smoker": false
    },
    "empTab": []
}
```

<img width="1076" height="562" alt="image" src="https://github.com/user-attachments/assets/ae5e7a88-b14b-498c-9f20-1b6262a51168" />


<img width="1108" height="512" alt="image" src="https://github.com/user-attachments/assets/98efaa07-fc2d-4338-a0a3-f0e32fa8742c" />


# Question : If we change the Data in UI Will it be saved in Model ?? Ans : Binding Modes

