---
sort: 1
title: 객체지향 프로그래밍 개념정리
tags: [ OOP ]
---

## 객체지향 프로그래밍

### 객체

  * 객체는 속성(Property)과 행동(Operation, Method)을 가진다.
  * 이러한 속성과 행동을 모두 합쳐 특성(Feature)이라고 부른다.

### 객체지향 프로그래밍의 4대 요소

  * 추상화
    * 객체를 모델링할 때, 필요로 하는 만큼 속성과 오퍼레이션을 추출해내는 것을 말한다
    * 구현대상을 모델링할 때, 그 대상의 모든 특성을 추출해낼 수없다.  
      구현에 있어서 필수적인 것들만 추출하고 구현해야 한다.
  * 캡슐화
    * 객체는 자신의 동작원리를 클래스라는 껍데기로 캡슐화한다
    * 객체 자신만이 행동이 어떻게 작동하는지 안다. 
    * 외부에선 알 수 없다.
  * 상속
    * 수퍼클래스가 서브클래스에게 자신의 특성(속성+행동)을 물려주는것을 말한다.
    * 특성을 물려받은 서브클래스는 자신만의 특성을 추가할 수 있다.
    * 또는, 물려받은 행동의 정의를 수정할 수 있다. (오버라이드)
  * 다형성
    * 같은 이름의 행동이 객체의 클래스에 정의된 내용에 따라 각기 다른 행동을 하는걸 말한다.

### 일반화(Generalization)

  * 객체지향에선 상속이라고 부르는데, UML에선 일반화라고 부른다  
    라고 책에 쓰여있다.(초보자를 위한 UML 객체지향설계-인포북-Joseph Schmuller)
  * 객체들의 일반적인 특성(속성 + 행동)을 찾고, 이걸로 수퍼클래스를 만든다.
  * 그런 다음, 수퍼클래스에서 서브클래스들에게 일반적인 특성을 상속해준다.
  * 예를들면, 직사각형, 삼각형, 직선은 일반적으로 꼭짓점배열을 가지며, 크기를 구하는 행동이 있다고 치자.
  * 꼭짓점 배열과 크기를 구하는 행동을 일반적인 특성으로 보고, 이걸로 Shape라는 수퍼클래스를 만든다.
  * 그리고 Rectangle, Triangle, StraightLine클래스에 Shape를 상속해준다.
  * 이렇게 일반화 관계를 상속으로 표현할 수 있다.
    ![generalization](https://user-images.githubusercontent.com/41663269/104588385-9e4a5500-56ab-11eb-89fe-5ad5ef687763.png)

### 객체 간 통신(커뮤니케이션)

  * 객체와 객체는 메세지를 주고 받는걸로 관계를 실현한다.
  * 객체와 객체는 메세지를 주고 받으면서 상호작용하게 된다.

### 객체간의 관계

  * 객체는 다른 객체와 연관관계를 가질 수 있다.

  * 방향성

    * 사람이 TV를 키다.
    * 사람 -켜다-> TV
    * 사람과 TV는 단방향성 연관을 가지는 것.

  * 다중성

    * 하나의 객체는 특정한 집합 내에서 여러 객체와 연관될 수 있다.

      ```
        사람-----타다------> 버스  
          |
          |------타다------> 자가용
      ```

    * 이런 경우, 버스랑 자가용 객체는 하나의 수퍼클래스(Vehicle-차량)로 구현할 수 있다.

      > ex: Class Vehicle  
      >
      > > Class Bus  extends Vehicle  
      > >  Class Car extends Vehicle  

    * 집합연관

      * 하나의 객체가 다른 객체들의 조합에 의해 만들어진 경우이다.

        ```
          비행기 -------- 날개 -------- 주익
            |              |---------- 미익
            |
            |-------------- 엔진
            |-------------- 콕핏
            |-------------- 동체
        
        ```

    * 복합연관

      * 집합연관의 한 형태이다.
      * 집합체 전체와 그 구성 객체들이 서로 밀접한 관계를 가지는 
      * 복합체가 소멸하면 구성 컴포넌트도 따라서 소멸한다.

***

## 예제

### Shape 클래스

*   모든 도형의 수퍼 클래스다.
*   직선, 삼각형, 직사각형 클래스는 Shape클래스를 상속받아서 구현한다.
*   서브 클래스한테 물려줄 기능
    *   직선, 삼각형, 직사각형 클래스에 공통적으로 필요한 기능들을 구현해서 물려준다.
    *   좌표계에 출력하는 행동을 구현해서 물려준다.
*   크기를 구하거나 출력하는 행동은 도형객체의 클래스에 따라 각각 다르다. 
    *   이건 추상메서드로 선언한다.
    *   서브클래스에선 이 추상메서드를 자신에게 맞게 오버라이드 해야 한다.
        ![ShapeUML](https://user-images.githubusercontent.com/41663269/104589930-f1250c00-56ad-11eb-94c5-6a492e2f2152.png)

## 실제 코드

###   Shape 클래스 (Super)

```java
    public abstract class Shape {
            protected ArrayList<Coordinate> vertices;
            //도형의 크기를 구합니다. 직선의 경우 길이를 구합니다.
            public abstract double getSize();
            //도형의 크기를 출력합니다.
            public abstract void displaySize();
            //도형을 좌표계에 출력합니다.
            public void display(){/*...*/}
    }
```

*   display는 Rectangle, Triangle, StraightLine이던 동일하게 동작한다.   
    그래서 추상메서드가 아닌 정의된 메서드로 물려준다.  
    이러면 서브클래스에선 이 코드를 재사용할 수 있다.   
*   반면 displaySize나 getSize는 클래스에 맞게 정의해야한다.  
    그래서 이 메서드는 추상메서드로 물려준다.

###   Rectangle 클래스 extends Shape

```java
    public class Rectangle extends Shape{
            /*...*/
            @Override
            public void displaySize() {
                System.out.printf("사각형의 넓이는 %f%n", this.getSize());
            }
            @Override
            public double getSize() {
                TreeSet<Double> setX = new TreeSet<Double>();
                TreeSet<Double> setY = new TreeSet<Double>();
                /*...*/
                return width * height;
            }
    }
```

*   Rectangle클래스는 자신에게 맞게 추상메서드를 오버라이드했다.

###   Triangle 클래스 extends Shape

```java
    public class Triangle extends Shape{
            @Override
            public double getSize() {
                /*...*/
                return Math.sqrt( 4*aSquared*bSquared - tmp*tmp ) / 4;
            }
            @Override
            public void displaySize() {
                System.out.printf("삼각형의 넓이는 %f%n", this.getSize());
            }
    }
```

*   Triangle 클래스도 추상메서드를 자기 자신에 맞게 오버라이드한다.

###    StraightLine 클래스

*   StraightLine클래스도 마찬가지로 상속받고 오버라이드한다.

###    메인 클래스

* 이렇게 해서 3개의 도형클래스의 일반적인 특성을 가지고 일반화해서 Shape클래스를 만들고 상속해주는 코드를 짰다. 

*   이러면 Shape클래스의 getSize, displaySize라는 같은 이름으로, 서로 다른 객체의 getSize, displaySize메서드를 호출할 수 있다.

    ```java
    class Main{
        public static void main(String[] args){
            ArrayList<Shape> shapeList = new ArrayList<Shape>();
            shapeList.add(new StraightLine());
            shapeList.add(new Triangle());
            shapeList.add(new Rectangle());
            for (Shape s : shapeList){
                s.display();
                s.displaySize();
            }
        }
    }
    ```

*   StraightLine, Triangle, Rectangle 클래스는 Shape클래스를 상속받았기 때문에  
    Shape클래스로 업캐스팅(Up-Casting)할 수 있다.

    *   이 경우, 수퍼클래스, 즉 Shape클래스에 선언되어 있는 메서드만 호출할 수 있다.
    *   앞서 일반화를 하면서 getSize, displaySize등의 메서드를 일반적인 특성으로서 Shape에 넣었기 때문에,   이런 메서드들은 호출할 수 있는 것이다.
    *   그렇지만 그 행동은 객체에 정의된대로 수행된다. 그러니까, 각각의 클래스에서 오버라이드 한 그 정의대로 행동을 취한다.
    *   그래서 똑같은 Shape타입에 똑같은 이름인 displaySize()로 메서드를 실행해도, 각각 다른 행동을 취하는 것이다.
    *   위 코드의 실행결과는 다음과 같다.  
        ![ProgramResult](https://user-images.githubusercontent.com/41663269/104594138-10bf3300-56b4-11eb-8169-4e0c63c27d34.png)