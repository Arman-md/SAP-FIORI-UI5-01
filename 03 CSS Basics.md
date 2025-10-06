# CSS Cascading Style Sheets : born to simplify the styling of webpage( beutify our html page ) in more modular way...!

<img width="1201" height="599" alt="image" src="https://github.com/user-attachments/assets/53f4a960-4551-45da-95e0-6d9185ad305f" />

## Applying CSS:


### Inline-> styling at tag level using : style property and value ( not resusable )
<tagname style="prop:value;prop:value;prop:value"> </tagname>

### Internal-> style code applied at page level using style prop. usually in the header, and we use a selector(identifier)

#### selectors:
-> tagname : applies to each tag and its tagspecific
-> .className : classification property additionally specified to group our elements or a particular catrgory
-> #id : eevery html element will have a unique id 

<style>

selector{
    prop:value;
    prop:value;
    ....
    }
</style>

ex:

``` html

<head>
    <style>
        h3{
            color: blue;
            border: 2px solid black;
        }
    </style>
</head>

<body style="background-color: aqua;">
    <!-- heading tags -->
    <h1>Welcome to HTML5</h1>
    <h2>Welcome to HTML5</h2>

    <h3>Welcome to HTML5</h3>

    <h3>Welcome to Earth</h3>
    <br>
    <input id="fn">
    <label> FIRST NAME </label>
    <br>
    <h4>Welcome to HTML5</h4>
</body>
```

#### CLassification of tags while applying properties : Block level elements
-> they themseleves dont have footprints on the page but used to structure the hml elements

1) DIV - always starts from new line ( used to group family of elements together )

-> avengers style will be applied in div avengers family( to all children)
``` html
<head>
 <style>
        .avengers {
            color: blue;
            border: 2px solid black;
        }

        #fn {
            background-color: black;
            color: beige;
            font-weight: bolder;
        }
    </style>
</head>

<body style="background-color: aqua;">
    <div class="avengers">
        <div class="Iron man">
            <h3>Welcome Ironman</h3>
        </div>

        <div class="hulk">
            <h3>Welcome Hulk</h3>
        </div>

        <div class="spiderman">
            <h3>Welcome Spidey</h3>
        </div>
    </div>
 <input id="fn">
    <label> FIRST NAME </label>
    <br>
</body>
```

2) SPAN/Inline elements


### External 


## Box Model

-> describes how element will be placed on the screen rleative to other element

<img width="1158" height="622" alt="image" src="https://github.com/user-attachments/assets/819886b7-f3bc-44e7-8cc8-9dc75db42877" />

## -> Responsive web design

``` html

<!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Responsive 3-Image Layout</title>
        <style>
            body {
                margin: 0;
                padding: 0;
                font-family: Arial, sans-serif;
                background-color: #f4f4f4;
            }

            .container {
                display: flex;
                flex-wrap: wrap;
                justify-content: center;
                gap: 20px;
                padding: 40px 20px;
            }

            .container img {
                width: 100%;
                max-width: 300px;
                height: auto;
                border-radius: 10px;
                box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
                transition: transform 0.3s ease;
            }

            .container img:hover {
                transform: scale(1.05);
            }

            @media (max-width: 768px) {
                .container {
                    flex-direction: column;
                    align-items: center;
                }
            }
        </style>
    </head>

    <body>

        <div class="container">
            <img src="images/blue-lamborghini-urus-suv-3i.jpg">
            <img src="images/Koenigsegg-Agera-RS.jpg">
            <img src="images/lamborghini-urus-side-view-4k-7b.jpg">
        </div>

    </body>

    </html>
```

output :

<img width="1752" height="653" alt="image" src="https://github.com/user-attachments/assets/eb85e9bd-e658-4e63-b9a3-c70f0b533412" />

<img width="1643" height="1019" alt="image" src="https://github.com/user-attachments/assets/5ddf6e33-1ab2-4b35-9af8-b60b62657173" />











