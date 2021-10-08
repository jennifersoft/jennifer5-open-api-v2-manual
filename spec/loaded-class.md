## Open API 명세 - 로디드 클래스 조회하기 (릴리즈 미정)

화면 [분석 > 로디드 클래스] 데이터를 조회합니다.

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

- Method : GET
- URL 형식 : `http(s)://<호스트>:<포트>/api-v2/loaded-class/<도메인ID>/<인스턴스ID>?search=<클래스이름의일부>`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/loaded-class/1000/20001" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/loaded-class/1000/20001?token=ABCD1234`
- 응답 예제 : 
```
[
  {
    "className": "com.jennfiersoft.StringUtil",
    "superClassName": "java.lang.Object",
    "interfaceClassNames": [ "javax.servlet.ServletContextListener", "java.lang.Cloneable" ],
    "classLoaderName": "BootstrapClassLoader module java.base"
  },
  {
    "className": "org.apache.commons.logging.Log",
    ...
  },
  ...
]
```
- 제약
  - 로드된 클래스가 6만개 이하인 경우에만 조회할 수 있습니다.
  - 검색은 클래스이름 검색만 지원합니다.
