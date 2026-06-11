# 스위치에서 CPU까지 [[목차](index.md)]

## 왜 NAND 인가? - NAND로 모든 논리 게이트 구현하기

### 목표
- NAND 게이트 하나로 NOT, AND, OR, XOR을 만들 수 있음을 이해하자
- NAND 게이트가 디지털 회로에서 특별한 위치를 차지하는 이유를 알아보자

### 실습
1. NAND 게이트 1개로 NOT 게이트를 만들어 동작을 확인한다
	- NAND의 두 입력을 같은 신호에 연결한다
	- 출력이 입력의 반대가 되는지 확인한다

1. NAND 게이트 2개로 AND 게이트를 만들어 동작을 확인한다
	- 첫 번째 NAND: 두 입력 A, B → NAND 출력
	- 두 번째 NAND: NAND 출력을 NOT으로 반전 (두 입력을 묶음) → AND 출력

1. NAND 게이트 3개로 OR 게이트를 만들어 동작을 확인한다
	- 첫 번째 NAND: A 입력을 NOT으로 반전
	- 두 번째 NAND: B 입력을 NOT으로 반전
	- 세 번째 NAND: 두 반전된 신호를 NAND → OR 출력

1. NAND 게이트 4개로 XOR 게이트를 만들어 동작을 확인한다
	- 여러 개의 NAND를 조합하여 XOR을 구성해 본다

### NAND만으로 NOT 만들기

NAND의 두 입력을 묶으면 NOT 게이트가 된다.

```
A ──┬──┐
    │N │─── NOT A
A ──┴──┘
```

**진리표**:

| A | NOT A |
|---|-------|
| 0 | 1     |
| 1 | 0     |

### NAND만으로 AND 만들기

NAND + NOT = AND. NOT도 NAND로 만들었으므로, AND는 NAND 2개로 완성된다.

```
A ──┬──┐
    │N1│──┬──┐
B ──┴──┘  │N2│─── A AND B
       A ──┴──┘
```

### NAND만으로 OR 만들기

두 입력을 각각 NOT으로 반전시킨 후 NAND하면 OR가 된다. NAND 3개로 완성된다.

```
    ┌──┐
A ──│N1│──┬──┐
    └──┘  │N3│─── A OR B
    ┌──┐  └──┘
B ──│N2│──┘
    └──┘
```

### NAND만으로 XOR 만들기

XOR은 NAND 4개로 구현할 수 있다.

**회로 구성**:
- N1: A NAND B
- N2: A NAND N1의 출력
- N3: B NAND N1의 출력
- N4: N2의 출력 NAND N3의 출력 → XOR

**진리표 확인**: 4가지 입력 조합을 따라가며 최종 출력이 XOR과 같음을 확인해 보자.

### 왜 NAND를 선택하는가?

NAND만으로 모든 게이트를 만들 수 있다면 AND, OR을 직접 사용하면 되지, 왜 굳이 더 많은 NAND를 써서 만드는 것일까?

이유는 **CMOS 회로의 물리적 특성** 때문이다.

1. **NAND가 NOR보다 빠르다**
	- NAND: NMOS 2개를 직렬로 연결 (GND 쪽)
	- NOR: PMOS 2개를 직렬로 연결 (Vdd 쪽)
	- PMOS는 NMOS보다 ON 저항이 크기 때문에 직렬로 연결하면 속도가 더 느려진다
	- 따라서 같은 조건에서 NAND가 NOR보다 더 빠르게 동작한다

1. **하나의 게이트로 통일하면 설계와 제조가 단순해진다**
	- 수십억 개의 트랜지스터가 들어가는 CPU에서 여러 종류의 게이트를 각각 설계하는 것보다
	- NAND 하나만 최적화하여 반복 배치하는 것이 훨씬 효율적이다

1. **NAND는 완전한 논리 집합(universal gate)이다**
	- NAND만 있으면 NOT, AND, OR, XOR, 어떤 논리 회로든 만들 수 있다
	- 이론적으로 NAND만으로 CPU 전체를 구현할 수 있다

### 결론
1. NAND 게이트 하나로 NOT, AND, OR, XOR 등 모든 논리 게이트를 만들 수 있다
1. NAND는 CMOS 회로에서 가장 빠르고 효율적인 게이트다
1. 실제 CPU는 대부분 NAND 게이트와 인버터(NOT)로 구성되어 있다
1. "NAND만 있으면 무엇이든 만들 수 있다"는 것이 디지털 회로 설계의 핵심 원리다

### 심화 주제
1. 다른 게이트도 universal gate가 될 수 있을까?
	- NOR 게이트도 NAND와 마찬가지로 universal gate다
	- NOR만으로 NOT, AND, OR, XOR을 만드는 방법을 생각해 보자
1. 역사적으로 NAND가 선택된 배경
	- 1960~70년대 TTL(Transistor-Transistor Logic) 시대에도 NAND가 가장 널리 사용되었다
	- CMOS 시대가 된 지금도 NAND는 가장 기본적인 게이트로 남아 있다
1. 실제 CPU의 게이트 구성
	- 현대 CPU의 대부분 면적은 NAND와 인버터가 차지한다
	- AND, OR 게이트는 설계 자동화 도구가 자동으로 NAND로 변환하여 합성한다
