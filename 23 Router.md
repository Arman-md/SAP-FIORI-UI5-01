# Router

<img width="1182" height="399" alt="image" src="https://github.com/user-attachments/assets/3b1bcfbb-f5bf-42ec-93c0-7fc04b842097" />


<img width="1003" height="637" alt="image" src="https://github.com/user-attachments/assets/6734c3aa-9d14-4efd-8f37-2dd7bc27ac2d" />

<img width="1422" height="765" alt="image" src="https://github.com/user-attachments/assets/dad39c74-5e1b-430c-bf45-cfd40f68695e" />


## in manifest.json, we have the router code as below:

``` json

{
    "sap.app": {
        "id": "com.plansee.coc.bc",
        "type": "application",
        "ach": "COC-BC",
        "description": "{{appDescription}}",
        "title": "{{appTitle}}",
        "i18n": "i18n/i18n.properties",
        "applicationVersion": {
            "version": "1.0"
        }
    },
    "sap.ui": {
        "deviceTypes": {
            "desktop": true,
            "tablet": true,
            "phone": true
        },
        "fullWidth": true,
        "technology": "UI5",
        "supportedThemes": [
            "sap_fiori_3",
            "sap_fiori_3_dark",
            "sap_horizon_dark"
        ]
    },
    "sap.ui5": {
        "dependencies": {
            "libs": {
                "sap.m": {
                    "minVersion": "1.100.0"
                },
                "sap.ui.layout": {
                    "minVersion": "1.100.0"
                }
            },
            "minUI5Version": "1.100.0",
            "components": {}
        },
        "contentDensities": {
            "compact": true,
            "cozy": true
        },

/// router code
        "rootView": {
            "viewName": "com.plansee.coc.bc.view.App",
            "type": "XML",
            "id": "idRootView"
        },
        "routing": {
            "config": {
                "viewPath": "com.plansee.coc.bc.View",
                "viewType": "XML",
                "controlId": "idAppCon",
                "clearControlAggregation": true
            },
            "routes": [
                {
                    "name": "spiderman",
                    "pattern": "",
                    "target": [
                        "modi",
                        "putin"
                    ]
                },
                {
                    "name": "superman",
                    "pattern": "fruits/{fruitNum}",
                    "target": [
                        "modi",
                        "putin"
                    ]
                }
            ],
            "targets": {
                "modi": {
                    "viewName": "View1",
                    "viewIid": "idView1",
                    "controlAggregation": "masterPages"
                },
                "putin": {
                    "viewName": "View2",
                    "viewId": "idView2",
                    "controlAggregation": "detailPages"
                }
            }
        },

/// end of router code
        "models": {
            "": {
                "type": "sap.ui.model.json.JSONModel",
                "uri": "model/mockdata/fruits.json",
                "settings": {},
                "preload": true
            },
            "i18n": {
                "type": "sap.ui.model.resource.ResourceModel",
                "settings": {
                    "bundleUrl": "i18n/i18n.properties"
                },
                "preload": false
            }
        }
    }
}


```
