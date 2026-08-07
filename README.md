---
type: readme
---
#readme

# 📖 Jadian 볼트 사용설명서

> **채널톡 SDR 세일즈 볼트**
> 학습한 것은 **레퍼런스로 쌓고**, 내가 맡은 딜은 **회사 단위로 추적**하는 볼트입니다.

| | |
|---|---|
| **소유자** | Jade (jade@channel.io) |
| **직무** | SDR — Inside Sales, 미드마켓 |
| **노트 수** | 132 |
| **백업** | Git 자동 커밋(5분) → [GitHub](https://github.com/nohyejin/Jadian) |
| **첨부 폴더** | `x.img/` |

---

# 1. 가장 중요한 구분 ⚠️

> ## 내 딜 vs 학습 자료

이 볼트에는 딜이 두 종류 있고, **절대 섞으면 안 됩니다.**

| | `01-accounts/` | `04-reference/deal-notes/` |
|---|---|---|
| **무엇** | 내가 직접 맡아 진행하는 딜 | 리드마켓 리뷰에서 들은 선임들의 딜 |
| **현재** | 0건 (앞으로 채움) | 25건 |
| **`type`** | `account` | `deal-note` |
| **액션 필드** | `next_action`·`next_date` **필수** | 없음 (내 액션이 아니므로) |
| **용도** | 팔로업 추적 | 참고·레퍼런스·학습 |
| **대시보드** | ✅ 집계됨 | ❌ 집계 안 됨 |

**왜 나누는가**: 내 액션이 아닌 딜에 `next_date`를 달면 대시보드가 남의 일로 가득 차서 무용지물이 됩니다. 학습 자료는 *"비슷한 딜 맡았을 때 꺼내 보는 것"* 이지 *"오늘 처리할 것"* 이 아닙니다.

---

# 2. 폴더 구조

```
Jadian/
├── README.md              ← 지금 이 문서
├── SDR_대시보드.md          ← ⭐ 매일 아침 여는 화면
│
├── 00-inbox/         (0)  임시 캡처 (콜 중 급하게 적은 것)
├── 01-accounts/      (2)  ★ 내 딜 — 지금은 템플릿만
│   ├── README.md          내 딜 목록 (Dataview)
│   └── _템플릿.md          새 딜 만들 때 복사
├── 02-daily/         (7)  데일리 노트 (스크럼·콜 로그)
│
├── 03-playbook/           영구 지식 — "어떻게 파는가"
│   ├── glossary.md        용어집 (AHT, TCO, PQL, RAG…)
│   ├── peter.md           버디 코칭 노트
│   ├── market/       (2)  미드마켓 정의 · 세일즈 파이프라인
│   ├── sales/        (7)  세일즈 방법론 · 페르소나 · 셀포
│   │   ├── funnel/   (9)  퍼널 6단계 + Convert/Lost + MOC
│   │   └── needs/   (10)  Core Needs 택소노미
│   ├── frameworks/   (6)  설득 논리 · 문제파악 · 제안서 flow…
│   ├── product/      (4)  세일즈덱 · 채널어드민 · 제품 구조
│   │   └── features/ (8)  ALF · CoS · 팀챗 · 미트-IVR…
│   └── cx/           (2)  CS/CX 업무 이해
│
├── 04-reference/          레퍼런스 — "무엇으로 설득하는가"
│   ├── deal-notes/  (26)  📚 리드마켓 학습 딜 25건
│   ├── verticals/   (14)  버티컬 정의 + 소구 포인트
│   ├── cases/       (20)  고객사 성공사례 (베리시, 스킨푸드…)
│   ├── competitors/  (5)  경쟁사 + 전환 플레이
│   ├── 플랫폼_연동_현황.md   카페24·위드소프트… 연동 가능 여부
│   ├── 내부_딜_사례.md      라빈·쥬비스·주노·김영편
│   └── 레퍼런스_플래시카드.md
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
| 딜 노트 | 회사명 그대로 (법인격 포함 시 `_`) | `베니토.md`, `주식회사_크랩.md` |
| 데일리 | `(월.일.)_구분.md` | `(8.7.)_Lead_Market.md` |

> ⚠️ 파일명 변경은 **반드시 Obsidian 안에서**. Finder에서 바꾸면 링크가 깨집니다.

---

# 4. 노트 유형과 스키마

## 4-1. 내 딜 (`type: account`) ★

```yaml
---
type: account
company: 회사명
vertical: "[[커머스-의류패션]]"     # 버티컬 허브로 링크
stage: "[[Open]]"                 # 퍼널 단계로 링크
keyman:                           # 키맨 이름/직책
keyman_contact: false             # 컨포 확보 여부
competitor: ["[[해피톡]]"]
core_needs: ["[[인건비절감]]"]
next_action: 키맨 컨포 확보 콜
next_date: 2026-08-11             # ⚠️ 반드시 채울 것 (기본 = 3일 뒤)
first_touch: 2026-08-08
sf_link:                          # 세일즈포스 링크
---
```
**본문**: `## Core Needs` / `## 전략` / `## Risk` / `## 타임라인`

> 💡 **`next_date`가 대시보드의 엔진입니다.** 비어 있으면 "오늘 액션"에 안 뜹니다.

## 4-2. 학습 딜 (`type: deal-note`) 📚

```yaml
---
type: deal-note
company: 베니토
vertical: "[[커머스-의류패션]]"
competitor: ["[[해피톡]]"]
core_needs: ["[[인건비절감]]"]
owner: 선임 (리드마켓 리뷰 청취)
reviewed: 2026-08-07
source: "[[(8.7.)_Lead_Market]]"
---
```
**본문**: `## Core Needs` / `## 전략` / `## Risk` — 액션 필드 없음.

## 4-3. 나머지 유형

| `type` | 위치 | 역할 |
|---|---|---|
| `funnel-stage` | `sales/funnel/` | 퍼널 단계 정의 + 병목 |
| `core-need` | `sales/needs/` | 니즈별 Pain → 해법 → 레퍼런스 |
| `persona` | `sales/페르소나.md` | 키맨 직무별 KPI와 메시지 |
| `vertical` | `04-reference/verticals/` | 버티컬 Pain + 소구 포인트 |
| `case` | `04-reference/cases/` | 고객사 성공사례 |
| `competitor` | `04-reference/competitors/` | 약점 + 전환 플레이 |
| `platform` | `04-reference/플랫폼_연동_현황.md` | 연동 가능 여부 |
| `feature` | `product/features/` | 제품 기능 + 세일즈 가치 |
| `framework` | `frameworks/` | 반복 사용하는 절차 |
| `moc` | 각 폴더 `README.md` | 폴더 안내 + 목록 |

---

# 5. 태그 체계

태그는 **유형 분류 전용**입니다. 주제 연결은 링크가 담당합니다.

| 태그 | 대상 | 개수 |
|---|---|---|
| `#account` | 내 딜 | 1 (템플릿) |
| `#deal-note` | 학습 딜 | 25 |
| `#case` | 고객사 성공사례 | 20 |
| `#vertical` | 버티컬 | 14 |
| `#core-need` | Core Needs | 10 |
| `#funnel` | 퍼널 단계 | 8 |
| `#feature` | 제품 기능 | 8 |
| `#framework` | 프레임워크 | 8 |
| `#daily` | 데일리 로그 | 7 |
| `#competitor` | 경쟁사 | 5 |
| `#sales-method` | 세일즈 방법론 | 3 |
| `#moc` `#readme` `#dashboard` `#glossary` `#persona` `#platform` `#deal-case` `#retro` `#cx` `#market` `#product` `#flashcards` | 단일 문서 | 각 1~2 |

> 정리 완료: `#edu` `#reference` `#tool` `#sales` `#LeadMarket` `#DailySync` `#회고` `#buddy` `#cs/cx` 는 위 체계로 통합되었습니다.

---

# 6. 링크 규칙 — 무엇을 `[[링크]]`할 것인가

> **기준: "다시 열어볼 노트인가?"**

## ✅ 링크할 것
1. **회사** — `[[베니토]]`
2. **버티컬** — `[[커머스-의류패션]]`
3. **레퍼런스 사례** — `[[베리시]]`
4. **경쟁사 / 플랫폼** — `[[해피톡]]`, `[[카페24]]`
5. **제품 기능 / Core Needs / 퍼널 단계** — `[[ALF]]`, `[[인건비절감]]`, `[[LM]]`

## ❌ 링크하지 말 것
일반 개념(효율화, 매출 증대), 일회성 고유명사, 형용사.
→ 전부 링크하면 그래프가 털뭉치가 되고 백링크가 의미를 잃습니다.

## 🔧 Unlinked mentions
허브 노트를 **만들기만 하면** 백링크 패널 하단에 링크 없이 언급된 곳이 뜹니다 → **Link 버튼 한 번**으로 전환.

## 별칭(alias) 주의
통합된 문서들은 `aliases`로 기존 링크를 유지합니다. `[[카페24]]` → [[플랫폼_연동_현황]], `[[CX팀장]]` → [[페르소나]], `[[라빈]]` → [[내부_딜_사례]], `[[유베이스]]` → [[BPO사]] 로 연결됩니다.

## 현재 최대 허브
[[ALF]] · [[상담효율화]] · [[채널통합]] · [[CoS]] · [[인건비절감]] · [[해피톡]]

---

# 7. 일상 워크플로우

## 📅 하루

| 시점 | 액션 |
|---|---|
| **출근** | [[SDR_대시보드]] → 🔥 오늘/지연된 액션 |
| **오전 스크럼** | 데일리 노트에 기록 |
| **콜 블록** | 통화 종료 즉시 **내 딜** 노트의 `stage`·`next_action`·`next_date` 갱신 (30초) |
| **콜 로그** | 데일리 노트 표에 **회사명을 링크로** → 백링크에 타임라인 자동 축적 |
| **리드마켓 리뷰** | 남의 딜에서 배운 건 `04-reference/deal-notes/`에 추가 |
| **퇴근 전** | ⚠️ 챙겨야 할 것 쿼리 확인 |

```markdown
## 콜 로그
| 회사 | 결과 | 다음 액션 |
|---|---|---|
| [[베니토]] | 키맨 통화 성공 | 런칭 일정 확인 |
```

## 📆 주간 (금요일 5분)

| 확인 | 방법 |
|---|---|
| 퍼널 균형 | [[퍼널]] — [[Open]]·[[Gathering]]이 많으면 정체 신호 |
| 안 쓰는 레퍼런스 | `04-reference/cases/` 백링크 0개 = 안 꺼내 쓴 무기 |
| 고립된 딜 | 그래프 Show orphans **on** + `path:"01-accounts"` |

`90-retro/`에 주간 회고 기록.

---

# 8. 새 딜 추가하기

## 내 딜일 때
1. `01-accounts/_템플릿.md` 복사 → 파일명을 **회사명**으로 (공백은 `_`)
2. frontmatter **최소 5개**: `company` · `vertical` · `stage` · `next_action` · **`next_date`**(기본 3일 뒤)
3. 본문 4개 섹션. 인용할 레퍼런스·기능·경쟁사는 **링크로**
4. 그날 데일리 콜 로그에 `[[회사명]]` 추가

> **Core Needs는 많을수록 좋지 않습니다.** 2~3개보다 **키맨의 고통이 큰 하나를 깊게.**

## 학습용(남의 딜)일 때
`04-reference/deal-notes/`에 `type: deal-note`로. **`next_date` 달지 말 것.**

---

# 9. 플러그인

## 활성 사용
| 플러그인 | 용도 |
|---|---|
| **Dataview** | 대시보드·허브 노트 자동 집계 |
| **Obsidian Git** | 5분마다 자동 커밋 → GitHub |
| **Full Calendar** | Google Calendar 연동 |
| **Calendar** | 데일리 노트 네비게이션 |
| **Spaced Repetition** | [[레퍼런스_플래시카드]] |
| **Excalidraw** | 다이어그램 |

## 설정 필요
- **코어 Daily Notes** → 폴더 `02-daily`, 형식 `YYYY-MM-DD`
- **Templater** → 템플릿 폴더 지정 + `01-accounts` 폴더 템플릿
- **Git** → Auto push interval **10분** (현재 0 = 자동 push 안 함)

## 미사용 (정리 후보)
`style-settings` · `table-editor` · `emoji-toolbar` · `icon-folder` · `tasks` · `kanban`

---

# 10. 그래프뷰 & 백링크

🔵 내 딜 🟡 레퍼런스 🟢 플레이북 🟣 퍼널 🩵 니즈 🟠 기능 ⚪ 로그

- **로컬 그래프 = 딜 브리핑** — 딜 노트에서 `Cmd+P` → Open local graph → Depth 2, 사이드바 고정
- **백링크 상시 노출** — 설정 → Backlinks → "Backlinks in document" 켜기
- ⚠️ **전체 그래프뷰는 주 1회면 충분.** 실질 가치의 90%는 백링크 패널 + 로컬 그래프에 있습니다.

---

# 11. DO / DON'T

## ✅ DO
- 콜 끝나면 **30초 안에** 딜 노트 갱신
- 데일리 콜 로그에 **회사명은 반드시 링크로**
- 내 딜은 `next_date`를 **항상** 채우기
- Lost 딜은 **사유 + 재접점 조건** 함께 기록
- 레퍼런스 인용 시 `[[베리시]]` 링크로 → 재사용 이력이 쌓임

## ❌ DON'T
- **남의 딜을 `01-accounts/`에 넣기** ← 대시보드가 무용지물이 됨
- 딜 정보를 데일리 노트에만 적기 (→ 검색 지옥)
- 모든 단어를 링크하기 (→ 그래프 털뭉치)
- Finder에서 파일명 변경 (→ 링크 깨짐)
- Core Needs를 4~5개씩 나열 (→ AE가 거절)

---

# 12. 백업 & 복구

- **자동 커밋** 5분마다 · **원격** [GitHub](https://github.com/nohyejin/Jadian)
- **복구**: `git log --oneline` → `git checkout <해시> -- <파일경로>`
- 설정 → File Recovery 에서도 복구 가능

---

# 13. 시작 지점

| 목적 | 열 노트 |
|---|---|
| **매일 아침** | [[SDR_대시보드]] |
| 내 딜 목록 | [[01-accounts/README\|01-accounts]] |
| 학습 딜 참고 | [[04-reference/deal-notes/README\|deal-notes]] |
| 퍼널 전체 | [[퍼널]] |
| 미드마켓이 뭔지 | [[미드마켓]] · [[미드마켓_세일즈_파이프라인]] |
| 어떻게 파는지 | [[세일즈커뮤니케이션의_이해]] · [[설득의_논리_전개]] · [[페르소나]] |
| 무엇으로 설득하는지 | [[버티컬_정의_및_주요_레퍼런스]] · [[플랫폼_연동_현황]] |
| 용어 모를 때 | [[glossary]] |
| 암기 | [[레퍼런스_플래시카드]] → `Cmd+P` → Review flashcards |
