---
type: funnel-stage
name: Gathering
order: 2
---
#funnel

> **키맨의 컨포(연락처)가 없어서 확보해야 하는 단계**


## 병목
컨택 — 키맨 연락처 확보 자체가 병목

## 운영 팁
cut: 2-3으로 넣고, 반응 ok면 2-2. **번호가 없는 것을 최대한 월말까지 줄이는 것**이 목표.

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "Gathering")
SORT next_date ASC
```
