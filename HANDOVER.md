# Handover — 2026-03-12

## 작업 요약

### Session 5 Marp 장표 제작 (주요 작업)
- **1부 Keynote 슬라이드 3장 추가** — LinkedIn 글 기반으로 "AI 에이전트를 사내에 배포하려다 멈췄다" → "왜 멈췄는가" → "그래서, AI Native Camp" 흐름 구성
  - `docs/slides/session5-showcase.md` (line 23~50)
- **2부 패널토크 슬라이드 추가** — 쉬는시간 + 연사 Keynote("조직이 AX를 정석적으로 실패하는 방법") + 패널토크("우리 조직은 어떻게 AX를 할 수 있을까?") 안내 페이지
  - `docs/slides/session5-showcase.md` (line 329~361)
- **다음 스텝 슬라이드 개편** — Eddie 피드백 반영: Claude Team Standard 시트 유지 항목 제거 → "1기 수료생 주도 팀별 확산 + 전 구성원 Claude Code 온보딩 + AX Meetup 정기 개최"로 변경
  - `docs/slides/session5-showcase.md` (line 364~372)

### Showcase 레포 PR 리뷰 & 머지
- **PR #6** (Sangsu/Eddie): 강의 링크 → 리드마그넷+워크북 PDF 자동 생성 — 머지 완료
- **PR #7** (Ethan 업데이트): 65개 → 412개 채널 전수 검증 결과 반영 — 머지 완료
- **PR #8** (Theo): 로켓런칭 리드 자동 분석 시스템 — 머지 완료
- 레포: `Rich00lee/lk-ai-camp-showcase`

### 장표 참여자 슬라이드 업데이트
- **Ethan**: 수치 전면 업데이트 (65→412채널, 5시간→30시간+, 1,970셀/343건) + "왜 AI여야 했는가" 상세 슬라이드 추가 (멀티모달 설명, 컬럼별 불일치 분포)
- **Theo**: placeholder → 실제 내용 (로켓런칭 리드 자동 분석 + B/A 테이블) 2슬라이드
- **Sangsu(Eddie)**: 신규 추가 — 강의 링크 → 리드마그넷+워크북 PDF 자동 생성 + 고객사 적용 시나리오 2슬라이드

### 참여자 피드백 반영
- **Vivi 피드백 6항목**: 스크린샷 확대(w:260→w:400), 인사이트 문구 교체, 플로우 아이콘 추가, 개선 발견 계기 추가, B/A 절감률(~93%, ~95%) 추가
- **Ethan 피드백 6항목**: 수치 4항목 반영, 상세 내용 슬라이드 추가, 다이어그램 이미지는 세로형이라 생략

### Slack 커뮤니케이션
- `#lk-ai-camp` (C0AG1577CMD)에 장표 초안 공유 메시지 + PDF 첨부 (ts: `1773278949.725489`)
- 피드백 반영 현황 스레드 답글 전송 (ts: `1773296690.361209`)

### CSS 테마 변경
- `ba-table` 클래스: Vivi B/A 슬라이드에도 적용 (이전 세션에서 Ethan만 적용되어 있었음)
- 절감률 별도 열 시도 → `ba-table`의 `th:last-child` 선택자가 절감률 열에 적용되는 문제 → After 열에 절감률 텍스트 통합으로 해결

## 성공/실패 기록

### 성공
- LinkedIn 글을 WebFetch로 읽어서 Keynote 슬라이드 소스로 활용 — 핵심 메시지 추출 잘 됨
- Showcase PR 3개 일괄 머지 + 장표 반영을 한 흐름으로 처리
- Slack MCP (claude_ai_Slack)로 채널 검색 → 메시지 전송 → 스레드 읽기 → 스레드 답글까지 원활

### 실패/회피
- **절감률 별도 열 추가 시도**: `ba-table` CSS가 `th:last-child`/`td:last-child`를 강조하므로, 4열 테이블로 만들면 절감률 열(마지막)이 강조됨. After 열에 텍스트 통합으로 우회
- **Ethan pipeline-flow.png**: 세로형(1824x2338)이라 가로 슬라이드에 부적합 → 생략. Ethan에게 가로형 리디자인 요청하거나 발표 당일 레포에서 직접 보여주는 방식 권장
- **Vivi 콜아웃/다이어그램**: Marp(마크다운 기반)에서는 이미지 위 오버레이나 박스형 다이어그램 불가 → 아이콘 + 텍스트로 대체

## 주요 결정 사항

1. **Sangsu(Eddie)는 앰버서더이지만 장표에 포함** — 제출했으니 넣기로 결정. 단, "7명 비개발자" 빅넘버는 일반 참여자 기준이므로 그대로 유지
2. **"Before / After" 섹션 구분 슬라이드 삭제** — 개별 참여자 B/A에 이미 포함되어 중복이므로 제거
3. **ba-table 클래스는 B/A 테이블에만 적용** — 서비스/역할, 단계/내용 등 비교가 아닌 테이블에는 적용하지 않기로 (강조가 의미 없음)
4. **2부 연사 Keynote → 패널토크 순서** — 외부 연사가 "조직이 AX를 정석적으로 실패하는 방법" 발표 후, 패널토크 진행
5. **피드백 수집은 Slack 스레드** — GitHub PR 리뷰는 내일 발표까지 시간이 촉박하고 비개발자 접근성이 낮음

## 주의사항 & 교훈

- **Marp `ba-table` CSS**: `th:last-child`/`td:last-child` 선택자 사용 → 테이블 열 수가 바뀌면 강조 대상이 달라짐. 열 추가 시 주의
- **Slack MCP 도구 구분**: `slack-ai-native-camp` (korotovsky, AI Native Camp 워크스페이스) vs `claude_ai_Slack` (LiveKlass Corp 워크스페이스) — `#lk-ai-camp`은 LiveKlass Corp 워크스페이스에 있음
- **Marp 빌드 명령**: `marp session5-showcase.md --theme theme.css --pdf --allow-local-files --no-stdin` — `--no-stdin` 없으면 파이프 대기로 hang
- **gh auth**: 레포 `Rich00lee` 소유 — `gh auth switch --user Rich00lee` 필요할 수 있음
- **PR 머지 시 `--admin` 플래그**: branch protection 때문에 필요

## 다음 단계

- **[P0] 아린·Jay 슬라이드 채우기** (쉬움) — 아린은 스레드에서 이미지 첨부 방식 질문, Jay는 오늘 중 과제 업로드 + 별도 장표(PDF) 제출 예정. PR 올라오면 머지 + 장표 반영
- **[P0] Jay 별도 장표 통합** (보통) — Jay가 직접 만든 PDF/슬라이드를 전체 장표에 어떻게 합칠지 결정 필요 (Marp에 삽입 vs 발표 시 전환)
- **[P0] 최종 PDF 빌드 + Slack 공유** (쉬움) — 아린·Jay 반영 후 최종 빌드 → 스레드에 최종본 업로드
- **[P1] 발표 당일 리허설** (보통) — 슬라이드 전환 확인 (특히 2부 연사 슬라이드 → 패널토크 전환 타이밍)
- **[P1] Ethan 다이어그램 이미지** (쉬움) — 가로형 리디자인 요청하거나 발표 시 레포 직접 보여주기로 대체
- **[P2] Vivi 플로우 시각화 개선** (어려움) — 별도 이미지 파일 제작 필요. Marp 마크다운으로는 한계

## 중요 파일 맵

| 파일 | 역할 |
|------|------|
| `docs/slides/session5-showcase.md` | Session 5 Marp 발표 장표 (메인) — 32슬라이드 |
| `docs/slides/theme.css` | 커스텀 Marp 테마 (`lk-camp`) — ba-table 클래스 포함 |
| `docs/slides/session5-showcase.pdf` | 빌드된 PDF (최신) |
| `docs/slides/vivi-ps-demo.png` | Vivi /ps 스킬 iMessage 스크린샷 |
| `docs/slides/ethan-pipeline.png` | Ethan 파이프라인 다이어그램 (세로형, 미사용) |
| `docs/slides/claude-logo.png` | Claude 로고 (타이틀/엔딩 슬라이드) |
