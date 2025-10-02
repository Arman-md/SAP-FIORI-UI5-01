# CSS

<img width="1201" height="599" alt="image" src="https://github.com/user-attachments/assets/53f4a960-4551-45da-95e0-6d9185ad305f" />


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











