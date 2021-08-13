## Open API 명세 - 소스코드(리소스)변경 이력 조회하기 (지원 버전 미정)

라라라라

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

### 진행 상태 조회하기
- 현재 상태를 조회합니다. 어떤 작업이 진행 중이고 대기 중인지 알 수 있습니다. 진행 단계의 자세한 기록은 뷰서버의 RDB Export 로그파일에 기록됩니다.
- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/deploy/[도메인ID]`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/deploy?startTime=1628757635000&endTime=1628758635000" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/deploy?token=ABCD1234&startTime=1628757635000&endTime=1628758635000`
- 응답 예제 : 
```
[
   {"id":"2e96102f","date":"2021-05-27","statusDescription":"COMPLETED"},
   {"id":"311d6aaa","date":"2021-05-29","statusDescription":"EXPORTING"}
]
```
