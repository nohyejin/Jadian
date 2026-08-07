---
type: readme
---
#readme

# 📖 Jadian 볼트 사용설명서

> **채널톡 SDR 세일즈 볼트**
> 콜드콜·미팅에서 얻은 딜 정보를 **회사 단위로 축적**하고, 축적된 정보가 **다음 콜의 무기**가 되도록 설계된 볼트입니다.

| | |
|---|---|
| **소유자** | Jade (jade@channel.io) |
| **직무** | SDR — Inside Sales, 미드마켓 |
| **노트 수** | 143 |
| **백업** | Git 자동 커밋(5분) → [GitHub](https://github.com/nohyejin/Jadian) |
| **첨부 폴더** | `x.img/` |

---

# 1. 핵심 설계 원칙

> ## 🔑 계정(회사)이 1급 객체다

날짜 노트에 딜을 적으면 *"베니토 정보가 몇 번째 노트에 있었더라"* 를 매번 검색해야 합니다.
이 볼트는 반대 방향입니다 — **회사마다 노트가 하나씩 있고, 날짜 기록이 그 아래로 붙습니다.**

```
❌ 날짜 → 회사   (append-only 로그, 조회 불가)
✅ 회사 → 날짜   (조회 가능한 CRM 레이어)
```

### 이걸로 가능해지는 것
| 질문 | 어디서 답이 나오는가 |
|---|---|
| "오늘 팔로업할 딜은?" | [[SDR_대시보드]] 🔥 쿼리 |
| "이 레퍼런스를 어떤 딜에 썼지?" | [[베리시]] 백링크 |
| "해피톡 쓰는 고객사 전부" | [[해피톡]] 백링크 + Dataview |
| "인건비절감 니즈 딜의 공통 논리" | [[인건비절감]] |
| "Contacting 단계에 몇 건?" | [[퍼널]] |

---

# 2. 폴더 구조

```
Jadian/
├── README.md              ← 지금 이 문서
├── SDR_대시보드.md          ← ⭐ 매일 아침 여는 화면
│
├── 00-inbox/              임시 캡처 (콜 중 급하게 적은 것)
├── 01-accounts/     (25)  ★ 회사별 딜 노트 — 볼트의 심장
├── 02-daily/         (7)  데일리 노트 (스크럼·콜 로그)
│
├── 03-playbook/           영구 지식 — "어떻게 파는가"
│   ├── glossary.md        용어집 (AHT, TCO, PQL, RAG…)
│   ├── peter.md           버디 코칭 노트
│   ├── market/       (2)  미드마켓 정의 · 세일즈 파이프라인
│   ├── sales/        (6)  세일즈 방법론 · 셀포
│   │   ├── funnel/   (9)  퍼널 6단계 + Convert/Lost + MOC
│   │   ├── needs/   (10)  Core Needs 택소노미
│   │   └── personas/ (5)  키맨 페르소나별 메시지
│   ├── frameworks/   (6)  설득 논리 · 문제파악 · 제안서 flow…
│   ├── product/      (4)  세일즈덱 · 채널어드민 · 제품 구조
│   │   └── features/ (8)  ALF · CoS · 팀챗 · 미트-IVR…
│   └── cx/           (2)  CS/CX 업무 이해
│
├── 04-reference/          레퍼런스 — "무엇으로 설득하는가"
│   ├── verticals/   (14)  버티컬 정의 + 소구 포인트
│   ├── cases/       (20)  고객사 성공사례 (베리시, 스킨푸드…)
│   ├── deal-cases/   (4)  내부 딜 사례 (라빈, 쥬비스…)
│   ├── competitors/  (7)  경쟁사 + 전환 플레이
│   └── platforms/    (6)  연동 가능성 (카페24, 위드소프트…)
│
├── 90-retro/         (1)  회고
├── pin/              (1)  개인 메모
├── Excalidraw/            그림
└── x.img/                 이미지 첨부
```

### 폴더 번호의 의미
- `00~02` = **흐르는 것** (매일 바뀜)
- `03~04` = **쌓이는 것** (영구 지식)
- `90` = **돌아보는 것**

---

# 3. 명명 규칙

| 대상 | 규칙 | 예시 |
|---|---|---|
| 폴더 | `번호-영문소문자` | `01-accounts`, `03-playbook` |
| 노트 | **공백 대신 언더바 `_`** | `미드마켓_세일즈_파이프라인.md` |
| 계정 노트 | 회사명 그대로 (법인격 포함 시 `_`) | `베니토.md`, `주식회사_크랩.md` |
| 데일리 | `(월.일.)_구분.md` | `(8.7.)_Lead_Market.md` |

> ⚠️ 파일명을 바꿀 때는 **반드시 Obsidian 안에서** 이름 변경하세요. 링크가 자동으로 따라갑니다. Finder에서 바꾸면 링크가 깨집니다.

---

# 4. 노트 유형과 스키마

각 노트는 frontmatter의 `type`으로 구분됩니다.

## 4-1. 계정 노트 (`type: account`) ★ 가장 중요

```yaml
---
type: account
company: 베니토
vertical: "[[커머스-의류패션]]"     # 버티컬 허브로 링크
stage: "[[Nurturing]]"            # 퍼널 단계로 링크
revenue:                          # 연매출
keyman:                           # 키맨 이름/직책
keyman_contact: false             # 컨포 확보 여부
competitor:
  - "[[해피톡]]"
core_needs:
  - "[[인건비절감]]"
  - "[[VOC데이터분석]]"
mrr_est:                          # 예상 MRR
next_action: 신규 브랜드 런칭 일정 확인 콜
next_date: 2026-08-12             # ⚠️ 반드시 채울 것
first_touch: 2026-08-07
source: "[[(8.7.)_Lead_Market]]"
sf_link:                          # 세일즈포스 링크
---
```

**본문 4개 섹션**: `## Core Needs` / `## 전략` / `## Risk` / `## 타임라인`

> 💡 **`next_date`가 이 볼트의 엔진입니다.** 비어 있으면 대시보드가 작동하지 않습니다.

## 4-2. 나머지 유형

| `type` | 위치 | 역할 |
|---|---|---|
| `funnel-stage` | `sales/funnel/` | 퍼널 단계 정의 + 병목 + 해당 딜 목록 |
| `core-need` | `sales/needs/` | 니즈별 Pain → 해법 → 레퍼런스 |
| `persona` | `sales/personas/` | 키맨 직무별 KPI와 메시지 |
| `vertical` | `04-reference/verticals/` | 버티컬 Pain + 소구 포인트 |
| `case` | `04-reference/cases/` | 고객사 성공사례 |
| `competitor` | `04-reference/competitors/` | 약점 + 전환 플레이 |
| `platform` | `04-reference/platforms/` | 연동 가능 여부 |
| `feature` | `product/features/` | 제품 기능 + 세일즈 가치 |
| `framework` | `frameworks/` | 반복 사용하는 절차 |

---

# 5. 링크 규칙 — 무엇을 `[[링크]]`할 것인가

> **기준: "다시 열어볼 노트인가?"**

## ✅ 링크할 것 (1급 객체 5종)
1. **회사** — `[[베니토]]`
2. **버티컬** — `[[커머스-의류패션]]`
3. **레퍼런스 사례** — `[[베리시]]`
4. **경쟁사 / 플랫폼** — `[[해피톡]]`, `[[카페24]]`
5. **제품 기능 / Core Needs / 퍼널 단계** — `[[ALF]]`, `[[인건비절감]]`, `[[LM]]`

## ❌ 링크하지 말 것
일반 개념(효율화, 매출 증대 등), 일회성 고유명사, 형용사.
→ 전부 링크하면 그래프가 털뭉치가 되고 백링크가 의미를 잃습니다.

## 🔧 Unlinked mentions 활용
허브 노트를 **만들기만 하면**, 백링크 패널 하단 **"Unlinked mentions"** 에 링크 없이 언급된 곳이 자동으로 뜹니다. → **Link 버튼 한 번**으로 전환.
기존 노트를 일일이 고칠 필요 없이 링크가 역방향으로 채워집니다.

## 현재 최대 허브
[[ALF]] 38 · [[LM]] 22 · [[상담효율화]] 15 · [[채널통합]] 14 · [[CoS]] 14 · [[인건비절감]] 13 · [[해피톡]] 12

---

# 6. 태그 체계

태그는 **유형 분류 전용**입니다. 주제 연결은 링크가 담당합니다.

`#account` `#vertical` `#case` `#deal-case` `#competitor` `#platform` `#feature` `#core-need` `#funnel` `#persona` `#framework` `#sales-method` `#glossary` `#moc` `#dashboard`

**레거시 태그** (기존 노트): `#edu` `#sales` `#market` `#LeadMarket` `#DailySync` `#회고` `#buddy` `#flashcards`

---

# 7. 일상 워크플로우

## 📅 하루

| 시점 | 액션 |
|---|---|
| **출근** | [[SDR_대시보드]] 열기 → 🔥 오늘/지연된 액션 확인 |
| **오전 스크럼** | 데일리 노트에 기록. 딜 관련 내용은 **해당 계정 노트로** 이동 |
| **콜 블록** | 통화 종료 즉시 계정 노트의 `stage`·`next_action`·`next_date` 갱신 **(30초)** |
| **콜 로그** | 데일리 노트 표에 **회사명을 링크로** 기록 → 계정 백링크에 타임라인 자동 축적 |
| **오후 스크럼** | 리드마켓 리뷰 내용 → 계정 노트 `## 전략` / `## Risk` |
| **퇴근 전** | 💤 방치된 딜 쿼리 확인, `next_date` 없는 딜 정리 |

```markdown
## 콜 로그
| 회사 | 결과 | 다음 액션 |
|---|---|---|
| [[베니토]] | 키맨 통화 성공 | 런칭 일정 확인 |
| [[플록]] | 부재 | 8/12 재콜 |
```

## 📆 주간 (금요일 5분)

| 확인 | 방법 | 의미 |
|---|---|---|
| 고립된 딜 | 그래프 Show orphans **on** + `path:"01-accounts"` | 버티컬·레퍼런스 연결 없는 딜 = 전략 없는 딜 |
| 안 쓰는 레퍼런스 | `04-reference/cases/` 백링크 0개 | 안 꺼내 쓴 무기 |
| 과밀 경쟁사 | [[해피톡]] 백링크 급증 | 전환 플레이북 별도 제작 시점 |
| 퍼널 균형 | [[퍼널]] | [[Open]]·[[Gathering]]이 많으면 정체 신호 |

`90-retro/`에 주간 회고 + 퍼널 스냅샷 기록.

---

# 8. 새 딜 추가하기 (Step by Step)

1. `01-accounts/` 우클릭 → New note → **회사명** (공백은 `_`)
2. `01-accounts/schema.md` 내용 복사 → 붙여넣기
3. frontmatter 채우기 — **최소 5개**:
   - `vertical` → `04-reference/verticals/` 중 하나로 링크
   - `stage` → `[[Open]]` 부터 시작
   - `core_needs` → `sales/needs/` 중 하나 이상
   - `next_action` + **`next_date`** ← 기본값은 **3일 뒤** (peter 룰)
4. 본문 4개 섹션 채우기. 인용할 레퍼런스·기능·경쟁사는 **링크로**
5. 그날 데일리 노트 콜 로그에 `[[회사명]]` 추가

> **Core Needs는 많을수록 좋지 않습니다.** 2~3개보다 **키맨의 고통이 큰 하나를 깊게.**

---

# 9. 플러그인 사용 현황

## 활성 사용
| 플러그인 | 용도 |
|---|---|
| **Dataview** | [[SDR_대시보드]] 및 모든 허브 노트의 자동 집계 |
| **Obsidian Git** | 5분마다 자동 커밋 → GitHub 백업 |
| **Full Calendar** | Google Calendar(jade@channel.io) 연동 |
| **Calendar** | 데일리 노트 네비게이션 |
| **Spaced Repetition** | 제품지식·레퍼런스 암기 ([[레퍼런스_플래시카드]]) |
| **Excalidraw** | 조직도·퍼널 다이어그램 |

## 설정 필요
- **코어 Daily Notes** → 폴더 `02-daily`, 형식 `YYYY-MM-DD`
- **Templater** → 템플릿 폴더 지정 + `01-accounts` 폴더 템플릿
- **Git** → Auto push interval **10분** (현재 0 = 자동 push 안 함)

## 미사용 (정리 후보)
`style-settings` · `table-editor` · `emoji-toolbar` · `icon-folder` · `tasks` · `kanban`

---

# 10. 그래프뷰 & 백링크

## 색상 그룹
🔵 딜(`01-accounts`) 🟡 레퍼런스(`04-reference`) 🟢 플레이북(`03-playbook`)
🟣 퍼널 🩵 니즈 🟠 기능 ⚪ 로그(`02-daily`)

**읽는 법**: 노란 레퍼런스 허브에 파란 딜 노드가 안 붙어 있으면 → **안 써먹고 있는 레퍼런스**.

## 로컬 그래프 = 딜 브리핑 ⭐
계정 노트에서 `Cmd+P` → **Open local graph** → 사이드바 고정, **Depth 2**.
콜 직전 5초 훑기로 *"비슷한 딜이 뭐였고 그때 뭘 썼는지"* 파악.

## 백링크 설정
설정 → Backlinks → **"Backlinks in document" 켜기**
→ 계정 노트 하단에 그 회사가 언급된 데일리 노트가 자동으로 붙습니다.

> ⚠️ **전체 그래프뷰는 주 1회면 충분합니다.** 실질 가치의 90%는 **백링크 패널 + 로컬 그래프**에 있습니다.

---

# 11. 해야 할 것 / 하지 말아야 할 것

## ✅ DO
- 콜 끝나면 **30초 안에** 계정 노트 갱신
- 데일리 콜 로그에 **회사명은 반드시 링크로**
- `next_date`를 **항상** 채우기
- Lost 딜은 **사유 + 재접점 조건**을 함께 기록
- 레퍼런스를 인용할 때 `[[베리시]]` 링크로 — 재사용 이력이 쌓입니다

## ❌ DON'T
- 딜 정보를 데일리 노트에만 적기 (→ 검색 지옥)
- 모든 단어를 링크하기 (→ 그래프 털뭉치)
- Finder에서 파일명 변경 (→ 링크 깨짐)
- Core Needs를 4~5개씩 나열 (→ AE가 거절)
- 그래프뷰를 하루 5분 이상 보기 (→ 그건 취미)

---

# 12. 백업 & 복구

- **자동 커밋**: 5분마다 `vault backup: {{date}}`
- **원격**: `https://github.com/nohyejin/Jadian`
- **복구**: `git log --oneline` → `git checkout <해시> -- <파일경로>`
- 실수로 지운 노트는 설정 → File Recovery에서도 복구 가능

---

# 13. 시작 지점

| 목적 | 열 노트 |
|---|---|
| **매일 아침** | [[SDR_대시보드]] |
| 퍼널 전체 보기 | [[퍼널]] |
| 미드마켓이 뭔지 | [[미드마켓]] · [[미드마켓_세일즈_파이프라인]] |
| 어떻게 파는지 | [[세일즈커뮤니케이션의_이해]] · [[설득의_논리_전개]] |
| 무엇으로 설득하는지 | [[버티컬_정의_및_주요_레퍼런스]] |
| 용어 모를 때 | [[glossary]] |
| 암기 | [[레퍼런스_플래시카드]] → `Cmd+P` → Review flashcards |

---

## 부록: 전체 딜 목록
```dataview
TABLE WITHOUT ID link(file.link, company) AS "기업", vertical AS "버티컬", stage AS "단계", next_action AS "다음 액션"
FROM "01-accounts"
WHERE type = "account"
SORT stage ASC, company ASC
```
