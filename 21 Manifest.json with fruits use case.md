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




