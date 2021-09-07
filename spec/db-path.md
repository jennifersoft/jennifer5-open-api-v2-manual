## Open API 명세 - JENNIFER DB 경로 조회하기 (지원 버전 미정)

화면 [설정 > JENNIFER DB > 보관 설정 > 경로] 데이터를 조회합니다.
Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

- Method : GET
- Path 형식 : `http(s)://<호스트>:<포트>/api-v2/manage/db/path/<도메인ID>`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/manage/db/path/1000" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/manage/db/path/1000?token=ABCD1234`
- 응답 예제 : 
```
{
  "main": "/home/jennifer/jennifer5/db/data",
  "backup": "/home/jennifer/jennifer5/db/data"
}
```
