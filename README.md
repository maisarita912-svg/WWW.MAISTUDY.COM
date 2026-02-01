<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MAI App - Future Study Platform</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Splash Screen */
        .splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            animation: fadeOut 3s forwards;
            animation-delay: 2s;
        }

        @keyframes fadeOut {
            to {
                opacity: 0;
                visibility: hidden;
            }
        }

        .logo {
            width: 150px;
            height: 150px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 60px;
            font-weight: bold;
            color: white;
            box-shadow: 0 10px 40px rgba(102, 126, 234, 0.3);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .splash-text {
            margin-top: 30px;
            font-size: 24px;
            font-weight: bold;
            color: #667eea;
            text-align: center;
        }

        .splash-subtitle {
            margin-top: 10px;
            font-size: 16px;
            color: #666;
        }

        /* Main Container */
        .container {
            max-width: 500px;
            margin: 0 auto;
            padding: 20px;
            opacity: 0;
            animation: slideIn 1s forwards;
            animation-delay: 5s;
        }

        @keyframes slideIn {
            to {
                opacity: 1;
            }
        }

        /* Registration Steps */
        .step {
            display: none;
            background: white;
            border-radius: 20px;
            padding: 40px 30px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            animation: fadeInUp 0.5s;
        }

        .step.active {
            display: block;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .step-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .step-number {
            display: inline-block;
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border-radius: 50%;
            line-height: 40px;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .step-title {
            font-size: 24px;
            color: #333;
            margin-bottom: 10px;
        }

        .step-subtitle {
            color: #666;
            font-size: 14px;
        }

        .form-group {
            margin-bottom: 25px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #333;
            font-weight: 600;
        }

        input[type="text"],
        input[type="tel"],
        input[type="number"],
        input[type="file"] {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s;
        }

        input:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
        }

        .btn:active {
            transform: translateY(0);
        }

        .photo-upload {
            text-align: center;
            margin-bottom: 20px;
        }

        .photo-preview {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: #f0f0f0;
            margin: 0 auto 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            border: 4px solid #667eea;
        }

        .photo-preview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .photo-preview-placeholder {
            font-size: 60px;
            color: #ccc;
        }

        /* ID Card */
        .id-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 20px;
            padding: 30px;
            color: white;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
        }

        .id-card-header {
            text-align: center;
            margin-bottom: 20px;
            padding-bottom: 20px;
            border-bottom: 2px solid rgba(255, 255, 255, 0.3);
        }

        .id-card-logo {
            font-size: 40px;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .id-card-body {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }

        .id-card-photo {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: white;
            overflow: hidden;
            border: 3px solid white;
        }

        .id-card-photo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .id-card-info {
            flex: 1;
        }

        .id-card-field {
            margin-bottom: 10px;
        }

        .id-card-label {
            font-size: 12px;
            opacity: 0.8;
            margin-bottom: 2px;
        }

        .id-card-value {
            font-size: 16px;
            font-weight: bold;
        }

        .id-card-footer {
            text-align: center;
            padding-top: 20px;
            border-top: 2px solid rgba(255, 255, 255, 0.3);
        }

        .student-id {
            font-size: 14px;
            letter-spacing: 2px;
            font-weight: bold;
        }

        /* Dashboard */
        .dashboard {
            display: none;
            animation: fadeInUp 0.5s;
        }

        .dashboard.active {
            display: block;
        }

        .welcome-section {
            background: white;
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 20px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .welcome-logo {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 20px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-size: 40px;
            font-weight: bold;
            color: white;
            margin-bottom: 15px;
        }

        .welcome-text {
            font-size: 24px;
            color: #333;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .welcome-subtitle {
            color: #666;
        }

        .course-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }

        .course-card {
            background: white;
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .course-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .course-icon {
            font-size: 50px;
            margin-bottom: 15px;
        }

        .course-title {
            font-size: 18px;
            font-weight: bold;
            color: #333;
            margin-bottom: 5px;
        }

        .course-desc {
            font-size: 12px;
            color: #666;
        }

        .progress-bar {
            width: 100%;
            height: 6px;
            background: #e0e0e0;
            border-radius: 3px;
            margin-top: 20px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
            border-radius: 3px;
            transition: width 0.5s;
        }

        /* OTP Input */
        .otp-inputs {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin: 20px 0;
        }

        .otp-input {
            width: 50px;
            height: 60px;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
        }

        .otp-input:focus {
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }

            .step {
                padding: 30px 20px;
            }

            .course-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Splash Screen -->
    <div class="splash-screen" id="splashScreen">
        <div class="logo">MAI</div>
        <div class="splash-text">MAI APP</div>
        <div class="splash-subtitle">BY Mr.adhyayan india</div>
    </div>

    <!-- Main Container -->
    <div class="container">
        <!-- Step 1: Student Name -->
        <div class="step active" id="step1">
            <div class="step-header">
                <div class="step-number">1</div>
                <h2 class="step-title">Student Name</h2>
                <p class="step-subtitle">कृपया अपना नाम दर्ज करें</p>
            </div>
            <div class="form-group">
                <label for="studentName">Full Name / पूरा नाम</label>
                <input type="text" id="studentName" placeholder="Enter your full name" required>
            </div>
            <button class="btn" onclick="nextStep(1)">Next / आगे बढ़ें</button>
        </div>

        <!-- Step 2: Class/Graduation -->
        <div class="step" id="step2">
            <div class="step-header">
                <div class="step-number">2</div>
                <h2 class="step-title">Class / Graduation</h2>
                <p class="step-subtitle">अपनी कक्षा या स्नातक स्तर दर्ज करें</p>
            </div>
            <div class="form-group">
                <label for="studentClass">Enter your Class or Graduation / कक्षा या स्नातक</label>
                <input type="text" id="studentClass" placeholder="e.g., Class 10, B.Tech 2nd Year" required>
            </div>
            <button class="btn" onclick="nextStep(2)">Next / आगे बढ़ें</button>
        </div>

        <!-- Step 3: Photo Upload -->
        <div class="step" id="step3">
            <div class="step-header">
                <div class="step-number">3</div>
                <h2 class="step-title">Student Photo</h2>
                <p class="step-subtitle">अपनी तस्वीर अपलोड करें</p>
            </div>
            <div class="photo-upload">
                <div class="photo-preview" id="photoPreview">
                    <span class="photo-preview-placeholder">📷</span>
                </div>
                <input type="file" id="studentPhoto" accept="image/*" onchange="handlePhotoUpload(event)" style="display: none;">
                <button class="btn" onclick="document.getElementById('studentPhoto').click()">Upload Photo / फोटो अपलोड करें</button>
            </div>
            <button class="btn" onclick="nextStep(3)" style="margin-top: 20px;">Next / आगे बढ़ें</button>
        </div>

        <!-- Step 4: Age -->
        <div class="step" id="step4">
            <div class="step-header">
                <div class="step-number">4</div>
                <h2 class="step-title">Age</h2>
                <p class="step-subtitle">अपनी आयु दर्ज करें</p>
            </div>
            <div class="form-group">
                <label for="studentAge">Age / आयु</label>
                <input type="number" id="studentAge" placeholder="Enter your age" min="5" max="100" required>
            </div>
            <button class="btn" onclick="nextStep(4)">Next / आगे बढ़ें</button>
        </div>

        <!-- Step 5: Father Name -->
        <div class="step" id="step5">
            <div class="step-header">
                <div class="step-number">5</div>
                <h2 class="step-title">Father's Name</h2>
                <p class="step-subtitle">पिता का नाम दर्ज करें</p>
            </div>
            <div class="form-group">
                <label for="fatherName">Father's Name / पिता का नाम</label>
                <input type="text" id="fatherName" placeholder="Enter father's name" required>
            </div>
            <button class="btn" onclick="nextStep(5)">Next / आगे बढ़ें</button>
        </div>

        <!-- Step 6: OTP Verification -->
        <div class="step" id="step6">
            <div class="step-header">
                <div class="step-number">6</div>
                <h2 class="step-title">Phone Verification</h2>
                <p class="step-subtitle">फोन नंबर सत्यापन</p>
            </div>
            <div class="form-group">
                <label for="phoneNumber">Phone Number / फोन नंबर</label>
                <input type="tel" id="phoneNumber" placeholder="Enter 10-digit mobile number" maxlength="10" required>
            </div>
            <button class="btn" onclick="sendOTP()" id="sendOtpBtn">Send OTP / OTP भेजें</button>
            
            <div id="otpSection" style="display: none; margin-top: 30px;">
                <p style="text-align: center; margin-bottom: 15px; color: #666;">Enter OTP / OTP दर्ज करें</p>
                <div class="otp-inputs">
                    <input type="text" class="otp-input" maxlength="1" oninput="moveToNext(this, 0)">
                    <input type="text" class="otp-input" maxlength="1" oninput="moveToNext(this, 1)">
                    <input type="text" class="otp-input" maxlength="1" oninput="moveToNext(this, 2)">
                    <input type="text" class="otp-input" maxlength="1" oninput="moveToNext(this, 3)">
                </div>
                <button class="btn" onclick="verifyOTP()" style="margin-top: 20px;">Verify OTP / सत्यापित करें</button>
            </div>
        </div>

        <!-- ID Card Display -->
        <div class="step" id="idCardStep">
            <div class="id-card">
                <div class="id-card-header">
                    <div class="id-card-logo">MAI</div>
                    <div>Student Identity Card</div>
                    <div style="font-size: 12px; opacity: 0.8;">MAI App by Mr.adhyayan india</div>
                </div>
                <div class="id-card-body">
                    <div class="id-card-photo" id="cardPhoto">
                        <span style="font-size: 40px;">👤</span>
                    </div>
                    <div class="id-card-info">
                        <div class="id-card-field">
                            <div class="id-card-label">Name</div>
                            <div class="id-card-value" id="cardName">-</div>
                        </div>
                        <div class="id-card-field">
                            <div class="id-card-label">Class/Graduation</div>
                            <div class="id-card-value" id="cardClass">-</div>
                        </div>
                        <div class="id-card-field">
                            <div class="id-card-label">Age</div>
                            <div class="id-card-value" id="cardAge">-</div>
                        </div>
                    </div>
                </div>
                <div class="id-card-footer">
                    <div class="id-card-field">
                        <div class="id-card-label">Father's Name</div>
                        <div class="id-card-value" id="cardFather">-</div>
                    </div>
                    <div class="student-id" id="cardStudentId" style="margin-top: 15px;">STUDENT ID: MAI-000000</div>
                </div>
            </div>
            <button class="btn" onclick="goToDashboard()" style="margin-top: 20px;">Continue to Dashboard / डैशबोर्ड पर जाएं</button>
        </div>

        <!-- Dashboard -->
        <div class="dashboard" id="dashboard">
            <div class="welcome-section">
                <div class="welcome-logo">MAI</div>
                <h1 class="welcome-text">Welcome to MAI App!</h1>
                <p class="welcome-subtitle">स्वागत है! आपकी सीखने की यात्रा यहाँ से शुरू होती है</p>
            </div>

            <div class="course-grid">
                <div class="course-card" onclick="openCourse('chatbot')">
                    <div class="course-icon">🤖</div>
                    <div class="course-title">AI Chatbot</div>
                    <div class="course-desc">24/7 AI सहायता</div>
                </div>

                <div class="course-card" onclick="openCourse('english')">
                    <div class="course-icon">🗣️</div>
                    <div class="course-title">English Speaking</div>
                    <div class="course-desc">AI के साथ अंग्रेजी सीखें</div>
                </div>

                <div class="course-card" onclick="openCourse('morse')">
                    <div class="course-icon">📡</div>
                    <div class="course-title">Morse Code</div>
                    <div class="course-desc">डिजिटल संचार</div>
                </div>

                <div class="course-card" onclick="openCourse('marketing')">
                    <div class="course-icon">📱</div>
                    <div class="course-title">Digital Marketing</div>
                    <div class="course-desc">ऑनलाइन मार्केटिंग</div>
                </div>

                <div class="course-card" onclick="openCourse('hindi')">
                    <div class="course-icon">📖</div>
                    <div class="course-title">Hindi</div>
                    <div class="course-desc">विशेषज्ञ द्वारा हिंदी</div>
                </div>

                <div class="course-card" onclick="openCourse('math')">
                    <div class="course-icon">🔢</div>
                    <div class="course-title">Mathematics</div>
                    <div class="course-desc">गणित विशेषज्ञ</div>
                </div>
            </div>

            <div class="welcome-section" style="margin-top: 20px;">
                <h3 style="color: #333; margin-bottom: 10px;">Your Learning Progress</h3>
                <p style="color: #666; font-si
