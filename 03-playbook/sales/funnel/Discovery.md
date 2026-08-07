---
type: funnel-stage
name: Discovery
order: 5
---
#funnel

> **미팅 수락을 받았고 추가적인 정보를 원하는 단계**


## 병목
정보 수집의 깊이 — discovery가 중구난방이면 세일즈 단에서 reject 당함

## 운영 팁
[[실전_세일즈_분석_framework]]에 따라 질의응답으로 depth를 깊게 파고든 뒤 현황 분석과 진단. **Core Needs는 많으면 좋지 않다** — 키맨의 고통이 큰 하나를 깊게.

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "Discovery")
SORT next_date ASC
```
