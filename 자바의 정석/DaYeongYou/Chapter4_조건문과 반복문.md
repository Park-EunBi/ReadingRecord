# 1. 조건문-if, switch

- 조건식과 문장을 포함하는 블록으로 구성됨
- 조건식의 연산결과에 따라 프로그램의 실행흐름 변경 가능
- 처리해야할 경우의 수가 많을 경우 switch 문을 사용해 표현할 수 있는지 살펴봐야 함
- 모든 switch 문 → if문 변경 가능, but 모든 if문 → switch 문 변경 불가

## 1.1 if문

```java
class FlowEx1 {
    public static void main(String[] args) {
        int visitCount = 0;
        if (visitCount < 1) {
            System.out.println("처음 오셨군요. 방문해 주셔서 감사합니다.");
        }
    }
}
```

- 변수 `visitCount` 에 저장된 값이 0이므로, 조건식 `visitCount < 1` 의 결과가 0<1 이 되어 조건식의 연산결과가 true가 되고 if문의 블록에 있는 출력문이 실행됨

```java
public class FlowEx2 {
    public static void main(String args[]) {
        int visitCount = 5;
        if (visitCount < 1) {
            System.out.println("처음 오셨군요. 방문해 주셔서 감사합니다.");
        } else {
            System.out.println("다시 방문해 주셔서 감사합니다.");
        }
        System.out.println("방문 횟수는 " + ++visitCount + "번 입니다.");
    }
}
```

- `visitCount` 에 저장된 값이 5이므로 if문의 조건식이 false가 되어 else 블록의 문장  수행

```java
public class FlowEx3 {
    public static void main(String[] args) {
        int score = 45;
        char grade = ' '; // 학점을 저장하는 변수. 공백으로 초기화
        if (score >= 90) {
            grade = 'A';
        } else if (score >= 80) {
            grade = 'B';
        } else {
            grade = 'C';
        }
        System.out.println("당신의 학점은 " + grade + "입니다. ");
    }
}
```

- if문은 삼항연산자로 바꿀 수 있는 경우가 많음.
    
    e.g) if문 대신 삼항연산자로 변경한 경우
    
    ```java
    public class FlowEx4 {
        public static void main(String[] args) {
            int score = 45;
            char grade = ' ';
            grade = (score >= 90) ? 'A' : ((score >= 80) ? 'B' : 'C');
            System.out.println("당신의 학점은 " + grade + "입니다. ");
        }
    }
    ```
    

## 1.2 중첩 if문

- if문 블록 안에 또 다른 if문 사용
- 중첩 횟수에는 제한 없음

```java
public class FlowEx5 {
    public static void main(String[] args) {
        int score = 82;
        String grade = "";
        System.out.println("당신의 점수는 " + score + "입니다. ");
        if (score >= 90) {
            grade = "A";
            if (score >= 98) {
                grade += "+";
            } else if (score < 94) {
                grade += "-";
            }
        } else if (score >= 80) {
            grade = "B";
            if (score >= 88) {
                grade += "+";
            } else if (score < 84) {
                grade += "-";
            }
        } else {
            grade = "C";
        }
        System.out.println("당신의 학점은 " + grade + "입니다. ");
    }
}
```

- 제일 바깥 쪽에 있는 if문에서 점수에 따라 학점(grade)을 결정
- 내부의 if문에서 학점을 더 세부적으로 나눠서 평가 → 결과 출력
- 학점을 저장하기 위해 char 대신 String 사용
    - char은 한 문자밖에 저장 불가
    - 두 문자 이상을 저장하는 데는 String을 사용
    - String 타입의 변수를 초기화 할 때는 보통 String grade=””; 와 같이 빈 문자열 사용
        - char 변수를 초기화 할 때는 char grade=’’; 와 같이 할 수 없음.
        - char 타입의 변수는 공백(’ ‘)으로 초기화

## 1.3 switch문

- 조건의 경우의 수가 많을 때는 if 문 보다 switch문을 사용하는 것이 더 간결하고 알아보기 쉬움.
- if문의 조건식의 결과가 true, false 두가지 밖에 없기 때문에 경우의 수가 많아질수록 계속 else-if문을 추가해야 함.
- 그러나 switch문의 조건식은 결괏값으로 int형 범위의 정수값 허용 → 하나의 조건식만 계산하면 그 결과에 따라면 해당 문장들 수행 - 같은 기능의 if문보다 속도 빠름

```java
public class FlowEx6 {
    public static void main(String[] args) {
        // Math class-random() 함수 : 1~10사이 값 추출
        int score = (int) (Math.random() * 10) + 1;

        switch (score * 100) {
            case 100:
                System.out.println("당신의 점수" + 100 + "점 이고, 상품은 자전거 입니다.");
                break;
            case 200:
                System.out.println("당신의 점수" + 200 + "점 이고, 상품은 TV 입니다.");
                break;
            case 300:
                System.out.println("당신의 점수" + 300 + "점 이고, 상품은 노트북 입니다.");
                break;
            case 400:
                System.out.println("당신의 점수" + 400 + "점 이고, 상품은 자동차 입니다.");
                break;
            default:
                System.out.println("당신의 점수에 해당하는 상품은 없습니다.");
        }
    }
}
```

### 임의의 정수 만들기

- **Math.random()** - 0.0과 1.0 사이의 임의의 double값을 반환
    - 0.0 <= Math.random() < 1.0
        1. 각 변에 원하는 개별 값을 곱한다.
        2. 각 변을 int형으로 변환한다.
        3. 각 변에 1을 더한다.
    
    e.g)
    
    `1 <= (int)(Math.random() * 3) + 1 < 4 // 1 ~ 3 중 임의의 정수
    -5 <= (int)(Math.random() * 11) - 5 < 6 // -5 ~ 5 중 임의의 정수`
    

- e.g) score 값을 1로 고정, switch의 break 문 제거

```java
public class FlowEx8 {
    public static void main(String[] args) {
        int score = 1;

        switch (score * 100) {
            case 100:
                System.out.println("당신의 점수" + 100 + "점 이고, 상품은 자전거 입니다.");
            case 200:
                System.out.println("당신의 점수" + 200 + "점 이고, 상품은 TV 입니다.");
            case 300:
                System.out.println("당신의 점수" + 300 + "점 이고, 상품은 노트북 입니다.");
            case 400:
                System.out.println("당신의 점수" + 400 + "점 이고, 상품은 자동차 입니다.");
            default:
                System.out.println("당신의 점수에 해당하는 상품은 없습니다.");
        }
    }
}
```

- score 값이 1이므로 switch 문의 조건식 결과값은 100이 된다. 그래서 `case 100:` 으로 이동후 break문이 없으므로 ****그 이하 모든 문장 수행
- 이러한 switch 문의 성질을 이용할 경우도 있음
    - 회원제로 운영되는 인터넷 사이트에서 많이 사용될 만한 코드
        
        ```java
        switch (level){
        	case 3:
        			grantDelete();  // 삭제 권한을 준다.
        	case 2:
        			grantWrite();   // 쓰기 권한을 준다.
        	case 1:
        			grantRead();    // 읽기 권한을 준다.
        ```
        
        - 로그인한 사용자의 등급(level) 체크 → 등급에 맞는 권한 부여
        - 제일 높은 등급인 3을 가진 사용자는 grantDelete(), grantWrite(), grantRead()가 모두 수행되어 읽기, 쓰기, 삭제 기능까지 모두 가짐.
        - 제일 낮은 등급인 1을 가진 사용자는 읽기 권한만 가짐.
- switch 문은 **조건식을** 잘 만들어내는 것이 중요
- 5점 단위로 학점 부여하는 예제
    
    ```java
    public class FlowEx11 {
        public static void main(String[] args) {
            int score = 84;
            String grade = "";
    
            switch (score / 5) { // 5점 단위로 학점 부여 99~95 -> A+ 94~90 -> A- 89~85 -> B+ 84~80 -> B-
                case 20:
                case 19:
                    grade = "A+";
                    break;
                case 18:
                    grade = "A-";
                    break;
                case 17:
                    grade = "B+";
                    break;
                case 16:
                    grade = "B-";
                    break;
                default:
                    grade = "F";
            }
            System.out.println("당신의 학점: " + grade + "입니다.");
        }
    }
    ```
    

# 2. 반복문 for, while, do-while

## 2.1 for문

![image](https://user-images.githubusercontent.com/71822139/212312731-3b05f113-d133-43ad-84ac-c436d7ae799a.png)
1. 초기화
2. 조건식
3. 수행될 문장
4. 증감식
- for문은 4부분으로 이뤄짐
- 이때 초기화는 처음에만 한번 수행
- 그 이후부터 조건식을 만족하는 한 '2->3->4'의 순서로 계속 반복
- 조건식의 결과가 false 시 for문 탈출
- 조건식, 증감식 모두 생략 가능
- 조건식은 생략시 true로 간주

```java
  // for문 작성 예-1
      for (; ; ) {
          // 반복해서 수행할 문장들
      }
```
- 조건식이 없기 때문에 결과가 true로 간주
- 블록 안의 문장들을 무한히 반복수행

```java
// for문 작성 예-2
    for (int i=0; ; ) {
        // 반복해서 수행할 문장들
    }
```
- for문에 int형 변수 i를 선언
- 0으로 초기화
- **변수 i는 for문 내에 선언**
  - 따라서 for문 내에서만 유효
  - 만약 for문 바깥에서 i를 사용한 경우 `Unreachable statement` 에러 발생!
  - 따라서 도달할 필요가 없기 때문에 지워야 하지만, 도달해야 할 필요가 있다면 코드를 변경해야 한다.
    ```java
    // for문 작성 예-3
        int i; // 선언부분을 for문 밖으로 옮겼다.
        for (i=0; ; ) {
            // 반복해서 수행할 문장들
        }
        System.out.println(i);

    ```
    - 변수 i를 for문 밖에서도 사용할 수 있도록 i의 선언부분을 for문 밖으로 빼냄.
    - i는 main 메서드 내에서 선언된 변수 이므로 for문 이후에도 유효
    - 그러나 for문의 "카운터" 로 사용되는 변수는 주로 for문의 블럭{} 내에서만 사용되기 때문에 for문 내에 선언 해서 for문이 끝나고 나면 없어지도록 하는 것이 좋음.(또 다른 반복문에서 다시 재사용 가능)
> for문 예제
```java
// 1부터 10까지의 합을 구하는 예제
  public class FlowEx12 {
    public static void main(String[] args) {
        int sum = 0; // 합계를 저장하기 위한 변수
        for (int i = 1; i <= 10; i++) {
            sum += i;
            System.out.println(i + " 까지의 합: " + sum);
        }
    }
}
```
```java
// 0과 10사이에 있는 짝수들의 합 구하는 예제
public class SumOdd {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 0; i <= 10; i += 2) {
            sum += i;
            System.out.println(i + " : " + sum);
        }
    }
}
```
- for문 증감식에 카운터 i의 값을 2씩 증가시키기 위해 i+=2 사용
- 카운터의 값을 원하는 만큼 값을 증가, 감소 가능
- 증감식 역시 for문의 초기화 부분처럼 쉼표(,) 를 넣어 여러 문장들을 넣을 수 있음

> 중첩 for 문 예제
```java
// 구구단 출력
public class NestedForLoop {
    public static void main(String[] args) {
        for (int i = 2; i <= 9; i++) {
            for (int j = 1; j <= 9; j++) {
                System.out.println(i + " * " + j + " = " + i * j);
            }
        }
    }
}
```
- i는 단을 출력하는데 사용
- j는 1부터 9까지의 곱에 사용
- 중첩 for문의 경우 외부 for문의 반복회수와 내부 for문의 반복회수를 곱한만큼 반복됨
- 외부 반복문이 한번 반복될때마다 내부 반복문 전체가 반복됨

```java
// 10부터 1까지 1씩  감소하면서 출력하는 예제
public class Countdown {
    public static void main(String[] args) {
        System.out.println("카운트 다운 시작");
        for (int i = 10; i >= 0; i--) {
            for (int j = 0; j < 1000000000; j++) {
                ;
            }
            System.out.println(i);
        }
        System.out.println("game over");
    }
}
```
- 매 출력마다 약 1초의 시간 지연
- 빈 문장(;)을 적어주긴 했지만 생략 가능

## 2.2 while문
![image](https://user-images.githubusercontent.com/71822139/212323279-b7ae0a6e-26b6-4a59-998c-dae67f598291.png)
- 조건식을 만족하는 동안 블록{} 반복 -> 반복 횟수가 정해지지 않았을 때 사용
> while 예제
```java
// while문으로 구구단 출력하기
public class TimesTable {
    public static void main(String[] args) {
        int i = 2; // 2단부터 시작
        while (i <= 9) {
            int j = 1; // 곱해지는 수
            while (j <= 9) {
                System.out.println(i + " * " + j + "=" + i * j);
                j++;
            }
            i++;
        } // end of while(i<=9)
    }
}
```
```java
// 1부터 몇까지 더하면 누적합계가 100에 가까워 지는지 구하는 예제
public class IsNearest {
    public static void main(String[] args) {
        int sum = 0;
        int i = 0;

        while (sum + i <= 100) {
            sum += ++i;
            System.out.println(i + "-" + sum);
        }
    }
}
```
## 2.3 do-while문
- while문의 변형
- 기본 구조는 while문과 같으나 블록({})이 먼저 수행한 후에 조건식을 판단하는 것이 while문과의 유일한 차이점
- while문은 조건식의 결과에 따라 블록({})이 한번도 수행되지 않을 수 있지만, do-while문은 최소한 한번 수행을 보장
> do-while 예제
```java
public class DoWhile {
    public static void main(String[] args) throws java.io.IOException {
        int input = 0;
        System.out.println("문장을 입력.");
        System.out.println("입력을 마치려면 x를 입력");
        do {
            input = System.in.read();
            System.out.print((char) input);
        } while (input != -1 && input != 'x');

    }
}
```

- `System.in.read()` 을 이용해 화면을 통해 사용자로부터 입력 받음
- 입력받은 내용을 다시 화면에 출력함
- 일단 사용자로부터 입력을 받은 후 입력받은 문자를 검사하므로 while문 보다는 do-while문이 적합함.
- 사용자가 'x'입력 또는 'ctrl+z' 입력시 `do-while`문을 빠져나가 프로그램 종료
  - 사용자가 입력한 내용을 편집할 수 있도록 하기 위해
  - 입력된 내용이 곧바로 프로그램으로 전달되는 것이 아니라
  - 사용자가 입력한 내용이 버퍼에 저장되어 있다가 `Enter 키`를 눌러야만 `System.in.read()`으로 전달됨
  - 화면에서 한 번에 여러 글자를 입력할 수 있지만 사실 `System.in.read()` 은 한 번에 한 문자 밖에 못 읽음.
  - `System.in.read()` 은 사용자가 입력한 문자를 `int형`으로 반환하므로 문자가 아닌 `문자의 코드값`이 반환됨.
  - 화면으로부터 입력받은 문자를 다시 출력하기 위해 `char형`으로 변환해야 함
  - 그리고 `System.in.read()`은 사용자가 입력한 문자가 'ctrl+z'이면 -1 반환
  - 화면을 통해서 사용자로부터 입력받는 방법은 잘 사용 x
    - `System.in.read()` 대신 앞으로 배울 `Scanner 클래스`를 사용하면 더 편리함.
  

## 2.4 break 문
- **현재 위치에서 가장 가까운** 반복문(for, switch 등)을 벗어나는 데 사용
- 주로 if문과 함께 사용되어 특정 조건을 만족하면 반복문을 벗어나도록 함.
```java
// 1부터 몇까지 더하면 합이 100을 넘는지 알아보는 예제
public class WhenOver100 {
    public static void main(String[] args) {
        int sum = 0;
        int i = 0;
        while (true) {
            if (sum > 100)
                break;
            ++i;
            sum += i;
        }//  end of while
        System.out.println("i= " + i);
        System.out.println("sum=" + sum);
    }
}
```
## 2.5 continue 문
- 반복문 내에서만 사용 가능
- continue를 만나면, 반복문의 끝으로 이동해 다음 반복으로 넘어감
  - for의 경우) 증감식 으로 이동
  - while의 경우) 조건식 으로 이동
- 반복문을 벗어나지 않고 다음 반복을 계속 수행한다는 점이 break와의 차이임.
- 전체 반복 중 특정조건을 만족하는 경우를 제외하고자 할 때 유용함!
```java
// 1부터 10 사이 3의 배수 제외하고 출력하는 예제
public class ExceptMultipleOf3 {
    public static void main(String[] args) {
        for (int i = 0; i <= 10; i++) {
            if (i % 3 == 0) // 3으로 나눴을때 나머지가 0이면 3의 배수임. 
                continue; // 다음 반복으로 넘어감
            System.out.println(i);
        }
    }
}
```

## 2.6 이름 붙은 반복문
- 여러 반복문이 중첩되었을 때 반복문 앞에 이름을 붙이고
- break문과 continue문에 이름을 지정 
- 하나 이상의 반복문을 벗어나거나 반복을 건너뛸 수 있음
![image](https://user-images.githubusercontent.com/71822139/212330456-845608cc-3494-496f-b9fd-1207803ed1b3.png)

```java
// 구구단을 출력하는 예제
public class LabledLoop {
    public static void main(String[] args) {
        Loop1:  // for문에 Loop1 이라는 이름을 붙임
        for (int i = 2; i <= 9; i++) {
            for (int j = 1; j <= 9; j++) {
                if (j == 5)
                    break Loop1;
                // break;
                // continue;
                System.out.println(i + "*" + j + "=" + i * j);
            } // end of for i
            System.out.println();
        }//end of Loop1
    }
}
```
- 제일 바깥에 있는 for문에 Loop1 이라는 이름 붙임
- 그리고 j가 5일때 break 수행
- 반복문의 이름이 지정되지 않은 break문은 자신이 속한 하나의 반복문만 벗어날 수 있음
- 반복문에 이름을 붙여줄 경우 break문에 반복문 이름을 지정해주면 하나이상의 반복문도 벗어날 수 있음.
