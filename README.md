# LGD_Production-Quality-Dashboard
# LG Display Production & Quality Dashboard

> **Vibe Coding을 활용한 디스플레이 생산·품질 현황 웹 서비스**

## 📅 날짜

**09월 09일**

---

## 📌 프로젝트 설명

Google Colab 환경에서 **HTML, CSS, JavaScript, Python Flask, Three.js, Cloudflared**를 활용하여 제작한 디스플레이 생산·품질 현황 웹 서비스입니다.

디스플레이 생산 현장에서 필요한 **생산 실적, 생산 달성률, 검사 수량, 불량률 등의 주요 생산·품질 정보**를 한 화면에서 확인할 수 있도록 구성하였습니다.

또한 Three.js와 WebGL을 이용하여 **패널 검사·이송 설비를 3D로 시각화**하고, 사용자가 마우스를 이용하여 설비를 회전하거나 확대·축소할 수 있도록 구현하였습니다.

Flask 서버와 Cloudflared를 연동하여 Google Colab에서 실행한 웹 서비스를 외부 브라우저에서도 접속할 수 있도록 구성하였습니다.

본 프로젝트의 생산 및 품질 데이터와 3D 설비는 **교육을 위한 가상 데이터 및 모의 설비**이며, 실제 LG디스플레이의 생산 데이터 또는 실제 설비 CAD 모델을 사용하지 않습니다.

---

## 🛠 사용 라이브러리 및 기술

### Python

* **Python**

  * 전체 웹 서비스 실행 및 서버 제어
  * 파일 다운로드 및 실행 환경 관리

* **Flask 3.1.2**

  * 웹 서버 구성
  * 생산·품질 데이터 제공
  * 설비 가동/정지 상태를 처리하는 API 구성

* **Werkzeug**

  * Flask 웹 서버 실행 및 관리

* **IPython.display**

  * Google Colab에서 외부 접속 주소 및 실행 결과 출력

### Front-End

* **HTML5**

  * 웹 페이지 구조 구성

* **CSS3**

  * 대시보드 UI 및 반응형 화면 디자인

* **JavaScript**

  * 버튼 이벤트 및 사용자 인터랙션 처리
  * Flask API와 비동기 통신
  * `async/await` 기반 데이터 처리

* **Three.js 0.170.0**

  * WebGL 기반 3D 생산·검사 설비 구현

* **OrbitControls**

  * 3D 설비 회전
  * 확대/축소
  * 사용자 시점 조작

### Server / Network

* **Cloudflared**

  * Google Colab의 로컬 Flask 서버를 외부에서 접속할 수 있도록 Cloudflare Tunnel 구성

### Python Standard Library

프로젝트 실행 및 서버 관리를 위해 다음 Python 기본 라이브러리를 사용하였습니다.

* `asyncio`
* `importlib.util`
* `json`
* `os`
* `pathlib`
* `re`
* `socket`
* `subprocess`
* `sys`
* `threading`
* `urllib.request`

---

## 💡 주요 기능

### 1. 생산·품질 현황 확인

교육용 가상 데이터를 이용하여 생산 및 품질 정보를 화면 상단에서 확인할 수 있도록 구현하였습니다.

| 항목     |      값 |
| ------ | -----: |
| 목표 생산량 | 1,000개 |
| 현재 생산량 |   800개 |
| 검사 수량  |   200개 |
| 불량 수량  |     4개 |
| 생산 달성률 |    80% |
| 불량률    |     2% |

생산 달성률은 다음과 같이 계산합니다.

```text
생산 달성률 = 현재 생산량 / 목표 생산량 × 100
```

불량률은 다음과 같이 계산합니다.

```text
불량률 = 불량 수량 / 검사 수량 × 100
```

---

### 2. Three.js 기반 3D 설비 구현

Three.js와 WebGL을 이용하여 패널 검사·이송 설비를 3D로 표현하였습니다.

주요 구성 요소는 다음과 같습니다.

* 패널 이송 롤러
* 디스플레이 패널
* 검사 헤드
* 금속 외장
* 반투명 유리 덮개
* 설비 상태등
* 조명
* 그림자

실제 LG디스플레이 설비를 그대로 구현한 것이 아니라 **교육 목적의 가상 3D 설비**입니다.

---

### 3. 3D 화면 조작

OrbitControls를 사용하여 사용자가 직접 설비를 확인할 수 있도록 구현하였습니다.

* 마우스 드래그 : 설비 회전
* 마우스 휠 : 확대 / 축소
* 시점 초기화 : 기본 카메라 위치로 복귀

---

### 4. 설비 가동 / 정지

웹 화면에서 **가동 및 정지 버튼**을 선택하면 Flask의 상태 API를 통해 설비 상태가 변경됩니다.

설비가 가동 상태일 경우 3D 화면에서 패널 이송 애니메이션이 실행되고, 정지 상태에서는 패널 이동이 멈추도록 구현하였습니다.

이를 통해 웹 화면의 설비 상태와 3D 모델의 상태가 동일하게 유지되도록 구성하였습니다.

---

### 5. 현황 확인 기능

`현황 확인` 버튼을 누르면 현재 생산·품질 현황을 확인했다는 메시지가 표시되도록 구현하였습니다.

```text
현황을 확인했습니다.
```

---

### 6. 반응형 웹 디자인

화면 크기에 따라 레이아웃이 자동으로 변경되도록 구성하였습니다.

큰 화면에서는

```text
3D 설비 | 설비 상태 및 조작
```

형태로 표시되고, 화면 폭이 좁아지면

```text
3D 설비
   ↓
설비 상태 및 조작
```

형태로 변경됩니다.

3D 화면 크기가 변경될 때 Three.js의 카메라 비율과 Renderer 크기도 함께 변경되도록 구성하였습니다.

---

### 7. Google Colab 외부 접속

Google Colab에서 Flask 서버를 실행한 후 Cloudflared를 이용하여 외부 접속 주소를 생성합니다.

전체 구조는 다음과 같습니다.

```text
사용자 Browser
      ↓
Cloudflare Tunnel
      ↓
Cloudflared
      ↓
Flask Server
      ↓
HTML / CSS / JavaScript
      ↓
Three.js / WebGL
```

따라서 별도의 웹 서버를 구축하지 않아도 Colab 환경에서 실행한 결과를 외부 브라우저에서 확인할 수 있습니다.

---

## 🎯 프로젝트 목적

본 프로젝트는 Vibe Coding 방식으로 생성형 AI를 활용하여 웹 서비스를 구현하고, 디스플레이 생산 현장에서 활용할 수 있는 **생산·품질 데이터 시각화 및 설비 모니터링 웹 서비스의 기본 구조를 학습하는 것**을 목적으로 제작하였습니다.

다음 과정을 중심으로 실습하였습니다.

```text
업무 문제 정의
      ↓
AI를 활용한 코드 생성
      ↓
Google Colab 실행
      ↓
웹 서비스 구현
      ↓
오류 확인 및 수정
      ↓
사용자 테스트
      ↓
기능 개선
```

---

## ⚠️ 주의사항

본 프로젝트에서 사용한 생산량, 검사량, 불량 수량 등의 데이터는 모두 **교육용 가상 데이터**입니다.

또한 Three.js로 제작한 패널 검사·이송 설비는 실제 LG디스플레이의 설비 구조나 CAD 데이터를 기반으로 제작한 것이 아닙니다.

Cloudflared에서 생성되는 접속 URL은 임시 주소이므로 Google Colab 런타임이 종료되거나 초기화되면 기존 URL을 사용할 수 없습니다.

---

## 📚 참고 문헌

### Google Colab

Google Colab FAQ
https://research.google.com/colaboratory/faq.html

Google Colab의 실행 환경 및 런타임 구성과 관련된 내용을 참고하였습니다.

### Cloudflare

Cloudflare Quick Tunnels
https://developers.cloudflare.com/cloudflare-one/networks/connectors/cloudflare-tunnel/do-more-with-tunnels/trycloudflare/

Google Colab에서 실행한 Flask 웹 서버를 외부에서 접속하기 위한 Cloudflare Tunnel 구성에 참고하였습니다.

### Three.js

Three.js Installation
https://threejs.org/manual/en/installation.html

Three.js 모듈 구성 및 WebGL 기반 3D 환경 구축 방법을 참고하였습니다.

### OrbitControls

Three.js OrbitControls
https://threejs.org/docs/pages/OrbitControls.html

3D 모델의 회전, 확대 및 축소 기능 구현에 참고하였습니다.

---

## 📂 프로젝트 파일

```text
LG-Display-Production-Quality-Dashboard/
│
├── 01_LGD_Vibe_Coding_Day1.ipynb
└── README.md
```

---

## 🖥 개발 환경

```text
Google Colab
Ubuntu
Python
Flask 3.1.2
HTML5
CSS3
JavaScript
Three.js 0.170.0
OrbitControls
WebGL
Cloudflared
```

---

## 📝 Summary

**LG Display Production & Quality Dashboard**는 Google Colab과 Flask를 기반으로 생산·품질 데이터를 웹에서 확인하고, Three.js를 이용해 디스플레이 패널 검사·이송 설비를 3D로 시각화한 교육용 Vibe Coding 프로젝트입니다.

Cloudflared를 이용하여 별도의 서버 구축 없이 외부에서 웹 서비스에 접속할 수 있도록 구현하였으며, 생산 현황 확인, 3D 설비 조작, 가동·정지 상태 변경 등의 기본적인 생산 모니터링 기능을 구현하였습니다.
