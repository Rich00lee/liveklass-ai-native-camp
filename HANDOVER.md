# Handover — 2026-03-12 (세션 3)

## 작업 요약

### GitHub Pages 배포 확인 + 404 해결
- 배포 URL 접속 → 404 에러 발견
- 원인: Pages 빌드가 트리거되지 않은 상태 (빈 배열)
- 해결: `gh api repos/.../pages/builds -X POST`로 수동 빌드 트리거
- **배포 URL**: `https://rich00lee.github.io/liveklass-ai-native-camp/slides/session5-showcase.html`

### p10 Ethan 파이프라인 이미지 여백 조정
- `expansion-flow.png` `w:1000` → `w:800`으로 변경

### Vivi 피드백 5건 전면 반영
1. `/ps` 워크플로우 → mermaid 가로형 플로우차트 (`vivi-workflow.png`)
2. 연동 서비스 구조도 이미지 (`vivi-services.png`) 추가
3. 실사용 개선 사례 B/A 테이블 슬라이드 신규 추가 (Case 1: 퍼미션, Case 2: SMS)
4. 추후 과제 업데이트 (`/arrange` 구현 완료 반영, 채용 브랜딩 에이전트 추가)
5. "의도적 비자동화" 한 줄 강조 추가

### Git 커밋 (5개)
- `95e3dbf` fix: p10 Ethan 파이프라인 이미지 여백 확보
- `42228fa` feat: Vivi 피드백 5건 반영
- `d7582b0` fix: Vivi 플로우차트 크기 확대 + 연동 구조도 테이블 제거
- `99089e6` fix: Vivi 플로우차트 가로형으로 재구성
- `1e26429` fix: Vivi 플로우차트 파일명 변경 (CDN 캐시 우회)

## 성공/실패 기록

### 성공
- mermaid CLI(`npx @mermaid-js/mermaid-cli`)로 복잡한 플로우차트를 슬라이드용 이미지로 즉시 렌더링
- 세로형 10단계 → 가로형 4단계 압축으로 가독성 대폭 개선

### 실패/회피
- GitHub Pages CDN 캐시: 동일 파일명으로 이미지 교체 시 CDN이 이전 버전 유지 → 파일명 변경으로 우회 (`vivi-flow.png` → `vivi-workflow.png`)

## 주의사항 & 교훈
- **Marp 빌드 명령**: `marp session5-showcase.md --theme theme.css --pdf --allow-local-files --no-stdin`
- **HTML 빌드**: `marp session5-showcase.md --theme theme.css --allow-local-files --no-stdin -o session5-showcase.html`
- **gh auth**: `gh auth switch --user Rich00lee` 필요할 수 있음
- **PR 머지**: branch protection 때문에 `--admin` 플래그 필요
- **GitHub Pages CDN**: 이미지 파일명 바꿔야 캐시 우회됨
- **mermaid 가로형**: `flowchart LR` + 단계 압축이 슬라이드에 적합

## 다음 단계

- **[P0] Jay (정영현) 슬라이드 채우기** — p37 placeholder. Jay PDF 수령 여부 Slack 확인
- **[P0] Slack 잔여 피드백 확인 + 최종 빌드** — 밤사이 추가 피드백 일괄 반영 → PDF/HTML 빌드 → push
- **[P1] 발표 당일(3/13 금 10:15) 리허설** — GIF 시연 슬라이드는 HTML 버전 사용 권장
- **[P2] Vivi 플로우 시각화 추가 개선** — 별도 이미지 파일 제작 필요 시

## 중요 파일 맵

| 파일 | 역할 |
|------|------|
| `docs/slides/session5-showcase.md` | Session 5 Marp 발표 장표 (메인) — **48슬라이드** |
| `docs/slides/session5-showcase.html` | 빌드된 HTML (GIF 지원, GitHub Pages 배포) |
| `docs/slides/session5-showcase.pdf` | 빌드된 PDF |
| `docs/slides/theme.css` | 커스텀 Marp 테마 (`lk-camp`) |
| `docs/slides/vivi-workflow.png` | Vivi /ps 워크플로우 (가로형, **신규**) |
| `docs/slides/vivi-services.png` | Vivi 연동 서비스 구조도 (**신규**) |
| `docs/slides/expansion-flow.png` | Ethan 검증 파이프라인 다이어그램 |
| `docs/slides/theo_rocket_automation.gif` | Theo 리드 자동 분석 시연 GIF (21MB) |
| `docs/slides/figma-plugin.gif` | Arin Figma 플러그인 시연 GIF |
