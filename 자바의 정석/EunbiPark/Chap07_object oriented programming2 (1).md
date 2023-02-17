# Chap07_object oriented programming2 (1)

# 상속 (inheritance)

## 상속의 정의와 장점

### 정의

기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것 

### 장점

1. 적은 양의 코드로 새로운 클래스를 작성할 수 있다 
2. 코드를 공통적으로 관리할 수 있기에 코드의 추가, 변경이 용이 

⇒ 코드의 재사용성 높이고 코드의 중복을 제거하여 프로그램의 생산성과 유지보수에 기여

### 구현 방법

```java
// 조상 클래스: Parent 
// 자손 클래스: Child
class Child **extends** Parent {
	//...
}
```

조상 클래스 == parent class, super class, base class

자손 클래스 == child class, sub class, derived class

### 상속 계층도 (class hierarchy)

클래스간 상속 관계를 그림으로 표현한 것 

자손 클래스는 조상 클래스의 모든 멤버를 상속받기에 child class는 parent class의 멤버들을 포함한다 

parent class에 age라는 int형 정수를 멤버변수로 추가하면 

child 클래스는 자동적으로 age 멤버변수가 추가된 것과 같은 효과를 얻는다 

하지만 자손 클래스인 child class가 변경되면 parent class는 아무 영향도 받지 않는다 

자손 클래스는 조상 클래스의 모든 멤버를 상속 받으므로 항상 조상 클래스보다 같거나 많은 멤버를 갖는다 


접근 제어자가 private 도는 default 인 멤버들은 상속되지 않는 것이 아니라 자손 클래스로부터의 접근이 제한되는 것이다 

같은 내용의 코드를 하나 이상의 클래스에 중복적으로 추가해야 하는 겨우, 상속관계를 이용하여 코드의 중복을 최소화해야한다. 

```java
class Tv {
	boolean power;
	int channel;

	void power() {power = ! power;}
	void channelUp() {++channel;}
	void channelDown() {--channel; }
}

class CaptionTv extends Tv {
	boolean caption;
	void displayCaption (String text) {
		if(caption) {
			System.out.println(text);
		}
	}
}

class CaptionTvTest {
	public static void main (String args []) {
		CaptionTv ctv = new CaptionTv ();
		ctv.channel = 10;
		ctv.channelUp();
		System.out.println(ctv.channel);
		ctv.displayCatption("Hello, World");
		ctv.caption = true;
		ctv.displayCaption("Hello, World");
	}
}
```

<aside>
📌 자손 클래스의 인스턴스를 생성하면 조상 클래스의 멤버와 자손 클래스의 멤버가 합쳐진 하나의 인스턴스로 생성된다

</aside>

## 클래스간의 관계 - 포함관계

상속 외에 클래스를 재사용하는 방법 → 클래스간 **포함 관계 (Composite)**를 맺어주는 것

한 클래스의 멤버변수로 다른 클래스 타입의 참조변수참조변수를 선언하는 것 

`상속`: extends 사용 

`포함`: 클래스 안에서 다른 클래스 사용

```java
// 변경 전 
class Circle {
	int x;
	int y;
	int r;
}

// 포함 관계 사용 
class Circle {
	Point c = new Point(); // 다른 클래스를 멤버변수로 선언 
	int r;
}
```

포함관계를 사용하면 

1. 코드가 간결해지고
2. 단위클래스별로 코드가 작게 나뉘어 코드를 관리하기 쉽다 

## 클래스간 관계 결정하기

 상속할지, 포함할지 결정하는 방법 

<aside>
📌 **상속**: is-a 관계: 
**포함**: has-a 관계

</aside>

## 단일 상속 (single inheritance)

java는 다중 상속을 지원하지 않는다 (c++은 지원)

```java
class TVCR extends TV, VCR {
	// error
} 
```

다중 상속은 클래스간의 관계가 복잡해지고, 상속 받은 멤버간 이름이 같은 경우를 구별할 수 있는 방법이 없다는 단점이 있기에 자바에서는 단일 상속만을 허용한다 

단일 상속만을 제공하기에 클래스 간의 관계가 보다 명확해지고 코드를 더욱 신뢰할 수 있게된다 

자바에서 다중 상속과 유사한 효과를 보고 싶다면 …

extends 와 포함을 동시에 사용하면 된다 

```java
class TVCR extends Tv {
	VCR vcr = new VCR(); 
	
	void play () {
		vcr.play();
	}
...
}
// 외부적으로는 TVCR의 인스턴스를 사용하는 것 처럼 보이지만 
// 내부적으로는 VCR 클래스의 인스턴스를 생성해서 사용하는 것
```

## Object class - 모든 클래스의 조상

Object 클래스 == 모든 클래스 상속계층도의 최상위에 있는 조상클래스 

다른 클래스로부터 상속받지 않는 모든 클래스는 자동적으로 Object 클래스를 상속받기 한다 

자바의 모든 클래스들은 Object 클래스의 멤버들을 상속받기 때문에 Object 클래스에 정의된 멤버들을 사용할 수 있다 

(`toString()`, `equals(Object o)` 등등)

# 오버라이딩 (overriding)

## 오버라이딩이란?

조상클래스로부터 상속받은 메서드의 내용을 변경하는 것 

상속 받은 메서드를 자손 클래스 자신에 맞게 변경해야 하는 경우 조상 클래스의 메서드를 오버라이딩한다 

```java
class Point {
	int x;
	int y;
		
	String getLocation() {
		return "x: " + x + ", Y: " + y;
	}
}

class Poiint3D extends Point {
	int z;

		String getLocation() {
		return "x: " + x + ", Y: " + y + ", z: " + z;
	}
}

```

## 오버라이딩의 조건

메서드의 내용만을 새로 작성하는 것이기에 

메서드의 선언부는 조상의 것과 완전히 일치해야 한다 

### 조건

자손 클래스에서 오버라이딩 하는 메서드는 조상 클래스의 메서드와 

1. 이름이 같아야 한다 
2. 매개변수가 같아야 한다 
3. 반환타입이 같아야 한다 

⇒ 선언부가 일치해야 한다 (접근 제어자, 예외는 제한된 조건 내에서 다르게 변경 가능)

### 예외

1. 접근 제어자는 조상 클래스의 메서드보다 좁은 범위로 변경할 수 없다 
    
    조상 클래스에 정의된 메서드의 접근 제어자가 `protected` 라면 
    
    이를 오버라이딩하는 자손 클래스의 메서드의 접근 제엊다는 `protected`나 `public` 이어야 한다 
    
    대부분 같은 범위의 접근 제어자를 사용한다 
    
2. 조상 클래스의 메서드보다 많은 수의 예외를 선언할 수 없다 
    
    선언된 예외의 개수 문제가 아니다 
    
    만약 조상은 `IOException`과 `SQLException`을 선언하고 
    
    자손은 `Exception`을 선언했다면 
    
    개수가 적더라도 `Exception`은 모든 예외의 최고 조상이므로 결국 더 많은 예외를 던질 수 있도록 선언된 것이므로 잘못된 오버라이딩이 된다 
    

<aside>
📌 조상 클래스의 메서드를 자손 클래스에서 오버라딩할 때 
1. 접근 제어자를 조상 클래스의 메서드보다 좁은 범위로 변경할 수 없다 
2. 예외는 조상 클래스의 메서드보다 많이 선언할 수 없다 
3. 인스턴스메서드를 static 메서드로 또는 그 반대로 변경할 수 없다

</aside>

조상 클래스에 정의된 static 메서드를 자손 클래스에서 똑같은 이름의 staic 메서드로 정의한다면 오버라이딩이 아니다 

각 클래스에 별개의 static 메서드를 정의한 것일 뿐이다  

이러한 메서드를 호출할 때에는 `클래스이름.메서드이름()` 으로 하는 것이 바람직하다 

static 멤버들은 자신이 정의된 클래스에 묶여있다고 생각하면 된다 

## 오버로딩 vs 오버라이딩

| 오버로딩 | 오버라이딩  |
| --- | --- |
| 기존에 없는 새로운 메서드를 정의하는 것 
(매개변수 변경, 내용 변경) | 상속받은 메서드의 내용을 변경하는 것  |

```java
class Parent {
	void parentmethod() {}
}

class Child extends Parent {
	void parentMethod() {} // 오버라이딩 
	void parentMethod(int i) {} // 오버로딩 

	void childMethod() {}
	void childMethod(int i) {} // 오버로딩 
	void childMethod () {} // 중복 정의 오류
}
```

## super

자손 클래스에서 조상 클래스로부터 상속받은 멤버를 참조하는데 사용되는 참조변수 

상속받은 멤버와 자신의 멤머와 이름이 같은 경우 `super`을 붙여 구분 (`this`와 유사한 기능 - 조상의 멤버와 자신의 멤버를 구분하는데 사용된다는 점을 제외하고 근본적으로 같다)

조상 클래스로부터 상속받은 멤버도 자손 클래스 자신의 멤버이기에 `this`를 사용할 수 있다. 그래도 조상 클래스의 멤버와 자손 클래스이 멤버가 중복 정의되어 서로 구별해야 하는 경우에만 `super`를 사용하는 것이 좋다  

`static` 메서드는 인스턴스와  관련이 없기에 `this` 와 마찬가지로 `static` 메서드에서 사용할 수 없고 인스턴스 메서드에서나 사용할 수 있다

```java
class SupterTest2 {
	public static void main (String args []) {
		Child c = new Child();
		c. method();
	}
}

class Parent {
	int x = 10;
}

class Child extends Parent {
	int x = 20;
	
	void methid() {
		System.out.println("x = " + x); // 20 
		System.out.println("this.x = " + this.x); // 20 
		System.out.println("super.x = " + super.x); // 10 
}
```

조상 클래스에 선언된 멤버변수와 같은 이름의 멤버변수를 자손 클래스에서 중복해서 정의하는 것이 가능하다 (`super`로 구분 가능)

변수만이 아니라 메서드 역시 `super`를 사용할 수 있다 

조상 클래스의 메서드를 자손클래스에서 오버라이딩 한 경우에 `super`를 사용한다 

```java
class Point {
	String getLocation() {
		return "x: " + x + ", t : " + y;
}

class Point3D extends Point {
	String getLocation() {
		return super.getLocation() + ", z : " + z; // 조상 메서드 호출
		}
}
```

조상클래스 메서드 내용에 추가적으로 작업을 덧붙이는 경우에 이처럼 `super`를 사용하여 조상클래스의 메서드를 포함시키는 것이 좋다 

후에 조상 클래스의 메서드가 변경되더라도 변경된 내용이 자손클래스의 메서드에 자동적으로 반영될 것이기 때문이다 

## super() - 조상 클래스의 생성자

자손 클래스의 인스턴스를 생성하면 자손의 멤버와 조상의 멤버가 모두 합쳐진 하나의 인스턴스가 생성된다 

이때, 조상 클래스 멤버의 초기화 작업이 수행되어야 하기 때문에 자손 클래스의 생성자에서 조상 클래스의 생성자가 호출되어야 한다 

Object 클래스를 제외한 모든 클래스의 생성자는 첫 줄에 반드시 자신의 생성자 또는 조상의 생성자를 호출해야한다 

그렇지 않으면 super()을 자동적으로 추가한다 

<aside>
📌 Object 클래스를 제외한 모든 클래스의 생성자 첫 줄에 생성자, `this()`, `super()`를 호출해야 한다. 그렇지 않으면 컴파일러가 자동적으로 `super();`를 생성자의 첫 줄에 삽입한다

</aside>

인스턴스를 생성할 때는 클래스를 선택하는 것만큼 생성자를 선택하는 것도 중요하다 

1. 클래스 - 어떤 클래스의 인스턴스를 생성할지 
2. 생성자 - 선택한 클래스의 어떤 생성자를 이용하여 인스턴스를 생성할 것인가? 

<aside>
📌 조상 클래스의 멤버변수는 조상의 생성자에 의해 초기화도도록 해야 한다

</aside>

# package 와 import

## package

클래스의 묶음 

같은 이름의 클래스일 지라도 서로 다른 패키지에 속하면 패키지명으로 구분할 수 있다 

<aside>
📌 클래스가 물리적으로 하나의 클래스파일(.class)인 것과 같이 패키지는 물리적으로 하나의 디렉토리이다

</aside>

- 하나의 소스파일에는 첫 번째 문장으로 단 한번의 패키지 선언만을 허용
- 모든 클래스는 반드시 하나의 패키지에 속해야 한다
- 패키지는 점을 구분자로 하여 계층 구조로 구성 가능
- 패키지는 물리적으로 클래스 파일(.class)을 포함하는 하나의 디렉토리

## 패키지의 선언

```java
package 패키지명; 
```

모든 클래스는 반드시 하나의 패키지에 포함되어 있어야 한다 (패키지를 생성하지 않으면 unnamed package가 생성된다)

## import 문

컴파일러에게 소스파일에 사용된 클래스의 패키지에 대한 정보를 제공하는 것 

## import 문의 선언

일반적인 소스파인 (*.java)의 구성은 다음의 순서로 되어 있다 

1. package 
2. import 
3. class 선언 

```java
import 패키지명.클래스명;
import 패키지명.*; // 성능상의 차이는 없다 (시간이 더 오래걸리긴 한다)
```

## static import 문

`static import` 문을 사용하면 `static` 멤버를 호출할 대 클래스 이름을 생략할 수 있다 

# 제어자 (modifier)

## 제어자란?

클래스. 변수, 메서드의 선언부에 함께 사용되어 부가적인 의미를 부여하는 것 

| 접근 제어자 | 그 외  |
| --- | --- |
| public. protected, default, private | static, final, abstract, native, transient, synchronized, volatile, strctfp |

클래스나 멤버변수, 메서드에 주로 사용되며 하나의 대상에 대하여 여러 제어자를 조합하여 사용한다 

접근 제어자는 네 가지 중 하나만 사용할 수 있다 

## static - 클래스의, 공통적인

하나의 변수를 모든 인스턴스가 공유하기에  클래스 변수 (static 멤버 변수)는 인스턴스에 관계없이 같은 값을 갖는다 

static이 붙은 멤버변수, 메서드, 초기화 블럭은 인스턴스를 생성하지 않고 사용할 수 있다 

<aside>
📌 static이 사용될 수 있는 곳 - 멤버변수, 메서드, 초기화 블럭

</aside>

| 멤버변수 | 메서드 |
| --- | --- |
| 모든 인스턴스에 공통적으로 사용되는 클래스변수가 된다 
클래스변수는 인스턴스를 생성하지 않고도 사용 가능하다
클래스가 메모리에 로드될 때 생성된다  | 인스턴스를 생성하지 않고도 호출이 가능한 static 메서드가 된다 
static 메서드 내에서는 인스턴스 멤버들을 직접 사용할 수 없다  |

인스턴스 멤버를 사용하지 않는 메서드라면 static을 붙여 static 메서드로 선언해보자

인스턴스를 생성하지 않고 호출이 가능하여 간편하고 속도가 빠르다 

## final - 마지막의, 변경될 수 없는

거의 모든 대상에 사용 가능 

| 클래스  | 변경될 수 없는 클래스, 확장될 수 없는 클래스 
다른 클래스의 조상이 될 수 없다  |
| --- | --- |
| 메서드  | 변경될 수 없는 메서드 
오버라이딩을 통해 재정의 될 수 없다  |
| 멤버변수, 지역변수 | 상수  |

### 생성자를 이용한 final 멤버 변수의 초기화

일반적으로 final이 붙으면 상수가 되기에 선언과 동시에 초기화한다 

그러나 인스턴스 변수의 경우 생성자에서 초기화 되도록 할 수 있다 

## abstract - 추상의, 미완성의

메서드의 선언부만 작성하고 실제 수행내용은 구현하지 않은 추상메서드를 선언하는데 사용 

| 클래스 | 클래스 내에 추상 메서드가 선언되어 있음을 의미 |
| --- | --- |
| 메서드 | 선언부만 작성하고 구현부는 작성하지 않은 추상 메서드임을 알림  |

완성되지 않은 메서드가 존재하기에 인스턴스를 생성할 수 없다 

### 완성된 클래스에 abstract을 붙이는 경우

목적: 인스턴스 생성하지 못하게 하는 것 

장점: 다른 클래스가 이 클래스를 상속받아서 일부의 원하는 메서드만 오버라이딩 해도 된다는 장점 

해당 클래스가 없다면 아무런 내용이 없는 메서드를 잔뜩 오버라이딩 해야 한다 

## 접근 제어자 (access modifier)

해당하는 멤버 또는 클래스를 외부에서 접근하지 못하도록 제한하는 역할 

접근 제어자가 지정되어 있지 않다면 default 제어자가 붙는다 

어느정도까지 접근을 허용할지를 생각하며 선택하면 된다 

| private  | 같은 클래스 내에서만 접근 가능  |
| --- | --- |
| default | 같은 패키지 내에서만 접근이 가능하다  |
| protected  | 같은 패키지 내에서, 그리고 다른 패키지의 자손 클래스에서 접근이 가능하다 |
| private | 접근 제한이 없다  |

**public > protected > default > private**

### 접근 제어자를 이용한 캡슐화

**접근 제어자를 사용하는 이유** 

1. 클래스의 내부에 선언된 데이터를 보호하기 위해 
2. 외부에는 불필요하지만 내부적으로 사용되는 부분을 감추기 위해

### 생성자의 접근 제어자

생성자에 접근 제어자를 사용하여 인스턴스의 생성을 제한할 수 있다 

보통 생성자의 접근 제어자는 클래스의 접근 제어자와 같지만, 다르게 지정할 수 있다 

`private`

외부에서 생성자에 접근할 수 없으므로 인스턴스를 생성할 수 없다 

클래스 내부에서는 생성할 수 있다 

대신 인스턴스를 생성하여 반환해주는 public 메서드를 제공하여 외부에서 클래스의 인스턴스를 사용할 수 있도록 할 수 있다 

해당 메서드는 `public static` 이어야 한다 

```java
class Singleton {
	...
	// 인스턴스가 미리 생성되어 있어야 하므로 static 
	private static Singleton s = new Singletone(); 
	private Sngletone() {}
	// 인스턴스를 생성하지 않고도 호출 가능 -> static 
	public static Singleton getInstance() {
		return s;
	}
	...
}
```

생성자를 통해 인스턴스를 생성하지 못하게 하고 `public` 메서드를 통해 인스턴스에 접근하게 함으로써 인스턴스 개수를 제한할 수 있다 

생성자가 `private`인 클래스는 다른 클래의 조상이 될 수 없다 

자손 클래스의 인스턴스를 생성할 때 조상클래스의 생성자를 호출해야 한는데 호출이 불가능하기 때문

클래스 앞에 final 을 추가하여 상속할 수 없는 클래스임을 알리는 것이 좋다 

## 제어자(modifier)의 조합

1. 메서드에 static과 abstract를 함께 사용할 수 없다 
    
    static은 몸통이 있는 메서드에만 사용 가능 
    
2. 클래스에는 abstract와 final을 동시에 사용할 수 없다 
    
    클래스에 사용되는 final은 클래스를 확장할 수 없다는 의미 그러나 abstract은 상속을 통해 확장해야한다는 의미이므로 모순이다 
    
3. abstract 메서드의 접근 제어자가 private일 수 없다
    
    abstract 메서드는 자손클래스에서 구현해주어야 하는데 접근제어자가 private이면 자손클래스에서 접근 불가 
    
4. 메서드에 private와 final 을 같이 사용할 필요는 없다 
    
    접근 제어자가 private인 메서드는 오버라이딩 될 수 없기 때문
