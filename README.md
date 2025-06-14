Develop an interactive multiple-choice quiz game that displays questions, collects answers, and provides a score at the end.

You can also, add different type of Questions like, Single or Multi Select, Fill in the Blanks or more.

Coding Section:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Interactive Quiz Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 20px;
      text-align: center;
    }

    .quiz-container {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      max-width: 600px;
      margin: auto;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    .question {
      font-size: 20px;
      margin-bottom: 15px;
    }

    .options {
      text-align: left;
      margin-bottom: 20px;
    }

    .options label {
      display: block;
      margin-bottom: 8px;
    }

    button {
      padding: 10px 20px;
      background: #333;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background: #555;
    }

    #score {
      font-size: 22px;
      color: green;
      margin-top: 20px;
    }
  </style>
</head>
<body>

<div class="quiz-container" id="quiz">
  <div id="questionBox" class="question"></div>
  <form id="quizForm">
    <div id="options" class="options"></div>
    <button type="submit">Next</button>
  </form>
  <div id="score"></div>
</div>

<script>
  const questions = [
    {
      type: "single",
      question: "Which language runs in a web browser?",
      options: ["Java", "C", "Python", "JavaScript"],
      answer: "JavaScript"
    },
    {
      type: "multi",
      question: "Select all programming languages:",
      options: ["HTML", "Python", "CSS", "Java"],
      answer: ["Python", "Java"]
    },
    {
      type: "text",
      question: "Fill in the blank: HTML stands for ______.",
      answer: "HyperText Markup Language"
    }
  ];

  let currentQuestion = 0;
  let score = 0;

  const quizForm = document.getElementById("quizForm");
  const questionBox = document.getElementById("questionBox");
  const optionsBox = document.getElementById("options");
  const scoreBox = document.getElementById("score");

  function loadQuestion() {
    let q = questions[currentQuestion];
    questionBox.innerText = q.question;
    optionsBox.innerHTML = "";

    if (q.type === "single") {
      q.options.forEach(opt => {
        optionsBox.innerHTML += `
          <label><input type="radio" name="option" value="${opt}"> ${opt}</label>
        `;
      });
    } else if (q.type === "multi") {
      q.options.forEach(opt => {
        optionsBox.innerHTML += `
          <label><input type="checkbox" name="option" value="${opt}"> ${opt}</label>
        `;
      });
    } else if (q.type === "text") {
      optionsBox.innerHTML = `
        <input type="text" name="textAnswer" placeholder="Type your answer here" required>
      `;
    }
  }

  quizForm.addEventListener("submit", function(e) {
    e.preventDefault();
    let q = questions[currentQuestion];
    let userAnswer;

    if (q.type === "single") {
      const selected = document.querySelector('input[name="option"]:checked');
      if (selected && selected.value === q.answer) {
        score++;
      }
    } else if (q.type === "multi") {
      const selected = Array.from(document.querySelectorAll('input[name="option"]:checked')).map(i => i.value);
      if (arraysEqual(selected.sort(), q.answer.sort())) {
        score++;
      }
    } else if (q.type === "text") {
      const textInput = document.querySelector('input[name="textAnswer"]');
      if (textInput && textInput.value.trim().toLowerCase() === q.answer.toLowerCase()) {
        score++;
      }
    }

    currentQuestion++;
    if (currentQuestion < questions.length) {
      loadQuestion();
    } else {
      quizForm.style.display = "none";
      questionBox.innerText = "Quiz Completed!";
      scoreBox.innerText = `Your score: ${score} / ${questions.length}`;
    }
  });

  function arraysEqual(a, b) {
    return JSON.stringify(a) === JSON.stringify(b);
  }

  loadQuestion();
</script>

</body>
</html>
