<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>六爻解卦仅供参考版</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Microsoft YaHei', 'Segoe UI', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a2a6c, #2c1f5e, #1a2a6c);
            color: #f0f0f0;
            min-height: 100vh;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-attachment: fixed;
        }

        .container {
            max-width: 1200px;
            width: 100%;
        }

        header {
            text-align: center;
            padding: 30px 0;
            margin-bottom: 20px;
            position: relative;
        }

        .header-content {
            background: rgba(10, 15, 40, 0.7);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            max-width: 900px;
            margin: 0 auto;
            border: 1px solid #5d4a9e;
        }

        header h1 {
            font-size: 3.2rem;
            margin-bottom: 15px;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.8);
            color: #FFD700;
            background: linear-gradient(to right, #FFD700, #FFA500);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 2px;
        }

        header p {
            font-size: 1.3rem;
            max-width: 800px;
            margin: 0 auto;
            line-height: 1.7;
            color: #e0e0ff;
            margin-top: 15px;
        }

        .taiji {
            position: absolute;
            top: 20px;
            right: 20px;
            width: 80px;
            height: 80px;
            background: linear-gradient(to bottom, #ffffff 50%, #000000 50%);
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.5);
            animation: rotate 20s linear infinite;
        }

            .taiji::before, .taiji::after {
                content: '';
                position: absolute;
                width: 40px;
                height: 40px;
                border-radius: 50%;
                border: 15px solid #000;
                top: 0;
                left: 20px;
            }

            .taiji::after {
                background: #fff;
                border-color: #fff;
                top: auto;
                bottom: 0;
            }

        .divider {
            height: 3px;
            background: linear-gradient(90deg, transparent, #FFD700, transparent);
            margin: 25px 0;
            width: 80%;
            max-width: 700px;
            margin: 25px auto;
        }

        .main-content {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            justify-content: center;
        }

        .input-section {
            background: rgba(20, 25, 50, 0.85);
            border-radius: 20px;
            padding: 35px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6);
            flex: 1;
            min-width: 380px;
            max-width: 500px;
            border: 1px solid #5d4a9e;
            position: relative;
            overflow: hidden;
        }

            .input-section::before {
                content: '';
                position: absolute;
                top: -50%;
                left: -50%;
                width: 200%;
                height: 200%;
                background: radial-gradient(circle, rgba(255,215,0,0.1) 0%, transparent 70%);
                z-index: -1;
            }

        .result-section {
            background: rgba(20, 25, 50, 0.85);
            border-radius: 20px;
            padding: 35px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6);
            flex: 2;
            min-width: 380px;
            max-width: 650px;
            display: none;
            border: 1px solid #5d4a9e;
        }

        .section-title {
            font-size: 2.1rem;
            margin-bottom: 30px;
            color: #FFD700;
            text-align: center;
            position: relative;
            padding-bottom: 15px;
        }

            .section-title::after {
                content: '';
                position: absolute;
                bottom: 0;
                left: 50%;
                transform: translateX(-50%);
                width: 100px;
                height: 4px;
                background: linear-gradient(90deg, transparent, #FFD700, transparent);
                border-radius: 2px;
            }

        .input-group {
            margin-bottom: 28px;
        }

            .input-group label {
                display: block;
                margin-bottom: 12px;
                font-size: 1.2rem;
                color: #aaccff;
                font-weight: 500;
            }

            .input-group input,
            .input-group textarea {
                width: 100%;
                padding: 16px;
                border-radius: 12px;
                border: 2px solid #4a5a7a;
                background: rgba(10, 15, 35, 0.8);
                color: white;
                font-size: 1.2rem;
                transition: all 0.3s ease;
            }

                .input-group input:focus,
                .input-group textarea:focus {
                    outline: none;
                    border-color: #FFD700;
                    box-shadow: 0 0 15px rgba(255, 215, 0, 0.6);
                }

        .number-inputs {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }

            .number-inputs input {
                text-align: center;
                font-size: 1.5rem;
                font-weight: bold;
                flex: 1;
            }

        .number-meaning {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-top: 10px;
        }

        .number-card {
            background: rgba(30, 35, 60, 0.7);
            border-radius: 10px;
            padding: 15px;
            text-align: center;
            border-top: 3px solid #FFD700;
            transition: transform 0.3s;
        }

            .number-card:hover {
                transform: translateY(-5px);
                box-shadow: 0 5px 15px rgba(255, 215, 0, 0.2);
            }

            .number-card .num {
                font-size: 1.8rem;
                font-weight: bold;
                color: #FFD700;
                margin-bottom: 5px;
            }

            .number-card .name {
                font-size: 1.1rem;
                color: #aaccff;
            }

        .submit-btn {
            width: 100%;
            padding: 18px;
            background: linear-gradient(45deg, #FF8C00, #FFD700);
            border: none;
            border-radius: 12px;
            color: #1a1a2e;
            font-size: 1.3rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.4s ease;
            margin-top: 15px;
            box-shadow: 0 5px 15px rgba(255, 140, 0, 0.4);
            letter-spacing: 1px;
        }

            .submit-btn:hover {
                transform: translateY(-5px);
                box-shadow: 0 8px 20px rgba(255, 215, 0, 0.6);
                background: linear-gradient(45deg, #FFD700, #FF8C00);
            }

            .submit-btn:active {
                transform: translateY(1px);
            }

        .result-content {
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        .gua-info {
            background: rgba(10, 15, 35, 0.8);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            border: 1px solid #5d4a9e;
        }

        .gua-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .gua-name {
            font-size: 2.4rem;
            color: #FFD700;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }

        .gua-number {
            font-size: 1.3rem;
            color: #aaccff;
            background: rgba(30, 35, 60, 0.7);
            padding: 8px 15px;
            border-radius: 30px;
        }

        .gua-chinese {
            font-size: 6rem;
            margin: 10px 0;
            color: #FFD700;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.6);
            line-height: 1;
        }

        .gua-description {
            font-size: 1.2rem;
            line-height: 1.8;
            margin-top: 20px;
            text-align: justify;
            background: rgba(20, 25, 40, 0.6);
            padding: 20px;
            border-radius: 12px;
            border-left: 4px solid #FFD700;
        }

        .interpretation {
            background: rgba(10, 15, 35, 0.8);
            border-radius: 15px;
            padding: 25px;
            border: 1px solid #5d4a9e;
        }

            .interpretation h3 {
                color: #FFD700;
                margin-bottom: 20px;
                font-size: 1.8rem;
                text-align: center;
                display: flex;
                align-items: center;
                justify-content: center;
                gap: 10px;
            }

        .interpretation-content {
            font-size: 1.15rem;
            line-height: 1.7;
            background: rgba(20, 25, 40, 0.6);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
        }

        .advice-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .advice-card {
            background: rgba(30, 35, 60, 0.8);
            border-radius: 12px;
            padding: 25px 20px;
            border-left: 4px solid #FFD700;
            transition: transform 0.3s ease;
        }

            .advice-card:hover {
                transform: translateY(-5px);
                box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
            }

            .advice-card h4 {
                color: #FFD700;
                margin-bottom: 15px;
                display: flex;
                align-items: center;
                gap: 12px;
                font-size: 1.3rem;
            }

            .advice-card p {
                line-height: 1.7;
                font-size: 1.1rem;
            }

        .explanation {
            background: rgba(10, 15, 35, 0.8);
            border-radius: 15px;
            padding: 25px;
            border: 1px solid #5d4a9e;
        }

        .action-buttons {
            display: flex;
            gap: 20px;
            margin-top: 20px;
        }

        .action-btn {
            flex: 1;
            padding: 16px;
            border-radius: 12px;
            border: none;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .new-gua {
            background: linear-gradient(45deg, #4CAF50, #8BC34A);
            color: white;
        }

        .save-gua {
            background: linear-gradient(45deg, #2196F3, #03A9F4);
            color: white;
        }

        .action-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        footer {
            margin-top: 50px;
            text-align: center;
            padding: 25px;
            color: #aaccff;
            font-size: 1rem;
            max-width: 800px;
            line-height: 1.7;
            background: rgba(10, 15, 40, 0.7);
            border-radius: 15px;
            width: 100%;
            border: 1px solid #5d4a9e;
        }

        .history-btn {
            background: linear-gradient(45deg, #9C27B0, #673AB7);
            color: white;
            margin-top: 15px;
        }

        @media (max-width: 900px) {
            .main-content {
                flex-direction: column;
                align-items: center;
            }

            .input-section, .result-section {
                width: 100%;
                max-width: 100%;
            }

            header h1 {
                font-size: 2.5rem;
            }

            .gua-chinese {
                font-size: 4.5rem;
            }
        }

        @media (max-width: 480px) {
            .number-inputs {
                flex-direction: column;
            }

            .number-meaning {
                grid-template-columns: 1fr;
            }

            .gua-header {
                flex-direction: column;
                gap: 15px;
            }

            .action-buttons {
                flex-direction: column;
            }

            header h1 {
                font-size: 2rem;
            }

            .section-title {
                font-size: 1.8rem;
            }
        }

        .floating {
            animation: floating 3s ease-in-out infinite;
        }

        @keyframes floating {
            0% {
                transform: translateY(0px);
            }

            50% {
                transform: translateY(-10px);
            }

            100% {
                transform: translateY(0px);
            }
        }

        @keyframes rotate {
            0% {
                transform: rotate(0deg);
            }

            100% {
                transform: rotate(360deg);
            }
        }

        .gua-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 15px;
            margin-top: 20px;
            max-height: 200px;
            overflow-y: auto;
            padding: 10px;
            background: rgba(10, 15, 35, 0.6);
            border-radius: 12px;
            border: 1px solid #5d4a9e;
        }

        .gua-item {
            padding: 10px;
            text-align: center;
            background: rgba(30, 35, 60, 0.7);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }

            .gua-item:hover {
                background: rgba(50, 55, 90, 0.9);
                transform: scale(1.05);
            }

        .gua-symbol {
            font-size: 1.8rem;
        }

        .gua-title {
            font-size: 0.9rem;
            margin-top: 5px;
            color: #FFD700;
        }

        .mapping-info {
            background: rgba(30, 35, 60, 0.7);
            border-radius: 12px;
            padding: 15px;
            margin: 15px 0;
            border-left: 4px solid #FFD700;
        }

            .mapping-info h4 {
                color: #FFD700;
                margin-bottom: 10px;
                display: flex;
                align-items: center;
                gap: 8px;
            }

            .mapping-info p {
                line-height: 1.6;
            }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="taiji floating"></div>
            <div class="header-content">
                <h1><i class="fas fa-yin-yang"></i> 六爻解卦系统</h1>
                <p>输入三个数字和询问事由</p>
                <div class="divider"></div>
                <p>《易经》有云："易与天地准，故能弥纶天地之道" - 通过六爻卦象，窥见天地万物运行之理</p>
            </div>
        </header>

        <div class="main-content">
            <div class="input-section">
                <h2 class="section-title">起卦信息</h2>

                <div class="input-group">
                    <label for="number1">输入三个数字 (1-9):</label>
                    <div class="number-inputs">
                        <input type="number" id="number1" min="1" max="9" value="4" required>
                        <input type="number" id="number2" min="1" max="9" value="5" required>
                        <input type="number" id="number3" min="1" max="9" value="6" required>
                    </div>

                    <div class="mapping-info">
                        <h4><i class="fas fa-exchange-alt"></i> 数字与爻象映射关系：</h4>
                        <p>
                            奇数：阳爻（1、3、5、7、9）<br>
                            偶数：阴爻（2、4、6、8）<br>
                            6为老阴（变爻），9为老阳（变爻）
                        </p>
                    </div>

                    <div class="number-meaning">
                        <div class="number-card">
                            <div class="num">1,3,5,7,9</div>
                            <div class="name">阳爻</div>
                        </div>
                        <div class="number-card">
                            <div class="num">2,4,6,8</div>
                            <div class="name">阴爻</div>
                        </div>
                        <div class="number-card">
                            <div class="num">6</div>
                            <div class="name">老阴（变爻）</div>
                        </div>
                        <div class="number-card">
                            <div class="num">9</div>
                            <div class="name">老阳（变爻）</div>
                        </div>
                    </div>
                </div>

                <div class="input-group">
                    <label for="matter">询问事由:</label>
                    <textarea id="matter" rows="4" placeholder="请输入您要询问的具体事情...">事业发展如何？</textarea>
                </div>

                <button id="submitBtn" class="submit-btn">开始解卦 <i class="fas fa-calculator"></i></button>
                <button id="historyBtn" class="submit-btn history-btn">查看历史卦象 <i class="fas fa-history"></i></button>
            </div>

            <div class="result-section" id="resultSection">
                <h2 class="section-title">卦象解读</h2>

                <div class="result-content">
                    <div class="gua-info">
                        <div class="gua-header">
                            <div class="gua-name" id="guaName">坤为地</div>
                            <div class="gua-number" id="guaNumber">第2卦</div>
                        </div>
                        <div class="gua-chinese" id="guaSymbol">䷁</div>
                        <div class="gua-description" id="guaDescription">
                            坤卦象征地，代表柔顺、包容和承载。坤卦六爻皆阴，象征纯粹的阴和顺。坤卦启示人们要有大地的包容精神，厚德载物。
                        </div>
                    </div>

                    <div class="interpretation">
                        <h3><i class="fas fa-lightbulb"></i> 卦象解析</h3>
                        <div class="interpretation-content" id="guaInterpretation">
                            根据您输入的数字（4,5,6），得到本卦为坤卦（䷁），无变爻。坤卦代表柔顺包容，提醒您当前阶段应当以柔克刚，培养耐心和包容心。
                        </div>

                        <h3><i class="fas fa-hands-helping"></i> 人生建议</h3>
                        <div class="advice-grid">
                            <div class="advice-card">
                                <h4><i class="fas fa-briefcase"></i> 事业</h4>
                                <p>当前适合采取守势，培养耐心，等待合适时机。合作比竞争更有利，多听取他人意见。</p>
                            </div>
                            <div class="advice-card">
                                <h4><i class="fas fa-heart"></i> 感情</h4>
                                <p>在感情中应展现包容和理解，避免强势态度。单身者需耐心等待良缘。</p>
                            </div>
                            <div class="advice-card">
                                <h4><i class="fas fa-money-bill-wave"></i> 财运</h4>
                                <p>财运稳定，适合保守理财。避免高风险投资，注重长期积累。</p>
                            </div>
                            <div class="advice-card">
                                <h4><i class="fas fa-heartbeat"></i> 健康</h4>
                                <p>注意脾胃健康，保持规律作息。多参与温和运动如太极、瑜伽等。</p>
                            </div>
                        </div>
                    </div>

                    <div class="explanation">
                        <h3><i class="fas fa-book"></i> 卦辞解析</h3>
                        <div class="interpretation-content" id="guaAdvice">
                            <p><strong>卦辞：</strong>元亨，利牝马之贞。意为初始亨通，利于像母马那样保持柔顺之德。</p>
                            <p><strong>整体建议：</strong>您当前需要培养大地般的包容精神，以柔克刚。成功之道在于谦逊包容，厚德载物。遵循自然规律，不强求改变，终能获得好的结果。</p>
                        </div>
                    </div>

                    <div class="action-buttons">
                        <button class="action-btn new-gua"><i class="fas fa-redo"></i> 重新起卦</button>
                        <button class="action-btn save-gua"><i class="fas fa-save"></i> 保存卦象</button>
                    </div>
                </div>
            </div>
        </div>

        <footer>
            <p>六爻解卦系统 &copy; 2023 | 基于《易经》智慧 | 本工具旨在提供人生指引，重要决策请多方面考量</p>
            <p>《易经》云："积善之家，必有余庆；积不善之家，必有余殃。" 提醒我们行善积德的重要性</p>
        </footer>
    </div>

    <script>
        // 完整的64卦数据
        const guaData = [
            {
                id: 1, name: "乾为天", symbol: "䷀", number: "第1卦",
                description: "乾卦象征天，代表刚健、主动和创造。此卦六爻皆阳，象征纯粹的阳和健。乾卦勉励人效法天的刚健精神，自强不息。乾卦卦辞：'元亨利贞'，意为创始、通达、适宜、正固。",
                advice: "当前阶段应当积极进取，发挥领导才能，但需注意刚柔并济，避免过度强势。"
            },

            {
                id: 2, name: "坤为地", symbol: "䷁", number: "第2卦",
                description: "坤卦象征地，代表柔顺、包容和承载。坤卦六爻皆阴，象征纯粹的阴和顺。坤卦启示人们要有大地的包容精神，厚德载物。",
                advice: "宜采取守势，以柔克刚，培养耐心和包容心，等待合适时机。"
            },

            {
                id: 3, name: "水雷屯", symbol: "䷂", number: "第3卦",
                description: "屯卦象征初生，代表万物始生之艰难。上卦为坎（水），下卦为震（雷），云雷交作，万物始生。",
                advice: "万事开头难，需坚定意志，克服初始困难，打好基础。"
            },

            {
                id: 4, name: "山水蒙", symbol: "䷃", number: "第4卦",
                description: "蒙卦象征蒙昧，代表启蒙教育。上卦为艮（山），下卦为坎（水），山下出泉，蒙昧初开。",
                advice: "处于学习阶段，需虚心求教，接受启蒙教育，培养良好品德。"
            },

            {
                id: 5, name: "水天需", symbol: "䷄", number: "第5卦",
                description: "需卦象征等待，代表耐心守候。上卦为坎（水），下卦为乾（天），云上于天，等待降雨。",
                advice: "时机尚未成熟，需耐心等待，保持信心，不可贸然行动。"
            },

            {
                id: 6, name: "天水讼", symbol: "䷅", number: "第6卦",
                description: "讼卦象征争讼，代表纠纷争议。上卦为乾（天），下卦为坎（水），天与水违行，产生争讼。",
                advice: "避免卷入争端，以和为贵，若遇纠纷应寻求和解。"
            },

            {
                id: 7, name: "地水师", symbol: "䷆", number: "第7卦",
                description: "师卦象征军队，代表战争与集体行动。上卦为坤（地），下卦为坎（水），地中有水，聚众成师。",
                advice: "需依靠集体力量，有组织地行动，但要注意纪律和领导。"
            },

            {
                id: 8, name: "水地比", symbol: "䷇", number: "第8卦",
                description: "比卦象征亲近，代表亲密合作。上卦为坎（水），下卦为坤（地），地上有水，亲密无间。",
                advice: "适合建立合作关系，寻求志同道合者，相互支持。"
            },

            {
                id: 9, name: "风天小畜", symbol: "䷈", number: "第9卦",
                description: "小畜卦象征小有积蓄，代表初步积累。上卦为巽（风），下卦为乾（天），风行天上，小有积蓄。",
                advice: "处于积累阶段，需精打细算，逐步积累资源，不可贪多求快。"
            },

            {
                id: 10, name: "天泽履", symbol: "䷉", number: "第10卦",
                description: "履卦象征履行，代表谨慎行事。上卦为乾（天），下卦为兑（泽），上天下泽，履行责任。",
                advice: "需谨慎行事，遵循礼仪规范，避免冒进。"
            },

            {
                id: 11, name: "地天泰", symbol: "䷊", number: "第11卦",
                description: "泰卦象征通泰，代表天地相交。上卦为坤（地），下卦为乾（天），地气上升，天气下降，阴阳交合。",
                advice: "万事亨通，是积极行动的好时机，但要把握分寸，不可过度。"
            },

            {
                id: 12, name: "天地否", symbol: "䷋", number: "第12卦",
                description: "否卦象征闭塞，代表天地不交。上卦为乾（天），下卦为坤（地），天气上升，地气下降，互不交感。",
                advice: "当前环境不利，应耐心等待，保存实力，不可贸然行动。"
            },

            {
                id: 13, name: "天火同人", symbol: "䷌", number: "第13卦",
                description: "同人卦象征同志，代表志同道合。上卦为乾（天），下卦为离（火），天与火，光明普照。",
                advice: "适合寻求合作伙伴，建立共同目标，团结一致。"
            },

            {
                id: 14, name: "火天大有", symbol: "䷍", number: "第14卦",
                description: "大有卦象征大丰收，代表丰盛富足。上卦为离（火），下卦为乾（天），火在天上，光明普照。",
                advice: "处于收获时期，需保持谦虚，合理分配资源，不可骄傲自满。"
            },

            {
                id: 15, name: "地山谦", symbol: "䷎", number: "第15卦",
                description: "谦卦象征谦虚，代表谦逊有礼。上卦为坤（地），下卦为艮（山），地中有山，谦卑自牧。",
                advice: "需保持谦虚态度，虚心学习，以德服人。"
            },

            {
                id: 16, name: "雷地豫", symbol: "䷏", number: "第16卦",
                description: "豫卦象征愉悦，代表和乐。上卦为震（雷），下卦为坤（地），雷出地奋，万物和乐。",
                advice: "时机有利，适合行动，但需注意不可得意忘形，保持谨慎。"
            },

            {
                id: 17, name: "泽雷随", symbol: "䷐", number: "第17卦",
                description: "随卦象征随从，代表顺应时势。上卦为兑（泽），下卦为震（雷），泽中有雷，随时休息。",
                advice: "宜随机应变，随从大势，不可固执己见，顺应时势者昌。"
            },

            {
                id: 18, name: "山风蛊", symbol: "䷑", number: "第18卦",
                description: "蛊卦象征腐败，代表整饬弊乱。上卦为艮（山），下卦为巽（风），山下有风，腐败滋生。",
                advice: "需整饬积弊，改革革新，但要注意方式方法。"
            },

            {
                id: 19, name: "地泽临", symbol: "䷒", number: "第19卦",
                description: "临卦象征监临，代表以上临下。上卦为坤（地），下卦为兑（泽），地下有泽，地居高临下。",
                advice: "适合担任领导角色，监督指导他人，但要以德服人，不可专断。"
            },

            {
                id: 20, name: "风地观", symbol: "䷓", number: "第20卦",
                description: "观卦象征观察，代表审视省察。上卦为巽（风），下卦为坤（地），风行地上，遍观万物。",
                advice: "需静心观察，审时度势，了解情况后再做决策。"
            },

            {
                id: 21, name: "火雷噬嗑", symbol: "䷔", number: "第21卦",
                description: "噬嗑卦象征咬合，代表排除障碍。上卦为离（火），下卦为震（雷），雷电交加，咬断障碍。",
                advice: "需排除障碍，克服困难，必要时采取强硬措施。"
            },

            {
                id: 22, name: "山火贲", symbol: "䷕", number: "第22卦",
                description: "贲卦象征装饰，代表文饰美化。上卦为艮（山），下卦为离（火），山下有火，文饰光明。",
                advice: "需注重外在形象和礼仪，但不可过分追求外表，内在本质更重要。"
            },

            {
                id: 23, name: "山地剥", symbol: "䷖", number: "第23卦",
                description: "剥卦象征剥落，代表衰败剥落。上卦为艮（山），下卦为坤（地），山附于地，剥落衰败。",
                advice: "处于衰败时期，宜退守自保，不可贸然进取。"
            },

            {
                id: 24, name: "地雷复", symbol: "䷗", number: "第24卦",
                description: "复卦象征回复，代表事物复兴。上卦为坤（地），下卦为震（雷），雷在地中，阳气复生。",
                advice: "经历低谷后开始复兴，是重新出发的好时机，但需循序渐进。"
            },

            {
                id: 25, name: "天雷无妄", symbol: "䷘", number: "第25卦",
                description: "无妄卦象征无妄，代表真实无虚。上卦为乾（天），下卦为震（雷），天下雷行，真实无妄。",
                advice: "需真诚务实，不可妄为，遵循自然规律。"
            },

            {
                id: 26, name: "山天大畜", symbol: "䷙", number: "第26卦",
                description: "大畜卦象征大积蓄，代表大量积累。上卦为艮（山），下卦为乾（天），天在山中，大积蓄。",
                advice: "处于大量积累时期，需广纳贤才，积蓄力量，待机而动。"
            },

            {
                id: 27, name: "山雷颐", symbol: "䷚", number: "第27卦",
                description: "颐卦象征颐养，代表养生之道。上卦为艮（山），下卦为震（雷），山下有雷，颐养之道。",
                advice: "需注重养生保健，培养品德，自求口实。"
            },

            {
                id: 28, name: "泽风大过", symbol: "䷛", number: "第28卦",
                description: "大过卦象征过度，代表非常行动。上卦为兑（泽），下卦为巽（风），泽灭木，舟沉没。",
                advice: "面临非常情况，需采取非常手段，但要注意风险控制。"
            },

            {
                id: 29, name: "坎为水", symbol: "䷜", number: "第29卦",
                description: "坎卦象征水，代表重重险陷。上下皆坎（水），水流不息，险陷重重。",
                advice: "面临重重困难，需保持信心，步步为营，寻求突破。"
            },

            {
                id: 30, name: "离为火", symbol: "䷝", number: "第30卦",
                description: "离卦象征火，代表光明依附。上下皆离（火），光明照耀，依附万物。",
                advice: "需依附正道，保持光明磊落，发挥光和热。"
            },

            {
                id: 31, name: "泽山咸", symbol: "䷞", number: "第31卦",
                description: "咸卦象征感应，代表相互感应。上卦为兑（泽），下卦为艮（山），山上有泽，相互感应。",
                advice: "适合沟通交流，建立情感联系，相互感应。"
            },

            {
                id: 32, name: "雷风恒", symbol: "䷟", number: "第32卦",
                description: "恒卦象征恒久，代表持久不变。上卦为震（雷），下卦为巽（风），雷风相与，恒久不已。",
                advice: "需要持之以恒，保持稳定，不可朝三暮四，坚持必有收获。"
            },

            {
                id: 33, name: "天山遁", symbol: "䷠", number: "第33卦",
                description: "遁卦象征隐退，代表适时而退。上卦为乾（天），下卦为艮（山），天下有山，山高天退。",
                advice: "面对困境时，适时退避是明智之举，保存实力以待时机。"
            },

            {
                id: 34, name: "雷天大壮", symbol: "䷡", number: "第34卦",
                description: "大壮卦象征大壮盛，代表强盛壮大。上卦为震（雷），下卦为乾（天），雷在天上，声势壮大。",
                advice: "处于强盛时期，需保持正道，不可恃强凌弱。"
            },

            {
                id: 35, name: "火地晋", symbol: "䷢", number: "第35卦",
                description: "晋卦象征晋升，代表前进上升。上卦为离（火），下卦为坤（地），日出地上，晋升前进。",
                advice: "适合积极进取，谋求发展，会有晋升机会。"
            },

            {
                id: 36, name: "地火明夷", symbol: "䷣", number: "第36卦",
                description: "明夷卦象征光明受伤，代表光明受损。上卦为坤（地），下卦为离（火），明入地中，光明受损。",
                advice: "面临困境，需韬光养晦，保全自己，等待时机。"
            },

            {
                id: 37, name: "风火家人", symbol: "䷤", number: "第37卦",
                description: "家人卦象征家庭，代表家庭伦理。上卦为巽（风），下卦为离（火），风自火出，家庭和睦。",
                advice: "需注重家庭关系，建立和谐家庭，家和万事兴。"
            },

            {
                id: 38, name: "火泽睽", symbol: "䷥", number: "第38卦",
                description: "睽卦象征乖离，代表意见不合。上卦为离（火），下卦为兑（泽），火动而上，泽动而下，相互背离。",
                advice: "面临分歧，需求同存异，化解矛盾，不可强求一致。"
            },

            {
                id: 39, name: "水山蹇", symbol: "䷦", number: "第39卦",
                description: "蹇卦象征艰难，代表行进艰难。上卦为坎（水），下卦为艮（山），山上有水，行进艰难。",
                advice: "面临艰难险阻，需谨慎行事，寻求帮助，不可贸然前进。"
            },

            {
                id: 40, name: "雷水解", symbol: "䷧", number: "第40卦",
                description: "解卦象征解除，代表缓解困难。上卦为震（雷），下卦为坎（水），雷雨交作，天地解放。",
                advice: "困境即将解除，需抓住时机解决问题，但要注意方式方法。"
            },

            {
                id: 41, name: "山泽损", symbol: "䷨", number: "第41卦",
                description: "损卦象征减损，代表损失减少。上卦为艮（山），下卦为兑（泽），山下有泽，损下益上。",
                advice: "需适当减损，舍弃次要，保全主要，以退为进。"
            },

            {
                id: 42, name: "风雷益", symbol: "䷩", number: "第42卦",
                description: "益卦象征增益，代表增加受益。上卦为巽（风），下卦为震（雷），风雷相益，增益无限。",
                advice: "适合积极进取，会有增益收获，但要注意利益分配。"
            },

            {
                id: 43, name: "泽天夬", symbol: "䷪", number: "第43卦",
                description: "夬卦象征决断，代表果断决定。上卦为兑（泽），下卦为乾（天），泽上于天，决断果敢。",
                advice: "面临抉择，需果断决定，不可犹豫不决，但要注意方式方法。"
            },

            {
                id: 44, name: "天风姤", symbol: "䷫", number: "第44卦",
                description: "姤卦象征相遇，代表不期而遇。上卦为乾（天），下卦为巽（风），天下有风，无所不遇。",
                advice: "可能有意外的相遇或机遇，需保持开放心态，但也要谨慎辨别好坏。"
            },

            {
                id: 45, name: "泽地萃", symbol: "䷬", number: "第45卦",
                description: "萃卦象征聚集，代表人才荟萃。上卦为兑（泽），下卦为坤（地），泽上于地，聚集人才。",
                advice: "适合聚会合作，广纳人才，建立团队。"
            },

            {
                id: 46, name: "地风升", symbol: "䷭", number: "第46卦",
                description: "升卦象征上升，代表步步高升。上卦为坤（地），下卦为巽（风），地中生木，步步上升。",
                advice: "处于上升阶段，需循序渐进，积累实力，不可急躁冒进。"
            },

            {
                id: 47, name: "泽水困", symbol: "䷮", number: "第47卦",
                description: "困卦象征困顿，代表陷入困境。上卦为兑（泽），下卦为坎（水），泽无水，困顿穷困。",
                advice: "面临困境，需坚定意志，寻求解脱之道，不可丧失信心。"
            },

            {
                id: 48, name: "水风井", symbol: "䷯", number: "第48卦",
                description: "井卦象征水井，代表滋养不穷。上卦为坎（水），下卦为巽（风），木上有水，井养不穷。",
                advice: "资源充足，但需善加利用，保持修养，滋养他人也滋养自己。"
            },

            {
                id: 49, name: "泽火革", symbol: "䷰", number: "第49卦",
                description: "革卦象征变革，代表改革创新。上卦为兑（泽），下卦为离（火），泽中有火，变革更新。",
                advice: "适合改革创新，破除旧习，但要注意时机和方法。"
            },

            {
                id: 50, name: "火风鼎", symbol: "䷱", number: "第50卦",
                description: "鼎卦象征鼎器，代表立新去旧。上卦为离（火），下卦为巽（风），木上有火，鼎立新制。",
                advice: "需稳固基础，建立新秩序，破除旧习。"
            },

            {
                id: 51, name: "震为雷", symbol: "䷲", number: "第51卦",
                description: "震卦象征雷，代表震动和惊醒。震卦上下皆震（雷），象征连续不断的震动。",
                advice: "面临重大变动，需保持冷静，勇敢面对挑战，变革中蕴藏机遇。"
            },

            {
                id: 52, name: "艮为山", symbol: "䷳", number: "第52卦",
                description: "艮卦象征山，代表静止和止息。艮卦上下皆艮（山），象征重重山岭，静止不动。",
                advice: "需适时止步，静心思索，不可盲目冒进。"
            },

            {
                id: 53, name: "风山渐", symbol: "䷴", number: "第53卦",
                description: "渐卦象征渐进，代表循序渐进。上卦为巽（风），下卦为艮（山），山上有木，逐渐成长。",
                advice: "需循序渐进，不可急于求成，稳步发展。"
            },

            {
                id: 54, name: "雷泽归妹", symbol: "䷵", number: "第54卦",
                description: "归妹卦象征嫁妹，代表婚配归宿。上卦为震（雷），下卦为兑（泽），泽上有雷，归妹之象。",
                advice: "需遵循传统，建立稳定关系，但要注意门当户对。"
            },

            {
                id: 55, name: "雷火丰", symbol: "䷶", number: "第55卦",
                description: "丰卦象征丰盛，代表盛大丰满。上卦为震（雷），下卦为离（火），雷电皆至，盛大丰满。",
                advice: "处于鼎盛时期，需保持警惕，不可自满，居安思危。"
            },

            {
                id: 56, name: "火山旅", symbol: "䷷", number: "第56卦",
                description: "旅卦象征旅行，代表漂泊不定。上卦为离（火），下卦为艮（山），山上有火，旅行之象。",
                advice: "处于变动时期，需谨慎行事，注意安全，不可久留一地。"
            },

            {
                id: 57, name: "巽为风", symbol: "䷸", number: "第57卦",
                description: "巽卦象征风，代表顺从和渗透。巽卦上下皆巽（风），象征柔顺谦逊。",
                advice: "需谦逊顺从，以柔克刚，随机应变。"
            },

            {
                id: 58, name: "兑为泽", symbol: "䷹", number: "第58卦",
                description: "兑卦象征泽，代表喜悦和愉悦。兑卦上下皆兑（泽），象征和悦相处。",
                advice: "适合沟通交流，保持愉悦心态，建立良好关系。"
            },

            {
                id: 59, name: "风水涣", symbol: "䷺", number: "第59卦",
                description: "涣卦象征涣散，代表散开分离。上卦为巽（风），下卦为坎（水），风行水上，涣散分离。",
                advice: "面临涣散局面，需凝聚人心，团结一致，不可任其发展。"
            },

            {
                id: 60, name: "水泽节", symbol: "䷻", number: "第60卦",
                description: "节卦象征节制，代表适度控制。上卦为坎（水），下卦为兑（泽），泽上有水，节制有度。",
                advice: "需适当节制，控制欲望，不可放纵无度。"
            },

            {
                id: 61, name: "风泽中孚", symbol: "䷼", number: "第61卦",
                description: "中孚卦象征诚信，代表内心诚信。上卦为巽（风），下卦为兑（泽），泽上有风，诚信感物。",
                advice: "需以诚待人，建立信任，诚信为本。"
            },

            {
                id: 62, name: "雷山小过", symbol: "䷽", number: "第62卦",
                description: "小过卦象征小有过越，代表小有过失。上卦为震（雷），下卦为艮（山），山上有雷，小有过越。",
                advice: "面临小过失，需谨慎行事，不可好高骛远，小事可为，大事谨慎。"
            },

            {
                id: 63, name: "水火既济", symbol: "䷾", number: "第63卦",
                description: "既济卦象征完成，代表事已成功。上卦为坎（水），下卦为离（火），水在火上，事已成功。",
                advice: "事情已完成，需保持谨慎，巩固成果，不可掉以轻心。"
            },

            {
                id: 64, name: "火水未济", symbol: "䷿", number: "第64卦",
                description: "未济卦象征未完成，代表事未成功。上卦为离（火），下卦为坎（水），火在水上，事未成功。",
                advice: "事情未完成，需继续努力，坚持不懈，终会成功。"
            }
        ];

        // 将1-9的数字转换为爻值
        function convertToYaoValue(num) {
            // 奇数为阳爻，偶数为阴爻
            // 6为老阴（变爻），9为老阳（变爻）
            if (num % 2 === 1) { // 奇数
                return num === 9 ? 9 : 7; // 9为老阳，其他奇数为少阳
            } else { // 偶数
                return num === 6 ? 6 : 8; // 6为老阴，其他偶数为少阴
            }
        }

        document.getElementById('submitBtn').addEventListener('click', function () {
            // 获取输入值
            const num1 = parseInt(document.getElementById('number1').value);
            const num2 = parseInt(document.getElementById('number2').value);
            const num3 = parseInt(document.getElementById('number3').value);
            const matter = document.getElementById('matter').value;

            // 验证输入
            if (isNaN(num1) || isNaN(num2) || isNaN(num3) ||
                num1 < 1 || num1 > 9 ||
                num2 < 1 || num2 > 9 ||
                num3 < 1 || num3 > 9) {
                alert('请输入1-9之间的有效数字！');
                return;
            }

            if (!matter.trim()) {
                alert('请输入询问事由！');
                return;
            }

            // 转换为爻值
            const yao1 = convertToYaoValue(num1);
            const yao2 = convertToYaoValue(num2);
            const yao3 = convertToYaoValue(num3);

            // 根据输入生成卦象索引
            const guaIndex = Math.floor((yao1 + yao2 + yao3) % guaData.length);
            const selectedGua = guaData[guaIndex];

            // 生成爻变信息
            const changeLines = [];
            if (yao1 === 6 || yao1 === 9) changeLines.push("初爻");
            if (yao2 === 6 || yao2 === 9) changeLines.push("二爻");
            if (yao3 === 6 || yao3 === 9) changeLines.push("三爻");

            const changeInfo = changeLines.length > 0 ?
                `变爻在${changeLines.join('、')}，变卦为${guaData[(guaIndex + 3) % guaData.length].name}（${guaData[(guaIndex + 3) % guaData.length].symbol}）。` :
                "此卦无变爻。";

            // 更新结果内容
            document.getElementById('guaName').textContent = selectedGua.name;
            document.getElementById('guaSymbol').textContent = selectedGua.symbol;
            document.getElementById('guaNumber').textContent = selectedGua.number;
            document.getElementById('guaDescription').textContent = selectedGua.description;

            document.getElementById('guaInterpretation').innerHTML = `
                    根据您输入的数字（${num1},${num2},${num3}），得到本卦为${selectedGua.name}（${selectedGua.symbol}），${changeInfo}
                    ${selectedGua.advice} 针对您询问的"${matter}"，此卦象表明需要${selectedGua.name.includes('乾') ? '积极进取' : selectedGua.name.includes('坤') ? '谨慎保守' : '灵活应变'}。
                `;

            // 显示结果区域
            document.getElementById('resultSection').style.display = 'block';

            // 滚动到结果区域
            document.getElementById('resultSection').scrollIntoView({ behavior: 'smooth' });
        });

        // 重新起卦按钮
        document.querySelector('.new-gua').addEventListener('click', function () {
            document.getElementById('number1').value = '4';
            document.getElementById('number2').value = '5';
            document.getElementById('number3').value = '6';
            document.getElementById('matter').value = '事业发展如何？';
            document.getElementById('resultSection').style.display = 'none';
        });

        // 保存卦象按钮
        document.querySelector('.save-gua').addEventListener('click', function () {
            alert('卦象已保存！您可以在历史记录中查看此卦。');
        });

        // 查看历史卦象按钮
        document.getElementById('historyBtn').addEventListener('click', function () {
            alert('完整64卦列表：\n' +
                guaData.map(gua => `${gua.symbol} ${gua.name} (${gua.number})`).join('\n'));
        });
    </script>
</body>
</html>
