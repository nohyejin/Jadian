---
type: funnel-stage
name: Convert
order: 7
---
#funnel

> **정식 영업 기회로 전환되어 AE에게 핸드오프된 상태**


## 운영 팁
이후 첫 세일즈 미팅 → 팔로업 → 온보딩 → 견적서 교환 → 클로징은 AE가 리드.

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "Convert")
SORT next_date ASC
```
