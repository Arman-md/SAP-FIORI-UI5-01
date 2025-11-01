#  List Control

<img width="1180" height="629" alt="image" src="https://github.com/user-attachments/assets/36d110aa-db71-407c-bfe9-4f5bbfc6b1fc" />


## How to adjust padding / margin ( CSS- BOX Model)



<img width="1752" height="910" alt="image" src="https://github.com/user-attachments/assets/0e16cfbe-cef4-4816-ac00-47b26e94a17f" />

https://sapui5.hana.ondemand.com/#/topic/777168ffe8324873973151dae2356d1c

https://sapui5.hana.ondemand.com/#/topic/c71f6df62dae47ca8284310a6f5fc80a

ex:

``` xml
 <Label class='sapUiSmallMarginTop' text="how many cherries you would like to order today?"></Label>

```


### before

<img width="662" height="80" alt="image" src="https://github.com/user-attachments/assets/79b6cdda-430d-4737-b8f5-dd3c26d95c7a" />

### after

<img width="613" height="68" alt="image" src="https://github.com/user-attachments/assets/e059833f-f097-4ead-8e5a-d98e9ddc660b" />



# List control cont..


<img width="1179" height="339" alt="image" src="https://github.com/user-attachments/assets/b6fbd917-7d67-4747-85b3-ff1234dbe8a9" />

``` xml

            <List id="idList">
                <items>
                    <!-- for simple usage -->
                    <DisplayListItem label="Apple" value="The best antibiotic"></DisplayListItem>
                    <!-- display data along with icon in verticl format  -->
                    <StandardListItem title="PineApple" description="Good for glowing skin" 
                    icon="https://www.aishcart.in/3302/sweet-mini-pineapple-gift-box-3kg.jpg" ></StandardListItem>
                    <!-- list with input data -> input list item ( user can change data with multiple values) -->
                    <InputListItem >
                        <content>
                            <HBox >
                                <Label class='sapUiSmallMarginTop' text="how many cherries you would like to order today?"></Label>
                                <Input type="Number" width="150%" class='sapUiTinyMarginBegin' ></Input>
                            </HBox>
                        </content>
                    </InputListItem>
                    <!-- Custom List item -->
                    <CustomListItem >
                        <content>
                            <HBox >
                                <Image src="https://www.aishcart.in/5828-large_default/litchi-fruit-box-10kg.jpg" width="30%"></Image>
                                <VBox >
                                    <Text text="Do you recognize this fruit?"></Text>
                                    <Switch ></Switch>
                                </VBox>
                            </HBox>
                        </content>
                    </CustomListItem>
                    <!-- Object List item -> used to display a business object in EX: SAP Material, sales order, amount+unit, etc-->
                    <ObjectListItem title="Banana" intro="A good source of potassium" number="80" numberUnit="Per KG" icon="https://thumbs.dreamstime.com/b/banana-close-up-isolated-white-31151806.jpg" >
                        <attributes>
                            <ObjectAttribute title="Color" text="Green Yellow" />
                            <ObjectAttribute title="Season" text="Summer" />
                        </attributes>
                        <firstStatus>
                            <ObjectStatus text="available" state="Success">

                        </ObjectStatus>
                        </firstStatus>
                    </ObjectListItem>
                    <!-- feed List item used to design a social media like - feeds -->
                    <FeedListItem icon="https://upload.wikimedia.org/wikipedia/commons/thumb/6/68/Joe_Biden_presidential_portrait.jpg/250px-Joe_Biden_presidential_portrait.jpg" text="Hey how is it going?" sender="Joe Biden" timestamp="today morning"></FeedListItem>
                    <!-- Action list item : used to show a clickable action  -->
                    <ActionListItem text="Order Now!" press="onItemPress"></ActionListItem>
                </items>
            </List>

```

<img width="1913" height="762" alt="image" src="https://github.com/user-attachments/assets/3f50e59e-7f25-40fb-87d6-756bfd6d4ce3" />

<img width="730" height="785" alt="image" src="https://github.com/user-attachments/assets/641c3a7f-c438-4285-824a-4713ba70655e" />



