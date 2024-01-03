# 퍼사드 패턴

<img src="https://i.imgur.com/8J409mb.png" >

퍼사드 패턴은 라이브러리와 프레임워크, 다른 클래스들의 복잡한 집합에 대한 단순화된 인터페이스를 제공하는 구조적 디자인 패턴입니다.

## 퍼사드 패턴을 사용해야 하는 이유

집에 스마트홈을 둔다고 가정해봅니다. 기존의 우리는 집의 환경들을 설정할 때 특정한 상황들에 맞춰 설정합니다. 외출했을 경우, 귀가했을 경우, 영화를 볼 경우 등등 다양한 상황에 맞게 환경들을 직접 설정합니다. 가령 전등을 끄거나 에어컨을 키거나, 알림 시스템을 작동시키는 등의, 이미 정형화 되어 있는 상황들을 위해 같은 일들을 매번 일일히 반복해야 합니다. 하지만 스마트홈을 사용하면 버튼 한번 누르는 것만으로 이 문제를 해결할 수 있습니다. 퍼사드 패턴은 이런 상황에서 스마트홈과 같은 역할을 합니다.

정교한 라이브러리나 프레임워크에 속하는 광범위한 객체들의 집합으로 우리의 코드를 짜야한다고 상상해 봅니다. 일반적으로, 우리는 이러한 객체들을 모두 초기화하고, 종석성 관계들을 추적하고, 올바른 순서로 메서드들을 실행하는 등의 작업을 수행해야 합니다. 퍼사드는 이런 복잡한 하위 시스템에 대한 간단한 인터페이스를 제공하는 클래스입니다.

## 퍼사드 패턴의 구조

이 예시에서 퍼사드 패턴은 복잡한 비디오 변환 프레임워크와의 상호작용을 단순화합니다.

우리의 코드가 수십 개의 프레임워크 클래스들과 직접 작업하도록 하는 대신, 해당 기능들을 캡슐화하여 코드의 나머지 부분으로부터 숨기는 퍼사드 클래스를 만듭니다.

<img src="https://i.imgur.com/KsvObYp.png">

## 퍼사드 패턴의 장점

### 서브 시스템 보호
- 서브 시스템의 구성 요소를 직접 호출하지 않으므로 잘못된 사용을 방지합니다

### 높은 확장성
- 코드 변경 시 퍼사드를 사용하는 상위 시스템은 서브 시스템의 변경에 큰 영향을 받지 않습니다. 이는 확장성을 고려하면서 서브 시스템 기능을 유지할 수 있도록 완충하는 역할을 해줍니다.

### 높은 이식성
- 여러 작업을 하나의 묶음으로 처리하여 복잡한 클래스를 단순화해서 서브 시스템을 공통적으로 사용할 수 있도록 이식성을 향상시킵니다.

## 퍼사드 패턴의 단점

### 단일 책임 원칙(SRP)에 위배 될 수 있습니다
- 퍼사드가 너무 많은 책임을 가질 경우, 해당 퍼사드는 신 객체(God Object)가 될 수 있고 오히려 퍼사드 자체가 복잡해지는 문제가 발생할 수 있습니다.

## 활용 예시

이 예시에서 퍼사드 패턴은 복잡한 비디오 변환 프레임워크와의 통신을 단순화합니다.

퍼사드는 하나의 메서드를 가진 단일 메서드를 제공하고 이 메서드는 프레임워크의 올바른 클래스들의 설정 그리고 결과를 가져오는 작업에 대한 모든 복잡성을 처리해줍니다.

```java
public class VideoConversionFacade {
    public File convertVideo(String fileName, String format) {
        System.out.println("VideoConversionFacade: conversion started.");
        VideoFile file = new VideoFile(fileName);
        Codec sourceCodec = CodecFactory.extract(file);
        Codec destinationCodec;
        if (format.equals("mp4")) {
            destinationCodec = new MPEG4CompressionCodec();
        } else {
            destinationCodec = new OggCompressionCodec();
        }
        VideoFile buffer = BitrateReader.read(file, sourceCodec);
        VideoFile intermediateResult = BitrateReader.convert(buffer, destinationCodec);
        File result = (new AudioMixer()).fix(intermediateResult);
        System.out.println("VideoConversionFacade: conversion completed.");
        return result;
    }
}
```

<sub>참고 문헌
- https://refactoring.guru/ko/design-patterns/facade
- https://hirlawldo.tistory.com/172
- https://gsbang.tistory.com/entry/Design-Pattern-Facade-Pattern%ED%8D%BC%EC%82%AC%EB%93%9C-%ED%8C%A8%ED%84%B4</sub>