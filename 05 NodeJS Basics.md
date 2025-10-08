# NODE JS

## -> ITS A FRAMEWORK TO Execute JS outside browser( because we dont want to learn server side languages like java or python 

## -> utilize the power of asynchronous non blocking io

## nodeJS is a powerful framework with great speed

## many already done modules will be available 

## node offeres - node package manages ( npm ) world's largest code repository)

## 

<img width="1145" height="643" alt="image" src="https://github.com/user-attachments/assets/4d190e89-cf56-427d-b87b-166ba6ba19d9" />

## node modules

### https://www.npmjs.com/

### we create our own modules ex:

``` js
// node js practice :
// json file java script objects
// the below is a json 
module.exports = {
    printArray: function (arr) {
        for (let index = 0; index < arr.length; index++) {
            const element = arr[index];
            console.log(element);

        }
    },

    printArrCount: function (arr) {
        console.log(arr.length);

    },

    calculator: function (opr1, opr2, ope) {
        switch (ope) {
            case '+':
                return opr1 + opr2;
                break;
            case '-':
                return opr1 - opr2;
                break;
            case '*':
                return opr1 * opr2;
                break;
            case '/':
                return opr1 / opr2;
                break;
            default:
                break;
        }
    }

}

```

``` js

// we link index.js and reuse.js and bring all here in reuse object



const reuse = require('./util/reuse');
var oReuse = require('./util/reuse');

console.log(oReuse.calculator(2, 5, '*'));

var arrVal = ["apple", "banana", "cherry"];
reuse.printArray(arrVal);


```


output :

<img width="688" height="257" alt="image" src="https://github.com/user-attachments/assets/c1712b9e-9522-4fed-83a0-d5cb4d67b954" />


## reuse.js
<img width="1826" height="940" alt="image" src="https://github.com/user-attachments/assets/4e050427-3e61-45c0-8e16-148ae2b8d4aa" />


## index.js
<img width="1466" height="448" alt="image" src="https://github.com/user-attachments/assets/55a7225a-68cf-46bb-9c01-0c39d856bc35" />


### working with global NPM Modules ( reusing npm modules )

#### creating server

# npm express :

``` https://www.npmjs.com/package/express?activeTab=readme ```

install node modules

#### run 'npm install express'( to install express modules )



<img width="1686" height="921" alt="image" src="https://github.com/user-attachments/assets/6b828108-f0f7-4412-8bce-b48859e476b9" />


``` js
// consuming a npm node module express
var express = require('express');

//import express from 'express'

// create our first node app
const app = express();

// implement our server side event
app.get('/', (req, res) => {
    res.send('Hello Arman2')
})

//
//console.log("server is running now in local host 3000");
// serve via port


app.listen(3001, () => {
    console.log("Server is running on http://localhost:3001");
});

```

## Micro service ( service inside a service with use of endpoints )

## CREATING Endpoints ex: EMPLOYEES

<img width="613" height="200" alt="image" src="https://github.com/user-attachments/assets/539d1371-51fe-4960-b495-221b11ebced7" />


## updates JS with endpoint /employees and retaed JSON Data

``` js
// consuming a npm node module express
var express = require('express');

//import express from 'express'

// create our first node app
const app = express();

// implement our server side event
app.get('/', (req, res) => {
    res.send('Hello Arman2')
});

app.get('/employees', function (req, res) {
    res.send([
        {
            "ID": "E001",
            "Name": "Alice Johnson",
            "Department": "Human Resources",
            "Designation": "HR Manager",
            "Email": "alice.johnson@example.com",
            "Phone": "+1-555-123-4567"
        },
        {
            "ID": "E002",
            "Name": "Bob Smith",
            "Department": "Engineering",
            "Designation": "Software Engineer",
            "Email": "bob.smith@example.com",
            "Phone": "+1-555-234-5678"
        },
        {
            "ID": "E003",
            "Name": "Carol Williams",
            "Department": "Marketing",
            "Designation": "Marketing Specialist",
            "Email": "carol.williams@example.com",
            "Phone": "+1-555-345-6789"
        }
    ]);

});
//
//console.log("server is running now in local host 3000");
// serve via port


app.listen(3001, () => {
    console.log("Server is running on http://localhost:3001");
});


```

## sending file to server

``` js

// sending file back
app.get('/file', function (req, res) {
    res.sendFile(__dirname + '/webapp/file.txt');
})
//
```


### result :

<img width="450" height="161" alt="image" src="https://github.com/user-attachments/assets/3035cf41-5a86-4961-bdfb-a806b8d380e9" />



## Result output 

<img width="996" height="829" alt="image" src="https://github.com/user-attachments/assets/cb9bcebe-a134-40c4-a51e-8002cf705f09" />


``` js
// with middle wares

// consuming a npm node module express
var express = require('express');

//import express from 'express'

// create our first node app
const app = express();

// we can make use of middlewares to send bulk files
// like whole directory can be sent ( folder containing files )
app.use(express.static('webapp'));

// implement our server side event
app.get('/', (req, res) => {
    res.send('Hello Arman2')
});


// endpoint handling code
app.get('/employees', function (req, res) {
    res.send([
        {
            "ID": "E001",
            "Name": "Alice Johnson",
            "Department": "Human Resources",
            "Designation": "HR Manager",
            "Email": "alice.johnson@example.com",
            "Phone": "+1-555-123-4567"
        },
        {
            "ID": "E002",
            "Name": "Bob Smith",
            "Department": "Engineering",
            "Designation": "Software Engineer",
            "Email": "bob.smith@example.com",
            "Phone": "+1-555-234-5678"
        },
        {
            "ID": "E003",
            "Name": "Carol Williams",
            "Department": "Marketing",
            "Designation": "Marketing Specialist",
            "Email": "carol.williams@example.com",
            "Phone": "+1-555-345-6789"
        }
    ]);

});

// sending file back
app.get('/file', function (req, res) {
    res.sendFile(__dirname + '/webapp/file.txt');
})
//

// serve via port
app.listen(3001, () => {
    console.log("Server is running on http://localhost:3001");
});


```

<img width="1172" height="650" alt="image" src="https://github.com/user-attachments/assets/cba5b67b-1b72-4516-83a7-3e70d4b081b6" />



<img width="1160" height="513" alt="image" src="https://github.com/user-attachments/assets/3c41aac2-e8b1-4d3e-8b7a-b192e824d081" />






