---
type: funnel-stage
name: Lost
order: 0
---
#funnel

> **실패 처리된 딜**


## 운영 팁
Lost 사유를 반드시 기록할 것. 재접점 조건(무엇이 바뀌면 다시 볼 수 있는가)을 함께 남긴다.

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "Lost")
SORT next_date ASC
```
