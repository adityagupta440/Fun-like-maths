<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Math Quest - Class 9</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    min-height: 100vh;
    background:
        radial-gradient(circle at 10% 20%, #3b1d91, transparent 30%),
        radial-gradient(circle at 90% 80%, #006d8f, transparent 30%),
        linear-gradient(135deg, #10082b, #20104d);
    color: white;
}

.game {
    width: 94%;
    max-width: 850px;
    margin: 20px auto;
    padding: 25px;
    background: rgba(255,255,255,0.10);
    border: 1px solid rgba(255,255,255,0.15);
    border-radius: 25px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.45);
}

/* START SCREEN */

#startScreen {
    text-align: center;
    padding: 45px 15px;
}

.logo {
    font-size: 42px;
    font-weight: 900;
    letter-spacing: 2px;
    color: #00ffd5;
    text-shadow: 0 0 20px rgba(0,255,213,0.5);
}

#startScreen h1 {
    font-size: 42px;
    color: #ffe600;
    margin: 15px 0;
}

.start-text {
    color: #ddd;
    line-height: 1.7;
    font-size: 17px;
    max-width: 650px;
    margin: auto;
}

.start-button,
.restart-button {
    border: none;
    background: linear-gradient(90deg, #ff00cc, #6c2cff);
    color: white;
    padding: 16px 40px;
    border-radius: 50px;
    font-size: 19px;
    font-weight: bold;
    cursor: pointer;
    margin-top: 25px;
    transition: 0.25s;
}

.start-button:hover,
.restart-button:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 30px rgba(255,0,200,0.3);
}

/* QUIZ */

#quizScreen {
    display: none;
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 12px;
}

.game-title {
    color: #ffe600;
    font-size: 25px;
    font-weight: bold;
}

.stats {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
}

.stat {
    background: rgba(0,0,0,0.3);
    padding: 9px 14px;
    border-radius: 20px;
    font-weight: bold;
}

/* PROGRESS */

.progress-area {
    margin-top: 25px;
}

.progress-text {
    display: flex;
    justify-content: space-between;
    margin-bottom: 8px;
    font-size: 14px;
}

.progress {
    height: 12px;
    background: rgba(0,0,0,0.4);
    border-radius: 20px;
    overflow: hidden;
}

.progress-bar {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, #00ffd5, #00aaff, #ff00cc);
    transition: width 0.4s;
}

/* TIMER */

.timer-container {
    text-align: center;
    margin: 25px 0;
}

.timer {
    width: 85px;
    height: 85px;
    margin: auto;
    border-radius: 50%;
    border: 6px solid #00ffd5;
    background: rgba(0,0,0,0.4);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 25px;
    font-weight: bold;
    transition: 0.3s;
}

.timer.warning {
    border-color: #ff4757;
    color: #ff4757;
}

/* QUESTION */

.question-card {
    background: rgba(0,0,0,0.25);
    border-radius: 22px;
    padding: 27px;
}

.question-number {
    color: #00ffd5;
    font-weight: bold;
    margin-bottom: 15px;
}

.question {
    font-size: 23px;
    line-height: 1.5;
    font-weight: bold;
    margin-bottom: 25px;
}

/* OPTIONS */

.options {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
}

.option {
    padding: 17px;
    background: rgba(255,255,255,0.07);
    color: white;
    border: 2px solid rgba(255,255,255,0.2);
    border-radius: 14px;
    cursor: pointer;
    text-align: left;
    font-size: 16px;
    transition: 0.2s;
}

.option:hover:not(:disabled) {
    border-color: #00ffff;
    background: rgba(0,255,255,0.12);
    transform: translateY(-3px);
}

.option.correct {
    background: #009e68;
    border-color: #00ffb0;
}

.option.wrong {
    background: #c92d3b;
    border-color: #ff6b76;
}

.option:disabled {
    cursor: not-allowed;
}

/* MESSAGE */

.message {
    min-height: 32px;
    margin-top: 18px;
    text-align: center;
    font-size: 18px;
    font-weight: bold;
}

/* NEXT */

.next-button {
    display: none;
    width: 100%;
    margin-top: 15px;
    padding: 16px;
    border: none;
    border-radius: 14px;
    background: linear-gradient(90deg, #ff00cc, #6c2cff);
    color: white;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
}

/* RESULT */

#resultScreen {
    display: none;
    text-align: center;
    padding: 45px 10px;
}

.result-icon {
    font-size: 42px;
    font-weight: bold;
    color: #ffe600;
}

.result-title {
    font-size: 38px;
    color: #ffe600;
    margin: 15px 0;
}

.final-score {
    font-size: 50px;
    color: #00ffd5;
    font-weight: bold;
}

.result-box {
    display: flex;
    justify-content: center;
    gap: 12px;
    margin: 30px 0;
    flex-wrap: wrap;
}

.result-item {
    min-width: 130px;
    padding: 18px;
    border-radius: 15px;
    background: rgba(255,255,255,0.1);
}

.result-item strong {
    display: block;
    font-size: 28px;
    color: #ffe600;
    margin-bottom: 5px;
}

/* MOBILE */

@media(max-width:600px) {

    .game {
        width: 96%;
        padding: 15px;
    }

    #startScreen h1 {
        font-size: 32px;
    }

    .logo {
        font-size: 32px;
    }

    .question {
        font-size: 19px;
    }

    .options {
        grid-template-columns: 1fr;
    }

    .header {
        flex-direction: column;
        align-items: stretch;
    }

    .stats {
        justify-content: center;
    }
}
</style>
</head>

<body>

<div class="game">

<!-- START SCREEN -->

<div id="startScreen">

    <div class="logo">
        MATH QUEST
    </div>

    <h1>Areas & Perimeters</h1>

    <p class="start-text">
        Welcome to Math Quest.
        <br><br>

        You will receive 15 random questions
        from a large question bank.
        <br><br>

        Each question has 90 seconds.
        Answer quickly to earn more XP and
        build your streak.
        <br><br>

        3 Lives | 90 Seconds per Question |
        15 Random Questions
    </p>

    <button class="start-button" onclick="startGame()">
        START GAME
    </button>

</div>


<!-- QUIZ SCREEN -->

<div id="quizScreen">

    <div class="header">

        <div class="game-title">
            MATH QUEST
        </div>

        <div class="stats">

            <div class="stat">
                XP: <span id="score">0</span>
            </div>

            <div class="stat">
                Streak: <span id="streak">0</span>
            </div>

            <div class="stat">
                Lives: <span id="lives">3</span>
            </div>

        </div>

    </div>


    <div class="progress-area">

        <div class="progress-text">

            <span>Quest Progress</span>

            <span id="progressText">
                1 / 15
            </span>

        </div>

        <div class="progress">

            <div
                class="progress-bar"
                id="progressBar">
            </div>

        </div>

    </div>


    <div class="timer-container">

        <div class="timer" id="timerCircle">

            <span id="timer">
                90
            </span>

        </div>

    </div>


    <div class="question-card">

        <div
            class="question-number"
            id="questionNumber">
            QUESTION 1
        </div>

        <div
            class="question"
            id="question">
        </div>

        <div
            class="options"
            id="options">
        </div>

        <div
            class="message"
            id="message">
        </div>

        <button
            class="next-button"
            id="nextButton"
            onclick="nextQuestion()">

            NEXT QUESTION

        </button>

    </div>

</div>


<!-- RESULT SCREEN -->

<div id="resultScreen">

    <div class="result-icon">
        MATH QUEST COMPLETE
    </div>

    <div
        class="result-title"
        id="resultTitle">
        MATH CHAMPION
    </div>

    <div class="final-score">

        <span id="finalScore">0</span>
        XP

    </div>

    <p id="rankText">
        Great work.
    </p>


    <div class="result-box">

        <div class="result-item">

            <strong id="correct">0</strong>

            Correct

        </div>

        <div class="result-item">

            <strong id="wrong">0</strong>

            Wrong

        </div>

        <div class="result-item">

            <strong id="accuracy">0%</strong>

            Accuracy

        </div>

    </div>


    <button
        class="restart-button"
        onclick="restartGame()">

        PLAY AGAIN

    </button>

</div>

</div>


<script>

/* =========================================================
   QUESTION BANK
   50 QUESTIONS
========================================================= */

var questionBank = [

{
q: "A rectangle has length 12 cm and breadth 8 cm. What is its perimeter?",
o: ["20 cm", "40 cm", "96 cm", "48 cm"],
a: 1
},

{
q: "What is the area of a rectangle with length 15 cm and breadth 6 cm?",
o: ["21 cm²", "42 cm²", "90 cm²", "180 cm²"],
a: 2
},

{
q: "A square has a side of 9 cm. What is its perimeter?",
o: ["18 cm", "27 cm", "36 cm", "81 cm"],
a: 2
},

{
q: "What is the area of a square whose side is 11 cm?",
o: ["22 cm²", "44 cm²", "121 cm²", "132 cm²"],
a: 2
},

{
q: "Which formula gives the perimeter of a rectangle?",
o: ["l × b", "2(l + b)", "l + b", "2lb"],
a: 1
},

{
q: "What is the area of a triangle with base 10 cm and height 8 cm?",
o: ["20 cm²", "40 cm²", "80 cm²", "18 cm²"],
a: 1
},

{
q: "The area of a parallelogram is calculated by:",
o: ["Base × Height", "½ × Base × Height", "Side × Side", "2(Base + Height)"],
a: 0
},

{
q: "A triangle has base 14 cm and height 5 cm. Find its area.",
o: ["19 cm²", "35 cm²", "70 cm²", "45 cm²"],
a: 1
},

{
q: "If the side of a square is doubled, its area becomes:",
o: ["2 times", "3 times", "4 times", "8 times"],
a: 2
},

{
q: "A rectangle has area 72 cm² and length 12 cm. Find its breadth.",
o: ["4 cm", "6 cm", "8 cm", "10 cm"],
a: 1
},

{
q: "What is the perimeter of a square with side 15 cm?",
o: ["30 cm", "45 cm", "60 cm", "225 cm"],
a: 2
},

{
q: "The area of a square is 144 cm². What is its side?",
o: ["10 cm", "12 cm", "14 cm", "16 cm"],
a: 1
},

{
q: "A parallelogram has base 12 cm and height 7 cm. What is its area?",
o: ["42 cm²", "84 cm²", "19 cm²", "96 cm²"],
a: 1
},

{
q: "A rectangle has length 20 m and breadth 10 m. Find its perimeter.",
o: ["40 m", "60 m", "200 m", "30 m"],
a: 1
},

{
q: "Which of the following is a unit of area?",
o: ["cm", "cm²", "kg", "litre"],
a: 1
},

{
q: "A square has perimeter 48 cm. Find its side.",
o: ["10 cm", "12 cm", "14 cm", "16 cm"],
a: 1
},

{
q: "A rectangle has perimeter 50 cm. If its length is 15 cm, find its breadth.",
o: ["5 cm", "10 cm", "15 cm", "20 cm"],
a: 0
},

{
q: "Find the area of a square whose perimeter is 36 cm.",
o: ["36 cm²", "72 cm²", "81 cm²", "144 cm²"],
a: 2
},

{
q: "Find the area of a rectangle of length 18 m and breadth 7 m.",
o: ["25 m²", "50 m²", "126 m²", "252 m²"],
a: 2
},

{
q: "A triangle has base 16 cm and height 9 cm. Its area is:",
o: ["72 cm²", "144 cm²", "25 cm²", "81 cm²"],
a: 0
},

{
q: "A parallelogram has base 20 cm and height 6 cm. Find its area.",
o: ["26 cm²", "60 cm²", "120 cm²", "240 cm²"],
a: 2
},

{
q: "The perimeter of a rectangle is 64 cm. If length is 20 cm, breadth is:",
o: ["10 cm", "12 cm", "14 cm", "16 cm"],
a: 1
},

{
q: "The area of a rectangle is 120 cm². If its breadth is 10 cm, its length is:",
o: ["10 cm", "12 cm", "15 cm", "20 cm"],
a: 1
},

{
q: "A square has area 225 cm². What is its perimeter?",
o: ["30 cm", "45 cm", "60 cm", "90 cm"],
a: 2
},

{
q: "Which unit is suitable for measuring the area of a classroom floor?",
o: ["cm", "m", "m²", "kg"],
a: 2
},

{
q: "Which unit is suitable for measuring the perimeter of a playground?",
o: ["m", "m²", "cm²", "litre"],
a: 0
},

{
q: "A rectangle is 25 cm long and 4 cm wide. Its area is:",
o: ["29 cm²", "50 cm²", "100 cm²", "200 cm²"],
a: 2
},

{
q: "A square has side 14 cm. Its area is:",
o: ["28 cm²", "56 cm²", "196 cm²", "224 cm²"],
a: 2
},

{
q: "A square has side 14 cm. Its perimeter is:",
o: ["28 cm", "42 cm", "56 cm", "196 cm"],
a: 2
},

{
q: "A triangle has base 20 cm and height 12 cm. Find its area.",
o: ["120 cm²", "240 cm²", "60 cm²", "32 cm²"],
a: 0
},

{
q: "A parallelogram has area 180 cm² and base 15 cm. Find its height.",
o: ["10 cm", "12 cm", "15 cm", "20 cm"],
a: 1
},

{
q: "A triangle has area 60 cm² and base 12 cm. Find its height.",
o: ["5 cm", "10 cm", "12 cm", "15 cm"],
a: 1
},

{
q: "If the length of a rectangle is doubled while breadth remains the same, its area becomes:",
o: ["Half", "Double", "Triple", "Four times"],
a: 1
},

{
q: "If both length and breadth of a rectangle are doubled, its area becomes:",
o: ["2 times", "3 times", "4 times", "8 times"],
a: 2
},

{
q: "If the side of a square is tripled, its area becomes:",
o: ["3 times", "6 times", "9 times", "12 times"],
a: 2
},

{
q: "A rectangle has length 30 cm and breadth 5 cm. Its perimeter is:",
o: ["35 cm", "60 cm", "70 cm", "150 cm"],
a: 2
},

{
q: "A square has perimeter 100 cm. Its area is:",
o: ["100 cm²", "400 cm²", "625 cm²", "2500 cm²"],
a: 2
},

{
q: "A rectangle has area 200 cm² and length 20 cm. Find its breadth.",
o: ["5 cm", "10 cm", "15 cm", "20 cm"],
a: 1
},

{
q: "The perimeter of a square is 80 cm. What is its side?",
o: ["10 cm", "15 cm", "20 cm", "40 cm"],
a: 2
},

{
q: "The area of a square with side 25 m is:",
o: ["50 m²", "100 m²", "625 m²", "1250 m²"],
a: 2
},

{
q: "A triangle has base 25 cm and height 8 cm. Find its area.",
o: ["100 cm²", "200 cm²", "33 cm²", "50 cm²"],
a: 0
},

{
q: "A parallelogram has base 18 cm and height 10 cm. Its area is:",
o: ["28 cm²", "90 cm²", "180 cm²", "360 cm²"],
a: 2
},

{
q: "A rectangle has length 16 cm and breadth 9 cm. Its area is:",
o: ["25 cm²", "50 cm²", "144 cm²", "288 cm²"],
a: 2
},

{
q: "A rectangle has length 16 cm and breadth 9 cm. Its perimeter is:",
o: ["25 cm", "50 cm", "144 cm", "288 cm"],
a: 1
},

{
q: "The area of a triangle is 90 cm² and its height is 12 cm. Find its base.",
o: ["10 cm", "12 cm", "15 cm", "18 cm"],
a: 2
},

{
q: "A parallelogram has area 240 cm² and height 12 cm. Find its base.",
o: ["10 cm", "15 cm", "20 cm", "24 cm"],
a: 2
},

{
q: "A rectangle has area 180 cm² and breadth 9 cm. Find its length.",
o: ["10 cm", "15 cm", "20 cm", "25 cm"],
a: 1
},

{
q: "A square has area 400 cm². Its side is:",
o: ["10 cm", "20 cm", "40 cm", "100 cm"],
a: 1
},

{
q: "A rectangle is 40 m long and 15 m wide. Its area is:",
o: ["55 m²", "110 m²", "600 m²", "800 m²"],
a: 2
},

{
q: "A rectangle is 40 m long and 15 m wide. Its perimeter is:",
o: ["55 m", "80 m", "110 m", "600 m"],
a: 2
},

{
q: "A square and a rectangle have the same area of 100 cm². The side of the square is:",
o: ["5 cm", "10 cm", "20 cm", "25 cm"],
a: 1
}

];


/* =========================================================
   GAME VARIABLES
========================================================= */

var gameQuestions = [];

var currentQuestion = 0;

var score = 0;

var streak = 0;

var lives = 3;

var correctAnswers = 0;

var wrongAnswers = 0;

var timeLeft = 90;

var timer;


/* =========================================================
   SHUFFLE FUNCTION
========================================================= */

function shuffle(array) {

    var currentIndex = array.length;
    var randomIndex;
    var temporaryValue;

    while (currentIndex !== 0) {

        randomIndex =
            Math.floor(Math.random() * currentIndex);

        currentIndex--;

        temporaryValue =
            array[currentIndex];

        array[currentIndex] =
            array[randomIndex];

        array[randomIndex] =
            temporaryValue;
    }

    return array;
}


/* =========================================================
   CREATE RANDOM GAME
========================================================= */

function createRandomGame() {

    var copy = questionBank.slice();

    shuffle(copy);

    gameQuestions =
        copy.slice(0, 15);

    /*
       Also randomize the answer choices.
       We store the correct answer as text
       before shuffling.
    */

    for (var i = 0; i < gameQuestions.length; i++) {

        var question =
            gameQuestions[i];

        var correctAnswer =
            question.o[question.a];

        question.o =
            shuffle(question.o.slice());

        question.a =
            question.o.indexOf(correctAnswer);
    }
}


/* =========================================================
   START GAME
========================================================= */

function startGame() {

    document.getElementById("startScreen").style.display =
        "none";

    document.getElementById("quizScreen").style.display =
        "block";

    currentQuestion = 0;
    score = 0;
    streak = 0;
    lives = 3;
    correctAnswers = 0;
    wrongAnswers = 0;

    createRandomGame();

    updateStats();

    showQuestion();
}


/* =========================================================
   SHOW QUESTION
========================================================= */

function showQuestion() {

    clearInterval(timer);

    timeLeft = 90;

    var q =
        gameQuestions[currentQuestion];


    document.getElementById("questionNumber").innerHTML =
        "QUESTION " +
        (currentQuestion + 1);


    document.getElementById("question").innerHTML =
        q.q;


    document.getElementById("progressText").innerHTML =
        (currentQuestion + 1) +
        " / 15";


    var progress =
        (currentQuestion / 15) * 100;


    document.getElementById("progressBar").style.width =
        progress + "%";


    document.getElementById("timer").innerHTML =
        timeLeft;


    document.getElementById("timerCircle")
        .classList.remove("warning");


    document.getElementById("message").innerHTML =
        "";


    document.getElementById("nextButton").style.display =
        "none";


    var options =
        document.getElementById("options");


    options.innerHTML = "";


    for (var i = 0; i < q.o.length; i++) {

        var button =
            document.createElement("button");


        button.className =
            "option";


        button.innerHTML =
            String.fromCharCode(65 + i) +
            ") " +
            q.o[i];


        button.onclick =
            createAnswerFunction(i);


        options.appendChild(button);
    }


    startTimer();
}


/* =========================================================
   ANSWER FUNCTION
========================================================= */

function createAnswerFunction(index) {

    return function() {

        checkAnswer(index);

    };
}


/* =========================================================
   TIMER
========================================================= */

function startTimer() {

    timer =
        setInterval(function() {

            timeLeft--;

            document.getElementById("timer").innerHTML =
                timeLeft;


            if (timeLeft <= 10) {

                document
                    .getElementById("timerCircle")
                    .classList.add("warning");

            }


            if (timeLeft <= 0) {

                clearInterval(timer);

                timeUp();

            }

        }, 1000);
}


/* =========================================================
   CHECK ANSWER
========================================================= */

function checkAnswer(selected) {

    clearInterval(timer);

    var q =
        gameQuestions[currentQuestion];


    var buttons =
        document.querySelectorAll(".option");


    for (var i = 0; i < buttons.length; i++) {

        buttons[i].disabled = true;

    }


    if (selected === q.a) {

        buttons[selected]
            .classList.add("correct");


        correctAnswers++;

        streak++;


        /*
           Faster answers earn more XP.
           Maximum base score = 100.
           Time bonus = up to 90.
           Streak bonus increases with streak.
        */

        var points =
            100 +
            timeLeft +
            (streak * 10);


        score += points;


        document.getElementById("message").innerHTML =
            "CORRECT! +" +
            points +
            " XP";


        document.getElementById("message").style.color =
            "#00ffcc";

    }

    else {

        buttons[selected]
            .classList.add("wrong");


        buttons[q.a]
            .classList.add("correct");


        wrongAnswers++;

        streak = 0;

        lives--;


        document.getElementById("message").innerHTML =
            "WRONG! Correct answer: " +
            q.o[q.a];


        document.getElementById("message").style.color =
            "#ff7675";


        if (lives <= 0) {

            updateStats();


            setTimeout(function() {

                endGame();

            }, 1200);


            return;
        }
    }


    updateStats();


    document.getElementById("nextButton").style.display =
        "block";
}


/* =========================================================
   TIME UP
========================================================= */

function timeUp() {

    var q =
        gameQuestions[currentQuestion];


    var buttons =
        document.querySelectorAll(".option");


    for (var i = 0; i < buttons.length; i++) {

        buttons[i].disabled = true;

    }


    buttons[q.a]
        .classList.add("correct");


    wrongAnswers++;

    streak = 0;

    lives--;


    document.getElementById("message").innerHTML =
        "TIME'S UP! Correct answer: " +
        q.o[q.a];


    document.getElementById("message").style.color =
        "#ff4757";


    updateStats();


    if (lives <= 0) {

        setTimeout(function() {

            endGame();

        }, 1200);

    }

    else {

        document.getElementById("nextButton").style.display =
            "block";

    }
}


/* =========================================================
   NEXT QUESTION
========================================================= */

function nextQuestion() {

    currentQuestion++;


    if (currentQuestion >= 15) {

        endGame();

    }

    else {

        showQuestion();

    }
}


/* =========================================================
   UPDATE STATS
========================================================= */

function updateStats() {

    document.getElementById("score").innerHTML =
        score;

    document.getElementById("streak").innerHTML =
        streak;

    document.getElementById("lives").innerHTML =
        lives;
}


/* =========================================================
   END GAME
========================================================= */

function endGame() {

    clearInterval(timer);


    document.getElementById("quizScreen").style.display =
        "none";


    document.getElementById("resultScreen").style.display =
        "block";


    document.getElementById("finalScore").innerHTML =
        score;


    document.getElementById("correct").innerHTML =
        correctAnswers;


    document.getElementById("wrong").innerHTML =
        wrongAnswers;


    var accuracy =
        Math.round(
            (correctAnswers / 15) * 100
        );


    document.getElementById("accuracy").innerHTML =
        accuracy + "%";


    if (accuracy >= 90) {

        document.getElementById("resultTitle").innerHTML =
            "MATH LEGEND";


        document.getElementById("rankText").innerHTML =
            "Outstanding performance. You have mastered this quiz.";

    }

    else if (accuracy >= 75) {

        document.getElementById("resultTitle").innerHTML =
            "MATH CHAMPION";


        document.getElementById("rankText").innerHTML =
            "Excellent work. Keep building your mathematics skills.";

    }

    else if (accuracy >= 50) {

        document.getElementById("resultTitle").innerHTML =
            "MATH EXPLORER";


        document.getElementById("rankText").innerHTML =
            "Good effort. Practice a little more and improve your score.";

    }

    else {

        document.getElementById("resultTitle").innerHTML =
            "MATH ROOKIE";


        document.getElementById("rankText").innerHTML =
            "Keep practicing. Your next attempt can be much better.";

    }
}


/* =========================================================
   RESTART
========================================================= */

function restartGame() {

    clearInterval(timer);


    document.getElementById("resultScreen").style.display =
        "none";


    document.getElementById("startScreen").style.display =
        "block";
}

</script>

</body>
</html>
