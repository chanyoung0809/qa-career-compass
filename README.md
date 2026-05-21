# QA 커리어 나침반 — 운영매니저용 제작/배포 가이드

이 문서는 **개발이나 영어가 익숙하지 않은 운영매니저**도 동일한 형식의 진로상담 안내 페이지를
만들고, 무료로 인터넷에 공개할 수 있도록 단계별로 안내합니다.

실제 운영 중인 예시 페이지: https://github.com/chanyoung0809/qa-career-compass

---

## 1. 이 사이트가 무엇을 하는 페이지인가요

레이서(수강생)의 이력서 작성 단계에 따라 적합한 안내와 1:1 상담 예약으로
연결해 주는 **정적 HTML 사이트**입니다.

페이지 흐름은 아래와 같습니다.

```
index.html (메인 진입)
  ├─ "이력서를 써봤어요" → overview.html (4가지 페르소나 카드)
  │                          ├─ type01.html (새싹 전공자)
  │                          ├─ type02.html
  │                          ├─ type03.html
  │                          └─ type04.html
  │                              └─ 각 유형 페이지 하단에서 booking.html 로
  │
  └─ "아직이요"        → start_guide.html (STAR 작성법 등 입문 가이드)
                              └─ booking.html 로 연결

booking.html  ← Cal.com 1:1 예약 캘린더가 임베드되어 있음
```

서버나 데이터베이스 없이 **HTML 파일만으로 동작**하기 때문에,
무료로 빠르게 배포할 수 있습니다.

---

## 2. 폴더 구조 — 어떤 파일을 만지면 어디가 바뀌나요

```
QA_resume_confirm_event/
├── index.html          ← 첫 화면. 두 개의 선택 카드
├── overview.html       ← 4가지 페르소나 카드 모음
├── type01.html         ← 페르소나 1번 상세
├── type02.html         ← 페르소나 2번 상세
├── type03.html         ← 페르소나 3번 상세
├── type04.html         ← 페르소나 4번 상세
├── start_guide.html    ← 이력서 작성 입문 가이드
├── booking.html        ← Cal.com 1:1 예약 페이지 (★ Cal.com 연결 부분)
├── assets/
│   ├── css/styles.css  ← 색상, 폰트, 카드 디자인 등 전체 디자인
│   └── js/script.js    ← 카드 클릭 같은 사소한 동작
└── _legacy/            ← 이전 버전 백업. 무시해도 됨
```

**문구만 바꾸고 싶다면** 각 `.html` 파일을 열어 따옴표 또는 태그 사이의
한국어 텍스트만 수정하면 됩니다. CSS는 건드리지 않아도 디자인이 그대로 적용됩니다.

> 메모장보다는 [VS Code](https://code.visualstudio.com/) (무료) 또는
> [Notepad++](https://notepad-plus-plus.org/) 사용을 권장합니다.
> 한국어가 깨지지 않고 색깔로 코드가 구분되어 훨씬 편합니다.

---

## 3. 본인 버전 만들기 — 단계별 가이드

### 사전 준비물 (모두 무료)

| 항목 | 용도 | 가입 링크 |
| --- | --- | --- |
| GitHub 계정 | 코드 저장소 | https://github.com/signup |
| GitHub Desktop | GitHub를 클릭만으로 다루기 | https://desktop.github.com/ |
| Cal.com 계정 | 1:1 예약 캘린더 | https://cal.com/signup |
| Vercel 계정 | 무료 배포 (GitHub 계정으로 로그인 가능) | https://vercel.com/signup |
| VS Code | 텍스트 수정용 에디터 | https://code.visualstudio.com/ |

### 3-1. 이 프로젝트를 내 GitHub로 복사하기 (Fork)

1. https://github.com/chanyoung0809/qa-career-compass 페이지 접속
2. 오른쪽 상단 **Fork** 버튼 클릭
3. "Create fork" 클릭 → 본인 GitHub 계정 아래로 복제 완료
4. 복제된 주소: `https://github.com/본인아이디/qa-career-compass`

### 3-2. 내 컴퓨터로 가져오기 (GitHub Desktop)

1. GitHub Desktop 실행 후 본인 GitHub 계정으로 로그인
2. 좌측 상단 **File → Clone repository** 클릭
3. 방금 Fork한 `qa-career-compass` 선택
4. 저장 위치를 정한 뒤 **Clone** 클릭
5. 해당 폴더가 본인 PC에 다운로드됨

### 3-3. 내용 수정하기

VS Code로 다운로드된 폴더를 열고, 각 HTML 파일에서 다음과 같은 부분만 수정합니다.

- **사이트 제목**: `<title>` 태그와 `<h1>` 태그 안의 문장
- **페르소나 설명**: type01~04.html 안의 본문 문구
- **상담 안내 문구**: booking.html 안의 안내 단락
- **이미지/이모지**: 그대로 두거나 원하는 이모지로 교체

> 처음에는 텍스트만 바꿔 보세요. 구조나 태그(`<div>`, `<span>` 등)는
> 건드리지 않는 것이 안전합니다.

---

## 4. Cal.com 1:1 예약 캘린더 연결하기 (가장 중요)

`booking.html` 페이지의 캘린더는 Cal.com의 **임베드 기능**으로 표시됩니다.
본인 일정으로 바꾸려면 **Cal.com에서 본인 이벤트를 만들고, 그 링크를
`booking.html` 한 군데에 붙여넣기**만 하면 됩니다.

### 4-1. Cal.com 이벤트 만들기

1. https://cal.com 가입 후 로그인
2. 좌측 메뉴 **Event Types** → 우측 상단 **+ New** 클릭
3. 다음과 같이 3개를 만들어 두면 기존 페이지와 호환됩니다.
   - **30분 상담** (간략 상담)
   - **60분 상담** (중간 심도)
   - **90분 상담** (심층 상담)
4. 각 이벤트의 **Event Link**(URL의 마지막 부분)를 메모해 둡니다.
   예: `https://cal.com/내아이디/one-on-one-01` → 링크 식별자는 `내아이디/one-on-one-01`

### 4-2. booking.html 안에서 두 곳 교체하기

`booking.html` 파일을 VS Code로 열어, **`cysong/one-on-one-01`** 이라고
적혀 있는 곳 두 군데를 본인 식별자(`내아이디/내이벤트이름`)로 바꿉니다.

찾아야 하는 곳:

```html
<!-- (1) 새 창으로 여는 fallback 링크 -->
<a href="https://cal.com/cysong/one-on-one-01" ...>새 창에서 예약 페이지 열기</a>

<!-- (2) 인라인 임베드 -->
Cal("inline", {
    elementOrSelector: "#my-cal-inline",
    config: { "layout": "month_view" },
    calLink: "cysong/one-on-one-01"   // ← 이 부분
});
```

VS Code에서 `Ctrl + H` (찾아 바꾸기)로 `cysong/one-on-one-01` 전체를
한 번에 본인 링크로 치환하면 편합니다.

### 4-3. 30/60/90분 안내 카드 수정 (선택)

`booking.html`에는 시간별 옵션 안내 카드가 있습니다(🍓 30분 / 🍰 60분 / 🎂 90분).
본인 운영 정책에 맞춰 문구를 자유롭게 수정하세요.

---

## 5. GitHub에 변경사항 올리기

1. GitHub Desktop으로 돌아가면 좌측에 수정된 파일 목록이 보입니다.
2. 좌측 하단 **Summary** 칸에 변경 내용을 한 줄로 적습니다.
   예: `Cal 링크 교체 및 본문 수정`
3. **Commit to main** 버튼 클릭
4. 상단 **Push origin** 버튼 클릭 → GitHub에 업로드 완료

---

## 6. Vercel로 배포하기 (무료 도메인)

### 6-1. Vercel에 GitHub 계정으로 로그인

1. https://vercel.com/login → **Continue with GitHub** 클릭
2. GitHub 권한 승인

### 6-2. 프로젝트 Import

1. https://vercel.com/new 접속
2. **Import Git Repository** 목록에서 `qa-career-compass` 옆 **Import** 클릭
   - 목록에 안 보이면 위쪽의 **Adjust GitHub App Permissions**를 눌러
     해당 repo 접근 권한을 추가
3. Configure Project 화면 설정:
   - **Project Name**: 원하는 이름 (이게 곧 `{이름}.vercel.app` 주소가 됩니다)
   - **Framework Preset**: `Other`
   - **Root Directory**: 변경하지 않음
   - **Build & Output Settings**: 그대로 두기 (정적 사이트라서 빌드 불필요)
4. **Deploy** 클릭 → 1~2분 후 배포 완료

### 6-3. 도메인 확인 및 변경

- 기본 도메인: `프로젝트명.vercel.app`
- 더 짧게 바꾸고 싶다면 Vercel 프로젝트 화면 **Settings → Domains** 에서 변경
- 개인 소유 도메인이 있다면 같은 화면에서 연결 가능

### 6-4. 이후 업데이트는 자동

GitHub Desktop으로 변경사항을 **Push origin** 하면, Vercel이 자동으로 감지해
1~2분 안에 다시 배포합니다. 별도 작업 불필요.

---

## 7. 자주 묻는 질문

**Q. 코드를 만지는 게 무서워요. 망가지면 어떡하죠?**

GitHub Desktop의 좌측 상단 **History** 탭에서 언제든 이전 시점으로 돌아갈 수 있어요.
또한 Fork한 본인 repo는 원본에 영향을 주지 않습니다. 마음껏 시도해 보세요.

**Q. 캘린더가 안 떠요.**

`booking.html` 안의 `calLink` 부분이 본인 Cal.com 링크 식별자와 정확히 일치하는지 확인하세요.
앞에 `https://cal.com/` 같은 주소까지 적으면 동작하지 않습니다. **아이디/이벤트이름** 형식만 남겨야 합니다.

**Q. 한글이 깨져요.**

파일을 저장할 때 인코딩이 **UTF-8** 이어야 합니다. VS Code는 기본값이 UTF-8이므로 안전합니다.
메모장으로 저장하면 다른 인코딩으로 저장될 수 있어 한글이 깨질 수 있습니다.

**Q. Vercel 무료 플랜으로 충분한가요?**

운영 안내 페이지 수준의 트래픽이라면 충분합니다.
월 100GB 대역폭, 무제한 배포가 무료 제공됩니다.

**Q. Cal.com 무료 플랜으로 충분한가요?**

1:1 예약은 무료 플랜으로 무제한 사용 가능합니다.
팀 기능, 라운드로빈 배정 등 고급 기능만 유료입니다.

---

## 8. 도움이 필요할 때

- 이 페이지를 만든 사람에게 직접 문의 (slack/메일)
- GitHub 사용법: https://docs.github.com/ko (한국어 공식 문서)
- Cal.com 사용법: https://cal.com/help
- Vercel 사용법: https://vercel.com/docs (한국어 일부 제공)

---

## 라이선스 / 사용 안내

본 페이지의 문구와 디자인은 엘리스 QA 트랙 운영팀 내부 사용을 위해 제작되었습니다.
구조와 코드를 참고하여 본인 운영용 페이지로 자유롭게 변경해 사용하세요.
