# 배열 (array)

## 배열(array)이란?

**같은 타입**의 여러 변수를 하나의 묶음으로 다루는 것 

```java
// 5개의 int를 저장할 수 있는 배열
int [] score = new int[5];
// score은 배열을 다루는 데 필요한 참조 변수 O, 저장공간 X 
```

저장공간이 연속적으로 배치되어 있다 

## 배열의 선언과 생성

```java
// 선언 방법 1
// 타입 [] 변수이름;
int [] score;

// 선언 방법 2
// 타입 변수이름[];
int score[]; 
```

### 배열의 생성

배열을 선언하는 것은 단지 생성된 배열을 다루기 위한 참조변수를 위한 공간을 만드는 것 

매열을 생성해야만 비로소 값을 저장할 수 있는 공간이 만들어지는 것이다 

|  | 선언 | 생성 |
| --- | --- | --- |
| 역할 | 참조 변수를 위한 공간 할당 | 값을 저장할 수 있는 공간 할당 |
| 방법 | 타입 [] 변수이름; | 변수이름 = new 타입 [길이]; |
| 예시 | int [] score; | score = new int[5]; |

```java
// 선언과 동시에 생성하는 방법 
int [] score = new int [5];
```

## 배열의 길이와 인덱스

배열의 요소(elememt): 생성된 배열의 각 저장공간 

접근 방법: 배열이름 [인덱스]

인덱스는 배열의 요소마다 붙여진 일련번호 

배열에 값을 저장하고 읽어오는 방법은 변수와 동일하지만 변수 이름 대신 인덱스를 사용한다는 것이 다르다 

인덱스의 값으로 상수 대신 변수, 수식도 가능하다 (인덱스 범위를 넘어서지 않도록 주의하자)

### 배열의 길이

배열의 길이는 양의 정수여야 하며, 최대값은 int 형 타입의 최대값이다 

길이가 0인 배열을 생성 할 수도 있다 → 꽤나 유용한 방법 (이후에 나옴)

### 배열이름.length

JVM이 모든 배열의 길이를 별도로 관리한다 

`배열이름.length`을 통해 배열의 길이에 대한 정보를 얻을 수 있다 

```java
int [] arr = new int [5];
int tmp = arr.length;
```

배열의 길이는 한 번 설정하면 변경할 수 없기에 `배열이름.length`는 상수이다 

for 문의 조건식에 배열의 길이를 직접 작성하는 것 보다 `배열이름.length` 을 사용하는 것이 좋다 

```java
int [] score = new int [5];

for (int i = 0 ; i < score.length; i++ ) {
		System.out.println(score[i]);
}
```

### 배열의 길이 변경하기

배열의 공간의 부족한 경우에는 

1. 더 큰 길이의 새로운 배열을 생성하고
2. 기존 배열의 내용을 새로운 배열에 복사한다 

처음부터 배열의 길이를 넉넉하게 잡아 배열을 새로 생성하는 상황이 적게 발생하도록 해야 한다 

(기존 길이의 2배 정도가 좋다) 

## 배열의 초기화

배열은 생성과 동시에 자동적으로 자신의 타입에 해당하는 기본값으로 초기화된다 

원하는 값으로 초기화 하고 싶을 땐 각 요소에 접근하여 값을 지정하면 된다 

1. 인덱스로 접근 
    
    ```java
    int [] score = new int [5];
    score [0] = 100;
    ```
    
2. for 문으로 인덱스 접근 
    
    ```java
    for (int i = 0 ; i < score.length; i++) 
    	score[i] = i * 10  + 50;
    ```
    
3. 초기화 문법 사용 
    
    ```java
    int [] score = new int [] {1, 2, 3, 4, 5}; //배열의 길이를 명시하지 않아도 된다 
    
    // new 타입[] 생략 - 배열의 선언과 생성을 함께 하는 경우만 가능 
    // parameter로 int 배열을 받는 경우에도 동일 
    int [] score = {1, 2, 3, 4, 5};
    
    // 괄호 안에 아무 것도 넣지 않으면 길이가 0인 배열 생성 
    // 참조변수의 기본값은 null, 배열을 가리키는 참조변수는 null 대신 길이가 0인 배열로 초기화한다 
    int [] score = new int[0];
    int [] score = new int [] {};
    int [] score = {};
    ```
    

### 배열의 출력

배열에 저장된 값을 확인할 때도 for문을 사용하면 된다 

1. for 문 사용 
    
    ```java
    int [] iArr= {1, 2, 3, 4, 5};
    
    for (int i = 0; i < iArr.length; i++ ) {
    	System.out.println(iArr[i]);
    ```
    
2. Arrays.toString(배열이름)
    
    ```java
    int [] iArr ={1, 2, 3, 4, 5};
    
    System.out.println(Arrays.toString(iArr));
    // [1, 2, 3, 4, 5]
    
    System.out.println(iArr);
    // I@123123bb -> 타입@주소 
    // char 배열은 예외적으로 바로 배열의 값을 출력할 수 있다 
    ```
    

## 배열의 복사

### for 문을 이용

```java
int [] arr = new int [5];
int [] tmp = new int [arr.length * 2];

for (int i = 0 ; i < arr.length; i++)
	tmp[i] = arr[i]; // arr의 값 복사 

arr = tmp; // 참조 변수 arr이 tmp를 가리키도록 변경 -> arr와 tmp가 같은 배열을 가리킴
// 배열은 참조변수를 통해서만 접근 할 수있기에 자신을 가리키는 참조 변수가 없는 배열은
// 사용할 수 없다 -> 쓸모가 없어지면 JVM의 가비지 컬렉터에 의해 자동적으로 제거 
```

### System.arraycopy()를 이용

지정된 범위의 값들을 한 번에 통째로 복사 

각 요소들이 연속적으로 저장되어 잇다는 배열의 특성 때문에 가능 

for 문 보다 효율적이다 

```java
// num[0] 에서 numNum[0] 으로 num.length 개의 데이터를 복사 
// 크기 주의 (여유 공간이 없으면 error 발생)
System.arraycopy(num, 0, newNum, 0, num.length);
```

## 배열의 활용

총합과 평균

최대값과 최소값 

섞기 

임의의 값으로 배열 채우기 

정렬하기 

빈도수 구하기 

등등 

# String 배열

## String 배열의 선언과 생성

```java
String [] name = new String [3]; // 각 요소는 null로 초기화 
```

## String 배열의 초기화

int 배열과 동일한 방법으로 초기화 

배열의 각 요소에 문자열을 지정하면 된다 

```java
String [] name = new String [3];
name [0] = "Park"; // 원래 name[0] = new String("Park")이어야 하지만 String 은 예외

String [] name2 = new String[] {"Park", "kim"};
String [] name3 = {"Park", "kim"}; // new String[] 생략 
```

String 배열과 같이 기본형 배열이 아닌 경우 배열에 저장되는 것은 객체의 주소이다 

## char 배열과 String 클래스

문자열은 char 배열과 동일한 의미 

그러나 자바에서는 char 배열이 아닌 String 클래스를 이용하여 문자열을 처리한다 

→ char 배열에서 여러 기능을 추가한 것이 String 클래스이기 때문 

중요! String 객체는 읽을 수만 있을 뿐 내용을 변경할 수는 없다 

```java
String str = "java";
str = str + "8"; // 문자열은 변경할 수 없으므로 새로운 내용의 문자열이 생성됨 
System.out.println(str); 
```

## String 클래스의 주요 메서드

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e18f12bf-27df-4d04-9924-b7ea25f08e32/Untitled.png)

## char 배열과 String 클래스의 변환

```java
char [] chArr = {'A', 'B', 'C'};
String str = new String(chArr); // char -> String
char[] tmp = str.toCharArray(); // String -> char 
```

## 커맨드 라인을 통해 입력 받기

프로그램을 실행할 때 클래스 이름 뒤에 공백문자로 구분하여 여러 개의 문자열을 프로그램에 전달 할 수 있다 

```java
c:\jdk1.8\work>java MainTest abc 123 
```

커맨드라인을 통해 입력된 두 문자열은 String 배열에 담겨 MainTes 클래스의 main 메서드의 매개변수( args)에 전달된다 

공백으로 구분되기에 공백이 있는 경우 `“`로 감싸야 한다 

커맨드라인에 매개변수를 입력하지 않으면 크기가 0인 배열이 생성되어 args.length의 값은 0이 된다. 매개변수가 입력되지 않아 배열을 생성하지 않으면 args의 값이 null이 될 것이고 args를 사용하는 모든 코드에서 에러가 발생한다 

그러나 JVM이 입력된 매개변수가 없을 때 null 대신 크기가 0인 배열을 생성해서 args에 전달하여 오류가 발생하지 않게 되었다 

# 다차원 배열

## 2차원 배열의 선원과 인덱스

2차원 배열은 배열의 배열의 값으로 되어 있다 

```java
// 방법 1
int [][] score;

// 방법 2
int score [][];

// 방법 3
int [] score [];
```

주로 테이블 형태의 데이터를 담는데 사용된다 

### 2차원 배열의 index

`배열이름[행idx][열idx]`

## 2차원 배열의 초기화

```java
int [][] arr = new int [][] {{1, 2, 3}, {4, 5, 6}};
int [][] arr = {{1, 2, 3}, {4, 5, 6}}; // 줄 바꿈 해주는 것이 좋다 
```

```java
System.out.println(arr.length); // 2 -> 배열의 배열이라는 것을 생각하면 된다 
System.out.println(arr[0].length); // 3
```

## 가변 배열

2차원 이상의 다차원 배열을 생성할 때 전체 배열 차수 중 마지막 차수의 길이를 지정하지 않고 추후에 각기 다른 길이의 배열을 생성함으로써 고정된 형태가 아닌 보다 유동적인 가변 배열을 설정할 수 있다 

```java
int [][] score = new int [5][]; // 두번째 차원의 길이 지정 안함 
score [0] = new int[3]; // 다른 크기로 생성 가능 
score [1] = new int[2];
score [2] = new int[6];
```

## 다차원 배열의 활용

좌표에 x 표하기 

빙고 

행렬의 곱셈

단어 맞추기
