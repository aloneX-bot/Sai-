
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>10 Questions 👀</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    min-height: 100vh;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #6a5acd, #00bcd4);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
    color: #222;
}

.container {
    width: 100%;
    max-width: 500px;
}

.card {
    background: rgba(255,255,255,0.96);
    border-radius: 28px;
    padding: 28px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.20);
    text-align: center;
}

.top {
    margin-bottom: 22px;
}

.logo {
    font-size: 42px;
    margin-bottom: 8px;
}

h1 {
    font-size: 27px;
    margin-bottom: 8px;
}

.subtitle {
    color: #777;
    font-size: 14px;
}

.progress-area {
    margin: 20px 0;
}

.progress-text {
    font-size: 13px;
    color: #777;
    margin-bottom: 7px;
}

.progress {
    width: 100%;
    height: 8px;
    background: #e8e8e8;
    border-radius: 20px;
    overflow: hidden;
}

.progress-bar {
    height: 100%;
    width: 10%;
    background: linear-gradient(90deg, #ff4ecd, #6a5acd);
    transition: width 0.4s ease;
}

.question {
    font-size: 22px;
    line-height: 1.35;
    margin: 25px 0;
}

.options {
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.option {
    border: none;
    width: 100%;
    padding: 15px;
    border-radius: 16px;
    background: #f4f4f7;
    font-size: 16px;
    cursor: pointer;
    transition: 0.2s;
    text-align: left;
}

.option:hover {
    transform: translateY(-2px);
    background: #ecebff;
}

.option:active {
    transform: scale(0.98);
}

.emoji {
    font-size: 21px;
    margin-right: 8px;
}

.footer {
    margin-top: 22px;
    font-size: 12px;
    color: #999;
}

.result {
    display: none;
}

.result-emoji {
    font-size: 65px;
    margin: 15px 0;
}

.result h2 {
    font-size: 27px;
    margin-bottom: 10px;
}

.result p {
    color: #666;
    line-height: 1.6;
    margin-bottom: 20px;
}

.restart {
    border: none;
    padding: 14px 25px;
    border-radius: 15px;
    background: #6a5acd;
    color: white;
    font-size: 15px;
    cursor: pointer;
}

.note {
    margin-top: 15px;
    font-size: 11px;
    color: #aaa;
}

@media(max-width: 400px) {
    .card {
        padding: 22px;
    }

    .question {
        font-size: 20px;
    }
}
</style>
</head>

<body>

<div class="container">

<div class="card" id="quiz">

    <div class="top">
        <div class="logo">👀</div>
        <h1>10 Random Questions</h1>
        <div class="subtitle">
            Let's see what kind of person you are 😭😂
        </div>
    </div>

    <div class="progress-area">
        <div class="progress-text" id="progressText">
            Question 1 of 10
        </div>

        <div class="progress">
            <div class="progress-bar" id="progressBar"></div>
        </div>
    </div>

    <div class="question" id="question">
        Loading...
    </div>

    <div class="options" id="options"></div>

    <div class="footer">
        No wrong answers... probably 👀
    </div>

</div>


<div class="card result" id="result">

    <div class="logo">🎉</div>

    <h1>Quiz Complete!</h1>

    <div class="result-emoji" id="resultEmoji">
        😎
    </div>

    <h2 id="resultTitle">
        Loading...
    </h2>

    <p id="resultText">
        Loading your result...
    </p>

    <button class="restart" onclick="restartQuiz()">
        🔄 Try Again
    </button>

    <div class="note">
        Made for fun. No serious personality analysis 😂
    </div>

</div>

</div>


<script>

const questions = [

    {
        question: "First important question... Where do you usually spend most of your time? 👀",
        options: [
            { text: "🏠 At home", type: "chill" },
            { text: "🏫 School / college", type: "smart" },
            { text: "🌆 Outside with friends", type: "social" },
            { text: "📱 Literally everywhere on my phone", type: "chaos" }
        ]
    },

    {
        question: "Your ideal free day looks like... 😌",
        options: [
            { text: "😴 Sleep + food + repeat", type: "chill" },
            { text: "👯 Go out with friends", type: "social" },
            { text: "🎮 Games / movies / series", type: "chaos" },
            { text: "📚 Learn or do something productive", type: "smart" }
        ]
    },

    {
        question: "Someone gives you ₹500. What's your first thought? 😂",
        options: [
            { text: "🍕 FOOD. Obviously.", type: "chill" },
            { text: "🛍️ Time to buy something", type: "social" },
            { text: "💰 SAVE IT", type: "smart" },
            { text: "🤔 I'll decide after 3 business days", type: "chaos" }
        ]
    },

    {
        question: "Pick your entertainment weapon 🎬",
        options: [
            { text: "🎥 Movies", type: "chill" },
            { text: "📺 Series", type: "smart" },
            { text: "🎵 Music", type: "social" },
            { text: "📱 Reels until my brain disappears", type: "chaos" }
        ]
    },

    {
        question: "Your friends would probably describe you as... 👀",
        options: [
            { text: "😂 Funny", type: "social" },
            { text: "😌 Calm", type: "chill" },
            { text: "🧠 Smart", type: "smart" },
            { text: "🤡 Certified chaos", type: "chaos" }
        ]
    },

    {
        question: "What's your reaction when plans suddenly get cancelled? 😭",
        options: [
            { text: "🥳 BEST NEWS EVER", type: "chill" },
            { text: "😐 Okay... anyway", type: "smart" },
            { text: "😩 NOOOO", type: "social" },
            { text: "😂 Let's make new plans", type: "chaos" }
        ]
    },

    {
        question: "Pick ONE food category for the rest of the day 🍔",
        options: [
            { text: "🍕 Pizza / fast food", type: "chaos" },
            { text: "🍛 Proper home food", type: "chill" },
            { text: "🍜 Something spicy", type: "social" },
            { text: "🍰 Dessert only. No questions.", type: "smart" }
        ]
    },

    {
        question: "When you get a message, you usually... 📱",
        options: [
            { text: "⚡ Reply instantly", type: "social" },
            { text: "👀 Read it and reply later", type: "smart" },
            { text: "😂 Reply when I remember", type: "chaos" },
            { text: "😴 See it after 5 business days", type: "chill" }
        ]
    },

    {
        question: "Choose your perfect weekend vibe 🌈",
        options: [
            { text: "🌿 Peaceful and relaxed", type: "chill" },
            { text: "🎉 Full masti with friends", type: "social" },
            { text: "🎮 Gaming / movies / music", type: "chaos" },
            { text: "✨ Trying something new", type: "smart" }
        ]
    },

    {
        question: "Final question... Which one sounds MOST like you? 👀",
        options: [
            { text: "😌 Peace > everything", type: "chill" },
            { text: "😂 Life is for fun", type: "social" },
            { text: "🧠 I like figuring things out", type: "smart" },
            { text: "🤡 I have no idea what's happening", type: "chaos" }
        ]
    }

];


let currentQuestion = 0;

let scores = {
    chill: 0,
    social: 0,
    smart: 0,
    chaos: 0
};


function loadQuestion() {

    const q = questions[currentQuestion];

    document.getElementById("question").textContent = q.question;

    document.getElementById("progressText").textContent =
        `Question ${currentQuestion + 1} of ${questions.length}`;

    document.getElementById("progressBar").style.width =
        `${((currentQuestion + 1) / questions.length) * 100}%`;

    const optionsContainer = document.getElementById("options");

    optionsContainer.innerHTML = "";

    q.options.forEach(option => {

        const button = document.createElement("button");

        button.className = "option";

        button.textContent = option.text;

        button.onclick = () => selectAnswer(option.type);

        optionsContainer.appendChild(button);

    });
}


function selectAnswer(type) {

    scores[type]++;

    currentQuestion++;

    if (currentQuestion < questions.length) {

        loadQuestion();

    } else {

        showResult();

    }
}


function showResult() {

    document.getElementById("quiz").style.display = "none";

    document.getElementById("result").style.display = "block";

    let personality =
        Object.keys(scores).reduce((a, b) =>
            scores[a] > scores[b] ? a : b
        );

    const results = {

        chill: {
            emoji: "😌",
            title: "The Chill One",
            text: "You seem like someone who enjoys peace, comfort and good vibes. Stress? Not invited. 😂"
        },

        social: {
            emoji: "🎉",
            title: "The Social One",
            text: "You seem to enjoy people, conversations and having a good time. Boring is probably not your thing. 😂"
        },

        smart: {
            emoji: "🧠",
            title: "The Thinker",
            text: "You seem thoughtful and curious. You actually think before doing things... sometimes. 👀"
        },

        chaos: {
            emoji: "🤡",
            title: "The Chaos Generator",
            text: "Your personality appears to be 50% fun, 50% randomness and 100% unpredictable. 😂"
        }

    };

    document.getElementById("resultEmoji").textContent =
        results[personality].emoji;

    document.getElementById("resultTitle").textContent =
        results[personality].title;

    document.getElementById("resultText").textContent =
        results[personality].text;
}


function restartQuiz() {

    currentQuestion = 0;

    scores = {
        chill: 0,
        social: 0,
        smart: 0,
        chaos: 0
    };

    document.getElementById("result").style.display = "none";

    document.getElementById("quiz").style.display = "block";

    loadQuestion();
}


loadQuestion();

</script>

</body>
</html>
