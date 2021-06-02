## Open API 명세 - 수동 RDB Export 작업 (릴리즈 버전 미정)

지난 날짜의 데이터를 내보내는 작업에 대한 API입니다. RDB Export 기능은 제니퍼5 엔지니어 문서를 참고하여 숙지하시기 바랍니다.
날짜를 제외한 다른 설정은 conf파일에 명시하는 RDB Export설정을 그대로 따릅니다. 

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

### 작업 추가하기
- Method : POST
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manual-rdb-export?date=<YYYY-MM-DD>`
- 요청 예제
  - curl : `> curl --request POST "https://java.jennifersoft.com/api-v2/manual-rdb-export?date=2021-05-29" -H "Authorization: Bearer ABCD1234"`
- 응답 예제
```
OK
```

### 진행 상태 조회하기
- 현재 상태를 조회합니다. 어떤 작업이 진행 중이고 대기 중인지 알 수 있습니다. 진행 단계의 자세한 기록은 뷰서버의 RDB Export 로그파일에 기록됩니다.
- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manual-rdb-export`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/manual-rdb-export" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/manual-rdb-export`
- 응답 예제 : 
```
[
   {"id":"2e96102f","date":"2021-05-27","statusDescription":"COMPLETED"},
   {"id":"311d6aaa","date":"2021-05-29","statusDescription":"EXPORTING"}
]
```
