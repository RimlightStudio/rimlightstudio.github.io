# 전력재판 : 육도윤회 공식 사이트 (GitHub Pages)

티저 랜딩(풀스크린 루프 영상, 클릭 → 블로그) + 개발일지 블로그. Jekyll 내장 빌드라 **로컬에 아무것도 설치 안 해도** 된다. 게임 레포와 **완전히 분리된** 별도 공개 레포로 운영.

## 최초 셋팅 (한 번, 10분)
1. GitHub 계정(또는 팀 Organization, 예: `rimlight-studio`) 로그인
2. **New repository** → 이름을 정확히 `<계정명>.github.io` (예: `rimlight-studio.github.io`) · **Public** · README 없이 생성
3. 이 폴더를 그 레포에 푸시 (Fable이 대신 가능 — 계정명만 알려주면 됨):
   ```
   git init && git add . && git commit -m "site: 초기 뼈대" && git branch -M main
   git remote add origin https://github.com/<계정명>/<계정명>.github.io.git && git push -u origin main
   ```
4. 레포 **Settings → Pages** → Source: `Deploy from a branch` · Branch: `main` / `(root)` → Save
5. 1~2분 뒤 `https://<계정명>.github.io` 접속. `_config.yml`의 `url:`에 이 주소 기입 후 커밋(OG 이미지 경로용)
6. (선택) 커스텀 도메인: 도메인 구매(가비아 등) → Settings → Pages → Custom domain 입력 → DNS에 안내된 A/CNAME 추가 → HTTPS 체크. 체크는 몇 시간 걸릴 수 있음

## 글 쓰는 법 (매번, 3분)
- `_posts/YYYY-MM-DD-제목영문.md` 파일 하나 추가. 맨 위:
  ```
  ---
  title: "8월 개발일지 — 첫 폰 빌드"
  author: 김찌
  ---
  ```
  그 아래는 마크다운. 이미지/GIF는 `assets/media/`에 넣고 `![설명](/assets/media/파일.gif)`.
- GitHub 웹에서도 됨: 레포 → `_posts` → **Add file → Create new file** → 붙여넣기 → Commit. 1~2분 뒤 반영.
- `published: false`면 빌드에서 제외(초안). 지우면 발행.

## 티저 영상 교체
- `assets/media/teaser.mp4` (10~15초 · 1080p · H.264 · 10MB 이하 권장 — 모바일 자동재생은 **무음 필수**, 이미 `muted`)
- `assets/media/teaser.jpg` = 영상 못 트는 환경용 포스터 · `og.jpg` = 링크 공유 썸네일(1200×630)
- ffmpeg 한 줄(Fable): `ffmpeg -i 원본.mp4 -t 15 -vf "scale=1920:-2" -c:v libx264 -crf 26 -an -movflags +faststart teaser.mp4`

## 제한·주의
- 파일 100MB 이하 · 레포 1GB · 월 전송 100GB(소프트) — 긴 영상은 유튜브 **미등록** 업로드 후 `<iframe>` 임베드
- 공개 레포 = 여기 올린 건 전부 공개. 원본 PSD·대본·내부 문서는 절대 넣지 않는다
- 방문 통계 원하면 Cloudflare Web Analytics(무료·쿠키 없음) 스크립트 한 줄을 `_layouts/default.html` `<head>`에
- 댓글 원하면 giscus(GitHub Discussions 기반, 무료) — 필요 시 Fable이 붙임

## 검색 유입 (배포 직후 1회)
- 구글: https://search.google.com/search-console → 속성 추가(URL 접두어) → HTML 태그 인증(`_layouts/default.html` `<head>`에 메타 1줄) → 사이트맵 `https://<주소>/sitemap.xml` 제출
- 네이버: https://searchadvisor.naver.com → 사이트 등록 → HTML 태그 인증 → 요청 → 사이트맵 제출(같은 sitemap.xml). 네이버 자사 블로그만큼 강하진 않지만 고유 키워드(전력재판·육도윤회·림라이트)는 잡힌다
- 글마다 `description:` 한 줄을 front matter에 쓰면 검색 결과·트위터 카드 문구로 쓰인다 (jekyll-seo-tag)

## 발견 레이어 (플랫폼 피드가 있는 곳)
- **itch.io**: 게임 페이지 + devlog 탭. 인디 팬 피드·태그 노출 + **M3 데모 배포 채널**(APK·비밀 페이지·키 배포) 겸용. 커스텀 CSS 가능
- **Postype**(선택): 원화·창작 팬덤 결. X 반응 보고 필요 시 미러링
