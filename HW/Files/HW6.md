# HW6

**전자회로설계(2020년 1학기) 개인별 설계과제 #6**

**제출일자 : 2020년 6월 6일(토) 17:00까지**

**1. 아래 주어진 설계사양에 부합되는 differentiator를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.**

**(설계사양): 사용할 op amp: *u*A741, Double Supply: ± 12 V, 부하저항: 10 kohm**

**Input signal: 10 Hz ~ 1 kHz sine wave,** **Input 크기: 1 V**

**2. 문제 1에서 설계된 differentiator에 1 V sine wave with a frequency of 10 kHz 신호를 input에 인가하고 출력파형을 PSpice를 이용하여 관찰하시오. 또한 정확히 미분 되었는지를 판별하고, 그렇지 못 하다면 원인을 분석하고 대안을 제시하시오.**

**3. 아래 주어진 설계사양에 부합되는 integrator를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.**

**(설계사양): 사용할 op amp: *u*A741, Double Supply: ± 12 V, 부하저항: 10 kohm**

**Input signal: ± 5 V square wave, Input freq.: 500 Hz**

**Output signal: 4 V triangle wave(peak-to-peak)**

**4. 문제 3에서 설계된 integrator에 ± 5 V square wave with a period of 20us 신호를 input에 인가하고 출력파형을 PSpice를 이용하여 관찰하시오. 또한 정확히 적분 되었는지를 판별하고, 그렇지 못 하다면 원인을 분석하고 대안을 제시하시오.**

HW6 : 개인별 설계과제 #6

Pspice Version : OrCad 17.4

2017117876

김승현

1. 아래 주어진 설계사양에 부합되는 differentiator를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.

(설계사양): 사용할 op amp: uA741, Double Supply: ± 12 V, 부하저항: 10 kohm

Input signal: 10 Hz ~ 1 kHz sine wave, Input 크기: 1 V

**[그림 1-1] 간단한 미분기**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image166.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image166.bmp)

[그림 1-1] 은 Op-Amp 로 구성하는 가장 간단한 미분기이다.

입력과 출력에 대한 전압 이득을 구하기 위해서는 *C*1 에 흐르는 전류와 *R*1 에 흐르는 전류가 같다는 것을 이용하면 구할 수 있다.

커패시터에 흐르는 전류는 $i(t) = C_{1}\frac{\text{dV}_{i}}{\text{dt}}$ 이며, 출력 전압은 *V*out = − *i*(*t*)*R*1 이므로 이를 연립하면

$V_{\text{out}} = - R_{1}C_{1}\frac{\text{dV}_{i}}{\text{dt}}$ 을 구할 수 있다.

또 다른 방법으로 주파수 관점에서 바라볼 때 커패시터의 임피던스는 $\frac{1}{\text{sC}_{1}}$ 이므로 반전 증폭기의 전압 이득인 $A_{v} = - \frac{Z_{2}}{Z_{1}}$ 에 의해 *Av* = − sC1*R*1 이 된다.

**[그림 1-2] 주파수 특성**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image167.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image167.bmp)

[그림 1-2] 는 간단한 미분기의 주파수 특성을 나타낸 것이다.

우리는 입력 신호로 10Hz ~ 1KHz 의 Sine wave를 사용할 것 이다.

그리고 Input 의 크기는 1V 이다.

출력 전압이 특별하게 정해진 말이 없고, 미분기라고 하였으므로

출력 전압도 1V 로 가정하고 설계를 시작하였다.

*Av* = − sC1*R*1 이므로, 10Hz ~ 1KHz 의 주파수를 가진 파형을 입력하므로 중간값인 100Hz 일 때 전압이득 1을 가지도록 설계하였다.

즉, $100\text{Hz} = \frac{1}{2\pi R_{1}C_{1}}$ 이 된다.

*R*1 이나 *C*1 중 하나를 임의로 지정하여야 하는데, *R*1 = 50*KΩ* 으로 지정하였다.

따라서 *C*1 = 31.83nF 이 된다.

**[그림 1-3] 간단한 미분기 회로도**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image168.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image168.bmp)

**[그림 1-4] 간단한 미분기 Bode Plot**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image169.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image169.bmp)

100Hz에서 전압이득이 1인지 확인하기 위하여 Bode Plot 이용하였다.

실제로 0dB를 나타내고 있으며, 고주파로 갈수록 상당히 불안정한 모습을 나타내고 있다.

**[그림 1-5] 간단한 미분기 AC Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image170.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image170.bmp)

**[그림 1-6] 간단한 미분기 10Hz Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image171.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image171.bmp)

주파수가 10Hz 인 정현파를 인가하였다. 5 주기만을 표현하기 위하여 $\frac{1}{10\text{Hz}} \times 5 = 500\text{ms}$ 으로 간격을 잡았다.

Bode Plot에서 확인했는 것처럼, 0.1 배의 전압 이득을 나타내고 있으며 미분기의 역할을 잘 수행하고 있다.

**[그림 1-7] 간단한 미분기 100Hz Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image172.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image172.bmp)

주파수가 100Hz 인 정현파를 인가하였다. 5 주기만을 표현하기 위하여 $\frac{1}{100\text{Hz}} \times 5 = 50\text{ms}$ 으로 간격을 잡았다.

**[그림 1-7] 간단한 미분기 1KHz Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image173.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image173.bmp)

1KHz 는 Bode Plot에서 10 배의 전압 이득을 나타내고 있음을 확인할 수 있다.

1KHz 부터는 출력 파형이 깔끔하지 못하고 불안정해지고 있는 모습을 볼 수 있다.

이렇게 되면, 초기에 10Hz ~ 1KHz 까지 모두 동작하는 미분기가 아니라 10Hz ~ 100Hz 만 올바르게 동작하고 있다.

따라서 1KHz 일 때 전압이득이 1 이 되도록 새롭게 설계를 진행하였다.

$1\text{KHz} = \frac{1}{2\pi R_{1}C_{1}}$ 에서 *R*1 = 50*KΩ* 이면 *C*1 = 3.18nF 이다.

**[그림 1-8] 10Hz ~ 1KHz를 사용할 수 있는 미분기 회로도**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image174.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image174.bmp)

**[그림 1-9] 10Hz Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image175.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image175.bmp)

**[그림 1-10] 100Hz Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image176.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image176.bmp)

**[그림 1-11] 1KHz Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image177.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image177.bmp)

이로서, 10Hz 일 때 전압이득 0.01

100Hz 일 때 전압이득 0.1

1KHz 일 때 전압이득 1 이 나오며 10Hz ~ 1KHz 구간내에서 올바른 미분을 하는 미분기가 설계되었다.

2. 문제 1에서 설계된 differentiator에 1 V sine wave with a frequency of 10 kHz 신호를 input에 인가하고 출력파형을 PSpice를 이용하여 관찰하시오. 또한 정확히 미분 되었는지를 판별하고, 그렇지 못 하다면 원인을 분석하고 대안을 제시하시오.

**[그림 2-1] 10KHz Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image178.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image178.bmp)

10KHz를 입력하였을 때 제대로 미분이 되지 않고, 삼각파형으로 나오는 것을 확인할 수 있다.

이때 완벽한 삼각파도 아니고 끝이 12V 가까이에서 잘린 모습인데, 이는 OP AMP 의 Output Voltage를 넘어서 파형이 잘린 것이다.

이는 발산을 하고 있고 불안정하다는 것을 나타낸다.

**[그림 2-2] 미분기의 Bode Plot**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image179.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image179.bmp)

오직 입력 커패시터 하나와 피드백 저항 1개로 이루어진 간단한 미분기의 경우

Bode Plot에서 볼 때 극점이 없다는 것을 알 수 있다.

즉 전달함수에서 극점이 없어서 차단 주파수가 무한대에 존재하여 Unstable 한 상태인 것 이다.

이는 잡음까지 증폭시킬 수 있어 실제로 사용하기에 어려움이 있다.

특히 고주파 노이즈에서 취약할 것이다.

이를 해결하기 위해서는 커패시터와 직렬로 저항을 하나 더 달아줘서 극점을 만들어주면 될 것이다.

**[그림 2-3] 극점을 만들어준 미분기**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image180.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image180.bmp)

*RS* 덕에 전달함수가 바뀌게 될 것이다.

즉 $V_{O}(s) = - \frac{R_{1}}{R_{s} + \frac{1}{\text{sC}_{1}}}V_{I}(s)$ 이므로 $\frac{V_{O}(s)}{V_{I}(s)} = - \frac{\text{sR}_{1}C_{1}}{\text{sR}_{s}C_{1} + 1} = - \frac{s\frac{R_{1}}{R_{s}}}{s + \frac{1}{R_{s}C_{1}}}$ 으로 *RS* 에 극점이 생김을 확인할 수 있다.

극점이 있으면 차단주파수가 생기면서 안정적으로 바뀌게 된다.

**[그림 2-4] 극점을 만들어준**

**미분기의 Bode Plot**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image181.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image181.bmp)

$A_{v} = - \frac{s\frac{R_{1}}{R_{s}}}{s + \frac{1}{R_{s}C_{1}}}$ 에서 분자의 영점은 Phase 에만 영향을 주고 있고, 분모의 극점 $\frac{1}{R_{s}C_{1}}$ 이 Frequency 에 영향을 주고 있다.

High Pass Filter 로서 주파수 범위를 넓히기 위해서는 *Rs* 가 작을수록 유리할 것이다. (즉 모서리에 고주파 성분을 많이 가지고있는 삼각파 등을 미분할 때 효과적이다)

이 과제에서 10KHz 가 안정적으로 미분이 되어야 하므로

$10\text{KHz} = \frac{1}{2\pi R_{s}C_{1}}$ , 이 때 *C*1 = 3.183nF 이므로 *Rs* = 5*KΩ* 이 된다.

**[그림 2-5] 극점을 만들어준 회로도**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image182.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image182.bmp)

**[그림 2-6] 10KHz Transient Analysis**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image183.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image183.bmp)

10KHz에서 정상적으로 미분이 잘 되고 있음을 확인할 수 있다.

**[그림 2-6] Bode Plot**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image184.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image184.bmp)

1번 문제의 Bode Plot 과 비교했을 때 10KHz 부근에서 Overshoot 된 모습이 아닌 안정된 모습의 Voltage dB를 확인할 수 있다.

3. 아래 주어진 설계사양에 부합되는 integrator를 설계하고, PSpice를 사용하여 동작상태를 검증(AC & Transient responses)하시오.

(설계사양): 사용할 op amp: uA741, Double Supply: ± 12 V, 부하저항: 10 kohm

Input signal: ± 5 V square wave, Input freq.: 500 Hz

Output signal: 4 V triangle wave(peak-to-peak)

입력 신호가 Peak to Peak 가 10V, Frequency 가 500Hz 인 사각파이다.

따라서 vpulse를 이용해야 하며 1 주기는 $\frac{1}{500\text{Hz}} = 2\text{ms}$ 임을 알 수 있다.

Delay 는 0s, TR, TF 는 1ns 로 잡았을 때 PW 는 1ms, PER 2ms 로 설정하고 V1=5, V2=-5를 입력한다면 원하는 입력 파형을 얻을 것이다.

**[그림 3-1] 간단한 적분기**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image185.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image185.bmp)

왼쪽 그림은 간단한 적분기의 회로도이다.

*R*1 에 흐르는 전류 $i = \frac{V_{i}}{R_{1}}$ 이고 커패시터에 걸리는 전압은

$V_{C1}(t) = \frac{1}{C_{1}}\int_{0}^{t}{i(t)\text{dt}} + V_{C1}(0^{-})$ 이다.

*V*out = − *VC*1(*t*) 이므로

$V_{\text{out}} = - \frac{1}{R_{1}C_{1}}\int_{0}^{t}{V_{i}(t)\text{dt}} - V_{C1}(0^{-})$ 가 될 것이다.

또 다른 방법으로 주파수 관점에서 바라볼 때 커패시터의 임피던스는 $\frac{1}{\text{sC}_{1}}$ 이므로 반전 증폭기의 전압 이득인 $A_{v} = - \frac{Z_{2}}{Z_{1}}$ 에 의해 $A_{v} = - \frac{\frac{1}{\text{sC}_{1}}}{R_{1}} = - \frac{1}{\text{sR}_{1}C_{1}}$ 이 된다.

**[그림 3-2] 주파수 특성**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image186.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image186.bmp)

왼쪽 그림처럼 극점 1개만을 가지는 주파수 특성을 가지게 된다.

사각파에는 수 많은 주파수들이 푸리에 급수로 이루어져 있으므로 단순히 frequency domain에서 계산은 오히려 더 복잡하다.

따라서 Time domain 에서 계산을 진행할 것이다.

$V_{\text{out}} = - \frac{1}{R_{1}C_{1}}\int_{0}^{t}{V_{i}(t)\text{dt}} - V_{C1}(0^{-})$ 에서 *Vi* = 5*V* 일 때 *t* = 1ms 이다.

즉 $V_{\text{out}} = - \frac{1}{R_{1}C_{1}}\int_{0}^{1m}{5\,\text{dt}}$ 를 만족하고, 사각파에서 반주기를 적분했을 때 삼각파는 Peak to Peak 까지 변동하므로 *V*out = 4 로 두고 계산한다.

또한 $V_{\text{out}} = - \frac{1}{R_{1}C_{1}}\int_{1m}^{2m}{- 5\,\text{dt}}$ 도 만족할 것이다.

즉 $4 = - \frac{5\text{ms}}{R_{1}C_{1}}$ 를 만족해야하고 커패시터가 크면 반응속도가 느리므로 *C*1 = 20nF 으로 두고

*R*1 = 62.5*KΩ* 을 얻었다.

**[그림 3-2] 간단한 적분기 회로도**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image187.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image187.bmp)

**[그림 3-3] 간단한 적분기 Transient Analysis**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image188.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image188.bmp)

예상대로*Vi* 가 마이너스 일 때 삼각파에서는 상승하는 모습을 보여주고 있다.

다만 *VC*1 에 충전되어 있는 Offset 전압에 의해 –10V를 DC 로 둔 삼각파형을 나타내고 있다.

**[그림 3-4] 간단한 적분기 Bode Plot**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image189.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image189.bmp)

Bode Plot 은 당초 예상했던 대로 극점 1개만을 가지는 dB를 나타내고 있다. 만약 100mHz 가 아니라 더 낮은 주파수까지 Trace를 하면, 계속 상승하는 모습을 보여줄 것이다.

따라서 DC 성분이 있을 수록 출력단에서 포화가 일어날 수 있다는 말이 된다.

실제로 매우 작은 DC 성분이 출력을 포화 상태로 만든다.

t=0 일 때 Input Offset Voltage 와 Input Current 가 커패시터를 충전시키고 이는 출력단의 Error Voltage를 유발한다.

4. 문제 3에서 설계된 integrator에 ± 5 V square wave with a period of 20us 신호를 input에 인가하고 출력파형을 PSpice를 이용하여 관찰하시오. 또한 정확히 적분 되었는지를 판별하고, 그렇지 못 하다면 원인을 분석하고 대안을 제시하시오.

**[그림 4-1] 간단한 적분기 PER 20us Vpulse 에 대한 Transient Reponse**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image190.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image190.bmp)

주기가 짧아짐에 따라 적분이 안되고 있음을 확인할 수 있다.

단순하게 생각해서 사각파안에는 수많은 주파수들이 들어있지만 사각파의 주기에 따라 저주파, 저주파의 양이 다를거라고 생각하였다.

그래서 긴 주기를 가지는 사각파를 임의로 인가해봤다.

**[그림 4-2] 간단한 적분기 PER 1sec Vpulse 에 대한 Transient Reponse**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image191.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image191.bmp)

주기가 무려 1초나 되는 사각파를 인가했더니, 출력전압은 적분은 됐지만 포화가 된 모습을 나타낸다.

처음에 예상했던 대로 주기가 길수록 DC 성분이 많아지고 주기가 짧을수록 DC 성분이 적다는 것을 알 수 있다.

따라서 PER 이 20us 인 Vpulse 는 주기가 짧아 DC 성분이 적다.

간단한 적분기는 극점이 하나밖에 없다.

Bode Plot에서 확인할 수 있었듯이 고주파로 갈수록 마이너스 dB 로 끝없이 가는 것과 동일한 결과이다.

이를 개선하기 위해서는 적당한 위치에 저항을 추가해줄 수 있다.

**[그림 4-3] 개선된 적분기**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image192.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image192.bmp)

$H(s) = - \frac{R_{F}f║\frac{1}{\text{sC}_{1}}}{R_{1}}$ 이므로 $H(s) = - \frac{\frac{R_{F}}{1 + \text{sR}_{F}C_{1}}}{R_{1}} = - \frac{R_{F}/R_{1}}{1 + \text{sR}_{F}C_{1}}$ 이다.

*RFC*1 이 클수록 뛰어난 Low Pass Filter 가 될 것이다.

현재 *C*1 = 20nF 이고, 대략적으로 주기가 20us 인 사각파에 50KHz 가 많다고 가정을 했다.

따라서 $50\text{KHz} = \frac{1}{2\pi R_{F}C_{1}}$ 에서 *C*1 = 20nF 대입시

**[그림 4-5] 개선된 적분기 회로도**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image193.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image193.bmp)

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image194.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image194.bmp)

*R*

*F*

= 159.15

*Ω*

을 얻을 수 있었다.

**[그림 4-4] 개선된 적분기 Bode Plot**

**[그림 4-6]** *RF* = 160*Ω* **일 때의 Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image195.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image195.bmp)

처음에 비해 확실히 적분이 되는 모습을 볼 수 있다.

하지만 다소 만족스럽지 못한 결과를 나타내고 있었다.

*RF* 가 클수록 더 많은 고주파를 커버할 수 있으므로 *RF* 를 1.6*KΩ* 으로 개선해 보았다.

**[그림 4-6]** *RF* = 1.6*KΩ* **일 때의 Transient Response**

![HW6%207ba87d6fe8d444bb9f533c230192dcdb/image196.bmp](HW6%207ba87d6fe8d444bb9f533c230192dcdb/image196.bmp)

*RF* = 160*Ω* 일 때의 비해 상대적으로 더 나은 적분 결과를 보여주고 있다.