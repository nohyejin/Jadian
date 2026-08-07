---
type: vertical
name: 커머스-FnB
tier: 이머징
---
#vertical

> **이머징 버티컬**

## 공통 Pain
주문·배송 문의 외 제품 신선도·청구 컴플레인, 정기구매 관리

## 소구 포인트
정기 구매 상품 관리 메시지 자동화로 재구매 유도. 침투율 낮으나 고성장 → 전략적 대응 필요

## 레퍼런스
- [[이랜드이츠]]

## 관련 딜 (학습 노트 + 내 딜)
```dataview
TABLE stage AS "단계", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "04-reference/deal-notes" OR "01-accounts"
WHERE contains(string(vertical), "커머스-FnB")
SORT stage ASC
```
