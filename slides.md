---
theme: default
title: 로봇 동작 시연
colorSchema: light
css: ./style.css
fonts:
  sans: Chiron GoRound TC
  weights: '400,700'
  provider: google
---

<!-- 첫 슬라이드 -->
<div class="flex flex-col h-full">

  <div class="text-right">
  
  ## 시스템분석설계
  <br>
  <br>
  <br>

  # 영어 대사 파트너 
  # 로봇 및 웹 구현
  
  </div>
  <br>
  <br>
  <br>
  <div class="text-left mt-auto">
  
  ### Triplelingo
  ### 4주차 발표
  
  </div>
  
  <div class="text-right">

  ##### 장혜미(팀장)_20232315 · 윤설희(조원)_20232307 · 비다(조원)_20242195
  
  </div>
</div>

---
layout: two-cols
---

<!-- 슬라이드(Slide) No.2 -->
# 목차

<br>
<br>

1. 하드웨어 설계
   - 구성요소 및 전체 연결도
   - 부품 소개 및 위치 구상

<br>

2. 텍스트 구분 기술
   - 배역별 대사 구분(re모듈)
   - 감정 및 분위기 파악
      1. Vader
      2. Transformers

<br>

3. 음성 구분 기술
   - ms사의 azure

::right::

<img src="/robotMoving.gif" class="w-full h-80% object-contain" />

<div class="text-center">

로봇의 고개 시뮬레이션

</div>


---

<!-- 슬라이드(Slide) No.3 -->
## 1. 하드웨어 설계
### - 구성요소 및 전체 연결도

<div style="top: 280px">

### 로봇이 작동하는 과정에서
### 네 가지 하드웨어가 
### 각자의 역할을 맡아 함께 동작

</div>

<img src="/hardware_diagram.png" style="position: absolute; right: 35px; top: 70px; width: 600px;" />



---

<!-- 슬라이드(Slide) No.4 -->
## 1. 하드웨어 설계
### 부품 소개 및 위치 구상

<div style="top: 380px">

부품 1. MG996R 서보제어(메탈 기어)

</div>


<div style="
  position: absolute; 
  left: 55px; 
  top: 140px; 
  width: 250px; 
  font-size: 10px; 
  line-height: 1.2;
">

| 축 | 역할 | 모델 |
|:---:|:---:|:---:|
| TILT | 양 어깨 움직임 | (Y축)MG996 |
| ROLL | 고개 좌우 회전 | (Z축)MG996 |
| PAN | 고개 끄덕임 | (X축)MG996 |

</div>

<img src="/servoMG.png" style="position: absolute; left: 65px; top: 280px; width: 220px;" />



<img src="/mgMoving.gif" style="position: absolute; right: 1px; top: 120px; width: 630px;" />

<style>
/* 표 디자인 강제 적용 */
table { 
  border-collapse: collapse !important; 
  width: 100% !important; 
}
th { 
  background-color: #333 !important; 
  color: #e2e2e3 !important; 
  padding: 6px !important; 
}
td { 
  padding: 6px !important; 
  border-bottom: 1px solid #444 !important;
  font-size: 10px !important; 
}
</style>

---


<!-- 슬라이드(Slide) No.5 -->
## 1. 하드웨어 설계
### 부품 소개 및 위치 구상

<div style="top: 380px">

부품 2. 마이크(ReSpeaker 2-Mics Pi HAT) --------------------- 두 개의 마이크, HAT 소켓, GPIO 헤더를 통해 RPi에 직결

</div>

<div style="
  position: absolute; 
  left: 55px; 
  top: 140px; 
  width: 250px; 
  font-size: 10px; 
  line-height: 1.2;
">

| 항목 | 내용 |
|:---:|:---:|
| 연결 | GPIO HAT (라즈베리 파이에 바로 꽂음) |
| 마이크 | 듀얼 MEMS 마이크 내장 |
| 특징 | 음성인식 특화 설계, 소리 크기 감지 용이 |

</div>

<img src="/mics.png" style="position: absolute; left: 65px; top: 280px; width: 220px;" />

<img src="/step1.jpeg" style="position: absolute; right: 5px; top: 80px; width: 625px;" />


<style>
/* 표 디자인 강제 적용 */
table { 
  border-collapse: collapse !important; 
  width: 100% !important; 
}
th { 
  background-color: #333 !important; 
  color: #e2e2e3 !important; 
  padding: 6px !important; 
}
td { 
  padding: 6px !important; 
  border-bottom: 1px solid #444 !important;
  font-size: 10px !important; 
}
</style>

---

<!-- 슬라이드(Slide) No.6 -->
## 1. 하드웨어 설계
### 부품 소개 및 위치 구상

<div style="top: 380px">

부품 3. MAX98357A 앰프 모듈(+스피커) ------------ I2S, "Inter-IC Sound"의 약자로, 디지털 음향 신호를 전달하는 방식

</div>

<div style="
  position: absolute; 
  left: 40px; 
  top: 140px; 
  width: 280px; 
  font-size: 10px; 
  line-height: 1.2;
">

| 항목 | 내용 |
|:---:|:---:|
| 연결방식 | I2S (디지털 신호, GPIO 18·19·21 핀) |
| 출력 | 최대 3W |
| 장점 | 헤드폰잭보다 잡음이 거의 없고 음성이 선명함 |

</div>

<img src="/speakerModule.png" style="position: absolute; left: 65px; top: 280px; width: 220px;" />

<img src="/step2.jpeg" style="position: absolute; right: 5px; top: 80px; width: 625px;" />

<style>
/* 표 디자인 강제 적용 */
table { 
  border-collapse: collapse !important; 
  width: 100% !important; 
}
th { 
  background-color: #333 !important; 
  color: #e2e2e3 !important; 
  padding: 6px !important; 
}
td { 
  padding: 6px !important; 
  border-bottom: 1px solid #444 !important;
  font-size: 10px !important; 
}
</style>

---

<!-- 슬라이드(Slide) No.7 -->
## 1. 하드웨어 설계
### 부품 소개 및 위치 구상

<div style="top: 380px">

부품 3. 8Ω 3W 소형 스피커(+모듈)

</div>

<div style="
  position: absolute; 
  left: 55px; 
  top: 140px; 
  width: 250px; 
  font-size: 10px; 
  line-height: 1.2;
">

| 항목 | 내용 |
|:---:|:---:|
| 규격 | 8Ω / 3W |
| 크기 | 약 40mm 직경 (로봇 흉상에 내장 가능) |
| 연결 | MAX98357A 출력단에 납땜 또는 JST 커넥터 |

</div>

<img src="/speaker2.jpg" style="position: absolute; left: 65px; top: 280px; width: 220px;" />

<img src="/step3.jpeg" style="position: absolute; right: 5px; top: 80px; width: 625px;" />

<style>
/* 표 디자인 강제 적용 */
table { 
  border-collapse: collapse !important; 
  width: 100% !important; 
}
th { 
  background-color: #333 !important; 
  color: #e2e2e3 !important; 
  padding: 6px !important; 
}
td { 
  padding: 6px !important; 
  border-bottom: 1px solid #444 !important;
  font-size: 10px !important; 
}
</style>

---
layout: two-cols
---

<!-- 슬라이드(Slide) No.8 -->
## 1. 하드웨어 설계
### 부품 소개 및 위치 구상

<br>

### LCD 미리보기

<div style="
  position: absolute; 
  left: 1px; 
  top: 150px; 
  width: 260px;  /* 슬라이드에서 실제로 보일 가로폭 */
  height: 280px; /* 슬라이드에서 실제로 보일 세로높이 */
  border: 1px solid #333; /* 위치 확인용 (나중에 지우세요) */
  overflow: hidden;
">
  
  <iframe 
    src="/lcd.html" 
    scrolling="no"
    style="
      width: 550px;   /* html의 실제 가로 내용 폭 */
      height: 700px;  /* html의 실제 세로 내용 폭 (버튼 포함) */
      border: none;
      transform: scale(0.5); /* 부모 박스(400px)에 맞게 비율 조정 */
      transform-origin: top left; /* 왼쪽 상단 기준으로 줄여야 위치 잡기 편함 */
    " 
  />
</div>

<div style="
  position: absolute; 
  left: 20px; 
  bottom: 10px; /* 바닥에서 40px 위로 띄움 */
  color: #888;
">
  부품 4. TFT LCD
</div>

::right::

<div style="
  position: absolute; 
  top: 60px; 
  width: 400px; 
  font-size: 15px; 
  line-height: 1.2;
">

|  | 제품 | 용도 |
|:---:|:---:|:---:|
| LCD | 3.5인치 TFT LCD (480×320) | 파형 + 입모양 |
| 연결 | SPI 또는 GPIO 직결 | 라즈베리 파이 직결 |
| 소프트웨어 | pygame | Python으로 실시간 렌더링 |

</div>

<img src="/lcd2.jpg" style="position: absolute; top: 200px; width: 300px;" />

<style>
/* 표 디자인 강제 적용 */
table { 
  border-collapse: collapse !important; 
  width: 100% !important; 
}
th { 
  background-color: #333 !important; 
  color: #e2e2e3 !important; 
  padding: 6px !important; 
}
td { 
  padding: 6px !important; 
  border-bottom: 1px solid #444 !important;
  font-size: 10px !important; 
}
</style>

---

<!-- 슬라이드(Slide) No.9 -->
## 1. 하드웨어 설계
### 부품 소개 및 위치 구상

<br>
<br>

### 하드웨어 흐름

<br>

### 마이크(I2S)로 음성 수집 
### → RPi가 AI 처리 
### → I2S 신호로 
### 앰프(MAX98357A) 전달
### → 8Ω 스피커 출력
### → SPI로 LCD에 입모양 렌더링

<img src="/step4.jpeg" style="position: absolute; right: 5px; top: 80px; width: 625px;" />

<div style="
  position: absolute; 
  right: 200px; 
  bottom: 10px; /* 바닥에서 40px 위로 띄움 */
  color: #888;
">
  SPI는 "Serial Peripheral Interface"의 약자
</div>


---
layout: two-cols
---

<!-- 슬라이드(Slide) No.10 -->
## 2. 텍스트 구분 기술
### 배역별 대사 구분(re 모듈)

<br>

###  = 패턴(정규표현식)을 이용해
### 문자열을 탐색·추출·변환하는 모듈 

::right::


 ## : 으로 구별 
 import re
<br><br>
text = """John: Hello, how are you?
Mary: I'm fine, thanks.
John: Good to hear that."""

pattern = r"(\w+): (.+)"

matches = re.findall(pattern, text)

for speaker, line in matches:
  print(speaker, "->", line)

<br>
<hr>

### 결과 

John -> Hello, how are you?
<br>
Mary -> I'm fine, thanks.
<br>
John -> Good to hear that.


---

<!-- 슬라이드(Slide) No.11 -->
## 2. 텍스트 구분 기술
### 감정 및 분위기 파악

<br>

# 1. VADER

### 구성 요소

- (1) 감성 사전(Lexicon)
<br>
   - 단어마다 '감정 점수(valence)'가 있음 
   - → 범위: 보통 -4 ~ +4

- (2) 규칙 보정(Rule-based adjustments)
<br>
단어 점수만 쓰지 않고, <br>문맥을 반영하는 규칙을 적용


<img src="/vader.png" style="position: absolute; right: 100px; top: 30px; width: 400px;" />

---

<!-- 슬라이드(Slide) No.11 -->
## 2. 텍스트 구분 기술
### 감정 및 분위기 파악

<br>

# 1. VADER


### 계산 과정 (핵심 알고리즘 흐름)
1. 문장을 단어 단위로 분리
2. 각 단어의 감정 점수 조회
3. 규칙 적용해서 점수 수정
4. 전체 점수 합산
5. 정규화(normalization)


VADER는 항상 이 4개를 반환함:
<br>
pos → 긍정 비율
<br>
neu → 중립 비율
<br>
neg → 부정 비율
<br>
compound → 전체 감정 점수

<img src="/vader_fo.jpeg" style="position: absolute; right: 150px; top: 60px; width: 300px;" />

---
layout: two-cols
---

<!-- 슬라이드(Slide) No.13 -->
## 2. 텍스트 구분 기술
### 감정 및 분위기 파악

<br>

# 2. Transformers


### 특징
- 문맥 이해 가능
- 문장 의미 파악
- 번역, 요약 가능

::right::

<br>
<br>

문장을 처리하기 위한 딥러닝 모델 구조(아키텍처)<br>
### → 특히 자연어 처리(NLP)를 혁신한 모델로 <br>
최신 NLP 모델(BERT, GPT 등)을 쉽게 가져다 쓰는 라이브러리


<div style="
  position: absolute; 
  top: 300px; 
  right: 5px;
  width: 500px; 
  font-size: 20px; 
  line-height: 1.8;
">

| 장점 | 단점 |
|:---:|:---:|
| 병렬 처리 → 빠름 | 계산량 큼 (GPU 필요) |
| 긴 문장 잘 처리 | 데이터 많이 필요 |
| 성능이 뛰어남 | 해석이 어려움(블랙박스 구조) |

</div>

<style>
/* 표 디자인 강제 적용 */
table { 
  border-collapse: collapse !important; 
  width: 100% !important; 
}
th { 
  background-color: #333 !important; 
  color: #e2e2e3 !important; 
  padding: 6px !important; 
}
td { 
  padding: 6px !important; 
  border-bottom: 1px solid #444 !important;
  font-size: 10px !important; 
}
</style>


---
layout: two-cols
---

<!-- 슬라이드(Slide) No.11 -->
## 2. 텍스트 구분 기술
### 감정 및 분위기 파악

<br>

# 3. VADER VS Transformers

### vader 구조  
단어 사전 + 규칙 
<br>
→  점수 계산


### Transformers 구조
문장 → 토큰화 
<br>→ 신경망 → 의미 이해 → 결과


::right::

<div style="
  position: absolute; 
  top: 100px; 
  right: 5px;
  width: 500px; 
  font-size: 20px; 
  line-height: 1.8;
">

| 항목 | VADER | Transformers |
|:---:|:---:|:---:|
| 속도 | 매우 빠름 | 느림 |
| 이모지 | 잘 처리 | 모델에 따라 다름|
| 풍자(sarcasm) | 약함 | 어느 정도 가능|
| 정확도 | 중간 | 매우 높음 |
| 문맥이해 | 거의 없음 | 매우 높음 |
| 설정 | 쉬움 | 복잡 |

</div>

<style>
/* 표 디자인 강제 적용 */
table { 
  border-collapse: collapse !important; 
  width: 100% !important; 
}
th { 
  background-color: #333 !important; 
  color: #e2e2e3 !important; 
  padding: 6px !important; 
}
td { 
  padding: 6px !important; 
  border-bottom: 1px solid #444 !important;
  font-size: 10px !important; 
}
</style>

---
layout: two-cols
---

<!-- 슬라이드(Slide) No.14 -->
## 3. 음성 구분 기술
### MS사의 AZURE

## 주요 기능

1️⃣ 클라우드 서비스
 - Virtual Machine
 - Storage
 - DB

<br>

2️⃣ AI 서비스
 - Speech-to-Text
 - Text-to-Speech
 - Pronunciation Assessment
 - NLP


::right::

Azure 발음 평가 (Pronunciation Assessment)
### : 사용자 음성 오디오 분석 (Speech-to-Text 기술 사용)
### -> 평가 항목: 정확도, 유창성
<br>

## 영어 대화 로봇에서 역할


✔️ 음성 입력
   - 사용자가 말하면 → 텍스트로 변환

✔️ 발음 평가
   - 발음 정확도 점수 제공

✔️ 음성 출력
   - 로봇이 자연스럽게 말함


---
layout: two-cols
---

<!-- 슬라이드(Slide) No.14 -->
## 3. 음성 구분 기술
### MS사의 AZURE

<br><br>

# Azure 발음 평가
## 핵심 점수

<br>

- Accuracy → 발음 정확도
- Fluency → 유창성
- Prosody → 억양/강세
- Completeness → 완성도

::right::

<img src="/azure.jpg" style="position: absolute; right: 100px; top: 30px; width: 400px;" />

---
layout: center
class: text-center
---

# 감사합니다

<div class="mt-10 opacity-80">
  <p class="text-xl mb-4">발표를 경청해 주셔서 감사합니다.</p>
  <p class="text-gray-400">Team_Triplelingo</p>
</div>

<div class="mt-15 py-4 px-10 border-t border-b border-gray-700 inline-block">
  <span class="text-2xl font-bold tracking-widest text-blue-400">Q & A</span>
</div>


<style>
/* 마지막 페이지 전용 폰트 스타일 */
h1 {
  font-size: 40px !important;
  font-weight: 900 !important;
  letter-spacing: -2px;
  background: linear-gradient(45deg, #3b82f6, #06b6d4);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>