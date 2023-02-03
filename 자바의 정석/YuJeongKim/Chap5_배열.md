## 배열

- 같은 타입의 여러 변수를 하나의 묶음으로 다루는 것
- 배열의 생성
    - 배열을 선언하는 것은 단지 생성된 배열을 다루기 위한 참조변수를 위한 공간이 만들어질 뿐이고, 배열을 생성해야만 비로소 값을 저장할 수 있는 공간이 만들어지는 것이다.
    - 배열 생성 시 각 배열요소는  자동적으로 int의 기본값인 0으로 초기화된다.
    
    ```java
    타입[] 변수이름;    //배열을 선선(배열을 다루기 위한 참조변수 선언)
    변수이름 = new 타입[길이];    //배열을 생성(실제 저장공간을 생성)
    ```
    
- 배열의 길이
    - 배열의 길이는 int범위의 양의 정수(0도 포함)이어야 한다.
    - 배열의 길이가 0일 수도 있다!
- 배열을 한번 생성하면 길이 변경할 수 없다!
    - 배열의 길이를 변경하는 방법
        1. 더 큰 배열을 새로 생성한다.
        2. 기존 배열의 내용을 새로운 배열에 복사한다.
- 배열의 생성과 초기화 동시에
    
    ```java
    int[] score = new int[] { 50, 60, 70, 80, 90 };  
    int[] score = new int[]{50, 60, 70, 80, 90 };
    int[] score = {50, 60, 70, 80, 90 };
    ```
    
- 배열의 출력
    - Arrays.toString(배열이름)
    
    ```java
    int[] iArr = { 1, 2, 3, 4, 5 }
    System.out.println(Arrays.toString(iArr));
    ```
    
- 배열의 복사
    1. 배열 arr의 길이인 arr.length의 값이 5이므로 길이가 10인 int배열 tmp가 생성되고, 배열 tmp의 각 요소는 int의 기본값인 0으로 초기화된다.
    2. for문을 이용해서 배열 arr의 모든 요소에 저장된 값을 하나씩 배열 tmp에 복사한다.
    3. 참조변수 arr에 참조변수 tmp의 값을 저장한다. arr의 값은 0x100에서 0x200으로 바뀌고, arr은 배열 tmp를 가리키게 된다.
    
    ```java
    int[] arr = new int[6];
    int[] tmp = new int[arr.length*2];
    
    for(int i=0; i<arr.length; i++)
    	tmp[i] = arr[i]
    
    arr = tmp;    //참조변수 arr이 새로운 배열을 가리키게 한다.
    ```
    
- System.arraycopy()를 이용한 배열의 복사
    - arraycopy()는 지정된 범위의 값들을 한 번에 통째로 복사한다
    - for문으로 배열을 복사하는 것보다 효과적이다
    
    ```java
    System.arraycopy(num, 0, newNum, 0, num.length);
    //num[0]에서 newNum[0]으로 num.length개의 데이터를 복사
    ```
    

## String 배열

- String 배열 생성

```java
String[] name = new String[]{"kim", "park", "yi"};
String[] name = {"kim", "park", "yi"};

String[] name = new String[3];
name[0] = new String("kim");
name[1] = new String("park");
name[2] = new String("yi");
```

- 배열 변수 name에 실제 객체가 아닌 객체의 주소가 저장되어있다.
- 기본형 배열이 아닌 경우, 즉, 참조형 배열의 경우 배열에 저장되는 것은 객체의 주소이다

## char배열과 String클래스

- 문자열 String은 문자배열인 char배열과 같은 뜻이다.
- 그런데 자바에서는 char배열이 아닌 String클래스를 이용해서 문자열을 처리하는 이유는?
    - String클래스가 char배열에 여러 가지 기능을 추가하여 확장한 것이기 대문
    - 객체지향언어인 자바에서는 char배열과 그에 관련된 기능들을 함께 묶어서 클래스에 정의한다.
- String객체(문자열)은 읽을수만 있을 뿐 내용은 변경할 수 없다!

## char배열과 String클래스의 변환

```java
char[] chArr = {'a', 'b', 'c'};
String str = new String(chArr);   //char배열 -> String
char[] tmp = str.toCharArr();    //String -> char배열 
```

## 커맨드 라인을 통해 입력받기

- 프로그램을 실행할 때 클래스 이름 뒤에 공백문자로 구분하여 여러 개의 문자열을 프로그램에 전달 할 수 있다.
- 만일 실행할 프로그램의 main메서드가 담긴 클래스의 이름이 MainTest라 가정하면 다음과 같이 실행할 수 있다.
    
    ```java
    c:\jdk1.8\work\ch5\java MainTest abc 123
    ```
    
    - 커맨드라인을 통해 입력된 두 문자열은 String배열에 담겨서 MainTest클래스의 main메서드의 매개변수(args)에 전달된다.
    - public static void main(String[] args) {…}
    - JVM이 입력된 매개변수가 없을 때, null 대신 크기가 0인 배열을 생성해서 args에 전달하도록 구현되었다.

## 다차원 배열

- 2차원 배열은 ‘배열의 배열’로 구성되었다.

```java
int[][] score = { {100,100,100}
									, {20,20,20}
									, {30,30,30}
									, {40,40,40}
									, {50,50,50}
								};

```

score.length = 5

score[0].length = 3

- for문을 이용한 2차원 배열 초기화
    
    ```java
    for(int i=0; i<score.length; i++) {
    	for(int j=0; j<score[i].length; j++) {
    		score[i][j] = 10;
    	}
    }
    ```
    
- 코드 예시
    
    ```java
    int[][] score = { {100,100,100}
    									, {20,20,20}
    									, {30,30,30}
    									, {40,40,40}
    									, {50,50,50}
    								};
    int sum = 0;
    
    for(int[] tmp : score) {
    	for(int i : tmp) {
    		sum += i;
    	}
    }
    ```
    

## 가변 배열

- 2차원 이상의 다차원 배열을 생성할 때 전체 배열 차수 중 마지막 차수의 길이를 지정하지 않고, 추후에 각기 다른 길이의 배열을 생성함으로써 고정된 형태가 아닌 보다 유동적인 가변 배열을 구성할 수 있다.
    
    ```java
    int[][] score = new int[5][3];
    ```
    
- 각 행마다 다른 길이의 배열을 생성하는 것이 가능하다.
    
    ```java
    int[][] score = new int[5][];
    score[0] = new int[4];
    score[1] = new int[3];
    score[2] = new int[2];
    score[3] = new int[2];
    score[4] = new int[3];
    ```
