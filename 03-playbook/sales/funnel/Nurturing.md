---
type: funnel-stage
name: Nurturing
order: 4
---
#funnel

> **키맨에게 긍정적인 반응을 얻은 상태**


## 병목
key-man을 통한 지식 공유 필요

## 운영 팁
부정적인 반응은 메일로 전송하고 tracking해서 월말에 재연락. 부정적인 곳에서 키맨을 뚫기보다 새로운 리드를 찾는 편이 낫다. 초반에는 negative한 것과 nurturing을 본인 기준에 맞게 조율.

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "Nurturing")
SORT next_date ASC
```
