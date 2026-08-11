## Q1
- 유형: 1
- 질문: create_app 함수는 어떤 작업을 수행하나요?
- 정답 위치:
  - app/__init__.py 19~63줄
- 한 줄 요약: Flask 앱 생성, 설정 로드, ProxyFix 조건 적용, extensions/modules 초기화를 수행한다
- 비고: 단일 함수 본문만 보면 답 가능

## Q2
- 유형: 1
- 질문: app/extensions의 init_app 함수는 무엇을 하나요?
- 정답 위치:
  - app/extensions/__init__.py 37~52줄
- 한 줄 요약: 등록된 확장 객체를 순회하며 extension.init_app(app)을 호출한다
- 비고: 확장 목록과 루프 호출 확인 필요

## Q3
- 유형: 1
- 질문: serve_swaggerui_assets 함수는 어떤 역할을 하나요?
- 정답 위치:
  - app/extensions/api/__init__.py 41~53줄
- 한 줄 요약: 경고를 남긴 뒤 ../static/에서 Swagger UI 자산을 서빙한다
- 비고: debug 조건 분기 포함

## Q4
- 유형: 1
- 질문: abort 함수는 기본 메시지를 어떻게 결정하나요?
- 정답 위치:
  - app/extensions/api/http_exceptions.py 27~39줄
- 한 줄 요약: 커스텀 메시지가 없으면 코드별 기본 메시지 또는 HTTPStatus description을 사용한다
- 비고: 분기 로직 확인 필요

## Q5
- 유형: 1
- 질문: set_sqlite_pragma 함수는 무엇을 설정하나요?
- 정답 위치:
  - app/extensions/flask_sqlalchemy/__init__.py 13~26줄
- 한 줄 요약: SQLite 연결에서 PRAGMA foreign_keys=ON을 실행한다
- 비고: sqlite3.Connection 타입일 때만 동작

## Q6
- 유형: 1
- 질문: load_user_from_request 함수는 사용자 정보를 어떤 순서로 조회하나요?
- 정답 위치:
  - app/modules/auth/__init__.py 10~21줄
- 한 줄 요약: request.oauth를 우선 사용하고, 없으면 oauth2.verify_request 결과를 사용한다
- 비고: 인증 정보 소스가 2단계로 나뉜다

## Q7
- 유형: 1
- 질문: access_token 함수는 토큰 처리에서 어떤 용도로 정의되어 있나요?
- 정답 위치:
  - app/modules/auth/views.py 27~38줄
- 한 줄 요약: 토큰 교환/갱신 엔드포인트이며 현재 None을 반환한다
- 비고: 데코레이터와 docstring으로 목적 확인

## Q8
- 유형: 1
- 질문: revoke_token 함수는 무엇을 위한 엔드포인트인가요?
- 정답 위치:
  - app/modules/auth/views.py 40~46줄
- 한 줄 요약: 사용자가 액세스 토큰을 폐기하도록 하는 엔드포인트다
- 비고: 구현 본문은 pass, 목적은 docstring에 명시

## Q9
- 유형: 1
- 질문: authorize 함수는 GET 요청과 POST 요청을 각각 어떻게 처리하나요?
- 정답 위치:
  - app/modules/auth/views.py 48~73줄
- 한 줄 요약: GET은 authorize 화면 렌더링, POST는 confirm 값 판정으로 승인 여부를 반환한다
- 비고: 인증 실패 시 401 처리도 포함

## Q10
- 유형: 1
- 질문: _get_is_static_role_property 함수는 어떤 작업을 하나요?
- 정답 위치:
  - app/modules/users/models.py 13~37줄
- 한 줄 요약: static role 비트마스크를 제어하는 getter/setter property를 생성한다
- 비고: has/set/unset_static_role 호출 구조 확인 필요

## Q11
- 유형: 1
- 질문: UserSignupForm 클래스는 어떤 정보를 제공하나요?
- 정답 위치:
  - app/modules/users/resources.py 62~80줄
- 한 줄 요약: 회원가입 폼용 recaptcha_server_key를 반환하는 GET 리소스다
- 비고: 현재 반환값은 TODO 문자열

## Q12
- 유형: 1
- 질문: TeamMembers 클래스는 팀 멤버에 대해 어떤 작업을 담당하나요?
- 정답 위치:
  - app/modules/teams/resources.py 135~183줄
- 한 줄 요약: 팀 멤버 목록 조회(GET)와 멤버 추가(POST)를 처리한다
- 비고: 추가 시 user_id 존재 여부 검증 포함

## Q13
- 유형: 1
- 질문: install_swagger_ui 함수는 Swagger UI 설치를 어떤 절차로 수행하나요?
- 정답 위치:
  - tasks/app/dependencies.py 31~94줄
- 한 줄 요약: 경로 준비, 필요 시 정리, zip 다운로드, dist만 추출해 설치한다
- 비고: force 옵션 동작이 포함됨

## Q14
- 유형: 1
- 질문: export 함수는 Swagger 스펙을 어떻게 내보내나요?
- 정답 위치:
  - tasks/app/swagger.py 16~29줄
- 한 줄 요약: 테스트 앱으로 swagger 엔드포인트를 호출해 결과 바이트를 반환한다
- 비고: quiet=false면 표준출력에도 출력

## Q15
- 유형: 1
- 질문: create_oauth2_client 함수는 OAuth2 클라이언트를 생성할 때 어떤 검증과 기본값 처리를 하나요?
- 정답 위치:
  - tasks/app/users.py 45~76줄
- 한 줄 요약: 사용자 존재를 검증하고, 기본 스코프를 계산해 OAuth2Client를 DB에 저장한다
- 비고: default_scopes가 없을 때만 authorizations에서 스코프를 읽는다

## Q16
- 유형: 2
- 질문: API v1 요청 처리는 프로젝트에서 어디서 시작되어 앱에 등록되나요?
- 정답 위치:
  - app/__init__.py 58~62줄
  - app/modules/api/__init__.py 12~16줄
- 한 줄 요약: create_app에서 modules.init_app을 호출하고, modules.api가 /api/v1 블루프린트를 등록한다
- 비고: 앱 엔트리와 API 등록 모듈을 함께 봐야 한다

## Q17
- 유형: 2
- 질문: 사용자 목록 조회 요청은 어디서 시작되어 실제 조회로 이어지나요?
- 정답 위치:
  - app/modules/users/__init__.py 10~21줄
  - app/modules/users/resources.py 24~42줄
- 한 줄 요약: users 네임스페이스 등록 후 Users.get에서 User.query offset/limit 조회가 실행된다
- 비고: 모듈 등록 파일과 리소스 파일이 분리돼 있다

## Q18
- 유형: 2
- 질문: 팀 목록 조회 기능은 어디서 시작되나요?
- 정답 위치:
  - app/modules/teams/__init__.py 10~21줄
  - app/modules/teams/resources.py 28~43줄
- 한 줄 요약: teams 네임스페이스 등록 후 Teams.get이 Team.query를 반환한다
- 비고: 등록 지점과 실행 지점을 함께 봐야 한다

## Q19
- 유형: 2
- 질문: 토큰 발급/갱신 요청은 어디서 시작되어 사용자 검증으로 이어지나요?
- 정답 위치:
  - app/modules/auth/__init__.py 39~40줄
  - app/modules/auth/views.py 25~38줄
  - app/extensions/auth/oauth2.py 50~54줄
- 한 줄 요약: auth_blueprint의 token 엔드포인트로 시작하고 validator _usergetter가 User.find_with_password를 호출한다
- 비고: 블루프린트 등록, 라우트, validator를 모두 연결해야 흐름이 보인다

## Q20
- 유형: 2
- 질문: OAuth2 클라이언트 생성 API 요청은 어디서 시작되어 저장되나요?
- 정답 위치:
  - app/modules/auth/__init__.py 40줄
  - app/modules/auth/resources.py 25~72줄
- 한 줄 요약: auth 네임스페이스의 OAuth2Clients.post가 새 OAuth2Client를 생성해 저장한다
- 비고: 리소스 등록과 post 처리 코드를 함께 확인

## Q21
- 유형: 2
- 질문: Swagger UI 정적 파일 요청은 어디서 시작되어 파일 서빙으로 연결되나요?
- 정답 위치:
  - app/extensions/api/__init__.py 54~62줄
  - app/extensions/api/__init__.py 41~51줄
- 한 줄 요약: /swaggerui 라우트가 serve_swaggerui_assets로 연결되고 send_from_directory로 응답한다
- 비고: 같은 파일 안에서 라우트 정의와 실제 처리 함수가 분리돼 있다

## Q22
- 유형: 2
- 질문: 애플리케이션 시작 시 확장 초기화는 어디서 시작되나요?
- 정답 위치:
  - app/__init__.py 58~59줄
  - app/extensions/__init__.py 37~50줄
- 한 줄 요약: create_app이 extensions.init_app을 호출하고, 확장 루프가 각 init_app을 실행한다
- 비고: 단일 파일만 보면 전체 초기화 체인이 보이지 않는다

## Q23
- 유형: 2
- 질문: 모듈 자동 로딩은 어디서 시작되며 어떤 기준으로 모듈을 불러오나요?
- 정답 위치:
  - app/__init__.py 61~62줄
  - app/modules/__init__.py 13~17줄
- 한 줄 요약: create_app에서 modules.init_app을 부르고 ENABLED_MODULES 목록으로 동적 import한다
- 비고: 설정 기반 동적 로딩 흐름을 확인하는 문제

## Q24
- 유형: 2
- 질문: SQLite 외래 키 제약 활성화는 어디서 시작되나요?
- 정답 위치:
  - app/extensions/flask_sqlalchemy/__init__.py 64~70줄
  - app/extensions/flask_sqlalchemy/__init__.py 13~26줄
- 한 줄 요약: SQLAlchemy.init_app에서 connect 이벤트에 set_sqlite_pragma를 걸고 pragma를 실행한다
- 비고: 이벤트 등록과 실제 콜백 함수를 함께 봐야 한다

## Q25
- 유형: 2
- 질문: 요청에서 현재 사용자(current_user) 로딩은 어디서 시작되나요?
- 정답 위치:
  - app/modules/auth/__init__.py 29줄
  - app/modules/auth/__init__.py 10~21줄
- 한 줄 요약: request_loader 등록이 시작점이고 load_user_from_request가 oauth 정보로 사용자 객체를 만든다
- 비고: request_loader 등록 라인과 로더 함수 본문이 핵심

## Q26
- 유형: 2
- 질문: users:read 같은 OAuth 스코프 검증은 어디서 시작되어 실제 인증 데코레이터로 연결되나요?
- 정답 위치:
  - app/modules/users/resources.py 30줄
  - app/extensions/api/namespace.py 81~156줄
  - app/extensions/api/api.py 31~49줄
- 한 줄 요약: 리소스의 login_required 선언이 Namespace.login_required를 거쳐 require_oauth로 연결되고 add_namespace에서 보안 설정이 치환된다
- 비고: 데코레이터 선언과 구현, 네임스페이스 등록까지 다 봐야 완전한 답이 된다

## Q27
- 유형: 2
- 질문: Invoke로 개발 서버를 실행할 때 시작 지점은 어디이며 앱 실행은 어디에서 일어나나요?
- 정답 위치:
  - tasks/app/run.py 22~43줄
  - tasks/app/run.py 83줄
- 한 줄 요약: run 태스크가 create_app을 호출하고 마지막에 app.run을 실행한다
- 비고: 의존성 설치 호출도 같은 흐름에 포함된다

## Q28
- 유형: 2
- 질문: 개발용 쉘 진입(enter) 흐름은 어디서 시작되어 앱 컨텍스트를 여나요?
- 정답 위치:
  - tasks/app/env.py 13~22줄
  - tasks/app/env.py 35~41줄
- 한 줄 요약: enter 태스크가 선택적으로 설치/마이그레이션을 수행한 뒤 create_app과 app_context로 쉘을 연다
- 비고: prepare 단계와 shell 진입 단계가 떨어져 있다

## Q29
- 유형: 2
- 질문: Swagger 클라이언트 코드 생성은 어디서 시작되어 스펙 파일을 준비하나요?
- 정답 위치:
  - tasks/app/swagger.py 32~49줄
  - tasks/app/swagger.py 16~25줄
- 한 줄 요약: codegen이 export를 호출해 swagger json을 만들고 clients 폴더에 저장한다
- 비고: 생성 태스크와 스펙 추출 태스크를 함께 봐야 한다

## Q30
- 유형: 2
- 질문: 팀 멤버 추가 요청은 어디서 시작되어 사용자 검증 후 멤버 생성으로 이어지나요?
- 정답 위치:
  - app/modules/teams/resources.py 128~178줄
  - app/extensions/api/http_exceptions.py 27~39줄
- 한 줄 요약: TeamMembers.post가 user_id 존재를 확인하고 없으면 abort, 있으면 TeamMember를 생성해 저장한다
- 비고: 성공 경로와 오류 경로가 분기된다

## Q31
- 유형: 3
- 질문: 이 프로젝트는 한마디로 어떤 서비스를 구현한 예제인가요?
- 정답 위치:
  - README.md 8~36줄
- 한 줄 요약: OpenAPI 문서화, OAuth2 인증, 권한/패치/테스트를 포함한 RESTful API 서버 예제다
- 비고: 프로젝트 목적과 목표 기능은 README 서두에 요약돼 있다

## Q32
- 유형: 3
- 질문: 루트 기준으로 핵심 폴더들은 어떻게 나뉘어 있나요?
- 정답 위치:
  - README.md 129~145줄
- 한 줄 요약: app, flask_restplus_patched, migrations, tasks, tests, docs, deploy로 역할이 분리돼 있다
- 비고: 처음 구조 파악 시 가장 먼저 보는 섹션

## Q33
- 유형: 3
- 질문: 코드를 처음 읽을 때 어디서 시작하라고 문서가 안내하나요?
- 정답 위치:
  - README.md 234~254줄
- 한 줄 요약: invoke app.run에서 시작해 create_app, extensions.init_app, modules.init_app 순으로 따라가라고 안내한다
- 비고: 입문자용 실행/코드 탐색 동선을 제공한다

## Q34
- 유형: 3
- 질문: 새 API 기능(엔드포인트)을 추가하려면 어느 폴더와 파일들을 먼저 보면 되나요?
- 정답 위치:
  - README.md 206~223줄
  - config.py 48~54줄
- 한 줄 요약: 엔드포인트는 app/modules에 구현하고 모듈은 ENABLED_MODULES와 init_app 등록 규칙을 따른다
- 비고: 문서 규칙과 실제 설정값을 함께 확인해야 한다

## Q35
- 유형: 3
- 질문: 소스에서 서버를 실행하려면 최소 어떤 설치와 명령이 필요하다고 문서에 나오나요?
- 정답 위치:
  - README.md 344~359줄
  - tasks/requirements.txt 1줄
- 한 줄 요약: tasks requirements 설치 후 invoke app.run으로 실행한다
- 비고: invoke 의존성이 핵심 전제다

## Q36
- 유형: 3
- 질문: 의존성 파일은 어떤 계층으로 나뉘어 있나요?
- 정답 위치:
  - requirements.txt 1~2줄
  - README.md 200줄
  - tests/requirements.txt 1~3줄
- 한 줄 요약: 루트 requirements가 app/tasks를 include하고 테스트 의존성은 tests/requirements로 분리된다
- 비고: 설치 범위에 따라 파일을 구분해서 봐야 한다

## Q37
- 유형: 3
- 질문: 배포 예시는 프로젝트의 어디에 정리돼 있으며 어떤 스택을 제공하나요?
- 정답 위치:
  - README.md 363~365줄
  - deploy/README.md 7~11줄
- 한 줄 요약: deploy 폴더에 배포 전략이 있고 stack1(nginx reverse proxy), stack2(uWSGI) 예시가 있다
- 비고: 실행 가이드와 배포 문서를 함께 읽어야 한다

## Q38
- 유형: 3
- 질문: 기본 인증 관련 API 설정(OAuth2 token URL/클라이언트)은 어디서 정의되나요?
- 정답 위치:
  - config.py 32~37줄
  - config.py 60줄
- 한 줄 요약: AUTHORIZATIONS의 oauth2_password tokenUrl과 Swagger OAuth client_id가 config.py에 정의돼 있다
- 비고: 인증 설정 확인 시 먼저 보는 설정 블록

## Q39
- 유형: 4
- 질문: 앱 시작 시 local 설정 파일을 찾지 못해 종료되면 어디를 봐야 하나요?
- 정답 위치:
  - app/__init__.py 44~52줄
- 한 줄 요약: create_app에서 local ImportError를 잡아 에러 로그를 남기고 sys.exit(1)로 종료한다
- 비고: local_config.py 누락 여부를 가장 먼저 확인

## Q40
- 유형: 4
- 질문: "SQLALCHEMY_DATABASE_URI must be configured!" 에러가 나면 어디서 발생하나요?
- 정답 위치:
  - app/extensions/flask_sqlalchemy/__init__.py 68~69줄
- 한 줄 요약: SQLAlchemy.init_app의 assert database_uri에서 발생한다
- 비고: config의 DB URI 설정값 확인 필요

## Q41
- 유형: 4
- 질문: "SECRET_KEY must be configured!" 에러는 어디서 확인해야 하나요?
- 정답 위치:
  - app/extensions/auth/oauth2.py 119~122줄
- 한 줄 요약: OAuth2Provider.init_app에서 SECRET_KEY assert가 실패한다
- 비고: 인증 확장 초기화 전 설정값이 필요

## Q42
- 유형: 4
- 질문: 로그인 없이 /auth/oauth2/authorize에 접근해 401이 날 때 어디를 봐야 하나요?
- 정답 위치:
  - app/modules/auth/views.py 60~61줄
  - app/extensions/api/http_exceptions.py 27~37줄
- 한 줄 요약: authorize가 비인증 사용자를 api.abort(401) 처리하고 abort 함수가 최종 응답 포맷을 만든다
- 비고: 발생 지점과 공통 에러 응답 생성 지점을 함께 확인

## Q43
- 유형: 4
- 질문: 팀 멤버 추가에서 "User with id ... does not exist" 404가 나면 어디서 발생하나요?
- 정답 위치:
  - app/modules/teams/resources.py 171~175줄
  - app/extensions/api/http_exceptions.py 37줄
- 한 줄 요약: TeamMembers.post에서 사용자 조회 실패 시 abort(404)를 호출한다
- 비고: user_id 인자 확인이 핵심

## Q44
- 유형: 4
- 질문: OAuth 토큰/그랜트 저장 중 DB 무결성 에러가 나면 어디서 처리하나요?
- 정답 위치:
  - app/extensions/auth/oauth2.py 74~76줄
  - app/extensions/auth/oauth2.py 95~97줄
- 한 줄 요약: _tokensetter와 _grantsetter가 IntegrityError를 잡아 로그 남기고 None 반환한다
- 비고: 토큰/그랜트 저장 경로를 분리해서 확인해야 한다

## Q45
- 유형: 4
- 질문: Invoke로 OAuth2 클라이언트 생성 시 "User with username ... does not exist"가 뜨면 어디를 봐야 하나요?
- 정답 위치:
  - tasks/app/users.py 58~60줄
- 한 줄 요약: create_oauth2_client에서 사용자 미존재 시 Exception을 즉시 발생시킨다
- 비고: 입력한 username 값 검증 필요

## Q46
- 유형: 4
- 질문: ID로 조회하는 API에서 "not found" 404가 날 때 공통으로 어디를 확인해야 하나요?
- 정답 위치:
  - app/extensions/api/namespace.py 30~62줄
  - app/modules/users/resources.py 82~85줄
  - app/modules/teams/resources.py 66~70줄
- 한 줄 요약: resolve_object_by_model이 내부적으로 get_or_404를 호출하고, users/teams 리소스가 이 경로를 사용한다
- 비고: 공통 데코레이터 구현과 각 리소스 선언을 같이 봐야 원인 파악이 빠르다

## Q47
- 유형: 5
- 질문: 결제 승인/환불 절차는 어떤 엔드포인트와 서비스 계층에서 처리되나요?
- 정답 위치:
  - README.md 168~208줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: payment, checkout, invoice, billing, refund 으로 검색했으나 결과 없음

## Q48
- 유형: 5
- 질문: 파일 업로드 API는 어느 경로에서 multipart 파일을 받아 저장하나요?
- 정답 위치:
  - README.md 206~209줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에서 확인할 수 없습니다.
- 비고: upload, multipart, file storage, s3, bucket 으로 검색했으나 결과 없음

## Q49
- 유형: 5
- 질문: GraphQL API 스키마와 resolver는 어디에 정의돼 있나요?
- 정답 위치:
  - README.md 28~31줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: graphql, schema, resolver 으로 검색했으나 결과 없음

## Q50
- 유형: 5
- 질문: 실시간 알림을 위한 WebSocket 채널은 어디서 열고 인증하나요?
- 정답 위치:
  - README.md 8~12줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에서 확인할 수 없습니다.
- 비고: websocket, socket.io, ws://, wss:// 으로 검색했으나 결과 없음

## Q51
- 유형: 5
- 질문: Redis 캐시 레이어는 어떤 키 전략과 만료 정책으로 동작하나요?
- 정답 위치:
  - app/requirements.txt 1~26줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: redis, cache, ttl 으로 검색했으나 결과 없음

## Q52
- 유형: 5
- 질문: 비동기 작업 큐(Celery/RabbitMQ) 실패 재시도 정책은 어디에 정의돼 있나요?
- 정답 위치:
  - README.md 273~299줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에서 확인할 수 없습니다.
- 비고: celery, rabbitmq, retry, queue 으로 검색했으나 결과 없음

## Q53
- 유형: 5
- 질문: Kubernetes 배포 매니페스트(Helm chart/Ingress)는 어디에 있나요?
- 정답 위치:
  - deploy/README.md 9~11줄
  - deploy/**/*.md (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: kubernetes, k8s, helm, ingress 으로 검색했으나 결과 없음

## Q54
- 유형: 5
- 질문: 소셜 로그인(구글/깃허브 OAuth) 설정은 어느 파일에서 관리하나요?
- 정답 위치:
  - config.py 32~37줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에서 확인할 수 없습니다.
- 비고: google, github, social login, oauth2_implicit 으로 검색했으나 결과 없음

## Q55
- 유형: 5
- 질문: SMS 기반 OTP 인증 절차는 어디에 구현돼 있나요?
- 정답 위치:
  - README.md 389~392줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: sms, otp, totp, 2fa 으로 검색했으나 결과 없음

## Q56
- 유형: 5
- 질문: 이메일 발송(회원가입 확인/알림) 기능은 어느 모듈에 있나요?
- 정답 위치:
  - README.md 178~193줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에서 확인할 수 없습니다.
- 비고: email, smtp, mail, notification 으로 검색했으나 결과 없음

## Q57
- 유형: 5
- 질문: 감사 로그(audit log) 저장 스키마와 보관 기간 정책은 어디에 정의돼 있나요?
- 정답 위치:
  - README.md 129~145줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: audit, retention, log storage, compliance 으로 검색했으나 결과 없음

## Q58
- 유형: 5
- 질문: 외부 알림(Slack/Webhook) 연동 실패 재전송 로직은 어디에 있나요?
- 정답 위치:
  - tasks/requirements.txt 1~4줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에서 확인할 수 없습니다.
- 비고: slack, webhook, retry, notification 으로 검색했으나 결과 없음

## Q59
- 유형: 5
- 질문: API 버전 롤백 전략(v2->v1 호환 정책)은 어디에 정의돼 있나요?
- 정답 위치:
  - app/modules/api/__init__.py 14~16줄
  - README.md (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: v2, rollback, backward compatibility, deprecation 으로 검색했으나 결과 없음

## Q60
- 유형: 5
- 질문: 다국어(i18n) 메시지 번역 파일과 locale 선택 로직은 어디에 있나요?
- 정답 위치:
  - README.md 168~209줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에서 확인할 수 없습니다.
- 비고: i18n, l10n, locale, gettext 으로 검색했으나 결과 없음

## Q61
- 유형: 5
- 질문: 관리자 대시보드 프런트엔드(React/Vue) 소스는 어느 폴더에 있나요?
- 정답 위치:
  - README.md 129~145줄
  - app/**/*.py (키워드 검색 결과 없음)
- 한 줄 요약: 문서에 해당 내용이 없습니다.
- 비고: react, vue, frontend, dashboard 으로 검색했으나 결과 없음
