---
type: moc
---
#moc

# 📚 deal-notes — 리드마켓 학습 노트

> 여기 있는 딜은 **내가 진행한 딜이 아닙니다.**
> 리드마켓 리뷰·데일리 스크럼에서 들은 선임들의 딜을 **참고자료·레퍼런스**로 정리한 것입니다.
>
> 내가 직접 맡은 딜은 [[01-accounts/README|01-accounts]]에 기록합니다.

## 이걸 어디에 쓰는가
- 비슷한 버티컬 딜을 맡았을 때 **어떤 논리로 접근했는지** 참고
- 경쟁사·플랫폼별 **Lost 사유 패턴** 학습
- Core Needs 유형별 **소구 방식** 학습

---

## 버티컬별
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", core_needs AS "Core Needs", competitor AS "경쟁사"
FROM "04-reference/deal-notes"
WHERE type = "deal-note"
GROUP BY vertical
```

## 경쟁사가 있는 딜 (전환 케이스)
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", vertical AS "버티컬", competitor AS "경쟁사"
FROM "04-reference/deal-notes"
WHERE competitor != null AND length(competitor) > 0
```

## 전체
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", vertical AS "버티컬", reviewed AS "리뷰일", source AS "출처"
FROM "04-reference/deal-notes"
WHERE type = "deal-note"
SORT reviewed DESC, company ASC
```
