# 캐스팅(Casting)

**하나의 데이터 타입을 다른 타입으로 바꾸는 것**을 **형변환**(캐스팅)이라고 한다.

좌변의 자료형에 맞게 우변의 형을 변형하는 것이다.

`int num = 1;`</br>
int형에 해당하는 변수 num을 만들기 위해 우변에 충분한 정보(1)가 있다.

`int num1 = 2.0;` → Error</br>
이 경우에는 컴파일 에러가 발생하는데, 우변의 데이터가 손실되는 것을 막기 위해 에러를 표시한다.

다음과 같이 변환하고자 하는 자료형을 명시해주면 에러가 나지 않는다.</br>
`int num2 = (int) 2.0;`

다음과 같은 경우에는 에러가 발생하지 않는다.</br>
`double num3 = 1;`</br>
여기서는 우변에서 손실되는 데이터가 없기 때문이다.

따라서, 형변환을 할 때는 **좌변에 필요한 정보가 우변에 충분히 있어야 한다.**

# 업캐스팅(UpCasting)

**자식 클래스의 객체가 부모 클래스 타입으로 형변환**되는 것이다.

- 업캐스팅에서는 캐스팅 연산자 괄호를 생략할 수 있다.
- 자식 클래스에만 있는 속성과 메소드를 호출할 수는 없다.
- 자식 클래스에 오버라이딩을 한 메소드가 있을 경우, 부모 클래스의 메소드가 아닌 오버라이딩 메소드가 실행된다.

```java
class Person {
    public String name;

    public Person(String name) {
        this.name = name;
    }
}
class Student extends Person{
    public int id;

    public Student(String name) {
        super(name);
    }
}

public static void main(String[] args) {
      Student student = new Student("홍길동");
      Person person = student;    // 업캐스팅
      person.name = "부모 이름";
      person.id    // 컴파일 오류
  }
```

## 사용 이유 - 다형성(Polymorphism)

**하나의 객체가 여러 자료형 타입을 가질 수 있는 것**을 다형성이라고 한다.

부모 클래스의 참조변수로 자식 클래스 타입의 인스턴스를 참조할 수 있다.

오버라이딩은 상속을 통해 ‘같은 이름의 메소드를 서로 다른 내용으로 구현’한다는 점에서 객체지향의 다형성을 실현한다고 볼 수 있다.

```java
class Developer{
    public String name;
    public void developApp(){
        // 서비스 개발
    }
}

class IosDeveloper extends Developer{
    @Override
    public void developApp(){
        // IOS 개발
    }

}

class AndroidDeveloper extends Developer{
    @Override
    public void developApp(){
        // Android 개발
    }
}

public class Company {
    public void developService(Developer developer){
        developer.developApp();
    }
}

public class UpCasting {
    public static void main(String[] args) {
        Company company = new Company();
				Developer developer = new AndroidDeveloper();

        company.developService(developer);
    }
}
```

업캐스팅을 사용하지 않는다면 Company 클래스에서 인자로 Developer, IosDeveloper, AndroidDeveloper를 받는 developService를 각각 따로 작성해야 한다.

# 다운캐스팅(DownCasting)

**업캐스팅된 객체를 다시 되돌리는 것**을 의미한다.

업캐스팅 되었던 객체의 자료형을 다시 자식 클래스의 정보를 담을 수 있도록 자식 클래스의 자료형으로 되돌려 놓는 것이다.

- 자식 클래스로 다운캐스팅을 할 때는 타입을 꼭 명시해줘야 한다.
- 다운캐스팅만 쓰면 우변이 좌변에서 필요한 정보를 모두 채워주지 못하므로 성립이 불가능하다.
- 업캐스팅이 되지 않았던 부모 클래스 타입의 객체를 다운캐스팅 하는 것은 런타임 에러를 발생시킨다.

```java
class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }
}

class Student extends Person{
    int id;
    
    public Student(String name) {
        super(name);
    }
}

public class Downcasting {
    public static void main(String[] args) {
        Person person = new Student("홍길동");
        Student student = (Student) person;
        student.id = 1;
        student.name = "학생";

				Person person2 = new Person();
				Student student2 = (Student) person2;    // 런타임 에러
    }
}
```

</br>

> 참고 자료</br>
[Velog | smallcherry.log - [Java] 업캐스팅과 다운캐스팅](https://velog.io/@smallcherry/Java-UpCastingAndDownCasting)</br>
[Velog | Gyul.log - 업캐스팅(Upcasting)과 다운캐스팅(Downcasting)](https://velog.io/@thd0427/업캐스팅Upcasting과-다운캐스팅Downcasting)
>
