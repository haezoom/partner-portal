# partner-portal

해줌 협력사(RTU·EMS 업체)에 공개하는 **연동 표준 문서와 자기검증 도구 안내**를 GitHub Pages 로 제공하는 저장소입니다.

- 사이트: https://haezoom.github.io/partner-portal/ (Pages 활성화 후)
- 원본: `docs/` (Jekyll, 테마 just-the-docs)

> ⚠️ **이 저장소와 사이트는 공개(public)입니다.** 협력사 배포용으로 분류된 문서만 올립니다.
> 올리기 전 [`CONTRIBUTING.md`](CONTRIBUTING.md) 의 공개 전 점검 목록을 확인하십시오.

## 구조

```
docs/
  _config.yml              사이트 설정
  index.md                 첫 페이지 (연동 흐름 요약)
  standards/               표준 문서 안내 (PDF 는 docs/assets/files/ 에)
  onboarding/              온보딩 절차
  tools/                   가늠(ganeum) 저장소 링크와 간단한 설명
  changelog.md             문서·도구 변경 이력
  assets/files/            배포용 PDF·첨부
```

## 로컬 미리보기 (선택)

```bash
cd docs
bundle install
bundle exec jekyll serve      # http://localhost:4000/partner-portal/
```

## GitHub Pages 설정

Settings → Pages → Source: **Deploy from a branch** → `main` / `/docs` → Save. Enforce HTTPS 켜기.
