# API 명세 - ERROR EVENT 대상별 설정 
화면의 [관리 > 룰 > EVENT룰 > ERROR EVENT > ERROR유형 > 대상별 설정] 기능을 API로 제어합니다. 화면으로 사용성을 충분히 이해한 후에 사용하시기 바랍니다. Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

#### Path 형식
`http(s)://<호스트>:<포트>/api-v2/manage/rule/event/error/<도메인아이디>/<ERROR유형>/individual-setting/<인스턴스아이디>`

#### 저장하기
- Method : PUT
- Content-Type: application/json
- Content : 설정값. true 또는 false
- 요청 예제 (7002 도메인 10001 인스턴스의 AGENT_STOP EVENT가 발생하지 않도록 설정하기)
    - `> curl --request PUT https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/individual-setting/10001 -H "Authorization: Bearer ABCD1234" -H "Content-Type: application/json" -d "false"`
- 응답 데이터: 없음

#### 조회하기
- Method : GET
- 요청 예제
    - `> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/individual-setting/10001 -H "Authorization: Bearer ABCD1234"`
- 응답: 설정 값이 있으면 true 또는 false, 없으면 404.

#### 제거하기
- Method : DELETE
- 요청 예제
    - `> curl --request DELETE https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/individual-setting/10001 -H "Authorization: Bearer ABCD1234"`
- 응답 데이터: 없음
