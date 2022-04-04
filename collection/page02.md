1. this에 관해 설명하시오.

2. local storage(브라우저 저장소)에 관해 설명하시오.

3. Javascript는 어떤 언어인가요?
   싱글 쓰레드 언어입니다.

하지만 실제사용시에는 멀티 스레드처럼 사용하는데 어떻게 그렇게 사용하나요?
비동기함수는 실행컨텍스트가 아닌 멀티쓰레드인 브라우저의 이벤트 루프에 의하여 일정시간이 지난뒤
태스크 큐로 옮겨집니다. 그리고 콜 스택에서 스택이 다 제거된 뒤에 이벤트루프에 의하여 콜스택으로 옮겨져 실행됩니다.
이 과정에서 자바스크립트엔진 싱글쓰레드로 작동하지만 브라우저는 멀티쓰레드임으로 자바스크립트도 멀티쓰레드인것처럼
작동하게 되는 것입니다.

비동기적으로 실행되는 것을 동기적으로 사용하는 방법은?
(generator 함수를 사용하여 코드 호출을 조작하여 동기적으로 사용하는 방법이 있고 이를 간편화한
promise 객체를 반환하는 async/await 키워드를 사용하여 동기적으로 사용할 수 있는 방법이 있습니다.
)

5. 이벤트 루프에 관해 설명하시오.

6. 이벤트 전파,이벤트 캡처링,이벤트 버블링,이벤트 위임에 대해 연관지어 설명해주시고 이벤트 위임을 사용하였을 때 장점을 알려주세요.

   이벤트 캡처링은 이벤트 객체가 window에서 시작하여 이벤트 타깃 방향으로 이동하는 단계이고
   타깃 단계는 이벤트 객체가 이벤트 타깃에 도달했을 때의 단계이며
   이벤트 버블링은 도달한 뒤 window 방향으로 이동하는 단계입니다.
   즉, 이벤트 객체는 DOM 트리를 돌아다니며 전파되기 때문에 지정된 요소외에서도
   이벤트 타깃을 캐치할 수 있습니다.

이러한 작동원리를 이용하여 이벤트를 발생시킨 요소에서 뿐만 아니라 상위 DOM요소에서도 이벤트 객체를 캐치함으로써 이벤트 타깃을 캐치할 수 있습니다.
이는 많은 DOM요소에 이벤트 핸들러를 등록해야할 경우 이들의 부모인 상위 요소에
이벤트핸들러를 등록해줌으로써 생산적인 코드를 구현할 수 있습니다.

또한 만약 이러한 이벤트 위임을 막고 싶다면 이벤트 전파를 중지시키는
이벤트객체의 stopPropagation() 메서드를 사용하면 됩니다.

## 7. 실행컨텍스트

8. 프로토타입에 관해 설명해주세요.

> call,bind,apply 메서드에 관해 설명해주세요.

> 프레임워크와 라이브러리의 차이

## 9. 마이크로태스크 큐와 태스크 큐

## 10. Cors와 Cors오류를 해결하기 위한 방법

CORS는 서로 다른 origin으로 네트워크 요청을 하여도 CORS 규칙을 지킨다면 리소스를 응답받을 수 있도록 하며 이에 대한 정책을 규정한 기능이다.

이 때 서버에서 허용 origin 설정(Access-Control-Allow-Origin)을 제대로 해주지 않았다면 CORS에러가 발생할 수 있다.

때문에 해당 에러를 해결하기 위해서는 서버에서 허용 origin을 알맞게 해주면 된다.(예)Access-Control-Allow-Origin: https://requestorigin.com)

다른 방법은 웹팩 개발 서버에서 proxy기능을 사용하는 방법이 있다.
proxy로 요청을 보내고자하는 서버를 입력해주면 나의 개발 서버로 요청을 보냈을 때 proxy가 대신하여 요청을 보내고자하는 서버에 요청을 보내고 응답을 받아 전달해준다.
(다만 proxy 설정 서버가 production모드인 경우 해결이 안될 수 있으니 로컬 서버로 설정할 경우에 사용하는 것이 좋다.
production 모드에서도 사용하고 싶다면 client orgin과 server origin이 같은 경우에 사용하는 것이 권장된다.)
)
**Reference**

- https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#the_http_request_headers

- https://evan-moon.github.io/2020/05/21/about-cors/#simple-request

- https://stackoverflow.com/questions/52877492/proxy-not-working-for-create-react-app-in-production