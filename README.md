# Mbti-
这个网页测试简单的mbti
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MBTI 性格测试</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #6a11cb, #2575fc);
            color: white;
            text-align: center;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            margin: auto;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
        }
        .question {
            margin-bottom: 15px;
            text-align: left;
        }
        label {
            display: block;
            padding: 5px;
        }
        button {
            background: #ffcc00;
            color: #333;
            padding: 10px;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
            width: 100%;
        }
        button:hover {
            background: #ffaa00;
        }
        #result {
            font-size: 24px;
            font-weight: bold;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>MBTI 性格测试</h2>
        <form id="mbtiForm">
            <div id="questions"></div>
            <button type="button" onclick="calculateMBTI()">提交测试</button>
        </form>
        <p id="result"></p>
    </div>

    <script>
        const questions = [
            "我喜欢在人多的环境中待着，而不是独处。",
            "我更倾向于和别人分享我的想法，而不是自己思考。",
            "我在新环境中很快能适应并结交朋友，而不是慢慢适应。",
            "我更喜欢讨论话题时大声表达，而不是静静地听别人说。",
            "我觉得周末的聚会比一个人在家更有趣。",
            "我愿意主动认识陌生人，而不是等别人来接近我。",
            "我倾向于在行动中思考，而不是事先做好计划。",
            "在学习或工作时，我喜欢和别人一起完成任务，而不是单独完成。",
            "我在社交场合中更容易感到兴奋，而不是疲惫。",
            "我觉得与人交谈比自己思考更能帮助我理解事物。",
            "我倾向于关注现实和具体细节，而不是未来的可能性。",
            "我更喜欢依靠逻辑和事实，而不是情感来做决定。",
            "我倾向于遵守既定规则，而不是灵活应变。",
            "我喜欢按计划行事，而不是随意调整安排。",
            "我更愿意听取别人的意见，而不是完全依赖自己的判断。",
            "我在面对压力时更倾向于冷静分析，而不是情绪化反应。",
            "我喜欢探索新思想，而不是遵循传统。",
            "我倾向于相信科学和数据，而不是个人直觉。",
            "我更容易接受新变化，而不是坚持旧习惯。",
            "我更喜欢独立完成任务，而不是依赖团队合作。"
        ];

        const mbtiDescriptions = {
            "ISTJ": "ISTJ（物流师）是可靠且有条理的人，注重细节，擅长遵循规则和执行计划。",
            "ISFJ": "ISFJ（守护者）温暖、体贴，对责任感极强，喜欢帮助他人，维护和谐环境。",
            "INFJ": "INFJ（提倡者）理想主义者，具有深刻洞察力，擅长帮助和激励他人。",
            "INTJ": "INTJ（策划者）有远见，逻辑性强，喜欢制定战略和解决复杂问题。",
            "ISTP": "ISTP（鉴赏家）务实、独立，喜欢探索和亲自动手解决问题。",
            "ISFP": "ISFP（探险家）感性、热爱自由，擅长用创造力表达自己。",
            "INFP": "INFP（调停者）富有想象力和同理心，追求个人价值观和理想。",
            "INTP": "INTP（逻辑学家）聪明、好奇，擅长分析问题，探索新理论。",
            "ESTP": "ESTP（企业家）充满活力，爱冒险，擅长快速决策和应对挑战。",
            "ESFP": "ESFP（表演者）热情开朗，喜欢社交，享受当下的快乐。",
            "ENFP": "ENFP（竞选者）富有创造力，充满激情，擅长激励和启发他人。",
            "ENTP": "ENTP（辩论家）聪明风趣，喜欢挑战传统观点，善于讨论和创新。",
            "ESTJ": "ESTJ（总经理）果断务实，擅长组织管理，确保事情按计划进行。",
            "ESFJ": "ESFJ（执政官）友善热情，喜欢帮助他人并维护社交关系。",
            "ENFJ": "ENFJ（主人公）善于激励他人，具有领导能力，追求积极变革。",
            "ENTJ": "ENTJ（指挥官）自信、果断，擅长战略规划，推动团队目标实现。"
        };

        function generateQuestions() {
            const questionContainer = document.getElementById("questions");
            questionContainer.innerHTML = "";
            questions.forEach((q, index) => {
                const div = document.createElement("div");
                div.className = "question";
                div.innerHTML = `
                    <p>${index + 1}. ${q}</p>
                    <label><input type="radio" name="q${index}" value="E"> 是</label>
                    <label><input type="radio" name="q${index}" value="I"> 否</label>
                `;
                questionContainer.appendChild(div);
            });
        }

        function calculateMBTI() {
            let type = "ENFP"; // 这里应根据回答计算 MBTI
            document.getElementById("result").innerText = `您的 MBTI 类型是 ${type}。\n${mbtiDescriptions[type]}`;
        }

        window.onload = generateQuestions;
    </script>
</body>
</html>
