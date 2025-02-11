# moo
moo
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Special</title>
    <style>
        body {
            text-align: center;
            font-family: 'Arial', sans-serif;
            background-image: url('https://placekitten.com/1920/1080'); /* Katzen Hintergrundbild */
            background-size: cover;
            color: white;
            padding-top: 50px;
            background-attachment: fixed;
        }
        h1 {
            font-size: 50px;
        }
        .question {
            font-size: 30px;
            margin-top: 20px;
        }
        .button {
            font-size: 20px;
            padding: 10px 20px;
            margin: 10px;
            border: none;
            cursor: pointer;
            border-radius: 10px;
            background-color: pink;
        }
        #response {
            font-size: 30px;
            margin-top: 20px;
        }
        .animation {
            display: none;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        @keyframes flyEmojis {
            0% { transform: translate(0, 0); opacity: 1; }
            100% { transform: translate(-100px, -300px); opacity: 0; }
        }
        #emojiContainer {
            font-size: 40px;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: flyEmojis 2s forwards;
        }
    </style>
</head>
<body>

    <!-- Start of the conversation -->
    <h1>Hiiii babyyyy</h1>
    <div id="question1" class="question">
        <button class="button" onclick="nextQuestion(1)">Weiter</button>
    </div>

    <!-- 1st Question: Valentine -->
    <div id="question2" class="question" style="display:none;">
        Ich weiß nicht, ob du was von Valentinstag hältst, aber it's ok.
        <br>
        <button class="button" onclick="nextQuestion(2)">Weiter</button>
    </div>

    <!-- 2nd Question: Do you love me -->
    <div id="question3" class="question" style="display:none;">
        Do you love me?
        <br>
        <button class="button" onclick="answerLove('yes')">Yes</button>
        <button class="button" onclick="answerLove('no')">No</button>
    </div>

    <div id="response3" class="question" style="display:none;"></div>

    <!-- 3rd Question: I Love You Moo -->
    <div id="question4" class="question" style="display:none;">
        I love you moo
        <br>
        <button class="button" onclick="answerMoo('mommy')">I love you too mommy</button>
        <button class="button" onclick="answerMoo('zara')">I love you too zara</button>
        <button class="button" onclick="answerMoo('mamushi')">I love you too mamushi</button>
    </div>

    <div id="response4" class="question" style="display:none;"></div>

    <!-- 4th Question: Sorry i have to ask this -->
    <div id="question5" class="question" style="display:none;">
        Sorry i have to ask this...
        <br>
        <button class="button" onclick="nextQuestion(5)">ok???</button>
    </div>

    <!-- 5th Question: Will you be my valentine -->
    <div id="question6" class="question" style="display:none;">
        Will you like be my valentine or do you find this cringe???!? (please be my valentine and touch me ob innappriate areas!)
        <br>
        <button class="button" onclick="answerValentine('weird')">No your weird</button>
        <button class="button" onclick="answerValentine('mommy')">Ok mommy</button>
        <button class="button" onclick="answerValentine('yesmommy')">Yes mommy</button>
        <button class="button" onclick="answerValentine('goodgirl')">Yes good girl</button>
        <button class="button" onclick="answerValentine('yesplease')">Yes please</button>
    </div>

    <div id="response6" class="question" style="display:none;"></div>

    <!-- Final Message with Animation -->
    <div id="animationContainer" class="animation">
        <img src="https://placekitten.com/100/100" alt="Kitten" style="position: absolute; animation: flyEmojis 5s infinite;">
        <img src="https://placekitten.com/120/120" alt="Kitten" style="position: absolute; animation: flyEmojis 5s infinite;">
        <img src="https://placekitten.com/130/130" alt="Kitten" style="position: absolute; animation: flyEmojis 5s infinite;">
        <img src="https://placekitten.com/140/140" alt="Kitten" style="position: absolute; animation: flyEmojis 5s infinite;">
        <img src="https://placekitten.com/150/150" alt="Kitten" style="position: absolute; animation: flyEmojis 5s infinite;">
    </div>

    <div id="finalMessage" class="question" style="display:none;">
        <h1>I LOVE YOU MO!</h1>
    </div>

    <script>
        let currentQuestion = 1;

        // Go to the next question
        function nextQuestion(questionNumber) {
            if (questionNumber === 1) {
                document.getElementById("question1").style.display = 'none';
                document.getElementById("question2").style.display = 'block';
            } else if (questionNumber === 2) {
                document.getElementById("question2").style.display = 'none';
                document.getElementById("question3").style.display = 'block';
            } else if (questionNumber === 5) {
                document.getElementById("question5").style.display = 'none';
                document.getElementById("question6").style.display = 'block';
            } else if (questionNumber === 6) {
                document.getElementById("question6").style.display = 'none';
                document.getElementById("response6").style.display = 'block';
                setTimeout(() => {
                    document.getElementById("animationContainer").style.display = 'block';
                    document.getElementById("finalMessage").style.display = 'block';
                }, 3000);
            }
        }

        // Handle the answer to 'Do you love me?'
        function answerLove(answer) {
            if (answer === 'yes') {
                document.getElementById("response3").innerHTML = "Yay thank you I love you too!";
            } else {
                document.getElementById("response3").innerHTML = "I know you just tested this to look what it says, but I know you love me.";
            }
            document.getElementById("question3").style.display = 'none';
            document.getElementById("response3").style.display = 'block';
            setTimeout(() => {
                document.getElementById("question4").style.display = 'block';
            }, 2000);
        }

        // Handle the answer to 'I love you moo'
        function answerMoo(answer) {
            let response;
            if (answer === 'mommy') {
                response = "I like that!";
            } else if (answer === 'zara') {
                response = "You turn me on!";
            } else if (answer === 'mamushi') {
                response = "I like that!";
            }
            document.getElementById("response4").innerHTML = response;
            document.getElementById("question4").style.display = 'none';
            document.getElementById("response4").style.display = 'block';
            setTimeout(() => {
                document.getElementById("question5").style.display = 'block';
            }, 2000);
        }

        // Handle the answer to 'Will you be my valentine'
        function answerValentine(answer) {
            let response;
            if (answer === 'weird') {
                response = "Nooo please, I love you!";
            } else if (answer === 'mommy') {
                response = "Was für ok? I asked you something cute!";
            } else if (answer === 'yesmommy') {
                response = "Good boy!";
            } else if (answer === 'goodgirl') {
                response = "You're the good boy here!";
            } else if (answer === 'yesplease') {
                response = "Hey, why are you begging for it?";
            }
            document.getElementById("response6").innerHTML = response;
            document.getElementById("question6").style.display = 'none';
            document.getElementById("response6").style.display = 'block';
        }
    </script>

</body>
</html>
