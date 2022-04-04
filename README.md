## JENNIFER5 Open API

제니퍼 서버 5.5.3 이후 새로 추가하는 Open API에 대해 간이로 작성하고 있는 문서입니다. 기존 API는 다음 사이트를 참고하시기 바랍니다.

https://jennifersoft.github.io/jennifer-developer-guide


### 인증 하기

모든 API는 인증정보가 필요합니다. 요청 헤더에 다음과 같이 인증토큰을 넣어 요청합니다. 인증토큰은 제니퍼5 화면의 [관리 > 인증 토큰 관리] 메뉴에서 발급합니다.

`Authorization: Bearer <인증토큰>`

일부 조회API는 브라우저에서 간편하게 호출할 수 있습니다. 아래 예제를 참고합니다.

### 가장 간단한 API - 인증 테스트하기

다음 URL로 HTTP를 요청하면 인증이 잘 되는지 확인할 수 있습니다. Open API 사용이 처음이면, 먼저 이 API를 이용해서 인증까지 확인하는 것을 권장합니다.

- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/auth-test`
- 요청 예제 
    - curl : `> curl --request GET https://java.jennifersoft.com/api-v2/auth-test -H "Authorization: Bearer ABCD1234"`
    - 브라우저 : `https://java.jennifersoft.com/api-v2/auth-test?token=ABCD1234` (GET만 가능)
    - 인증토큰이 `ABCD1234`일 때의 예입니다. 브라우저 방식은 인증토큰이 브라우저 기록에 남을 수 있습니다. 주의하시기 바랍니다.

응답으로 `OK`를 확인하면 인증이 제대로 된 것입니다. 문제가 있으면 아래의 [공통 HTTP 응답 코드 설명](#공통-HTTP-응답-코드)과 메시지를 확인합니다.

### API 명세

- 관리
    - 인스턴스
        - [호스트네임과 프로세스ID로 인스턴스 찾기](spec/instance-list-by-process-id.md)
    - [JENNIFER DB 경로 조회](spec/db-path.md)
    - EVENT 룰
        - [EVENT 룰 설정 조회](spec/manage-rule-event.md)
        - [ERROR EVENT 룰 적용 On/Off 제어](spec/manage-rule-event-error-applied.md)
        - [ERROR EVENT 대상별 설정 제어](spec/manage-rule-event-error-individual.md)
    - [액티브 서비스 경과시간 범위 조회하기](spec/active-service-color-range-boundary.md)
- [수동 RDB Export](spec/manual-rdb-export.md)
- [소스코드(리소스) 변경이력 조회](spec/deploy.md)
- [로디드 클래스 조회하기](spec/loaded-class.md)
- [시스템 환경변수 조회하기](spec/environment-variable.md)
    
### 공통 HTTP 응답 코드

- 400 Bad Request : 잘못된 요청입니다. 응답의 메시지와 API명세를 확인합니다.
- 401 Unauthorized : 인증에 실패했습니다. 인증 토큰이 유효한지, 형식에 맞게 요청했는지 확인합니다.
- 404 Not Found : 요청한 데이터가 없습니다. 응답의 메시지를 확인합니다. 유효하지 않은 API를 요청했을 때도 발생합니다.
- 405 Method Not Allowed : 유효하지 않은 메소드(GET,POST 등)로 요청했습니다. API의 명세를 보고 지원하는 메소드인지 확인합니다.
- 500~599 : 서버에서 문제가 발생했습니다. 응답의 메시지와 뷰서버의 로그를 확인합니다. 그래도 문제를 해결할 수 없으면 지원을 요청합니다.
- 200 : 처리되었음을 의미합니다. API명세에서 특별한 언급이 없으면 이 응답으로 내려갑니다.
