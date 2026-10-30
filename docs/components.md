# Components

디자인 원본 `figcraft/design_system.figcraft`의 **Components** 페이지를 글로 옮긴 문서입니다.
각 항목의 "컴포넌트 세트"는 Figma 컴포넌트 세트 이름과 variant 속성(값)입니다. 크기는 px입니다.

- [Button](#button)
- [Icon Button](#icon-button)
- [Icons](#icons)
- [Badge & Tag](#badge--tag)
- [Card & List](#card--list)
- [Selection Controls](#selection-controls)
- [Text Field & Select](#text-field--select)
- [Modal & Bottom Sheet](#modal--bottom-sheet)
- [Toast & Alert](#toast--alert)
- [Navigation](#navigation)
- [Table](#table)
- [Tabs](#tabs)

### 공통 규칙

- **상태(State)**: Default · Hover · Focus · Disabled를 기본으로, 선택형 컴포넌트는 Selected를 더합니다. Hover는 `{role}/solid-hover`·`{role}/subtle-hover`, Disabled 글자는 `text/disabled`를 씁니다.
- **포커스**: 키보드 포커스는 `Focus/Ring`(3px `border/focus`)으로 표시합니다.
- **아이콘 교체 팁 (FigCraft)**: Variant·Size·State를 먼저 정한 뒤 아이콘을 교체하세요. 아이콘을 바꾼 다음 Variant를 바꾸면 아이콘 색이 이전 값으로 남을 수 있습니다. 그럴 때는 아이콘을 다시 교체하거나 내부 Vector 선 색을 토큰에 다시 연결합니다.
- 인스턴스에서 색을 직접 바꾸지 말고, 속성(Variant·State·Filled 등)을 전환해 토큰 바인딩을 유지하세요.

---

## Button

사용자가 작업을 실행하도록 하는 기본 요소입니다.

| Variant | 쓰임 |
| --- | --- |
| Primary | 한 화면의 핵심 행동. 화면당 하나만 둡니다. |
| Tonal · Outline · Ghost | 보조 행동 |
| Secondary | 강조가 필요한 보조 행동 (오렌지 브랜드 색) |
| Danger | 되돌릴 수 없는 작업 (삭제, 해지 등) |

**컴포넌트 세트** `Button` — Variant(Primary / Secondary / Tonal / Outline / Ghost / Danger) · Size(Small / Medium / Large) · State(Default / Hover / Focus / Disabled)
**속성** Label · Show leading icon / Leading icon · Show trailing icon / Trailing icon
**모서리** `radius/button`

---

## Icon Button

라벨 없이 아이콘 하나로 행동을 나타내는 정사각형 버튼입니다. 툴바·카드 헤더·테이블 행처럼 공간이 좁고 의미가 아이콘으로 분명한 곳(검색, 닫기, 더보기, 삭제)에 씁니다.

- 툴바와 행 안의 반복 행동은 **Ghost**, 화면의 핵심 행동(예: 플로팅 추가 버튼)은 **Primary**, 보조 강조는 **Tonal·Outline·Secondary**, 삭제처럼 되돌릴 수 없는 행동은 **Danger**.
- 크기: 밀도가 높은 B2B 테이블·카드는 Small(32), 일반 툴바는 Medium(40), 모바일 주요 행동은 Large(48).
- **접근성**: 아이콘만 있는 버튼은 코드에서 반드시 접근 가능한 이름(`aria-label="검색"` 등)을 지정하고, 의미가 한눈에 분명하지 않은 아이콘에는 툴팁을 함께 제공합니다.

**컴포넌트 세트** `Icon Button` — Variant(Primary / Secondary / Tonal / Outline / Ghost / Danger) · Size(Small 32 / Medium 40 / Large 48) · State(Default / Hover / Focus / Disabled)
**속성** Icon (instance swap, 기본 `Icon/plus`)

| 사용 예시 | 조합 |
| --- | --- |
| 툴바 | Ghost · Medium |
| 카드 헤더 닫기 | Ghost · Small |
| 목록 행 삭제 | Danger · Small |
| 플로팅 추가 버튼 | Primary · Large |

---

## Icons

기능과 상태를 빠르게 알아보게 하는 선형 아이콘입니다. 24px 그리드에 2px 둥근 선으로 그려져 있고, 기본 색은 `text/primary`입니다. 버튼 등 다른 컴포넌트 안에서는 주변 텍스트와 같은 색 토큰으로 바꿔 씁니다.

- 출처: [Lucide](https://lucide.dev) v1.61.0 (ISC License). 추가 아이콘은 같은 이름 규칙(`Icon/<lucide 이름>`)으로 가져옵니다.
- 구현에서도 같은 Lucide 아이콘을 씁니다 (웹 `lucide-react`, Flutter `lucide_icons_flutter`).

포함된 아이콘 82개:

activity, arrow-down, arrow-left, arrow-right, arrow-up, bell, bookmark, box, building-2, calendar, camera, chart-bar, chart-line, chart-pie, check, chevron-down, chevron-left, chevron-right, chevron-up, circle-alert, circle-check, circle-help, circle-x, clock, compass, copy, credit-card, download, droplet, ellipsis, ellipsis-vertical, external-link, eye, eye-off, file, file-text, filter, folder, globe, heart, house, image, info, layout-grid, link, list, lock, lock-open, log-in, log-out, mail, map, map-pin, menu, message-circle, minus, moon, mountain, navigation, pencil, phone, plus, refresh-cw, route, search, settings, share-2, shopping-cart, sliders-horizontal, star, sun, table, trash-2, trending-down, trending-up, triangle-alert, upload, user, users, wallet, wind, x

---

## Badge & Tag

**배지(Badge)** 는 상태·분류·난이도처럼 읽기 전용 정보를 짧은 라벨로 표시합니다.

- 목록과 표 안에서는 은은한 **Subtle**, 썸네일 위나 강한 강조가 필요할 때는 **Solid**.
- 의미가 있는 색(Success·Warning·Danger·Info)은 상태를 나타낼 때만 쓰고, 단순 분류에는 Neutral/Primary를 씁니다.

**카운트 배지(Count Badge)** 는 아이콘 위에 읽지 않은 알림 수를 표시합니다. 99개를 넘으면 `99+`로 표시합니다.

**태그(Tag)** 는 사용자가 누를 수 있는 필터·선택 칩입니다. 대시보드 필터 바나 B2C 카테고리 선택에 쓰며, 선택 상태에는 체크 아이콘, 적용된 필터 제거에는 닫기(x) 아이콘이 붙습니다.

| 컴포넌트 세트 | 속성 |
| --- | --- |
| `Badge` | Tone(Neutral / Primary / Info / Success / Warning / Danger) · Style(Subtle / Solid) · Size(Medium / Small) |
| `Count Badge` | Tone(Danger / Primary / Neutral) |
| `Tag` | State(Default / Selected / Focus / Disabled) |

**모서리** `radius/badge`

| 사용 예시 | 조합 |
| --- | --- |
| 등산 코스 난이도 | Badge Subtle + 점(dot), Success / Warning / Danger |
| 대시보드 표의 주문 상태 | Badge Small, 상태별 Tone |
| 아이콘 위 알림 수 | Count Badge(Danger)를 절대 위치로 겹침 |
| 필터 칩 | Tag 단일 선택(Selected) + 적용된 조건 제거(Removable) |

---

## Card & List

정보를 묶어 보여주는 기본 단위입니다.

- **아바타(Avatar)**: 사람·조직을 이니셜이나 아이콘으로 표시합니다.
- **리스트 항목(List Item)**: 설정 메뉴·회원 목록처럼 같은 형태의 정보를 세로로 나열합니다. 한 줄은 메뉴, 두 줄은 이름 + 부가정보.
- **카드(Card)**: 독립된 콘텐츠 묶음.
  - **Outlined** — B2B 대시보드의 KPI·요약
  - **Elevated** — B2C 피드의 콘텐츠·추천 (그림자)
  - **Filled** — 배경과 구분만 필요한 보조 영역

| 컴포넌트 세트 | 속성 |
| --- | --- |
| `Avatar` | Size(Small / Medium / Large / XLarge) · Type(Initials / Icon) |
| `List Item` | State(Default / Hover / Selected / Disabled) · Lines(One / Two) |
| `Card` | Style(Outlined / Elevated / Filled) |

**모서리** `radius/card`, `radius/avatar`

| 사용 예시 | 조합 |
| --- | --- |
| 설정 메뉴 | List Item + 아이콘 + 셰브론 + 구분선 |
| 회원 리스트 (B2B 관리자) | List Item + 아바타 + 두 줄 |
| 대시보드 KPI | Card Outlined + Content 슬롯 |
| B2C 콘텐츠 | Card Elevated + 미디어 + 액션 |

---

## Selection Controls

사용자가 옵션을 선택하거나 설정을 켜고 끌 때 사용하는 컨트롤입니다.

- **체크박스(Checkbox)**: 여러 항목을 독립적으로 고르거나 약관 동의처럼 제출 전에 확인을 받을 때. 하위 항목이 일부만 선택되었다면 상위 항목을 **Indeterminate**로 표시합니다.
- **라디오(Radio)**: 2~5개 정도의 상호 배타적인 옵션 중 하나만 고를 때. 항상 하나가 기본 선택되도록 합니다.
- **토글(Toggle)**: 저장 버튼 없이 즉시 적용되는 켜기/끄기 설정(알림, 다크 모드 등).
- 모든 컨트롤은 라벨과 함께 쓰는 것이 기본이고, 표나 카드 안처럼 문맥이 명확할 때만 라벨을 숨깁니다.

| 컴포넌트 세트 | 속성 |
| --- | --- |
| `Checkbox` | Checked(Off / On / Indeterminate) · State(Default / Hover / Focus / Disabled) |
| `Radio` | Checked(Off / On) · State(Default / Hover / Focus / Disabled) |
| `Toggle` | Checked(Off / On) · State(Default / Focus / Disabled) |

사용 예시: 약관 동의(Checkbox), 배송 방법(Radio), 알림 설정(Toggle — 관리자가 고정한 항목은 Disabled와 사유 문구).

---

## Text Field & Select

**입력창(Text Field)** 은 짧은 텍스트(이메일, 이름, 검색어, 숫자 등)를 직접 입력하는 기본 입력 요소입니다.

- 레이블은 항상 보이게 두고, 형식 안내나 오류 메시지는 하단 도움말(Helper)로 전달합니다.
- 모바일·B2C 화면과 터치 위주 폼은 **Large(48)**, 데스크톱 대시보드·필터 바처럼 밀도가 높은 화면은 **Medium(40)**.
- 검색처럼 용도를 아이콘으로 알릴 때는 앞 아이콘, 지우기·비밀번호 보기 같은 보조 동작에는 뒤 아이콘을 켭니다.
- 정해진 목록에서 고르는 값이면 Select를 씁니다.
- **Filled**: `No`는 값이 비어 Placeholder를 보여주는 상태(`text/secondary`), `Yes`는 값을 입력한 상태(`text/primary`). Disabled는 두 경우 모두 `text/disabled`.

**선택 상자(Select)** 는 정해진 목록에서 하나를 고를 때 씁니다. Focus는 목록이 열린 상태입니다. 아직 고르지 않았으면 Filled=No("선택하세요", `text/secondary`), 값을 고른 뒤에는 Filled=Yes(`text/primary`).

| 컴포넌트 세트 | 속성 |
| --- | --- |
| `Text Field` | Size(Medium / Large) · State(Default / Hover / Focus / Error / Disabled) · Filled(No / Yes) |
| `Select` | Size(Medium) · State(Default / Focus / Disabled) · Filled(No / Yes) |

**속성** Label · Value · Helper · Show label · Show helper · Show leading icon / Leading icon · Show trailing icon / Trailing icon (Select는 아이콘 속성 없음)
**모서리** `radius/input`

---

## Modal & Bottom Sheet

사용자의 흐름을 잠시 멈추고 확인·선택을 받아야 할 때 화면 위에 띄우는 레이어입니다. 뒤 화면은 `bg/overlay` 딤으로 가려 포커스를 모읍니다.

- **다이얼로그(Dialog)**: 데스크톱·B2B 화면에서 가운데 정렬. 되돌리기 어려운 작업(삭제, 해지 등)에는 **Destructive** 타입으로 위험을 분명히 알립니다.
- **바텀시트(Bottom Sheet)**: 모바일에서 엄지가 닿기 쉬운 하단에서 올라와 정렬·필터 같은 보조 선택을 처리합니다.
- **액션시트(Action Sheet)**: 항목 몇 개 중 하나를 고르는 짧은 메뉴.

| 컴포넌트 | 속성 |
| --- | --- |
| `Dialog` | Size(Small / Medium) · Type(Default / Destructive) |
| `Bottom Sheet` | 단일 컴포넌트 |
| `Action Sheet` | 단일 컴포넌트 |

**모서리** 다이얼로그 `radius/xl`, 바텀시트 `radius/sheet`(상단 모서리만) · **그림자** `Elevation/3`

---

## Toast & Alert

**토스트(Toast)** 는 사용자의 동작 결과(저장, 삭제, 전송 등)를 잠시 알려 주고 자동으로 사라지는 가벼운 피드백입니다.

- 반전(inverse) 색상으로 어떤 배경에서도 눈에 띕니다.
- 모바일은 하단 중앙, 데스크톱은 우측 하단에 쌓아 표시합니다.
- 실행 취소·보기 같은 액션은 하나만 두고, 사용자가 반드시 읽어야 하는 내용에는 쓰지 않습니다.

**알림 배너(Alert)** 는 페이지나 섹션 안에 고정되어 해결될 때까지 남는 상태 메시지입니다.

- Tone: **Info** 안내 · **Success** 완료 · **Warning** 주의가 필요한 상황 · **Danger** 오류·실패 · **Neutral** 일반 공지
- Style: **Subtle**이 기본, **Accent**(왼쪽 강조 막대)는 여러 정보가 모인 화면에서 더 눈에 띄어야 할 때.

| 컴포넌트 세트 | 속성 |
| --- | --- |
| `Toast` | Tone(Neutral / Info / Success / Warning / Danger) |
| `Alert` | Tone(Neutral / Info / Success / Warning / Danger) · Style(Subtle / Accent) |

---

## Navigation

사용자가 앱·서비스의 주요 영역 사이를 이동하도록 돕는 컴포넌트 묶음입니다.

- **Top App Bar** (모바일 B2C): 현재 위치와 뒤로가기·주요 액션. 목록·상세처럼 계층이 있는 화면은 **Default**, 탭의 첫 화면이나 큰 제목이 필요한 화면은 **Large title**.
- **Bottom Navigation** (모바일 B2C): 3–5개의 최상위 목적지를 전환합니다.
- **Sidebar** (B2B 대시보드 웹): 좌측에 메뉴를 고정 노출합니다. 현재 페이지는 Selected, 권한이 없는 메뉴는 Disabled로 표시하고, 처리할 건수가 있는 메뉴에는 카운트 배지를 함께 보여줍니다.

| 컴포넌트 | 속성 |
| --- | --- |
| `Top App Bar` | Type(Default / Large title) |
| `Bottom Navigation` | 단일 컴포넌트 (`Bottom Nav Item` 조합) |
| `Bottom Nav Item` | State(Default / Selected) |
| `Sidebar` | 단일 컴포넌트 (`Sidebar Item` 조합) |
| `Sidebar Item` | State(Default / Hover / Selected / Focus / Disabled) |

---

## Table

B2B 대시보드에서 주문·고객·재고처럼 여러 항목을 비교하고 일괄 처리할 때 쓰는 데이터 테이블입니다.

- 헤더 셀은 정렬 상태(없음·오름차순·내림차순)를 보여 줍니다.
- 숫자 열은 오른쪽 정렬과 고정폭 숫자(tnum, `Numeric/Small`)로 자릿수를 맞춥니다.
- 본문 셀은 텍스트·숫자·배지·아바타·체크박스·액션 6가지 유형을 조합해 행을 만들고, 행은 기본·호버·선택 상태를 가집니다.
- 상단 툴바(검색·필터 태그·주요 액션)와 하단 페이지네이션을 함께 배치해 하나의 테이블 카드로 씁니다.
- 모바일에서는 테이블 대신 List Item을 권장합니다.

| 컴포넌트 | 속성 |
| --- | --- |
| `Table Header Cell` | Type(Label / Checkbox) · Align(Left / Right) · Sort(None / Ascending / Descending) |
| `Table Cell` | Type(Text / Numeric / Badge / Avatar+Text / Checkbox / Action) |
| `Table Row` | State(Default / Hover / Selected) |
| `Pagination` | 단일 컴포넌트 (`Pagination Item` 조합) |
| `Pagination Item` | Type(Page / Prev / Next / Ellipsis) · State(Default / Hover / Focus / Selected / Disabled) |

---

## Tabs

같은 맥락 안에서 콘텐츠 묶음을 전환할 때 씁니다.

- **Line 탭**: 페이지·목록 상단에서 주문 상태처럼 성격이 다른 목록을 나눌 때. 항목 수가 판단에 도움이 되면 Count를 켭니다.
- **Pill 탭**: B2C 화면의 카테고리·필터처럼 가볍게 고르는 선택지. 아이콘으로 구분을 돕습니다.
- **Segmented Control**: 2–4개의 상호 배타적인 보기 옵션(기간 단위, 지도/목록 보기)을 즉시 바꿀 때. 옵션이 5개 이상이면 탭이나 Select를 씁니다.

| 컴포넌트 세트 | 속성 |
| --- | --- |
| `Tab` | Style(Line / Pill) · State(Default / Hover / Focus / Selected / Disabled) — Label · Show icon / Icon · Show count (+ Count 배지의 Count) |
| `Segmented Control` | Segments(2 / 3 / 4) — 각 Segment의 State / Label |
| `Segment` | State(Default / Selected / Focus / Disabled) |

| 사용 예시 | 조합 |
| --- | --- |
| 주문 목록 상단 | Line 탭 + Count |
| 코스 카테고리 (B2C 모바일) | Pill 탭 + 아이콘 |
| 대시보드 기간 선택 (B2B) | Segmented Control |
