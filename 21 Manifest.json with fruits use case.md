## Use Case


<img width="1277" height="314" alt="image" src="https://github.com/user-attachments/assets/bebef191-8917-4809-8c8c-8ca0ee1764f7" />


### sample data : fruits.json

``` json

{
    "fruits": [
        {
            "fruitNum": "1",
            "name": "Mango",
            "category": "alkaline",
            "type": "tropical",
            "color": "yellow",
            "price": 100,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Mangos_-_single_and_halved.jpg/500px-Mangos_-_single_and_halved.jpg",
            "healthBenefit": "Rich in vitamins A and C"
        },
        {
            "fruitNum": "2",
            "name": "Orange",
            "category": "citrus",
            "type": "citrus",
            "color": "orange",
            "price": 80,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Oranges_-_whole-halved-segment.jpg/500px-Oranges_-_whole-halved-segment.jpg",
            "healthBenefit": "Boosts immune system"
        },
        {
            "fruitNum": "3",
            "name": "Banana",
            "category": "neutral",
            "type": "tropical",
            "color": "yellow",
            "price": 40,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/Bananavarieties.jpg/250px-Bananavarieties.jpg",
            "healthBenefit": "Good source of potassium"
        },
        {
            "fruitNum": "4",
            "name": "Guava",
            "category": "alkaline",
            "type": "tropical",
            "color": "green",
            "price": 60,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Guava_pink_fruit.jpg/250px-Guava_pink_fruit.jpg",
            "healthBenefit": "Improves digestion"
        },
        {
            "fruitNum": "5",
            "name": "Lemon",
            "category": "citrus",
            "type": "citrus",
            "color": "yellow",
            "price": 30,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/P1030323.JPG/250px-P1030323.JPG",
            "healthBenefit": "Aids in detoxification"
        },
        {
            "fruitNum": "6",
            "name": "Papaya",
            "category": "alkaline",
            "type": "tropical",
            "color": "orange",
            "price": 50,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Carica_papaya_-_K%C3%B6hler%E2%80%93s_Medizinal-Pflanzen-029.jpg/250px-Carica_papaya_-_K%C3%B6hler%E2%80%93s_Medizinal-Pflanzen-029.jpg",
            "healthBenefit": "Supports digestion"
        },
        {
            "fruitNum": "7",
            "name": "Apple",
            "category": "neutral",
            "type": "temperate",
            "color": "red",
            "price": 120,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a6/Pink_lady_and_cross_section.jpg/250px-Pink_lady_and_cross_section.jpg",
            "healthBenefit": "Promotes heart health"
        },
        {
            "fruitNum": "8",
            "name": "Pineapple",
            "category": "alkaline",
            "type": "tropical",
            "color": "brown",
            "price": 90,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/%E0%B4%95%E0%B5%88%E0%B4%A4%E0%B4%9A%E0%B5%8D%E0%B4%9A%E0%B4%95%E0%B5%8D%E0%B4%95.jpg/250px-%E0%B4%95%E0%B5%88%E0%B4%A4%E0%B4%9A%E0%B5%8D%E0%B4%9A%E0%B4%95%E0%B5%8D%E0%B4%95.jpg",
            "healthBenefit": "Anti-inflammatory properties"
        },
        {
            "fruitNum": "9",
            "name": "Mosambi",
            "category": "citrus",
            "type": "citrus",
            "color": "green",
            "price": 70,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/7/7a/%28Citrus_limetta%29_Mosambi_at_a_market_in_Seethammadhara.jpg/250px-%28Citrus_limetta%29_Mosambi_at_a_market_in_Seethammadhara.jpg",
            "healthBenefit": "Rich in vitamin C"
        },
        {
            "fruitNum": "10",
            "name": "Watermelon",
            "category": "neutral",
            "type": "tropical",
            "color": "green",
            "price": 60,
            "currency": "INR",
            "status": "available",
            "image": "https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Watermelon_cross_BNC.jpg/250px-Watermelon_cross_BNC.jpg",
            "healthBenefit": "Hydrating and refreshing"
        }
    ],
    "suppliers": [
        {
            "supplierNum": "1",
            "name": "Fresh Fruits Co.",
            "city": "Mumbai",
            "sinceWhen": 2005,
            "fruits": [
                "Mango",
                "Banana",
                "Papaya"
            ],
            "contactPerson": "Rajesh Kumar",
            "contactEmail": "rajesh@freshfruits.in",
            "contactNumber": 9876543210
        },
        {
            "supplierNum": "2",
            "name": "Citrus World",
            "city": "Nagpur",
            "sinceWhen": 2010,
            "fruits": [
                "Orange",
                "Lemon",
                "Mosambi"
            ],
            "contactPerson": "Anita Deshmukh",
            "contactEmail": "anita@citrusworld.in",
            "contactNumber": 9123456780
        },
        {
            "supplierNum": "3",
            "name": "Himalayan Apples",
            "city": "Shimla",
            "sinceWhen": 1998,
            "fruits": [
                "Apple"
            ],
            "contactPerson": "Vikram Thakur",
            "contactEmail": "vikram@himalayanapples.in",
            "contactNumber": 9988776655
        },
        {
            "supplierNum": "4",
            "name": "Tropical Treats",
            "city": "Chennai",
            "sinceWhen": 2012,
            "fruits": [
                "Guava",
                "Pineapple"
            ],
            "contactPerson": "Meena Iyer",
            "contactEmail": "meena@tropicaltreats.in",
            "contactNumber": 9871234567
        },
        {
            "supplierNum": "5",
            "name": "Fruit Basket",
            "city": "Delhi",
            "sinceWhen": 2008,
            "fruits": [
                "Watermelon",
                "Apple"
            ],
            "contactPerson": "Amit Sharma",
            "contactEmail": "amit@fruitbasket.in",
            "contactNumber": 9812345678
        },
        {
            "supplierNum": "6",
            "name": "Nature's Bounty",
            "city": "Bangalore",
            "sinceWhen": 2015,
            "fruits": [
                "Papaya",
                "Banana"
            ],
            "contactPerson": "Kavita Rao",
            "contactEmail": "kavita@naturesbounty.in",
            "contactNumber": 9845123456
        },
        {
            "supplierNum": "7",
            "name": "Fruit Fiesta",
            "city": "Hyderabad",
            "sinceWhen": 2003,
            "fruits": [
                "Mango",
                "Guava"
            ],
            "contactPerson": "Suresh Reddy",
            "contactEmail": "suresh@fruitfiesta.in",
            "contactNumber": 9876541230
        },
        {
            "supplierNum": "8",
            "name": "Citrus Delight",
            "city": "Pune",
            "sinceWhen": 2011,
            "fruits": [
                "Orange",
                "Mosambi"
            ],
            "contactPerson": "Neha Joshi",
            "contactEmail": "neha@citrusdelight.in",
            "contactNumber": 9823456789
        },
        {
            "supplierNum": "9",
            "name": "Apple Orchard",
            "city": "Manali",
            "sinceWhen": 2000,
            "fruits": [
                "Apple"
            ],
            "contactPerson": "Ravi Negi",
            "contactEmail": "ravi@appleorchard.in",
            "contactNumber": 9876549876
        },
        {
            "supplierNum": "10",
            "name": "Green Farms",
            "city": "Ahmedabad",
            "sinceWhen": 2006,
            "fruits": [
                "Watermelon",
                "Banana"
            ],
            "contactPerson": "Pooja Patel",
            "contactEmail": "pooja@greenfarms.in",
            "contactNumber": 9898989898
        }
    ],
    "cities": [
        {
            "cityNum": "1",
            "name": "Mumbai",
            "population": 20411000,
            "state": "Maharashtra",
            "famousFor": "Mango"
        },
        {
            "cityNum": "2",
            "name": "Nagpur",
            "population": 2405665,
            "state": "Maharashtra",
            "famousFor": "Orange"
        },
        {
            "cityNum": "3",
            "name": "Shimla",
            "population": 169578,
            "state": "Himachal Pradesh",
            "famousFor": "Apple"
        },
        {
            "cityNum": "4",
            "name": "Chennai",
            "population": 10921804,
            "state": "Tamil Nadu",
            "famousFor": "Guava"
        },
        {
            "cityNum": "5",
            "name": "Delhi",
            "population": 31870000,
            "state": "Delhi",
            "famousFor": "Watermelon"
        },
        {
            "cityNum": "6",
            "name": "Bangalore",
            "population": 12700000,
            "state": "Karnataka",
            "famousFor": "Papaya"
        },
        {
            "cityNum": "7",
            "name": "Hyderabad",
            "population": 10000000,
            "state": "Telangana",
            "famousFor": "Mango"
        },
        {
            "cityNum": "8",
            "name": "Pune",
            "population": 6800000,
            "state": "Maharashtra",
            "famousFor": "Mosambi"
        },
        {
            "cityNum": "9",
            "name": "Manali",
            "population": 8000,
            "state": "Himachal Pradesh",
            "famousFor": "Apple"
        },
        {
            "cityNum": "10",
            "name": "Ahmedabad",
            "population": 8200000,
            "state": "Gujarat",
            "famousFor": "Banana"
        }
    ]
}

```


## Manifest.json

https://sapui5.hana.ondemand.com/#/topic/be0cf40f61184b358b5faedaec98b2da

<img width="1206" height="625" alt="image" src="https://github.com/user-attachments/assets/dff7c68a-291b-4abd-b798-cc9f52ed0963" />


<img width="1872" height="966" alt="image" src="https://github.com/user-attachments/assets/6f0573f2-c696-4b8b-a86e-69f8ee397bdd" />



<img width="1513" height="813" alt="image" src="https://github.com/user-attachments/assets/c4182aa6-8b29-4816-ad8a-18fbd454968e" />


<img width="1913" height="890" alt="image" src="https://github.com/user-attachments/assets/d8c7f107-d375-471f-826c-a155b71690f2" />


## Perform deletion of items in UI 

``` XML
 <List id="idList" items="{/fruits}" mode="Delete" delete="onDeleteItem">
                <items>
                    <!-- relative bindings in child items -->
                    <ObjectListItem title="{name}" intro="{type}" number="{price}" numberUnit="{currency}" icon="{image}" id="idListItem"></ObjectListItem>
                </items>
            </List>

```


``` JS
                onDeleteItem: function (oEvent) {

                    // on which event the delete was pressed..
                    var oItem = oEvent.getParameter("listItem"); // correct parameter name

                    // get object of the list conbtrol
                    var oList = oEvent.getSource();

                    // delete the item 
                    oList.removeItem(oItem);
                }


```


## Search operation in view 1

<img width="1763" height="817" alt="image" src="https://github.com/user-attachments/assets/9d9658f4-4114-4dc2-8a7f-118227f82267" />

view1.xml
``` xml
<mvc:View xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.View1">
    <!-- Put APP container control( contains other controls ) -->
    <Page title="First View" >
        <content>
            <!-- <Button text="Next Page" press="onNext"></Button> -->
            <SearchField id="idSearch" search="onSearch"></SearchField>
            <!-- {/fruits} - is absolute path in aggregation binding..! -->
            <List id="idList" items="{/fruits}" mode="Delete" delete="onDeleteItem">
                <items>
                    <!-- relative bindings in child items -->
                    <ObjectListItem title="{name}" intro="{type}" number="{price}" numberUnit="{currency}" icon="{image}" id="idListItem">
                        <firstStatus>
                            <ObjectStatus text="{status}" state="{ path: 'status' , formatter: '.formatter.getStatusState' }"></ObjectStatus>
                        </firstStatus>
                    </ObjectListItem>
                </items>
            </List>
        </content>
        <headerContent>
            <Button icon="sap-icon://initiative" press="onNext" tooltip="Navigate to next sceen"></Button>
        </headerContent>
    </Page>
</mvc:View>

```

## view1.controller.js
``` js
//scaffolding
sap.ui.define(

    [
        'com/plansee/coc/bc/controller/BaseController',
        'sap/m/MessageBox',
        'sap/ui/model/Filter',
        'sap/ui/model/FilterOperator',
        'com/plansee/coc/bc/util/formatter'
    ], function (Controller, MessageBox, Filter, FilterOperator, formatter) {
        'use strict';
        return Controller.extend("com.plansee.coc.bc.controller.View1",
            {
                formatter: formatter,
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

                },

                onItemPress: function () {
                    MessageBox.information(" Thanks for placing the order");
                },

                onDeleteItem: function (oEvent) {

                    // on which event the delete was pressed..
                    var oItem = oEvent.getParameter("listItem"); // correct parameter name

                    // get object of the list conbtrol
                    var oList = oEvent.getSource();

                    // delete the item 
                    oList.removeItem(oItem);
                },

                onSearch: function (oEvent) {
                    // read the search value from the UI.
                    var sSearchText = oEvent.getParameter("query");
                    //CONSTRUCT A FILter object ( like an IF condition with operand and operator)
                    var oFilter1 = new Filter("name", FilterOperator.Contains, sSearchText);
                    var oFilter2 = new Filter("type", FilterOperator.Contains, sSearchText);


                    // array of filters
                    var aFilter = [oFilter1, oFilter2];

                    // construction of a OR filter ( either of condition should be true)
                    var oFilter = new Filter({
                        filters: aFilter,
                        and: false
                    })
                    // inject the filter object inside the list binding
                    var oList = this.getView().byId("idList");
                    oList.getBinding("items").filter(oFilter);

                }
            }
        )
    });


```

## formatter
``` js

sap.ui.define([

], function () {
    'use strict';
    return {
        getStatusState: function (inp) {
            switch (inp) {
                case 'available':
                    return 'Success';
                    break;

                case 'Out of stock':
                    return 'Warning';
                    break;

                case 'Discontinued':
                    return 'Error';
                    break;

                default:
                    break;
            }
        }
    }

});

```

# Worklist FIORI App

<img width="1193" height="625" alt="image" src="https://github.com/user-attachments/assets/72c4e051-29dd-4a14-9b9e-6d9871d4e526" />

<img width="1083" height="195" alt="image" src="https://github.com/user-attachments/assets/cee17d61-c3ac-4da4-9e4a-45f4b6b165f7" />


<img width="695" height="236" alt="image" src="https://github.com/user-attachments/assets/9091aded-dfce-473e-8fe4-d677824b75c4" />

## view 1

``` xml
<mvc:View xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.View1">
    <!-- Put APP container control( contains other controls ) -->
    <Page title="First View" id="idView1">
        <content>
            <!-- <Button text="Next Page" press="onNext"></Button> -->
            <SearchField id="idSearch" search="onSearch"></SearchField>
            <!-- {/fruits} - is absolute path in aggregation binding..! -->
            <List id="idList" items="{/fruits}" mode="SingleSelectMaster" selectionChange="onSelectionChange">
                <items>
                    <!-- relative bindings in child items -->
                    <ObjectListItem title="{name}" intro="{type}" number="{price}" numberUnit="{currency}" icon="{image}" id="idListItem">
                        <firstStatus>
                            <ObjectStatus text="{status}" state="{ path: 'status' , formatter: '.formatter.getStatusState' }"></ObjectStatus>
                        </firstStatus>
                    </ObjectListItem>
                </items>
            </List>
        </content>
        <headerContent>
            <Button icon="sap-icon://initiative" press="onNext" tooltip="Navigate to next sceen"></Button>
        </headerContent>
    </Page>
</mvc:View>

```


## view 2

``` xml

<mvc:View xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.View2">
    <!-- Put APP container control( contains other controls ) -->
    <Page title="Second View" showNavButton="true" navButtonPress="onBack" id="idView2" >
        <content >
            <!-- <Button text="Back" press="onBack"></Button> -->
            <ObjectHeader title="{name}" intro="{healthBenefit}" number="{price}" numberUnit="{currency}" icon="{image}">
            </ObjectHeader>
        </content>
        <headerContent>
            <!-- <Button icon="sap-icon://nav-back" press="onBack" tooltip="Navigate to last sceen"></Button> -->
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


## controller1

``` js

//scaffolding
sap.ui.define(

    [
        'com/plansee/coc/bc/controller/BaseController',
        'sap/m/MessageBox',
        'sap/ui/model/Filter',
        'sap/ui/model/FilterOperator',
        'com/plansee/coc/bc/util/formatter'
    ], function (Controller, MessageBox, Filter, FilterOperator, formatter) {
        'use strict';
        return Controller.extend("com.plansee.coc.bc.controller.View1",
            {
                formatter: formatter,
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

                },

                onItemPress: function () {
                    MessageBox.information(" Thanks for placing the order");
                },

                onDeleteItem: function (oEvent) {

                    // on which event the delete was pressed..
                    var oItem = oEvent.getParameter("listItem"); // correct parameter name

                    // get object of the list conbtrol
                    var oList = oEvent.getSource();

                    // delete the item 
                    oList.removeItem(oItem);
                },

                onSearch: function (oEvent) {
                    // read the search value from the UI.
                    var sSearchText = oEvent.getParameter("query");
                    //CONSTRUCT A FILter object ( like an IF condition with operand and operator)
                    var oFilter1 = new Filter("name", FilterOperator.Contains, sSearchText);
                    var oFilter2 = new Filter("type", FilterOperator.Contains, sSearchText);


                    // array of filters
                    var aFilter = [oFilter1, oFilter2];

                    // construction of a OR filter ( either of condition should be true)
                    var oFilter = new Filter({
                        filters: aFilter,
                        and: false
                    })
                    // inject the filter object inside the list binding
                    var oList = this.getView().byId("idList");
                    oList.getBinding("items").filter(oFilter);

                },

                onSelectionChange: function (oEvent) {

                    // get object of which item user selected in VIEW 1 ?
                    var oSelectedItem = oEvent.getParameter("listItem");
                    // get the address of the selected item
                    var sPath = oSelectedItem.getBindingContextPath();
                    // Bind the whole of 2nd view with this Path
                    /// get obj of view 2 and get page.
                    var oView2 = this.getView().getParent().getPage("idView2");
                    /// perform the element Binding with VIew 2
                    oView2.bindElement(sPath);

                    // call next VIEW 2:
                    this.onNext();

                }
            }
        )
    });
```

## Output :

### View 1

<img width="1150" height="641" alt="image" src="https://github.com/user-attachments/assets/ef03e859-3f0f-4d84-b49d-bff4905824cf" />

<img width="1174" height="947" alt="image" src="https://github.com/user-attachments/assets/c736ae61-677b-4980-b4e1-d910f167663a" />







