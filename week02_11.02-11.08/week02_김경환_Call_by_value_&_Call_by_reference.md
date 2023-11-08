## Call by value와 Call by reference

이 두 단어는 파라미터 내 변수의 값(value)을 복사하는 방식으로 호출하는가, 주소값(reference)을 복사하는 방식으로 호출하는가를 애기한다.

파라미터를 사용해 함수를 호출할 경우 함수에선 새로운 변수를 생성한다. 이때 이 변수에 어떤 값이 들어오느냐에 따라서 작동이 달라진다.

스택에는 변수값 혹은 객체의 주소값이 들어가고

힙의 경우에는 객체가 저장된다.

call by reference의 경우

변수 안에 '리모콘' 즉 주소값이 복사된다.

그리고 call by value의 경우에는

값 그 자체를 복사한다.

원시 변수에서는 변수값을, 참조형 변수의 경우에는 참조형 변수값을 복사해서 가져온다.

자바의 경우에는 call by value 방식을 사용한다.

## Call by value의 예시

```java
public class _01_onlyForPractice {
    public static void main(String[] args) {
        int x = 10;
        int[] y = {20};
        Potato potato1 = new Potato("큰강아지");
        Potato potato2 = new Potato("작은강아지");

        hello(x, y, potato1, potato2);

        System.out.println("x = " + x);
        System.out.println("y = " + y[0]);
        System.out.println("potato1 = " + potato1.name);
        System.out.println("potato2 = " + potato2.name);
    }
    public static void hello(int x, int[] y, Potato potato1, Potato potato2) {
        x++;
        y[0]++;
        potato1 = new Potato("큰고양이");
        potato2.setPotato("작은고양이");
    }
}
class Potato {
    String name;
    public Potato(String name) {
        this.name = name;
    }
    public void setPotato(String name) {
        this.name = name;
    }
}
```

다음과 같은 코드가 있을 경우

터미널에 호출되는 x와, y, 감자1, 감자2의 값은 얼마일까?

x는 10

y는 21

감자1은 큰강아지,

감자2는 작은고양이이다.

---

call by value는 새로운 값을 새로운 변수에 넣었기 때문에 기존 변수들의 값은 달라진게 없어야할텐데 변화가 있다.

그 이유는 변수가 가지는, 우리가 함수를 호출할 때 복사한 값이 가지는 특성 때문이다.

x의 경우 변수값 그 자체를 복사하여

새로운 변수 x에 넣었기 때문에

실질적으로 변화한 것은 새로운 변수 x에 들어있는 값이다.

그렇기 때문에 기존의 변수 x에는 변화가 없다.

y의 경우 복사한 것은 배열이기에 새로운 배열이 생성된다.

하지만 이 경우 배열을 새롭게 복사했지만 배열 내의 주소값, 즉 리모콘들은 그대로 가져오게 된다.

힙에 저장되있는 값들에 직접 접근할 수 있는 리모콘들을 가지기 때문에 배열 내의 값을 수정할 경우 기존 배열 내의 값에도 적용된다.

감자1의 경우는 x와 거의 동일한 이유에서 변화가 없다.

별개의 새로운 변수가 사용되고 새로운 변수를 만드는 것이기 때문에 기존의 변수에는 영향을 주지 않는다.

감자2의 경우는 작은고양이가 된다. y의 경우와 비슷한 방식이 사용됩니다.

y의 경우에서 복사해온 변수 자체는 새로운 것이지만 그 안에 들어있던 주소값들은 그대로였던 것 처럼

감자2의 경우에도 객체 자체는 새 것이지만 객체 내의 주소값들은 그대로이기 때문에

객체 내의 함수나 변수들을 변경할 경우 힙에 들어있는 객체에 직접 접근할 수 있다.

그래서 감자2의 경우 작은고양이가 출력된다.

