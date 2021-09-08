## Open API 명세 - 소스코드(리소스)변경이력 조회하기 (지원 버전 미정)

화면 [분석 > 소스코드(리소스)변경이력] 데이터 중 일부를 조회합니다. 현재 변경된 시간과 인스턴스ID를 조회할 수 있습니다.

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/deploy/<도메인ID>?startTime=<조회범위시작시간>&endTime=<끝시간>`
  - 조회범위는 ms단위이고, 25시간(endTime-startTime) 이하만 지원합니다.
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/deploy/1000?startTime=1628757635000&endTime=1628758635000" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/deploy/1000?startTime=1628757635000&endTime=1628758635000&token=ABCD1234`
- 응답 예제 : 
```
[
  { "collectTime": 1628757730967, "instanceId": 20000 },
  { "collectTime": 1628757910322, "instanceId": 20003 }
]
```
응답 중 `collectTime`은 제니퍼5 데이터서버 기준으로 배포완료를 인지한 시간입니다.
