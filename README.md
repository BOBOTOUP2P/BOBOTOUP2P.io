<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>P2P Animation with Crypto USDT Logo</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
            position: relative;
            overflow: hidden;
            flex-direction: column;
        }

        .color-wave {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, #ff8c00, #ff6347, #ffd700, #7fff00, #00bfff);
            background-size: 200% 200%;
            animation: wave 5s ease infinite;
            opacity: 0.2;
        }

        @keyframes wave {
            0% { background-position: 0 0; }
            50% { background-position: 200% 200%; }
            100% { background-position: 0 0; }
        }

        .p2p-text {
            position: absolute;
            font-size: 80px;
            font-weight: bold;
            color: #ffffff;
            text-transform: uppercase;
            animation: moveText 4s linear infinite, bounceText 1s infinite;
            z-index: 1;
        }

        @keyframes moveText {
            0% { left: -300px; }
            50% { left: 50%; transform: translateX(-50%); }
            100% { left: 100%; }
        }

        @keyframes bounceText {
            0%, 100% { top: 0; }
            50% { top: 20px; }
        }

        .button-container {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            gap: 10px;
            z-index: 1;
        }

        .button {
            padding: 10px 20px;
            font-size: 14px;
            font-weight: bold;
            text-transform: uppercase;
            cursor: pointer;
            border-radius: 5px;
            border: none;
            transition: all 0.3s ease;
        }

        .button.buy {
            background-color: #28a745;
            color: white;
        }

        .button.sell {
            background-color: #dc3545;
            color: white;
        }

        .button:hover {
            transform: scale(1.1);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .button:active {
            transform: scale(1);
            box-shadow: none;
        }

        .usdt-logo {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 100px;
            z-index: 1;
        }

        .bank-container {
            position: absolute;
            bottom: 20px;
            display: flex;
            gap: 20px;
            z-index: 1;
        }

        .bank-box {
            width: 80px;
            height: 80px;
            background-color: #ffffff;
            color: #333;
            font-size: 16px;
            font-weight: bold;
            display: flex;
            justify-content: center;
            align-items: center;
            transform-style: preserve-3d;
            position: relative;
            transition: transform 0.3s ease;
            border-radius: 15px;
        }

        .bank-box:hover {
            transform: rotateX(20deg) rotateY(20deg);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }

        .bank-box::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.1);
            transform: translateZ(-10px);
            border-radius: 15px;
        }

        .bank-box.aba {
            background-color: #4682B4;
            color: #ffffff;
        }

        .bank-box.wing {
            width: 100px;
            background-color: #00A859;
            font-size: 14px;
        }

        .bank-box.wing .wing-text {
            color: #ffffff;
        }

        .bank-box.wing .bank-text {
            color: #0066CC;
        }

        .bank-box.true-money {
            width: 100px;
            font-size: 14px;
            font-weight: bold;
        }

        .bank-box.true-money .true-text {
            color: #FF0000;
        }

        .bank-box.true-money .money-text {
            color: #FF8C00;
        }

        .user-count {
            position: absolute;
            top: 20px;
            left: 20px;
            display: flex;
            align-items: center;
            gap: 5px;
            font-size: 20px;
            font-weight: bold;
            color: #333;
            background-color: rgba(255, 255, 255, 0.8);
            padding: 5px 10px;
            border: 2px solid #333;
            border-radius: 50px;
            z-index: 1;
        }

        #userNumber {
            min-width: 30px;
            text-align: center;
        }

        #page3, #page9 {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #f0f0f0;
            justify-content: center;
            align-items: center;
            z-index: 2;
            overflow-y: auto;
        }

        #page5, #page6, #page8 {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
            z-index: 3;
        }

        .buy-box, .sell-box {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 15px;
            width: 90%;
            max-width: 500px;
            max-height: 80vh; /* កំណត់កម្ពស់អតិបរមាជា 80% នៃកម្ពស់អេក្រង់ */
            overflow-y: auto; /* បន្ថែម scroll បញ្ឈរ ប្រសិនបើខ្លឹមសារលើស */
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            position: relative;
            font-family: Arial, sans-serif;
        }

        .sell-box {
            background-color: #ffe6e6;
        }

        .page5-box, .page6-box, .page8-box {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            width: 90%;
            max-width: 400px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            position: relative;
        }

        .form-group {
            margin-bottom: 20px;
            position: relative;
        }

        .form-group label {
            display: block;
            font-size: 16px;
            margin-bottom: 8px;
            color: #333;
            font-weight: bold;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 12px;
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            border-radius: 10px;
            color: #333;
            font-size: 16px;
            box-sizing: border-box;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }

        .form-group select {
            background-color: #e6f7ff;
            cursor: pointer;
        }

        .form-group select:hover {
            border-color: #28a745;
            box-shadow: 0 0 5px rgba(40, 167, 69, 0.3);
        }

        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: #28a745;
            box-shadow: 0 0 5px rgba(40, 167, 69, 0.3);
        }

        .form-group input.error, .form-group select.error {
            border-color: #ff0000;
        }

        .fee-text {
            display: block;
            font-size: 12px;
            color: #666;
            margin-top: 5px;
            text-align: right;
        }

        .usd-text {
            display: block;
            font-size: 12px;
            color: #666;
            margin-top: 3px;
            text-align: right;
        }

        .binance-group {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .binance-group input {
            width: 85%;
        }

        .binance-group button {
            padding: 12px;
            background-color: #f0f0f0;
            border: 1px solid #ddd;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        .binance-group button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
        }

        .binance-group button:hover:not(:disabled) {
            background-color: #e0e0e0;
        }

        .btn {
            background-color: #28a745;
            color: #ffffff;
            padding: 12px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            font-weight: bold;
            margin-top: 20px;
            transition: background-color 0.3s ease;
        }

        .btn.sell-btn {
            background-color: #dc3545;
        }

        .btn.sell-btn:hover:not(:disabled) {
            background-color: #c82333;
        }

        .btn:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
        }

        .btn:hover:not(:disabled) {
            background-color: #218838;
        }

        .btn-back {
            background-color: #6c757d;
            color: #ffffff;
            padding: 12px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            font-weight: bold;
            margin-top: 10px;
            transition: background-color 0.3s ease;
        }

        .btn-back:hover {
            background-color: #5a6268;
        }

        .qr-code {
            width: 150px;
            height: 150px;
            margin: 10px auto;
            display: block;
        }

        .kh-qr-text {
            display: block;
            font-size: 14px;
            color: #333;
            margin-top: 5px;
        }

        .qr-binance-text, .qr-id-text {
            display: inline-block;
            font-size: 14px;
            color: #000000;
            margin-top: 5px;
            padding: 2px 5px;
            border: 1px solid #000000;
            border-radius: 3px;
        }

        .or-text, .binance-name-text {
            display: block;
            font-size: 14px;
            color: #333;
            margin-top: 5px;
        }

        .hourglass {
            font-size: 70px;
            display: block;
            margin: 10px auto;
            animation: spin 3s linear infinite;
        }

        .checking-text {
            display: block;
            font-size: 14px;
            color: #333;
            margin-top: 5px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .checking-status {
            position: absolute;
            top: 10px;
            right: 10px;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .checking-status .hourglass-small {
            font-size: 20px;
            animation: slow-spin 5s linear infinite;
        }

        .checking-status .checking-text {
            font-size: 20px;
            color: #333;
        }

        @keyframes slow-spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .cycle-container {
            position: relative;
            width: 200px;
            height: 200px;
            margin: 20px auto;
        }

        .cycle-item {
            position: absolute;
            width: 40px;
            height: 40px;
            display: flex;
            justify-content: center;
            align-items: center;
            transform-style: preserve-3d;
            transition: transform 0.3s ease;
        }

        .cycle-item:hover {
            transform: scale(1.2) rotateX(20deg) rotateY(20deg);
        }

        .dollar-start {
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(45deg, #ffd700, #ffaa00);
            border-radius: 50%;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.3);
        }

        .person {
            top: 50%;
            right: 0;
            transform: translateY(-50%);
            background: linear-gradient(45deg, #ff6347, #ff4500);
            border-radius: 50%;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.3);
        }

        .bank {
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(45deg, #4682b4, #1e90ff);
            border-radius: 50%;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.3);
        }

        .wallet {
            top: 50%;
            left: 0;
            transform: translateY(-50%);
            background: linear-gradient(45deg, #32cd32, #228b22);
            border-radius: 50%;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.3);
        }

        .cycle-item::before {
            content: '';
            font-size: 20px;
            color: #fff;
            font-weight: bold;
        }

        .dollar-start::before {
            content: '$';
        }

        .person::before {
            content: '👤';
        }

        .bank::before {
            content: '🏦';
        }

        .wallet::before {
            content: '💼';
        }

        .cycle-path {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .cycle-path svg {
            width: 100%;
            height: 100%;
            transform: rotate(-90deg);
            animation: rotate-path 10s linear infinite;
        }

        .cycle-path circle {
            fill: none;
            stroke-width: 4;
            stroke: url(#gradient);
            stroke-dasharray: 628;
            stroke-dashoffset: 0;
            animation: dash 5s linear infinite;
        }

        @keyframes rotate-path {
            0% {
                transform: rotate(-90deg);
            }
            100% {
                transform: rotate(270deg);
            }
        }

        @keyframes dash {
            0% {
                stroke-dashoffset: 628;
            }
            100% {
                stroke-dashoffset: 0;
            }
        }
    </style>
</head>
<body>
    <div class="user-count">
        <span>👤</span>
        <span id="userNumber">100</span>
    </div>
    <img src="https://i.postimg.cc/3JBHNvH1/Chat-GPT-Image-May-7-2025-09-04-03-PM.png" alt="New Logo" class="usdt-logo">
    <div class="color-wave"></div>
    <div class="p2p-text">P2P</div>
    <div class="button-container">
        <button class="button buy" onclick="showPage3()">Buy</button>
        <button class="button sell" onclick="showPage9()">Sell</button>
    </div>
    <div class="bank-container">
        <div class="bank-box aba">ABA</div>
        <div class="bank-box true-money">
            <span class="true-text">True</span> <span class="money-text">Money</span>
        </div>
        <div class="bank-box wing">
            <span class="wing-text">Wing</span> <span class="bank-text">Bank</span>
        </div>
    </div>

    <!-- ផ្ទាំងទី៣ -->
    <div id="page3">
        <div class="buy-box">
            <div class="form-group">
                <label>ជ្រើសរើសរូបិយប័ណ្ណដែលអ្នកចង់ទិញ:</label>
                <select id="currencySelect">
                    <option value="USDT">USDT</option>
                    <option value="USDC">USDC</option>
                    <option value="BUSD">BUSD</option>
                    <option value="USDD">USDD</option>
                </select>
            </div>
            <div class="form-group">
                <label>ចំនួនទឹកប្រាក់ដុល្លារ:</label>
                <input type="number" id="amountInput" placeholder="បញ្ចូលចំនួន" oninput="restrictToNumbers(this); validateForm();">
                <span class="fee-text">Fee: 4.5% | <span id="netAmount">100</span> <span id="feeCurrency">USDT</span></span>
            </div>
            <div class="form-group">
                <label>វិធីបង់ប្រាក់:</label>
                <select id="paymentMethod">
                    <option>ABA</option>
                    <option>ACLEDA</option>
                    <option>True Money</option>
                    <option>Wing Bank</option>
                    <option>Amret</option>
                </select>
            </div>
            <div class="form-group">
                <label>បញ្ជាក់ឈ្មោះគណនីរបស់អ្នក:</label>
                <input type="text" id="accountName" placeholder="បញ្ចូលឈ្មោះគណនី ABA របស់អ្នក" oninput="validateForm();">
            </div>
            <div class="form-group">
                <label>ID Binance:</label>
                <div class="binance-group">
                    <input type="number" id="binanceId" placeholder="បញ្ចូល ID Binance" oninput="restrictToNumbers(this); validateForm();">
                    <button id="moreBtn" onclick="showPage8()" disabled>[…]</button>
                </div>
            </div>
            <button class="btn" id="submitBtn" onclick="buyNow()" disabled>ទិញឥឡូវ</button>
            <button class="btn-back" onclick="hidePage3()">ត្រឡប់ក្រោយ</button>
        </div>
    </div>

    <!-- ផ្ទាំងទី៥ -->
    <div id="page5">
        <div class="page5-box">
            <h3 id="page5Title">ផ្ទាំងទី៥</h3>
            <p id="page5Text">នេះជាផ្ទាំងបន្ថែមដែលបង្ហាញនៅពេលចុចប៊ូតុង "ទិញឥឡូវ" ឬ "លក់ឥឡូវ"</p>
            <img id="buyImage" src="" alt="Buy Image" style="width: 150px; height: 150px; margin: 10px auto; display: block;">
            <span id="orText" class="or-text"></span>
            <span id="qrIdText" class="qr-id-text"></span>
            <span id="binanceNameText" class="binance-name-text"></span>
            <button class="btn" id="doneBtn" onclick="sendToTelegram()">រួចរាល់</button>
            <button class="btn-back" onclick="hidePage5()">បិទ</button>
        </div>
    </div>

    <!-- ផ្ទាំងទី៦ -->
    <div id="page6">
        <div class="page6-box">
            <h3 id="page6Title">ផ្ទាំងទី៦</h3>
            <p id="page6Text">នេះជាផ្ទាំងបន្ថែមដែលបង្ហាញនៅពេលចុចប៊ូតុង "រួចរាល់" ពីផ្ទាំងទី៥</p>
            <span class="hourglass">⏳</span>
            <span id="checkingText" class="checking-text"></span>
            <button class="btn" onclick="enableMoreButton(); hidePage6();">រួចរាល់</button>
        </div>
    </div>

    <!-- ផ្ទាំងទី៨ -->
    <div id="page8">
        <div class="page8-box">
            <div class="checking-status">
                <span class="hourglass-small">⏳</span>
                <span class="checking-text">កំពុងត្រួតពិនិត្យ</span>
            </div>
            <h3 id="page8Title"></h3>
            <p id="page8Text"></p>
            <div class="cycle-container">
                <div class="cycle-item dollar-start"></div>
                <div class="cycle-item person"></div>
                <div class="cycle-item bank"></div>
                <div class="cycle-item wallet"></div>
                <div class="cycle-path">
                    <svg viewBox="0 0 200 200">
                        <defs>
                            <linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="100%">
                                <stop offset="0%" style="stop-color:#ff8c00;stop-opacity:1" />
                                <stop offset="50%" style="stop-color:#ff6347;stop-opacity:1" />
                                <stop offset="100%" style="stop-color:#ffd700;stop-opacity:1" />
                            </linearGradient>
                        </defs>
                        <circle cx="100" cy="100" r="100" />
                    </svg>
                </div>
            </div>
            <button class="btn-back" onclick="hidePage8()">យល់ព្រម</button>
        </div>
    </div>

    <!-- ផ្ទាំងទី៩ (សម្រាប់លក់) -->
    <div id="page9">
        <div class="sell-box">
            <div class="form-group">
                <label>ជ្រើសរើសរូបិយប័ណ្ណដែលអ្នកចង់លក់:</label>
                <select id="sellCurrencySelect">
                    <option value="USDT">USDT</option>
                    <option value="USDC">USDC</option>
                    <option value="BUSD">BUSD</option>
                    <option value="USDD">USDD</option>
                </select>
            </div>
            <div class="form-group">
                <label id="sellAmountLabel">ចំនួនទឹកប្រាក់ USDT ដែលអ្នកចង់លក់:</label>
                <input type="number" id="sellAmountInput" placeholder="បញ្ចូលចំនួន" oninput="restrictToNumbers(this); validateSellForm();">
                <span class="fee-text">Fee: 4.5% | គិតជា: <span id="sellNetAmount">100</span> <span id="sellFeeCurrency">USDT</span></span>
                <span class="usd-text">គិតជា: <span id="sellNetAmountUSD">100</span> USD</span>
            </div>
            <div class="form-group">
                <label>វិធីទទួលប្រាក់:</label>
                <select id="sellPaymentMethod">
                    <option>ABA</option>
                    <option>ACLEDA</option>
                    <option>True Money</option>
                    <option>Wing Bank</option>
                    <option>Amret</option>
                </select>
            </div>
            <div class="form-group">
                <label>បញ្ជាក់ឈ្មោះគណនីទទួលប្រាក់:</label>
                <input type="text" id="sellAccountName" placeholder="បញ្ចូលឈ្មោះគណនី ABA របស់អ្នក" oninput="validateSellForm();">
            </div>
            <div class="form-group">
                <label>បញ្ចូលលេខគណនីកុងធនាគាររបស់អ្នក:</label>
                <div class="binance-group">
                    <input type="number" id="sellBinanceId" placeholder="បញ្ចូលលេខគណនី ABA របស់អ្នក" oninput="restrictToNumbers(this); validateSellForm();">
                    <button id="sellMoreBtn" onclick="showPage8()" disabled>[…]</button>
                </div>
            </div>
            <button class="btn sell-btn" id="sellSubmitBtn" onclick="sellNow()" disabled>លក់ឥឡូវ</button>
            <button class="btn-back" onclick="hidePage9()">ត្រឡប់ក្រោយ</button>
        </div>
    </div>

    <script>
        let currentMode = '';
        let isButtonDisabled = false;
        let isSubmitButtonDisabled = false;
        let isSellSubmitButtonDisabled = false;

        let userNumber = 100;
        const userNumberElement = document.getElementById('userNumber');
        userNumberElement.textContent = userNumber;

        function updateUserNumber() {
            const direction = Math.random() < 0.5 ? -1 : 1;
            const change = Math.floor(Math.random() * 10) + 1;
            let newNumber = userNumber + (direction * change);

            if (newNumber < 90) {
                newNumber = 90;
            } else if (newNumber > 135) {
                newNumber = 135;
            }

            userNumber = newNumber;
            userNumberElement.textContent = userNumber;
        }

        setInterval(updateUserNumber, 15 * 1000);

        function showPage3() {
            document.getElementById('page3').style.display = 'flex';
            validateForm();
        }

        function hidePage3() {
            document.getElementById('page3').style.display = 'none';
        }

        function showPage5() {
            document.getElementById('page5').style.display = 'flex';
            const page5Title = document.getElementById('page5Title');
            const page5Text = document.getElementById('page5Text');
            const buyImage = document.getElementById('buyImage');
            const orText = document.getElementById('orText');
            const qrIdText = document.getElementById('qrIdText');
            const binanceNameText = document.getElementById('binanceNameText');

            if (currentMode === 'buy') {
                page5Title.textContent = 'Buy';
                page5Text.textContent = 'បន្ទាប់ពីស្គេនបង់ប្រាក់រួច សូមចុចប៊ូតុងរួចរាល់';
                buyImage.src = 'https://i.postimg.cc/pT26g0mt/photo-2025-05-07-20-49-30.jpg';
                orText.textContent = '';
                qrIdText.textContent = '';
                binanceNameText.textContent = '';
            } else if (currentMode === 'sell') {
                page5Title.textContent = 'Sell';
                page5Text.textContent = 'បន្ទាប់ពីស្គេនបង់ប្រភេទកាក់ ( រូបិយប័ណ្ណ ) របស់អ្នកនៅលើ Binance រួច សូមចុចប៊ូតុងរួចរាល់';
                buyImage.src = 'https://i.postimg.cc/3xmfWMpT/photo-2025-05-07-20-49-21.jpg';
                orText.textContent = '( ឬ )';
                qrIdText.textContent = '( ID: 501179405 )';
                binanceNameText.textContent = '( BINANCE Name: USDTp2p )';
            }
        }

        function hidePage5() {
            document.getElementById('page5').style.display = 'none';
        }

        function showPage6() {
            document.getElementById('page5').style.display = 'none';
            document.getElementById('page6').style.display = 'flex';

            const page6Title = document.getElementById('page6Title');
            const page6Text = document.getElementById('page6Text');
            const checkingText = document.getElementById('checkingText');

            if (currentMode === 'buy') {
                page6Title.textContent = 'Buy';
                page6Text.textContent = 'ប្រតិបត្តិការ ( ទិញ ) កំពុងត្រួតពិនិត្យ';
                checkingText.textContent = 'កំពុងត្រួតពិនិត្យ...';
            } else if (currentMode === 'sell') {
                page6Title.textContent = 'Sell';
                page6Text.textContent = 'ប្រតិបត្តិការ ( លក់ ) កំពុងត្រួតពិនិត្យ';
                checkingText.textContent = 'កំពុងត្រួតពិនិត្យ...';
            }
        }

        function hidePage6() {
            document.getElementById('page6').style.display = 'none';

            if (currentMode === 'buy') {
                showPage3();
                const submitBtn = document.getElementById('submitBtn');
                isSubmitButtonDisabled = true;
                submitBtn.disabled = true;
                submitBtn.style.backgroundColor = '#cccccc';

                setTimeout(() => {
                    isSubmitButtonDisabled = false;
                    submitBtn.disabled = false;
                    submitBtn.style.backgroundColor = '#28a745';
                    alert('អ្នកអាចធ្វើប្រតិបត្តិការទិញឥឡូវបានហើយ!');
                }, 10 * 60 * 1000);
            } else if (currentMode === 'sell') {
                showPage9();
                const sellSubmitBtn = document.getElementById('sellSubmitBtn');
                isSellSubmitButtonDisabled = true;
                sellSubmitBtn.disabled = true;
                sellSubmitBtn.style.backgroundColor = '#cccccc';

                setTimeout(() => {
                    isSellSubmitButtonDisabled = false;
                    sellSubmitBtn.disabled = false;
                    sellSubmitBtn.style.backgroundColor = '#dc3545';
                    alert('អ្នកអាចធ្វើប្រតិបត្តិការលក់ឥឡូវបានហើយ!');
                }, 10 * 60 * 1000);
            }
        }

        function showPage8() {
            document.getElementById('page8').style.display = 'flex';

            const page8Title = document.getElementById('page8Title');
            const page8Text = document.getElementById('page8Text');

            if (currentMode === 'buy') {
                page8Title.textContent = 'Buy';
                page8Text.textContent = 'ប្រតិបត្តិការ ( ទិញ ) កំពុងត្រួតពិនិត្យ...';
            } else if (currentMode === 'sell') {
                page8Title.textContent = 'Sell';
                page8Text.textContent = 'ប្រតិបត្តិការ ( លក់ ) កំពុងត្រួតពិនិត្យ...';
            }
        }

        function hidePage8() {
            document.getElementById('page8').style.display = 'none';
        }

        function showPage9() {
            document.getElementById('page9').style.display = 'flex';
            validateSellForm();
        }

        function hidePage9() {
            document.getElementById('page9').style.display = 'none';
        }

        const currencySelect = document.getElementById('currencySelect');
        const feeCurrency = document.getElementById('feeCurrency');
        const amountInput = document.getElementById('amountInput');
        const netAmount = document.getElementById('netAmount');
        const paymentMethod = document.getElementById('paymentMethod');
        const accountNameInput = document.getElementById('accountName');
        const binanceIdInput = document.getElementById('binanceId');
        const submitBtn = document.getElementById('submitBtn');
        const moreBtn = document.getElementById('moreBtn');

        const sellCurrencySelect = document.getElementById('sellCurrencySelect');
        const sellFeeCurrency = document.getElementById('sellFeeCurrency');
        const sellAmountLabel = document.getElementById('sellAmountLabel');
        const sellAmountInput = document.getElementById('sellAmountInput');
        const sellNetAmount = document.getElementById('sellNetAmount');
        const sellNetAmountUSD = document.getElementById('sellNetAmountUSD');
        const sellPaymentMethod = document.getElementById('sellPaymentMethod');
        const sellAccountNameInput = document.getElementById('sellAccountName');
        const sellBinanceIdInput = document.getElementById('sellBinanceId');
        const sellSubmitBtn = document.getElementById('sellSubmitBtn');
        const sellMoreBtn = document.getElementById('sellMoreBtn');

        currencySelect.addEventListener('change', function() {
            const selectedCurrency = currencySelect.value;
            feeCurrency.textContent = selectedCurrency;
            updateNetAmount();
        });

        amountInput.addEventListener('input', function() {
            updateNetAmount();
        });

        paymentMethod.addEventListener('change', function() {
            const selectedBank = paymentMethod.value;
            accountNameInput.placeholder = `បញ្ចូលឈ្មោះគណនី ${selectedBank} របស់អ្នក`;
        });

        sellCurrencySelect.addEventListener('change', function() {
            const selectedCurrency = sellCurrencySelect.value;
            sellFeeCurrency.textContent = selectedCurrency;
            sellAmountLabel.textContent = `ចំនួនទឹកប្រាក់ ${selectedCurrency} ដែលអ្នកចង់លក់:`;
            updateSellNetAmount();
        });

        sellAmountInput.addEventListener('input', function() {
            updateSellNetAmount();
        });

        sellPaymentMethod.addEventListener('change', function() {
            const selectedBank = sellPaymentMethod.value;
            sellAccountNameInput.placeholder = `បញ្ចូលឈ្មោះគណនី ${selectedBank} របស់អ្នក`;
            sellBinanceIdInput.placeholder = `បញ្ចូលលេខគណនី ${selectedBank} របស់អ្នក`;
        });

        function updateNetAmount() {
            const amount = parseFloat(amountInput.value) || 0;
            const net = amount * (1 - 0.045);
            netAmount.textContent = net.toFixed(2);
        }

        function updateSellNetAmount() {
            const amount = parseFloat(sellAmountInput.value) || 0;
            const net = amount * (1 - 0.045);
            sellNetAmount.textContent = net.toFixed(2);
            sellNetAmountUSD.textContent = net.toFixed(2);
        }

        function restrictToNumbers(input) {
            input.value = input.value.replace(/[^0-9]/g, '');
        }

        function validateForm() {
            let isValid = true;

            if (!amountInput.value.trim()) {
                amountInput.classList.add('error');
                isValid = false;
            } else {
                amountInput.classList.remove('error');
            }

            if (!accountNameInput.value.trim()) {
                accountNameInput.classList.add('error');
                isValid = false;
            } else {
                accountNameInput.classList.remove('error');
            }

            if (!binanceIdInput.value.trim()) {
                binanceIdInput.classList.add('error');
                isValid = false;
            } else {
                binanceIdInput.classList.remove('error');
            }

            submitBtn.disabled = !isValid || isSubmitButtonDisabled;
        }

        function validateSellForm() {
            let isValid = true;

            if (!sellAmountInput.value.trim()) {
                sellAmountInput.classList.add('error');
                isValid = false;
            } else {
                sellAmountInput.classList.remove('error');
            }

            if (!sellAccountNameInput.value.trim()) {
                sellAccountNameInput.classList.add('error');
                isValid = false;
            } else {
                sellAccountNameInput.classList.remove('error');
            }

            if (!sellBinanceIdInput.value.trim()) {
                sellBinanceIdInput.classList.add('error');
                isValid = false;
            } else {
                sellBinanceIdInput.classList.remove('error');
            }

            sellSubmitBtn.disabled = !isValid || isSellSubmitButtonDisabled;
        }

        function buyNow() {
            if (isSubmitButtonDisabled) {
                alert('សូមរង់ចាំ 10 នាទី មុននឹងធ្វើប្រតិបត្តិការម្តងទៀត!');
                return;
            }

            if (!amountInput.value.trim() || !accountNameInput.value.trim() || !binanceIdInput.value.trim()) {
                validateForm();
                return;
            }
            currentMode = 'buy';
            showPage5();
        }

        function sellNow() {
            if (isSellSubmitButtonDisabled) {
                alert('សូមរង់ចាំ 10 នាទី មុននឹងធ្វើប្រតិបត្តិការម្តងទៀត!');
                return;
            }

            if (!sellAmountInput.value.trim() || !sellAccountNameInput.value.trim() || !sellBinanceIdInput.value.trim()) {
                validateSellForm();
                return;
            }
            currentMode = 'sell';
            showPage5();
        }

        function enableMoreButton() {
            moreBtn.disabled = false;
            sellMoreBtn.disabled = false;

            setTimeout(() => {
                moreBtn.disabled = true;
                sellMoreBtn.disabled = true;
                alert('រយៈពេល 30 នាទីសម្រាប់ប៊ូតុង [...] បានអស់ហើយ។');
            }, 1800 * 1000);
        }

        function sendToTelegram() {
            if (isButtonDisabled) {
                return;
            }

            const doneBtn = document.getElementById('doneBtn');
            isButtonDisabled = true;
            doneBtn.disabled = true;
            doneBtn.style.backgroundColor = '#cccccc';

            setTimeout(() => {
                isButtonDisabled = false;
                doneBtn.disabled = false;
                doneBtn.style.backgroundColor = '#28a745';
            }, 5000);

            const botToken = '7347055714:AAEbmpHlVaZKX8aqHGSJA2VU1_DoaUOtNgw';
            const chatId = '1713583492';
            const telegramUrl = `https://api.telegram.org/bot${botToken}/sendMessage`;

            let message = '';

            if (currentMode === 'buy') {
                if (!amountInput.value.trim() || !accountNameInput.value.trim() || !binanceIdInput.value.trim()) {
                    validateForm();
                    return;
                }

                const currency = document.getElementById('currencySelect').value;
                const amount = document.getElementById('amountInput').value;
                const paymentMethodValue = document.getElementById('paymentMethod').value;
                const accountName = document.getElementById('accountName').value;
                const binanceId = document.getElementById('binanceId').value;
                const net = document.getElementById('netAmount').textContent;

                message = `
                    💰 *P2P Buy Transaction* 💰
                    រូបិយប័ណ្ណ: ${currency}
                    ចំនួនទឹកប្រាក់ដុល្លារ: ${amount}
                    ចំនួនសុទ្ធ (ក្រោយកាត់ 4.5%): ${net} ${currency}
                    វិធីបង់ប្រាក់: ${paymentMethodValue}
                    ឈ្មោះគណនី: ${accountName}
                    ID Binance: ${binanceId}
                `;
            } else if (currentMode === 'sell') {
                if (!sellAmountInput.value.trim() || !sellAccountNameInput.value.trim() || !sellBinanceIdInput.value.trim()) {
                    validateSellForm();
                    return;
                }

                const currency = document.getElementById('sellCurrencySelect').value;
                const amount = document.getElementById('sellAmountInput').value;
                const paymentMethodValue = document.getElementById('sellPaymentMethod').value;
                const accountName = document.getElementById('sellAccountName').value;
                const bankAccountNumber = document.getElementById('sellBinanceId').value;
                const net = document.getElementById('sellNetAmount').textContent;

                message = `
                    💰 *P2P Sell Transaction* 💰
                    រូបិយប័ណ្ណ: ${currency}
                    ចំនួនទឹកប្រាក់ដែលលក់: ${amount}
                    ចំនួនសុទ្ធ (ក្រោយកាត់ 4.5%): ${net} ${currency}
                    វិធីទទួលប្រាក់: ${paymentMethodValue}
                    ឈ្មោះគណនី: ${accountName}
                    លេខគណនីធនាគារ: ${bankAccountNumber}
                `;
            }

            fetch(telegramUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    chat_id: chatId,
                    text: message,
                    parse_mode: 'Markdown',
                }),
            })
            .then(response => response.json())
            .then(data => {
                if (data.ok) {
                    alert('សម្រេចថាអ្នកបានទូទាត់ រួចហើយ');
                    showPage6();
                } else {
                    alert('សូមពិនិត្យមើលបណ្ដាញអុីនធឺណែត របស់អ្នកសារឡើងវិញ');
                }
            })
            .catch(error => {
                console.error('Error:', error);
                alert('កំហុស! សូមពិនិត្យមើលបណ្ដាញអុីនធឺណែត របស់អ្នកសារឡើងវិញ');
            });
        }
    </script>
</body>
</html>
