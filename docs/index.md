---
title: 홈
nav_order: 1
---

# 해줌 협력사 포털

해줌과 MQTT 표준으로 연동하는 RTU·EMS 협력사를 위한 문서와 도구를 모았습니다.

## 연동 흐름

| 단계 | 할 일 | 안내 |
|---|---|---|
| 1. 표준 확인 | 자원 종류(태양광·ESS)에 맞는 표준 문서를 읽습니다 | [표준 문서](standards/) |
| 2. 온보딩 신청 | RTU 목록과 담당자 정보를 제출하고, stg 접속정보·자격증명을 받습니다 | [온보딩](onboarding/) |
| 3. 온보딩 — 로컬 자기시험 | 가늠(ganeum)으로 broker 에 실제로 보낼 메시지를 검증합니다 | [자기검증 도구](tools/) |
| 4. 온보딩 — stg 검증 | stg 에 발행하고, 해줌의 수신 확인을 거쳐 통과 통보를 받습니다 | [온보딩](onboarding/) |
| 5. 운영 전환 | 실제 RTU 로 다시 등록하고 운영 환경으로 전환합니다 | [온보딩](onboarding/) |

가늠은 공개 도구라 온보딩을 신청하기 전에도 미리 받아 써 볼 수 있습니다.

## Phase별 진행

Phase1(모니터링)은 측정·상태 데이터 발행만, Phase2(제어)는 여기에 제어 명령 수신과 응답이 더해집니다.

| 구분 | 가늠 CLI (온보딩) | STG (온보딩) | PROD (운영) |
|---|---|---|---|
| **Phase1(모니터링)** | telemetry·info 메시지를 로컬에서 자체 검증 | 서버 인증서 검증 + 아이디·비번으로 접속 → telemetry·info 발행 → 해줌이 스키마·주기·rtu_id·시각 확인 후 통과 통보 | 실제 RTU 로 다시 등록 → 운영 자격증명으로 상시 모니터링 |
| **Phase2(제어)** | 명령 서명 검증(골든 벡터) + ACK·result 응답 판정 | mTLS 인증서로 접속 → 명령 서명 검증 → 즉시 제어(IMMEDIATE) 수용·적용·result 시험 | mTLS·명령 서명 검증을 거쳐 실제 충·방전 제어 |

### 인증서·서명키

Phase별로 쓰는 인증서와 서명키, 갱신 방식입니다. 이미지를 누르면 원본 크기로 볼 수 있습니다.

[![해줌 MQTT 표준의 인증서/서명키 사용 안내]({{ '/assets/images/mqtt-cert-signing-guide.png' | relative_url }})]({{ '/assets/images/mqtt-cert-signing-guide.png' | relative_url }})
