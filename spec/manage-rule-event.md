## Open API 명세 - ERROR EVENT 룰 설정 조회 (5.5.3.5 이상)

화면의 [관리 > 룰 > EVENT룰] 화면의 설정정보를 API로 조회합니다. 응답 데이터는 화면을 참고하면 대부분 직관적으로 알 수 있습니다. 몇몇 데이터에 대한 추가 설명은 [응답 데이터에 대한 추가 설명](#응답-데이터에-대한-추가-설명)을 참고합니다.

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

### ERROR EVENT 설정 조회하기
- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manage/rule/event/error/<도메인아이디>`
- 요청 예제
`
> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/error/7002 -H "Authorization: Bearer ABCD1234"
`
- 응답 예제
```
[
  {
    "errorType" : "SERVICE_EXCEPTION",
    "applied" : true,
    "level" : "WARNING",
    "checkTimeRange" : 60000,
    "thresholdErrorCount" : 1,
    "iconRecoveryTime" : 60000,
    "customMessage" : "hello world",
    "autoScriptCommand" : "/etc/handle_event.sh"
  }
  ...
]
````

### Metric EVENT 설정 조회하기
- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manage/rule/event/metric/<도메인아이디>/<대상타입>`
  - `<대상타입>` : `domain`, `instance`, `business` 중 하나.
- 요청 예제 : `> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/metric/7002 -H "Authorization: Bearer ABCD1234"`
- 응답 예제 : 
```
[
  {
    "metricId" : "heap_usage",
    "level" : "NORMAL",
    "applied" : true,
    "expression" : "value>30",
    "checkTimeRange" : 60000,
    "thresholdErrorCount" : 1,
    "iconRecoveryTime" : 60000,
    "customMessage" : "hello world",
    "autoScriptCommand" : "/etc/handle_event.sh"
  }
  ...
]
```

### 비교 EVENT 설정 조회하기
- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manage/rule/event/compare/<도메인아이디>/<대상타입>`
  - `<대상타입>` : `domain`, `instance` 중 하나.
- 요청 예제 : `> curl --request GET https://java.jennifersoft.com/api-v2/manage/rule/event/comparing/1006/instance -H "Authorization: Bearer ABCD1234"`
- 응답 예제 : 
```
[
  {
    "metricId" : "service_rate",
    "level" : "NORMAL",
    "applied" : true,
    "iconRecoveryTime" : 60000,
    "target" : {
      "operator" : ">",
      "period" : "PREVIOUS_WEEK", 
      "ratioInPercent" : 130
    },
    "filter" : {
      "metricId" : "service_rate",
      "minimumValue" : 3.0
    }
  }
  ...
]
```

### 응답 데이터에 대한 추가 설명
- 모든 시간 값은 ms 단위입니다.
- level : NORMAL, WARNING, FATAL 중 하나입니다.
- autoScriptCommand, filter : 활성화 하지 않은 경우 null 입니다. 
