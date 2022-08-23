## Open API 명세 - RDB Export 대상 DB의 접속 암호 설정하기 (릴리즈 미정)

RDB Export 대상 DB의 접속 암호를 설정합니다. RDB Export 기능은 제니퍼5 엔지니어 문서를 참고하여 숙지하시기 바랍니다.

이 API는 뷰서버 conf 파일에 지정하는 `rdb_export_jdbc_password` 옵션의 대안입니다. 이 API를 이용하면 옵션과 다르게 암호를 파일에 노출시키지 않을 수 있습니다. conf파일의 옵션으로도 암호가 설정된 경우 이 API로 설정한 값을 사용합니다.

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

### 암호 설정하기

- Method : PUT
- URL : `http(s)://<호스트>:<포트>/api-v2/configuration/rdb-export-password-override`
- Content-Type: text/plain
- Request Body: 설정할 암호
- 요청 예제
  - curl : `> curl --request PUT "https://java.jennifersoft.com/api-v2/configuration/rdb-export-password-override" -H "Content-type: text/plain" -H "Authorization: Bearer ABCD1234" -d "XYZ1234"`
* 응답 예제 : 
  ```json
  "Password: XYZ1234"
  ```
  * 설정된 값을 응답으로 줍니다. 보안을 위해 별도의 조회 API는 제공하지 않습니다.

### 암호 삭제하기
- Method : DELETE
- URL : `http(s)://<호스트>:<포트>/api-v2/configuration/rdb-export-password-override`
- 요청 예제
  - curl : `> curl --request DELETE "https://java.jennifersoft.com/api-v2/configuration/rdb-export-password-override" -H "Authorization: Bearer ABCD1234"`
