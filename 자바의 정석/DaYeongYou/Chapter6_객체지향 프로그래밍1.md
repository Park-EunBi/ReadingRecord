# 1. 객체지향언어

## 1.1 객체지향언어의 역사

- 객체지향이론의 기본 개념
  - 실제 세계는 사물(객체)로 이뤄져 있으며, 발생하는 모든 사건들은 사물간의 상호작용이다.

## 1.2 객체지향언어

- 기존 프로그래밍언어와 전혀 다른 것이 아님
  - 기존의 프로그래밍 언어에 몇 가지 규칙을 추가한 보다 발전된 형태
  - 이러한 규칙들을 이용해 코드 간에 서로 관계를 맺어줌으로써 보다 유기적으로 프로그램 구성 가능.
- 객체지향언어의 주요 특징
  1. **코드의 재사용성**이 높다.
     - 새로운 코드를 작성할 때 기존의 코드를 이용해 쉽게 작성 가능
  2. 코드의 **관리가 용이**하다.
     - 코드간의 관계를 이용해 적은 노력으로 쉽게 코드 변경 가능
  3. **신뢰성이 높은 프로그래밍**을 가능하게 한다.
     - `제어자`, `메서드`를 이용해 데이터를 **보호**
     - 올바른 값 **유지**
     - 코드의 **중복** 제거
     - 코드의 불일치로 인한 오동작 **방지**
- 가장 큰 장점
  - 코드의 재사용성이 높고 유지보수가 용이
    → 프로그램의 개발과 유지보수에 드는 시간과 비용을 획기적으로 개선
- 상속, 다형성과 같은 객체지향개념

  - 재사용성, 유지보수, 중복된 코드 제거
  - 세가지 관점으로 보면 이해가 쉬움.

- 객체지향개념에 얽매여 고민하기 보다는 → 일단 프로그램을 기능적으로 완성한 후에 코드 개선의 방향으로 생각할 것.
- 처음부터 이론을 많이 안다고 해서 좋은 설계를 할 수 있는 건 아님.

# 2. 클래스와 객체

## 2.1 클래스와 객체의 정의와 용도

- **클래스 정의**
  - 객체를 정의해놓은 것
  - 객체의 설계도 또는 틀
- **클래스 용도**
  - 객체를 생성하는 데 사용됨
  - 객체는 클래스에 정의된 대로 생성됨.
- **객체의 정의**
  - 실제로 존재
  - 사물 또는 개념
- **객체의 용도**

  - 객체가 가지고 있는 기능과 속성에 따라 다름

- 클래스는 단지 객체를 생성하는 데 사용됨, 객체 그 자체 ❌
  - e.g.) TV를 보기위해, TV(객체)가 필요함. TV설계도(클래스)가 필요한 건 아님
    - TV설계도(클래스) - 단지 TV라는 제품(객체)를 만드는데만 사용됨.
    - TV설계도를 통해 TV가 만들어진 후에야 사용 가능.
    - 프로그래밍: **먼저 클래스 작성 → 클래스로부터 객체 생성해 사용!**

## 2.2 객체와 인스턴스

- 인스턴스화
  - 클래스로부터 객체를 만드는 과정
  - 어떤 클래스로부터 만들어진 객체 : 그 **클래스의 인스턴스**
  - e.g.) TV 클래스 → 만들어진 객체 : **TV클래스의 인스턴스!**
  - 인스턴스 == 객체, 객체는 모든 인스턴스를 대표하는 포괄적인 의미.

## 2.3 객체의 구성요소 - 속성과 기능

- 객체는 **속성**과 **기능** - 두 종류의 구성요소로 이뤄짐
  - 객체는 속성, 기능의 집합.
  - 객체가 가지고 있는 속성과 기능을 그 객체의 **멤버**라 함.
- 클래스란 객체를 정의한 것 → 클래스에는 객체의 모든 속성과 기능 정의.

## 2.4 인스턴스의 생성과 사용

- TV클래스 → TV설계도 작성한 것에 불과.

  - **TV 인스턴스를 생성해야** 제품(tv) 사용 가능

  ```java
  클래스명 변수명;           // 클래스의 객체를 참조학 위한 참조변수 선언
  변수명 = new 클래스명();   // 클래스의 객체 생성 -> 객체의 주소를 참조변수에 저장.

  Tv t;                  // tv클래스 타입의 참조변수 t를 선언
  t = new Tv();          // tv인스턴스를 생성한 후, 생성된 tv인스턴스의 주소를 t에 저장.
  ```

- Tv 클래스로부터 인스턴스 생성 →인스턴스의 속성(channel)과 메서드(channelDown())를 사용하는 방법

```java
class Tv {
    // Tv의 속성(멤버변수)
    String color; // 색
    boolean power; // 전원상태(on/off)
    int channel; // 채널

    // tv의 기능(메서드)
    void power() {
        power = !power;
    }

    void channelUp() {
        ++channel;
    }

    void channelDown() {
        --channel;
    }
}

class TvTest {
    public static void main(String[] args) {
        Tv t;
        t = new Tv();
        t.channel = 7;
        t.channelDown();
        System.out.println("현재 채널은 " + t.channel + "번 입니다.");
    }
}
```

1. **Tv t;**
   - Tv 클래스 타입의 참조변수 t 선언
   - 메모리에 참조변수 t를 위한 공간 생성.
   - 인스턴스가 생성되지 않았으므로 참조변수로 아무것도 할 수 없음.
2. t = new Tv();
   - 연산자 new 에 의해 Tv 클래스의 인스턴스가 메모리의 빈 공간에 생성됨.
   - 멤버변수는 각 자료형에 해당하는 기본값으로 초기화.
     - color(참조형): null
     - power(boolean): false
     - channel(int): 0
   - 대입연산자(=)에 의해 생성된 객체의 주속밧이 참조변수 t에 저장됨.
   - 참조변수 t를 통해 Tv인스턴스 접근 가능.
   - 인스턴스를 다루기 위해서는 **참조변수가 반드시 필요**
3. t.channel = 7;
   - 참조변수 t에 저장된 주소에 있는 인스턴스의 멤버변수 channel에 7 저장
   - 인스턴의 멤버변수를 사용하려면 `참조변수.멤버변수`
4. t.channelDown();
   - 참조변수 t가 참조하고 있는 **Tv인스턴스의 channelDown 메서드** 호출
   - channelDown 메서드 → 멤버변수 channel에 저장되어 있는 값을 1 감소.
   - channel : 7 → 6
5. System.out.println(”현재 채널은 “+t.channel+” 입니다.”);
   - 참조변수 t가 참조하고 있는 TV인스턴스의 멤버변수 channel에 저장되어 있는 값 출력.

### 인스턴스와 참조변수의 관계

- 일상생활에서 사용하는 TV와 TV리모콘의 관계
- TV리모콘(참조변수)을 사용해 TV(인스턴스)를 다루기 때문임.
- 인스턴스는 참조변수를 통해서만 다룰 수 있으며, 참조변수의 타입은 인스턴스의 타입과 일치해야 함.

```java
class TvTest2 {
    public static void main(String[] args) {
        Tv t1 = new Tv();
        Tv t2 = new Tv();
        System.out.println("t1의 channel: " + t1.channel + "입니다. ");
        System.out.println("t2의 channel: " + t2.channel + "입니다. ");

        t1.channel = 7;
        System.out.println("t1의 channel값을 " + t1.channel + "로 변경하였습니다.");

        System.out.println("t1의 channel: " + t1.channel + "입니다. ");
        System.out.println("t2의 channel: " + t2.channel + "입니다. ");
    }
}
```

- Tv클래스의 인스턴스 t1과 t2 생성 → 인스턴스 t1의 멤버변수인 channel의 값 변경.
- →같은 클래스로부터 생성되었을지라도 각 인스턴스의 속성(멤버변수)는 서로 다른 값을 유지
  - 메서드의 내용은 모든 인스턴스에 대해 동일.

```java
public class TvTest3 {
    public static void main(String[] args) {
        Tv t1 = new Tv();
        Tv t2 = new Tv();
        System.out.println("t1의 channel: " + t1.channel + "입니다. ");
        System.out.println("t2의 channel: " + t2.channel + "입니다. ");

        t2 = t1; // 새롭게 추가된 문장
        t1.channel = 7;
        System.out.println("t1의 channel값을 " + t1.channel + "로 변경하였습니다.");

        System.out.println("t1의 channel: " + t1.channel + "입니다. ");
        System.out.println("t2의 channel: " + t2.channel + "입니다. ");
    }
}
```

- 참조변수에는 하나의 값(주소)만이 저장될 수 있음.
- 둘 이상의 참조변수가 하나의 인스턴스를 가리키는(참조하는)것은 가능, but 하나의 참조변수가 여러 개의 인스턴스를 가리키는 것은 가능 ❌

## 2.5 객체 배열

- 많은 수의 객체를 다뤄야할 때, 배열로 다루면 편리
- 객체 역시 배열로 다루는 것이 가능 → `객체 배열`
- 객체 배열 안에 객체가 저장되는 것은 아니고 → `객체의 주소` 가 저장됨
- 사실, 객체배열은 참조변수들을 하나로 묶은 `참조 변수 배열`임.

`Tv tv1, tv2, tv3` → `Tv[] tvArr = new Tv[3]`

- 길이가 3인 객체 배열 tvArr 생성 → 각 요소는 참조변수의 기본값인 `null`로 자동 초기화.
- 객체 배열 → 3개의 객체, 정확히는 **객체의 주소**를 저장 가능
- 객체 배열 생성 → 객체를 다루기 위한 참조변수들이 만들어짐!
  - 객체 저장 ❌
  - 객체 생성 후 객체 배열의 각 요소에 저장하는 것을 잊으면 안됨.

```java
TV[] tVArr =new Tv[3]; // 참조변수배열(객체배열)을생성

// 객체를 생성해서 배열의 각 요소에 저장
tvArr[0] = new Tv();
tvArr[1] = new Tv();
tvArr[2] = new Tv();
```

- 배열 초기화 블럭
  `Tv[] tvArr = { new Tv(), new Tv(), new Tv() };`
- 다뤄야 할 객체수가 많을 땐 for문 사용

  ```java
  Tv[] tvArr = new Tv[100];

  for(int i=0; i<tvArr.length; i++){
  	tvArr[i]=new Tv();
  }
  ```

- 모든 배열이 그렇듯이 객체 배열도 같은 타입의 객체만 저장 가능
- 여러 종류의 객체를 하나의 배열에 저장하려면, `다형성` 이용!

## 2.6 클래스의 또 다른 정의

- 객체지향이론의 관점
  - 클래스 : 객체를 생성하기 위한 틀
  - 클래스는 속성과 기능으로 정의됨
- 프로그래밍적 관점

  1. **클래스-데이터와 함수의 결합**
     - 서로 관련된 변수들을 정의 → 이들에 대한 작업을 수행하는 함수들을 함께 정의하는 것.
     - c언어 → 문자열을 문자의 배열로 다루지만, 자바에서는 String이라는 클래스로 문자열을 다룬다.
       - 문자열을 단순히 문자의 배열로 정의하지 않고, 클래스로 정의한 이유는 문자열과 문자열을 다루는 데 필요한 함수들을 함께 묶기 위해서임.
  2. **클래스-사용자정의 타입**

     - 제공하는 자료형 외에 서로 관련도니 변수들을 묶어 하나의 타입으로 새로 추가하는 것 = 사용자 정의 타입.
     - 객체지향언어에서는 클래스 == 사용자 정의 타입.
     - 기본형의 개수가 8개로 정해져 있음. 참조형의 개수가 정해져 있지 않은 이유 → 프로그래머가 새로운 타입 추가 가능.
     - e.g) 시간 표현

     시, 분, 초를 하나로 묶는 사용자 정의 타입, **클래스를 정의해 사용**

     ```java
     class Time{
     	int hour;
     	int minute;
     	float second;
     }
     ```

     - 시, 분, 초를 저장하기 위한 세 변수를 멤버변수로 갖는 Time 클래스 정의
     - 시간 데이터에 추가적인 제약조건이 있다면?

       1. 시, 분, 초는 모두 0보다 크거나 같아야 함
       2. 시의 범위는 0~23, 분과 초의 범위는 0~59.
          → 객체지향언어가 아닌 언어에서는 이러한 추가적인 조건 반영이 어렵지만, 객체지향언에서는 제어자와 메서드를 이용해 조건들을 코드에 반영 가능

       ```java
       public class Time {
           private int hour;
           private int minute;
           private float second;

           public int getHour() {
               return hour;
           }

           public int getMinute() {
               return minute;
           }

           public float getSecond() {
               return second;
           }

           public void setHour(int h) {
               if (h < 0 || h > 23) return;
               hour = h;
           }

           public void setMinute(int m) {
               if (m < 0 || m > 59) return;
               minute = m;
           }

           public void setSecond(int s) {
               if (s < 0.0f || s > 59.99f) return;
               second = s;
           }
       }
       ```

       - 제어자를 이용해 변수의 값 직접 변경 ❌
       - 메서드를 통해 값 변경하도록
       - 값을 변경할 때 지정된 값의 유효성을 조건문으로 점검한 후 유효한 값일 때만 변경.

# 3. 변수와 메서드

## 3.1 선언위치에 따른 변수의 종료

- 변수는 **클래스 변수**, **인스턴스 변수**, **지역 변수** 모두 3종류가 있음.
- 변수의 종류는 `선언된 위치` 에 따라 결정됨.
- 변수의 종류를 파악하기위해서는 변수가 어느 영역에 선언되었는지 확인하는 것이 중요함.

```java
class Variables{
	int iv; // 인스턴스 변수
	static int cv; // 클래스 변수(static변수, 공유변수)

	void method(){
		int lv = 0; // 지역 변수
	}
}
```

| 변수의 종류                       | 선언위치                    | 생성시기                    |
| --------------------------------- | --------------------------- | --------------------------- |
| 클래스변수                        | 클래스 영역                 | 클래스가 메모리에 올라갈 때 |
| 인스턴스변수                      | 클래스 영역                 | 인스턴스가 생성되었을 때    |
| 지역변수                          | 클래스 영역 이외의 영역     |
| (메서드, 생성자, 초기화블록 내부) | 변수 선언문이 수행되었을 때 |

1. **인스턴스 변수**

- 클래스 영역에 선언
- 클래스의 인스턴스를 생성할 때 만들어짐
- 인스턴스 변수의 값을 읽어 오거나 저장하기 위해서는 먼저 인스턴스 생성
- 독립적인 저장공간 → 서로 다른 값 가질 수 있음.

1. **클래스 변수**

- 클래스 변수를 선언 하는 방법: 인스턴스 변수 앞에 **static** 붙임
- 인스턴스 마다 독립적인 저장공간을 갖는 인스턴스 변수와는 달리, 클래스 변수는 **모든 인스턴스가 공통된 저장공간(변수)을 공유**
- 한 클래스의 **모든 인스턴스들이 공통적인 값을 유지**해야 하는 속성인 경우 클래스 변수 사용
- 인스턴스 생성하지 않고도 언제라도 바로 사용 가능
- `클래스이름.클래스변수` 와 같은 형식
- 메모리에 로딩될 때 생성 → 프로그램 종료될 때까지 유지
- `public` 을 앞에 붙이면, 어디서나 접근 가능한 전역변수의 성격을 가짐

1. **지역 변수**

- 메서드 내에 선언되어 메서드 내에서만 사용 가능
- 메서드가 종료되면 소멸되어 사용 불가
- for문, while문 안에 선언된 지역변수 → 지역변수가 선언된 `블록 {}` 내에서만 사용 가능.
- `블록 {}` 을 벗어나면 소멸되어 사용 불가.

## 3.2 클래스 변수와 인스턴스 변수

- 차이를 이해하기 위한 예로 `카드 게임`에 사용되는 카드를 **클래스로 정의**
- 카드게임 → 클래스
  - 카드를 분석해 **속성, 기능**을 알아내야 함.
- 속성: 카드 무늬, 숫자, 폭, 높이
- 어떤 속성을 `클래스 변수` vs `인스턴스 변수` ?

  - 각 Card인스턴스는 자신만의 무늬(kind)와 숫자(number)를 유지 → 인스턴스 변수
  - 각 카드의 폭(width), 높이(height) - 모든 인스턴스가 공통적으로 같은 값을 유지해야 → 클래스 변수

    - 카드의 폭을 변경해야할 필요가 있을 경우 → 모든 카드의 width 값을 변경하지 않고 한 카드의 width값만 변경해도 모든 카드의 width가 변경되는 셈!

    ```java
    public class CardTest {
        public static void main(String[] args) {
            System.out.println("Card.width=" + Card.width);
            System.out.println("Card.height=" + Card.height);

            Card c1 = new Card();
            c1.kind = "Heart";
            c1.number = 7;

            Card c2 = new Card();
            c2.kind = "Space";
            c2.number = 4;

            System.out.println("c1은 " + c1.kind + ", " + c1.number + "이며, 크기는 (" + c1.width + ", " + c1.height + ") ");
            System.out.println("c2는 " + c2.kind + ", " + c2.number + "이며, 크기는 (" + c2.width + ", " + c2.height + ") ");
            System.out.println("c1의 width, height를 각각 50, 80으로 변경합니다.");
            c1.width = 50;
            c1.height = 80;

            System.out.println("c1은 " + c1.kind + ", " + c1.number + "이며, 크기는 (" + c1.width + ", " + c1.height + ") ");
            System.out.println("c2는 " + c2.kind + ", " + c2.number + "이며, 크기는 (" + c2.width + ", " + c2.height + ") ");

        }
    }

    class Card {
        // 인스턴스 변수
        String kind;
        int number;
        // 클래스 변수
        static int width = 100;
        static int height = 250;
    }
    ```

    - Card 클래스의 클래스변수인 width, height는 Card 클래스의 인스턴스를 생성하지 않고도 `클래스.클래스변수` 와 같은 방식으로 사용 가능
    - Card인스턴스인 c1, c2는 클래스변수인 width, height를 공유 → c1 변경시 c2도 바뀜.
    - `Card.width`, `c1.width`, `c2.width` 는 모두 같은 저장공간 참조 → 항상 같은 값 가짐.

> 인스턴스 변수는 인스턴스가 생성될 때마다 생성되므로 인스턴스마다 각기 다른 값을 유지할 수 있지만, 클래스 변수는 모든 인스턴스가 하나의 저장공간을 공유 → 항상 공통된 값 가짐.

## 3.3 메서드

- 특정 작업을 수행하는 일련의 문장들을 하나로 묶은 것.
- 넣을 값(입력)과 반환하는 결과(출력)만 알면 됨.
  - 메서드 == 블랙박스라고 하는 이유.
- println(), random()과 같은 메서드들 역시 내부적으로 어떻게 동작하는지 몰라도 사용하는데 어려움 없었음.

### 메서드를 사용하는 이유

1. **높은 재사용성**
   - 이미 Java API에서 제공하는 메서드들을 사용하면서 경험한 것처럼 한번 만들어놓은 메서드는 몇번이고 호출 가능.
2. **중복된 코드 제거**
   - 같은 내용의 문장들이 여러곳에 반복해서 나타나곤 함.
   - 반복되는 문장 → 하나의 메서드로 작성 → 반복되는 문장들 대신 메서드를 호출하는 한 문장으로 대체 가능
   - 전체 소스코드의 길이가 짧아지고, 변경사항 발생 시 수정해야 할 코드의 양도 줄음 → 오류 발생 가능성 낮아짐.
3. **프로그램의 구조화**

   - 큰 규모의 프로그램 → 문장들을 작업단위로 나눠 여러 개의 메서드에 담아 프로그램의 구조를 단순화 시키는 것이 필수적.
   - main 메서드는 프로그램의 전체 흐름이 한눈에 들어올 정도로 **단순하게 구조화**하는 것이 좋음.
   - 처음에 프로그램을 설계시) 내용이 없는 메서드를 작업단위로 만듦 → 하나씩 완성시키는 것도 프로그램을 구조화하는 좋은 방법.

     - 성적처리 프로그램 설계

       ```java
       public class GradeProcess {
           static int showMenu() { /* 나중에 내용을 완성한다. */ }

           static void inputRecord() { /* 나중에 내용을 완성한다. */ }

           static void changeRecord() { /* 나중에 내용을 완성한다. */ }

           static void deleteRecord() { /* 나중에 내용을 완성한다. */ }

           static void searchRecord() { /* 나중에 내용을 완성한다. */ }

           static void showRecordList() { /* 나중에 내용을 완성한다. */ }

           public static void main(String[] args) {
               // ...
               switch (showMenu()) {
                   case 1:
                       inputRecord();
                       break; // 데이터를 입력받는 메서드
                   case 2:
                       changeRecord();
                       break; // 데이터를 변경하는 메서드
                   case 3:
                       deleteRecord();
                       break; // 데이터를 삭제하는 메서드
                   case 4:
                       searchRecord();
                       break; // 데이터를 검색하는 메서드
                   default:
                       showRecordList(); // 데이터의 목록을 보여주는 메서드
               }
           }
       }
       ```

## 3.4 메서드의 선언과 구현

- 메서드는 크게 두 부분, `선언부(header)`, `구현부(body)` 로 이뤄짐.

### 메서드 선언부(method declaration, method header)

- `메서드 이름`, `매개변수 선언`그리고 `반환 타입` 으로 구성됨.
- 메서드가 작업을 수행하기 위해 어떤 값들을 필요로 하고 작업의 결과로 어떤 타입의 값을 반환하는지에 대한 정보 제공

  - e.g.) 메서드 add: 두개의 정수를 입력받아→ 두 값을 더한 결과(int)를 반환

    ```java
    int add (int x, int y){ // 반환 타입, 메서드 이름, 매개변수 선언(입력)
    	int result = x + y;

    	return result;

    }
    ```

- 메서드의 선언부는 후에 변경사항이 발생하지 않도록 신중히 작성해야 함.
- 메서드의 선언부를 변경 → 그 메서드가 호출되는 모든 곳도 같이 변경됨.

### 매개변수 선언(parameter declaration)

- 메서드가 작업을 수행하는 데 필요한 값들(입력)을 제공받이 위함.
- 필요한 값의 개수만큼 변수를 선언 → 각 변수간 구분은 쉼표(,)
- 주의) 일반적인 변수선언과 달리 두 변수의 타입이 같아도 변수의 타입을 생략 불가.

### 메서드 이름(method name)

- 변수의 명명 규칙을 따름
- 특정 작업 수행 → **동사**인 경우가 많음.
- 이름만으로도 메서드의 기능을 쉽게 알 수 있도록 함축적이면서 의미있는 이름을 짓도록.

### 반환타입(return type)

- 메서드 작업수행 결과(출력)인 반환값의 타입을 적는다.
- 반환값이 없는 경우 반환타입으로 `void를 적어야 함`

### 메서드의 구현부(method body)

- 선언부 다음에 오는 괄호{}를 구현부
- 메서드를 호출했을 때 수행될 문장을 넣음

### return문

- 메서드의 반환타입이 void가 아닐경우 구현부{} 안에 `return 반환값` 이 반드시 포함되어야!
- 작업을 수행한 결과인 `반환값` 을 호출한 메서드로 전달 → 이 값의 타입은 **반환타입과 일치하거나 적어도 자동 형변환이 가능한 것**이어야 함.
- return 문은 단 하나의 값만 반환 가능.

### 지역변수

- 메서드 내에 선언된 변수들은 메서드 내에서만 사용 가능
- **메서드 내**에 선언된 변수 == 지역변수.

## 3.5 메서드의 호출

- 메서드를 정의 → 호출 ❌ → 아무일도 일어나지 ❌
- 메서드 호출 ⭕️ → 구현부 {} 문장 수행
- 메서드 호출 방법
  `메서드이름(값1, 값2, ....)`
  e.g) print99danAll(); // void print99danAll() 호출.
  int result = add(3,5) // int add(int x, int y)를 호출 후 결과를 result에 저장.

### 인자(argument)와 매개변수(parameter)

- 메서드 호출 시 괄호() 안에 지정해준 값들을 `인자` or `인수`라고 함
- 이때 **인자의 개수, 순서** → 호출된 메서드에 **선언된 매개변수**와 일치해야.

인자 → **메서드가 호출**되면서 **매개변수에 대입** → 인자의 타입은 매개변수 타입과 일치 or 자동형변환 가능해야.

  <img width="333" alt="object_oriented_1" src="https://user-images.githubusercontent.com/71822139/216500912-e5e53989-cade-4375-8878-4a952af21426.png">

- 메서드에 선언된 매개변수의 개수보다 많은 값을 괄호()에 넣거나 타입이 다른 값을 넣으면 컴파일러가 **에러 발생시킴.**
- 반환 타입이 void 가 아닌경우 → 메서드가 작업을 수행 → 반환한 값을 대입연산자로 변수에 저장, but 저장하지 않아도 문제 ❌

### 메서드의 실행흐름

- **같은 클래스 내**의 메서드끼리는 참조변수를 사용 하지 않아도 → 서로 호출 가능
- **static** 메서드 → 같은 클래스 내의 인스턴스 메서드 호출 ❌
- 두개의 값을 매개변수로 받아서 사칙연산 수행하는 4개의 메서드를 가진 MyMath 클래스

  ```java
  class MyMath {
  	long add(long a, long b){
  			long result = a+b;
  			return result;
  //			return a+b; // 위의 두줄을 이와 같이 한줄로 간단히 표현 가능
  	long subtract(long a, long b) { return a-b; }
  	long multiply(long a, long b) { return a*b; }
  	double divide(double a, double b) { return a/b; }
  }
  ```

  MyMath 클래스의 `add(long a, long b)`를 호출하기 위해서는,

  → 먼저 `MyMath mm = new MyMath();` 와 같이 해서 **MyMath의 인스턴스를 생성** → 참조 변수 `mm`을 통해야 함.

    <img width="308" alt="object_oriented_2" src="https://user-images.githubusercontent.com/71822139/216500914-24b91cf7-47a5-49a8-8067-3816927cf423.png">

  1️⃣ main메서드에서 메서드 add 호출 → 호출시 지정한 1L, 2L이 메서드 add의 매개변수 a,b 에 각각 복사(대입)

  2️⃣ 메서드 add의 괄호{} 안에 있는 문장들이 순서대로 수행

  3️⃣ 메서드 add의 모든 문장이 실행 or return 문을 만나면 → 호출한 메서드(main)로 되돌아와서 이후 문장 수행.

  - 메서드 add의 호출결과가 value에 저장되는 것이 아닌, 사실은 `호출한 자리를` **반환값**이 대신
  - 대입연산자에 의해 이 값이 value에 저장됨.
    e.g) long value = **add(1L, 2L)**;
    long value = **3L**;
  - add 메서드의 매개변수 타입이 long이므로 **long** 또는 **long으로 자동형변환이 가능한 값**을 지정해야 함.
  - 호출시 매개변수로 지정된 값은 메서드의 매개변수로 복사..
  - 1L, 2L의 값이 long 타입의 매개변수 a, b에 각각 복사됨.
  - 메서드는 호출시 넘겨받은 값으로 연산 수행. 결과를 반환 → 종료.
  - 메서드의 결과를 저장하기 위한 변수 **value 역시 반환값과 같은 타입** or **자동형변환 되어 저장될 수 있는 타입**이어야.

```java
double result4 = mm.divide(5L, 3L);
double divide(double a, double b){
	return a/b;
}
```

- divide 메서드에 선언된 매개변수 타입은 double형인데, 이와 다른 long형의 값인 5L과 3L을 사용해서 호출하는 것이 가능함.
- **메서드 호출 시에 입력된 값**은 메서드의 **매개변수에 대입되는 값**임.
- long형의 값을 double형 변수에 저장하는 것과 같음
  - `double a = 5L`을 수행 했을 때와 같이 long형의 값인 5L은 double형 값인 5.0으로 **자동 형변환**되어 divide의 매개변수 a에 저장됨.
  - 그래서 divide 메서드에 두 개의 정수값(5L, 3L)을 입력해 호출하였음에도 불구하고, 연산결과가 double형의 값이 됨.

## 3.6 return 문

- return문: 현재 실행중인 메서드 종료 → 호출한 메서드로 되돌아감.
- 반환값의 유무에 관계없이 모든 메서드에는 적어도 하나의 return 문이 있어야 함.
- 반환값이 void → 컴파일러가 메서드의 마지막에 `return;` 을 자동적으로 추가
- 반환타입이 void가 아닌경우 → **반드시 return문이 있어야** 함.
  - 없으면 컴파일에러 발생.
  - if문의 조건식의 결과에 따라 return문이 실행되지 않을 경우도 고려해야 함.
    - if문의 else블록에 return 문 추가 → 항상 결과값이 반환되도록.

### 반환값

- return 문의 반환값으로 주로 변수가 옴 → but 항상 ❌
  e.g.
  ```java
  int add( int x, int y){
  	return x+y
  }
  ```
  - 예를 들어 매개변수 x와 y의 값이 각각 3, 5
    - `return x+ y`
    - `return 3+5`
    - `return 8`
    - 반환값 = 8
- 간단한 메서드의 경우 if문 대신 조건연산자 사용
  - 메서드 abs → 입력받은 정수의 부호를 판단해 음수일 경우 부호연산자(-)를 사용해 양수로 반환.
  ```java
  int abs(int x){
  	return x>=0 ? x: -x;
  }
  ```

### 매개변수의 유효성 검사

- 메서드의 구현부{} 를 작성할 때, 제일 먼저 해야 하는 일: 매개변수의 값이 적절한 것인지 확인하는 것.
- “호출하는 쪽에서 알아서 적절한 값을 넘겨주겠지” 라는 생각은 절대로 ❌
- 타입만 맞으면 어떤 값도 매개변수를 통해 넘어올 수 있음.
- 가능한 모든 경우의 수에 대해 고민하고 대비한 코드를 작성해야 함.
  ```java
  float divide(int x, int y){
  	// 작업을 하기 전에 나누는 수(y)가 0인지 확인
  	if/(y==0){
  		System.out.println("0으로 나눌 수 없습니다.");
  		return 0;
  	}
  	return x/(float)y;
  }
  ```
- 적절하지 않은 값이 매개변수를 통해 넘어온다면 매개변수의 값을 보정 or 보정하는 것이 불가 → return 문을 사용해 작업을 중단, 호출한 메서드로 되돌아가야함
- 메서드 작성 → 매개변수의 유효성 검사를 반드시 넣어야 함.
  - 메서드 작성에 있어서 간과하기 쉬운 중요한 부분임.

## 3.7 JVM의 메모리 구조

- 응용프로그램이 실행 → JVM은 시스템으로부터 프로그램을 수행하는데 필요한 메모리 할당 → JVM은 이 메모리를 용도에 따라 여러 영역으로 나눠 관리.
- 3가지 주요 영역
  - method area, call stack, heap
    <img width="282" alt="jvm_memory_structure" src="https://user-images.githubusercontent.com/71822139/216500749-5ccd0a6d-8437-4a76-b8ad-b39621997202.png">
        cv: 클래스 변수 lv: 지역변수, iv: 인스턴스 변수
  1. 메서드 영역(method area)
     - 프로그램 실행 중 어떤 클래스가 사용되면, JVM은 해당 클래스의 클래스파일(\*.class)을 읽어서 분석 → 클래스에 대한 정보(클래스 데이터)를 이곳에 저장.
     - 클래스변수도 이 영역에 함께 생성
  2. 힙(heap)
     - 인스턴스가 생성되는 공간
     - 프로그램 실행 중 생성되는 인스턴스 → 모두 heap에 저장됨.
     - 인스턴스 변수가 생성되는 공간.
  3. 호출스택(call stack)
     - 메서드 작업에 필요한 메모리 공간 제공
     - 메서드 호출 → 호출스택에 호출된 메서드를 위한 메모리 할당
     - 메서드가 작업을 수행하는 동안 지역변수들과 연산의 중간결과 등에 저장.
     - 메서드가 작업을 마치면 할당되었던 메모리 공간 반환 → 지워짐
- 각 메서드를 위한 메모리 상의 작업공간 → 서로 구별
- 첫번째로 호출된 메서드를 위한 작업공간이 호출스택의 맨 밑에 마련.
  - 첫번째 메서드 수행 중 다른 메서드 호출 → 첫번째 메서드의 바로 위에 두번째 호출된 메서드를 위한 공간 마련.
  - 첫번째 메서드 → 수행 멈춤 → 두번째 메서드 수행 시작 → 수행 끝 → 두번째 메서드의 호출스택 메모리 공간 반환
  - 첫번째 메서드 → 다시 수행 시작 → 수행 끝 → 첫번째 메서드의 호출스택 메모리 공간 반환.

### 호출 스택 특징

- 메서드 호출 → 수행에 필요한 만큼의 메모리를 스택에 할당
- 메서드 수행 끝 → 사용했던 메모리 반환 → 스택에 제거
- 호출스택의 제일 위에 있는 메서드 → 현재 실행 중인 메서드
- 아래에 있는 메서드 → 바로 위의 메서드를 호출한 메서드

## 3.8 기본형 매개변수와 참조형 매개변수

- 메서드 호출 → 매개변수로 지정한 값 → 메서드의 매개변수에 복사해 넘겨줌.
- 매개변수 타입이 기본형(primitive type)일 경우
  - 기본형 **값 복사**
- 참조형(reference type)일 경우
  - 인스턴스 **주소 복사**
- 메서드의 매개벼수를 기본형 선언 → 단순히 저장된 값만 얻음
- 참조형 선언 → 저장된 곳의 주소를 알기 때문에 → 값 읽어오는 건 물론 값 변경 가능
- 기본형 매개변수: 변수의 값을 읽기만 가능(read only)
- 참조형 매개변수: 변수의 값을 읽고 변경할 수 있음(read&write)

> 예제-1

```java
class Data {
    int x;
}

public class PrimitiveParamEx {
    public static void main(String[] args) {
        Data d = new Data();
        d.x = 10;
        System.out.println("main():x= " + d.x);

        change(d.x);
        System.out.println("After change(d.x)");
        System.out.println("main():x= " + d.x);
    }
    static void change(int x) { // 기본형 매개변수
        x = 1000;
        System.out.println("change(): x=" + x);
    }
}
```

- change메서드에서 main메서드로부터 넘겨받은 d.x의 값을 1000으로 변경했는데도 main메서드에서는 d.x의 값이 그대로
- d.x의 값이 변경된 것이 아니라, change 메서드의 매개변수 x의 값이 변경된 것.
- 즉, 원본이 아닌 복사본이 변경
- → 기본형 매개변수는 변수에 저장된 값만 읽을 수만 있을 뿐 변경 불가

> 예제-2

```java
class Data {
    int x;
}

public class ReferenceParamEx {
    public static void main(String[] args) {
        Data d = new Data();
        d.x = 10;
        System.out.println("main() : x = " + d.x);

        change(d);
        System.out.println("After change(d)");
        System.out.println("main() : x = " + d.x);
    }

    static void change(Data d) { // 기본형 매개변수
        d.x = 1000;
        System.out.println("change() : x = " + d.x);
    }
}
```

- 예제-1 과 달리 change메서드를 호출한 후에 d.x의 값이 변경됨 → change메서드의 매개변수를 참조형으로 선언함.
- change메서드의 매개변수가 참조형이라서 값이 아니라 `값이 저장된 주소` 를 change메서드에 넘겨주었기 때문에 값을 읽어오는 것뿐 아니라 변경하는 것도 가능
- main메서드의 참조변수 d와 change의 메서드의 참조변수 d는 같은 객체 가르킴 → 매개변수 d로 x의 값을 읽는 것과 변경하는 것 모두 가능

> 예제-3

```java
public class ReferenceParamEx2 {
    public static void main(String[] args) {
        int[] x = {10}; // 크기가 1인 배열. x[0]=10;
        System.out.println("main() : x=" + x[0]);
        change(x);
        System.out.println("After change(d)");
        System.out.println("main() : x = " + x[0]);
    }

    static void change(int[] x) { // 참조형 매개변수
        x[0] = 1000;
        System.out.println("change(): x=" + x[0]);
    }
}
```

- 이전의 참조형 매개변수 예제를 Data 클래스의 인스턴스 대신 길이가 1인 배열 x를 사용하도록 변경.
- 배열도 객체와 같이 참조변수를 통해 데이터가 저장된 공간에 접근함.
- 임시적으로 간단히 처리할 때는 별도의 클래스를 선언하는 것보다 이처럼 배열을 사용

> 예제-4

```java
public class ReferenceParamEx3 {
    public static void main(String[] args) {
        int[] arr = new int[]{3, 2, 1, 6, 5, 4};
        printArr(arr);
        sortArr(arr);
        printArr(arr);
        System.out.println("sum="+sumArr(arr));
    }

    static void printArr(int[] arr) { // 배열 모든 요소 출력
        System.out.print("[");
        for (int i : arr)
            System.out.print(i + ", ");
        System.out.println("]");
    }

    static int sumArr(int[] arr) { // 배열 모든 요소의 합을 반환
        int sum = 0;
        for (int i = 0; i < arr.length; i++)
            sum += arr[i];
        return sum;
    }

    static void sortArr(int[] arr) { // 배열 모든 요소 오름차순 정렬
        for (int i = 0; i < arr.length; i++)
            for (int j = 0; j < arr.length-1-i; j++)
                if (arr[j] > arr[j + 1]) {
                    int tmp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = tmp;
                }
    } // sortArr(int[] arr)
}
```

- 메서드로 배열을 다루는 여러가지 방법
- 매개변수의 타입이 배열이니까 참조형 매개변수임.
- 따라서 sortArr 메서드에서 정렬한 것이 원래의 배열에 영향을 미친다.

예제-5

```java
public class ReturnTest {
    public static void main(String[] args) {
        ReturnTest r = new ReturnTest();

        int result = r.add(3, 5);
        System.out.println(result); // 8

        int[] result2 = {0};
        r.add(3, 5, result2);
        System.out.println(result2[0]); // 8
    }

    int add(int a, int b) {
        return a + b;
    }

    void add(int a, int b, int[] result) {
        result[0] = a + b;
    }
}
```

- 반환값이 있는 메서드를 반환값이 없는 메서드로 바꿈.
- 앞에 배운 참조형 매개변수를 활용하면 반환값이 없어도 메서드의 실행결과를 얻어 올 수 있음
- 메서드는 단 하나의 값만 반환할 수 있지만, 이걸 응용하면 여러 개의 값을 반환받는 것과 같은 효과

## 3.9 참조형 반환타입

- 매개변수 뿐만 아니라 반환타입도 참조형 가능
- 모든 참조형 타입의 값은 `객체의 주소` 이므로 그저 정수값이 반환되는 것일뿐 특별할 것이 없음.

```java
class Data {
    int x;
}

public class ReferenceReturnEx {
    public static void main(String[] args) {
        Data d = new Data();
        d.x = 10;
        Data d2 = copy(d);
        System.out.println("d.x=" + d.x); // 10
        System.out.println("d2.x=" + d2.x); // 10
    }

    static Data copy(Data d) {
        Data tmp = new Data();
        tmp.x = d.x;

        return tmp;
    }
}
```

- copy 메서드는 새로운 객체를 생성 → 매개변수로 넘겨받은 객체에 저장된 값을 복사해서 반환
- 반환하는 값이 Data객체의 주소 → 반환 타입이 Data임.
- 호출결과를 저장하는 변수의 타입 역시 `Data` 타입의 참조변수이어야 함.

`Data d2 = copy(d);`

- copy메서드 내에서 생성한 객체를 main메서드에서 사용할 수 있으려면, 이렇게 새로운 객체의 주소를 반환해주어야 함.
- 그렇지 않으면, copy 메서드 종료 → 새로운 객체의 참조 사라짐 → 객체 사용 불가.

## 3.10 재귀호출(recursive call)

- 메서드 내부에서 메서드 자신을 다시 호출하는 것.
- 재귀호출을 하는 메서드==**재귀메서드**
- 호출된 메서드는 `값에 의한 호출` 을 통해, 원래의 값이 아닌 복사된 값으로 작업 → 호출된 메서드와 관계없이 독립적인 작업수행 가능.
- 재귀호출은 반복문과 유사한 점이 많으며, 대부분의 재귀호출은 반복문으로 작성 가능.
- 반복문은 그저 같은 문장 반복, but 메서드를 호출 → 반복문보다 몇 가지 과정, 예를 들면 매개변수 복사와 종료 후 복귀할 주소 저장 등, 이 추가로 필요 → 반복문 보다 재귀호출의 수행시간이 더 오래 걸림
- 반복문 대신 재귀호출을 사용 하는 이유 → **논리적 간결함**
- 다소 비효율적이라도 알아보기 쉽게 작성 → 논리적 오류가 발생할 확률 ↓, 수정 용이
- 어떤 작업을 반복적으로 처리 → 반복문으로 작성 후 재귀호출로 간단하게 할 수 없는지 고민.
  - 재귀호출은 비효율적 → 재귀호출에 드는 비용보다 재귀호출의 간결함이 주는 이득이 충분히 큰 경우에만 사용.

> 대표적인 재귀호출 예-팩토리얼

```java
public class FactorialTest {
    public static void main(String[] args) {
        int result = factorial(4);
        System.out.println(result);
    }

    static int factorial(int n) {
        int result = 0;
        if (n == 1)
            result = 1;
        else
            result = n * factorial(n - 1);
        return result;
    }
}
```

- 팩토리얼을 계산하는 메서드 구현 → 테스트
- factorial 메서드가 **static** 메서드이므로 인스턴스를 생성하지 않고 직접 호출 가능
- main메서드와 같은 클래스에 있으므로 static메서드 호출 시 클래스 이름 생략 가능.
- `FactorialTest.factorial(4)` 대신 `factorial(4)` 로

> 이전 예제에 매개변수 유효성 검사하는 코드 추가

```java
public class FactorialTest2 {
    static long factorial(int n) {
        if (n <= 0 || n > 20) return -1; // 매개변수 유효성 검사
        if (n <= 1) return 1;
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {
        int n = 21;
        long result = 0;
        for (int i = 1; i <= n; i++) {
            result = factorial(i);
            if (result == -1) {
                System.out.printf("유효하지 않은 값입니다. (0<n<=20): %d%n", n);
                break;
            }
            System.out.printf("%2d!=%20d%n", i, result);
        }
    }
}
```

> x^1부터 x^n까지의 합을 구하는 예제.

```java
public class PowerTest {
    public static void main(String[] args) {
        int x = 2;
        int n = 5;
        long result = 0;
        for (int i = 1; i <= n; i++) {
            result += power(x, i);
        }
        System.out.println(result);
    }

    static long power(int x, int n) {
        if (n == 1) return x;
        return x * power(x, n - 1);
    }
}
```

- 재귀호출을 사용해 x^n을 구하는 power() 메서드.
- 메서드 정의에 자신을 포함하는 재귀 메서드 임.
- 이 메서드도 재귀호출이 아닌 반복문으로 처리가능.

## 3.11 클래스 메서드(static 메서드)와 인스턴스 메서드

- 메서드 앞에 static → 클래스 메서드
- 클래스 정의 시 어느 경우에 static 사용?
- 클래스는 데이터(변수)와 데이터에 관련된 메서드의 집합.
  - 같은 클래스 내에 있는 메서드와 멤버변수는 아주 밀접한 관계.
- 인스턴스 메서드 → 인스턴스 변수와 관련된 작업을 하는, 즉 메서드의 작업을 수행하는 데 **인스턴스 변수를 필요로 하는 메서드**
- 인스턴스 변수는 인스턴스(객체)를 생성해야만 만들어짐.
  - 인스턴스 메서드 **역시 인스턴스를 생성해야만** 호출할 수 있음.
- 메서드 중에서 인스턴스와 관계없는(인스턴스 변수나 인스턴스 메서드 사용 x) 메서드 → 클래스 메서드(static 메서드)로 정의.
- 물론 인스턴스 변수를 사용하지 않는다고 해서 반드시 클래스 메서드로 정의해야 하는 건 아니지만, 특별한 이유가 없는 한 그렇게 하는 게 일반적임.

1. **클래스 설계 시 멤버변수 중 모든 인스턴스에 공통으로 사용하는 것에 static 붙임.**
   - 생성된 각 인스턴스는 서로 독립적
   - 각 인스턴스의 변수는 서로 다른 값 유지
     - **모든 인스턴스에서 같은 값이 유지**되어야 하는 변수 → **static 붙여 클래스변수로 정의**
2. **클래스 변수는 인스턴스를 생성하지 않아도 사용 가능**
   - static이 붙은 변수는 클래스가 메모리에 올라갈 때 이미 자동적으로 생성.
3. **클래스 메서드는 인스턴스 변수 사용 불가.**
   - 인스턴스변수는 인스턴스가 반드시 존재해야만 사용가능
   - 클래스메서드는 인스턴스 생성없이 호출 가능 → 클래스 메서드가 호출 → 인스턴스가 존재하지 않을 수 있음 ⇒ 클래스 메서드에서 인스턴스변수 사용 금지.
   - but, 인스턴스 변수나 인스턴스 메서드에서는 **static가 붙은 멤버들을 사용하는 것이 언제나 가능**
   - 인스턴스 변수가 존재 → static 변수가 이미 메모리에 존재.
4. 메서드 내에서 인스턴스 변수를 사용하지 않는다면, static를 붙이는 걸 고려.
   - 메서드의 작업 내용 중 인스턴스 변수를 필요로 한다면, static 붙일 수 없음.
   - 그러나 인스턴스 변수를 필요로 하지 않는다면 static을 붙이자
   - 메서드 호출시간이 짧아지므로, 성능 향상.
   - static을 안 붙인 메서드 → 실행 시 호출되어야 할 메서드를 찾는 과정이 추가적으로 필요함 → 시간이 더 걸림.

예제-인스턴스메서드

```java
class MyMath2 {
    long a, b;

    // 인스턴스변수 a,b만을 이용해 작업 -> 매개변수 필요 x
    long add() {
        return a + b;
    }

    long subtract() {
        return a - b;
    }

    long multiply() {
        return a * b;
    }

    double divide() {
        return a / b;
    }

    // 인스턴스변수와 관계없이 매개변수만으로 작업 가능
    static long add(long a, long b) {
        return a + b;
    } // a,b는 지역변수

    static long subtract(long a, long b) {
        return a - b;
    }

    static long multiply(long a, long b) {
        return a * b;
    }

    static double divide(double a, double b) {
        return a / b;
    }
}

public class MyMathTest2 {
    public static void main(String[] args) {
        // 클래스메서드 호출. 인스턴스 생성없이 호출가능
        System.out.println(MyMath2.add(200L, 100L));
        System.out.println(MyMath2.subtract(200L, 100L));
        System.out.println(MyMath2.multiply(200L, 100L));
        System.out.println(MyMath2.divide(200.0, 100.0));

        MyMath2 mm = new MyMath2(); // 인스턴스 생성
        mm.a = 200L;
        mm.b = 100L;
        // 인스턴스 메서드는 객체생성 후에만 호출 가능
        System.out.println(mm.add());
        System.out.println(mm.subtract());
        System.out.println(mm.multiply());
        System.out.println(mm.divide());
    }
}
```

- 인스턴스 메서드인 add(), subtract(), multiply(), divide()는 인스턴스 변수인 a와 b만으로도 충분히 작업 가능. 매개변수 필요 x → 괄호()에 매개변수 선언 x
- but, `add(long a, long b)`, `subtract(long a, long b)`등은 **인스턴스 변수**없이 매개변수만으로 작업 수행 → **static**을 붙여 **클래스 메서드**로 선언.
- main 메서드 → **클래스 메서드**는 객체생성없이 바로 호출 가능
- 인스턴스 메서드 → MyMath2클래스의 인스턴스를 생성한 후에야 호출 가능

## 3.12 클래스 멤버와 인스턴스 멤버간의 참조와 호출

- 같은 클래스에 속한 멤버들 간에는 **별도의 인스턴스 생성 x**
- 서로 참조 또는 호출 가능.
- 단 **클래스 멤버**가 **인스턴스 멤버**를 참조 또는 호출하고자 하는 경우 → 인스턴스 생성해야 함
- 인스턴스 멤버(인스턴스 변수, 메서드)가 존재하는 시점에 클래스 멤버는 항상 존재
- but 클래스 멤버가 존재하는 시점→ 인스턴스 변수 없을 수도 있음.

```java
public class TestClass {
    void instanceMethod() {
    } // 인스턴스메서드

    static void staticMethod() {
    } // static 메서드

    void instanceMethod2() { // 인스턴스메서드
        instanceMethod(); // 다른 인스턴스메서드 호출
        staticMethod(); // static메서드 호출
    }

    static void staticMethod2() { // static 메서드
        // instanceMethod(); // 에러!! 인스턴스 변수 사용 불가
        // Non-static method 'instanceMethod()' cannot be referenced from a static context
        staticMethod(); // static 메서드 호출 가능
    }
}
```

- 같은 클래스 내의 메서드 → 서로 객체의 생성 or 참조변수 없이 직접 호출 가능
- but, static 메서드 → 인스턴스 메서드 호출 불가.

```java
public class TestClass2 {
    int iv; // 인스턴스 변수
    static int cv; // 클래스 변수

    void instanceMethod() { // 인스턴스 메서드
        System.out.println(iv); // 인스턴스 변수 사용 가능
        System.out.println(cv); // 클래스 변수 사용 가능
    }

    static void staticMethod() { // 클래스 메서드
        System.out.println(iv); // 인스턴스 변수 사용 불가
        // Non-static field 'iv' cannot be referenced from a static context
        System.out.println(cv); // 클래스 변수 사용 가능
    }
}
```

변수와 메서드간의 호출

- 메서드 간의 호출과 마찬가지로 인스턴스메서드 → 인스턴스변수 사용 가능
- but, static 메서드에서는 인스턴스 변수 사용 불가.

- 클래스 멤버 → 언제나 참조, 호출 가능
- 인스턴스 멤버 → 클래스 멤버 사용 ok
- but, 인스턴스 멤버는 반드시 객체를 생성한 후에만 참조 or 호출 가능 → **클래스 멤버가 인스턴스 멤버를 참조, 호출** → **객체 생성**해야 함.
- 인스턴스멤버 간의 호출 → 문제 x
  - 하나의 인스턴스멤버가 존재 → 인스턴스가 이미 생성되어있음. → 다른 인스턴스 멤버들도 모두 존재
- 실제로 같은 클래스 내에서 클래스 멤버가 인스턴스 멤버를 참조 똔느 호출해야 하는 경우는 드뭄.
  - 만일 그런 경우가 발생 → 인스턴스 메서드로 작성해야할 메서드를 클래스 메서드로 한 건 아닌지 고려
