# 고정 소수점과 부동 소수점
## 실수의 메모리 표현
컴퓨터의 메모리는 2진수 체계를 기반으로 데이터를 저장합니다. 실수도 2진수 체계를 기반으로 데이터를 저장하게 됩니다.

## 실수의 2진수 표현
실수란 정수와 소수로 이루어진 수를 의미합니다. 정수와 소수는 표기상으론 별다를 바 없어보이는 숫자들의 나열 같지만 이진수 변환에 있어 차이를 가집니다.

### 정수의 이진수 표현
10진수의 정수를 2진수의 정수로 변환하는 것은 어렵지 않습니다. 아래 그림과 같은 간단한 법칙을 통해 변환이 가능합니다.

아래와 같이 바꾸고 싶은 정수를 1이 될때까지 2로 나눈 후 발생한 나머지들을 역순으로 둔 후 가장 앞자리에 1을 추가해주면 됩니다.

![정수 이진수 변환](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnrujE%2FbtrbAAYB26O%2F2agaEiFGFuCIV33eihv9Yk%2Fimg.png)

### 소수의 이진수 표현
소수의 경우 소수점의 이하가 0이 될 때까지 2로 계속 곱해주면서, 정수 부분에 1이 발생한다면 1, 아닐 경우 0을 적어가며 소수가 없어질 때까지 반복하시면 됩니다.

![소수 이진수 변환](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbjXXhE%2FbtrbABwAtn9%2FvniK6fAyznRI3YesopKi3k%2Fimg.png)

공식을 따라하는 것만으로 어렵지 않게 소수를 정수로 변환할 수 있습니다. 하지만 소수에 2로 나눠지지 않는 수나 1이 들어올 경우 상황이 달라집니다.

![소수 이진수 변환2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmyTEk%2FbtrbKGXGUss%2FcYZoNnkmQ0F1eOK3cMIAnk%2Fimg.png)

아무리 2를 곱해보아도 소수 부분이 없어지지 않아 무한히 0011이 반복됩니다. 이를 **무한 소수**라고 합니다.

## 고정 소수점과 부동 소수점
특정 진수를 타 진수로 변환할 경우 필연적으로 위와 같이 무한 소수가 발생할 수 있습니다. 한정된 메모리를 가지는 컴퓨터의 입장에서 무한 소수를 저장한다는 것은 불가능합니다.

이런 경우를 위해 실수형을 표현하기 위한 방법이 고정 소수점과 부동 소수점입니다.

## 고정 소수점

고정 소수점 방식은 메모리를 **정수부**와 **소수부**로 고정해서 나누고 지정하여 처리하는 방식입니다.

>1. 처음 1비트는 부호를 나타냅니다. 양수는 0, 음수는 1입니다.
>
>2. 다음 15비트는 정수부를 나타냅니다.
>
>3. 다음 16비트는 소수부를 나타냅니다.
>
>4. 정수부와 소수부의 경계를 소수점의 위치로 두고 2진수로 변환된 수를 넣으면 됩니다.
>
>5. 남는 자리가 있을 경우 모두 0으로 채웁니다.

<br>

![고정 소수점](https://gguguk.github.io/assets/img/post_img/fixed_point.png)

<br>

가령 10진수 7.625를 32비트 고정 소수점으로 표현해본다면

<br>

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mtable displaystyle="true" columnalign="right left" columnspacing="0em" rowspacing="1.3em 0.3em">
    <mtr>
      <mtd>
        <msub>
          <mn>7.625</mn>
          <mrow data-mjx-texclass="ORD">
            <mo stretchy="false">(</mo>
            <mn>10</mn>
            <mo stretchy="false">)</mo>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <mi></mi>
        <mo>=</mo>
        <msup>
          <mn>2</mn>
          <mn>2</mn>
        </msup>
        <mo>&#x22C5;</mo>
        <mn>1</mn>
        <mo>+</mo>
        <msup>
          <mn>2</mn>
          <mn>1</mn>
        </msup>
        <mo>&#x22C5;</mo>
        <mn>1</mn>
        <mo>+</mo>
        <msup>
          <mn>2</mn>
          <mn>0</mn>
        </msup>
        <mo>&#x22C5;</mo>
        <mn>1</mn>
        <mo>+</mo>
        <msup>
          <mn>2</mn>
          <mrow data-mjx-texclass="ORD">
            <mo>&#x2212;</mo>
            <mn>1</mn>
          </mrow>
        </msup>
        <mo>&#x22C5;</mo>
        <mn>1</mn>
        <mo>+</mo>
        <msup>
          <mn>2</mn>
          <mrow data-mjx-texclass="ORD">
            <mo>&#x2212;</mo>
            <mn>2</mn>
          </mrow>
        </msup>
        <mo>&#x22C5;</mo>
        <mn>0</mn>
        <mo>+</mo>
        <msup>
          <mn>2</mn>
          <mrow data-mjx-texclass="ORD">
            <mo>&#x2212;</mo>
            <mn>3</mn>
          </mrow>
        </msup>
        <mo>&#x22C5;</mo>
        <mn>1</mn>
      </mtd>
    </mtr>
    <mtr>
      <mtd></mtd>
      <mtd>
        <mi></mi>
        <mo>=</mo>
        <msub>
          <mn>111.101</mn>
          <mrow data-mjx-texclass="ORD">
            <mo stretchy="false">(</mo>
            <mn>2</mn>
            <mo stretchy="false">)</mo>
          </mrow>
        </msub>
      </mtd>
    </mtr>
  </mtable>
</math>

먼저 십진수를 이진수로 전환해줍니다.

<br>

![고정 소수점2](https://gguguk.github.io/assets/img/post_img/fixed_point_example.png)

전환한 이진수를 그대로 기입해주면 됩니다.

### 고정 소수점의 장점

- 실수를 정수부와 소수부로 표현하여 직관적입니다.
- 속도가 빠릅니다.

### 고정 소수점의 단점

- 큰 실수를 표현하기 어렵습니다.
- 정수부가 길고 소수부가 짧거나 그 반대의 경우를 표현할 수 없습니다.

## 부동 소수점

부동 소수점에서 부동(float)은 소수점이 둥둥 떠다닌다는 의미입니다. 정규화를 통해 소수점이 옮겨다니는 방식의 실수 표현법이라고 볼 수 있습니다.

부동 소수점은 고정 소수점 방식과는 달리 메모리를 **가수부**와 **지수부**로 나눕니다.

- 가수 : 실수의 실제값을 표현합니다.

- 지수 : 실수의 크기를 표현합니다.

![부동 소수점](https://gguguk.github.io/assets/img/post_img/floating_point.png)

부동 소수점을 표현하는 체계는 다양합니다. 일반적으로 가장 널리 쓰이는 표준은 IEEE 754라고 합니다

IEEE 754에 따른 부동 소수점은 아래와 같은 순서를 따릅니다.

1. 먼저 2진수를 정규화합니다

2. 처음 1비트는 부호를 나타냅니다. 0은 양수이고 1은 음수입니다.

3. 다음 8비트는 지수부를 나타냅니다. 정규화 과정에서 얻어낸 지수에 바이아스 값을 더해서 이진수 변환한 후에 넣어줍니다.

4. 나머지 23비트는 가수부를 나타냅니다. 정규화를 통해 얻은 값의 소수 부분으로 채웁니다.

<br>

가령 7.625를 부동 소수점으로 표현해본다면 아래와 같습니다.

1. 2진수 변환 : 111.101

2. 정규화 : <math xmlns="http://www.w3.org/1998/Math/MathML">
  <msub>
    <mn>1.11101</mn>
    <mrow data-mjx-texclass="ORD">
    </mrow>
  </msub>
  <mo>&#xD7;</mo>
  <msup>
    <mn>2</mn>
    <mn>2</mn>
  </msup>
</math>

3. 지수부 : 2 + 127(바이아스 값) = 129 = 10000001

4. 가수부 : 11101

![부동 소수점2](https://gguguk.github.io/assets/img/post_img/floating_point_example.png)

### 부동 소수점의 장점

- 표현할 수 있는 수의 범위가 넓어집니다.

### 부동 소수점의 단점

- 오차가 발생할 수 있습니다.

<sub>참고 문헌 : https://gguguk.github.io/posts/fixed_point_and_floating_point/, https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%8B%A4%EC%88%98-%ED%91%9C%ED%98%84%EB%B6%80%EB%8F%99-%EC%86%8C%EC%88%98%EC%A0%90-%EC%9B%90%EB%A6%AC-%ED%95%9C%EB%88%88%EC%97%90-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0#%EC%8B%A4%EC%88%98%EC%9D%98_%EB%A9%94%EB%AA%A8%EB%A6%AC_%ED%91%9C%ED%98%84, https://blog.hexabrain.net/357