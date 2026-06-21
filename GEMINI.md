# KEPCO ES PMS 디자인 시스템 — Gemini 지침

이 프로젝트는 켑코이에스(KEPCO ES) 사업관리시스템(PMS) 디자인 시안 C의 디자인 시스템을 따릅니다.
HTML/CSS를 생성하거나 수정할 때 반드시 아래 규칙을 적용하세요.

---

## 폰트

- `'Noto Sans KR', sans-serif` (Google Fonts, weight: 300/400/500/700/900)
- 기본 font-size: `15px`, line-height: `1.55`
- `-webkit-font-smoothing: antialiased` 적용

---

## 색상 토큰 (CSS Variables)

```css
:root {
  /* 브랜드 */
  --navy:     #0F3460;
  --blue:     #1a5fb4;
  --blue-lt:  #dde8f8;
  --blue-md:  #7db0e8;
  --blue-dk:  #103d80;
  --amber:    #f5870a;
  --amber-lt: #fff1e0;
  --amber-dk: #c2660a;

  /* 시멘틱 */
  --green:    #16a34a;
  --green-lt: #e3f9ed;
  --green-dk: #0d7a3a;
  --red:      #ef4444;
  --red-lt:   #fdecec;
  --red-dk:   #c0291a;
  --purple:   #5e35b1;

  /* 배경/텍스트 */
  --bg:         #f5f7fa;
  --bg2:        #ffffff;
  --text:       #2d3748;
  --text-muted: #64748b;
  --text-label: #475569;
  --border:     #e2e8f0;
  --sidebar-bg: #eef1f6;

  /* 공통 */
  --radius-sm: 6px;
  --radius-md: 8px;
  --font-ui:   'Noto Sans KR', sans-serif;
}
```

---

## 레이아웃 구조

```
[A] Header       — height: 56px, bg: --navy, shadow: 0 2px 6px rgba(0,0,0,0.25)
[B] LNB Sidebar  — width: 256px, bg: --sidebar-bg, border-right: 1px solid --border
[C] 탭 네비      — height: 58px, bg: linear-gradient(#fff → #edf3fa)
[D] 브레드크럼   — bg: --bg2, border-bottom: 1px solid --border
[E] 콘텐츠 영역  — padding: 24px, overflow-y: auto
[F] 푸터         — border-top: 1px solid --border, font-size: 13px
```

---

## 컴포넌트 규칙

### 버튼 `.btn`
```css
height: 38px;
padding: 0 18px;
border-radius: var(--radius-sm);   /* 6px */
font-weight: 700;
font-size: 13px;
transition: all 0.15s ease;
```
- `.btn-primary`  → bg `--blue`,  hover bg `--blue-dk`
- `.btn-accent`   → bg `--green`, hover bg `--green-dk`
- `.btn-secondary`→ bg `#64748b`
- `.btn-outline`  → border 1.5px `--border`, hover border `--blue-md`

### 카드 `.card`
```css
background: var(--bg2);
border-radius: var(--radius-md);   /* 8px */
border: 1px solid var(--border);
box-shadow: 0 1px 3px rgba(15,23,42,0.07), 0 1px 2px rgba(15,23,42,0.04);
padding: 20px 24px;
```
- 카드 타이틀: font-size 15px, weight 700, color `--blue-dk`
- 타이틀 좌측 세로 바: width 4px, height 16px, bg `--blue`, border-radius 2px

### 폼 컨트롤 `.form-control`
```css
height: 38px;
padding: 0 12px;
border: 1.5px solid var(--border);
border-radius: var(--radius-sm);
font-size: 13px;
```
- focus: `border-color: --blue; box-shadow: 0 0 0 3px rgba(26,95,180,0.16);`
- 레이블: font-size 13px, weight 600, color `--text-label`

### 테이블 `.data-table`
```css
/* th */
background-color: #f1f5f9;
color: var(--text-label);
font-weight: 700;
font-size: 13px;
padding: 11px 16px;
border-bottom: 2px solid var(--border);

/* td */
padding: 11px 16px;
border-bottom: 1px solid var(--border);

/* tr:hover */
background-color: #f8faff;
```

### 배지 `.badge`
```css
padding: 3px 10px;
border-radius: var(--radius-sm);
font-size: 13px;
font-weight: 500;
```
- `.badge-success`  → bg `--green-lt`, color `--green-dk`
- `.badge-danger`   → bg `--red-lt`,   color `--red-dk`
- `.badge-warning`  → bg `--amber-lt`, color `--amber-dk`
- `.badge-secondary`→ bg `#f1f5f9`,    color `#64748b`

### KPI 카드 `.kpi-card`
```css
border-left: 4px solid var(--blue);  /* .green/.amber/.red 클래스로 색상 변경 */
padding: 16px 20px;
```
- 수치: font-size 28px, weight 900, color `--navy`
- 레이블: font-size 13px, weight 700, color `--text-muted`

### LNB 메뉴
- 1depth: height 44px, border-radius 8px, 활성 시 bg `--blue-lt`, color `--blue-dk`
- 2depth: height 38px, padding-left 55px, 활성 시 font-weight 700
- hover: `background-color: rgba(26,95,180,0.07)`

### 탭 아이템 `.tab-item`
```css
height: 38px;
padding: 0 20px;
border-radius: 7px;
font-size: 14px;
border: 1px solid #cbd5e1;
```
- 활성: bg `--navy`, color white, box-shadow `0 6px 14px rgba(15,52,96,0.24)`
- 활성 인디케이터: `::after` — bottom: -9px, height 3px, color `--amber`

---

## 다크 모드 (`body.dark`)

```css
--bg:    #0f172a;
--bg2:   #1e293b;
--text:  #f8fafc;
--border:#334155;
--navy:  #38bdf8;
--blue:  #60a5fa;
```

---

## 일반 규칙

- 모든 인터랙션에 `transition` 적용 (버튼 0.15s, 사이드바 0.25s)
- 그림자는 `rgba(15,23,42, ...)` 계열 사용
- border-radius는 `--radius-sm(6px)` 또는 `--radius-md(8px)` 사용
- 스크롤바: width 4~6px, thumb color `#c8d4e0`, track transparent
