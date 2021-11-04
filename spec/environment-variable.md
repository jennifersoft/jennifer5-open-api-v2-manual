## Open API 명세 - 로디드 클래스 조회하기 (5.6.0.9 이상)

[분석 > 시스템 환경변수] 화면의 데이터를 조회합니다.

Open API 사용이 처음이라면 기본적인 사용법을 [README](/README.md)를 참고하여 숙지합니다.

- Method : GET
- URL 형식 : `http(s)://<호스트>:<포트>/api-v2/environment-variable/<도메인ID>`
- 요청 예제
  - curl : `> curl --request GET "https://java.jennifersoft.com/api-v2/environment-variable/1000" -H "Authorization: Bearer ABCD1234"`
  - 브라우저 : `https://java.jennifersoft.com/api-v2/environment-variable/1000?token=ABCD1234`
- 응답 예제 : 
```
{
  // 인스턴스ID
  "20001": {    
    "SYSTEM": {
      "PATH": "/usr/local/sbin:/usr/local/bin",
      "JAVA_HOME": "/usr/java/jdk1.6.0_45"
      ...
    },
    "JAVA": {
      "java.vendor": "Sun Microsystems Inc.",
      ...
    },
    ...
  },
  "20002": {
    "SYSTEM": {
      ...
    },
    ...
  },
  ...
}
```
