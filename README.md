# CoWorks Frontend

> 문서 작성부터 서명까지, 한 번에

CoWorks는 대학 내 종이 문서, 수기 서명, 이메일 중심의 행정 문서 처리 과정을 온라인으로 전환하기 위한 전자문서 처리 플랫폼입니다. 이 저장소는 CoWorks 서비스의 프론트엔드 영역으로, 사용자가 문서를 생성하고 작성한 뒤 검토와 전자서명까지 진행할 수 있는 화면과 상호작용을 담당합니다.

## 프로젝트 소개

CoWorks Frontend는 PDF 기반 행정 문서를 웹에서 작성할 수 있도록 지원합니다. 사용자는 템플릿을 선택해 문서를 생성하고, 문서 위에 배치된 입력 필드와 서명 필드를 통해 실제 양식에 작성하듯 문서를 처리할 수 있습니다.

문서는 작성, 검토, 서명, 완료 단계로 진행되며 사용자 역할에 따라 접근 가능한 화면과 작업이 달라집니다. 교직원은 템플릿과 폴더를 관리하고, 작성자와 검토자, 서명자는 각자 할당된 문서를 처리합니다.

<p align="center">
  <img src="https://github.com/user-attachments/assets/86a2e14f-dbf1-41e6-8225-006e52fc92e6" width="49%" />
  <img src="https://github.com/user-attachments/assets/c283e0fd-0475-462a-b72f-6dfc9577e843" width="49%" />
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/662d1051-5741-431f-9317-d41d5efc11cd" width="49%" />
  <img src="https://github.com/user-attachments/assets/2672aa39-2457-4811-9f58-dc1f21c7600b" width="49%" />
</p>

## 주요 기능

- **인증 및 사용자 흐름**
  - 로그인, 회원가입, 히즈넷 로그인 콜백 처리
  - 사용자 직분과 권한에 따른 초기 화면 분기

- **템플릿 관리**
  - PDF 템플릿 업로드
  - PDF 미리보기 및 다중 페이지 문서 표시
  - 입력 필드, 테이블 필드, 서명 필드 좌표 배치
  - 템플릿 수정, 삭제, 복제

- **문서 작성**
  - 템플릿 기반 문서 생성
  - PDF 위 좌표 기반 입력 필드 작성
  - 테이블 데이터 입력 및 일괄 입력
  - 작성 내용 자동 저장 및 수동 저장
  - 문서 미리보기와 PDF 다운로드

- **검토 및 서명**
  - 문서 상태에 따른 검토 화면과 서명 화면 제공
  - 검토 승인 및 반려 처리
  - 서명 패드 기반 전자서명 입력
  - 모든 서명 완료 시 완료 문서 화면 제공

- **문서 관리**
  - 문서 목록 조회, 검색, 상태별 필터링
  - 폴더 기반 문서 분류와 이동
  - 미분류 문서 관리
  - 문서별 상태와 담당자 정보 확인

- **대량 문서 생성**
  - Excel, CSV 파일 업로드
  - 업로드 데이터 미리보기
  - 유효 데이터 기반 문서 일괄 생성

- **알림**
  - 문서 할당, 검토 요청, 반려 등 주요 이벤트 표시
  - SSE 기반 실시간 알림 수신 구조

## 화면 구성

- `/login` - 로그인
- `/signup` - 회원가입
- `/tasks` - 사용자 할 일 대시보드
- `/review` - 검토 대기 문서 화면
- `/templates` - 템플릿 목록
- `/templates/pdf/upload` - PDF 템플릿 업로드
- `/templates/edit/:id` - 템플릿 수정
- `/documents` - 문서 목록
- `/documents/new` - 문서 생성
- `/documents/:id` - 문서 작성 및 편집
- `/documents/:id/review` - 문서 검토
- `/documents/:id/signer-assignment` - 서명자 지정
- `/documents/:id/sign` - 문서 서명
- `/documents/:id/completed` - 완료 문서 확인
- `/folders` - 폴더 기반 문서 관리

## 기술 스택

- **React 19**
- **TypeScript**
- **Vite**
- **React Router**
- **Zustand**
- **Axios**
- **Tailwind CSS**
- **html2canvas / jsPDF / JSZip**
- **xlsx**

## 프로젝트 구조

```text
src/
├── components/        # 공통 UI 컴포넌트, 모달, PDF 뷰어
├── config/            # API 주소 및 엔드포인트 설정
├── hooks/             # 문서 편집, PDF 캔버스, 템플릿 필드 관련 훅
├── pages/             # 라우트 단위 페이지
├── services/          # API 호출 서비스
├── stores/            # Zustand 전역 상태 관리
├── types/             # 문서, 템플릿, 사용자, 폴더 타입 정의
└── utils/             # 문서 미리보기, 출력, 다운로드 등 유틸리티
```

## 실행 방법

```bash
npm install
npm run dev
```

기본 개발 서버 주소는 `http://localhost:5173`입니다.

백엔드 API 주소는 기본적으로 `http://localhost:8080/api`를 사용합니다. 다른 주소를 사용할 경우 `.env`에 아래 값을 설정합니다.

```env
VITE_API_URL=http://localhost:8080/api
```

## 사용 가능한 스크립트

```bash
npm run dev      # 개발 서버 실행
npm run build    # 프로덕션 빌드
npm run lint     # ESLint 검사
npm run preview  # 빌드 결과 미리보기
```
