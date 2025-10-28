<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Facebook Only Access - Prank Tool</title>
    <style>
        /* ফন্ট এবং সাধারণ স্টাইল */
        body {
            font-family: 'Arial', sans-serif;
            background-color: #1a1a1a;
            color: #00ff41; /* নিয়ন গ্রিন */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            overflow: hidden;
        }

        /* কন্টেইনার স্টাইল */
        .container {
            width: 90%;
            max-width: 600px;
            background-color: #2a2a2a;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 255, 65, 0.5);
            text-align: center;
            border: 1px solid #00ff41;
        }

        /* অ্যানিমেশনের জন্য স্টাইল */
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        @keyframes blink {
            50% { border-color: transparent }
        }

        .welcome-text {
            overflow: hidden; /* টেক্সট হাইড করার জন্য */
            border-right: .15em solid #00ff41; /* কাস্টম কার্সর */
            white-space: nowrap; /* টেক্সট এক লাইনে রাখার জন্য */
            margin: 0 auto;
            letter-spacing: .15em;
            animation: 
                typing 3.5s steps(40, end),
                blink .75s step-end infinite;
            font-size: 2em;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }

        /* ইনপুট বক্স স্টাইল */
        .input-box {
            background-color: #333;
            border: 2px solid #00ff41;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            box-shadow: 0 0 10px rgba(0, 255, 65, 0.3);
        }

        #linkInput {
            width: 95%;
            padding: 12px;
            margin-bottom: 15px;
            border: none;
            border-radius: 5px;
            background-color: #111;
            color: #00ff41;
            font-size: 1.1em;
            transition: all 0.3s;
        }

        #linkInput:focus {
            outline: none;
            box-shadow: 0 0 10px #00ff41;
        }

        /* বাটন স্টাইল */
        .action-button {
            background-color: #00ff41;
            color: #1a1a1a;
            border: none;
            padding: 12px 25px;
            text-transform: uppercase;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s, box-shadow 0.3s;
        }

        .action-button:hover {
            background-color: #33ff66;
            transform: scale(1.05);
            box-shadow: 0 0 15px #33ff66;
        }

        /* লোডিং এবং কোডিং অ্যানিমেশন */
        .loading-area {
            display: none;
            text-align: left;
            margin-top: 20px;
            height: 250px;
            overflow-y: scroll;
            background-color: #111;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #00ff41;
            font-size: 0.9em;
            white-space: pre-wrap;
        }
        
        /* প্রোগ্রেস বার */
        .progress-bar-container {
            width: 100%;
            background-color: #333;
            border-radius: 5px;
            margin-top: 15px;
            border: 1px solid #00ff41;
        }

        .progress-bar {
            height: 20px;
            background-color: #00ff41;
            width: 0%;
            border-radius: 5px;
            text-align: center;
            line-height: 20px;
            color: #1a1a1a;
            font-weight: bold;
            transition: width 0.1s;
        }

        /* র্যান্ডম পাসওয়ার্ড */
        .password-display {
            margin-top: 15px;
            font-size: 1.2em;
        }
        .correct-password {
            color: #ff00ea; /* ফিউশিয়া কালার */
            font-weight: bold;
            animation: pulse 1s infinite alternate;
        }

        @keyframes pulse {
            from { box-shadow: 0 0 5px #ff00ea; }
            to { box-shadow: 0 0 20px #ff00ea; }
        }

        /* চূড়ান্ত ডেটা ডিসপ্লে */
        .result-data {
            display: none;
            margin-top: 30px;
            text-align: left;
            border: 2px solid #00ff41;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 255, 65, 0.5);
            background: #1a1a1a;
        }

        .data-box {
            margin-bottom: 15px;
            padding: 10px;
            border-radius: 5px;
            background-color: #333;
            border-left: 5px solid;
            animation: data-fade-in 1s forwards;
            opacity: 0;
        }

        @keyframes data-fade-in {
            to { opacity: 1; }
        }

        .box-1 { border-left-color: #ff0000; animation-delay: 0s; } /* লাল */
        .box-2 { border-left-color: #00ffff; animation-delay: 0.5s; } /* সায়ান */
        .box-3 { border-left-color: #ffff00; animation-delay: 1.0s; } /* হলুদ */
        .box-4 { border-left-color: #ff69b4; animation-delay: 1.5s; } /* হট পিঙ্ক */
        .box-5 { border-left-color: #00ff41; animation-delay: 2.0s; } /* সবুজ */

        .data-label {
            font-weight: bold;
            color: #999;
            display: block;
            font-size: 0.8em;
        }
        .data-value {
            font-size: 1.1em;
        }
    </style>
</head>
<body>

    <div class="container" id="mainContainer">
        <h1 class="welcome-text">Welcome My Tools</h1>

        <div id="inputSection" style="display: none;">
            <h2>Enter Facebook ID Link</h2>
            <div class="input-box">
                <input type="text" id="linkInput" placeholder="এখানে ফেইসবুক আইডির লিঙ্ক দিন">
                <button class="action-button" onclick="startLoading()">Access Victims Account</button>
            </div>
        </div>

        <div id="loadingSection" style="display: none;">
            <div class="progress-bar-container">
                <div class="progress-bar" id="progressBar">0%</div>
            </div>
            <div class="loading-area" id="loadingArea"></div>
            <div class="password-display" id="passwordDisplay"></div>
        </div>

        <div id="resultSection" class="result-data">
            <h2>Access Account</h2>
            <button class="action-button" onclick="showData()" style="animation: pulse 1s infinite alternate;">Go</button>
            
            <div id="dataDisplay" style="margin-top: 20px;">
                <div class="data-box box-1">
                    <span class="data-label">আইডির নাম:</span>
                    <span class="data-value">Zihan Albi</span>
                </div>
                <div class="data-box box-2">
                    <span class="data-label">জন্ম তারিখ:</span>
                    <span class="data-value">১০ নভেম্বর ২০০০</span>
                </div>
                <div class="data-box box-3">
                    <span class="data-label">লোকেশন:</span>
                    <span class="data-value">সিলেট</span>
                </div>
                <div class="data-box box-4">
                    <span class="data-label">ইউজার নেম:</span>
                    <span class="data-value">https://www.facebook.com/Sexy.Girl.চমে</span>
                </div>
                <div class="data-box box-5">
                    <span class="data-label">পাসওয়ার্ড:</span>
                    <span class="data-value">Anha???</span>
                </div>
                
                <button class="action-button" style="margin-top: 15px;" onclick="showSavePopup()">কালেক্ট করুন</button>
            </div>
        </div>
    </div>

    <script>
        // জাভাস্ক্রিপ্ট ফাংশনালিটি

        document.addEventListener('DOMContentLoaded', () => {
            // ১. ওয়েলকাম টেক্সট অ্যানিমেশনের পর ইনপুট পপ-আপ দেখাও
            setTimeout(() => {
                showInitialPrompt();
            }, 4000); // 4 সেকেন্ড পর (অ্যানিমেশন টাইমের চেয়ে একটু বেশি)
        });

        function showInitialPrompt() {
            // "Enter" দেওয়ার জন্য পপআপ
            alert('Welcome My Tools - ইন্টার দিন');
            document.getElementById('inputSection').style.display = 'block';
            document.querySelector('.welcome-text').style.animation = 'none'; // অ্যানিমেশন বন্ধ করা
            document.querySelector('.welcome-text').style.borderRight = 'none'; // কার্সর সরানো
        }

        const scanMessages = [
            "আইডির ইনফরমেশন চ্যাক...",
            "পাসওয়ার্ড চ্যাক...",
            "ভেরিফাই...",
            "Initializing main matrix bypass...",
            "Injecting payload...",
            "Checking database connection...",
            "Accessing victim's session data...",
            "Decrypting hash values...",
            "Final verification protocol running..."
        ];

        const passwords = [
            "password123",
            "zihan2000",
            "iloveu*",
            "victim01",
            "12345678",
            "secret_key",
            "Anha???" // সঠিক পাসওয়ার্ড
        ];

        // ৪. লোডিং শুরু করা
        function startLoading() {
            const link = document.getElementById('linkInput').value;
            if (!link) {
                alert("দয়া করে একটি ফেসবুক লিঙ্ক দিন।");
                return;
            }

            document.getElementById('inputSection').style.display = 'none';
            document.getElementById('loadingSection').style.display = 'block';

            let progress = 0;
            const loadingArea = document.getElementById('loadingArea');
            const progressBar = document.getElementById('progressBar');
            const totalTime = 30000; // ৩০ সেকেন্ড = ৩০,০০০ মিলিসেকেন্ড
            const updateInterval = 300; // ০.৩ সেকেন্ডে আপডেট

            const intervalId = setInterval(() => {
                progress += (updateInterval / totalTime) * 100;

                if (progress >= 100) {
                    clearInterval(intervalId);
                    progressBar.style.width = '100%';
                    progressBar.innerText = '100% DONE';
                    showFinalPopup();
                    return;
                }

                // প্রোগ্রেস আপডেট
                progressBar.style.width = progress + '%';
                progressBar.innerText = Math.floor(progress) + '% Loading...';

                // কোডিং স্টাইল মেসেজ
                if (progress % 5 < 1) { // প্রতি কয়েক সেকেন্ডে একটি করে নতুন মেসেজ যোগ করা
                    const randomMessage = scanMessages[Math.floor(Math.random() * scanMessages.length)];
                    loadingArea.innerHTML += `> <span style="color:#00ffff;">[PROCESS]</span> ${randomMessage}<br>`;
                }

                // উপর থেকে নিচে কোডিং পড়ার ইফেক্ট
                if (Math.random() < 0.8) {
                    const randomCode = generateRandomCode();
                    loadingArea.innerHTML += `<span style="color:#00ff41;">${randomCode}</span><br>`;
                }

                // স্ক্রল ডাউন
                loadingArea.scrollTop = loadingArea.scrollHeight;

                // র্যান্ডম পাসওয়ার্ড দেখানো
                if (progress > 50 && progress < 90) {
                    displayRandomPassword(progress);
                }

            }, updateInterval);
        }

        // র্যান্ডম কোড জেনারেটর
        function generateRandomCode() {
            const chars = '0123456789ABCDEFabcdef?><*&^%$#@!+=-';
            let code = '';
            for (let i = 0; i < 40; i++) {
                code += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return code;
        }

        // র্যান্ডম পাসওয়ার্ড ডিসপ্লে
        function displayRandomPassword(progress) {
            const display = document.getElementById('passwordDisplay');
            let passwordToShow = passwords[Math.floor(Math.random() * passwords.length)];
            
            if (progress > 85 && passwordToShow === "Anha???") {
                passwordToShow = `<span class="correct-password">Anha??? [ ডান ]</span>`;
                display.innerHTML = `Found Password: ${passwordToShow}`;
            } else {
                 // শুধুমাত্র একটি র্যান্ডম পাসওয়ার্ড দেখানো
                display.innerHTML = `Scanning Passwords: ${passwordToShow}`;
            }
        }

        // ৫. চূড়ান্ত পপ-আপ
        function showFinalPopup() {
            setTimeout(() => {
                document.getElementById('loadingSection').style.display = 'none';
                document.getElementById('mainContainer').innerHTML += '<div id="accessPopup" class="popup-style" style="text-align:center; padding: 20px;"><h2>Access Account</h2><p style="color:#fff;">Data Ready to be Viewed.</p></div>';
                
                alert("Access Account");
                document.getElementById('resultSection').style.display = 'block';
            }, 1000); // লোডিং শেষ হওয়ার ১ সেকেন্ড পর
        }

        // ৬. Go বাটনে ক্লিক করলে ডেটা দেখানো
        function showData() {
            document.getElementById('dataDisplay').style.display = 'block';
            document.querySelector('#resultSection > button').style.display = 'none'; // Go বাটন হাইড করা
        }

        // ৭. সেভ পপ-আপ
        function showSavePopup() {
            alert("সেইভ করা হয়েছে");
        }
    </script>
</body>
</html>
