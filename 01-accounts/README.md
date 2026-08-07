---
type: moc
---
#moc

# 01-accounts — 내 딜

> 여기에는 **내가 직접 진행하는 딜만** 넣습니다.
> 리드마켓에서 듣거나 학습한 다른 분들의 딜은 [[04-reference/deal-notes/README|deal-notes]]에 있습니다.

새 딜: `_템플릿.md` 복사 → 파일명을 회사명으로.

```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", stage AS "단계", next_action AS "다음 액션", next_date AS "예정일"
FROM "01-accounts"
WHERE type = "account" AND company != null
SORT next_date ASC
```
