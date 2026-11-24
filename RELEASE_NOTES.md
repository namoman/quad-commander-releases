## QuadCommander v0.2.3 🚀

### ⚡️ v0.2.3 주요 변경사항 및 신규 기능
- **Everything 초고속 라이브 검색 & 즉시 정렬 엔진**:
  - **Everything C-API 고속 연동**: `Everything_SetSort(EVERYTHING_SORT_NAME_ASCENDING)` 호출로 수백만 파일 검색 시 IPC 레벨에서 즉각 오름차순 정렬된 결과 반환 (추가 RAM 점유율 0MB, 0.01초 레이턴시)
  - **40ms 초저지연 디바운스 & 키보드 탐색**: 입력창 타이핑 즉시 검색 결과 갱신, 검색어 하이라이트 매칭, 방향키(↑/↓) 선택 및 Enter 즉시 열기, Esc 닫기 지원
  - **스마트 관련도 랭킹 점수화 (Relevance Scoring)**:
    - Rust `jwalk` On-Demand 병렬 엔진에서 완전 일치(Exact) > 접두사 일치(Prefix) > 부분 일치(Substring) 순위 및 폴더 우선, A-Z 정렬 적용
- **사용자 친화적 검색 엔진 설정 모달**:
  - 최초 `Ctrl+F` 실행 시 전문 용어 없는 쉬운 용어와 장단점 위주의 비교 안내 모달 표시
  - Everything 연동(0.01초/점유율 0%) vs 가벼운 실시간 검색(초경량/설치 불필요) vs 자체 기억 검색(자체 덤프) 중 선택 가능
  - **"다음부터 묻지 않음 (기본값으로 저장)"** 옵션 및 툴바 ⚙️ 버튼, 메뉴바(`도구 > 검색 엔진 설정...`)를 통한 언제든 재설정 지원
- **F1 도움말 내 심층 기술 아키텍처 명세 (`search_tech`)**:
  - NTFS `$MFT` 바이너리 덤프, USN Change Journal 실시간 동기화, Tokio `spawn_blocking` 비동기 스레드 풀 격리 메커니즘 등 엔지니어링 기술 스펙 문서화
- **Q-Dir 스타일 9가지 멀티 패널 레이아웃 & 커스터마이저**:
  - 1분할, 좌우/상하 2분할, 3단 변형, 4단 행/열 분할 등 원클릭 전환 및 커스텀 분할비 영구 저장/관리 지원
- **원격 UNC 서버 공유 폴더 열거 지원 (`NetShareEnum`)**:
  - Windows 네이티브 `NetShareEnum` API를 연동하여 `\\server` 접속 시 사용 가능한 공유 폴더 실시간 자동 탐색

### 🛡️ v0.2.2 보안/안정성 개선
- **보안 취약점 강화 (Security Hardening)**:
  - **DLL 하이재킹 차단**: Windows Everything IPC 로드 시 상대경로 DLL 로드 경로 제거 및 신뢰할 수 있는 시스템/설치 경로만 허용
  - **디렉터리 탈출(Path Traversal) 방지**: 파일/폴더 생성, 이름 변경, 일괄 이름 변경 시 `..`, `/`, `\` 탈출 검증 적용
  - **Zip Bomb 및 심볼릭 링크 위험 방어**: 단일 파일 4GB 압축 해제 제한 및 외부 경로 덮어쓰기 방어
  - **인젝션 방어**: 기본 앱 열기 및 Spotlight 검색 연동 시 CLI 플래그 인젝션(`--`) 방어
  - **CSP(Content Security Policy) 활성화**: Tauri 앱 내 스크립트 및 리소스 로드 보안 정책 적용

### 📦 플랫폼별 공식 설치 파일 (아래 첨부 파일에서 다운로드)
- **macOS 설치 디스크 이미지**: QuadCommander_v0.2.3.dmg
- **Windows 설치형 (권장)**: QuadCommander_Setup_v0.2.3.exe
- **Windows 포터블 (무설치)**: QuadCommander_Portable_v0.2.3.exe
- **Windows MSI 패키지**: QuadCommander_v0.2.3.msi

> 💡 **참고**: GitHub 시스템 정책상 하단 Assets 목록에 자동으로 표시되는 Source code (zip/tar.gz) 링크는 릴리스 소개 문서 압축본이며, 실제 프로그램 파일이 아닙니다. 상단에 첨부된 .dmg 또는 .exe 파일을 다운로드하여 실행해 주시기 바랍니다.
