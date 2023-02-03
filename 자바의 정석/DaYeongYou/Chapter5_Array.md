# 1. 배열이란?

같은 타입의 여러 변수를 하나의 묶음으로 다루는 것

변수와달리 배열은 각 저장공간이 연속적으로 배치되어 있다는 특징이 있음.

## 1. 배열의 선언과 생성

### 배열의 선언

변수는 선언과 동시에 저장공간이 생성되지만, **배열을 선언**하면 **저장공간이 만들어지는 것이 아닌** 배열을 다루기 위한 **참조변수**가 만들어진다. 

2가지 선언 방법이 있는데,

| 선언방법 | e.g. |
| --- | --- |
| 1. `타입[] 변수이름;` | int[] score;
String[] name; |
| 2. `타입 변수이름[]`; | int score[];
String name[]; |

보통 java에서는 1번째 선언방법을 사용한다. 1번의 선언 예시를 보면 `int[]` 가 배열기호로, **자료형의 일부**로 본다. 즉, `정수형 배열`을 뜻하는 것을 알 수 있다.

2번째 방법은 배열변수의 오른쪽에 배열기호를 붙인다. 이는 c언어 스타일이다.

### 배열의 생성

배열을 선언하는 것은 단지 생성된 배열을 다루기 위한 참조변수를 위한 공간이 만들어지는 것.

배열을 생성해야만 비로소 값을 저장할 수 있는 공간이 만들어짐.

배열을 생성하기 위해서는 연산자 `new` 와 함께 **배열의 타입**과 **길이**를 지정해야!

```java
타입[] 변수이름; // 배열을 선언: 배열을 다루기 위한 참조변수 선언
변수이름 = new 타입[길이]; // 배열을 생성: 실제 저장공간을 생성

int[] score; // 1. int 타입의 배열을 다루기 위한 참조변수 score 선언
score = new int[5]; // 2. int 타입의 값 5개를 저장할 수 있는 배열 생성.
```

## 2. 배열의 인덱스

배열의 인덱스는 각 요소(저장공간)에 자동으로 붙는 일련의 번호이다.

인덱스의 범위는 0부터 (배열길이-1) 까지.

배열에 값을 저장하고 읽어오는 방법은 변수와 같다. 단지 변수이름 대신 `배열이름[인덱스]` 를 사용한다는 점만 다르다.

```java
public class ArrayEx1 {
public static voidmain(String[] args) {
//        int[] score; //배열 score선언(참조변수)
//        score=new int[5]; //배열의 생성(int저장공간*5)

int[] score =new int[5];//배열의 선언과 생성을 동시에
score[3]=100;

        System.out.println("score[0]="+score[0]);
        System.out.println("score[1]="+score[1]);
        System.out.println("score[2]="+score[2]);
        System.out.println("score[3]="+score[3]);
        System.out.println("score[4]="+score[4]);

// for문으로 배열의 모든 요소 출력
for(inti=0; i<5; i++){
            System.out.printf("score[%d]:%d%n", i, score[i]);
        }
    }
}
```

## 3. 배열의 길이

`배열이름.length` 을 통해서 배열의 길이에 대한 정보를 얻을 수 있음.

```java
int[] arr = new int[5]; // 길이가 5인 int배열
int tmp = arr.length; // arr.length의 값은 5이고 tmp에 5가 저장됨.
```

배열은 한번 생성하면 **실행 동안 그 길이를 바꿀 수 없다.**

따라서 arr.length는 상수이다.

## 4. 배열의 초기화

배열의 각 요소에 처음으로 값을 저장하는 것.

```java
int[] score = new int[5];
score[0]=50;
score[1]=60;
score[2]=70;
score[3]=80;
score[4]=90;

// 중괄호 이용
int[] score={50,60,70,80,90};

// 에러
int[] score;
score={50,60,70,80,90}; // 두 줄로 나누는 것은 안됨.
```

### 배열의 출력

- 배열을 초기화할 때 for문을 사용하듯이.
- 배열에 저장된 값을 확인할 때도 for문을 사용하면 됨.
- `println` 메서드는 출력 후에 줄 바꿈을 하므로, 여러 줄에 출력되어 보기 불편할 때가 있다.
- 그럴 땐, 출력 후 줄 바꿈을 하지 않는 `print` 메서드를 사용.

```java
int[] iArr={100, 95, 80, 20, 40};
// 배열을 가리키는 참조변수 iArr의 값을 출력
System.out.println(iArr); // [I@14318bb]와 같은 형식의 문자열 출력. -> 따라서 iArr의 값을 바로 출력하는 것이 아님.

// 1. for문 + print 메서드 사용
int[] iArr = {100, 95, 80, 70, 60};
for( int i =0; i<iArr.length; i++){
	System.out.print(iArr[i]+", ");
}
System.out.println(); // 다음 출력이 바로 이어지지 않도록 줄 바꿈.
```

- 더 간단한 방법은 `Arrays.toString(배열이름)` 메서드 사용
    - 이 메서드는 배열의 모든 요소를 ‘[첫번째요소, 두번째요소… ]’ 와 같은 형식의 **문자열로** 만들어서 반환.
    - 이 메서드를 이용하면 배열의 내용을 쉽게 확인 가능.
        
        ```java
        int[] iArr = {100, 95, 80, 70, 60}; // 길이가 5인 int 배열
        // 배열 iArr의 모든 요소 출력. [100, 95, 80, 70, 60] 이 출력됨.
        System.out.println(Arrays.toString(iArr)); // [100, 95, 80, 70, 60]
        ```
        
        - 만약, iArr의 값을 바로 출력하면, 어떻게 될까?
        - iArr은 `참조변수` 이므로 변수에 저장된 값, 즉 **배열의 주소**가 출력된다고 생각한다면 잘 따라오고 있는 것
        - 그러나 **타입@주소** 형식으로 출력됨.
            
            즉, 배열을 가리키는 **참조변수**를 출력해봐야 얻을 정보가 없음.
            
- 예외적으로, `char 배열`은  `println 메서드`로 출력하면 각 요소가 구분자 없이 그대로 출력됨.
    - println 메서드가 char배열일 때만 이렇게 동작하도록 만들어졌기 때문임.

```java
// char형 배열
char[] chArr = {'a', 'b', 'c'};
System.out.println(chArr) // abc 출력
```

## 5. 배열의 복사

- 배열은 한번 생성하면 그 길이를 변경할 수 없음
- 더 많은 저장공간이 필요하다면 보다 큰 배열을 새로 만들고 **이전 배열로부터 내용을 복사**해야 함.

아래서부터 배열을 복사하는 법, **2가지**

### 1. for문을 이용해서 배열을 복사(👎 비추)

```java
int[] arr = new int[5];
...
int[] tmp = new int[arr.length * 2]; // 기존 배열보다 길이가 2배인 배열 생성

for (int i = 0; i<arr.length; i++)
	tmp[i] = arr[i]; // arr[i]의 값을 tmp[i]에 저장.
arr = tmp; //참조변수 arr이 새로운 배열을 가리킴.
```

- 이렇게 작업하는 건 비용이 많이 듦
    
    → 처음부터 배열의 길이를 넉넉하게 잡아줘서 **새로 배열을 만드는 일이 가능한 적게끔**(그렇다고 너무 크게 잡으면 메모리 낭비이므로 기존의 **2배** 정도의 길이로 배열을 생성하는 것이 좋음)
    
    <img width="440" alt="arr_1" src="https://user-images.githubusercontent.com/71822139/216499261-2fead049-4f60-4776-9435-89ba36162c3f.png">
    

  - 따라서 배열 arr 과 배열 tmp는 동일한 배열이다.

### 2. System.arraycopy() 를 이용한 배열의 복사(👍 추천)

- for문 대신 **System 클래스의 arraycopy()**를 이용하면 보다 빠르고 간단하게 배열 복사 가능
- for문은 배열의 요소 하나하나에 접근해서 복사
- **arraycopy()는 지정된 범위의 값들을 한번에 통째로 복사**
- 각 요소들이 **연속적으로 저장**되어 있다는 배열의 특징으로 이렇게 처리하는 것이 가능.

배열의 복사에 사용되었던 for 문을 arraycopy()로 바꾸면,

```java
for (int i = 0; i < num.length; i++) {
      newNum[i] = num[i];
};
```

                      ↓

```java
 System.arraycopy(num, 0, newNum, num.length);
```

arraycopy() 를 호출할때는 **어느 배열의 몇번째 요소**에서 **어느 배열로 몇번째 요소로 몇개의 값을 복사할 것**인지 지정해줘야 함.

<img width="891" alt="arr_2" src="https://user-images.githubusercontent.com/71822139/216499266-ff55263a-8af5-4cc7-a02c-a5759551c355.png">

  → 이때 복사하려는 배열의 위치가 적절하지 못하여 *복사하려는 내용보다 여유 공간이 적으면* `ArrayIndexOutOfBoundsException` 발생하니 주의

```java
public static void main(String[] args){
        char[] abc={'A','B','C','D'};
        char[] num = {'0','1','2','3','4','5','6','7','8','9'};
        System.out.println(abc);
        System.out.println(num);

        // 배열 abc와 num을 붙여 하나의 배열(result)로 만든다.
        char[] result=new char[abc.length+num.length];
        System.arraycopy(abc, 0, result, 0, abc.length);
        System.arraycopy(num, 0, result, abc.length, num.length);
        System.out.println(result);

        // 배열 abc을 배열 num의 첫번째 위치부터 배열 abc의 길이만큼 복사.
        System.arraycopy(abc, 0, num, 0, abc.length);
        System.out.println(num);

        // number의 인덱스 6 위치에 3개의 복사.
        System.arraycopy(abc, 0, num, 6, 3);
        System.out.println(num);
}
```

다른 배열과 달리 `char 배열`은 for문을 사용하지 않고도 **print() 나 println()**으로 **배열에 저장된 모든 문자를 출력**할 수 있다.

## 6. 배열의 활용

### 총합과 평균

- for문을 이용해 배열에 저장된 값을 모두 더한 결과를 배열의 개수로 나눠 평균을 구하는 예제.
- 평균을 구하기 위해 전체 합을 배열의 길이인 `score.length` 로 나눔.
- 이때, int와 int 간의 연산은 int를 결과로 얻기 때문에 정확한 평균값을 얻지 못함. → score.length를 float로 변환(sum을 float로 변환해도 ok. 둘 중 하나만)

```java
public static void main(String[] args) {
        int sum = 0;         // 총점
        float average = 0f;  // 평균

        int[] score = {100, 88, 100, 100, 90};

        for (int i = 0; i < score.length; i++) {
            sum += score[i];
        }

        average = sum / (float) score.length;      // 계산결과를 float로 얻기 위해 형 변환

        System.out.println("총점: " + sum);
        System.out.println("평균: " + average);

    }
```

### 최대값과 최소값

- 배열에 저장된 값 중에서 최대값과 최소값을 구하는 예제
- 배열의 첫번째 요소 `score[0]` 의 값으로 최대값을 의미하는 변수 max
- 최소값을 의미하는 변수 min을 초기화

```java
public static void main(String[] args) {
        int[] score = {79, 88, 91, 33, 100, 55, 95};

        int max = score[0]; // 배열의 첫번째 값으로 최대값 초기화
        int min = score[0]; // 배열의 첫번째 값으로 최소값 초기화

        for (int i = 1; i < score.length; i++) {
            if (score[i] > max) {
                max = score[i];
            } else if (score[i] < min) {
                min = score[i];
            }
        } // end of for
        System.out.println("최대값: " + max);
        System.out.println("최소값: " + min);
    }
```

### 섞기(shuffle)

- 길이가 10인 배열 numArr을 생성하고 0~9의 숫자로 차례대로 초기화해 출력
- random()을 이용해 배열의 임의의 위치에 있는 값과 배열의 첫번째 요소인 numArr[0]의 값을 교환하는 일을 100번 반복.

```java
public static void main(String[] args) {
        int[] numArr = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
        // = int[] numArr = new int[10];
        // for (int i=0; i<numArr.length; i++){
        //        numArr[i] = i;
        //        System.out.println(numArr[i]);
        //    }
        System.out.println(Arrays.toString(numArr));

        for (int i = 0; i < 100; i++) { // 배열길이만큼 반복해도 ok. 충분히 섞기 위해 교재에서는 100번 반복.
            int n = (int) (Math.random() * 10);
            // numArr[0]과 numArr[n]의 값을 서로 바꾼다.
            int tmp = numArr[0];
            numArr[0] = numArr[n];
            numArr[n] = tmp;
            System.out.println(Arrays.toString(numArr));
        }
    }
```

### 로또번호 생성

- 길이가 45인 배열에 1부터 45까지의 값을 모두 담음
- 반복문을 이용해 **배열의 인덱스가 i인 값(ball[i])**과 **random()에 의해 결정된 임의의 위치에 있는 값과 자리를 바꾸는 것**을 **6**번 반복.

```java
public static void main(String[] args) {
        int[] ball = new int[45]; // 45개의 정수값
        // 배열의 각 요소에 1~45의 값 저장
        for (int i = 0; i < ball.length; i++)
            ball[i] = i + 1;
        int temp = 0;
        int j = 0;

        for (int i = 0; i < 6; i++) {
            j = (int) (Math.random() * 45);
            temp = ball[i];
            ball[i] = ball[j];
            ball[j] = temp;
        }
        // 배열 ball의 앞에서부터 6개의 요소 출력
        for (int i = 0; i < 6; i++)
            System.out.printf("ball[%d]=%d%n", i, ball[i]);
    }
```

### 임의의 값으로 배열 채우기

- 배열을 연속적인 범위의 임의의 값으로 채우는 건 random()만 사용하면 쉽게 할 수 있다.
    
    ```java
    for(int i=0; i<arr.length; i++){
    	arr[i]=(int)(Math.random()) * 5; 
    }
    ```
    
    - 그러면 불연속적인 값들로 배열을 채우는 건 어떻게 해야할까?
        - **배열을 하나 더 사용!**
        - 먼저 배열 code에 불연속적인 값들을 담고, 임의로 선택된 index에 저장된 값으로 배열 arr의 요소들을 하나씩 채우면 됨.
        - 저장된 값에 상관없이 배열의 index는 항상 연속적이기 때문!
        
        ```java
        public static void main(String[] args) {
                int[] code = {-4, -1, 3, 6, 11}; // 불연속적인 값들로 구성된 배열
                int[] arr = new int[10];
        
                for (int i = 0; i < arr.length; i++) {
                    int tmp = (int) (Math.random() * code.length);
                    arr[i] = code[tmp];
                }
                System.out.println(Arrays.toString(arr));
            }
        ```
        

### 버블정렬

- 길이가 10인 배열에 0과 9사이의 임의의 값으로 채움
- 버블정렬 알고리즘을 통해 크기순으로 정렬.
- 알고리즘의 정렬방법
    - 배열의 길이가 n일때, 배열의 첫 번째부터 n-1까지의 요소에 대해 근접한 값과 크기를 비교해 자리 바꿈 반복.

```java
public static void main(String[] args) {
        int[] numArr = new int[10];
        for (int i = 0; i < numArr.length; i++) {
            System.out.print(numArr[i] = (int) (Math.random() * 10));
        }
        System.out.println();

        for (int i = 0; i < numArr.length; i++) {
            boolean changed = false; // 자리 바꿈이 발생했는지 체크
            for (int j = 0; j < numArr.length-1-i; j++) {
                if (numArr[j] > numArr[j + 1]) { // 옆의 값이 작으면 서로 바꿈
                    int temp = numArr[j];
                    numArr[j] = numArr[j + 1];
                    numArr[j + 1] = temp;
                    changed = true; // 자리바꿈 발생 -> changed를 true로
                }
            }
            if (!changed) break; // 자리바꿈이 없다면 반복문 탈출
            
            for (int k = 0; k < numArr.length; k++)
                System.out.print(numArr[k]); // 정렬 출력
            System.out.println();
        }
    }
```
- 그림으로 보는 배열의 정렬
<img width="842" alt="arr_3" src="https://user-images.githubusercontent.com/71822139/216499273-daa8ec30-f150-40a2-9768-15f37eb5b31b.png">

### 빈도수 구하기

- 길이가 10인 배열을 만들고 0과 9사이의 임의의 값으로 초기화
- 배열에 저장된 **각 숫자가 몇번 반복해서** 나타나는지를 세어서 **배열 counter**에 담은 다음 화면에 출력

```java
public static void main(String[] args) {
int[] numArr =new int[10];
int[] counter =new int[10];

for(inti = 0; i < numArr.length; i++) {
        numArr[i] = (int) (Math.random() * 10);
        System.out.print(numArr[i]);
    }
    System.out.println();

for(inti = 0; i < numArr.length; i++)
        counter[numArr[i]]++;//배열 counter에서 배열 numArr에 저장된 값과 일치하는 인덱스의 요소에 저장된 값 1증가

for(inti = 0; i < numArr.length; i++)
        System.out.println(i + "의 개수 :" + counter[i]);
}
```

# 2. String 배열의 선언

## 1. String 배열의 선언과 생성

배열의 타입이 String인 경우에도 int 배열의 선언과 다르지 않다.

예를 들어 3개의 문자열을 담을 수 있는 배열을 생성하는 문장은 다음과 같다.

`String[] name = new String[3];`  ← **3개의 문자열**을 담을 수 있는 배열을 생성.

위의 문장을 실행하면,

- **3개의 String 타입의 참조변수를 저장하기 위한 공간**이 마련
- 참조형 변수의 기본값은 **null**이므로 각 요소의 값은 **null**로 초기화

## 2. String 배열의 초기화

- 초기화 역시 int 배열과 동일한 방법!
- 배열의 각 요소에 문자열을 지정

```java
String[] name = new String[3]; // 길이가 3인 String 배열 생성
name[0] = "Kim";
name[1] = "Park";
name[2] = "Yu";
```

- 또는 괄호{} 를 사용해서 다음과 같이 초기화 할 수 있다.

```java
String[] name = new String[] {"Kim", "Park", "Yu"};
String[] name = {"Kim", "Park", "Yu"}; // new String[] 생략가능
```

- 배열에는 실제 객체가 아닌 **객체의 주소**가 저장됨

```java
public static void main(String[] args) {
        String[] names = {"Kim", "Park", "Yi"};
        for (int i = 0; i < names.length; i++)
            System.out.println("names[" + i + "]: " + names[i]);

        String tmp = names[2]; // 배열의 세번째 요소를 tmp에 저장
        System.out.println("tmp: " + tmp);
        
        names[0] = "Yu"; // 배열 names의 첫번째 요소를 Yu로 변경
        for (String str : names) // 향상된 for문
            System.out.println(str);
    }
```

- 16진수를 2진수로 변환하는 예제

```java
public static void main(String[] args) {
        char[] hex = {'C', 'A', 'F', 'E'};
        String[] binary = {"0000", "0001", "0010", "0011",
                "0100", "0101", "0110", "0111",
                "1000", "1001", "1010", "1011",
                "1100", "1101", "1110", "1111"};
        String result = "";
        for (int i = 0; i < hex.length; i++) {
            if (hex[i] >= '0' && hex[i] <= '9') {
                result += binary[hex[i] - '0']; // '8'-'0'의 결과는 8
            } else {
                result += binary[hex[i] - 'A' + 10]; // 'C'-'A'의 결과는 2
            }
        }
        System.out.println("hex: " + new String(hex));
        System.out.println("binary: " + result);
    }
```

- 먼저 변환하고자 하는 16진수를 배열 hex에 나열
    - 16진수: A~F까지 6개의 문자 포함
    - char배열로 처리.
- 문자열 배열 binary에는 이진수 ‘0000’부터 ‘1111’(16진수로 0~F)까지 모두 16개의 값을 문자열로 저장.
- for문을 이용해서 배열 hex에 저장된 문자를 하나씩 읽어서 그에 해당하는 이진수 표현을 배열 binary에서 얻어 result에 덧붙이고 그 결과를 화면에 출력.

## 3. char 배열과 String 클래스

- 문자열을 저장할 때 String 타입의 변수를 사용함
- 사실 문자열 == 문자를 연이어 늘어놓은 것
- 문자배열인 char배열과 같은 뜻임.
- 자바에서 char배열이 아닌 String 클래스를 이용해서 문자열을 처리하는 이유는, String 클래스가 char 배열에 여러가지 기능을 추가해 확장한 것이기 때문임.

→ char 배열보다 String 클래스를 사용하는 것이 문자열을 다루기 더 편리함.

> String 클래스는 char배열에 기능(메서드)를 추가한 것
> 

- String 객체는 char 배열과 달리, 읽을 수만 있을 뿐 내용 변경 불가.

### String 클래스의 주요 메서드

| 메서드 | 설명 |
| --- | --- |
| char charAt(int index) | 문자열에서 해당 위치(index)에 있는 문자 반환 |
| int length() | 문자열 길이 반환 |
| String substrnig(int from, int to) | 문자열에서 해당 범위(from~to)에 있는 문자열 반환. (to는 범위에 포함x) |
| boolean equals(Object obj) | 문자열의 내용이 obj와 같은지 확인. 같으면 결과는 true, 다르면 false |
| char[] toCharArray() | 문자열을 문자배열(char[])으로 변환해 반환 |
1. charAt()
- charAt 메서드는 문자열에서 지정된 index에 있는 한 문자를 가져옴
- 배열에서 `배열이름[index]` 로 index에 위치한 값을 가져오는 것과 같음

e.g) 

```java
String str = "ABCDE";
char ch = str.charAt(3); // 문자열 str의 4번째 문자 'D'를 ch에 저장.
```

1. substring()
- 문자열의 일부 뽑음
- 범위의 끝은 포함되지 않음.

e.g)

```java
String str = "012345";
String tmp = str.substring(1,4);
System.out.println(tmp); // 123 출력
```

1. equals()
- 문자열의 내용이 같은 지 다른지 확인하는데 사용
- **기본형 변수**의 값을 비교하는 경우 `==` 연산자 사용
- 문자열의 내용을 비교할 때는 `equals()`
- 이 메소드는 대소문자 구분함에 주의
- 대소문자를 구분하지 않고 비교하려면 `equals()` 대신 `equalsIgnoreCase()` 를 사용해야.
    
    

### char배열과 String클래스의 변환.

- char배열을 String클래스로 변환하거나, 또는 그 반대로 변환해야 하는 경우.
- String 클래스의 `charAt(int idx)` 을 사용하는 방법을 보여주는 예제
    - charAt(int idx)은 문자열 중에서 idx번째 위치에 있는 문자 반환.
    - idx의 값은 배열처럼 0부터 시작.

```java
public static void main(String[] args) {
        String src = "ABCDE";

        for (int i = 0; i < src.length(); i++) {
            char ch = src.charAt(i); // src의 i번째 문자를 ch에 저장.
            System.out.println("src.charAt(" + i + "):" + ch);
        }
        // String →️ char[]
        char[] chArr = src.toCharArray();
        // char 배열 출력
        System.out.println(chArr);
    }
```

## 4. 커맨드라인을 통해 입력받기

- Scanner클래스의 nextLine() 외에도 화면을 통해 사용자로부터 값을 입력받을 수 있는 간단한 방법 → 커맨드라인
- 프로그램 실행시 **클래스 이름 뒤 공백문자로 구분**해 **여러개의 문자열을 프로그램에 전달** 가능.

```java
public static void main(String[] args) {
        System.out.println("매개변수의 개수: " + args.length);
        for (int i = 0; i < args.length; i++) {
            System.out.println("args [" + i + "] = \"" + args[i] + "\"");
        }
    }
```

- 커맨드라인에 입력된 매개변수는 `공백문자`로 구분하기 때문에 입력될 값에 공백이 있는 경우 큰따옴표(”)로 감싸주어야 한다.
- 그리고 커맨드라인에서 숫자를 입력해도 **숫자가 아닌 문자열**로 처리됨에 주의!
- 만약 문자열 “123”을 숫자 123으로 바꾸려면..
    - `int num = Integer.parseInt("123")` 으로 해야 함.
- 커맨드라인에 매개변수를 입력하지 않으면 크기가 0인 배열이 생성 → args.length의 값: 0
    - 크기가 0인 배열을 생성하는 것도 ok
    - but 입력된 매개변수가 없다고 해서, 배열을 생성하지 않으면, 참조변수 args의 값 == null
        - → 배열 args을 사용하는 모든 코드에서 에러 발생.
        - 에러를 피하려면, main 메서드에 `if문` 추가.
        
        ```java
        public static void main(String[] args) {
                if (args != null) { // args가 null이 아닐때만 괄호{}의 문장들을 수행.
                    System.out.println("매개변수의 개수: " + args.length);
                    for (int i = 0; i < args.length; i++) {
                        System.out.println("args [" + i + "] = \"" + args[i] + "\"");
                    }
                }
            }
        ```
        

# 3. 다차원 배열

## 1. 2차원 배열의 선언과 인덱스

- 1차원 배열과 같되, 괄호가 하나 더 들어감.
    
    
    | 선언 방법 | 선언 예 |
    | --- | --- |
    | 타입[][] 변수이름; | int[][] score; |
    | 타입 변수이름[][]; | int score[][]; |
    | 타입[] 변수이름[]; | int[] score[]; |
- 2차원 배열은 주로 테이블 형태의 데이터를 담는 데 사용, 4행 3열 데이터를 담기위한 배열
    - `int[][] score = new int[4][3];` 으로 선언.
    - 이때 각 배열요소의 타입인 int의 기본값인 0이 저장됨.
    - 배열을 생성하면, 배열의 각 요소에는 배열요소타입의 기본값이 자동저장됨.

### 2차원 배열의 index

- 행(row), 열(column)으로 구성됨
- 인덱스도 행,열에 각각 존재.
- 접근법: `배열이름[행 index][열 index]`

## 2. 2차원 배열의 초기화

- 2차원 배열도 괄호{}를 사용해 생성과 초기화를 동시에 가능
- 1차원 배열보다 괄호{}를 한번 더 써서 행별로 구분.
    
    ```java
    int[][] arr = new int[][] { {1,2,3}, {4,5,6} };
    int[][] arr = { {1,2,3}, {4,5,6} } // new int[][] 생략.
    ```
    
- 2차원 배열 score의 모든 요소의 합을 구하고, 출력하는 예제
    
    ```java
    public static void main(String[] args) {
            int[][] score = {
                    {100, 100, 100},
                    {20, 20, 20},
                    {30, 30, 30},
                    {40, 40, 40}
            };
            int sum = 0;
    
            for (int i = 0; i < score.length; i++) {
                for (int j = 0; j < score[i].length; j++) {
                    System.out.printf("score[%d][%d]=%d%n", i, j, score[i][j]);
                }
            }
            for (int[] tmp : score) { // 향상된 for문 -> 각 요소에 저장된 값들을 읽어올 수만 있음. 값 변경 불가.
                for (int i : tmp) {
                    sum += i;
                }
            }
            System.out.println("sum=" + sum);
        }
    ```
    

## 3. 가변배열

- 2차원 이상의 다차원 배열을 생성할 때 전체 배열 차수 중 마지막 차수의 길이를 지정하지 않고, 추후에 각기 다른 길이의 배열 생성 → 유동적인 가변 배열 구성 가능.

```java
int[][] score = new int[5][3]; // 5행 3열의 2차원 배열생성

// 다음과 같이 표현 가능
int[][] score = new int[5][]; // 2번째 차원길이 지정x
score[0] =new int[3];
score[1] =new int[3];
score[2] =new int[3];
score[3] =new int[3];
score[4] =new int[3];
```