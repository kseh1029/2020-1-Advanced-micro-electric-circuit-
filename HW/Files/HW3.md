# HW3

**전자회로론(2020년 1학기) 개인별 설계과제 #3**

**제출일자 : 2020년 4월 25일(토) 17:00까지**

1. 아래 주어진 설계사양에 부합되는 open loop 형태의 전압증폭기 등가회로를 설계하고, 개발된 등가회로를 Spice를 사용하여 설계사양을 검증하시오.

설계사양 : 입력저항 : 2 Mohm

전압이득 : 100 dB

Pole frequencies : 1e6, 1e7, 1e8 rad/sec

출력저항 : 10 ohm

2. 문제 1에서 개발된 등가회로를 이용하여 β=0.1인 series-shunt negative feedback amplifier를 설계하고, Spice를 사용하여 아래 사항을 검증하고 문제 1의 결과와 비교 분석하시오.

입력저항, 출력저항,

전압이득, 3dB frequency,

unity gain frequency/bandwidth

3. Feedback gain, β값에 따른 stable, marginally stable, unstable amplifiers 회로를 설정하고, 각 영역 대표회로의 impulse response를 Spice를 통하여 구하시오. 그 결과를 정성적으로 분석 하시오.

4. 문제 3에서 구성된 negative feedback amplifier가 안정되게 동작할 수 있도록 frequency compensation(주파수 보상)을 행하시오. 주파수 보상 방식은 dominant pole compensation technique 을 사용하시오.

5. 문제 3에서 얻어진 영역별 대표 β값을 그대로 사용하여, 주파수 보상된 amplifier(문제 4 결과)의 impulse response를 Spice를 통하여 구하고, 그 결과를 문제 3의 결과와 비교 분석 하시오.

**주의사항 : 모든 문제는 개인적인 분석을 요함**

HW3 : 개인별 설계과제 #3

Pspice Version : OrCad 16.5

2017117876

김승현

1. 아래 주어진 설계사양에 부합되는 open loop 형태의 전압증폭기 등가회로를 설계하고, 개발된 등가회로를 Spice를 사용하여 설계사양을 검증하시오.

설계사양 : 입력저항 : 2 Mohm

전압이득 : 100 dB

Pole frequencies : 1e6, 1e7, 1e8 rad/sec

출력저항 : 10 ohm

설계사양에 따라 해석해보자면, 입력저항 *R*id 가 2*MΩ* 이고, 전압이득은 100dB = 20log10105 이므로 *Av* = 105 이다. 극점 주파수를 106, 107, 108 rad/sec 으로 지정하기 위해선 RC 회로가 있어야할 필요성이 있었다.

그리고 출력저항은 *RL* 이 10*Ω* 으로 설정되면 된다.

극점주파수를 고려하지 않은 단순한 등가회로는 다음과 같다. 신호저항과 증폭기의 *ro* 는 무시한 아주 간단한 회로이다. 물론 *μ* = 105 가 될 것이다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image47.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image47.bmp)

PSpice에서 이를 실현하기 위해서 BJT를 이용해 공통 이미터와 이미터 팔로워를 통해 만들려고 했으나 등가회로로 구현하기 위해 E/Analog 소자를 이용해 종속전압을 달았다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image48.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image48.bmp)

회로 모양은 위와 같고, 종속전압을 4개로 나눈 이유는 극점을 명확하게 106, 107, 108 rad/sec 으로 지정하기 위해 나눴다.

그러기 위해서 적절한 R과 C를 정해줄 필요가 있었는데, $\omega = \frac{1}{\text{RC}}$ 에 의해 각각 106, 107, 108 에 해당하는 *ω* 와 R은 1*kΩ* 로 고정시켜서 각각 1nF, 100pF, 10pF 로 정하게 되었다.

각 극점이 제대로 지정됐는지 확인하기 위해 각각의 커패시터들 한 개씩만 적용하여 극점을 확인해 보았다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image49.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image49.bmp)

위 사진은 C1 인 1nF 만 단독으로 있을때의 Frequency Plot 이다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image50.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image50.bmp)

$\frac{10^{6}}{2\pi} = 159.155\text{kHz}$ 와 오차범위 내 같은결과를 나타내고 있다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image51.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image51.bmp)

위 사진은 C2 인 100pF 만 단독으로 있을때의 Frequency Plot 이다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image52.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image52.bmp)

$\frac{10^{7}}{2\pi} = 1.591\text{MHz}$ 와 오차범위 내 같은결과를 나타내고 있다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image53.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image53.bmp)

위 사진은 C3 인 10pF 만 단독으로 있을때의 Frequency Plot 이다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image54.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image54.bmp)

$\frac{10^{8}}{2\pi} = 15.91\text{MHz}$ 와 오차범위 내 같은결과를 나타내고 있다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image55.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image55.bmp)

위 사진은 C1, C2, C3가 모두 있을 때의 Frequency Plot 이다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image56.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image56.bmp)

C1 에 가장 큰영향을 받아 157.21KHz 의 3dB 주파수를 나타내고 있다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image57.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image57.bmp)

전압이득 역시 dB Scale 로 확인했을 때에 100dB 가 나왔다.

2. 문제 1에서 개발된 등가회로를 이용하여 β=0.1인 series-shunt negative feedback amplifier를 설계하고, Spice를 사용하여 아래 사항을 검증하고 문제 1의 결과와 비교 분석하시오.

입력저항, 출력저항,

전압이득, 3dB frequency,

unity gain frequency/bandwidth

![HW3%200a2e85eab68846c7994aeb7a50b98158/image58.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image58.bmp)

처음에 만든 증폭기 회로에서 Negative Feedback을 주어서 직렬병렬 전압증폭기 구조로 만들었다.

이 때 *β* 는 0.1 이므로 Gain을 0.1 로 설정하였다.

이론상으로 $A_{f} = \frac{A}{1 + A\beta} = \frac{10^{5}}{1 + 10^{5}*0.1} = 9.99$ 인 전압이득을 가지게 된다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image59.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image59.bmp)

입력이 1V 일 때 출력은 10V 가까이 출력되는 것을 확인할 수 있다.

Cursor를 이용해 값을 확인하였다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image60.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image60.bmp)

위의 그림처럼 9.999V 가 *V*out 에 걸린다.

즉, 전압이득이 9.99[V/V] 이다.

Unity gain Frequency 와 Bandwidth 는 다음과 같다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image61.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image61.bmp)

![HW3%200a2e85eab68846c7994aeb7a50b98158/image62.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image62.bmp)

대략적으로 54.734MHz에서 7.8697 dB를 나타내고 있다. 이 보다 약간 큰 주파수인 54.8MHz 정도에서 Unity Frequency 임을 알 수 있고, 대칭되지 않는 주파수 Plot 이므로 Unity Bandwidth 또한 Unity Freqeuncy 와 동일하다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image63.png](HW3%200a2e85eab68846c7994aeb7a50b98158/image63.png)

Bias Point Analysis를 통해 입출력 저항을 구하였다.

3. Feedback gain, β값에 따른 stable, marginally stable, unstable amplifiers 회로를 설정하고, 각 영역 대표회로의 impulse response를 Spice를 통하여 구하시오. 그 결과를 정성적으로 분석 하시오.

pole frequency 가 106, 107, 108 이며, 전압이득은 105 이므로

$A(s) = \frac{10^{5}}{(1 + s/10^{6})(1 + s/10^{7})(1 + s/10^{8})}$ 일 것이다.

Marginally stable을 구하기 위해 위상이 –180도일때의 주파수를 구한다.

$A(j\omega) = \frac{10^{5}}{(1 + j\omega/10^{6})(1 + j\omega/10^{7})(1 + j\omega/10^{8})}$ 이므로

$\theta = \frac{1}{\tan^{- 1}(\frac{\omega}{10^{6}}) + \tan^{- 1}(\frac{\omega}{10^{7}}) + \tan^{- 1}(\frac{\omega}{10^{8}})} = - 180{^\circ}$

이를 만족하는 *ω* = 3.331 × 107 rad/sec 이다.

Stable Operation을 하려면 ∣ Avert*β*cr⟨1 을 만족해야 한다.

$\mid \text{Avert} = \frac{10^{5}}{\sqrt{1 + (\frac{\omega}{10^{6}})^{2}}\sqrt{1 + (\frac{\omega}{10^{7}})^{2}}\sqrt{1 + (\frac{\omega}{10^{8}})^{2}}}$ 이므로 *ω* = 3.331 × 107 rad/sec 를 대입시 818.594 가 나온다.

∣ Avert*β*cr⟨1 를 만족할 때 stable 하므로, *β*cr ≥ 1.221 × 10 − 3 일 때 osciliation 이 일어날 것이다.

따라서, stable 은 *β*cr⟨1.221 × 10 − 3 일 때 이며, *β*cr = 1.221 × 10 − 3 일 때 marginally stable 이다.

엄밀하게 확인을 하기 위해서 Bode Plot을 해석 해보면 다음과 같다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image64.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image64.bmp)

x축은 Hz 로 그렸고, y 축은 dB 로 그린 Bode Plot 이다.

오메가로 표시하지 않았기 때문에 2*π* 를 나눈 Hz 로 표시를 하였다.

A 회로와 *β* 회로를 별도로 봤을 때, 위상이 –180도가 되는 주파수가 *ω* = 3.331 × 107 rad/sec 즉 *f* = 5.301MHz 이므로 이때의 dB는 $\mid \text{Avert} = \frac{10^{5}}{\sqrt{1 + (\frac{\omega}{10^{6}})^{2}}\sqrt{1 + (\frac{\omega}{10^{7}})^{2}}\sqrt{1 + (\frac{\omega}{10^{8}})^{2}}}$ 가 818.594 이므로 20log10(818.594) = 58.26dB 이다.

이 때를 기준으로 –20dB/decade를 가지는 부분에 *β* 가 있다면, 안정적이라고 볼 수 있다.

왜냐면, *f*180 이 –40dB/decade 구간에 위치하므로 직선 $20\log_{10}\frac{1}{\beta}$ 가 –20dB/decade 구간에서 20logvertAvert와 교차하면 위상 여유는 양이 되고 귀환 증폭기가 안정해지며 *β* 가 주파수에 의존하는 일반적인 경우에도 $20\log_{10}\frac{1}{\beta}$와 20logvertAvert 의 교차점에서 기울기들의 차이가 20 dB/decade를 초과하지 않으면 귀환 증폭기는 안정하다.

따라서 Stable 은 90dB, Marginally Stable 은 58.26dB, Unstable은 50dB 로 지정하였다.

이 때의 *β* 값은 각각 31.6*μ*, 1.221*m*, 3.162*m* 이다.

**< 각각** *β* **에 따른 Impulse Reponse >**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image65.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image65.bmp)

Impulse Response를 테스트 하기 위해 VPULSE 전원을 인가 하였다.

*β* **= 31.6u 일 때 Impuse Reponse**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image66.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image66.bmp)

*β* **= 1.221m 일 때 Impuse Reponse**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image67.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image67.bmp)

*β* **= 3.162m 일 때 Impulse Reponse**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image68.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image68.bmp)

*β* **가 클수록 출력 부분에 point 가 많이 찍혀있는데, 그부분을 확대해보면 다음 그림과 같다.**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image69.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image69.bmp)

크게 확대해서 보면 불안정한 회로의 경우 발산을 하려고 하는 모습이 보인다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image70.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image70.bmp)

반면 안정한 회로의 경우 바로 수렴을 한다.

*β* 값에 따른 안정도를 자세히 분석하기 위해 Bode Plot 으로 확인했다.

**< 각각** *β* **에 따른 Bode Plot >**

*β* **= 31.6u 일 때 Bode Plot**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image71.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image71.bmp)

Bode Plot을 통해 dB Scale을 확인해 본 결과 overshoot, 급격한 phase 변동도 없는 안정한 회로임을 확인 하였다.

*β* **= 1.221m 일 때 Bode Plot**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image72.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image72.bmp)

반면 임계값을 기준으로 했을 때도 위상이 완전히 반전되거나 그러지는 않지만 급격한 변동을 보여주고 있으며

Overshoot 가 있음을 확인하였다.

*β* **= 3.162m 일 때 Bode Plot**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image73.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image73.bmp)

실제로 unstable 할 수 있는 *β* 값을 부여했을 때, 위상이 반전되고 overshoot 가 있음을 확인 하였다.

하지만 위의 해석은 어디까지나 $A_{f} = \frac{A}{1 + A\beta}$ 에 대한 Bode Plot 분석이다.

*Aβ* 를 해석하면 Gain Margin 과 Phase Margin을 구해 더욱더 정확하게 확인이 가능하다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image74.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image74.bmp)

![HW3%200a2e85eab68846c7994aeb7a50b98158/image75.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image75.bmp)

*β* 값이 31.6u 일 때 기준으로 dB가 0이면, 그 때의 Phase 는 –88.439도 이다. Phase Margin 이 –180 기준으로 볼 때 91.561도 있음을 확인할 수 있다.

Phase 가 –180도 일 때 dB는 –31.898이므로 Gain Margin 는 31.898 이다.

둘다 양수의 Margin을 가지므로 확실히 안정하다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image76.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image76.bmp)

![HW3%200a2e85eab68846c7994aeb7a50b98158/image77.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image77.bmp)

*β* 값이 1.221m 일 때 기준으로 dB가 0이면, 그 때의 Phase 는 –180도 이다. 정확하게 Phase Margin 기준에 일치한다.

Phase 가 –180도 일 때 dB 역시 0이므로 정확하게 Gain Margin 기준에 일치한다.

따라서, Marginally Stable 한 *β* 라고 판단이 가능하다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image78.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image78.bmp)

![HW3%200a2e85eab68846c7994aeb7a50b98158/image79.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image79.bmp)

*β* 값이 3.162m 일 때 기준으로 dB가 0이면, 그 때의 Phase 는 –195.892 도 이다. -180 도 보다 더 넘어가있으므로 Phase Margin 이 없다.

Phase 가 –180도 일 때 기준으로 8.2428dB를 나타내므로 0dB 밑으로 내려오지 않아 Gain Margin 도 없다.

4. 문제 3에서 구성된 negative feedback amplifier가 안정되게 동작할 수 있도록 frequency compensation(주파수 보상)을 행하시오. 주파수 보상 방식은 dominant pole compensation technique 을 사용하시오.

dominant pole compensation technique 은 원래의 증폭기가 불안정할 때 극점을 추가하는 방법이다.

가장 간단한 방법으로 충분히 낮은 주파수에 새로운 극점을 추가하여 개방 루프 이득 A를 A’ 로 수정하여 주파수를 보상한다.

여러 방법이 있지만, *R*id 에 커패시터를 달아주는 방식으로 진행하였다.

$\frac{1}{\text{RC}} = 2\pi f$ 이며 *R*id = 2*MΩ* 이다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image80.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image80.bmp)

원하는 폐쇄 루프 이득에 맞게 주파수를 정해줘야 한다.

이 과제에서는 *β* 가 0.1 로 맞춰지는게 목적 이므로, 20dB를 기준으로 잡았다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image81.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image81.bmp)

따라서 $\frac{1}{2M\Omega*C} = 2\pi*1.591$ 을 만족하는 50.01nF 을 추가할 커패시터로 사용한다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image82.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image82.bmp)

![HW3%200a2e85eab68846c7994aeb7a50b98158/image83.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image83.bmp)

새 극점을 추가하고 나서 A 만의 회로의 Bode Plot을 확인해 보았다.

dB 가 0 에 가까울 때 Phase 는 –126.09도 이다. Phase Margin 이 –180 기준으로 볼 때 54도 있음을 확인할 수 있다.

Phase 가 –180도 일 때 dB는 –19.964이므로 Gain Margin 는 19.964 이다.

A 만의 회로에서도 안정됨을 확인할 수 있다.

5. 문제 3에서 얻어진 영역별 대표 β값을 그대로 사용하여, 주파수 보상된 amplifier(문제 4 결과)의 impulse response를 Spice를 통하여 구하고, 그 결과를 문제 3의 결과와 비교 분석 하시오.

**< 각각** *β* **에 따른 Impulse Reponse >**

*β* **= 1.221m 일 때 Impuse Reponse**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image84.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image84.bmp)

*β* **= 1.221m 일 때 Impuse Reponse**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image85.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image85.bmp)

*β* **= 3.162m 일 때 Impuse Reponse**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image86.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image86.bmp)

주파수 보상을 하고나서 전압이득이 낮아졌지만, 출력전압이 쭈우욱 유지되려 하는 모습을 나타내고 있다.

어떤 의미를 가지는지 Bode Plot 으로 자세히 알아보았다.

**< 각각** *β* **에 따른 Bode Plot >**

*β* **값이 31.6u 일 때 Bode Plot**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image87.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image87.bmp)

*β* **값이 1.221m 일 때 Bode Plot**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image88.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image88.bmp)

*β* **값이 3.162m 일 때 Bode Plot**

![HW3%200a2e85eab68846c7994aeb7a50b98158/image89.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image89.bmp)

기존에 주파수 보상을 하지 않았을때와 확연한 차이를 보여준다.

우선, 전체적으로 Overshoot 가 사라졌고, Phase 의 급격한 변화 또한 사라졌다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image90.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image90.bmp)

*β* 값이 0.1 일 때가 처음 설계할 때 처음 기준을 잡았던 *β* 이다.

2번에서 구한 회로에 비해 Bandwidth 는 감소하였으나 overshoot 가 사라져 안정된 모습을 보인다.

![HW3%200a2e85eab68846c7994aeb7a50b98158/image91.bmp](HW3%200a2e85eab68846c7994aeb7a50b98158/image91.bmp)

*β* 값이 0.1 일 때의 Frequency Reponse 이다.