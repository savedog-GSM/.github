<p align="center">
  <img src="https://raw.githubusercontent.com/savedog-GSM/Client/dev/public/savedog-icon.png" width="96" alt="지켜멍 로고" />
</p>

<h1 align="center">지켜멍</h1>

<p align="center">시각장애인의 이동을 돕는 로보독과 웹 관제 서비스</p>

<p align="center">
  <a href="https://savedog.vercel.app">웹 서비스</a> ·
  <a href="https://github.com/savedog-GSM/Client">프론트엔드</a> ·
  <a href="https://github.com/savedog-GSM/Server">백엔드</a> ·
  <a href="https://github.com/savedog-GSM/SaveDog--relay">로보독 중계</a>
</p>

## 프로젝트 소개

지켜멍은 로보독이 수집한 주변 정보를 웹에서 확인하고 이동을 보조하는 프로젝트입니다. 센서와 카메라로 주변 상황을 파악하고, 스마트폰 위치와 지도 경로를 함께 보여줍니다.

광주소프트웨어마이스터고등학교 UPDOWN 팀이 개발하고 있습니다.

## 주요 기능

| 기능 | 내용 |
| --- | --- |
| 실시간 관제 | 센서값, 위험도, 연결 상태와 위치 확인 |
| 예상 이동 경로 | 카카오 도보 경로를 지도에 표시하고 거리·시간·이동 안내 제공 |
| 로보독 제어 | 웹에서 이동·정지 명령 전달 |
| 카메라 인식 | 중계 프로그램이 보낸 사진과 서버의 물체 인식 결과 확인 |
| 위험 알림·신고 | 주의·위험 상태 확인, 신고 내역 검토와 처리 |
| 스마트폰 위치 전송 | GPS 위치를 서버로 전달 |
| 모바일 편의시설 화면 | 큰 화장실·편의점 버튼과 한국어 음성 안내 |
| 시연 모드 | 실제 연결과 구분되는 예시 데이터로 기능 소개 |

편의시설 검색과 경로 제공은 백엔드 연동 준비 단계입니다. 예상 이동 경로는 일반 도보 경로이며 실시간 장애물을 반영한 자율 주행 경로는 아닙니다.

## 저장소 구성

| 저장소 | 역할 | 주요 기술 | 담당 |
| --- | --- | --- | --- |
| [Client](https://github.com/savedog-GSM/Client) | 웹 관제, 지도, 스마트폰 화면과 음성 안내 | React, TypeScript, Vite, STOMP, Kakao Maps | [jiwoo1222](https://github.com/jiwoo1222) |
| [Server](https://github.com/savedog-GSM/Server) | 센서·위치 수신, 위험도 판단, 로봇 명령, 물체 인식과 실시간 전송 | Spring Boot, WebSocket, YOLO | [ci667702-star](https://github.com/ci667702-star) |
| [SaveDog--relay](https://github.com/savedog-GSM/SaveDog--relay) | 로보독과 서버 사이의 센서·사진·제어 명령 중계 | Python, Bluetooth, OpenCV | [hyeinggu](https://github.com/hyeinggu) |

각 저장소의 실행 방법과 API·장비 설정은 해당 저장소의 README에서 확인합니다.

## 연결 구조

```text
로보독 ↔ Bluetooth ↔ Python 중계 프로그램 ↔ Spring 서버 ↔ 웹 관제
                                                 ↑
                                           스마트폰 GPS

웹 지도 ↔ Vercel 함수 ↔ 카카오 도보 API
```

## 협업 방식

1. 각 파트 담당자가 기능과 변경할 내용을 설명하는 이슈를 작성합니다.
2. `dev`에서 작업 브랜치를 만들고 작업 단위로 커밋합니다.
3. `dev`를 대상으로 PR을 작성하고 변경 이유와 확인 결과를 남깁니다.
4. 해당 파트 담당자의 리뷰와 AP(Approve)를 받은 뒤 병합합니다.
5. 배포할 변경은 `dev`를 거쳐 `main`으로 반영합니다.

| 구분 | 형식 |
| --- | --- |
| 이슈 | `[type] 작업 내용` |
| 브랜치 | `feature/작업내용`, `fix/작업내용`, `refactor/작업내용` |
| 커밋 | `type :: 작업내용 #이슈번호` |
| PR | `[type/#이슈번호] 작업 내용` |

기능별로 이슈와 PR을 나누고 관련 없는 변경을 한 커밋에 모으지 않습니다. 담당자가 확인해야 하는 부분은 PR에 명시합니다.
