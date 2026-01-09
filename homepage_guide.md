# 📚 독서 동아리 '책울림' 홈페이지 제작 가이드

이 문서는 중학교 독서 동아리 활동을 위한 웹사이트 제작 과정을 단계별로 설명합니다. 이 가이드를 통해 HTML, CSS, JavaScript를 사용하여 반응형 홈페이지를 구축하는 방법을 이해할 수 있습니다.

## 1. 프로젝트 개요
*   **목적**: 동아리 소개, 활동 공유, 신규 부원 모집(가입 신청) 등 동아리 운영을 돕는 온라인 공간 마련
*   **기술 스택**: HTML5, CSS3, Vanilla JavaScript (프레임워크 없이 기본 웹 기술 사용)
*   **주요 기능**:
    *   반응형 메뉴 (모바일 지원)
    *   부드러운 스크롤 이동
    *   노션(Notion) 설문지 연동 (팝업창)
    *   SNS 공유를 위한 오픈 그래프(Open Graph) 설정

## 2. 파일 구조
프로젝트는 크게 세 가지 파일로 구성됩니다.
```
📂 homepage/
 ├── index.html  (구조 및 내)
 ├── style.css   (디자인 및 스타일)
 └── script.js   (동적 기능 및 상호작용)
```

## 3. 단계별 구현 내용

### 1단계: HTML 구조 잡기 (`index.html`)
웹사이트의 뼈대를 만듭니다. 시맨틱 태그(`header`, `nav`, `section`, `footer`)를 사용하여 의미 있는 구조를 만듭니다.

**주요 섹션:**
*   **Navigation**: 로고와 메뉴 링크, 가입 신청 버튼.
*   **Hero**: 메인 배너. 눈길을 끄는 문구와 책 그래픽 배치.
*   **About**: 동아리 활동(읽기, 나누기, 글쓰기) 소개 카드.
*   **Teacher**: 지도 교사 소개. (예: 헤르만 헤세와 같은 인생 작가 소개 포함)
*   **Reading**: 이달의 선정 도서 소개.
*   **Community & Gallery**: 공지사항, 서평, 활동 사진 갤러리.
*   **Join Button**: 노션 폼으로 연결되는 링크.

### 2단계: 디자인 입히기 (`style.css`)
'모던 북카페' 컨셉의 차분하고 지적인 분위기를 연출합니다.

**컬러 팔레트:**
*   `Deep Navy` (#2C3E50): 지적이고 신뢰감 있는 주조색
*   `Warm Orange` (#E67E22): 따뜻함과 활력을 주는 강조색
*   `Off-white` (#F9F9F9): 눈이 편안한 배경색

**폰트:**
*   `Noto Sans KR`: 가독성 좋은 본문 폰트
*   `Song Myung`: 감성적인 명조체 (제목용)

**반응형 설정:**
*   `@media (max-width: 768px)` 쿼리를 사용하여 모바일 화면에서는 메뉴가 햄버거 버튼으로 바뀌고, 레이아웃이 세로로 정렬되도록 조정했습니다.

### 3단계: 기능 구현 (`script.js`)
사용자와 상호작용하는 기능을 추가합니다.

*   **모바일 메뉴 토글**: 햄버거 아이콘 클릭 시 메뉴 열림/닫힘.
*   **스무스 스크롤**: 메뉴 클릭 시 해당 섹션으로 부드럽게 이동.
*   **스크롤 애니메이션**: 스크롤을 내릴 때 요소들이 천천히 나타나는 효과 (`IntersectionObserver` 사용).
*   **가입 신청 팝업**:
    *   노션 보안 정책(iframe 입력 차단)을 우회하기 위해 `window.open`을 사용하여 별도의 팝업창을 띄웁니다.
    *   창 크기와 위치를 중앙으로 정렬하여 사용자 편의성을 높였습니다.

```javascript
// 팝업창 코드 예시
const width = 600;
const height = 800;
const left = (window.innerWidth - width) / 2;
const top = (window.innerHeight - height) / 2;
window.open(url, 'JoinForm', `width=${width},height=${height},top=${top},left=${left},...`);
```

## 4. 외부 서비스 연동

### 노션(Notion) 가입 신청서
*   노션 데이터베이스의 '설문(Form)' 기능을 사용합니다.
*   공유 시 반드시 **'보기 링크 복사'**를 사용해야 학생들에게 노션 전체 화면이 아닌 설문지만 보여줄 수 있습니다.

### SNS 미리보기 (Open Graph)
*   카카오톡 등으로 링크 공유 시 예쁜 썸네일이 나오도록 `<head>`에 메타 태그를 추가했습니다.
    *   `og:title`: 사이트 제목
    *   `og:description`: 사이트 설명
    *   `og:image`: 썸네일 이미지 URL

## 5. 배포하기 (GitHub Pages)
1.  GitHub 저장소를 만들고 코드를 업로드합니다 (`git push`).
2.  저장소 **Settings > Pages** 메뉴로 이동합니다.
3.  **Branch**를 `main`으로 설정하고 **Save**를 누릅니다.
4.  잠시 후 생성된 주소(예: `https://ID.github.io/repo-name`)를 학생들에게 공유합니다.

---
*Created by Antigravity*
