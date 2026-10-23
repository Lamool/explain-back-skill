# explain-back

방금 한 작업에서 배운 것을 되짚어 주는 Claude Code 스킬이에요.
작업을 "끝냈다"에서 "이해했다"로 넘어가도록, 핵심 개념을 정리하고 퀴즈로 확인한 뒤 학습 노트에 기록해요.

## 하는 일

1. **핵심 개념 3개 정리**: 이번 작업에서 실제로 쓰인 개념을 골라 한 줄 정의, 쓰인 위치(`파일:줄`), 왜 중요한지를 알려 줘요.
2. **대화형 퀴즈 3문제**: 쉬움 → 중간 → 응용 순서로 문제를 내고 답을 기다려요.
3. **힌트**: "패스"라고 하면 정답 대신 힌트를 하나 주고 한 번 더 기회를 줘요.
4. **채점과 피드백**: 정답 / 부분 정답 / 다시 보기로 채점하고 모범 답안을 보여 줘요.
5. **LEARNING.md 기록**: 프로젝트 루트의 `LEARNING.md` 에 날짜, 핵심 개념, 문제와 정답, 복습할 것을 쌓아요. 다음에 실행하면 지난번에 틀린 개념을 다시 물어봐요.

코드뿐 아니라 문서 작성, 설정 변경 같은 작업에도 쓸 수 있어요.

## 설치

Claude Code 에서 아래 두 줄을 입력하세요.

```
/plugin marketplace add Lamool/explain-back-skill
/plugin install explain-back@explain-back-skill
```

설치 후 Claude Code 를 다시 시작하면 적용돼요.

## 사용법

```
/explain-back:explain-back                   # 이번 대화에서 한 작업 전체
/explain-back:explain-back src/app.py        # 특정 파일이나 주제
```

"오늘 배운 거 정리해줘", "퀴즈 내줘", "복습하자" 처럼 말해도 실행돼요.
요청할 때만 실행되고, 작업이 끝났다고 해서 알아서 끼어들지는 않아요.

## LEARNING.md 예시

```markdown
## 2026-10-23 · v01_1_var_type.py

**핵심 개념**
- **리스트 vs 튜플**: 리스트는 수정 O, 튜플은 수정 X
- **set**: 중복 제거, 순서 없음 (`[0]` 불가)
- **`isinstance()`**: 실행 중에 진짜 타입 검사

**퀴즈**
| 문제 | 정답 | 결과 |
|------|------|:----:|
| `coords[0] = 99` 는 왜 오류가 날까? | 튜플은 수정 불가 → TypeError | O |
| `nums = {3, 1, 2, 2}` 에서 `nums[0]` 이 안 되는 이유는? | set 은 순서가 없어 인덱스로 못 꺼냄 | O |
| `isinstance()` 로 문자열 입력을 막으려면? | `if not isinstance(x, (int, float)): raise TypeError(...)` | △ |

**복습**
- 확인만 하지 말고 `raise` 로 오류를 일으켜야 실제로 막힘
```

## 업데이트와 제거

```
/plugin marketplace update explain-back-skill    # 최신 버전 받기
/plugin uninstall explain-back@explain-back-skill
```

## 라이선스

MIT
