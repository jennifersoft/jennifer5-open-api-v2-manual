## Open API 명세 - 액티브 서비스 상세 조회하기 (5.6.1)

액티브 서비스 목록의 단일 액티브 서비스 상세 정보를 조회합니다.

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

- Method : GET
- URL 형식 : `http(s)://<호스트>:<포트>/api-v2/active-service/detail/<도메인아이디>/<트랜잭션아이디>?sessionId=<에이전트 세션 아이디>&threadHash=<액티브 서비스를 실행중인 스레드의 해시>`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/active-service/detail/1000/1234567?sessionId=1&threadHash=10" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/active-service/detail/1000/1234567?sessionId=1&threadHash=10&token=ABCD1234`
- 응답 예제 : 
```
{
  "userId": "jennifer",
  "guid": "guid",
  "sql": "select * from jennifer",
  "http": {
    "method": "get",
    "query": "a=1&b=2"
  }
}
```

* 요청 파라미터의 각종 정보는 액티브 서비스 상세 조회 api 의 결과에 포함된 값입니다.
