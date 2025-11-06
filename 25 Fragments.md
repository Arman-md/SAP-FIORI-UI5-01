
# 

<img width="632" height="258" alt="image" src="https://github.com/user-attachments/assets/d2b90c07-b193-4ed9-a625-5ab10b5cc26e" />

# Fragments

<img width="656" height="364" alt="image" src="https://github.com/user-attachments/assets/3e1c21eb-551a-4f9e-9797-b9ec2614f6da" />


<img width="627" height="135" alt="image" src="https://github.com/user-attachments/assets/f3eaa1c7-64d8-4c2d-920f-80d6f5fbef67" />

<img width="609" height="345" alt="image" src="https://github.com/user-attachments/assets/804fd4ce-1a7f-4472-9ad5-cb2bde4c5742" />
## Static fragments :

<img width="1866" height="781" alt="image" src="https://github.com/user-attachments/assets/a29564e6-0c41-43c9-9c1e-dc55cef5eb27" />



``` xml

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m" xmlns:f="sap.ui.layout.form">
    <f:SimpleForm>
        <f:content>
            <Label text="Name"></Label>
            <Text text="{name}"></Text>
            <Label text="Color"></Label>
            <Text text="{color}"></Text>
            <Label text="Price"></Label>
            <Text text="{price} {currency}"></Text>
            <Label text="Status"></Label>
            <Text text="{status}"></Text>
        </f:content>
    </f:SimpleForm>
</core:FragmentDefinition>


<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m" >
    <Table id="idSupplierTable" items="{/suppliers}" itemPress="onSupplierItem">
        <columns>
            <Column >
                <header>
                    <Text text="Supplier Name"></Text>
                </header>
            </Column>
            <Column >
                <header>
                    <Text text="City"></Text>
                </header>
            </Column>
            <Column minScreenWidth="Tablet" demandPopin="true">
                <header>
                    <Text text="Contact Details" ></Text>
                </header>
            </Column>
            <Column minScreenWidth="Tablet">
                <header>
                    <Text text="Since When"></Text>
                </header>
            </Column>
        </columns>
        <items>
            <ColumnListItem type="Navigation" >
                <cells>
                    <Text text="{name}"></Text>
                    <Input value="{city}"></Input>
                    <Text text="{contactEmail}" ></Text>
                    <Text text="{sinceWhen}"></Text>
                </cells>
            </ColumnListItem>
        </items>
    </Table>
</core:FragmentDefinition>



<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m">
    <Select items="{/cities}">
        <core:Item key="{name}" text="{name}"> </core:Item>
    </Select>
    <ComboBox items="{/cities}">
        <core:Item key="{name}" text="{name}"> </core:Item>
    </ComboBox>
    <MultiComboBox items="{/cities}">
        <core:Item key="{name}" text="{name}"> </core:Item>
    </MultiComboBox>
</core:FragmentDefinition>





```


## Dynamic Fragments


<img width="1175" height="638" alt="image" src="https://github.com/user-attachments/assets/f80ae2d5-cfa6-4ae2-894e-ccc7b9b528ee" />


<img width="609" height="345" alt="image" src="https://github.com/user-attachments/assets/a31e8497-428c-4a2b-a494-1a50cd034286" />

   
# filter button :

``` xml
<headerToolbar>
            <Toolbar >
                <ToolbarSpacer />
                <Button icon="sap-icon://filter" tooltip="Open Supplier Filter" press="onFilter"></Button>
            </Toolbar>
        </headerToolbar>

```



# value help for input field





``` xml   <Input value="{city}" showValueHelp="true" valueHelpRequest="onF4Help"></Input> ```

<img width="1628" height="907" alt="image" src="https://github.com/user-attachments/assets/1916e7d1-b3eb-4f06-839b-546cbe5fc625" />

<img width="1625" height="654" alt="image" src="https://github.com/user-attachments/assets/7a3f5354-ea06-45dc-b377-325e528438b4" />


## output ( just a skeleton)

<img width="1624" height="523" alt="image" src="https://github.com/user-attachments/assets/0efc724f-aeb9-4601-af70-c9176ff265a9" />



### POP UP -> SELECT DIALOG CONTROL IN SDK ( SEARCH AND READ )





## view2.controller.js

``` js

//scaffolding
sap.ui.define(

    [
        'com/plansee/coc/bc/controller/BaseController',
        'sap/m/MessageBox',
        'sap/m/MessageToast',
        'sap/ui/core/Fragment',
        'sap/ui/model/Filter',
        'sap/ui/model/FilterOperator'
    ], function (Controller, MessageBox, MessageToast, Fragment, Filter, FilterOperator) {
        'use strict';
        return Controller.extend("com.plansee.coc.bc.controller.View2",
            {
                onInit: function () {

                    // alert("now we have the app contorller for fiori like app");

                    // step 1 get the router object

                    this.oRouter = this.getOwnerComponent().getRouter();

                    // step 2 attach route handler which triggers our code, everytime route chnages
                    this.oRouter.getRoute("superman").attachMatched(this.herculis, this);
                },

                herculis: function (oEvent) {
                    // everytime root changes, this event is triggered..!

                    // reconstruction of the path of the fruit
                    var sPath = '/fruits/' + oEvent.getParameter("arguments").fruitNum;

                    // set this to binding
                    this.getView().bindElement(sPath);


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
                },

                onSupplierItem: function (oEvent) {
                    var oSelectedItem = oEvent.getParameter("listItem");
                    var sPath = oSelectedItem.getBindingContextPath();
                },

                onConfirmPopup: function (oEvent) {
                    var sId = oEvent.getSource().getId();
                    if (sId.indexOf("city") !== -1) {
                        // step 1 
                        var oSelectedItem = oEvent.getParameter("selectedItem");
                        // get label of selected item
                        var sText = oSelectedItem.getLabel();
                        // set this value to field in table
                        this.ofield.setValue(sText);
                    } else {
                        // because of supplier pop up
                        // step 1 
                        var oSelectedItem = oEvent.getParameter("selectedItem");
                        // get label of selected item
                        var sText = oSelectedItem.getTitle();
                        // Filter our table based on selected item
                        // get table object
                        var oTable = this.getView().byId("idSupplierTable");

                        // construct a filter
                        var oFilter = new Filter("name", FilterOperator.EQ, sText);

                        // inject
                        oTable.getBinding("items").filter(oFilter);
                    }

                },

                // create object of city pop up
                oCityPopUp: null,
                ofield: null,
                onF4Help: function (oEvent) {
                    // MessageBox.confirm("This functionality is under development");
                    this.ofield = oEvent.getSource();
                    var that = this;
                    if (!this.oCityPopUp) {
                        Fragment.load({
                            name: 'com.plansee.coc.bc.fragments.popup',
                            id: 'city',
                            controller: this
                        }).then((oFragment) => {
                            that.oCityPopUp = oFragment;
                            that.oCityPopUp.open();

                            that.getView().addDependent(that.oCityPopUp);
                            that.oCityPopUp.setTitle("Choose city(s)");
                            that.oCityPopUp.bindAggregation("items", {
                                path: '/cities',
                                template: new sap.m.DisplayListItem({
                                    label: '{name}',
                                    value: '{famousFor}'

                                })
                            })
                        })
                    } else {
                        this.oCityPopUp.open();
                    }

                },
                // a global variable to avoid creating fragment object again and again

                oSupplierPopup: null,
                onFilter: function () {
                    // if global var is not there, then only create else dont..!
                    if (!this.oSupplierPopup) {

                        //MessageBox.confirm("This functionality is under development");
                        // create a new fragment object
                        Fragment.load({
                            name: 'com.plansee.coc.bc.fragments.popup',
                            id: 'supplier',
                            controller: this

                            // then is a promise function which is predefined in JS
                        }).then((oFragment) => {
                            // SET THE GLOBAL VARIABLE:
                            this.oSupplierPopup = oFragment;

                            // set a title
                            this.oSupplierPopup.setTitle("Choose a supplier");
                            // allow fragment to access modell data
                            this.getView().addDependent(this.oSupplierPopup);

                            // BELOW IS a CALLBACK function where we open our fragment
                            this.oSupplierPopup.open();
                            this.oSupplierPopup.bindAggregation("items", {
                                path: '/suppliers',
                                template: new sap.m.StandardListItem({
                                    icon: 'sap-icon://supplier',
                                    title: '{name}',
                                    description: '{city}'
                                })
                            })
                        });
                    } else {
                        this.oSupplierPopup.open();
                    }

                }
            }
        )
    });

```

## view 2.xml


``` xml

<mvc:View xmlns:internal="sap.landvisz.internal" xmlns:mvc="sap.ui.core.mvc" xmlns="sap.m" controllerName="com.plansee.coc.bc.controller.View2" 
xmlns:f="sap.ui.layout.form" 
xmlns:core="sap.ui.core">
    <!-- Put APP container control( contains other controls ) -->
    <Page title="Detailed View" showNavButton="true" navButtonPress="onBack" id="idView2" >
        <content >
            <!-- <Button text="Back" press="onBack"></Button> -->
            <ObjectHeader title="{name}" intro="{healthBenefit}" number="{price}" numberUnit="{currency}" icon="{image}">
            </ObjectHeader>
            <IconTabBar >
                <items>
                    <IconTabFilter icon="sap-icon://warning" text="More Info">
                        <core:Fragment fragmentName="com.plansee.coc.bc.fragments.moreinfo" type="XML"/>
                    </IconTabFilter>
                    <IconTabFilter icon="sap-icon://supplier" text="Suppliers">
                        <core:Fragment fragmentName="com.plansee.coc.bc.fragments.suppliers" type="XML"/>
                    </IconTabFilter>
                    <IconTabFilter icon="sap-icon://map" text="Cities">
                        <core:Fragment fragmentName="com.plansee.coc.bc.fragments.cities" type="XML"/>
                    </IconTabFilter>
                </items>
            </IconTabBar>
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


## cities.fragment.xml

``` xml

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m">
    <Select items="{/cities}">
        <core:Item key="{name}" text="{name}"> </core:Item>
    </Select>
    <ComboBox items="{/cities}">
        <core:Item key="{name}" text="{name}"> </core:Item>
    </ComboBox>
    <MultiComboBox items="{/cities}">
        <core:Item key="{name}" text="{name}"> </core:Item>
    </MultiComboBox>
</core:FragmentDefinition>
```


## suppliers.fragment.xml

``` xml

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m" >
    <Table id="idSupplierTable" items="{/suppliers}" itemPress="onSupplierItem">
        <headerToolbar>
            <Toolbar >
                <ToolbarSpacer />
                <Button icon="sap-icon://filter" tooltip="Open Supplier Filter" press="onFilter"></Button>
            </Toolbar>
        </headerToolbar>
        <columns>
            <Column >
                <header>
                    <Text text="Supplier Name"></Text>
                </header>
            </Column>
            <Column >
                <header>
                    <Text text="City"></Text>
                </header>
            </Column>
            <Column minScreenWidth="Tablet" demandPopin="true">
                <header>
                    <Text text="Contact Details" ></Text>
                </header>
            </Column>
            <Column minScreenWidth="Tablet">
                <header>
                    <Text text="Since When"></Text>
                </header>
            </Column>
        </columns>
        <items>
            <ColumnListItem type="Navigation" >
                <cells>
                    <Text text="{name}"></Text>
                    <Input value="{city}" showValueHelp="true" valueHelpRequest="onF4Help"></Input>
                    <Text text="{contactEmail}" ></Text>
                    <Text text="{sinceWhen}"></Text>
                </cells>
            </ColumnListItem>
        </items>
    </Table>
</core:FragmentDefinition>

```


## popup.fragments.xml


``` xml

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m">
    <SelectDialog id="popup" confirm="onConfirmPopup">
</SelectDialog>
</core:FragmentDefinition>

```


## Output

### we can filter based on cities :

<img width="1804" height="888" alt="image" src="https://github.com/user-attachments/assets/65a00eb1-8bf7-46e3-bd85-6b636b1779e4" />

### filter based on supplier


<img width="1918" height="980" alt="image" src="https://github.com/user-attachments/assets/1794fb6b-3448-4615-8ede-8e9f7e1832ca" />


<img width="1916" height="687" alt="image" src="https://github.com/user-attachments/assets/f7847d9d-d9e2-4489-8b50-f37881f797fe" />



<img width="526" height="121" alt="image" src="https://github.com/user-attachments/assets/0ac9c262-e346-469a-a4db-cf1ca0dd32c8" />
