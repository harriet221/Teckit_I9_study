# 네이티브 앱(Native APP)

모바일 기기에 최적화된 네이티브 언어로 개발된 앱을 의미한다.

안드로이드 운영체제의 대표적인 네이티브 언어는 코틀린(Kotlin) 또는 자바(Java)이며, iOS는 스위프트(Swift) 또는 오브젝티브 C(Objective C)이다.

해당 언어를 기반으로 각 모바일 운영체제에 맞는 앱을 개발한 것이 네이티브 앱이다.

구글 플레이스토어나 앱 스토어에 등록된 대부분의 애플리케이션은 네이티브 앱이다.

## 장점

- 각 운영체제에 최적화된 방식으로 개발되므로 앱의 구동 속도가 빠르고 안정적이다.
- 높은 사양의 그래픽으로 원하는 디자인을 구현할 수 있다.
- 디바이스 전체에 접근 권한을 가질 수 있으므로 기기 자체의 기능을 앱에 활용할 수 있다.

## 단점

- 다른 운영체제에서는 호환이 되지 않으므로 안드로이드와 iOS 앱을 별도로 개발해야 한다.
- 다른 앱 개발 방식에 비해 제작하는 데 비용과 시간이 많이 든다.
- 앱에 수정사항이 생기는 경우, 앱 마켓의 심사를 거치고 전체 업데이트를 진행해야 한다.

</br>

# 웹 앱(Web APP)

네이티브 앱처럼 보이고 기능 또한 동일하게 구현되지만, 웹 기술을 활용하여 만들어진 앱을 의미한다.

웹 기반의 HTML, CSS, Javascript 등을 활용하며, 별도의 앱 파일을 설치하지 않고 인터넷 브라우저를 기반으로 동작한다.

## 장점

- 인터넷 브라우저를 기반으로 동작하므로 별도의 앱을 설치하지 않아도 된다.
- 표준 웹 언어로 만들기 때문에 상대적으로 제작 비용이 저렴하고 개발 기간도 짧은 편이다.
- 수정사항이 생겨도 앱 마켓의 심사를 거치는 과정이 없으므로 업데이트 속도가 빠르다.

## 단점

- 디바이스에 접근 권한이 없다.
- 앱 설치를 하지 않는 대신, 브라우저 실행 및 URL 입력이나 별도의 링크를 통하는 과정을 거쳐야 해서 번거롭다.
- 네이티브 앱에 비해 상대적으로 구동 속도가 느리고 안정성이 떨어진다.

## 모바일 웹과의 차이점

모바일 웹은 PC를 기준으로 제작된 뒤 모바일 화면 규격에 맞게 폰트나 이미지 등을 바꾼 것이지만, 웹 앱은 처음부터 모바일을 기준으로 제작되므로 스마트폰 이용자에게 훨씬 편안한 환경을 제공한다.

실행 방식에도 차이가 있다.

모바일 웹은 화면의 일부분이 바뀔 때 전체를 서버에서 새롭게 불러오는 풀 브라우저 방식(Full Browsing)을 사용하지만, 웹 앱은 변경이 필요한 부분만 바꾸는 단일 페이지 방식(SPA, Single Page Application)을 사용한다.

따라서 모바일 웹이 웹 앱보다 속도가 느리다는 특징이 있다.

</br>

# 하이브리드 앱(Hybrid APP)

하이브리드 앱은 네이티브 앱과 웹 앱의 개발 방식을 모두 사용하며, 웹과 앱의 장점을 합쳐놓은 방식이다.

앱의 화면이나 기능 등 콘텐츠 영역은 웹 기반으로 제작하고, 겉모습은 앱 마켓에 등록하고 설치하는 방식을 통해 네이티브 앱으로 포장한 것이다.

## 장점

- 웹 기술을 기반으로 제작되지만, 모바일 API도 사용할 수 있으므로 디바이스 자체 기능도 활용할 수 있다.
- 네이티브 앱에 비해 개발 비용 및 시간을 절약할 수 있다.
- 한번 개발해두면 패키징을 바꾸는 방식으로 여러 플랫폼에 대응할 수 있다.

## 단점

- 네이티브 앱과 웹 앱 개발 지식이 모두 필요하다.
- 브라우저의 성능이 떨어지면 앱 구동 속도도 저하된다.
- 네이티브 앱에 비해 디자인의 자유도가 떨어진다.
