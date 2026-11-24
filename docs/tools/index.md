---
title: 자기검증 도구
nav_order: 3
---

# 자기검증 도구 — 가늠(ganeum)

가늠은 온보딩 과정에서 협력사가 **stg broker 에 발행하기 전에** 자사 메시지가 해줌 표준을 지키는지 로컬에서 검증하는 단일 바이너리입니다(온보딩 절차 단계 ⑤). 표준의 JSON Schema 가 내장되어 있어 별도 런타임이나 인터넷 연결 없이 실행되며, 온보딩 신청 전에도 미리 받아 써 볼 수 있습니다.

| 대상 | 지원 내용 |
|---|---|
| 태양광 | 모니터링(telemetry·info) 검증, 제어 명령(command·response·result) 검증과 서명 검증 |
| ESS (Draft) | ESS 표준 v0.2 기준 메시지 검증과 서명 검증 — 미리보기 버전 |

설치·사용법·릴리스는 가늠 저장소에서 안내합니다.

**[github.com/haezoom/ganeum](https://github.com/haezoom/ganeum){:target="_blank" rel="noopener noreferrer"}**

## ESS 미리보기 사용법 (`feature/ess-draft` 브랜치)

{: .warning }
> ESS 표준 v0.2(Draft) 기준의 미리보기입니다. 정식 릴리스 전까지 `feature/ess-draft` 브랜치로 제공하며, 표준 협의 결과에 따라 동작이 바뀔 수 있습니다.

### 1. 받아서 빌드

Go 1.26 이상이 필요합니다.

```bash
git clone -b feature/ess-draft https://github.com/haezoom/ganeum.git
cd ganeum
make build
./ganeum ess version
```

이미 저장소를 받아 두었다면:

```bash
git fetch origin
git checkout feature/ess-draft
git pull
make build
```

### 2. 자기시험

ESS 기능은 `ganeum ess <명령>` 으로 씁니다.

```bash
./ganeum ess golden                                  # 서명 골든 벡터: PASS 16 / FAIL 0
./ganeum ess validate out/                           # 내가 보낼 메시지 전수 검증
./ganeum ess validate --info out/info.json out/telemetry_*.json   # info 신고값과 telemetry 대조
./ganeum ess verify-command --keystore keystore.json --now now command.json   # 받은 제어 명령 서명 검증
./ganeum ess help                                    # 전체 명령
```

검사 대상은 **broker 에 실제로 발행하는 바이트 그대로**여야 합니다. publish 직전의 값을 파일로 남겨 그 파일을 검증하십시오.

### 3. 자세한 안내

- [ESS 프로필 README](https://github.com/haezoom/ganeum/blob/feature/ess-draft/docs/ess/README.md)
- [ESS QUICKSTART](https://github.com/haezoom/ganeum/blob/feature/ess-draft/docs/ess/QUICKSTART.md)
- [범위·협의 중 항목 (DRAFT_NOTES)](https://github.com/haezoom/ganeum/blob/feature/ess-draft/docs/ess/DRAFT_NOTES.md)
