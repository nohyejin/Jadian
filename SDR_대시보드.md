---
type: dashboard
---
#dashboard

# 🎯 SDR 대시보드

## 🔥 오늘/지연된 액션
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", stage AS "단계", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE next_date != null AND next_date <= date(today)
  AND !contains(string(stage), "Lost") AND !contains(string(stage), "Convert")
SORT next_date ASC
```

## ⚠️ next_date 미설정 딜 — 먼저 채우기
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", stage AS "단계", next_action AS "다음 액션"
FROM "01-accounts"
WHERE next_date = null AND !contains(string(stage), "Lost")
SORT stage ASC
```

## 📞 키맨 컨포 미확보
> *"번호가 없는 것을 최대한 월말까지 줄이는 것"*
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", vertical AS "버티컬", stage AS "단계", first_touch AS "첫터치"
FROM "01-accounts"
WHERE keyman_contact = false AND !contains(string(stage), "Lost")
SORT first_touch ASC
```

## 📊 퍼널 현황
> *"[[Open]]과 [[Gathering]]의 개수가 적은 것이 잘하는 사람"*
```dataview
TABLE WITHOUT ID stage AS "단계", length(rows) AS "건수"
FROM "01-accounts"
GROUP BY stage
SORT length(rows) DESC
```

## 🏷 버티컬 분포
```dataview
TABLE WITHOUT ID vertical AS "버티컬", length(rows) AS "건수"
FROM "01-accounts"
GROUP BY vertical
SORT length(rows) DESC
```

## 🎯 Core Needs 분포
```dataview
TABLE WITHOUT ID core_needs AS "니즈", length(rows) AS "건수"
FROM "01-accounts"
FLATTEN core_needs
GROUP BY core_needs
SORT length(rows) DESC
```

## ⚔️ 경쟁사 리플레이스 기회
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", competitor AS "경쟁사", stage AS "단계"
FROM "01-accounts"
WHERE competitor != null AND length(competitor) > 0
SORT stage ASC
```

## 💤 방치된 딜 (7일 이상 무터치)
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", stage AS "단계", next_action AS "다음 액션"
FROM "01-accounts"
WHERE file.mtime < date(today) - dur(7 days)
  AND !contains(string(stage), "Lost") AND !contains(string(stage), "Convert")
SORT file.mtime ASC
```

## ❌ Lost 딜 — 재접점 조건 확인
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", vertical AS "버티컬", next_action AS "재접점 조건"
FROM "01-accounts"
WHERE contains(string(stage), "Lost")
```

---

## 🧭 빠른 이동

**퍼널** · [[퍼널]] · [[Open]] · [[Gathering]] · [[Contacting]] · [[Nurturing]] · [[Discovery]] · [[LM]] · [[Convert]] · [[Lost]]

**프레임워크** · [[설득의_논리_전개]] · [[문제파악_framework]] · [[실전_세일즈_분석_framework]] · [[call_분석_framework]] · [[reference_구조화_framework]] · [[제안서_flow]] · [[셀포]]

**세일즈 방식** · [[Visionary_Sales]] · [[Feature_Sales]] · [[Price_Sales]]

**페르소나** · [[CX팀장]] · [[CX팀원]] · [[IT개발자]] · [[마케터]] · [[대표경영진]]

**니즈** · [[인건비절감]] · [[상담효율화]] · [[채널통합]] · [[AI자동화]] · [[VOC데이터분석]] · [[CRM마케팅]] · [[컨버전개선]] · [[리드젠]] · [[라우팅]] · [[리텐션업셀]]

**기능** · [[ALF]] · [[CoS]] · [[팀챗]] · [[미트-IVR]] · [[챗셰어링]] · [[AI-BPO]] · [[워크플로우-태스크]] · [[수신함-채널통합]]

**경쟁사** · [[해피톡]] · [[데이터라이즈]] · [[챗봇나우]] · [[크리마]]

**기타** · [[glossary|용어집]] · [[미드마켓]] · [[미드마켓_세일즈_파이프라인]]
