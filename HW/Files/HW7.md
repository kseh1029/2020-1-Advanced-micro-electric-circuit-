# HW7

**전자회로설계(2020년 1학기) 개인별 설계과제 #7**

**제출일자 : 2020년 6월 20일(토) 17:00까지**

**1. 아래 주어진 설계사양에 부합되는 passive filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.**

**설계사양 : Butterworth type 4차 band-pass filter**

**Quality factor : 20**

**Center frequency : 1 kHz**

**사용저항 : 10 kohm**

**2. 아래 주어진 설계사양에 부합되는 passive filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.**

**설계사양 : Butterworth type 6차 low-pass filter**

**Cutoff frequency : 15 kHz**

**사용저항 : 10 kohm**

**3. 아래 주어진 설계사양에 부합되는 active filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.**

**설계사양 : Butterworth type 2차 band-pass filter**

**Quality factor : 10**

**Center frequency : 1 kHz**

**사용 capacitor : 0.1uF**

**Gain in pass-band : 1**

**4. 아래 주어진 설계사양에 부합되는 active filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.**

**설계사양 : Butterworth type 4차 low-pass filter**

**Cutoff frequency : 15 kHz**

**사용 capacitor : 0.1 uF**

**Gain in pass-band : 2**

HW7 : 개인별 설계과제 #7

Pspice Version : OrCad 17.4

2017117876

김승현

1. 아래 주어진 설계사양에 부합되는 passive filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.

설계사양 : Butterworth type 4차 band-pass filter

Quality factor : 20

Center frequency : 1 kHz

사용저항 : 10 kohm

*f*0 **가 Center Frequency 이다.**

![HW7%204662f1548702442784321abd77f50897/image197.png](HW7%204662f1548702442784321abd77f50897/image197.png)

Passive Band-passFilter를 만들기 위해서는 R과 C를 이용하거나 R과 L을 이용하는 방법, RLC를 이용하는 방법이 있다.

본 과제에서는 편의를 위해 R과 C로만 Passive Filter를 설계할 것이다.

> 설계를 할 때 Quality factor 인 Q 인자가 높을수록 좁은 통과 대역을 갖게 되고 Q 인자가 낮을수록 넓은 통과 대역을 갖게 된다.

왼쪽 그림에서 *f*0 가 Center Frequency 으로 중심 주파수 혹은 Resonant Frequency 라고 불린다.

Band-pass Filter 는 어떤 기준이 되는 저주파와 고주파는 잘라내고 중간대역만 통과시키는 필터이다.

따라서 Low-pass Filter 와 High-pass Filter를 설계하여 두 개를 연결 시키면 중간대역만 얻을 수 있다.

**Low-pass Filter**

![HW7%204662f1548702442784321abd77f50897/image198.bmp](HW7%204662f1548702442784321abd77f50897/image198.bmp)

![HW7%204662f1548702442784321abd77f50897/image199.bmp](HW7%204662f1548702442784321abd77f50897/image199.bmp)

**LPF Bode Plot**

**High-pass Filter**

![HW7%204662f1548702442784321abd77f50897/image200.bmp](HW7%204662f1548702442784321abd77f50897/image200.bmp)

![HW7%204662f1548702442784321abd77f50897/image201.bmp](HW7%204662f1548702442784321abd77f50897/image201.bmp)

**HPF Bode Plot**

**Band-pass Filter Bode Plot**

![HW7%204662f1548702442784321abd77f50897/image202.bmp](HW7%204662f1548702442784321abd77f50897/image202.bmp)

![HW7%204662f1548702442784321abd77f50897/image203.bmp](HW7%204662f1548702442784321abd77f50897/image203.bmp)

**HPF 와 LPF를 연결한 필터**

여기서 Band Width 는 *fC*2 − *fC*1 이 될 것이다.

Center Frequency 혹은 Resonant Frequency 는 $f_{0} = \sqrt{f_{C1}f_{C2}}$ 로 구할 수 있다.

Quality Factor $Q \equiv \frac{f_{0}}{\text{BW}}$ 로 정의된다.

Cutoff Frequency 는 $f_{C1 =}\frac{1}{2\pi R_{1}C_{1}},f_{C2 =}\frac{1}{2\pi R_{2}C_{2}}$ 로 구할 수 있다.

$f_{C1} = f_{0} - \frac{\text{BW}}{2}$, $f_{C2} = f_{0} + \frac{\text{BW}}{2}$ 로 근사화 할 수 있다.

참고로 Band Width를 *ωC*2 − *ωC*1 로 잡게 된다면

Center Frequency 또한 $\omega_{0} = \sqrt{\omega_{C1}\omega_{C2}}$ 이 되고, Quality Factor $Q \equiv \frac{\omega_{0}}{\text{BW}}$ 일 것이다.

이 과제에서 설계 조건은 Q factor 는 20, Center Frequency 는 1KHz, 저항은 10*KΩ* 이였다.

따라서 $Q \equiv \frac{f_{0}}{\text{BW}}$ 에 의해 $\text{BW} = \frac{f_{0}}{Q} = \frac{1\text{KHz}}{20} = 50$ 이므로

*fC*1 = 975Hz, *fC*2 = 1025Hz 가 된다.

$f_{C1 =}\frac{1}{2\pi R_{1}C_{1}} = 975\text{Hz} = \frac{1}{2\pi*10K\Omega*C_{1}}$ 에 의해 *C*1 = 16.32nF

$f_{C2 =}\frac{1}{2\pi R_{2}C_{2}} = 1025\text{Hz} = \frac{1}{2\pi*10K\Omega*C_{2}}$ 에 의해 *C*2 = 15.53nF 을 선택할 수 있다.

**2nd Order Band-Pass Filter 회로도**

![HW7%204662f1548702442784321abd77f50897/image204.bmp](HW7%204662f1548702442784321abd77f50897/image204.bmp)

위 회로는 설계 조건을 기반으로 만든 2차 Band-pass Filter 이다. 하지만 4차 Band-Pass Filter를 만들어야 하므로 같은 회로를 한번 더 붙여줄 필요성이 있다.

여러 필터를 함께 연결하여 사용해 차수를 높이는 것은 필터의 성능을 향상시키기 위해 할 수 있는 방법 중 하나이기 때문이다.

**4th Order Band-Pass Filter 회로도**

![HW7%204662f1548702442784321abd77f50897/image205.bmp](HW7%204662f1548702442784321abd77f50897/image205.bmp)

![HW7%204662f1548702442784321abd77f50897/image206.bmp](HW7%204662f1548702442784321abd77f50897/image206.bmp)

![HW7%204662f1548702442784321abd77f50897/image207.bmp](HW7%204662f1548702442784321abd77f50897/image207.bmp)

최초 설계한 2차 Band-pass Filter를 연결해 4차 Band-pass Filter 로 만들었다

*FL* = 975Hz, *FH* = 1025Hz 가 나올것이라 생각했지만 그렇지 않았다.

Bandwidth 가 너무 넓게 나와서 *f*0 를 $\sqrt{390.61*2.558K}$ 을 확인해보니 1000Hz 는 올바르게 나왔다.

Quality Factor 가 20이나 되기 때문에 상당히 뾰족한 모양의 그래프를 예상했지만 설계상의 문제인지 그런 결과를 얻기가 어려웠다.

그래서 R, C 만의 회로로는 설계가 어려워 보였기 때문에 R, L, C를 모두 이용해서 Band-pass Filter 설계를 시도하였다.

![HW7%204662f1548702442784321abd77f50897/image208.bmp](HW7%204662f1548702442784321abd77f50897/image208.bmp)

위 그림은 2nd Order Band-pass Filter 이다.

해당 회로에서 L 과 C 의 공진으로 인해 전류가 흐른다고 가정시 인덕터에 걸리는 전압은 $V_{L} = \frac{V_{i}}{R}\text{sL}$ 즉 절대값으로 표현시 $\mid V_{L} \mid = \frac{V_{i}}{R}\omega_{0}L$ 이며 커패시터에 걸리는 전압은 $V_{C} = \frac{V_{m}}{R}\frac{1}{\text{sC}},\, \mid V_{C} \mid = \frac{V_{m}}{R}\frac{1}{\omega_{0}C}$ 이다.

이 두 식에서*Vi* 는 입력이므로 Q를 $\frac{\omega_{0}L}{R}$ 혹은 $\frac{1}{R\omega_{0}C}$으로 둘 수 있다.

설계조건에서 *f*0 = 1KHz 였고, Q는 20, *R* = 10*KΩ* 인 것을 고려하면 $Q = \frac{1}{R\omega_{0}C}$ 에 의해

$20 = \frac{1}{10K\Omega*2\pi*1\text{KHz}*C}$ 으로 커패시턴스를 얻을 수 있다.

따라서 *C* = 795.775pF 이다.

마찬가지로 $Q = \frac{\omega_{0}L}{R}$ 에 의해 $20 = \frac{2\pi*1\text{KHz}*L}{10K\Omega}$ 으로 인덕턴스 *L* = 31.83*H* 이다.

**4th Order Band-Pass Filter (RLC) 회로도**

![HW7%204662f1548702442784321abd77f50897/image209.bmp](HW7%204662f1548702442784321abd77f50897/image209.bmp)

![HW7%204662f1548702442784321abd77f50897/image210.bmp](HW7%204662f1548702442784321abd77f50897/image210.bmp)

![HW7%204662f1548702442784321abd77f50897/image211.bmp](HW7%204662f1548702442784321abd77f50897/image211.bmp)

$\text{BW} = \frac{f_{0}}{Q} = \frac{1\text{KHz}}{20} = 50$ 이므로 *fL* = 975Hz, *fH* = 1025Hz 가 나왔어야 했지만 약간의 차이가 있었다.

따라서 소자 값을 수정해 스케일링을 해줄 필요가 있었다.

![HW7%204662f1548702442784321abd77f50897/image212.bmp](HW7%204662f1548702442784321abd77f50897/image212.bmp)

![HW7%204662f1548702442784321abd77f50897/image213.bmp](HW7%204662f1548702442784321abd77f50897/image213.bmp)

![HW7%204662f1548702442784321abd77f50897/image214.bmp](HW7%204662f1548702442784321abd77f50897/image214.bmp)

이로서 50Hz 정도의 Band-pass를 가지는 Filter 가 설계되었다.

2. 아래 주어진 설계사양에 부합되는 passive filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.

설계사양 : Butterworth type 6차 low-pass filter

Cutoff frequency : 15 kHz

사용저항 : 10 kohm

**Low-pass Filter**

![HW7%204662f1548702442784321abd77f50897/image198.bmp](HW7%204662f1548702442784321abd77f50897/image198.bmp)

![HW7%204662f1548702442784321abd77f50897/image199.bmp](HW7%204662f1548702442784321abd77f50897/image199.bmp)

**LPF Bode Plot**

Low-pass Filter 설계를 위해 R과 C를 이용한 회로이다.

$f_{C1 =}\frac{1}{2\pi R_{1}C_{1}}$ 이므로 $15\text{KHz} = \frac{1}{2\pi*10K\Omega*C_{1}}$ 이므로 *C*1 = 1061pF 이다.

**1st Order Low-pass Filter 회로도**

![HW7%204662f1548702442784321abd77f50897/image215.bmp](HW7%204662f1548702442784321abd77f50897/image215.bmp)

1차 로우패스 필터를 AC Sweep 한 결과, 당초 예상했던 3dB 주파수가 15KHz 에 가까운 14.96KHz 가 나왔다.

![HW7%204662f1548702442784321abd77f50897/image216.bmp](HW7%204662f1548702442784321abd77f50897/image216.bmp)

![HW7%204662f1548702442784321abd77f50897/image217.bmp](HW7%204662f1548702442784321abd77f50897/image217.bmp)

![HW7%204662f1548702442784321abd77f50897/image218.bmp](HW7%204662f1548702442784321abd77f50897/image218.bmp)

![HW7%204662f1548702442784321abd77f50897/image219.bmp](HW7%204662f1548702442784321abd77f50897/image219.bmp)

![HW7%204662f1548702442784321abd77f50897/image220.bmp](HW7%204662f1548702442784321abd77f50897/image220.bmp)

이 회로를 총 6단으로 연결시켜 보았다.

그랬더니 예상치도 못하게 작은 값이 나왔다.

다단으로 붙을 경우 주파수도 변동이 생기고, 전압 이득도 급격하게 떨어지고 있음을 확인할 수 있었다.

1061pF 일 때 0.86KHz 가 나왔으므로, 커패시터를 일정 비율로 더 줄인다면 15KHz 로 만들 수 있을거라 생각했다.

$\frac{15\text{KHz}}{0.86\text{KHz}} = 17.4419$ 배 차이나므로 $\frac{1061\text{pF}}{17.4419} = 60.48\text{pF}$ 을 적용시켰다.

![HW7%204662f1548702442784321abd77f50897/image221.bmp](HW7%204662f1548702442784321abd77f50897/image221.bmp)

![HW7%204662f1548702442784321abd77f50897/image222.bmp](HW7%204662f1548702442784321abd77f50897/image222.bmp)

![HW7%204662f1548702442784321abd77f50897/image223.bmp](HW7%204662f1548702442784321abd77f50897/image223.bmp)

이로서 6차 Low-pass Filter를 설계할 수 있었다.

3. 아래 주어진 설계사양에 부합되는 active filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.

설계사양 : Butterworth type 2차 band-pass filter

Quality factor : 10

Center frequency : 1 kHz

사용 capacitor : 0.1uF

Gain in pass-band : 1

![HW7%204662f1548702442784321abd77f50897/image224.jpeg](HW7%204662f1548702442784321abd77f50897/image224.jpeg)

![HW7%204662f1548702442784321abd77f50897/image225.bmp](HW7%204662f1548702442784321abd77f50897/image225.bmp)

왼쪽 그림은 OP-Amp를 이용해 Active Filter를 만드는 방법을 나타낸 그림이다.

여기서 Band-pass Filter 에 맞게 그린 회로가 오른쪽 그림이다.

![HW7%204662f1548702442784321abd77f50897/image226.bmp](HW7%204662f1548702442784321abd77f50897/image226.bmp)

![HW7%204662f1548702442784321abd77f50897/image227.bmp](HW7%204662f1548702442784321abd77f50897/image227.bmp)

![HW7%204662f1548702442784321abd77f50897/image228.bmp](HW7%204662f1548702442784321abd77f50897/image228.bmp)

*Vx* **에 대하여 KCL을 적용**

따라서 $\frac{V_{o}}{V_{i}} = - \frac{Y_{1}Y_{3}}{Y_{5}(Y_{1} + Y_{2} + Y_{3} + Y_{4}) + Y_{2}Y_{4}}$ 라는 식을 얻었다.

![HW7%204662f1548702442784321abd77f50897/image229.bmp](HW7%204662f1548702442784321abd77f50897/image229.bmp)

*Y*1=G1,Y2=G*2,Y*3= sC1,*Y*4= sC2,*Y*5=*G*3를 대입을 한다.

식을 일반적으로 Q Factor 와 공진주파수가 고려된 $\frac{K\omega_{n}}{s^{2} + \frac{\omega_{n}}{Q}s + {\omega_{n}}^{2}}$ 꼴로 맞춰준다.

![HW7%204662f1548702442784321abd77f50897/image230.bmp](HW7%204662f1548702442784321abd77f50897/image230.bmp)

![HW7%204662f1548702442784321abd77f50897/image231.bmp](HW7%204662f1548702442784321abd77f50897/image231.bmp)

${\omega_{n}}^{2} = \frac{G_{1}G_{3} + G_{2}G_{3}}{C_{1}C_{2}}$, $k = \sqrt{\frac{C_{1}C_{2}}{G_{1}G_{3} + G_{2}G_{3}}\frac{{G_{1}}^{2}}{{C_{1}}^{2}}}$, $Q = \omega_{n}\frac{1}{(\frac{1}{C_{1}} + \frac{1}{C_{2}})G_{3}}$ 라는 정보를 얻었다.

설계조건에서 Q = 10, *C*1 = *C*2 = 0.1uF, *ωn* = 2*π* * 10*K* 이므로 이를 대입하면

**Active 2nd Order Band-pass Filter 회로도**

![HW7%204662f1548702442784321abd77f50897/image232.bmp](HW7%204662f1548702442784321abd77f50897/image232.bmp)

*R*1= 1.591K*Ω*,R*2= 83.76Ω*,R*3= 31.83KΩ*

을 얻을 수 있다.

**Active 2nd Order Band-pass Filter AC Sweep**

![HW7%204662f1548702442784321abd77f50897/image233.bmp](HW7%204662f1548702442784321abd77f50897/image233.bmp)

AC Sweep 결과에서 Center Frequency 가 1KHz 임을 확인할 수 있다.

4. 아래 주어진 설계사양에 부합되는 active filter를 설계하고, PSpice를 사용하여 동작 상태를 검증(AC sweep 해석)하시오.

설계사양 : Butterworth type 4차 low-pass filter

Cutoff frequency : 15 kHz

사용 capacitor : 0.1 uF

Gain in pass-band : 2

![HW7%204662f1548702442784321abd77f50897/image234.bmp](HW7%204662f1548702442784321abd77f50897/image234.bmp)

Butterworth Coefficients 테이블을 참조해 설계를 시작하였다.

![HW7%204662f1548702442784321abd77f50897/image235.bmp](HW7%204662f1548702442784321abd77f50897/image235.bmp)

위의 회로에서 $\frac{V_{o}}{V_{i}} = - \frac{\frac{R_{2}}{R_{1}}}{1 + {\omega_{n}}^{}C_{1}(R_{2} + R_{3} + \frac{R_{2}R_{3}}{R_{1}})s + {\omega_{n}}^{2}C_{1}C_{2}R_{2}R_{3}s^{2}} = - \frac{\text{Kb}_{1}}{s^{2} + a_{1}s + b_{1}}$ 의 전달함수를 가진다.

*b*1 = *ωn*2*C*1*C*2*R*2*R*3 이며 $a_{1} = \omega_{n}C_{1}(R_{2} + R_{3} + \frac{R_{2}R_{3}}{R_{1}})$ 이고, $K = \frac{R_{2}}{R_{1}}$ 이다.

공통된 항으로 묶어내면 *R*1, *R*2, *R*3 를 다음과 같이 얻을 수 있다.

$R_{2} = \frac{a_{1}C_{2} - \sqrt{{a_{1}}^{2}{C_{2}}^{2} - 4b_{1}C_{1}C_{2}(1 + K)}}{4\pi f_{c}C_{1}C_{2}}$

$R_{1} = \frac{R_{2}}{K}$

$R_{3} = \frac{b_{1}}{4\pi^{2}{f_{C}}^{2}C_{1}C_{2}R_{2}}$

설계 조건에서 Cutoff Frequenct 는 15KHz, K 는 2, 사용 커패시터는 0.1uF 이므로 *C*1 를 0.1uF 로 잡았다.

$C_{2} \geq C_{1}\frac{4b_{1}(1 + K)}{{a_{1}}^{2}}$ 을 반드시 만족해야 한다.

4th Order Low-pass Filter를 설계해야 하므로 Butterworth Coefficients 테이블에서

*a*1 = 1.8478, *a*2 = 0.7654, *b*1 = 1, *b*2 = 1 을 이용할 것이다.

처음 1단에서 사용할 Low-pass Filter부터 설계하면 다음과 같다.

*a*1 = 1.8478, *b*1 = 1 을 만족하면서 $C_{2} \geq C_{1}\frac{4b_{1}(1 + K)}{{a_{1}}^{2}}$ 범위 안에 드는 *C*2 는 0.3514uF 보다 커야하므로 편의상

*C*2 = 0.5uF 으로 지정하였다.

$R_{2} = \frac{a_{1}C_{2} - \sqrt{{a_{1}}^{2}{C_{2}}^{2} - 4b_{1}C_{1}C_{2}(1 + K)}}{4\pi f_{c}C_{1}C_{2}}$ 에 *fc* = 15KHz, *C*1 = 0.1uF, *C*2 = 0.5uF, *a*1 = 1.8478, *b*1 = 1 대입시

*R*2 = 44.59*Ω* 이다.

$R_{1} = \frac{R_{2}}{K}$ 에 *K* = 2 대입시 *R*1 = 22.3*Ω* 이다.

$R_{3} = \frac{b_{1}}{4\pi^{2}{f_{C}}^{2}C_{1}C_{2}R_{2}}$ 는 *R*3 = 50.5*Ω* 이 된다.

2단에서 사용할 Low-pass Filter부터 설계하면 다음과 같다.

*a*2 = 0.7654, *b*1 = 1 을 만족하면서 $C_{2} \geq C_{1}\frac{4b_{2}(1 + K)}{{a_{2}}^{2}}$ 범위 안에 드는 *C*2 는 2.04835uF 보다 커야하므로 편의상

*C*2 = 2.5uF 으로 지정하였다.

$R_{2} = \frac{a_{1}C_{2} - \sqrt{{a_{1}}^{2}{C_{2}}^{2} - 4b_{1}C_{1}C_{2}(1 + K)}}{4\pi f_{c}C_{1}C_{2}}$ 에 *fc* = 15KHz, *C*1 = 0.1uF, *C*2 = 2.5uF, *a*2 = 0.7654, *b*1 = 1 대입시

*R*2 = 22.35*Ω* 이다.

$R_{1} = \frac{R_{2}}{K}$ 에 *K* = 2 대입시 *R*1 = 11.67*Ω* 이다.

$R_{3} = \frac{b_{1}}{4\pi^{2}{f_{C}}^{2}C_{1}C_{2}R_{2}}$ 는

*R*3= 20.15Ω이 된다.

![HW7%204662f1548702442784321abd77f50897/image236.bmp](HW7%204662f1548702442784321abd77f50897/image236.bmp)

**Butterworth type 4th Order Low-pass Filter 회로도**

**Butterworth type 4th Order Low-pass Filter AC Sweep**

![HW7%204662f1548702442784321abd77f50897/image237.bmp](HW7%204662f1548702442784321abd77f50897/image237.bmp)

![HW7%204662f1548702442784321abd77f50897/image238.bmp](HW7%204662f1548702442784321abd77f50897/image238.bmp)

3dB 주파수가 15KHz 에는 가깝지만 정확하지는 않아서 커패시터를 줄여 주파수 범위를 넓혀줄 필요가 있었다.

![HW7%204662f1548702442784321abd77f50897/image239.bmp](HW7%204662f1548702442784321abd77f50897/image239.bmp)

![HW7%204662f1548702442784321abd77f50897/image240.bmp](HW7%204662f1548702442784321abd77f50897/image240.bmp)

2단 회로에서 저항과 커패시터를 줄여서 원하는 3dB 주파수를 얻었다.