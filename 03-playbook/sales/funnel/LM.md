---
type: funnel-stage
name: LM
order: 6
---
#funnel

> **Lead Market — 디스커버리까지 완료되어 팀 차원의 기회 검증·평가를 받는 단계**


## 병목
AE에게 매력적으로 보이는가

## 운영 팁
어떻게 하면 딜이 예뻐 보이고 AE에게 잘 팔릴 수 있을지가 핵심. [[셀포]] 작성 품질 = 세일즈포스를 읽었을 때 어떻게 미팅을 해야 할지 틀이 보이는 것.

## 이 단계의 딜
```dataview
TABLE vertical AS "버티컬", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(stage), "LM")
SORT next_date ASC
```
