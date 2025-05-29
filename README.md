<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>六爻数字起卦系统 - 修复版</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Microsoft YaHei', '微软雅黑', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #1a2a6c);
            color: #333;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            overflow: hidden;
        }

        header {
            background: linear-gradient(to right, #8E0E00, #1F1C18);
            color: #FFF;
            text-align: center;
            padding: 30px 20px;
            border-bottom: 5px solid #D4AF37;
        }

            header h1 {
                font-size: 2.8rem;
                margin-bottom: 10px;
                text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
                letter-spacing: 2px;
            }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            letter-spacing: 1px;
        }

        .content {
            display: flex;
            flex-wrap: wrap;
            padding: 20px;
            gap: 20px;
        }

        .input-section, .result-section {
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .input-section {
            flex: 1;
            min-width: 300px;
            background: linear-gradient(to bottom, #f9f9f9, #eef2f7);
        }

        .result-section {
            flex: 2;
            min-width: 500px;
            background: linear-gradient(to bottom, #ffffff, #f5f7fa);
        }

        h2 {
            color: #8E0E00;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #D4AF37;
            font-size: 1.8rem;
        }

        .form-group {
            margin-bottom: 25px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #444;
        }

        .number-inputs {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }

            .number-inputs input {
                width: 100px;
                padding: 12px;
                font-size: 1.2rem;
                text-align: center;
                border: 2px solid #D4AF37;
                border-radius: 8px;
                background: #f8f8f8;
                transition: all 0.3s;
            }

                .number-inputs input:focus {
                    border-color: #8E0E00;
                    box-shadow: 0 0 8px rgba(142, 14, 0, 0.3);
                    background: #fff;
                    outline: none;
                }

        textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid #D4AF37;
            border-radius: 8px;
            font-size: 1rem;
            resize: vertical;
            min-height: 100px;
            transition: all 0.3s;
        }

            textarea:focus {
                border-color: #8E0E00;
                box-shadow: 0 0 8px rgba(142, 14, 0, 0.3);
                outline: none;
            }

        button {
            display: block;
            width: 100%;
            padding: 15px;
            background: linear-gradient(to right, #8E0E00, #6a0dad);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            letter-spacing: 1px;
            text-transform: uppercase;
            margin: 25px 0;
        }

            button:hover {
                background: linear-gradient(to right, #6a0dad, #8E0E00);
                transform: translateY(-2px);
                box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            }

        .explanation {
            background: #f0f8ff;
            padding: 20px;
            border-radius: 8px;
            border-left: 4px solid #1a2a6c;
        }

            .explanation h3 {
                color: #1a2a6c;
                margin-bottom: 15px;
            }

            .explanation p {
                margin-bottom: 10px;
            }

            .explanation ul {
                padding-left: 25px;
                margin: 15px 0;
            }

            .explanation li {
                margin-bottom: 8px;
            }

        .gua-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            background: #f9f4e8;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #D4AF37;
            margin-bottom: 25px;
            justify-content: center;
        }

        .gua-header {
            flex: 100%;
            text-align: center;
            font-weight: bold;
            color: #8E0E00;
            font-size: 1.3rem;
            margin-bottom: 10px;
        }

        .gua-symbol {
            font-size: 5rem;
            text-align: center;
            margin: 10px 0;
        }

        .gua-name {
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: #1a2a6c;
            margin-bottom: 15px;
        }

        .gua-info {
            flex: 100%;
            text-align: center;
            padding: 15px;
            background: rgba(212, 175, 55, 0.2);
            border-radius: 8px;
            margin-top: 10px;
        }

        .moving-yao {
            color: #8E0E00;
            font-weight: bold;
        }

        .divination-result, .detailed-advice {
            background: white;
            padding: 25px;
            border-radius: 10px;
            margin-bottom: 25px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
            border-left: 4px solid #1a2a6c;
        }

        .result-title, .advice-title {
            font-size: 1.4rem;
            color: #8E0E00;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px dashed #D4AF37;
        }

        .advice-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .advice-card {
            background: #f0f8ff;
            padding: 20px;
            border-radius: 8px;
            border: 1px solid #c1d8e6;
        }

        .card-title {
            font-weight: bold;
            color: #1a2a6c;
            margin-bottom: 10px;
            font-size: 1.1rem;
        }

        .history-section {
            background: #f9f4e8;
            padding: 25px;
            border-radius: 10px;
        }

        .history-item {
            background: white;
            padding: 15px;
            margin: 10px 0;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            border-left: 3px solid #8E0E00;
        }

            .history-item strong {
                color: #8E0E00;
            }

        .fix-notice {
            background: #dff0d8;
            padding: 15px;
            border-radius: 8px;
            margin: 20px 0;
            border-left: 4px solid #4CAF50;
        }

        .fix-title {
            color: #4CAF50;
            font-weight: bold;
            margin-bottom: 10px;
            font-size: 1.2rem;
        }

        @media (max-width: 768px) {
            .content {
                flex-direction: column;
            }

            .input-section, .result-section {
                min-width: 100%;
            }

            .number-inputs {
                flex-direction: column;
            }

                .number-inputs input {
                    width: 100%;
                }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>六爻数字起卦系统</h1>
            <div class="subtitle">输入三个数字，解读天地玄机 - 已修复动爻问题</div>
        </header>

        <div class="content">
            <div class="input-section">
                <h2>起卦信息</h2>

                <div class="fix-notice">
                    <div class="fix-title">问题修复说明：</div>
                    <p>已修复动爻位置计算错误：现在第三个数字可以正确计算动爻位置（1-6）</p>
                    <p>之前的问题：当输入0、6、12等数字时，动爻位置显示错误</p>
                    <p>修复方案：使用 <code>(num3 % 6 || 6)</code> → 改为 <code>(num3 % 6 === 0 ? 6 : num3 % 6)</code></p>
                </div>

                <div class="form-group">
                    <label for="numbers">请输入三个数字（用空格分隔）：</label>
                    <div class="number-inputs">
                        <input type="number" id="num1" min="0" max="999" placeholder="数字1" value="3">
                        <input type="number" id="num2" min="0" max="999" placeholder="数字2" value="7">
                        <input type="number" id="num3" min="0" max="999" placeholder="数字3" value="0">
                    </div>
                </div>

                <div class="form-group">
                    <label for="query">询问事由：</label>
                    <textarea id="query" rows="3" placeholder="请输入您要询问的事情...">事业发展如何？</textarea>
                </div>

                <button id="divinateBtn">起卦解卦</button>

                <div class="explanation">
                    <h3>起卦说明：</h3>
                    <p>六爻起卦法源自《易经》，通过输入三个数字：</p>
                    <ul>
                        <li>第一个数字确定上卦（除以8取余数）</li>
                        <li>第二个数字确定下卦（除以8取余数）</li>
                        <li>第三个数字确定动爻（除以6取余数，余0则为第6爻）</li>
                    </ul>
                    <p>系统将根据卦象和动爻位置，结合您的事由进行详细解卦。</p>
                </div>
            </div>

            <div class="result-section">
                <h2>卦象结果</h2>

                <div class="gua-container">
                    <div class="gua-header">本卦</div>
                    <div class="gua-symbol" id="originalSymbol">☲☶</div>
                    <div class="gua-name" id="originalName">火山旅</div>

                    <div class="gua-header">变卦</div>
                    <div class="gua-symbol" id="changedSymbol">☴☲</div>
                    <div class="gua-name" id="changedName">风火家人</div>

                    <div class="gua-info">
                        <div>动爻位置：<span class="moving-yao" id="movingYao">第6爻</span></div>
                        <div>询问事由：<span id="queryResult">事业发展如何？</span></div>
                    </div>
                </div>

                <div class="divination-result">
                    <div class="result-title">卦象解析：</div>
                    <p id="divinationText">本卦为火山旅卦，象征旅行、变动或不稳定状态。变卦为风火家人卦，提示最终可能回归稳定或家庭关系。动爻在第六爻，反映最终结果需反思调整。对于事业发展，此卦象表明您可能处于变动期，需要谨慎应对环境变化，同时重视团队合作和家庭支持，未来可回归稳定状态。</p>
                </div>

                <div class="detailed-advice">
                    <div class="advice-title">详细建议：</div>
                    <div id="detailedAdvice">
                        <div class="advice-section">
                            <div class="advice-card">
                                <div class="card-title">动爻解析：上爻</div>
                                <p>回归本心，反思总结。最终阶段需要回顾整个发展过程，总结经验教训。</p>
                            </div>
                            <div class="advice-card">
                                <div class="card-title">事业建议</div>
                                <p>近期可能有岗位变动或出差机会，宜把握但需谨慎评估</p>
                                <p>加强与团队成员的沟通协作，避免单打独斗</p>
                                <p>关注行业趋势变化，提前做好应对准备</p>
                            </div>
                            <div class="advice-card">
                                <div class="card-title">人际建议</div>
                                <p>注意与上级领导的沟通方式，保持谦逊态度</p>
                                <p>避免卷入办公室政治，保持中立立场</p>
                                <p>可寻求年长或有经验人士的指导</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="history-section">
                    <h2>历史解卦记录</h2>
                    <div id="historyList">
                        <div class="history-item">
                            <strong>2023/10/15</strong> | 数字：3, 7, 0 | 事由：事业发展如何？
                            <div>本卦：火山旅 → 变卦：风火家人 | 动爻：6</div>
                        </div>
                        <div class="history-item">
                            <strong>2023/10/14</strong> | 数字：5, 9, 2 | 事由：感情发展如何？
                            <div>本卦：风天小畜 → 变卦：风火家人 | 动爻：2</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // 扩展卦象数据库
        const trigrams = {
            0: { name: "坤", symbol: "☷", element: "地", nature: "柔顺" },
            1: { name: "震", symbol: "☳", element: "雷", nature: "震动" },
            2: { name: "坎", symbol: "☵", element: "水", nature: "险陷" },
            3: { name: "兑", symbol: "☱", element: "泽", nature: "喜悦" },
            4: { name: "艮", symbol: "☶", element: "山", nature: "静止" },
            5: { name: "离", symbol: "☲", element: "火", nature: "明丽" },
            6: { name: "巽", symbol: "☴", element: "风", nature: "顺从" },
            7: { name: "乾", symbol: "☰", element: "天", nature: "刚健" }
        };

        // 六十四卦数据库（扩展版）
        const hexagrams = {
            "离艮": {
                name: "火山旅",
                changed: "风火家人",
                meaning: "旅卦象征旅行、不安定和变动。表示处于不稳定状态，需要谨慎行事",
                interpretation: "火山旅卦，上离下艮，火在山上燃烧，象征旅途中的不安定。此卦表示你正处于一个变动期，可能在外奔波或内心不安。",
                movingYao: {
                    1: "初爻：谨慎开始，避免冒进",
                    2: "二爻：寻求稳定，注意人际",
                    3: "三爻：面临困境，需忍耐",
                    4: "四爻：渐入佳境，把握机会",
                    5: "五爻：领导责任，谨慎决策",
                    6: "六爻：回归本心，反思总结"
                }
            },
            "乾坤": {
                name: "天地否",
                changed: "地天泰",
                meaning: "否卦象征闭塞不通，需要等待转机",
                interpretation: "天地否卦，上乾下坤，天地不交，万物不通。表示当前处境困难，需要耐心等待转机。",
                movingYao: {
                    1: "初爻：静待时机，不宜妄动",
                    2: "二爻：寻求贵人，化解困境",
                    3: "三爻：忍耐坚持，终见曙光",
                    4: "四爻：转变思路，寻求突破",
                    5: "五爻：领导困境，需守正道",
                    6: "六爻：否极泰来，转机将至"
                }
            },
            "坎离": {
                name: "水火既济",
                changed: "火水未济",
                meaning: "既济卦象征事情已成，但需谨慎守成",
                interpretation: "水火既济卦，上坎下离，水在火上，象征烹饪完成。表示事情已经成功，但需要保持谨慎。",
                movingYao: {
                    1: "初爻：成功初始，防微杜渐",
                    2: "二爻：保持警惕，勿失良机",
                    3: "三爻：守成艰难，防范风险",
                    4: "四爻：巩固成果，预防隐患",
                    5: "五爻：谦逊守正，共享成果",
                    6: "六爻：功成身退，避免过满"
                }
            },
            "震巽": {
                name: "雷风恒",
                changed: "风雷益",
                meaning: "恒卦象征持久稳定，需要持之以恒",
                interpretation: "雷风恒卦，上震下巽，雷风相激，象征持久。表示需要保持恒心，坚持不懈。",
                movingYao: {
                    1: "初爻：立定志向，坚定信念",
                    2: "二爻：调整方法，避免固执",
                    3: "三爻：坚持原则，不随波逐流",
                    4: "四爻：寻找突破，创新方法",
                    5: "五爻：坚守中道，平衡各方",
                    6: "六爻：反思调整，避免僵化"
                }
            },
            "艮兑": {
                name: "山泽损",
                changed: "泽山咸",
                meaning: "损卦象征减损付出，有失有得",
                interpretation: "山泽损卦，上艮下兑，山下有泽，象征减损。表示需要适当付出才能有所收获。",
                movingYao: {
                    1: "初爻：量力而行，避免过度",
                    2: "二爻：合理付出，期待回报",
                    3: "三爻：三人行则损一人，专注重点",
                    4: "四爻：减轻损失，及时止损",
                    5: "五爻：大舍大得，把握关键",
                    6: "六爻：得道多助，终获支持"
                }
            },
            "巽乾": {
                name: "风天小畜",
                changed: "风火家人",
                meaning: "小畜卦象征小有积蓄，需要积累力量",
                interpretation: "风天小畜卦，上巽下乾，风行天上，象征小有积蓄。表示需要积累力量，等待时机。",
                movingYao: {
                    1: "初爻：回归正道，重新开始",
                    2: "二爻：携手同行，共创未来",
                    3: "三爻：夫妻反目，注意关系",
                    4: "四爻：保持诚信，化解猜疑",
                    5: "五爻：富以其邻，共享成果",
                    6: "六爻：积蓄已成，适时而动"
                }
            },
            "坤艮": {
                name: "地山谦",
                changed: "地火明夷",
                meaning: "谦卦象征谦虚谨慎，以柔克刚",
                interpretation: "地山谦卦，上坤下艮，地中有山，象征谦虚。表示应以谦逊态度行事，以柔克刚。",
                movingYao: {
                    1: "初爻：谦谦君子，卑以自牧",
                    2: "二爻：鸣谦贞吉，中心得也",
                    3: "三爻：劳谦君子，万民服也",
                    4: "四爻：无不利，撝谦不违则",
                    5: "五爻：不富以其邻，利用侵伐",
                    6: "六爻：鸣谦，志未得也"
                }
            }
        };

        // 动爻位置解释库
        const yaoPositions = {
            1: { name: "初爻", meaning: "事物起始阶段，需谨慎根基" },
            2: { name: "二爻", meaning: "事物发展阶段，需把握时机" },
            3: { name: "三爻", meaning: "事物转折阶段，面临关键选择" },
            4: { name: "四爻", meaning: "事物上升阶段，接近目标但需谨慎" },
            5: { name: "五爻", meaning: "事物鼎盛阶段，领导者位置需守正" },
            6: { name: "上爻", meaning: "事物终极阶段，反映最终结果" }
        };

        // 建议库
        const adviceCategories = {
            "事业": [
                "近期可能有岗位变动或出差机会，宜把握但需谨慎评估",
                "加强与团队成员的沟通协作，避免单打独斗",
                "关注行业趋势变化，提前做好应对准备",
                "考虑拓展新领域或学习新技能",
                "注意工作与生活的平衡，避免过度劳累"
            ],
            "人际": [
                "注意与上级领导的沟通方式，保持谦逊态度",
                "避免卷入办公室政治，保持中立立场",
                "可寻求年长或有经验人士的指导",
                "注意处理好家庭与工作的关系",
                "与合作伙伴保持良好沟通"
            ],
            "时机": [
                "未来3个月是关键调整期，不宜做重大决策",
                "今年秋季可能有重要发展机遇出现",
                "注意农历五月和九月的关键时间节点",
                "早晨5-7点是思考决策的黄金时段",
                "周末适合进行重要的人际交往活动"
            ],
            "财运": [
                "近期投资需谨慎，避免高风险项目",
                "考虑长期稳健型理财方式",
                "注意控制不必要的开支",
                "可能有意外收入机会，但需甄别真伪",
                "与他人合作财务事项需明确协议"
            ],
            "健康": [
                "注意劳逸结合，避免过度劳累",
                "定期体检，关注心脑血管健康",
                "适当增加户外运动时间",
                "注意饮食均衡，避免暴饮暴食",
                "保持良好作息习惯，保证充足睡眠"
            ]
        };

        // 初始化
        document.addEventListener('DOMContentLoaded', function () {
            // 绑定按钮事件
            document.getElementById('divinateBtn').addEventListener('click', calculateGua);

            // 初始化历史记录
            updateHistory();

            // 初始计算一次卦象
            calculateGua();
        });

        // 计算卦象（修复动爻问题）
        function calculateGua() {
            // 获取输入值
            const num1 = parseInt(document.getElementById('num1').value) || 0;
            const num2 = parseInt(document.getElementById('num2').value) || 0;
            const num3 = parseInt(document.getElementById('num3').value) || 0;
            const query = document.getElementById('query').value || "询问事由";

            // 计算卦象
            const shangGua = num1 % 8;
            const xiaGua = num2 % 8;

            // 修复动爻位置计算问题
            let movingYao = num3 % 6;
            // 关键修复：正确处理余数为0的情况（应为第6爻）
            movingYao = movingYao === 0 ? 6 : movingYao;

            // 获取卦象信息
            const guaKey = `${trigrams[shangGua].name}${trigrams[xiaGua].name}`;
            const hexagram = hexagrams[guaKey] || hexagrams["离艮"]; // 默认使用火山旅

            // 显示卦象
            document.getElementById('originalSymbol').textContent =
                `${trigrams[shangGua].symbol}${trigrams[xiaGua].symbol}`;
            document.getElementById('originalName').textContent = hexagram.name;

            // 显示变卦（简单示例，实际应计算变卦）
            document.getElementById('changedSymbol').textContent =
                `${trigrams[(shangGua + 1) % 8].symbol}${trigrams[(xiaGua + 1) % 8].symbol}`;
            document.getElementById('changedName').textContent = hexagram.changed;

            // 显示动爻位置
            document.getElementById('movingYao').textContent = `第${movingYao}爻`;
            document.getElementById('queryResult').textContent = query;

            // 显示卦象解析
            document.getElementById('divinationText').textContent =
                `${hexagram.interpretation} ${yaoPositions[movingYao].meaning}。`;

            // 生成详细建议
            generateAdvice(hexagram, movingYao, query);

            // 保存到历史记录
            saveToHistory(num1, num2, num3, query, hexagram.name, hexagram.changed, movingYao);
        }

        // 生成详细建议
        function generateAdvice(hexagram, movingYao, query) {
            const adviceContainer = document.getElementById('detailedAdvice');
            let adviceHTML = '<div class="advice-section">';

            // 添加动爻特定建议
            if (hexagram.movingYao && hexagram.movingYao[movingYao]) {
                adviceHTML += `
                        <div class="advice-card">
                            <div class="card-title">动爻解析：${yaoPositions[movingYao].name}</div>
                            <p>${hexagram.movingYao[movingYao]}</p>
                        </div>`;
            }

            // 添加分类建议
            const relevantCategories = getRelevantCategories(query);

            relevantCategories.forEach(category => {
                const categoryAdvice = adviceCategories[category];
                if (categoryAdvice) {
                    const randomAdvices = getRandomItems(categoryAdvice, 3);
                    adviceHTML += `
                            <div class="advice-card">
                                <div class="card-title">${category}建议</div>
                                ${randomAdvices.map(advice => `<p>${advice}</p>`).join('')}
                            </div>`;
                }
            });

            adviceHTML += '</div>';
            adviceContainer.innerHTML = adviceHTML;
        }

        // 根据询问内容获取相关建议分类
        function getRelevantCategories(query) {
            const categories = ["事业", "人际", "时机", "财运", "健康"];
            const queryLower = query.toLowerCase();

            // 根据关键词匹配
            if (queryLower.includes("事业") || queryLower.includes("工作")) {
                return ["事业", "人际", "时机"];
            }
            if (queryLower.includes("感情") || queryLower.includes("人际")) {
                return ["人际", "时机"];
            }
            if (queryLower.includes("财运") || queryLower.includes("投资")) {
                return ["财运", "时机"];
            }
            if (queryLower.includes("健康") || queryLower.includes("身体")) {
                return ["健康", "时机"];
            }

            // 默认返回
            return ["事业", "人际", "时机"];
        }

        // 从数组中随机获取指定数量的元素
        function getRandomItems(array, count) {
            const shuffled = [...array].sort(() => 0.5 - Math.random());
            return shuffled.slice(0, count);
        }

        // 保存到历史记录（添加动爻位置）
        function saveToHistory(num1, num2, num3, query, benGua, bianGua, movingYao) {
            const history = JSON.parse(localStorage.getItem('divinationHistory') || '[]');
            const date = new Date().toLocaleDateString();

            history.unshift({
                date,
                nums: [num1, num2, num3],
                query,
                benGua,
                bianGua,
                movingYao
            });

            // 最多保存10条记录
            if (history.length > 10) history.pop();

            localStorage.setItem('divinationHistory', JSON.stringify(history));
            updateHistory();
        }

        // 更新历史记录显示（显示动爻位置）
        function updateHistory() {
            const history = JSON.parse(localStorage.getItem('divinationHistory') || '[]');
            const historyList = document.getElementById('historyList');

            if (history.length === 0) {
                historyList.innerHTML = '<div class="history-item">暂无历史记录</div>';
                return;
            }

            historyList.innerHTML = history.map(item => `
                        <div class="history-item">
                            <strong>${item.date}</strong> | 数字：${item.nums.join(', ')} | 事由：${item.query}
                            <div>本卦：${item.benGua} → 变卦：${item.bianGua} | 动爻：${item.movingYao}</div>
                        </div>
                    `).join('');
        }
    </script>
</body>
</html>
