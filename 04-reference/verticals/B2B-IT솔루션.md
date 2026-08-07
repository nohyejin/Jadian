---
type: vertical
name: B2B-IT솔루션
tier: 코어
---
#vertical

> **코어 버티컬**

## 공통 Pain
기술 복잡성 → 긴 세일즈 사이클, 업무시간 외 상담 다수, 기능별 담당자 배정 필요

## 소구 포인트
기능별 담당자 자동 배정 + 내부 대화로 제품팀·엔지니어 협업. 고연매출 신규보다 기존 고객 업셀 집중

## 레퍼런스
- [[아임웹]]
- [[투바]]

## 이 버티컬의 딜
```dataview
TABLE stage AS "단계", keyman AS "키맨", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE contains(string(vertical), "B2B-IT솔루션")
SORT stage ASC
```
