---
type: core-need
name: AI자동화
category: 실행
---
#core-need

**분류**: 실행

## 고객이 겪는 상황 (Pain)
단순 반복 문의가 전체의 상당 비중(취교반배 기준 약 80%). 업무시간 외 대응 불가.

## 채널톡의 해법
[[ALF]] 규칙·지식·태스크 3단계 세팅. 채널톡 AI는 학습하지 않고 RAG로 참조 → 할루시네이션 방지.

## 활용 레퍼런스
- [[슬로우앤드]]
- [[콜로소]]

## 이 니즈를 가진 딜
```dataview
TABLE vertical AS "버티컬", stage AS "단계", next_action AS "다음 액션"
FROM "01-accounts"
WHERE contains(string(core_needs), "AI자동화")
SORT stage ASC
```
