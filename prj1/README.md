# Project 1 · webOS Subscription Management Dashboard

구독자와 가전의 사용 현황을 조회하는 팀 프로젝트입니다.
구독자 검색·필터링, 사용자별 가전 조회, 기기 사용 현황과 차트, 상태별 Badge를 제공합니다.

## 팀과 담당

| 역할 | 팀원 |
|---|---|
| PM / TE | 최민석 |
| Backend | 하지훈 |
| Frontend | 이광수 |

백엔드는 구독자·가전·사용 현황 API, 조회 대상 검증과 404 응답을 제공합니다.

## 실행

Python 3.11 이상 환경에서 이 디렉터리를 작업 디렉터리로 사용합니다.

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```

Windows PowerShell에서는 가상환경 활성화 명령을 `.venv\Scripts\Activate.ps1`로 바꿉니다.
브라우저에서 `http://127.0.0.1:8000`으로 접속하고 API 문서는 `/docs`에서 확인합니다.

| API | 내용 |
|---|---|
| `GET /health` | 서버 상태 |
| `GET /api/subscribers` | 구독자 목록 |
| `GET /api/subscribers/{user_id}/devices` | 사용자별 가전 |
| `GET /api/devices/{device_id}/usage` | 기기 사용 현황 |

## 구조

- `app/main.py`: FastAPI 앱, 정적 파일·템플릿 설정.
- `app/api/`: 구독자와 가전 API.
- `app/data/dummy_data.py`: 과제용 더미 데이터.
- `app/templates/`, `app/static/`: 대시보드 UI.
- `requirement_1~3.md/.pdf`: 요구사항별 설명.
- `tests/`: 개발자 검증과 Playwright E2E 테스트.
- `tests/reports/`: 팀에서 작성한 로컬·CI·배포 검증 보고서.
- `.github/workflows/ci.yml`: 원본 저장소의 CI 설정 사본.

원본 workflow는 `prj1/.github/`에 보관되어 이 과목 저장소에서 자동 실행되지 않습니다.
원본의 CI와 배포 이력은 아래 팀 저장소에서 볼 수 있습니다.

## 테스트와 문서

```bash
python tests/req1_test_template.py
pip install -r tests/requirements-te.txt
python -m playwright install chromium
python tests/req1_e2e_test.py
python tests/req2_e2e_test.py
python tests/req3_e2e_test.py
```

E2E 테스트에는 실행 중인 서버가 필요합니다. 원본 팀 보고서의 107/107 결과는
해당 보고서에 명시된 환경·커밋의 결과입니다. 현재 사본의 추가 API 검사는 [검증 기록](../docs/verification.md)에 있습니다.

## 관련 자료

- 팀 저장소: [minseok209/sogang_lg](https://github.com/minseok209/sogang_lg)
- [요구사항 1](requirement_1.pdf) · [요구사항 2](requirement_2.pdf) · [요구사항 3](requirement_3.pdf)
- [최종 검증 보고서](tests/reports/final_test_report.md)
