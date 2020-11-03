# HW5

**전자회로설계(2020년 1학기) 개인별 설계과제 #5**

**제출일자 : 2020년 5월 23일(토) 17:00까지**

**1. 아래 주어진 설계사양에 부합되는 capacitor coupled inverting type audio amplifier를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.**

**(설계사양): 사용할 op amp: *u*A741,** **Double Supply : ± 15 V**

**Bandwidth: 100 Hz ~ 15 KHz, 부하저항 : 2 kohm**

**전압이득 : 20 dB of 15 mV input signal amplitude**

**2. 문제 1과 같은 설계사양에 부합되는 capacitor coupled non-inverting type audio amp.를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.**

**3. 문제 1 과 문제 2의 설계된 증폭기 회로를 single supply 형태로 전환하고, PSpice를 사용하여 동작상태(AC & Transient responses)를 검증하시오.**

**4. 주어진 입출력 관계식에 해당되는 회로를 *u*A741 op amp.(double supply) 1개를 사용하여 direct coupled 구조로 설계하고, PSpice를 이용하여 검증 하시오.**

***Vout= 2Vin1 - 3Vin2 - Vin3 + 5Vin4***

HW5 : 개인별 설계과제 #5

Pspice Version : OrCad 17.4

2017117876

김승현

1. 아래 주어진 설계사양에 부합되는 capacitor coupled inverting type audio amplifier를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.

(설계사양): 사용할 op amp: uA741, Double Supply : ± 15 V

Bandwidth: 100 Hz ~ 15 KHz, 부하저항 : 2 kohm

전압이득 : 20 dB of 15 mV input signal amplitude

Inverting Amplifier를 설계하기 위해서는 입력전압과 전압이득에 맞는 적절한 저항을 선택하는 것이 필요하다.

20dB 의 전압이득은 10배를 나타낸다.

일반적으로 Inverting Amplifier 는 다음과 같이 설계가 가능하다.

![HW5%200a4f56389ee746d09aea97c086865030/image130.bmp](HW5%200a4f56389ee746d09aea97c086865030/image130.bmp)

![HW5%200a4f56389ee746d09aea97c086865030/image131.bmp](HW5%200a4f56389ee746d09aea97c086865030/image131.bmp)

설계 조건에 따라 $R_{1} = \frac{V_{i}}{100I_{\text{bias}(\max)}}$ 이므로 *Vi* = 15mV , *I*bias(max ) = 500uA 를 대입하여 *R*1 을 구한다.

*R*1 = 300*Ω* 을 구할 수 있고, 전압이득은 10배 이므로 *R*2 = 3*KΩ* 이 된다.

Output offset voltage를 최소화 하기 위해 $R_{3} = \frac{R_{1}R_{2}}{R_{1} + R_{2}} = \frac{300*3000}{300 + 3000} = 272.72\Omega$ 을 positve input 에 달아줘야 한다.

다음으로 주파수 영역을 설정해야 한다.

설계조건에서 100Hz ~ 15KHz 의 Bandwidth를 가지므로 Lower 3dB, Upper 3dB 에 극점을 둘 필요가 있다.

![HW5%200a4f56389ee746d09aea97c086865030/image132.bmp](HW5%200a4f56389ee746d09aea97c086865030/image132.bmp)

negative input, op-amp output 에 들어가는 커패시터와 저항은 Lower 3dB를 담당하고

feedback 에 들어가는 커패시터와 저항은 Upper 3dB를 담당한다.

종전에 *R*1 = 300*Ω*, *R*2 = 3*KΩ*, *R*3 = 272.72*Ω* 를 구하였다.

설계조건에서 *RL* = 2*KΩ* 이므로 이에 맞게 커패시터를 설정해주면 된다.

$100\text{Hz} = \frac{1}{2\pi R_{1}C_{1}} = \frac{1}{2\pi*300*C_{1}}$ 을 만족하는 *C*1 은 5.305uF 이다.

$100\text{Hz} = \frac{1}{2\pi R_{L}C_{L}} = \frac{1}{2\pi*2K*C_{L}}$을 만족하는 *CL* 은 0.795uF 이며, $15\text{KHz} = \frac{1}{2\pi R_{2}C_{2}} = \frac{1}{2\pi*3K*C_{2}}$ 를 만족하는 *C*2 = 3.536nF 이다.

**그림1-1) 최초 조건에 맞는 Inverting Amplifier 이론적 설계**

![HW5%200a4f56389ee746d09aea97c086865030/image133.bmp](HW5%200a4f56389ee746d09aea97c086865030/image133.bmp)

따라서 조건에 맞게 설계한 스케메틱은 위의 그림과 같다.

실제로 AC Sweep을 해본결과 전압이득은 20dB 로 잘 나오는 것을 확인할 수 있었으나 Lower 3dB 가 153.05Hz

Upper 3dB 가 13.227KHz 가 나왔다.

따라서 Lower 3dB를 100Hz 까지 넓히기 위하여 *C*1, *CL* 는 키울 필요성이 있었고

Upper 3dB를 15KHz 까지 넓히기 위하여 *C*2 는 줄일 필요성이 있었다.

기존 *C*1 = 5.305uF 에서 1.5 배를 곱한 *C*1 = 7.9575uF 로 수정하였다.

*CL* = 0.795uF 에서 1.58 배를 곱한 *CL* = 1.25uF 를 사용하였다.

*C*2 = 3.536nF 에서 0.85 배를 곱한 *C*2 = 3.02nF 를 사용하였다.

**그림1-2) 올바른 Bandwidth를 위해 커패시터를 수정한 Inverting Amplifier**

![HW5%200a4f56389ee746d09aea97c086865030/image134.bmp](HW5%200a4f56389ee746d09aea97c086865030/image134.bmp)

**그림1-3) Inverting Amplifier AC Sweep**

![HW5%200a4f56389ee746d09aea97c086865030/image135.bmp](HW5%200a4f56389ee746d09aea97c086865030/image135.bmp)

**그림1-4) Inverting Amplifier AC Sweep Frequency**

![HW5%200a4f56389ee746d09aea97c086865030/image136.bmp](HW5%200a4f56389ee746d09aea97c086865030/image136.bmp)

Bandwidth 확인을 위해 3dB 주파수를 확인해 본 결과 100Hz, 15KHz 로 설계 조건에 맞음을 확인할 수 있다.

Transient Analysis를 위해 20dB 의 전압이득을 가지는 VSIN 1KHz, 15mV를 인가하였다.

한 주기에 1ms 가 걸리므로 5 주기가 나오도록 Run to time 은 5ms 로 설정했다.

**그림1-5) Inverting Amplifier Transient Analysis**

![HW5%200a4f56389ee746d09aea97c086865030/image137.bmp](HW5%200a4f56389ee746d09aea97c086865030/image137.bmp)

**그림1-6) Inverting Amplifier Transient Analysis Peak Voltage**

![HW5%200a4f56389ee746d09aea97c086865030/image138.bmp](HW5%200a4f56389ee746d09aea97c086865030/image138.bmp)

실제로 전압을 측정해본 결과, 14.972mV 가 151.908mV 로 약 10배 증가함을 확인하였다.

2. 문제 1과 같은 설계사양에 부합되는 capacitor coupled non-inverting type audio amp.를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.

![HW5%200a4f56389ee746d09aea97c086865030/image139.bmp](HW5%200a4f56389ee746d09aea97c086865030/image139.bmp)

![HW5%200a4f56389ee746d09aea97c086865030/image140.bmp](HW5%200a4f56389ee746d09aea97c086865030/image140.bmp)

일반적으로 Non-inverting Amplifier 는 위와 같이 설계가 가능하다.

설계 조건에 따라 $R_{1} = \frac{V_{i}}{100I_{\text{bias}(\max)}}$ 이므로 Inverting Amplfier에서 구한 *R*1 = 300*Ω* 을 그대로 사용할 수 있다.

Non-inverting Amplifier에서 전압이득 $A_{v} = 1 + \frac{R_{2}}{R_{1}}$ 이므로 *R*2 는 *R*1 의 9배가 된다. 즉 *R*2 = 2.7*KΩ* 이다

Output offset voltage를 최소화 하기 위해 $R_{3} = \frac{R_{1}R_{2}}{R_{1} + R_{2}} = \frac{300*2700}{300 + 2700} = 270\Omega$ 을 positve input 에 달아줘야 한다.

다음으로 주파수 영역을 설정해야 한다.

설계조건에서 100Hz ~ 15KHz 의 Bandwidth를 가지므로 Lower 3dB, Upper 3dB 에 극점을 둘 필요가 있다.

![HW5%200a4f56389ee746d09aea97c086865030/image141.bmp](HW5%200a4f56389ee746d09aea97c086865030/image141.bmp)

positive input, op-amp output 에 들어가는 커패시터와 저항은 Lower 3dB를 담당한다.

feedback 에 들어가는 커패시터와 저항은 Upper 3dB를 담당한다.

종전에 *R*1 = 300*Ω*, *R*2 = 2.7*KΩ*, *R*3 = 270*Ω* 를 구하였다.

설계조건에서 *RL* = 2*KΩ* 이므로 이에 맞게 커패시터를 설정해주면 된다.

$100\text{Hz} = \frac{1}{2\pi R_{3}C_{3}} = \frac{1}{2\pi*270*C_{3}}$ 을 만족하는 *C*3 은 2.947uF 이다.

$100\text{Hz} = \frac{1}{2\pi R_{L}C_{L}} = \frac{1}{2\pi*2K*C_{L}}$을 만족하는 *CL* 은 0.795uF 이며, $15\text{KHz} = \frac{1}{2\pi R_{2}C_{2}} = \frac{1}{2\pi*2.7K*C_{2}}$ 를 만족하는 *C*2 = 3.929nF 이다.

**그림2-1) 최초 조건에 맞는 Non-Inverting Amplifier 이론적 설계**

![HW5%200a4f56389ee746d09aea97c086865030/image142.bmp](HW5%200a4f56389ee746d09aea97c086865030/image142.bmp)

따라서 조건에 맞게 설계한 스케메틱은 위의 그림과 같다.

실제로 AC Sweep을 해본결과 전압이득은 20dB 로 잘 나오는 것을 확인할 수 있었으나 Lower 3dB 가 233.14Hz

Upper 3dB 가 13.679KHz 가 나왔다.

따라서 Lower 3dB를 100Hz 까지 넓히기 위하여 *C*3, *CL* 는 키울 필요성이 있었고

Upper 3dB를 15KHz 까지 넓히기 위하여 *C*2 는 줄일 필요성이 있었다.

기존 *C*3 = 2.947uF 에서 2.36 배를 곱한 *C*3 = 6.7781uF 로 수정하였다.

*CL* = 0.795uF 에서 2.5 배를 곱한 *CL* = 1.9875uF 를 사용하였다.

**그림2-2) 올바른 Bandwidth를 위해 커패시터를 수정한 Non-Inverting Amplifier**

![HW5%200a4f56389ee746d09aea97c086865030/image143.bmp](HW5%200a4f56389ee746d09aea97c086865030/image143.bmp)

*C*

2

= 3.929nF 에서 0.88 배를 곱한

*C*

2

= 3.457nF 를 사용하였다.

**그림2-3) Non-Inverting Amplifier AC Sweep**

![HW5%200a4f56389ee746d09aea97c086865030/image144.bmp](HW5%200a4f56389ee746d09aea97c086865030/image144.bmp)

**그림2-4) Non-Inverting Amplifier AC Sweep Frequency**

![HW5%200a4f56389ee746d09aea97c086865030/image145.bmp](HW5%200a4f56389ee746d09aea97c086865030/image145.bmp)

Bandwidth 확인을 위해 3dB 주파수를 확인해 본 결과 100Hz, 15KHz 로 설계 조건에 맞음을 확인할 수 있다.

**그림2-5) Non-Inverting Amplifier Transient Analysis**

![HW5%200a4f56389ee746d09aea97c086865030/image146.bmp](HW5%200a4f56389ee746d09aea97c086865030/image146.bmp)

**그림2-6) Non-Inverting Amplifier Transient Analysis Peak Voltage**

![HW5%200a4f56389ee746d09aea97c086865030/image147.bmp](HW5%200a4f56389ee746d09aea97c086865030/image147.bmp)

실제로 전압을 측정해본 결과, 14.952mV 가 147.105mV 로 약 10배 증가함을 확인하였다.

3. 문제 1 과 문제 2의 설계된 증폭기 회로를 single supply 형태로 전환하고, PSpice를 사용하여 동작상태(AC & Transient responses)를 검증하시오.

![HW5%200a4f56389ee746d09aea97c086865030/image148.bmp](HW5%200a4f56389ee746d09aea97c086865030/image148.bmp)

![HW5%200a4f56389ee746d09aea97c086865030/image149.bmp](HW5%200a4f56389ee746d09aea97c086865030/image149.bmp)

Double Supply에서 GND를 $\frac{V_{\text{CC}}}{2}$, − *V*EE 를 GND 로 바꾸면 Single Supply 로 사용할 수 있다.

**그림3-1) Single Supply 로 바꾼 Inverting Amplifier**

![HW5%200a4f56389ee746d09aea97c086865030/image150.bmp](HW5%200a4f56389ee746d09aea97c086865030/image150.bmp)

**그림3-2) Single Supply Inverting Amplifier AC Sweep**

![HW5%200a4f56389ee746d09aea97c086865030/image151.bmp](HW5%200a4f56389ee746d09aea97c086865030/image151.bmp)

**그림3-3) Single Supply Inverting Amplifier AC Sweep Frequency**

![HW5%200a4f56389ee746d09aea97c086865030/image152.bmp](HW5%200a4f56389ee746d09aea97c086865030/image152.bmp)

**그림3-4) Single Supply Inverting Amplifier Transient Analysis**

![HW5%200a4f56389ee746d09aea97c086865030/image153.bmp](HW5%200a4f56389ee746d09aea97c086865030/image153.bmp)

**그림3-5) Single Suuply Inverting Amplifier Transient Analysis Peak Voltage**

![HW5%200a4f56389ee746d09aea97c086865030/image154.bmp](HW5%200a4f56389ee746d09aea97c086865030/image154.bmp)

Double Supply 에 비해 전압 이득이 약간 감소한 모습을 보이고 있지만 Inverting Amplifier 로 바람직한 동작을 보여주고 있다.

**그림3-6) Single Supply 로 바꾼 Non-Inverting Amplifier**

![HW5%200a4f56389ee746d09aea97c086865030/image155.bmp](HW5%200a4f56389ee746d09aea97c086865030/image155.bmp)

Inverting Amplfier 에서는 전압 분배기 저항을 둘 다 100*KΩ* 으로 했을때는 정상적으로 작동하였다.

하지만, Non-Inverting Amplfier 에서는 전압 분배기 저항을 100*KΩ* 으로 했더니 Transient Analysis 에서는

전압이득이 거의 1에 가깝고, AC Sweep 에서는 Upper 3dB 가 엄청나게 높은 주파수로 올라가는 것을 확인하였다.

따라서 전압분배기의 저항을 100*Ω* 으로 낮추고 해석을 하였다.

**그림3-7) Single Supply Non-Inverting Amplifier AC Sweep**

![HW5%200a4f56389ee746d09aea97c086865030/image156.bmp](HW5%200a4f56389ee746d09aea97c086865030/image156.bmp)

**그림3-8) Single Supply Non-Inverting Amplifier AC Sweep Frequency**

![HW5%200a4f56389ee746d09aea97c086865030/image157.bmp](HW5%200a4f56389ee746d09aea97c086865030/image157.bmp)

**그림3-9) Single Supply Non-Inverting Amplifier Transient Analysis**

![HW5%200a4f56389ee746d09aea97c086865030/image158.bmp](HW5%200a4f56389ee746d09aea97c086865030/image158.bmp)

**그림3-10) Single Suuply Non-Inverting Amplifier Transient Analysis Peak Voltage**

![HW5%200a4f56389ee746d09aea97c086865030/image159.bmp](HW5%200a4f56389ee746d09aea97c086865030/image159.bmp)

Double Supply 에 비해 전압 이득이 많이 감소하였다.

파형은 Non-Inverting Amplifier를 따르고 있다.

4. 주어진 입출력 관계식에 해당되는 회로를 uA741 op amp.(double supply) 1개를 사용하여 direct coupled 구조로 설계하고, PSpice를 이용하여 검증 하시오.

Vout= 2Vin1 - 3Vin2 - Vin3 + 5Vin4

Vout 의 부호를 보고 Vin1 과 Vin4는 Non-Inverting, Vin2 와 Vin3는 Inverting 임을 짐작할 수 있다.

**그림4-1) 예상되는 회로 모양**

![HW5%200a4f56389ee746d09aea97c086865030/image160.bmp](HW5%200a4f56389ee746d09aea97c086865030/image160.bmp)

1개의 Op-amp 만을 사용하여 Inverting, Non-Inverting을 구성하려면 위와 같은 회로모양이 되어야 할 것이다.

계산의 편의를 위해 피드백 저항은 고정을 시킨상태로 *Rf* 를 사용해서 *VO* 이 나오도록 각각의 소자가 *Rf*/*Mx* 의 저항을 가지도록 설정하였다.

이 모양을 그대로 *Vo* 으로 나타내기엔 어려움이 있어 보인다.

그래서 각각 한 개씩만 있다고 가정을 하고 수식의 일반화를 하였다.

**그림4-2) 수식 일반화를 위한 회로**

![HW5%200a4f56389ee746d09aea97c086865030/image161.bmp](HW5%200a4f56389ee746d09aea97c086865030/image161.bmp)

왼쪽과 같은 회로가 있다고 할 때 Inverting 의 경우

$V_{o} = - \frac{\frac{R_{f}}{1}}{\frac{R_{f}}{M_{a}}}V_{a} = - M_{a}V_{a}$ 로 표시가 가능하다

Non-Inverting 의 경우

$V_{o} = \frac{\frac{R_{f}}{s}}{\frac{R_{f}}{M_{1}} + \frac{R_{f}}{s}}(1 + \frac{\frac{R_{f}}{1}}{\frac{R_{f}}{M_{a}}})V_{1}$ 이 된다.

이 수식을 정리하면 $V_{o} = \frac{\frac{R_{f}}{s}}{\frac{R_{f}}{M_{1}} + \frac{R_{f}}{s}}(1 + \frac{\frac{R_{f}}{1}}{\frac{R_{f}}{M_{a}}})V_{1} = \frac{\frac{R_{f}}{s}}{\frac{R_{f}(s + M_{1})}{\text{sM}_{1}}}(1 + M_{a})V_{1} = \frac{M_{1}}{s + M_{1}}(1 + M_{a})V_{1}$ 이다.

Inverting 의 출력이 *Vo* = − *MaVa* 였던것처럼, Non-Inverting 의 출력이 *Vo* = *M*1*V*1 이면 나중에 구하기 쉬운 결과를 나타낼 것이다.

따라서 $V_{o} = \frac{M_{1}}{s + M_{1}}(1 + M_{a})V_{1} = M_{1}V_{1}$ 을 만족하도록 하면, *s* = 1 + *M*1 − *Ma* 임을 구할 수 있다.

마찬가지로 주어진 과제에서처럼 Inverting 2개, Non-Inverting 이 2개 인 상황에서는

*Vo* = *V*1*M*1 + *V*4*M*4 − *V*2*M*2 − *V*3*M*3 가 되고, *s* = 1 + (*M*2 + *M*3) − (*M*1 + *M*4) 가 될 것이다.

주어진 수식이 *Vo* = 2*V*1 − 3*V*2 − *V*3 + 5*V*4 를 만족해야 하므로

*M*1 = 2, *M*2 = 3, *M*3 = 1, *M*4 = 5 이 됨을 알 수 있다.

따라서 *s* = 1 + (3 + 1) − (2 + 5) = − 2 가 나온다.

여기서 s 가 음수가 되면, 저항이 음수가 되는데 이건 말이 안되는 상황이다.

s를 양수로 만들 필요성이 있다.

op-amp에서 negative 에 붙은 저항은 s 값에 더하는 것을 알았다.

결국 *M*2 + *M*3 와 함께 s를 더해줄 *M*5 를 추가할 필요가 있다.

**그림4-3)** *M*5 **가 추가된 회로**

![HW5%200a4f56389ee746d09aea97c086865030/image162.bmp](HW5%200a4f56389ee746d09aea97c086865030/image162.bmp)

*M*

5

가 추가된 회로이다.

*Vo* = *V*1*M*1 + *V*4*M*4 − *V*2*M*2 − *V*3*M*3 은 그대로 유지되고 있지만

*s* = 1 + (*M*2 + *M*3 + *M*5) − (*M*1 + *M*4) 가 되었다.

종전에 *s* = − 2 임을 확인하였으므로, *M*5 = 3 으로 두어 *s* = 1 로 양의 값으로 만들어 주었다.

*Rf* = 10*KΩ* 이라고 가정하고 각각의 M, s 값으로 나눠 다음과 같은 회로를 얻었다.

**그림4-4) 최종 완성된 회로**

![HW5%200a4f56389ee746d09aea97c086865030/image163.bmp](HW5%200a4f56389ee746d09aea97c086865030/image163.bmp)

**그림4-5)** *Vo* = *V*1*M*1 + *V*4*M*4 − *V*2*M*2 − *V*3*M*3

실제 측정은 편의를 위해 vpulse를 이용하여 아래 그래프를 얻었다.

![HW5%200a4f56389ee746d09aea97c086865030/image164.bmp](HW5%200a4f56389ee746d09aea97c086865030/image164.bmp)

**그림4-6)***Vo* **연산결과**

![HW5%200a4f56389ee746d09aea97c086865030/image165.bmp](HW5%200a4f56389ee746d09aea97c086865030/image165.bmp)