# 배열

데이터가 많아지면 **그룹 관리**의 필요성이 생긴다. 이럴 때 사용하는 것이 **배열**

여러 데이터를 하나의 이름으로 그룹핑해서 관리하기 위한 **데이터 스터럭쳐**

</br>

## 배열이란?

배열이란 연관된 데이터를 하나의 변수에 그룹핑해서 관리하기 위한 방법

배열을 이용하면 하나의 변수에 여러 데이터를 담을 수 있고, 반복문과 결합하면 많은 정보도 효율적으로 처리할 수 있다.

</br>

## 배열의 용어

아래는 배열을 사용하고 있는 간단한 자바 코드이다. 이 코드를 이용해서 배열과 관련된 중요한 용어를 먼저 살펴보겠다.

</br>

``` java
String[] student = new String[5];
	{
		student[0] = "최진혁";
		student[1] = "한이람";
		student[2] = "최유빈";
		student[3] = "한이은";
		student[4] = "김주한";
	}
```

</br>

`new String[5]`는 5개의 데이터를 담을 수 있는 크기의 배열을 만든다. 이것을 변수 `student`에 대입한다. `student[0]`은 첫 번째 배열의 값이고 문자열 최진혁을 값으로 대입하고 있다. 이것을 그림으로 나타내면 아래와 같다. 

</br>

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2788.gif)

</br>

위의 그림에서 최진혁은 배열에 저장된 값이고, 숫자 0은 최진혁이라는 값을 식별하는 인덱스이다. 이 인덱스를 이용해서 최진혁이라는 값을 가져올 수 있다. 값 최진혁과 인덱스 0을 합쳐서 엘리먼트라고 한다.

</br>

## 배열의 사용

배열은 매우 다양한 용도로 사용할 수 있는 데이터 스트럭쳐이다.

학급을 프로그래밍적으로 표현하기엔 배열이 좋다. 선생님이 학생의 이름을 기억하는 것은 어려운 일이기 때문에 학교에서는 학생들에게 번호를 부여한다. 이 번호는 학년이 바뀔 때까지 절대 바뀌지 않는다. 전학을 가면 그 번호는 결번이 되고, 전학을 오면 마지막 번호에 추가된다.

여기서 학생은 배열에서 하나의 엘리먼트로 표현할 수 있다. 학생의 이름은 배열의 값, 학생의 인덱스는 학번으로 기능할 수 있다. 위에서 5명이 소속된 학급을 배열로 만들었다. 만약 한이은 학생의 데이터를 가져오고 싶다면 아래처럼 인덱스 3을 이용하면 된다.

</br>

``` java
System.out.println(student[3]);
```

```
한이은
```

</br>

메소드 `System.out.println()`은 인자로 전달된 값을 출력하는 역할을 한다.

배열에는 여러 정보가 저장되어 있고, 이러한 다수의 정보를 처리하기 위한 방법은 반복문이다. 그래서 배열과 반복문은 바늘과 실의 관계라고 할 수 있다. 아래는 자바에서 반복문으로 데이터를 처리하는 모습이다.

</br>

``` java
int i = 0;
while(student.length > i) {
    System.out.println(student[i]);
    i++;
}
```

```
최진혁
한이람
최유빈
한이은
김주한
```

</br>

``` java
for(int i = 0; i < student.length; i++) {
    System.out.println(student[i]);
}
```

```
최진혁
한이람
최유빈
한이은
김주한
```

</br>

`배열.length`는 배열의 길이를 의미한다. 이 값을 이용해서 몇 번 순회할지를 결정할 수 있다.

</br>

``` java
System.out.println(student.length);
```

```
5
```

</br>

## 배열의 단점

1. 크기가 정해져 있다.

2. 기능이 없다.

</br>


## 배열의 장점

1. 크기가 정해져 있다.

2. 기능이 없다.

자바 개발자는 배열을 좋은 부품으로 사용하려고 한다.

좋은 부품은 작고 가볍고 단순하다. (크기가 정해져 있어 빠르고 메모리를 적게 사용한다.)

배열은 다른 자료구조에서 좋은 부품으로 사용된다.

</br>

## 배열의 한계

배열은 좋은 데이터 표현방법이다. 하지만 배열로 모든 것을 해결할 수는 없다. 위의 예제에서 한이은 학생이 전학을 갔다고 하면, 아래와 같이 처리할 수 있다.

</br>

``` java
student[3] = null;
```

</br>

이것을 그림으로 표현하면 아래와 같다.

</br>

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2792.gif)

</br>

null은 값이 없다는 뜻이고, 위의 반복문으로 이것을 실행하면 아래와 같은 결과가 출력된다.

</br>

```
최진혁
한이람
최유빈
null
김주한
```

</br>

위의 실행결과에는 null이 포함되어 있다. 즉 처리되지 않아야 할 정보인 인덱스 3까지 결과에 포함되어 있고, 조건문으로 제외해도 된다.

</br>

``` java
for(int i = 0; i < student.length; i++){
  if(student[i] != null) {
    System.out.println(student[i]); 
  }
}
```

```
최진혁
한이람
최유빈
김주한
```

</br>

이것도 좋은 방법이지만 위와 같은 반복문이 수십 개 등장한다면 그만큼 조건문도 많아진다. 이것이 배열의 단점이다. 배열은 인덱스에 따라서 값을 유지하기 때문에 엘리먼트가 삭제되어도 빈자리가 남게 된다. 

그렇다면 존재하지 않는 데이터는 아예 없애버리는 것이 좋다.

</br>

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2790.gif)

</br>

즉 삭제한 자리를 뒤에 위치한 엘리먼트로 메꾸면 된다. 이렇게 데이터가 순서에 따라서 빈틈없이 연속적으로 위치하는 데이터 스트럭쳐를 리스트(list)라고 한다. 그런데 이렇게 해도 문제가 있다. 김주한 학생의 식별자인 인덱스 값이 4에서 3이 되었다. 만약 인덱스 4를 이용해서 김주한 학생의 값을 가져오는 프로그램이 있다면 문제가 생긴다. 

이럴 경우, 인덱스가 중요한 경우에는 배열을 사용하고, null를 처리에서 제외해야 한다면 조건문을 사용하면 된다. 인덱스가 중요하지 않은 경우에는 리스트를 사용하면 된다.

</br>

## 결론

배열은 거의 모든 언어에 포함된 데이터 스트럭쳐이다. 하지만 배열만으로는 부족한 경우가 생긴다. 이런 경우에 보다 적합한 데이터 스트럭쳐를 고안해야 된다. 하지만 대부분의 데이터 스트럭쳐들은 모두 직간접적으로 배열을 부품으로 사용한다. 따라서 배열에 대한 이해는 모든 데이터 스트럭쳐 이해의 공통요소라고 할 수 있다.