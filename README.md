# OHC Design System (ohcds)

클라이언트에게 별도 디자인 시스템이 없을 때 기본으로 쓰는 OHC 디자인 시스템의 **원본 저장소**입니다.
디자인 원본인 FigCraft 파일과, 그 안의 토큰·컴포넌트 규칙을 글로 옮긴 문서를 담고 있습니다.
코드 구현은 이 저장소를 기준으로 각 플랫폼 저장소에서 따로 관리합니다.

## 구성

| 경로 | 내용 |
| --- | --- |
| `figcraft/design_system.figcraft` | 디자인 원본 (FigCraft). 변수·텍스트/이펙트 스타일·컴포넌트가 모두 여기에 있습니다. |
| `docs/foundations.md` | 토큰 설명 — Color, Typography, Spacing, Radius, Elevation |
| `docs/components.md` | 컴포넌트 설명 — 용도, Figma 컴포넌트 세트와 속성, 사용 규칙 |

## 구현 저장소

| 저장소 | 내용 |
| --- | --- |
| [`ohcds_nextjs`](../ohcds_nextjs) | Next.js + Tailwind CSS v4 + shadcn/ui 쇼케이스와 웹 샘플 페이지 (대시보드, 모바일 금융 앱) |
| [`ohcds_flutter`](../ohcds_flutter) | Flutter 이식판 (토큰, `Ohc*` 컴포넌트, 갤러리 앱) |

토큰이나 컴포넌트 스펙을 바꿀 때는 이 저장소의 FigCraft 파일과 문서를 먼저 고치고, 각 구현 저장소에 반영합니다.

## FigCraft 파일 구조

| 페이지 | 프레임 |
| --- | --- |
| Foundations | Color(Primitive, Semantic · Light, Semantic · Dark), Typography, Radius, Elevation, Spacing |
| Components | Button, Icons, Badge & Tag, Card & List, Selection Controls, Text Field, Modal & Bottom Sheet, Toast & Alert, Navigation, Table, Tabs, Icon Button |

각 컴포넌트 프레임은 `Header`(설명) · `Usage`(사용 예시) · `Variants`(컴포넌트 세트) 순서로 구성됩니다.

### 변수 컬렉션

| 컬렉션 | 모드 | 내용 |
| --- | --- | --- |
| Primitive | Value | 원본 팔레트 (`primary/50` … `success/950`, `base/white`, `base/black`) |
| Semantic | Light / Dark | 역할별 색상 (`bg/*`, `text/*`, `border/*`, `{role}/*`, `shadow/*`) |
| Typography | Mobile / Desktop | 글꼴(`font/sans`, `font/mono`)과 Display·Heading 크기 |
| Spacing | Mobile / Desktop | `space/*` 스케일과 `layout/*` 토큰 |
| Radius | Value | `radius/*` 스케일과 역할 토큰 |

### 스타일

- 텍스트 스타일 19개: Display, Heading, Title, Body, Label, Caption, Overline, Numeric, Code
- 이펙트 스타일 4개: `Elevation/1`~`3`, `Focus/Ring`

## 클라이언트 브랜드에 맞추기

1. **색** — Primitive의 `primary` 램프(11단계)만 교체합니다. 시맨틱 색상이 램프를 참조하므로 화면 전체가 따라 바뀝니다.
2. **모서리** — 역할 토큰(`radius/button`, `radius/card` 등)이 가리키는 스케일만 바꿉니다.
3. **글꼴** — Typography 컬렉션의 `font/sans`를 바꿉니다.

## 이름 규칙

- 토큰 이름은 Figma 경로(`bg/canvas`, `primary/solid`, `layout/page-margin`)를 기준으로 하며, 각 구현은 이 경로를 그대로 옮깁니다.
  예: CSS `--ohc-bg-canvas` · Tailwind `bg-bg-canvas` · Flutter `ohc.colors.bgCanvas`
- Mobile 값이 기본이고, Desktop 값은 너비 768px(48rem) 이상에서 적용합니다.
- OHC의 `secondary`는 오렌지 브랜드 색입니다. shadcn/ui의 `secondary`(낮은 강조의 중립색)와 다릅니다.
