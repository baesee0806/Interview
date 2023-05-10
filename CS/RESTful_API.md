# RESTful API란?
<p>RESTful API는 Representational State Transfer의 약어로, HTTP/HTTPS 프로토콜을 기반으로 하는 웹 프로그래밍 아키텍처 중 하나입니다. RESTful 웹 서비스는 URI(Uniform Resource Identifier)로 리소스를 표현하고, HTTP 메서드를 사용하여 리소스를 조작하며, JSON 등을 통해 데이터를 주고받는 API를 말합니다. RESTful API는 유니버설 클라이언트(브라우저, 모바일 앱 등)와 서버 간 상호작용을 위한 분산 아키텍처 스타일 중 하나로, 멀티플랫폼 개발에 유용하게 적용됩니다.</p>

## RESTful API를 사용하면 어떤 이점이 있나요?

### 확장성</br>
REST API를 구현하는 시스템은 REST가 클라이언트-서버 상호 작용을 최적화하기 때문에 효율적으로 크기 조정할 수 있습니다. 무상태는 서버가 과거 클라이언트 요청 정보를 유지할 필요가 없기 때문에 서버 로드를 제거합니다. 잘 관리된 캐싱은 일부 클라이언트-서버 상호 작용을 부분적으로 또는 완전히 제거합니다. 이러한 모든 기능은 성능을 저하시키는 통신 병목 현상을 일으키지 않으면서 확장성을 지원합니다.
</br>

### 유연성</br>
RESTful 웹 서비스는 완전한 클라이언트-서버 분리를 지원합니다. 각 부분이 독립적으로 발전할 수 있도록 다양한 서버 구성 요소를 단순화하고 분리합니다. 서버 애플리케이션의 플랫폼 또는 기술 변경은 클라이언트 애플리케이션에 영향을 주지 않습니다. 애플리케이션 함수를 계층화하는 기능은 유연성을 더욱 향상시킵니다. 예를 들어, 개발자는 애플리케이션 로직을 다시 작성하지 않고도 데이터베이스 계층을 변경할 수 있습니다.
</br>

### 독립성</br>
REST API는 사용되는 기술과 독립적입니다. API 설계에 영향을 주지 않고 다양한 프로그래밍 언어로 클라이언트 및 서버 애플리케이션을 모두 작성할 수 있습니다. 또한 통신에 영향을 주지 않고 양쪽의 기본 기술을 변경할 수 있습니다.

## RESTful API 인증 방법이란 무엇인가요?

RESTful 웹 서비스는 응답을 보내기 전에 먼저 요청을 인증해야 합니다. 인증은 신원을 확인하는 프로세스입니다. 예를 들어, 신분증이나 운전면허증을 제시하여 신원을 증명할 수 있습니다. 마찬가지로 RESTful 서비스 클라이언트는 신뢰를 구축하기 위해 서버에 자신의 신원를 증명해야 합니다.

### HTTP 인증

HTTP는 REST API를 구현할 때 직접 사용할 수 있는 일부 인증 체계를 정의합니다. 다음은 이러한 체계 중 두 가지입니다.

### 기본 인증

기본 인증에서 클라이언트는 요청 헤더에 사용자 이름과 암호를 넣어 전송합니다. 안전한 전송을 위해 이 페어를 64자의 세트로 변환하는 인코딩 기술인 base64로 인코딩합니다.

### 전달자 인증

전달자(bearer) 인증이라는 용어는 토큰 전달자에 대한 액세스 제어를 제공하는 프로세스를 나타냅니다. 일반적으로 전달자 토큰은 서버가 로그인 요청에 대한 응답으로 생성하는 암호화된 문자열입니다. 클라이언트는 리소스에 액세스하기 위해 요청 헤더에 토큰을 넣어 전송합니다.

### API 키
API 키는 REST API 인증을 위한 또 다른 옵션입니다. 이 접근 방식에서 서버는 고유하게 생성된 값을 최초 클라이언트에 할당합니다. 클라이언트는 리소스에 액세스하려고 할 때마다 고유한 API 키를 사용하여 본인을 검증합니다. API 키의 경우 클라이언트가 이 키를 전송해야 해서 네트워크 도난에 취약하기 때문에 덜 안전합니다.

### OAuth
OAuth는 모든 시스템에 대해 매우 안전한 로그인 액세스를 보장하기 위해 암호와 토큰을 결합합니다. 서버는 먼저 암호를 요청한 다음 권한 부여 프로세스를 완료하기 위해 추가 토큰을 요청합니다. 특정 범위와 수명으로 언제든지 토큰을 확인할 수 있습니다.

## RESTful API 서버 응답에는 무엇이 포함되어 있나요?
REST 원칙에 따라 서버 응답에 다음과 같은 주요 구성 요소를 포함해야 합니다.

### 상태 표시줄
상태 표시줄에는 요청 성공 또는 실패를 알리는 3자리 상태 코드가 있습니다. 예를 들어, 2XX 코드는 성공을 나타내고 4XX 및 5XX 코드는 오류를 나타냅니다. 3XX 코드는 URL 리디렉션을 나타냅니다.

다음은 몇 가지 일반적인 상태 코드입니다.
```
200: 일반 성공 응답
201: POST 메서드 성공 응답
400: 서버가 처리할 수 없는 잘못된 요청
404: 리소스를 찾을 수 없음
```
### 메시지 본문
응답 본문에는 리소스 표현이 포함됩니다. 서버는 요청 헤더에 포함된 내용을 기반으로 적절한 표현 형식을 선택합니다. 클라이언트는 데이터 작성 방식을 일반 텍스트로 정의하는 XML 또는 JSON 형식으로 정보를 요청할 수 있습니다. 예를 들어, 클라이언트가 John이라는 사람의 이름과 나이를 요청하면 서버는 다음과 같이 JSON 표현을 반환합니다.

'{"name":"John", "age":30}'

### 헤더
응답에는 응답에 대한 헤더 또는 메타데이터도 포함됩니다. 이는 응답에 대한 추가 컨텍스트를 제공하고 서버, 인코딩, 날짜 및 콘텐츠 유형과 같은 정보를 포함합니다.

--- 

## 면접 대답

RESTful API는 Representational State Transfer의 약어로, HTTP/HTTPS 프로토콜을 기반으로 하는 웹 프로그래밍 아키텍처 중 하나입니다.

RESTful API는 URI(Uniform Resource Identifier)로 리소스를 표현하고, HTTP 메서드를 사용하여 리소스를 조작하며, JSON 등을 통해 데이터를 주고받는 API를 말합니다.

RESTful API는 stateless하며, 클라이언트와 서버 간의 의존성이 줄어들어 분산 강건성을 보장합니다.

RESTful API는 CRUD(Create, Read, Update, Delete) 작업을 다음과 같은 HTTP 메서드로 처리합니다: GET, POST, PUT, DELETE

RESTful API는 유니버설 클라이언트(브라우저, 모바일 앱 등)와 서버 간 상호작용을 위한 분산 아키텍처 스타일 중 하나이며, 멀티플랫폼 개발에 유용합니다.

---
### 추가로 http 메소드에 대한 질문

HTTP 메서드는 RESTful API에서 데이터를 생성, 읽기, 갱신, 삭제하기 위한 다양한 작업을 정의하는 데 사용됩니다. RESTful API에서는 다음과 같은 4가지의 HTTP 메서드를 사용합니다.


GET: 리소스를 조회합니다. 해당 리소스의 데이터를 읽어들이는데 사용되며, 조회를 할 때는 요청의 body 대신 Query parameter를 통해 데이터를 전달합니다.

POST: 리소스를 생성합니다. 새로운 데이터를 등록하기 위한 용도로 사용됩니다. 주로 데이터 생성이나 업로드를 위해 사용됩니다. 요청의 body에 데이터를 담아 전송합니다.

PUT: 리소스를 갱신합니다. 기존 데이터를 수정하기 위한 용도로 사용됩니다. 기존 리소스를 대체하는 방식으로 동작합니다. 요청의 body에 데이터를 담아 전송합니다.

DELETE: 리소스를 삭제합니다. 해당 리소스를 삭제하기 위한 용도로 사용됩니다. 요청의 body를 사용하지 않고, URI의 삭제 대상 리소스를 나타내는 쿼리 스트링만을 전송합니다.

위와 같은 HTTP 메서드 중에서 API 구현에 맞게 데이터 조작을 처리하는 것이 중요합니다. API 호출 시 어떤 메서드를 사용해야 하는지, 해당 메서드와 함께 어떤 정보를 보내야 하는지, 적절한 HTTP 응답 상태 코드를 사용하여 API 호출 결과를 알려줘야 합니다.

### HTTP 다른 메소드

HEAD: GET과 유사한 동작을 하지만, 실제 응답 본문(body)을 반환하지 않습니다. 응답 헤더 정보만을 가져옵니다.

OPTIONS: 서버에서 지원하는 HTTP 메서드 집합을 반환합니다. 클라이언트는 이를 통해 서버에서 사용 가능한 메서드를 알 수 있습니다.

PATCH: 리소스의 일부를 수정하는 용도로 사용됩니다. PUT과 유사하지만, 리소스를 대체하지 않고 해당 리소스의 일부분만 업데이트 할 수 있습니다.

TRACE: 요청 메시지를 서버에 보내고 서버에서는 해당 메시지를 그대로 응답하게 됩니다. 이 메서드는 서버와 클라이언트 간의 원격 디버깅 목적으로 주로 사용됩니다.

CONNECT: 서버와의 터널링을 지원하기 위한 메서드입니다. 프록시를 거쳐 SSL 연결 등을 설정할 때 사용될 수 있습니다.

MOVE: WebDAV(웹 분산 영상(versioning), 작성, 권한 시스템 등 제공)에서 사용되는 메소드로 파일을 이동시키기 위한 메소드입니다.

이외에도 여러 메서드가 있지만 RESTful API에서는 일반적으로 GET, POST, PUT, DELETE, 그리고 OPTIONS와 HEAD가 자주 사용됩니다.