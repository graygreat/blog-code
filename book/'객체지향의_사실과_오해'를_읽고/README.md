## 1년 전...

>선배: 객체지향이 뭔지 설명해줄 수 있어?
>
>Gray: 클래스로 만들어서 객체를 만들고 ...

객체지향이 무엇인지 모르고 개발을 하고 있었음

## 객체지향은 무엇일까?

### 1. 실세계를 모방하는 것이 아닌 새로운 세계를 창조하는 것

* 많은 책을 보면 객체지향은 실세계를 모방하는 것이라고 말한다.
* 객체는 현실 객체의 부분적인 특징을 모방하는 것이 아니라 현실 객체가 가지지 못한 추가적인 능력을 보유할 수 있다.
* 현실에서 트럼프 카드는 스스로 뒤집기, 말하기, 걷기를 할 수 없지만, 객체지향 세계에서는 이 모든 것이 가능하다.


![](https://i.imgur.com/9iOEaWr.png)


### 2. 역할과 책임

* 여러 사람이 동일한 역할을 수행할 수 있다.

	* 각자의 맡은 역할만 수행하면 누가 무엇을 실행했는지는 상관없다.
	* 자동차는 자동차의 역할만 하면 되지 어떤 자동차인지는 중요하지 않다.
* 역할은 대체 가능성을 의미한다.

	* K3, 아반떼, 테슬라 모델3 중에 어떤 것을 선택해도 자동차 역할을 할 수 있다.
* 책임을 수행하는 방법은 자율적으로 선택할 수 있다.

	* 자동차가 어떤 원리로 움직이는지는 차마다 다를 수 있다.
	* 동일한 요청에 대해 서로 다른 방식으로 응답할 수 있는 능력을 다형성이라고 한다.
* 한 사람이 동시에 여러 역할을 수행할 수 있다.

	* 자동차는 자가용의 역할도 할 수 있지만, 레이싱 카의 역할도 할 수 있다.

![](https://i.imgur.com/3UpeUDt.png)


### 3. 협력

* 특정한 책임을 수행하는 역할 간의 연쇄적인 요청과 응답을 통해 목표를 달성한다.
* 역할과 책임을 가진 객체들은 서로 협력을 하면서 객체지향의 세계를 만들어나갈 수 있다.

### 4. 행동이 상태를 결정한다

* 클래스를 어떻게 구성하지? 어떤 필드가 필요하지?
* 애플리케이션에 필요한 협력을 생각하고 협력에 참여하는 데 필요한 행동을 생각한 후 행동을 수행할 객체를 선택하는 방식으로 수행된다.

	* 행동은 객체가 협력에 참여하면서 완수해야 하는 책임


### 5. 객체는 자율적인 존재

* 자율적인 객체는 상태와 행위를 지니며 스스로 자신을 책임지는 객체
* 너무 상세한 범위까지 책임을 지게 된다면 자유의 범위를 제한할 수 있다.
* 또 그렇다고 너무 추상적인 책임을 지게 하면 협력 관계에 문제가 생길 수 있다.
* 자율성을 보장할 수 있을 정도로 충분히 추상적인 동시에 협력의 의도를 뚜렷하게 표현할 수 있어야 한다.

	* 많은 설계와 개발을 통해 익힐 수 있을 것 같다.

* 객체가 자율적이면 어떻게 객체지향 내에서 객체들은 소통을 할 수 있을까?

	* 메시지를 통해서 가능


### 6. 추상화

* 어떤 양상, 세부 사항, 구조를 좀 더 명확하게 이해하기 위해 특정 절차나 물체를 의도적으로 생략하거나 감춤으로써 복잡도를 극복하는 방법
* 복잡성을 다루기 위한 추상화의 방법

	* 구체적인 사물 간의 공통점 추출
	* 중요한 부분을 강조하기 위해 불필요한 세부 사항을 제거함으로써 단순하게 만듦
* SM5, 제네시스, K5를 자동차로 추상화하게 되면 복잡성을 줄여 유연하게 객체를 표현할 수 있다.


### 7. 개념

* 추상화와 개념은 비슷하게 생각할 수 있음
* 빠른 속도로 거리를 누비는 교통수단에 대해서는 '자동차'라는 개념을 적용할 수 있다.
* 개념을 통해 타입을 생각할 수 있다.
* 동일한 타입으로 분류되기 위해서는 공통의 행동을 가져야 한다.


## 1주일 전, 던졌던 질문


**객체가 역할과 책임을 가지는 것은 알겠는데, 역할과 책임은 어떻게 나눌까?**

* 메시지 서비스 담당하는 역할을 하는 'MessageService' 객체가 있다.
* 'MessageService' 객체는 메시지를 저장, 전송, 변경, 취소해야 할 책임이 있다.
* 역할은 책임의 집합이다.
* Gray라는 역할을 가진 내가 열심히 일하고 운동하고 밥을 먹어야 할 책임이 있듯이, 객체도 역할이 책임을 진다고 생각하면 된다.


## 그래서 객체지향이 뭔데?


* 자율적인 객체들이 적절한 책임을 지고 역할을 수행하면서 서로 협력 관계를 구축하는 것이다.


## 결론


### 비슷한 내용을 여러 해석을 통해 표현

#### 장점

* 중요한 내용을 반복해서 여러 가지 해석으로 볼 수 있어서 기억에 남음

#### 단점

* 개념에 혼란이 옴

### 1년 전에 읽었을 때와는 또 다른 느낌

* 1년 전, 객체지향이 무엇인지를 아는 것에 초점을 맞춤
* 현재는 내 코드가 객체지향을 지키고 있나? 어떻게 하면 좀 더 객체지향스러워질까?

### 다른 분들은 어떻게 설계를 하고 적용했을까?

* 책임 주도 설계에서 어떤 식으로 설계를 해나가는지 궁금하다.
