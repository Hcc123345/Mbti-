# Mbti-
This website test basic mbti
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MBTI Personality Test</title>
    <style>
        body { font-family: Arial, sans-serif; background: linear-gradient(to right, #ff9966, #ff5e62); color: white; text-align: center; }
        .container { max-width: 600px; margin: 20px auto; padding: 20px; background: rgba(0, 0, 0, 0.8); border-radius: 10px; }
        .question { margin-bottom: 15px; }
        button { background: #ffcc00; border: none; padding: 10px; margin-top: 20px; cursor: pointer; border-radius: 5px; }
        #result { margin-top: 20px; font-weight: bold; }
    </style>
</head>
<body>
    <div class="container">
        <h2>MBTI Personality Test</h2>
        <form id="quizForm">
            <div id="questions"></div>
            <button type="button" onclick="calculateMBTI()">Submit</button>
        </form>
        <div id="result"></div>
    </div>

    <script>
        const questionsData = [
            { question: "Do you prefer to spend time alone rather than in large groups?", type: "E" },
            { question: "Do you rely more on logic than feelings when making decisions?", type: "F" },
            { question: "Do you prefer to follow a structured schedule rather than being spontaneous?", type: "P" },
            { question: "Do you often think about future possibilities rather than focusing on present realities?", type: "S" },
            { question: "Do you feel energized by social interactions?", type: "E" },
            { question: "Do you prioritize facts over abstract theories?", type: "N" },
            { question: "Do you make decisions based on personal values rather than objective analysis?", type: "T" },
            { question: "Do you like planning things in advance rather than going with the flow?", type: "J" },
            { question: "Do you prefer deep one-on-one conversations rather than group discussions?", type: "I" },
            { question: "Do you trust your gut feeling more than detailed analysis?", type: "T" },
            { question: "Do you find it easy to adapt to last-minute changes?", type: "P" },
            { question: "Do you often focus on small details rather than the bigger picture?", type: "N" },
            { question: "Do you like trying out new experiences rather than sticking to routines?", type: "J" },
            { question: "Do you enjoy working alone more than working in a team?", type: "I" },
            { question: "Do you prefer practical solutions rather than theoretical discussions?", type: "S" },
            { question: "Do you often make decisions quickly rather than weighing all options?", type: "F" },
            { question: "Do you prefer having a plan rather than being flexible?", type: "J" },
            { question: "Do you feel more comfortable in familiar situations rather than exploring the unknown?", type: "S" },
            { question: "Do you value personal relationships more than professional achievements?", type: "F" },
            { question: "Do you enjoy spontaneous activities rather than well-organized plans?", type: "P" }
        ];

        function loadQuestions() {
            const questionsDiv = document.getElementById("questions");
            questionsData.forEach((q, index) => {
                questionsDiv.innerHTML += `<div class='question'>
                    <p>${index + 1}. ${q.question}</p>
                    <label><input type='radio' name='q${index}' value='yes'> Yes</label>
                    <label><input type='radio' name='q${index}' value='no'> No</label>
                </div>`;
            });
        }

        function calculateMBTI() {
            let scores = { E: 0, I: 0, S: 0, N: 0, T: 0, F: 0, J: 0, P: 0 };
            let totalQuestions = questionsData.length;
            for (let i = 0; i < totalQuestions; i++) {
                let selected = document.querySelector(`input[name='q${i}']:checked`);
                if (!selected) {
                    alert("Please answer all questions before submitting.");
                    return;
                }
                if (selected.value === "yes") {
                    scores[questionsData[i].type]++;
                } else {
                    scores[questionsData[i].type === "E" ? "I" :
                        questionsData[i].type === "I" ? "E" :
                        questionsData[i].type === "S" ? "N" :
                        questionsData[i].type === "N" ? "S" :
                        questionsData[i].type === "T" ? "F" :
                        questionsData[i].type === "F" ? "T" :
                        questionsData[i].type === "J" ? "P" : "J"]++;
                }
            }

            let mbtiType = "";
            mbtiType += scores.E > scores.I ? "E" : "I";
            mbtiType += scores.S > scores.N ? "S" : "N";
            mbtiType += scores.T > scores.F ? "T" : "F";
            mbtiType += scores.J > scores.P ? "J" : "P";

            const descriptions = {
                "ISTJ": "ISTJs are responsible, organized, and practical. They value tradition and hard work.",
                "ISFJ": "ISFJs are nurturing, detail-oriented, and dependable. They prioritize harmony.",
                "INFJ": "INFJs are insightful, idealistic, and compassionate. They seek meaning in life.",
                "INTJ": "INTJs are strategic, independent, and driven. They love planning and problem-solving.",
                "ISTP": "ISTPs are analytical, adaptable, and practical. They enjoy hands-on work.",
                "ISFP": "ISFPs are artistic, sensitive, and spontaneous. They value personal freedom.",
                "INFP": "INFPs are creative, introspective, and empathetic. They seek authenticity.",
                "INTP": "INTPs are curious, logical, and innovative. They enjoy deep intellectual discussions.",
                "ESTP": "ESTPs are energetic, social, and action-oriented. They thrive in fast-paced environments.",
                "ESFP": "ESFPs are fun-loving, enthusiastic, and spontaneous. They love new experiences.",
                "ENFP": "ENFPs are imaginative, enthusiastic, and people-oriented. They value creativity.",
                "ENTP": "ENTPs are witty, bold, and curious. They love debating and exploring new ideas.",
                "ESTJ": "ESTJs are practical, efficient, and decisive. They enjoy structure and leadership.",
                "ESFJ": "ESFJs are warm, responsible, and social. They prioritize relationships.",
                "ENFJ": "ENFJs are charismatic, empathetic, and inspiring. They are natural leaders.",
                "ENTJ": "ENTJs are ambitious, strategic, and goal-oriented. They excel at leadership."
            };

            document.getElementById("result").innerHTML = `Your MBTI Type: ${mbtiType}<br>${descriptions[mbtiType]}`;
        }

        window.onload = loadQuestions;
    </script>
</body>
</html>
