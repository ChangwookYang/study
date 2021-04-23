# 람다식 정리!  (4/23)
  
람다식 자주 나오는데 잘모름..  
  
참고 사이트 : [람다식](https://juyoung-1008.tistory.com/48 "람다식")  
  
  
**Java8** 버전부터 람다식이 지원되었다.  
람다식은 익명함수를 생성하기 위한 식으로 객체 지향 언어보다 **함수지향언어**에 가깝다!  
람다 형태는 매개변수를 가진 코드 블록이지만, 런타임 시에는 **익명 구현 객체**(추상메소드를 한개 포함한)를 생성한다.  
  
  
함수형 프로그래밍은 병렬처리와 이벤트 지향 프로그래밍에 적합하여 딥러닝, 빅데이터와 더불어 문법적 트렌드로 관심받고있다.  
JAVA에서도 이런 트렌드를 따라갈 필요를 느낀 것 같으며, 람다식은 문법의 간결성으로 기존 자바 문법보다 쉽게 함수를 표현할 수 있다.  
  
  
**람다식은 결국 로컬 익명 구현객체를 생성하지만,**  
**람다식의 사용 목적은 인터페이스가 갖고 있는 메소드를 간편하게 즉흥적으로 구현해서 사용하는 것이 목적이다!**  
  
  
만약 한개의 추상메소드를 갖는 인터페이스가 있을때, 이 추상메소드를 구현해서 사용하기 위한 방법은 아래와 같다.

## 1. 인터페이스를 직접 클래스로 구현해서 메소드로 호출
```Java
@FunctionalInterface
public interface TestInterface {
  public int plusAandB(int a, int b);
}

public class  TestInterfaceImpl implements TestInterface {
  @Override
  public int plusAandB(int a, int b){
     return a + b;
  }
}

public class Main {
  public static void main(String[] args){
    TestInterface t1 = new TestInterfaceImpl();
    sysout(t1.plusAandB(3, 4));
  }
}
```  
위와 같은 방법으로 구현 시 인터페이스를 구현한 클래스를 재사용할 수 있는 장점이 있지만  
재사용이 필요하지 않는 메소드를 만들어 사용해야할 때도 있을 것이다.  
그런것들을 클래스로 구현하면 불필요한 class 파일이 늘어나게 될 것이다.  

## 2. 인터페이스를 익명구현 객체로 구현해서 메소드를 호출
```Java
public class Main {
  public static void main(String[] args){
    TestInterface t2 = new TestInterface(){
       
       @Override
       public int plusAandB(int a, int b){
          return a + b;
       }
    }
  }
}
```
위 처럼 익명 구현 객체를 사용하게 된다면 불필요한 클래스 파일이 생기는걸 막고 1번보다 간결하다.
  
  
## 3. 람다식을 이용해서 더 간결하게 인터페이스 구현
```Java
public class Main {
  public static void main(String[] args){
	TestInterface t3 = (a, b) -> {return a+b;};
	sysout(t3.plusAandB(3, 4));
  }
}
``` 

# 함수적 인터페이스와 람다식 기본 문법  
람다식을 사용하기 위해서는 구현할 인터페이스가 필요하다.  
람다식으로 구현하기 위한 인터페이스는 조건이 하나 있는데 **한개의 추상메소드만 가지고 있어야한다**는 것이다.  
그리고 이런 인터페이스를 미리 **함수적 인터페이스(@functionalInterface)**라고 부른다.  
즉, 함수구현 전용 인터페이스라고 부르는 것이다.  
@FunctionalInterface 어노테이션으로 이런 함수적 인터페이스를 명시할 수 있다.  
  
@FunctionalInterface 인터페이스가 적용된 인터페이스는 한개의 추상메소드만 선언할 수 있게 된다.  
@FunctionalInterface 가 선언된 인터페이스에 추상메소드가 1개가 아니면 에러가 발생한다.  
```Java
@FunctionalInterface
public interface TestInterface {
   public int plusAandB(int a, int b);
}
```
  
## 람다식 기본구조
람다식의 기본구조는 다음과 같다.  
소괄호에는 구현한 함수의 인자를 그리고 화살표 다음에 중괄호에는 구현할 함수 몸체를 넣어주면 된다.  
```javascript
// (타입 매개변수, ...) -> {실행문;...}
```
  
함수를 간편하고 쉽게 표현하기위해서 람다는 많은 생략 기법을 사용한다.  
* 람다식 매개인자의 자료형은 생략가능하다.  
* 람다식의 매개인자가 한개인 경우 매개인자를 감싸는 소괄호를 생략할 수 있다.  
* 람다식의 함수 몸체에 실행문이 한개인 경우 함수 몸체를 감싸는 중괄호를 생략할 수 있다.  
* 람다식의 함수 몸체에 실행문이 한개이고, 그 실행문이 return일 경우 함수의 몸체를 감싸는 중괄호와 return을 생략할 수 있다.  
  
```Java
InterfaceA1 a1 = (int a) -> {sysout("a:" + a); };
// 매개인자 자료형 생략
InterfaceA1 a2 = (a) -> {sysout("a:" + a); };

InterfaceB1 b1 = (int a, int b) -> {sysout("a+b:" + (a+b)); };
// 매개인자 자료형 생략
InterfaceB1 b2 = (a, b) -> {sysout("a+b:" + (a+b));};

// 매개인자 하나뿐이라 소괄호 생략
InterfaceA1 a3 = a -> {sysout("a:" + a); };
// 함수 실행문이 한개라 중괄호 생략
InterfaceA1 a4 = a -> sysout("a:" + a);

TestIntercace t3 = a -> {return "a:" + String.valueOf(a); };
// 함수의 실행문이 한개이며, 리턴문만 있을 경우 중괄호와 더불어 return문도 생략 가능하다.
TestInterface t4 = a -> "a:" + String.valueOf(a);

// 매개인자가 없는 경우에는 빈 소괄호르 사용해야한다.
InterfaceA1 a2 = () -> {sysout("인자 없는 함수 구현");

```
