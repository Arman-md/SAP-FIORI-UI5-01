# Icon Tab Bar

<img width="1650" height="768" alt="image" src="https://github.com/user-attachments/assets/b36cbef0-f7b2-4bfc-96ab-3806d2428374" />

``` XML

            <IconTabBar >
                <items>
                    <IconTabFilter icon="sap-icon://warning" text="More Info">
                        <f:SimpleForm>
                            <f:content>
                                <Label text="Name"></Label>
                                <Text text="{name}"></Text>
                                <Label text="Color"></Label>
                                <Text text="{color}"></Text>
                                <Label text="Price"></Label>
                                <Text text="{price}"></Text>
                                <Label text="Status"></Label>
                                <Text text="{status}"></Text>
                            </f:content>
                        </f:SimpleForm>
                    </IconTabFilter>
                    <IconTabFilter icon="sap-icon://supplier" text="Suppliers">
                        <Table ></Table>
                    </IconTabFilter>
                    <IconTabFilter icon="sap-icon://map" text="Cities">
                        <Select items="{/cities}">
                            <core:Item key="{name}" text="{name}"> </core:Item>
                        </Select>
                        <ComboBox items="{/cities}">
                            <core:Item key="{name}" text="{name}"> </core:Item>
                        </ComboBox>
                        <MultiComboBox items="{/cities}">
                            <core:Item key="{name}" text="{name}"> </core:Item>
                        </MultiComboBox>
                    </IconTabFilter>
                </items>
            </IconTabBar>

```


<img width="1877" height="926" alt="image" src="https://github.com/user-attachments/assets/b289d40f-52ce-4ab4-a2c0-832e0e900163" />



