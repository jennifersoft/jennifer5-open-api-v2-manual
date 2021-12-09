## Open API 명세 - 액티브 서비스 경과시간 범위 조회하기 (5.6.0.11)

[설정 > 룰 > 액티브 서비스 경과시간 범위] 화면의 데이터를 조회합니다.

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

- Method : GET
- URL 형식 : `http(s)://<호스트>:<포트>/api-v2/manage/rule/active-service-color-range-boundary`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/manage/rule/active-service-color-range-boundary" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/manage/rule/active-service-color-range-boundary?token=ABCD1234`
- 응답 예제 : 
```
[3000, 5000, 8000]
```
- 응답 형식 : 경과시간이 작은 순서입니다. 순서대로 파란색, 연두색, 주황색, 빨간색 사이의 경계값입니다.
