(작성중)

### API 명세 - ERROR EVENT 룰 설정 조회 (5.5.3.5 이상)

화면의 [관리 > 룰> EVENT룰] 화면의 설정정보를 API로 조회합니다.

우선 기본적인 API 사용법은 [README](/README.md)를 참고하여 숙지합니다.

#### Path 형식
`http(s)://<호스트>:<포트>/api-v2/manage/rule/event/error/<도메인아이디>`
#### 요청 예제
`> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002 -H "Authorization: Bearer ABCD1234"`

#### 응답 예제
```json
[
  {
    "errorType":"SERVICE_EXCEPTION",
    "applied":true,
    "level":"WARNING",
    "iconRecoveryTime":60000,
    "checkTimeRange":60000,
    "thresholdErrorCount":1,
    "customMessage":"",
    "autoScriptCommand":null
  }
  ...
]
````
