<!DOCTYPE HTML>
<html>

    <head>
        <title>5 Star Rating</title>
        <meta name="viewport" content="width=device-width,initial-scale=1.0">
        <meta charset="utf-8" />
        <style>
        body {
            margin: 10px auto 0 auto;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {

            width: 200px;
            margin: 0 auto;
            text-align: center;
            box-shadow: 5px 5px 20px grey;
            padding: 20px;
        }

        .container ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .container ul li {
            display: inline-block;
            padding: 2px;
            font-size: 40px;
            cursor: pointer;
        }

        .selected,
        .hover {
            color: #FFDF00;
        }
        </style>
    </head>

    <body>
        <div class="container">
            <h2>RATING WIDGET</h2>
            <ul id="ratingElement">
                <li>*</li>
                <li>*</li>
                <li>*</li>
                <li>*</li>
                <li>*</li>
            </ul>
            <h3>You rated <span id="ratingValue">0</span>/5</h3>
        </div>
        <script>
        const ratingStarArr = document.querySelectorAll("li");
        const ratingValue = document.getElementById("ratingValue");

        for (const [index, element] of ratingStarArr.entries()) {
            element.addEventListener("click", () => {
                for (let i = 0; i < ratingStarArr.length; i++) {
                    if (i <= index) {
                        if (!ratingStarArr[i].classList.contains("selected"))
                            ratingStarArr[i].classList.add("selected");
                    } else {
                        if (ratingStarArr[i].classList.contains("selected"))
                            ratingStarArr[i].classList.remove("selected");
                    }
                }

                ratingValue.innerHTML = index + 1;
            });

            element.addEventListener("mouseover", () => {
                for (let i = 0; i < ratingStarArr.length; i++) {
                    if (i <= index) {
                        if (!ratingStarArr[i].classList.contains("selected"))
                            ratingStarArr[i].classList.add("hover");
                    }
                }
            });

            element.addEventListener("mouseout", () => {
                const allHoverSelected = document.getElementsByClassName("hover");
                while (allHoverSelected[0]) {
                    allHoverSelected[0].classList.remove("hover");
                }
            });
        }
        </script>
    </body>

</html>