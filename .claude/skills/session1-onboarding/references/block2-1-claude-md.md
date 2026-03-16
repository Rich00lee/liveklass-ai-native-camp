> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/memory

## EXPLAIN

### CLAUDE.md — Claude의 장기 기억

CLAUDE.md는 Claude Code가 프로젝트를 열 때마다 **자동으로 읽는 지시서**다.

매번 "나는 라이브클래스 세일즈팀이야"라고 설명하지 않아도 됨.
→ CLAUDE.md에 한 번 써두면 영구히 적용된다.

**LiveKlass 세일즈팀 예시**:
```markdown
# CLAUDE.md

## 나는 누구
- 라이브클래스 세일즈팀 (B2B 에듀테크)
- 주요 업무: 리드 발굴 → 미팅 → 제안 → 계약 → 온보딩

## 우리 팀 도구
- CRM: 구글시트
- 협업: Slack, Notion
- 고객 관리: 이메일 + Slack

## 응답 스타일
- 항상 한국어로 응답
- 실무 바로 적용 가능한 형태로 작성
- 숫자/데이터 기반으로 설명
```

이렇게 만들어두면 Claude는 항상 이 컨텍스트를 알고 대화한다.

## EXECUTE

지금 바로 나만의 CLAUDE.md를 만들어보세요:

```bash
# Claude Code에 이렇게 입력하세요:
CLAUDE.md 파일 만들어줘.
나는 라이브클래스 [직군]이고, 주요 업무는 [업무 내용]이야.
자주 쓰는 도구는 Slack, Notion, 구글시트야.
```

만들어진 파일을 확인하고 내용이 맞는지 수정해보세요.

## QUIZ

AskUserQuestion으로 퀴즈 출제:

질문: "CLAUDE.md가 없으면 어떤 불편함이 생길까요?"
- "매번 설명을 반복해야 한다" → ✅ 정답! "CLAUDE.md는 Claude의 장기 기억이에요. 한 번만 세팅하면 영구적으로 적용됩니다."
- "Claude가 오류가 난다" → "오류는 아니지만, 매 대화마다 컨텍스트를 다시 설명해야 해서 비효율적이에요."
- "잘 모르겠다" → 예시로 설명: "오늘 처음 만나는 사람에게 매번 자기소개를 해야 한다고 생각해보세요."
