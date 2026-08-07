---
type: funnel-stage
name: Contacting
order: 3
---
#funnel

> **키맨 컨포가 확보되어 컨택해야 하는 단계**


## 병목
콜을 보면서 **제안이 날카롭지 않은지** 점검

## 운영 팁
모든 업체에게 최대한 빠르게 contact 했을 때 성과가 좋았음. 전화 끊을 때 언제 전화할지 물어보고 다음 action을 명확히.

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "Contacting")
SORT next_date ASC
```
