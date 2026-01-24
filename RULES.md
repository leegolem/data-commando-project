# 프로젝트 규칙

## 작업 시작 루틴
- 작업 시작 시 무조건 git pull
원격(GitHub)에 올라온 최신 작업물을 로컬로 동기화한다
<br>

## 라이브러리 추가시 (uv)
라이브러리 추가하면:
1. 추가한 사람이 uv add 패키지명 실행
2. 변경된 pyproject.toml, uv.lock 둘 다 커밋/푸시
<br>

다른 팀원:
1. git pull
2. uv sync
<br>

## 작업물 받기 (조원이 해야 할 일)
기본: git pull
- 아래 중 하나라도 해당하면 추가로 실행:
    - pyproject.toml 변경됨
    - uv.lock 변경됨
    - import 에러 발생 / 라이브러리가 없다는 에러가 뜸
- 이 경우:
    - uv sync

## 커밋 규칙 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
- 개인 작업물 커밋 시 git add . 사용 금지
반드시 아래처럼 본인 폴더만 add
```powershell
git add notebooks/본인폴더/
```

- 공용 파일 수정 시
반드시 커밋으로 무엇을 언제 어떻게 수정했는지 표시하기
수정한 파일만 명시적으로 add
<br>
<br>


# 프로젝트 파일 구성
DATA-COMMANDO-PROJECT/
├─ main/
│  └─ h&m_dataset/        # 공동 데이터 (원본, 수정 금지)
│
├─ notebooks/
│  ├─ member1/            # 개인 작업물
│  ├─ member2/
│  ├─ member3/
│  └─ member4/
│
├─ pyproject.toml
├─ uv.lock
├─ README.md
└─ .gitignore

## 폴더 역할 정리

- main/
    - 팀 공용 데이터
    - 원본 데이터만 보관
    - 개인 수정/가공 결과 저장 금지

- notebooks/member1~4/
    - 각자 전처리 / 시각화 / 실험용 노트북 작성 공간
    - 개인 작업물은 본인 폴더에만 커밋