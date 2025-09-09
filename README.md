# my-website
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="format-detection" content="telephone=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <title>留学生女巫的毒药</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }
        
        body {
            font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            color: #333;
            line-height: 1.6;
            padding: 0;
            margin: 0;
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 100%;
            margin: 0 auto;
            padding: 20px 15px;
        }
        
        .screen {
            display: none;
            background: white;
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            margin-bottom: 30px;
            text-align: center;
        }
        
        .screen.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        h1 {
            color: #4b0082;
            font-size: 28px;
            margin-bottom: 15px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.1);
        }
        
        h2 {
            color: #6a5acd;
            font-size: 22px;
            margin: 15px 0;
        }
        
        p {
            margin-bottom: 15px;
            font-size: 16px;
            color: #555;
        }
        
        .btn {
            display: inline-block;
            background: linear-gradient(to right, #7b52ab, #6a0dad);
            color: white;
            padding: 14px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            font-size: 18px;
            border: none;
            cursor: pointer;
            margin: 10px 5px;
            box-shadow: 0 4px 15px rgba(106, 13, 173, 0.3);
            transition: all 0.3s;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(106, 13, 173, 0.4);
        }
        
        .btn:active {
            transform: translateY(1px);
        }
        
        .btn-small {
            padding: 8px 15px;
            font-size: 14px;
        }
        
        .character-container {
            width: 200px;
            height: 200px;
            margin: 20px auto;
            border: 4px solid #7b52ab;
            border-radius: 15px;
            overflow: hidden;
            background: #f0e6ff;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        #characterImage {
            max-width: 100%;
            max-height: 100%;
        }
        
        .default-character {
            width: 120px;
            height: 120px;
            position: relative;
        }
        
        .stats {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
            margin: 20px 0;
        }
        
        .stat {
            flex: 1;
            min-width: 100px;
            margin: 10px;
            padding: 15px;
            background: #f8f2ff;
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
        }
        
        .stat-value {
            font-size: 28px;
            font-weight: bold;
            color: #6a0dad;
        }
        
        .stat-label {
            font-size: 14px;
            color: #777;
        }
        
        .card {
            background: #f8f2ff;
            border-radius: 15px;
            padding: 20px;
            margin: 20px 0;
            border: 2px dashed #7b52ab;
        }
        
        .card-icon {
            font-size: 50px;
            margin-bottom: 15px;
        }
        
        .card-title {
            font-size: 20px;
            font-weight: bold;
            color: #6a0dad;
            margin-bottom: 10px;
        }
        
        .card-description {
            font-size: 16px;
            color: #555;
        }
        
        .upload-section {
            margin: 20px 0;
            padding: 15px;
            background: #e6d9ff;
            border-radius: 15px;
        }
        
        .share-section {
            margin: 30px 0;
            padding: 20px;
            background: #f0e6ff;
            border-radius: 15px;
        }
        
        .ending-description {
            font-size: 18px;
            line-height: 1.8;
            color: #4b0082;
            margin: 20px 0;
            padding: 15px;
            background: #f8f2ff;
            border-radius: 15px;
            text-align: left;
        }
        
        .share-btn {
            background: linear-gradient(to right, #25d366, #128c7e);
            display: block;
            width: 80%;
            margin: 20px auto;
            padding: 16px;
            font-size: 20px;
        }
        
        .round-counter {
            font-size: 18px;
            color: #6a0dad;
            font-weight: bold;
            margin: 15px 0;
        }
        
        .items-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            margin: 15px 0;
            gap: 10px;
        }
        
        .item {
            width: 80px;
            padding: 10px;
            background: #f0e6ff;
            border-radius: 10px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid transparent;
        }
        
        .item:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(106, 13, 173, 0.3);
            border-color: #6a0dad;
        }
        
        .item.disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .item-icon {
            font-size: 30px;
            margin-bottom: 5px;
        }
        
        .item-name {
            font-size: 12px;
            color: #6a0dad;
            margin-bottom: 5px;
        }
        
        .item-count {
            font-size: 14px;
            font-weight: bold;
            color: #4b0082;
        }
        
        .item-tooltip {
            position: absolute;
            background: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 8px 12px;
            border-radius: 8px;
            font-size: 12px;
            z-index: 100;
            max-width: 200px;
            display: none;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* 响应式设计 */
        @media (max-width: 480px) {
            .container {
                padding: 15px 10px;
            }
            
            .screen {
                padding: 20px 15px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            h2 {
                font-size: 20px;
            }
            
            .btn {
                padding: 12px 25px;
                font-size: 16px;
            }
            
            .stat {
                min-width: 80px;
                padding: 10px;
            }
            
            .stat-value {
                font-size: 24px;
            }
            
            .items-container {
                gap: 5px;
            }
            
            .item {
                width: 70px;
                padding: 8px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 开始屏幕 -->
        <div id="startScreen" class="screen active">
            <h1>留学生女巫的毒药</h1>
            <p>管理你的留学生活，平衡知识、健康与压力！</p>
            <div class="character-container">
                <div id="characterImage" class="default-character">
                    <div style="position: absolute; width: 20px; height: 40px; background: #6a5acd; left: 40px; top: 60px;"></div>
                    <div style="position: absolute; width: 24px; height: 24px; background: #ffdbac; left: 38px; top: 36px; border: 2px solid #e6b894;"></div>
                    <div style="position: absolute; width: 8px; height: 8px; background: #4b0082; left: 42px; top: 44px;"></div>
                    <div style="position: absolute; width: 8px; height: 8px; background: #4b0082; left: 50px; top: 44px;"></div>
                    <div style="position: absolute; width: 12px; height: 4px; background: #ff6b6b; left: 44px; top: 52px;"></div>
                </div>
            </div>
            <button class="btn" onclick="showScreen('uploadScreen')">开始游戏</button>
        </div>
        
        <!-- 上传形象屏幕 -->
        <div id="uploadScreen" class="screen">
            <h2>上传你的形象</h2>
            <p>选择或上传一个代表你的形象，开始留学生活！</p>
            <div class="character-container">
                <div id="uploadedImage"></div>
            </div>
            <div class="upload-section">
                <input type="file" id="imageUpload" accept="image/*" style="display: none;">
                <button class="btn" onclick="document.getElementById('imageUpload').click()">选择图片</button>
                <p style="margin-top: 15px; font-size: 14px;">或者使用默认角色开始游戏</p>
            </div>
            <button class="btn" onclick="startGame()">开始留学生活</button>
            <button class="btn" onclick="showScreen('startScreen')">返回</button>
        </div>
        
        <!-- 游戏屏幕 -->
        <div id="gameScreen" class="screen">
            <h2>留学生活挑战</h2>
            <div class="round-counter">学期进度: <span id="roundCounter">1</span>/10</div>
            <div class="stats">
                <div class="stat">
                    <div class="stat-value" id="knowledgeValue">0</div>
                    <div class="stat-label">知识点</div>
                </div>
                <div class="stat">
                    <div class="stat-value" id="healthValue">5</div>
                    <div class="stat-label">健康值</div>
                </div>
                <div class="stat">
                    <div class="stat-value" id="stressValue">0</div>
                    <div class="stat-label">压力值</div>
                </div>
            </div>
            
            <!-- 道具区域 -->
            <h3>我的道具</h3>
            <div class="items-container" id="itemsContainer">
                <!-- 道具将通过JS动态添加 -->
            </div>
            
            <div class="card">
                <div class="card-icon" id="cardIcon">🎓</div>
                <div class="card-title" id="cardTitle">欢迎来到留学生活！</div>
                <div class="card-description" id="cardDescription">点击下方按钮抽取事件卡，开始你的留学生活挑战！</div>
            </div>
            <button class="btn" id="drawCardBtn" onclick="drawCard()">抽取事件卡</button>
            <button class="btn" id="useItemBtn" style="display: none;" onclick="hideItemUse()">返回</button>
        </div>
        
        <!-- 结局屏幕 -->
        <div id="endingScreen" class="screen">
            <h2>学期结束</h2>
            <div class="ending-description" id="endingDescription"></div>
            <div class="share-section">
                <h3>分享你的留学生活结局</h3>
                <p>长按保存图片分享到朋友圈</p>
                <div id="shareImageContainer" style="margin: 20px auto; width: 300px; height: 400px; background: #f0e6ff; border-radius: 15px; padding: 20px; display: none;">
                    <canvas id="shareCanvas" width="300" height="400"></canvas>
                </div>
                <button class="btn share-btn" onclick="generateShareImage()">生成分享图片</button>
                <button class="btn" onclick="restartGame()">再玩一次</button>
            </div>
        </div>
        
        <div id="itemTooltip" class="item-tooltip"></div>
    </div>

    <script>
        // 游戏数据
        let player = {
            knowledge: 0,
            health: 5,
            stress: 0,
            items: {}
        };
        
        let rounds = 0;
        const maxRounds = 10;
        let gameOver = false;
        let endingType = '';
        let usingItemMode = false;
        
        // 扩展事件卡
        const cards = [
            {name: "完成作业", icon: "📚", effect: {knowledge: 2, stress: 1}, description: "完成了困难的作业，知识点增加了，但压力也增大了"},
            {name: "参加讲座", icon: "🎓", effect: {knowledge: 1}, description: "参加了一场精彩的学术讲座"},
            {name: "聚会熬夜", icon: "🎉", effect: {health: -1, stress: -1}, description: "和朋友聚会到很晚，健康下降但压力减少了"},
            {name: "签证资料丢失", icon: "📑", effect: {stress: 2}, description: "重要的签证资料丢失了，压力大增"},
            {name: "感冒生病", icon: "🤒", effect: {health: -2, stress: 1}, description: "不小心感冒了，健康下降"},
            {name: "图书馆自习", icon: "📖", effect: {knowledge: 3, stress: 1}, description: "在图书馆高效学习了一天，知识点大幅增加"},
            {name: "网络购物包裹延迟", icon: "📦", effect: {stress: 1}, description: "期待的包裹延迟送达，有点烦躁"},
            {name: "交友成功", icon: "👥", effect: {stress: -2}, description: "结识了新朋友，心情愉快"},
            {name: "兼职收入", icon: "💰", effect: {stress: -1}, description: "兼职获得了收入，经济压力减小"},
            {name: "误过重要讲座", icon: "⏰", effect: {knowledge: -1, stress: 2}, description: "睡过头错过了重要讲座，知识点减少"},
            // 新增事件卡
            {name: "小组项目合作", icon: "👨‍👩‍👧‍👦", effect: {knowledge: 2, stress: -1}, description: "与同学合作完成小组项目，学到了新知识，社交减压"},
            {name: "文化冲击", icon: "🌍", effect: {stress: 2}, description: "遇到文化差异带来的困惑，压力增加"},
            {name: "获得奖学金", icon: "🏆", effect: {knowledge: 1, stress: -2}, description: "获得奖学金认可，知识点和心情都提升了"},
            {name: "语言障碍", icon: "🗣️", effect: {stress: 2, knowledge: -1}, description: "语言不通导致沟通困难，压力增加"},
            {name: "烹饪成功", icon: "🍳", effect: {health: 1, stress: -1}, description: "成功做出家乡美食，健康提升压力减少"},
            {name: "考试失利", icon: "📝", effect: {knowledge: -2, stress: 2}, description: "重要考试没考好，知识点减少压力增加"},
            {name: "参加社团活动", icon: "🎭", effect: {stress: -2, health: -1}, description: "参加有趣的社团活动，减压但有点累"},
            {name: "家乡包裹", icon: "📬", effect: {health: 1, stress: -2}, description: "收到家人寄来的包裹，健康压力都改善"}
        ];
        
        // 道具系统
        const itemsData = [
            {id: "energy_drink", name: "能量饮料", icon: "🥤", description: "恢复1点健康值，但增加1点压力", effect: {health: 1, stress: 1}, obtainChance: 0.3},
            {id: "study_guide", name: "学习指南", icon: "📘", description: "增加2点知识点", effect: {knowledge: 2}, obtainChance: 0.4},
            {id: "meditation", name: "冥想练习", icon: "🧘", description: "减少2点压力", effect: {stress: -2}, obtainChance: 0.3},
            {id: "vitamins", name: "维生素", icon: "💊", description: "恢复2点健康值", effect: {health: 2}, obtainChance: 0.2},
            {id: "coffee", name: "咖啡", icon: "☕", description: "增加1点知识点，减少1点健康", effect: {knowledge: 1, health: -1}, obtainChance: 0.5},
            {id: "lucky_charm", name: "幸运符", icon: "🔮", description: "下一张事件卡效果翻倍(正面)", effect: {special: "double_next"}, obtainChance: 0.1}
        ];
        
        // 结局描述
        const endings = {
            success: {
                title: "学业有成！",
                description: "恭喜你！你成功平衡了学习与生活，以优异的成绩完成了本学期。你的知识点积累丰富，健康状态良好，压力管理得当。教授们对你的表现赞不绝口，同学们都视你为榜样。留学生活虽然充满挑战，但你用智慧和毅力证明了自己的能力！"
            },
            knowledge: {
                title: "学有所成但身心俱疲",
                description: "你成功积累了足够的知识点，学期成绩优异。然而，在追求学术成就的过程中，你忽视了身心健康。长期的熬夜学习和高压力状态让你的身体发出了警告。下学期记得要更好地平衡学习与休息哦！"
            },
            health: {
                title: "健康第一",
                description: "你这学期特别注重身体健康，保持了良好的生活作息。虽然知识点积累略有不足，但健康的身体是你最大的财富。下学期可以适当增加学习时间，争取更好的学术表现！"
            },
            stress: {
                title: "压力山大",
                description: "本学期你感受到了巨大的压力，留学生活的种种挑战让你有些喘不过气。虽然勉强完成了学业，但过程中的压力给你带来了不少困扰。记得多与朋友交流，寻找缓解压力的方法，下学期会更好！"
            },
            fail: {
                title: "休学调整",
                description: "很遗憾，由于健康问题或压力过大，你不得不暂时休学调整。留学生活确实充满挑战，这次经历让你更清楚地认识到平衡的重要性。好好休息，调整状态，下学期重新出发！"
            }
        };
        
        // 显示指定屏幕
        function showScreen(screenId) {
            document.querySelectorAll('.screen').forEach(screen => {
                screen.classList.remove('active');
            });
            document.getElementById(screenId).classList.add('active');
            
            // 滚动到顶部
            window.scrollTo(0, 0);
        }
        
        // 开始游戏
        function startGame() {
            // 初始化游戏状态
            player = {
                knowledge: 0,
                health: 5,
                stress: 0,
                items: {}
            };
            rounds = 0;
            gameOver = false;
            
            // 初始化道具
            initItems();
            
            // 更新UI
            updateStats();
            updateItemsDisplay();
            
            // 显示游戏屏幕
            showScreen('gameScreen');
        }
        
        // 初始化道具
        function initItems() {
            // 给玩家随机1-2个初始道具
            const initialItemCount = Math.floor(Math.random() * 2) + 1;
            for (let i = 0; i < initialItemCount; i++) {
                const availableItems = itemsData.filter(item => 
                    !player.items[item.id] && Math.random() < item.obtainChance
                );
                
                if (availableItems.length > 0) {
                    const randomItem = availableItems[Math.floor(Math.random() * availableItems.length)];
                    player.items[randomItem.id] = 1;
                }
            }
        }
        
        // 更新状态显示
        function updateStats() {
            document.getElementById('knowledgeValue').textContent = player.knowledge;
            document.getElementById('healthValue').textContent = player.health;
            document.getElementById('stressValue').textContent = player.stress;
            document.getElementById('roundCounter').textContent = rounds;
        }
        
        // 更新道具显示
        function updateItemsDisplay() {
            const itemsContainer = document.getElementById('itemsContainer');
            itemsContainer.innerHTML = '';
            
            let hasItems = false;
            
            for (const itemId in player.items) {
                if (player.items[itemId] > 0) {
                    hasItems = true;
                    const itemData = itemsData.find(item => item.id === itemId);
                    
                    const itemElement = document.createElement('div');
                    itemElement.className = 'item';
                    itemElement.dataset.id = itemId;
                    itemElement.innerHTML = `
                        <div class="item-icon">${itemData.icon}</div>
                        <div class="item-name">${itemData.name}</div>
                        <div class="item-count">×${player.items[itemId]}</div>
                    `;
                    
                    // 添加鼠标悬停提示
                    itemElement.addEventListener('mouseover', (e) => {
                        const tooltip = document.getElementById('itemTooltip');
                        tooltip.textContent = itemData.description;
                        tooltip.style.display = 'block';
                        tooltip.style.left = (e.pageX + 10) + 'px';
                        tooltip.style.top = (e.pageY + 10) + 'px';
                    });
                    
                    itemElement.addEventListener('mousemove', (e) => {
                        const tooltip = document.getElementById('itemTooltip');
                        tooltip.style.left = (e.pageX + 10) + 'px';
                        tooltip.style.top = (e.pageY + 10) + 'px';
                    });
                    
                    itemElement.addEventListener('mouseout', () => {
                        document.getElementById('itemTooltip').style.display = 'none';
                    });
                    
                    // 添加点击使用功能
                    itemElement.addEventListener('click', () => {
                        useItem(itemId);
                    });
                    
                    itemsContainer.appendChild(itemElement);
                }
            }
            
            if (!hasItems) {
                itemsContainer.innerHTML = '<p>暂无道具，抽取事件卡有机会获得道具</p>';
            }
        }
        
        // 使用道具
        function useItem(itemId) {
            if (usingItemMode) return;
            
            const itemData = itemsData.find(item => item.id === itemId);
            if (!itemData || !player.items[itemId] || player.items[itemId] <= 0) return;
            
            // 特殊道具处理
            if (itemData.effect.special === "double_next") {
                // 设置下一个事件卡效果翻倍
                player.nextCardDoubleEffect = true;
                alert(`使用了${itemData.name}，下一个正面事件卡效果将翻倍！`);
            } else {
                // 普通道具效果
                for (let key in itemData.effect) {
                    player[key] += itemData.effect[key];
                }
                
                // 状态修正
                if (player.health > 5) player.health = 5;
                if (player.health < 0) player.health = 0;
                if (player.stress < 0) player.stress = 0;
                
                alert(`使用了${itemData.name}: ${itemData.description}`);
            }
            
            // 减少道具数量
            player.items[itemId]--;
            if (player.items[itemId] <= 0) {
                delete player.items[itemId];
            }
            
            // 更新UI
            updateStats();
            updateItemsDisplay();
            
            // 检查游戏是否结束
            if (player.health <= 0 || player.stress >= 10) {
                setTimeout(endGame, 1000);
            }
        }
        
        // 进入使用道具模式
        function showItemUse() {
            usingItemMode = true;
            document.getElementById('drawCardBtn').style.display = 'none';
            document.getElementById('useItemBtn').style.display = 'inline-block';
            alert("请点击要使用的道具");
        }
        
        // 退出使用道具模式
        function hideItemUse() {
            usingItemMode = false;
            document.getElementById('drawCardBtn').style.display = 'inline-block';
            document.getElementById('useItemBtn').style.display = 'none';
        }
        
        // 抽取事件卡
        function drawCard() {
            if (gameOver || rounds >= maxRounds) {
                endGame();
                return;
            }
            
            if (usingItemMode) {
                hideItemUse();
                return;
            }
            
            rounds++;
            
            const cardIndex = Math.floor(Math.random() * cards.length);
            const card = cards[cardIndex];
            
            // 检查是否有双倍效果
            let effectMultiplier = 1;
            if (player.nextCardDoubleEffect) {
                // 只对正面效果翻倍
                let hasPositiveEffect = false;
                for (let key in card.effect) {
                    if (card.effect[key] > 0) {
                        hasPositiveEffect = true;
                        break;
                    }
                }
                
                if (hasPositiveEffect) {
                    effectMultiplier = 2;
                    alert("幸运符生效！事件卡正面效果翻倍！");
                }
                
                player.nextCardDoubleEffect = false;
            }
            
            // 显示卡片信息
            document.getElementById('cardIcon').textContent = card.icon;
            document.getElementById('cardTitle').textContent = card.name;
            document.getElementById('cardDescription').textContent = card.description;
            
            // 应用卡片效果
            for (let key in card.effect) {
                player[key] += card.effect[key] * effectMultiplier;
            }
            
            // 状态修正
            if (player.health > 5) player.health = 5;
            if (player.health < 0) player.health = 0;
            if (player.stress < 0) player.stress = 0;
            
            // 随机获得道具
            if (Math.random() < 0.4) { // 40%几率获得道具
                const availableItems = itemsData.filter(item => 
                    Math.random() < item.obtainChance
                );
                
                if (availableItems.length > 0) {
                    const obtainedItem = availableItems[Math.floor(Math.random() * availableItems.length)];
                    
                    if (!player.items[obtainedItem.id]) {
                        player.items[obtainedItem.id] = 1;
                    } else {
                        player.items[obtainedItem.id]++;
                    }
                    
                    alert(`获得了道具: ${obtainedItem.name}!\n${obtainedItem.description}`);
                }
            }
            
            // 更新UI
            updateStats();
            updateItemsDisplay();
            
            // 检查游戏是否结束
            if (player.health <= 0 || player.stress >= 10) {
                setTimeout(endGame, 1500);
            } else if (rounds >= maxRounds) {
                setTimeout(endGame, 1500);
            }
        }
        
        // 结束游戏
        function endGame() {
            gameOver = true;
            
            // 确定结局类型
            if (player.health <= 0 || player.stress >= 10) {
                endingType = 'fail';
            } else if (player.knowledge >= 15) {
                if (player.health >= 4 && player.stress <= 5) {
                    endingType = 'success';
                } else {
                    endingType = 'knowledge';
                }
            } else if (player.health >= 4) {
                endingType = 'health';
            } else if (player.stress >= 7) {
                endingType = 'stress';
            } else {
                endingType = 'fail';
            }
            
            // 显示结局描述
            document.getElementById('endingDescription').innerHTML = `
                <h3>${endings[endingType].title}</h3>
                <p>${endings[endingType].description}</p>
                <p>最终数据：知识点 ${player.knowledge}，健康值 ${player.health}，压力值 ${player.stress}</p>
            `;
            
            // 显示结局屏幕
            showScreen('endingScreen');
        }
        
        // 重新开始游戏
        function restartGame() {
            showScreen('startScreen');
        }
        
        // 生成分享图片
        function generateShareImage() {
            const shareContainer = document.getElementById('shareImageContainer');
            shareContainer.style.display = 'block';
            
            const canvas = document.getElementById('shareCanvas');
            const ctx = canvas.getContext('2d');
            
            // 绘制背景
            ctx.fillStyle = '#6a11cb';
            ctx.fillRect(0, 0, 300, 400);
            
            // 绘制内容区域
            ctx.fillStyle = 'white';
            ctx.fillRect(10, 10, 280, 380);
            
            // 绘制标题
            ctx.fillStyle = '#4b0082';
            ctx.font = 'bold 20px PingFang SC, Microsoft YaHei';
            ctx.textAlign = 'center';
            ctx.fillText('留学生女巫的毒药', 150, 40);
            
            // 绘制结局类型
            ctx.fillStyle = '#6a0dad';
            ctx.font = 'bold 18px PingFang SC, Microsoft YaHei';
            ctx.fillText(endings[endingType].title, 150, 70);
            
            // 绘制数据
            ctx.fillStyle = '#333';
            ctx.font = '16px PingFang SC, Microsoft YaHei';
            ctx.textAlign = 'left';
            ctx.fillText(`知识点: ${player.knowledge}`, 50, 110);
            ctx.fillText(`健康值: ${player.health}`, 50, 140);
            ctx.fillText(`压力值: ${player.stress}`, 50, 170);
            
            // 绘制二维码提示
            ctx.textAlign = 'center';
            ctx.font = '14px PingFang SC, Microsoft YaHei';
            ctx.fillText('长按识别二维码体验游戏', 150, 350);
            
            // 显示保存提示
            alert('长按图片保存到相册，然后分享到朋友圈！');
        }
        
        // 图片上传处理
        document.getElementById('imageUpload').addEventListener('change', function(event) {
            const file = event.target.files[0];
            if (!file) return;
            
            if (!file.type.match('image.*')) {
                alert('请选择图片文件！');
                return;
            }
            
            const reader = new FileReader();
            reader.onload = function(e) {
                const img = document.createElement('img');
                img.src = e.target.result;
                img.style.maxWidth = '100%';
                img.style.maxHeight = '100%';
                
                const container = document.getElementById('uploadedImage');
                container.innerHTML = '';
                container.appendChild(img);
            };
            reader.readAsDataURL(file);
        });
        
        // 初始化
        window.onload = function() {
            // 微信中隐藏导航栏
            document.addEventListener('WeixinJSBridgeReady', function() {
                WeixinJSBridge.call('hideToolbar');
            });
            
            // 添加使用道具按钮事件
            document.getElementById('useItemBtn').addEventListener('click', hideItemUse);
        };
    </script>
</body>
</html>
