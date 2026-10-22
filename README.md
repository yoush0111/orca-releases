# orca-releases

[Orca](https://github.com/stablyai/orca) 포크의 내부 배포용 설치본 저장소입니다.
**바이너리만** 올라오며, 소스는 공개하지 않습니다.

최신 설치본: **[Releases 최신 버전](https://github.com/yoush0111/orca-releases/releases/latest)**

---

## 설치

### Windows

1. 최신 릴리즈에서 `orca-windows-setup.exe`를 받아 실행합니다.
2. 미서명 빌드라 SmartScreen 경고가 뜹니다 → **추가 정보 → 실행**.
3. 이후 버전은 **자동 업데이트**됩니다. 다시 받을 필요 없습니다.

> **`1.0.6-personal` 이전 버전을 쓰고 있다면 한 번만 수동으로 재설치해야 합니다.**
> 그 이전 빌드는 업데이트 피드가 upstream(`stablyai/orca`)을 가리켜서 이 저장소의 릴리즈를 보지 못합니다.
> 한 번 재설치하면 그다음부터는 자동 업데이트가 정상 동작합니다.

### macOS

**현재 배포하지 않습니다.** 지금까지의 릴리즈는 모두 Windows 설치본뿐입니다.

electron-builder는 macOS 타깃을 크로스 빌드할 수 없어 별도의 Mac 빌드 머신이 필요합니다.
필요해지면 같은 태그에 `.dmg`를 함께 올릴 예정입니다.

---

## upstream과 다른 점

업스트림 Orca에 **Redmine 연동**을 얹은 빌드입니다. 그 외 동작은 upstream과 같습니다.

### Redmine을 작업 소스로 사용

GitHub · GitLab · Jira · Linear에 이어 **Redmine이 다섯 번째 작업 소스**로 추가됩니다.
`Settings → Redmine`에서 Redmine 주소와 REST API 키로 연결하면, Tasks 탭에서 일감을 조회할 수 있습니다.

- API 키는 Redmine의 **내 계정 → API 액세스 키**에서 확인합니다.
  (Redmine 관리 설정에서 REST API가 활성화돼 있어야 합니다.)
- 목록에서 내 담당 / 프로젝트 / 상태로 필터링할 수 있습니다.
- 일감 행에서 바로 워크스페이스를 만들 수 있고, 브랜치명은 `feature/<일감번호>-<제목-슬러그>`로 자동 생성됩니다.

### 프로젝트별 repo 매핑

`Settings → Redmine → Project repositories`에서 Redmine 프로젝트마다 작업할 repo를 지정해 두면,
일감의 **→** 버튼이 그 repo로 워크스페이스 컴포저를 엽니다. 서브프로젝트는 부모 설정을 물려받습니다.
지정한 repo는 일감 목록의 프로젝트 열에도 표시됩니다.

### 일감 링크를 Orca 안에서 열기

Redmine 일감 링크는 기본적으로 **플로팅 워크스페이스의 브라우저 탭**으로 열립니다.

| 동작 | 결과 |
|---|---|
| 클릭 (기본) | 플로팅 워크스페이스 브라우저 탭 |
| 설정에서 끈 뒤 클릭 | 활성 워크트리 탭 |
| `Shift` + `Ctrl` + 클릭 | 시스템 기본 브라우저 |

플로팅 워크스페이스에서는 타이틀바 토글로 **Redmine 작업 뷰**를 열 수 있고, 토글 상태는 재시작 후에도 유지됩니다.

---

## 패치 노트

패치 노트는 각 릴리즈의 노트로 옮겼습니다.

- `1.0.34-personal` 이후: [yoush0111/orca 릴리즈](https://github.com/yoush0111/orca/releases)
- `1.0.33-personal` 이전: [이 저장소의 릴리즈](https://github.com/yoush0111/orca-releases/releases)

---

## 버전 표기

`1.0.N-personal`은 이 배포본의 자체 번호이며, upstream Orca의 버전과는 무관하게 증가합니다.
각 릴리즈가 어떤 소스로 빌드됐는지는 소스 저장소의 동일한 이름의 태그로 추적합니다.
