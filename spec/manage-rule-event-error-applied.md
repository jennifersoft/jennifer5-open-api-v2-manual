## API 명세 - ERROR EVENT 룰 적용 On/Off 제어 (5.5.3.3 이상)

화면의 [관리 > 룰 > EVENT룰 > ERROR EVENT > ERROR유형 > 룰 적용] On/Off여부를 API로 제어합니다.

우선 기본적인 API 사용법을 [README](/README.md)를 참고하여 숙지합니다.

### 조회하기
- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manage/rule/event/error/<도메인아이디>/<ERROR유형>/applied`
- 요청 예제 (7002 도메인의 AGENT_STOP ERROR EVENT의 룰 적용 여부 조회하기)
    - `> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/applied -H "Authorization: Bearer ABCD1234"`
- 응답: `true` 또는 `false`

### 저장하기
- Method : PUT
- Content-Type: application/json
- Content : 설정값. true 또는 false
- 요청 예제 (Off로 변경하기)
  - `> curl --request PUT https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002/AGENT_STOP/applied -H "Authorization: Bearer ABCD1234" -H "Content-Type: application/json" -d "false"`



