새로 추가하는 Open API에 대해서 간이로 작성하고 있는 문서입니다. 기존 API는 다음 사이트를 참고하시기 바랍니다.

https://jennifersoft.github.io/jennifer-developer-guide


### 인증 하기

모든 API는 인증정보가 필요합니다. 요청 헤더에 다음과 같이 인증토큰을 넣어 요청합니다. 토큰은 제니퍼5 화면의 [관리 > 인증 토큰 관리] 메뉴에서 발급합니다.

`Authorization: Bearer <인증토큰>`

### API 명세 - ERROR EVENT 룰 적용 ON/OFF 여부
- Path 형식: `http(s)://<호스트>:<포트>/api-v2/manage/rule/event/error/<도메인아이디>/<ERROR유형>/applied`
- 조회
    - Method : GET
    - 요청 예제
        - `> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/applied -H "Authorization: Bearer ABCD1234"`
    - 응답: true 또는 false

### API 명세 - ERROR EVENT 대상별 설정
화면의 [관리 > 룰 > EVENT룰 > ERROR EVENT > ERROR유형 > 대상별 설정] 기능을 API로 제어합니다. 화면으로 사용성을 충분히 이해한 후에 사용하시기 바랍니다.
- Path 형식: `http(s)://<호스트>:<포트>/api-v2/manage/rule/event/error/<도메인아이디>/<ERROR유형>/individual-setting/<인스턴스아이디>`
- 개별 설정 값 저장
    - Method : PUT
    - Content-Type: application/json
    - Content : 설정값. true 또는 false
    - 요청 예제 (7002 도메인 10001 인스턴스의 AGENT_STOP EVENT가 발생하지 않도록 설정하기)
        - `> curl --request PUT https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/individual-setting/10001 -H "Authorization: Bearer ABCD1234" -H "Content-Type: application/json" -d "false"`
    - 응답 데이터: 없음
- 개별 설정 값 조회
    - Method : GET
    - 요청 예제
        - `> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/individual-setting/10001 -H "Authorization: Bearer ABCD1234"`
    - 응답: 설정 값이 있으면 true 또는 false, 없으면 404.
- 개별 설정 값 제거
    - Method : DELETE
    - 요청 예제
        - `> curl --request DELETE https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/individual-setting/10001 -H "Authorization: Bearer ABCD1234"`
    - 응답 데이터: 없음
    
### 공통 HTTP 응답 코드

- 400 Bad Request : 잘못된 요청입니다. 응답의 메시지와 API명세를 확인합니다.
- 401 Unauthorized : 인증에 실패했습니다. 인증 토큰이 유효한지, 형식에 맞게 요청했는지 확인합니다.
- 404 Not Found : 요청한 데이터가 없습니다. 응답의 메시지를 확인합니다. 유효하지 않은 API를 요청했을 때도 발생합니다.
- 405 Method Not Allowed : 유효하지 않은 메소드로 요청했습니다 (예: POST). API의 명세를 보고 지원하는 메소드인지 확인합니다.
- 500~599 : 서버에서 문제가 발생했습니다. 응답의 메시지와 뷰서버의 로그를 확인합니다. 문제 해결이 안 될 경우 지원을 요청합니다.
- 200 : 처리됨을 의미합니다. API명세 상 특별한 언급이 없으면 이 응답으로 내려갑니다.


