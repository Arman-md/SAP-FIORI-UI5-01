# JS

<img width="1198" height="644" alt="image" src="https://github.com/user-attachments/assets/f4f4f7e9-cbb5-4440-9417-dfeab7de588d" />


<img width="1199" height="372" alt="image" src="https://github.com/user-attachments/assets/c545f8a5-55f6-4f23-9fb5-3930b0479eeb" />


<img width="1200" height="543" alt="image" src="https://github.com/user-attachments/assets/d62e0e6c-a04d-4d83-b216-3a8262fa5111" />


<img width="1097" height="178" alt="image" src="https://github.com/user-attachments/assets/c444fb9b-d769-4728-8323-f96d88846d40" />

<img width="1243" height="637" alt="image" src="https://github.com/user-attachments/assets/75b14566-06ec-4d23-98dc-ebe0ba281982" />


<img width="1165" height="618" alt="image" src="https://github.com/user-attachments/assets/0f8a54c4-ae8b-426e-a196-bd394d3f88dd" />

# DOCUMENT IS THE OBJECT OF DOOOOOM

## We can use it to access DOM

``` html

<html>

<head>
    <script>
        // internal JS
        function showText1() {
            alert("Welcome to JS1");
        }

        function showText2() {
            alert("Welcome to JS2");
            document.write('<h2> Welcome to JS2 </h2>');// replaces whole dom and writes
        }
        function onLogin() {
            // get object of DOM for respective ids
            var oUser = document.getElementById("user");
            var oPwd = document.getElementById("pwd");
            // get strings ( user name and password ) in a string
            var sUser = oUser.value;
            var sPwd = oPwd.value;
            if (sUser == sPwd) {
                alert("Dont enter same user name and password...!");
            } else {
                document.write('<h2> Login Successful..! </h2>');// replaces whole dom and writes 
            };
        }
    </script>
</head>

<body>
    <table>
        <tr>
            <td><label>User Id </label> </td>
            <td><input id="user"> </td>
        </tr>
        <tr>
            <td> <label>password</label></td>
            <td> <input id="pwd" type="password"></td>
        </tr>
        <tr>
            <td> </td>
            <td> </td>
        </tr>
    </table>
    <button onclick="onLogin()">login</button>
    <button onclick="showText2()">Click Me2</button>
</body>

</html>

```
<img width="1914" height="353" alt="image" src="https://github.com/user-attachments/assets/1387164f-40d5-4107-885a-bde3240ac36b" />


``` html
<html>

<head>
    <script>
        // internal JS
        function showText1() {
            alert("Welcome to JS1");
        }

        function showText2() {
            alert("Welcome to JS2");
            document.write('<h2> Welcome to JS2 </h2>');// replaces whole dom and writes
        }
        function onLogin() {
            // get object of DOM for respective ids
            var oUser = document.getElementById("user");
            var oPwd = document.getElementById("pwd");
            // get strings ( user name and password ) in a string
            var sUser = oUser.value;
            var sPwd = oPwd.value;
            if (sUser == sPwd) {
                alert("Dont enter same user name and password...!");
            } else {
                document.write('<h2> Login Successful..! </h2>');// replaces whole dom and writes 
            };
        }
    </script>
</head>

<body>
    <table>
        <tr>
            <td><label>User Id </label> </td>
            <td><input id="user"> </td>
        </tr>
        <tr>
            <td> <label>password</label></td>
            <td> <input id="pwd" type="password"></td>
        </tr>
        <tr>
            <td> </td>
            <td> </td>
        </tr>
    </table>
    <button onclick="onLogin()">login</button>
    <button onclick="showText2()">Click Me2</button>
</body>

</html>

```
# debugging in console/ chrome :


<img width="1932" height="755" alt="image" src="https://github.com/user-attachments/assets/7f7b5316-fc71-4f13-bce2-b9b4f3c8ac2f" />


# asynchronous non blocking io


## 🚦 Imagine a Traffic Signal System
### Think of JavaScript as a traffic cop managing cars (tasks) at an intersection.

### Synchronous blocking I/O is like letting one car go at a time, and everyone else has to wait until it's done.

### Asynchronous non-blocking I/O is like having multiple lanes and smart signals that let cars go without waiting, as long as their path is clear.


## 🧠 Now, in JavaScript terms:

### ✅ Asynchronous means:
JavaScript can start a task (like reading a file or calling an API) and move on to the next task without waiting for the first one to finish.

### ✅ Non-blocking I/O means:
When JavaScript does input/output (like reading a file, fetching data from a server), it doesn't block other code from running while waiting for the result.

## 🔧 How does it work?
### JavaScript uses:

##### Event Loop: A system that checks if any async task is done and then runs its callback.
##### Callbacks / Promises / async-await: Ways to handle results later, when they're ready.


📦 Example:
``` js

console.log("Start");

setTimeout(() => {
  console.log("Async task done!");
}, 2000); // Simulates a 2-second delay

console.log("End");
```
Output:

```
Start
End
Async task done!

```



### Even though the async task takes 2 seconds, JavaScript doesn't wait. It moves on and comes back when the task is ready.

🧵 Summary:


<img width="741" height="194" alt="image" src="https://github.com/user-attachments/assets/2d98fad8-29e2-4393-8837-dae491e52875" />

 
<img width="1199" height="641" alt="image" src="https://github.com/user-attachments/assets/240a4d40-a236-4109-a395-8566f47286da" />


## How do display a message after 5 seconds delay,( by passing JS ASYNCH NON BLOCKING IO )?

### ANS : USING A CALLBACK FUNCTION EX:|

<img width="784" height="255" alt="image" src="https://github.com/user-attachments/assets/fc01fcab-d621-49a9-91a0-08e904ac92a0" />

HERE ABOVE, the box is hidden ( faded ) in 5 seconds after that the alert message is displayed...!
















