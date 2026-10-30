# Foundations

디자인 원본 `figcraft/design_system.figcraft`의 **Foundations** 페이지와 변수·스타일을 글로 옮긴 문서입니다.

- [Color](#color)
- [Typography](#typography)
- [Spacing](#spacing)
- [Radius](#radius)
- [Elevation](#elevation)

---

## Color

### 기본 색상 (Primitive)

브랜드·중립·상태 색상의 원본 팔레트입니다. **화면에 직접 쓰지 않고** 시맨틱 색상이 이 값을 참조하며, 의뢰인 브랜드에 맞출 때는 `primary` 램프만 교체합니다.
브랜드 램프(primary·secondary·neutral)는 Ridgeline 원본 값을 기준으로 OKLCH 보간한 11단계이고, 상태색은 Tailwind v3 팔레트를 씁니다.

| 단계 | primary<br>Ridgeline Pine | secondary<br>Ridgeline Sunset | neutral<br>Ridgeline Slate | danger<br>Tailwind red | warning<br>Tailwind amber | info<br>Tailwind blue | success<br>Tailwind green |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 50 | #EEFAF6 | #FFF4EE | #F8FAFC | #FEF2F2 | #FFFBEB | #EFF6FF | #F0FDF4 |
| 100 | #DDF4EC | #FFE3D5 | #EAEEF3 | #FEE2E2 | #FEF3C7 | #DBEAFE | #DCFCE7 |
| 200 | #B0E5D3 | #FFC8AE | #DAE1EA | #FECACA | #FDE68A | #BFDBFE | #BBF7D0 |
| 300 | #7FD6B9 | #FFAB85 | #CBD5E1 | #FCA5A5 | #FCD34D | #93C5FD | #86EFAC |
| 400 | #54BB9E | #F98C60 | #96A3B5 | #F87171 | #FBBF24 | #60A5FA | #4ADE80 |
| 500 | #14A085 | #F26B3A | #64748B | #EF4444 | #F59E0B | #3B82F6 | #22C55E |
| 600 | #0E7C66 | #D9532A | #4B5A6F | #DC2626 | #D97706 | #2563EB | #16A34A |
| 700 | #0C6554 | #B1401F | #334155 | #B91C1C | #B45309 | #1D4ED8 | #15803D |
| 800 | #0A4F42 | #8A2E14 | #202B3F | #991B1B | #92400E | #1E40AF | #166534 |
| 900 | #09362D | #4F1A0C | #0F172A | #7F1D1D | #78350F | #1E3A8A | #14532D |
| 950 | #05201A | #300F06 | #0A1020 | #450A0A | #451A03 | #172554 | #052E16 |

`base/white` #FFFFFF, `base/black` #000000

### 시맨틱 색상 (Semantic)

화면에 실제로 적용하는 역할별 색상입니다. 배경·텍스트·테두리와 상태 강조에 사용하며, Light/Dark 모드에 따라 값이 자동으로 바뀝니다.

| 그룹 | 용도 |
| --- | --- |
| `bg/*` | 화면 배경(`canvas`), 카드 등 표면(`surface`), 보조 영역(`subtle`, `muted`), 반전 배경(`inverse`), 모달 딤(`overlay`) |
| `text/*` | 본문(`primary`), 보조 설명(`secondary`), 비활성(`disabled`), 반전 배경 위 글자(`inverse`) |
| `border/*` | 기본 구분선(`default`), 강조 테두리(`strong`), 키보드 포커스(`focus`) |
| `{role}/*` | 역할 색. role은 `primary`, `secondary`, `danger`, `warning`, `info`, `success` |
| `shadow/*` | Elevation 스타일에 쓰는 그림자 색 |

역할 색은 모두 같은 7가지 슬롯을 가집니다.

| 슬롯 | 용도 |
| --- | --- |
| `solid` / `solid-hover` | 채워진 버튼·배지의 배경과 그 호버 |
| `on-solid` | `solid` 위의 글자·아이콘 |
| `subtle` / `subtle-hover` | 은은한 배경(Tonal 버튼, Subtle 배지, 알림 배너)과 그 호버 |
| `text` | 흰/어두운 배경 위의 역할 색 글자·링크 |
| `border` | 역할 색 테두리 |

| 토큰 | Light | Dark |
| --- | --- | --- |
| `bg/canvas` | `neutral/50` #F8FAFC | `neutral/950` #0A1020 |
| `bg/surface` | `base/white` #FFFFFF | `neutral/900` #0F172A |
| `bg/subtle` | `neutral/100` #EAEEF3 | `neutral/800` #202B3F |
| `bg/muted` | `neutral/200` #DAE1EA | `neutral/700` #334155 |
| `bg/inverse` | `neutral/900` #0F172A | `neutral/50` #F8FAFC |
| `text/primary` | `neutral/900` #0F172A | `neutral/50` #F8FAFC |
| `text/secondary` | `neutral/600` #4B5A6F | `neutral/400` #96A3B5 |
| `text/disabled` | `neutral/400` #96A3B5 | `neutral/600` #4B5A6F |
| `text/inverse` | `base/white` #FFFFFF | `neutral/900` #0F172A |
| `border/default` | `neutral/200` #DAE1EA | `neutral/800` #202B3F |
| `border/strong` | `neutral/300` #CBD5E1 | `neutral/700` #334155 |
| `border/focus` | `primary/500` #14A085 | `primary/400` #54BB9E |
| `primary/solid` | `primary/600` #0E7C66 | `primary/400` #54BB9E |
| `primary/solid-hover` | `primary/700` #0C6554 | `primary/300` #7FD6B9 |
| `primary/on-solid` | `base/white` #FFFFFF | `primary/950` #05201A |
| `primary/subtle` | `primary/50` #EEFAF6 | `primary/950` #05201A |
| `primary/subtle-hover` | `primary/100` #DDF4EC | `primary/900` #09362D |
| `primary/text` | `primary/700` #0C6554 | `primary/300` #7FD6B9 |
| `primary/border` | `primary/200` #B0E5D3 | `primary/800` #0A4F42 |
| `secondary/solid` | `secondary/700` #B1401F | `secondary/400` #F98C60 |
| `secondary/solid-hover` | `secondary/800` #8A2E14 | `secondary/300` #FFAB85 |
| `secondary/on-solid` | `base/white` #FFFFFF | `secondary/950` #300F06 |
| `secondary/subtle` | `secondary/50` #FFF4EE | `secondary/950` #300F06 |
| `secondary/subtle-hover` | `secondary/100` #FFE3D5 | `secondary/900` #4F1A0C |
| `secondary/text` | `secondary/700` #B1401F | `secondary/300` #FFAB85 |
| `secondary/border` | `secondary/200` #FFC8AE | `secondary/800` #8A2E14 |
| `danger/solid` | `danger/600` #DC2626 | `danger/400` #F87171 |
| `danger/solid-hover` | `danger/700` #B91C1C | `danger/300` #FCA5A5 |
| `danger/on-solid` | `base/white` #FFFFFF | `danger/950` #450A0A |
| `danger/subtle` | `danger/50` #FEF2F2 | `danger/950` #450A0A |
| `danger/subtle-hover` | `danger/100` #FEE2E2 | `danger/900` #7F1D1D |
| `danger/text` | `danger/700` #B91C1C | `danger/300` #FCA5A5 |
| `danger/border` | `danger/200` #FECACA | `danger/800` #991B1B |
| `warning/solid` | `warning/700` #B45309 | `warning/400` #FBBF24 |
| `warning/solid-hover` | `warning/800` #92400E | `warning/300` #FCD34D |
| `warning/on-solid` | `base/white` #FFFFFF | `warning/950` #451A03 |
| `warning/subtle` | `warning/50` #FFFBEB | `warning/950` #451A03 |
| `warning/subtle-hover` | `warning/100` #FEF3C7 | `warning/900` #78350F |
| `warning/text` | `warning/700` #B45309 | `warning/300` #FCD34D |
| `warning/border` | `warning/200` #FDE68A | `warning/800` #92400E |
| `info/solid` | `info/600` #2563EB | `info/400` #60A5FA |
| `info/solid-hover` | `info/700` #1D4ED8 | `info/300` #93C5FD |
| `info/on-solid` | `base/white` #FFFFFF | `info/950` #172554 |
| `info/subtle` | `info/50` #EFF6FF | `info/950` #172554 |
| `info/subtle-hover` | `info/100` #DBEAFE | `info/900` #1E3A8A |
| `info/text` | `info/700` #1D4ED8 | `info/300` #93C5FD |
| `info/border` | `info/200` #BFDBFE | `info/800` #1E40AF |
| `success/solid` | `success/700` #15803D | `success/400` #4ADE80 |
| `success/solid-hover` | `success/800` #166534 | `success/300` #86EFAC |
| `success/on-solid` | `base/white` #FFFFFF | `success/950` #052E16 |
| `success/subtle` | `success/50` #F0FDF4 | `success/950` #052E16 |
| `success/subtle-hover` | `success/100` #DCFCE7 | `success/900` #14532D |
| `success/text` | `success/700` #15803D | `success/300` #86EFAC |
| `success/border` | `success/200` #BBF7D0 | `success/800` #166534 |
| `shadow/ambient` | #0F172A0A | #0000004D |
| `shadow/key-1` | #0F172A0F | #00000080 |
| `shadow/key-2` | #0F172A14 | #00000099 |
| `shadow/key-3` | #0F172A1F | #000000B3 |
| `bg/overlay` | #0F172A80 | #000000A6 |

---

## Typography

화면의 정보 위계를 만드는 글자 스타일입니다. 제목·본문·라벨·숫자·코드 용도별로 골라 쓰며, **Display·Heading 계열만** Mobile/Desktop 모드에 따라 크기가 바뀝니다.

### 글꼴

| 토큰 | 글꼴 | 용도 |
| --- | --- | --- |
| `font/sans` | Pretendard | 제목·본문·라벨·숫자 전체. 한글과 라틴 글자의 균형이 좋고 9가지 굵기를 지원합니다. |
| `font/mono` | JetBrains Mono | 코드, 토큰 이름, 고정폭이 필요한 값. 한글이 섞인 코드는 D2Coding으로 대체합니다. |

### 텍스트 스타일

크기는 `글자 크기/줄 높이`(px)이고, `→` 오른쪽은 Desktop 값입니다. 자간은 글자 크기 대비 %입니다.

| 스타일 | 크기 | 굵기 | 자간 | 용도 |
| --- | --- | --- | --- | --- |
| `Display/Large` | 36/46 → 48/60 | Bold | -2% | 랜딩·온보딩 히어로 |
| `Display/Medium` | 32/42 → 40/52 | Bold | -2% | 섹션 히어로, 빈 화면 타이틀 |
| `Heading/H1` | 28/38 → 32/42 | Bold | -1.5% | 페이지 제목 |
| `Heading/H2` | 22/30 → 24/32 | Bold | -1% | 섹션 제목 |
| `Heading/H3` | 17/24 → 20/28 | SemiBold | -0.5% | 카드·패널 제목 |
| `Title` | 15/22 | SemiBold | 0 | 리스트 항목 제목, 강조 본문 |
| `Body/Large` | 17/28 | Regular | 0 | 읽기 중심 긴 본문 |
| `Body/Medium` | 15/24 | Regular | 0 | 기본 본문 |
| `Body/Small` | 13/20 | Regular | 0 | 대시보드 표, 보조 설명 |
| `Label/Large` | 15/20 | SemiBold | 0 | 버튼, 탭 |
| `Label/Medium` | 13/18 | Medium | 0 | 작은 버튼, 입력 라벨, 메타 정보 |
| `Label/Small` | 11/14 | Medium | 0 | 배지, 타임스탬프 |
| `Caption` | 12/16 | Regular | 0 | 도움말, 각주 |
| `Overline` | 11/14 | SemiBold | 2% | 그룹 라벨 (대문자) |
| `Numeric/Large` | 28/36 | Bold | -1% | KPI 수치 |
| `Numeric/Medium` | 15/20 | Medium | 0 | 카드·요약의 강조 숫자 |
| `Numeric/Small` | 13/20 | Medium | 0 | 테이블·리스트 안 숫자 |
| `Code/Medium` | 14/22 | Regular (mono) | 0 | 코드 블록 |
| `Code/Small` | 12/18 | Regular (mono) | 0 | 인라인 코드, 토큰 이름 |

- `Numeric/*`은 고정폭 숫자(`font-feature-settings: "tnum"`)를 적용해 자릿수를 맞춥니다.

---

## Spacing

요소 사이의 거리와 컴포넌트 안쪽 여백을 정하는 공통 단위입니다. **4px 그리드**를 기본으로 하고, 아이콘·배지·촘촘한 리스트처럼 좁은 곳에만 2px 반 단계(2·6·10)를 씁니다.

- 버튼·입력창·리스트 같은 **컴포넌트 내부** 패딩과 간격 → `space/*`
- 화면 좌우 여백·그리드 간격·섹션 간격처럼 **기기 크기에 따라 달라지는** 값 → `layout/*`

### 기본 스케일 (`space/*`)

모든 모드에서 같은 값입니다. 임의의 숫자 대신 가장 가까운 단계를 고르세요.

| 토큰 | 값 | 주요 용도 |
| --- | --- | --- |
| `space/0` | 0 | 여백 없음 · 붙어 있어야 하는 요소 |
| `space/2` | 2px | 아이콘·텍스트 미세 보정, 배지 내부 |
| `space/4` | 4px | 아이콘과 라벨 사이, 촘촘한 인라인 간격 |
| `space/6` | 6px | 칩·태그 세로 패딩, 촘촘한 표 셀 |
| `space/8` | 8px | 관련 요소 묶음, 작은 버튼 패딩 |
| `space/10` | 10px | 2줄 리스트 항목 상하 여백 등 촘촘한 반 단계 |
| `space/12` | 12px | 리스트 항목 내부, 입력창 세로 패딩 |
| `space/16` | 16px | 기본 컴포넌트 패딩, 모바일 화면 여백 |
| `space/20` | 20px | 큰 버튼 가로 패딩, 폼 필드 사이 |
| `space/24` | 24px | 데스크톱 카드 패딩, 그리드 간격 |
| `space/32` | 32px | 모바일 섹션 간격, 데스크톱 화면 여백 |
| `space/40` | 40px | 콘텐츠 그룹 사이 큰 간격 |
| `space/48` | 48px | 섹션 상하 여백, 모달 내부 큰 구획 |
| `space/64` | 64px | 데스크톱 섹션 간격 |
| `space/80` | 80px | 랜딩 히어로 상하 여백 |
| `space/96` | 96px | 랜딩 페이지 큰 블록 구분 |

### 레이아웃 토큰 (`layout/*`)

페이지·섹션·카드 같은 레이아웃 프레임에 바인딩합니다. 최상위 프레임의 Spacing 모드만 Mobile / Desktop으로 바꾸면 안쪽 간격이 한 번에 따라갑니다.

| 토큰 | Mobile | Desktop | 참조 | 주요 용도 |
| --- | --- | --- | --- | --- |
| `layout/page-margin` | 16px | 32px | `space/16` → `space/32` | 화면 좌우 바깥 여백 |
| `layout/gutter` | 16px | 24px | `space/16` → `space/24` | 그리드 컬럼·나란히 놓인 카드 사이 간격 |
| `layout/section-gap` | 32px | 64px | `space/32` → `space/64` | 페이지 안 큰 섹션 사이 간격 |
| `layout/stack-gap` | 12px | 16px | `space/12` → `space/16` | 섹션 안 요소를 세로로 쌓을 때 기본 간격 |
| `layout/card-padding` | 16px | 24px | `space/16` → `space/24` | 카드·패널·모달 안쪽 여백 |

---

## Radius

UI 요소의 둥글기를 일관되게 맞추는 값입니다. 컴포넌트에는 숫자 스케일 대신 **역할 토큰을 우선** 적용하세요.
역할 토큰은 스케일을 참조하므로, 클라이언트 브랜드에 맞춰 더 둥글게/각지게 바꾸려면 역할 토큰의 참조만 바꾸면 전체 UI가 함께 변합니다.
작은 컨트롤일수록 작은 값, 큰 컨테이너일수록 큰 값을 쓰고, 안쪽 요소의 반경은 바깥 컨테이너보다 작게(바깥 − 패딩) 유지하세요.

### 스케일

| 토큰 | 값 | 용도 |
| --- | --- | --- |
| `radius/none` | 0 | 구분선, 화면 끝까지 닿는 미디어, 표 셀 |
| `radius/xs` | 2px | 체크박스, 진행 막대, 툴팁 화살표 |
| `radius/sm` | 4px | 태그, 작은 버튼, 촘촘한 표 안 칩 |
| `radius/md` | 8px | 인터랙티브 컨트롤 기본값 — 버튼, 입력창, 선택 상자 |
| `radius/lg` | 12px | 컨테이너 — 카드, 팝오버, 드롭다운 메뉴 |
| `radius/xl` | 16px | 큰 컨테이너 — 다이얼로그, 히어로 카드 |
| `radius/2xl` | 24px | 모바일 바텀시트·전체 화면 모달 (상단 모서리) |
| `radius/full` | 9999px | 알약·원 — 배지, 아바타, 토글, 칩 |

### 역할 토큰

| 토큰 | 참조 | 적용 대상 |
| --- | --- | --- |
| `radius/button` | `radius/md` (8px) | 버튼 |
| `radius/input` | `radius/md` (8px) | 입력창, 선택 상자, 검색 |
| `radius/card` | `radius/lg` (12px) | 카드, 리스트 그룹, 대시보드 위젯 |
| `radius/badge` | `radius/full` | 배지, 상태 알약, 칩 |
| `radius/sheet` | `radius/2xl` (24px) | 바텀시트·모달 (상단 모서리만) |
| `radius/avatar` | `radius/full` | 아바타, 프로필 이미지 |

---

## Elevation

그림자는 화면 위 요소의 '높이'를 표현해, 어떤 표면이 다른 표면 위에 놓여 있는지와 무엇이 지금 사용자의 주의를 요구하는지 알려 줍니다. 높이가 높을수록 일시적이고 중요한 레이어입니다.

| 스타일 | 그림자 (x y blur spread) | 용도 |
| --- | --- | --- |
| `Elevation/1` | `shadow/key-1` 0 1 3 0 + `shadow/ambient` 0 1 2 0 | 목록 행·리스트 아이템 — 배경에서 살짝 떠 있는 요소 |
| `Elevation/2` | `shadow/key-2` 0 6 16 -2 + `shadow/ambient` 0 2 4 0 | 카드·패널·대시보드 위젯 — 콘텐츠를 묶는 표면 |
| `Elevation/3` | `shadow/key-3` 0 16 40 -6 + `shadow/ambient` 0 4 10 0 | 바텀시트·모달·팝오버 — 콘텐츠 위에 겹쳐 뜨는 레이어 |
| `Focus/Ring` | `border/focus` 0 0 0 3 | 키보드 포커스 표시 |

다크 모드에서는 그림자가 잘 보이지 않으므로 같은 스타일이 더 진한 그림자 색(`shadow/*` Dark 값)으로 바뀌며, 표면 색(`bg/surface`) 차이와 함께 높이를 전달합니다.
