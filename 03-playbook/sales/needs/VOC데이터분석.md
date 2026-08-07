---
type: core-need
name: VOC데이터분석
category: 데이터 자산화
---
#core-need

**분류**: 데이터 자산화

## 고객이 겪는 상황 (Pain)
상담 데이터가 쌓이지만 인사이트로 전환되지 않음. 태그·분류 체계 부재.

## 채널톡의 해법
[[CoS]]로 이탈 신호 포착, 불만 패턴 식별, 매출 직결 인사이트 도출, 선제적 고객 관리.

## 활용 레퍼런스
- [[베리시]]
- [[시스디자인]]

## 관련 딜 (학습 노트 + 내 딜)
```dataview
TABLE vertical AS "버티컬", stage AS "단계", next_action AS "다음 액션"
FROM "04-reference/deal-notes" OR "01-accounts"
WHERE contains(string(core_needs), "VOC데이터분석")
SORT stage ASC
```
