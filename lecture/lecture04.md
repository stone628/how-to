# 스위치에서 CPU까지 [[목차](index.md)]

## MOSFET을 이용한 디지털 스위치

### 목표
- MOSFET의 사용 방법을 알아보자
- MOSFET의 반도체 특성을 알아보자
- MOSFET 스위치와 BJT 스위치의 차이점을 이해하자

### 실습
1. 지난 실습 시간에 만들었던 전지 + 전선 + 스위치 + 전류 제한 저항 + LED의 회로를 만들어서 동작을 확인한다

1. N-channel MOSFET(예: 2N7000)으로 스위치를 만들어 동작을 확인한다
	- 게이트(Gate)에 전압을 걸지 않으면 LED가 꺼져 있는다
	- 게이트에 3~5V를 걸면 LED가 켜진다
	- 게이트에 연결한 선을 손으로 만져도 LED 상태가 유지된다
		- 게이트가 절연되어 있어 전류가 흐르지 않기 때문이다
		- BJT와 달리 게이트에 거의 전류가 흐르지 않는다

1. P-channel MOSFET(예: IRF9620)으로 스위치를 만들어 동작을 확인한다
	- 게이트에 전압을 걸지 않으면 LED가 꺼져 있는다
	- 게이트를 0V(GND)에 연결하면 LED가 켜진다
	- P-channel은 게이트에 0V를 걸어야 켜지므로 N-channel과 반대다

1. 멀티미터로 MOSFET 게이트에 흐르는 전류를 측정한다
	- 게이트 전류가 거의 0에 가까움을 확인한다
	- BJT 스위치의 베이스 전류와 비교한다
		- BJT는 베이스 전류가 필요하지만 MOSFET은 거의 필요하지 않다

1. N-channel과 P-channel MOSFET 스위치를 비교한다
	- 회로 구성의 차이
		- N-channel은 부하(LOAD)가 드레인(Drain) 쪽에 위치한다
		- P-channel은 부하(LOAD)가 소스(Source) 쪽에 위치한다
	- ON/OFF 신호의 방향이 반대다
		- N-channel: 게이트에 HIGH(1)를 주면 ON
		- P-channel: 게이트에 LOW(0)를 주면 ON

### 결론
1. MOSFET은 게이트 전압으로 ON/OFF를 제어하는 전압 제어 소자다
1. MOSFET의 게이트는 산화막으로 절연되어 있어 전류가 거의 흐르지 않는다 -> 대기 전력이 매우 작다
1. MOSFET은 N-channel과 P-channel 두 종류가 있다
1. MOSFET과 BJT의 가장 큰 차이:
	- BJT: 전류로 제어 (베이스 전류 필요)
	- MOSFET: 전압으로 제어 (게이트 전류 불필요)
1. MOSFET은 현대 CPU, 스마트폰 등 대부분의 디지털 회로에 사용된다

### 심화 주제
1. BJT와 MOSFET의 장단점 비교
	- BJT: 전류 구동 능력이 좋고, 정특성이 안정적이다
	- MOSFET: 입력 저항이 매우 높아 전력 소모가 적고, 집적 회로에 유리하다
1. CMOS(Complementary MOS)란?
	- N-channel과 P-channel MOSFET을 쌍으로 사용하는 회로 방식
	- 두 MOSFET이 번갈아 켜지고 꺼져서 전력 소모가 극히 적다
	- 현대 CPU와 메모리의 기본 구성 요소다

