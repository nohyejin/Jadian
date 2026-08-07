---
type: funnel-stage
name: Open
order: 1
---
#funnel

> **아직까지 touch하지 않은 리드**


## 운영 팁
리드 수령 후 3일 내 1차 콜. **Open 개수가 적은 것이 잘하는 사람의 지표.**

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "Open")
SORT next_date ASC
```
