---
type: dashboard
---
#dashboard

# 🎯 SDR 대시보드

> **내 딜**은 `01-accounts/`, **학습용 참고 딜**은 `04-reference/deal-notes/`.
> 아래 쿼리는 전부 **내 딜만** 봅니다.

## 🔥 오늘 / 지연된 액션
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", stage AS "단계", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE type = "account" AND company != null AND next_date != null AND next_date <= date(today)
SORT next_date ASC
```

## 📋 내 딜 전체
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", vertical AS "버티컬", stage AS "단계", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE type = "account" AND company != null
SORT next_date ASC
```

## ⚠️ 챙겨야 할 것
> `next_date`가 비었거나 · 키맨 컨포가 없는 딜
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", stage AS "단계",
  choice(next_date = null, "📅 날짜 없음", "") + choice(keyman_contact = false, " 📞 컨포 없음", "") AS "누락"
FROM "01-accounts"
WHERE type = "account" AND company != null
  AND (next_date = null OR keyman_contact = false)
  AND !contains(string(stage), "Lost")
```

## 📊 퍼널 현황
> *"[[Open]]과 [[Gathering]]의 개수가 적은 것이 잘하는 사람"* — [[퍼널]]
```dataview
TABLE WITHOUT ID stage AS "단계", length(rows) AS "건수"
FROM "01-accounts"
WHERE type = "account" AND company != null
GROUP BY stage
SORT length(rows) DESC
```

---

## 🧭 빠른 이동

**내 딜** · [[01-accounts/README|01-accounts]] · [[퍼널]]
**학습 딜** · [[04-reference/deal-notes/README|deal-notes]]

**프레임워크** · [[설득의_논리_전개]] · [[문제파악_framework]] · [[실전_세일즈_분석_framework]] · [[call_분석_framework]] · [[reference_구조화_framework]] · [[제안서_flow]] · [[셀포]]

**세일즈 방식** · [[Visionary_Sales]] · [[Feature_Sales]] · [[Price_Sales]] · [[페르소나]]

**니즈** · [[인건비절감]] · [[상담효율화]] · [[채널통합]] · [[AI자동화]] · [[VOC데이터분석]] · [[CRM마케팅]] · [[컨버전개선]] · [[리드젠]] · [[라우팅]] · [[리텐션업셀]]

**기능** · [[ALF]] · [[CoS]] · [[팀챗]] · [[미트-IVR]] · [[챗셰어링]] · [[AI-BPO]] · [[워크플로우-태스크]] · [[수신함-채널통합]]

**레퍼런스** · [[버티컬_정의_및_주요_레퍼런스]] · [[내부_딜_사례]] · [[플랫폼_연동_현황]] · [[해피톡]] · [[데이터라이즈]] · [[챗봇나우]]

**기타** · [[glossary|용어집]] · [[미드마켓]] · [[미드마켓_세일즈_파이프라인]] · [[레퍼런스_플래시카드]]
