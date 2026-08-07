---
type: core-need
name: CRM마케팅
category: 매출 기여
---
#core-need

**분류**: 매출 기여

## 고객이 겪는 상황 (Pain)
상담 데이터와 주문 정보가 연동되지 않음. 재구매 유도·개인화 메시지 부재.

## 채널톡의 해법
수집된 고객정보 기반 선제적 마케팅. 알림톡·문자·카카오톡 액션 발송. 구매주기별 자동 메시지.

## 활용 레퍼런스
- [[어뮤즈]]
- [[펫프렌즈]]

## 이 니즈를 가진 딜
```dataview
TABLE vertical AS "버티컬", stage AS "단계", next_action AS "다음 액션"
FROM "01-accounts"
WHERE contains(string(core_needs), "CRM마케팅")
SORT stage ASC
```
