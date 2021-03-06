매번 프로젝트에서 세션을 사용하여 인증하곤 했습니다.
시스템의 규모가 커지고 세션을 저장해야하는 인증 방식에는 한계가 있을 수 있습니다.
이러한 것을 해결하기 위해 토큰을 사용하여 인증을 할 수 있습니다.

인증 방식들의 특징에 대해서 알아보도록 하겠습니다.


## 1. 서버 기반 인증

서버 기반 인증은 서버 측에서 사용자의 정보를 기억하고 있습니다. 사용자의 정보 즉, 세션을 유지하기 위해서 메모리, 디스크, DB에 저장을 할 수 있습니다.

![](image/1.png)

위 방식이 세션을 사용하는 흐름입니다. 하지만 이러한 방식은 여러가지 문제가 있습니다.

### 1-1. 서버 기반 인증 문제점

#### 확장성

세션을 사용하면 서버를 확장하는 것이 어려워집니다. 여러 대의 서버를 사용하게 되면 분산 시스템을 설계 해야하는데 이 과정에서 세션을 사용하는 것이 불가능한 것은 아니지만 매우 복잡한 과정을 거쳐야합니다.

#### 서버 부하

사용자가 인증을 할 때, 세션을 사용하게 됩니다. 세션은 사용자의 정보를 서버에 저장하기 때문에 사용자의 수가 늘어날수록 서버에 부하가 오게 됩니다.

#### CORS (Cross-Origin Resource Sharing)

세션을 사용할 때 쿠키를 사용하게 되는데 쿠키는 단일 도메인 및 서브 도메인에서만 동작을 하게 됩니다. 그렇기 때문에 여러 도메인에서 세션을 사용하게 될 경우 관리하는 것이 어렵습니다.


## 2. 토큰 기반 인증

토큰 기반 인증은 다양한 장점들을 가지고 있는데 대표적으로 Stateless 하다는 것입니다.
상태를 가지지 않음으로써 서버 기반 인증에서 발생할 수 있었던 확장성 문제와 서버 부하의 문제가 해결될 수 있습니다.

![](image/2.png)

위 흐름과 같이 토큰을 서버가 아닌 클라이언트가 가지게 되고 요청 시 서버에 전달함으로서 인증을 할 수 있습니다.

### 2-1. 토큰 기반 인증 장점

#### Stateless

위에서 말했듯이 토큰 기반 인증은 서버에서 사용자의 정보를 가지지 않기 때문에 무상태성을 가집니다.
무상태성을 가진다는 것은 서버가 확장을 하여도 문제가 생기지 않습니다.

상태를 가지는 세션을 사용하는 방식에서 서버를 확장한다면 사용자가 로그인 했을 때, 유저는 처음 로그인한 서버에만 요청하는 문제가 발생할 수 있습니다. 하지만 토큰을 사용하게 되면 어떠한 서버로 요청이 가도 상관이 없게 됩니다.

#### 보안성

클라이언트가 서버에 요청을 보낼 때, 쿠키가 전달되지 않음으로 쿠키로 인해 발생할 수 있었던 취약점들이 사라집니다. 여기서 의문점이 생길 수 있는 게 토큰도 전달하는데 이것은 문제가 생기지 않을까? 인 데, 토큰은 유효 기간을 설정할 수 있어서 특정 시간이 지나면 토큰이 사라지게 됩니다. 이 방법에 대해서는 추후 자세히 다루겠습니다.

#### OAuth

우리는 OAuth를 사용하여 로그인 방식에 대해 확장을 할 수 있습니다. 토큰 기반 인증을 통해 naver, kakao, google 서비스 계정으로 OAuth가 구현된 다른 웹 서비스에 로그인할 수 있게 됩니다.

#### 여러 플랫폼 및 도메인

토큰을 사용하면 어떤 플랫폼, 도메인에서도 토큰만 유효하다면 요청이 정상적으로 처리될 수 있습니다.


## 3. Access Token, Refresh Token

토큰 기반 인증의 장점에 관해 얘기할 때, 토큰의 유효 기간에 관해 얘기 했습니다.
쿠키와 마찬가지로 토큰 또한 공격자에게 탈취당할 가능성이 있어 보안에 취약할 수 있습니다.
그래서 Access Token은 유효 기간을 설정하여 이 문제를 해결할 수 있었는데, 이 또한 문제가 있습니다.
보안을 위해 유효기간을 짧게 설정하면 매번 로그인해서 새로운 Token을 발급받아야 합니다.

이런 문제를 해결하기 위해 Refresh Token이 나오게 되었습니다.

Refresh Token은 처음 로그인에 성공했을 때, Access Token과 동시에 발급됩니다. 다른 점은 Refresh Token은 긴 유효기간을 가지면서 Access Token이 만료됐을 때, 새로 발급해주는 역할을 하게 됩니다.

Access Token은 API 요청 시마다 HTTP 통신을 통해 노출되지만 Refresh Token은 Access Token이 만료됐을 경우에만 서버로 보내지기 때문에 탈취의 위험이 훨씬 적습니다.


## 4. 마무리

서버 기반 인증, 토큰 기반 인증에 대해서 대략적인 흐름을 살펴보았습니다.
서버 기반 인증의 문제점들을 토큰 기반 인증 시스템에서 해결해주고 있어서 최근에는 많은 서비스에서 토큰 기반 인증을 사용하고 있습니다.

API를 사용하여 웹 서비스를 개발한다면 토큰을 사용하여 사용자들의 인증을 하는 것을 추천해 드립니다.