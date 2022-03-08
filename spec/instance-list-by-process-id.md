## Open API 명세 - 프로세스ID로 인스턴스 찾기 (릴리즈 미정)

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

- Method : GET
- URL 형식 : `http(s)://<호스트>:<포트>/api-v2/manage/instance?processId=1234&hostname=myhost
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/manage/instance?processId=1234&hostname=myhost" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/manage/instance?processId=1234&hostname=myhost&token=ABCD1234`
- 응답 예제 : 
```
// 도메인ID 1000, 인스턴스ID 20000인 인스턴스가 검색된 응답입니다. 일반적인 경우 응답은 1개를 초과하지 않습니다.
{
  "1000": {
    "20000": {"hostname":"myhost", "processId":"1234"}
  }
}
```
- 응답 형식 : 대응되는 인스턴스가 없는 경우 비어 있습니다. -> ```{}```