## Open API 명세 - 수동 RDB Export 작업 (릴리즈 미정)

지난 날짜의 데이터를 내보내는 작업에 대한 API입니다. RDB Export 기능은 제니퍼5 엔지니어 문서를 참고하여 숙지하시기 바랍니다.
수동으로 내보내는 데이터에 대한 설정은 뷰서버의 conf파일에 설정하는 RDB Export설정을 그대로 따릅니다. 

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

### 작업 추가하기
- Method : POST
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manual-rdb-export?date=<YYYY-MM-DD>`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/manual-rdb-export?date=2021-05-29" -H "Authorization: Bearer ABCD1234"`
- 응답 예제
```
OK
```

### 진행 상태 조회하기
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