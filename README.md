<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>성인용 그림사전 - 병원</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      background-color: #f0f4f8;
      color: #333;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
      min-height: 100vh;
    }
    header {
      text-align: center;
      margin-bottom: 20px;
    }
    h1 {
      font-size: 28px;
      color: #1a365d;
      margin-bottom: 8px;
    }
    p.subtitle {
      font-size: 15px;
      color: #4a5568;
    }
    .dictionary-container {
      position: relative;
      max-width: 1000px;
      width: 100%;
      background: #ffffff;
      border-radius: 16px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
      overflow: hidden;
      display: flex;
      flex-direction: column;
    }
    .image-wrapper {
      position: relative;
      width: 100%;
      background-color: #eef2f5;
    }
    
    /* SVG 내부 오브젝트 스타일 */
    .interactive-obj {
      cursor: pointer;
      transition: all 0.2s ease;
    }
    .interactive-obj:hover {
      filter: drop-shadow(0 0 8px rgba(43, 108, 176, 0.8));
      opacity: 0.9;
    }
    .interactive-obj.active {
      filter: drop-shadow(0 0 12px #3182ce);
    }

    /* 하단 설명 카드 */
    .info-panel {
      padding: 24px;
      background: #ffffff;
      border-top: 2px solid #edf2f7;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      min-height: 120px;
    }
    .info-content {
      flex: 1;
    }
    .word-header {
      display: flex;
      align-items: baseline;
      gap: 12px;
      margin-bottom: 8px;
    }
    .word-ko {
      font-size: 28px;
      font-weight: 700;
      color: #2b6cb0;
    }
    .word-en {
      font-size: 20px;
      font-weight: 500;
      color: #718096;
    }
    .word-desc {
      font-size: 15px;
      color: #4a5568;
      line-height: 1.5;
    }
    .audio-buttons {
      display: flex;
      gap: 10px;
      flex-shrink: 0;
    }
    .btn-speech {
      padding: 12px 20px;
      font-size: 15px;
      font-weight: 600;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      transition: background-color 0.2s, transform 0.1s;
    }
    .btn-speech:active {
      transform: scale(0.97);
    }
    .btn-ko {
      background-color: #3182ce;
      color: #ffffff;
    }
    .btn-ko:hover {
      background-color: #2b6cb0;
    }
    .btn-en {
      background-color: #38a169;
      color: #ffffff;
    }
    .btn-en:hover {
      background-color: #2f855a;
    }

    @media (max-width: 640px) {
      .info-panel {
        flex-direction: column;
        align-items: flex-start;
      }
      .audio-buttons {
        width: 100%;
      }
      .btn-speech {
        flex: 1;
        justify-content: center;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>🏥 성인용 그림사전 (병원)</h1>
    <p class="subtitle">병원 안의 요소(의사, 간호사, 장비 등)를 클릭하면 단어 뜻과 발음을 들을 수 있습니다.</p>
  </header>

  <div class="dictionary-container">
    <div class="image-wrapper">
      <!-- 외부 파일 없이 100% 작동하는 SVG 병원 일러스트 -->
      <svg viewBox="0 0 1000 562" width="100%" height="100%" style="display: block;">
        <!-- 배경: 병원 내부 -->
        <rect width="1000" height="562" fill="#f4f7f6"/>
        
        <!-- 벽면 구분선 및 복도 표현 -->
        <path d="M0,350 L1000,350" stroke="#cbd5e0" stroke-width="4"/>
        <path d="M0,0 L1000,0 L1000,350 L0,350 Z" fill="#ebf8ff"/>
        <path d="M0,350 L1000,350 L1000,562 L0,562 Z" fill="#e2e8f0"/>
        
        <!-- 입원실 창문 및 병상 배경 -->
        <rect x="40" y="60" width="220" height="200" rx="8" fill="#bee3f8" stroke="#90cdf4" stroke-width="3"/>
        <line x1="150" y1="60" x2="150" y2="260" stroke="#90cdf4" stroke-width="2"/>
        
        <!-- 타이틀 텍스트 -->
        <text x="500" y="45" font-size="24" font-weight="bold" fill="#2c5282" text-anchor="middle">그림 사전: 병원</text>

        <!-- 1. 환자 & 병상 -->
        <g class="interactive-obj" id="obj-patient" onclick="selectItem(this, '환자', 'Patient', '병원의 입원실에서 치료 및 회복 중인 사람입니다.')">
          <rect x="50" y="220" width="180" height="90" rx="10" fill="#e2e8f0" stroke="#4a5568" stroke-width="3"/>
          <circle x="80" y="200" r="20" fill="#fbd38d"/> <!-- 환자 머리 -->
          <rect x="95" y="195" width="120" height="50" rx="10" fill="#cbd5e0"/> <!-- 침대 이불 -->
          <text x="140" y="280" font-size="14" font-weight="bold" fill="#2d3748" text-anchor="middle">환자 Patient</text>
        </g>

        <!-- 2. 의사 (진찰 중) -->
        <g class="interactive-obj" id="obj-doctor" onclick="selectItem(this, '의사', 'Doctor', '환자의 상태를 진찰하고 전문 치료를 시행하는 의료진입니다.')">
          <circle cx="100" cy="380" r="22" fill="#fbd38d"/>
          <path d="M75,410 L125,410 L130,500 L70,500 Z" fill="#ffffff" stroke="#2b6cb0" stroke-width="3"/> <!-- 흰 가운 -->
          <path d="M90,410 L90,450 L110,450 L110,410" fill="none" stroke="#e53e3e" stroke-width="3"/> <!-- 청진기 -->
          <text x="100" y="525" font-size="15" font-weight="bold" fill="#1a365d" text-anchor="middle">의사 Doctor</text>
        </g>

        <!-- 3. 전문의 (데스크) -->
        <g class="interactive-obj" id="obj-specialist" onclick="selectItem(this, '전문의', 'Specialist Doctor', '특정 진료 과목을 전문적으로 담당하는 의사입니다.')">
          <rect x="330" y="230" width="150" height="110" fill="#feebc8" stroke="#dd6b20" stroke-width="3" rx="5"/>
          <circle cx="405" cy="190" r="20" fill="#fbd38d"/>
          <rect x="385" y="210" width="40" height="30" fill="#3182ce"/> <!-- 수술복 -->
          <text x="405" y="285" font-size="14" font-weight="bold" fill="#7b341e" text-anchor="middle">전문의 Specialist</text>
        </g>

        <!-- 4. 간호사 스테이션 -->
        <g class="interactive-obj" id="obj-station" onclick="selectItem(this, '간호사 스테이션', 'Nurse Station', '간호사들이 환자 차트 관리 및 수속 업무를 진행하는 공간입니다.')">
          <rect x="300" y="320" width="220" height="120" rx="10" fill="#319795" stroke="#234e52" stroke-width="3"/>
          <rect x="380" y="280" width="60" height="40" fill="#2d3748"/> <!-- 모니터 -->
          <text x="410" y="380" font-size="16" font-weight="bold" fill="#ffffff" text-anchor="middle">간호사 스테이션</text>
          <text x="410" y="405" font-size="13" fill="#e6fffa" text-anchor="middle">NURSE STATION</text>
        </g>

        <!-- 5. 간호사 -->
        <g class="interactive-obj" id="obj-nurse" onclick="selectItem(this, '간호사', 'Nurse', '환자의 투약, 체온 측정 및 회복을 돕는 보건 의료 전문가입니다.')">
          <circle cx="600" cy="330" r="22" fill="#fbd38d"/>
          <path d="M575,355 L625,355 L630,480 L570,480 Z" fill="#4fd1c5" stroke="#234e52" stroke-width="2"/> <!-- 간호사복 -->
          <rect x="585" y="400" width="30" height="40" fill="#ffffff" rx="3"/> <!-- 차트판 -->
          <text x="600" y="505" font-size="15" font-weight="bold" fill="#1a365d" text-anchor="middle">간호사 Nurse</text>
        </g>

        <!-- 6. 방사선사 -->
        <g class="interactive-obj" id="obj-radiologist" onclick="selectItem(this, '방사선사', 'Radiologist', 'X-ray, CT 등의 영상 의학 장비를 다루는 전문가입니다.')">
          <circle cx="780" cy="360" r="22" fill="#fbd38d"/>
          <path d="M755,385 L805,385 L810,490 L750,490 Z" fill="#319795" stroke="#1d4044" stroke-width="2"/>
          <text x="780" y="515" font-size="15" font-weight="bold" fill="#1a365d" text-anchor="middle">방사선사 Radiologist</text>
        </g>

        <!-- 7. X-RAY 검사판 -->
        <g class="interactive-obj" id="obj-xray" onclick="selectItem(this, 'X-RAY 검사', 'X-Ray Examination', '방사선으로 뼈나 내부 장기 상태를 촬영하는 검사입니다.')">
          <rect x="800" y="380" width="70" height="50" fill="#1a202c" stroke="#e2e8f0" stroke-width="3" rx="4"/>
          <!-- 흉부 X-ray 뼈 묘사 -->
          <path d="M835,390 L835,420 M820,400 Q835,395 850,400 M820,410 Q835,405 850,410" stroke="#ffffff" stroke-width="2" fill="none"/>
          <text x="835" y="446" font-size="11" font-weight="bold" fill="#e2e8f0" text-anchor="middle">X-RAY 필름</text>
        </g>

        <!-- 8. 과장 의사 -->
        <g class="interactive-obj" id="obj-chief" onclick="selectItem(this, '과장 의사', 'Chief Doctor', '진료 과목을 총괄하며 진단 결과를 분석하고 지도를 담당하는 책임 의사입니다.')">
          <circle cx="910" cy="350" r="22" fill="#fbd38d"/>
          <path d="M885,375 L935,375 L940,490 L880,490 Z" fill="#ffffff" stroke="#2b6cb0" stroke-width="3"/>
          <text x="910" y="515" font-size="15" font-weight="bold" fill="#1a365d" text-anchor="middle">과장 의사 Chief</text>
        </g>

        <!-- 9. 활력 징후 모니터 -->
        <g class="interactive-obj" id="obj-vitals" onclick="selectItem(this, '활력 징후 모니터', 'Vital Signs Monitor', '심박수, 혈압, 산소포화도 등 생체 지표를 실시간으로 측정하는 모니터입니다.')">
          <rect x="870" y="100" width="100" height="70" fill="#1a202c" stroke="#4a5568" stroke-width="4" rx="6"/>
          <!-- 심전도 그래프 -->
          <path d="M880,135 L900,135 L905,120 L910,150 L915,130 L920,135 L960,135" stroke="#48bb78" stroke-width="2" fill="none"/>
          <text x="920" y="190" font-size="13" font-weight="bold" fill="#2d3748" text-anchor="middle">활력 징후 Vital Signs</text>
        </g>
      </svg>
    </div>

    <!-- 정보 및 발음 영역 -->
    <div class="info-panel">
      <div class="info-content">
        <div class="word-header">
          <span class="word-ko" id="word-ko">의사</span>
          <span class="word-en" id="word-en">Doctor</span>
        </div>
        <div class="word-desc" id="word-desc">그림 속 인물이나 장비를 누르면 명칭과 설명이 나오며, 음성 발음을 들을 수 있습니다.</div>
      </div>
      <div class="audio-buttons">
        <button class="btn-speech btn-ko" onclick="speak('ko')">🔊 한국어 발음</button>
        <button class="btn-speech btn-en" onclick="speak('en')">🔊 English</button>
      </div>
    </div>
  </div>

  <script>
    let currentKo = "의사";
    let currentEn = "Doctor";

    function selectItem(element, ko, en, desc) {
      document.querySelectorAll('.interactive-obj').forEach(el => el.classList.remove('active'));
      element.classList.add('active');

      currentKo = ko;
      currentEn = en;

      document.getElementById('word-ko').innerText = ko;
      document.getElementById('word-en').innerText = en;
      document.getElementById('word-desc').innerText = desc;

      speak('ko');
    }

    function speak(lang) {
      if (!('speechSynthesis' in window)) {
        alert('현재 브라우저에서는 음성 재생(TTS) 기능이 지원되지 않습니다.');
        return;
      }

      window.speechSynthesis.cancel();

      const text = lang === 'ko' ? currentKo : currentEn;
      const utterance = new SpeechSynthesisUtterance(text);
      
      utterance.lang = lang === 'ko' ? 'ko-KR' : 'en-US';
      utterance.rate = 0.9;

      window.speechSynthesis.speak(utterance);
    }
  </script>
</body>
</html>
