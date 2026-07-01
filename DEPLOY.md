# makemind_git — Deploy & Build (SSOT)

> 배포 시 확인할 유일 근거.

## 한 줄 요약
**GitHub Pages** 로 호스팅되는 정적 공개 인트로 사이트 ("makemind — Let AI Execute Anything"). **Firebase 아님.**

## 사실
| 항목 | 값 |
|---|---|
| 성격 | 오픈소스 AppPlayer 생태계 **공개 소개/랜딩** (정적 `index.html`) |
| 호스팅 | **GitHub Pages** (`.nojekyll`, 빌드 없음 — 소스가 곧 배포물) |
| Git | `github.com/app-appplayer/makemind` (메인 리포) · 발행자 mcpdevstudio |
| 빌드 | 없음 (정적 HTML/CSS/JS 직접) |
| **검색 색인** | **허용(색인 대상)** — 완성된 공개 사이트이므로 noindex **하지 않음**. (다른 홈페이지들과 반대) |

## 배포
GitHub Pages = 리포 push 시 자동 반영 (Pages 설정에 따름). 별도 firebase deploy 없음.
```bash
cd homepage/makemind_git
git add -A && git commit -m "<설명>" && git push
```

## 주의
- 다른 홈페이지(makemind_app·appplayer_app·safepage_app·makemind_guild·makemind_dev)는 미완성이라 noindex 차단. **이 사이트만 예외로 색인 허용.** 혼동 금지.
