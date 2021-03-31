### API 명세 - ERROR EVENT 룰 설정 조회 (5.5.3.5 이상)

화면의 [관리 > 룰> EVENT룰] 화면의 설정정보를 API로 조회합니다.

우선 기본적인 API 사용법을 [README](/README.md)를 참고하여 숙지합니다.

#### Path 형식
`http(s)://<호스트>:<포트>/api-v2/manage/rule/event/error/<도메인아이디>`
#### 요청 예제
`> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002 -H "Authorization: Bearer ABCD1234"`

#### 응답 예제
```
[
  {
    "errorType" : "SERVICE_EXCEPTION",
    "applied" : true,
    "level" : "WARNING",
    "iconRecoveryTime" : 60000,
    "checkTimeRange" : 60000,
    "thresholdErrorCount" : 1,
    "customMessage" : "",
    "autoScriptCommand" : "/etc/handle_event.sh"
  }
  ...
]
````

#### 응답 데이터에 대한 추가 설명
대응되는 데이터는 화면을 참고하면 대부분 알 수 있습니다. 여기서는 몇가지 데이터에 대해서 추가로 설명합니다. 모든 시간 값은 ms 단위입니다.
- level : NORMAL, WARNING, FATAL 중 하나입니다.
- autoScriptCommand : 설정이 없는 경우 null 입니다.






