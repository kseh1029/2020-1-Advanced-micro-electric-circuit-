# HW2

**전자회로론(2020년 1학기)**

**개인별 설계과제 #2**

**제출일자 : 2020년 4월 11일(토) 17:00까지**

**1. 아래 주어진 설계사양에 부합되는 cascade amplifier를 설계하시오.**

**설계사양 : 회로구조 : CC-CE Amplifier**

**사용Tr. : Q2N2222**

**전압이득 : 40 dB** ± **10%**

**Lower half power frequency : 20 Hz** ± **10%**

**Upperer half power frequency : 20 KHz** ± **10%**

**Load resistance : 5 Kohm**

**Supply Voltage : 20 VDC**

**2. 문제 1에서 설계된 증폭회로의 동작특성을 Spice를 사용하여 검증하고, 문제 1의 설계사양과 비교 분석하시오.**

**동작특성 : 입력저항, 출력저항,**

**전압이득, Half power frequencies,**

**Bandwidth, Unity gain frequency/bandwidth,**

**Power consumption**

**3. 입력신호가** 1 • sin (2*π* • 103*t*) **mV 일 경우, 출력신호를 plot하고 위상차를 구하시오.**

**4. 문제 1에서 설계된 증폭회로의 Impulse response를 Spice를 사용하여 구하시오.**

**5. 문제 1에서 설계된 증폭회로의 step response를 Spice를 사용하여 구하시오.**

**(주의사항 : 설계과정 및 분석을 요함.)**

# HW2

HW2 : 개인별 설계과제 #2

Pspice Version : OrCad 16.5

2017117876

김승현

1. 아래 주어진 설계사양에 부합되는 cascade amplifier를 설계하시오.

**설계사양 : 회로구조 : CC-CE Amplifier**

**사용Tr. : Q2N2222**

**전압이득 : 40 dB** ± **10%**

**Lower half power frequency : 20 Hz** ± **10%**

**Upperer half power frequency : 20 KHz** ± **10%**

**Load resistance : 5 Kohm**

**Supply Voltage : 20 VDC**

Common Collector 와 Common Emitter 가 Two-Stage 로 연결된 Cascade Amplifier를 설계하기 전 각 증폭기의 역할에 대해 알 필요가 있다.

Common Emitter 의 경우 일반적으로 입력저항은 (*β* + 1)*re* 로 낮고 출력저항은 *RC* 로 나오게 된다. 이때 증폭률은 *Av* = − *gm*(*RC* ∥ *RL*) 가 된다.

Common Collector 의 경우 Emitter Follower 라고도 불리며, 전압이득은 $\frac{R_{L}}{R_{L} + r_{e}}$이라 1에 가깝고 출력저항이 *re* 로 매우 작게 나온다. 입력저항은 (*β* + 1)(*re* + *RL*) 로 나오게 된다.

일반적으로 Common Emitter를 먼저 사용하고 Common Collector를 사용해 출력저항을 낮춰서 오디오나 기타 디바이스에 사용하기 적합하도록 낮은 저항을 만들어주는 것이 목적인데, 본 과제에서는 CC-CE Amp를 설계하라고 지시하여 Common Collector를 1 Stage 에 달아 최종 출력저항은 크게 나오게 될 것이다.

**① Common Emitter 설계**

Q2N2222 BJT를 사용하므로 해당 Datasheet를 보고 베타 값을 얻어야 한다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image20.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image20.bmp)

Datasheet에서 *IC* 가 1mA, *V*CE 가 10V 일 때 베타가 최소 50이 나옴을 확인할 수 있다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image21.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image21.bmp)

기본적으로 Common Emitter 는 왼쪽처럼 틀을 잡아서 시작할 수 있다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image22.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image22.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image23.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image23.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image24.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image24.bmp)

설계하고 싶은 사양에서 *V*CC = 20*V* 이고, 전압이득은 40dB 이므로 *Av* = − 100 으로 설계해야 한다. 또한, *RL* = 5*kΩ* 이다.

*Av* = − *gm*(*RC* ∥ *RL*) 이 되며 *IC* = 1mA 일때로 가정하고 설계를 진행하면

$g_{m} = \frac{I_{C}}{V_{T}}$ 로 $g_{m} = \frac{1\text{mA}}{25\text{mV}}$ 이며, $r_{e} = \frac{\alpha}{g_{m}} \simeq \frac{1}{g_{m}} = 25\Omega$ 이 된다.

*Av* 가 –100 이 되기 위해선 (*RC* ∥ *RL*) 가 2500이 되어야 하고,

*RL* = 5*kΩ* 으로 설계사양에 명시되어 있으므로, *RC* = 5*kΩ* 으로 설정할 수 있다.

*V*CE = 10*V* 가 걸릴것이며, 이에 따라 *VE* 에는 5V 가 걸려야 하므로, *RE* 는 5*kΩ* 이 되며, *VB* 는 *V*BE = 0.7*V* 의 전압강하 위에 있으므로 5.7V 가 된다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image25.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image25.bmp)

*R*

BB

= 0.1

*β*

*R*

*E*

로 두고 있으며,

*R*

BB

=

*R*

1

∥

*R*

2

이고

$V_{B} = \frac{R_{2}}{R_{1} + R_{2}}V_{\text{CC}}$ 이므로 *R*BB = 0.1 * 50 * 5*k* = 25*kΩ*

$\frac{R_{1}}{R_{1} + R_{2}} \times 20V = 5.7V$ 을 연립하게 되면 *R*1 = 87.72*kΩ*, *R*2 = 34.96*kΩ*을

얻을 수 있다.

그리고, 저주파 반전력주파수가 20Hz, 고주파 반전력주파수가 20kHz 이므로 주파수 특성에 맞게 커패시터를 설정해줘야 한다.

저주파 3dB 주파수의 경우 *CE* 에 직접적으로 영향을 받게 된다. 보통 *C*1 과 *C*2 는 10% 씩 차지하고, *CE* 는 80%를 차지하도록 설계한다.

*C*1 을 구하기 위해 *C*2 와 *CE* 를 쇼트시키고 *C*1 에서 바라보면 다음과 같다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image26.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image26.bmp)

*r*e*는 25Ω*이므로 등가저항을 구하면 1.213*kΩ* 을 구할수 있다.

$2\pi f = \frac{1}{\text{RC}}$ 을 만족해야 하고, 이때 3dB 주파수의 10%를 *C*1 에게 분담을 시키면 $2\pi \times 20\text{Hz} \times 0.1 = \frac{1}{1.213k\Omega \times C_{1}}$ 이므로 *C*1 = 65.6uF 이 된다.

*CE* 를 구하기 위해 *C*1 과 *C*2 를 쇼트시키고 *CE* 에서 바라보면 다음과 같다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image27.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image27.bmp)

$\frac{0}{50 + 1} + 25\Omega$ 과 5k*Ω*은 병렬이므로 등가저항을 구하면 24.87Ω*이다. $2\pi f = \frac{1}{\text{RC}}$ 을 만족해야 하고, 이때 3dB 주파수를 80%를 분담하는게 일반적이지만, 100% 정확하게 20Hz에서 3dB가 되도록 설정하였다.

$2\pi \times 20\text{Hz} = \frac{1}{24.87\Omega \times C_{E}}$ 이므로 *CE* = 309.974uF 이 된다.

*C*2 를 구하기 위해 *C*1 과 *CE* 를 쇼트시키고 *C*2 에서 바라보면 다음과 같다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image28.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image28.bmp)

$2\pi f = \frac{1}{\text{RC}}$ 을 만족해야 하고, 이때 3dB 주파수의 10%를

C2에게 분담을 시키면 $2\pi \times 20\text{Hz} \times 0.1 = \frac{1}{10k\Omega \times C_{2}}$ 이므로 C2= 7.957uF 이 된다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image29.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image29.bmp)

R*1과*RC 사이에 커패시터를 추가함으로서 제한을 둘 수 있다.

20kHz 로 설정을 해야하므로, $2\pi f = \frac{1}{\text{RC}}$을 만족해야 하고,

$2\pi f = \frac{1}{(R_{C} \parallel R_{L})C_{F}}$ 이므로 *CF* = 3.181nF 이다.

② **Common Collector 설계**

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image30.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image30.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image31.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image31.bmp)

기본적으로 Common Collector 는 왼쪽처럼 틀을 잡아서 시작할 수 있다.

$A_{v} = \frac{R_{E}}{r_{e} + R_{E}}$ 이므로 거의 신경쓰지 않고도 1이 나올 것이다.

*IC* = 1mA 일때로 가정하고 설계를 진행하면

*V*CE = 10*V* 가 걸릴것이며, 이에 따라 *VE* 에는 10V 가 걸려야 하므로, *RE* 는 10*kΩ* 이 되며, *VB* 는 *V*BE = 0.7*V* 의 전압강하 위에 있으므로 10.7V 가 된다.

일반적으로 *R*BB = 0.1 *βRE* 로 두고 있으며, *R*BB = *R*1 ∥ *R*2 이고

$V_{B} = \frac{R_{2}}{R_{1} + R_{2}}V_{\text{CC}}$ 이므로 *R*BB = 0.1 * 50 * 10*k* = 50*kΩ*

$\frac{R_{1}}{R_{1} + R_{2}} \times 20V = 10.7V$ 을 연립하게 되면 *R*1 = 93.45*kΩ*, *R*2 = 107.52*kΩ*을

얻을 수 있다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image32.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image32.bmp)C1에 직접적인 영향을 받진 않지만 20Hz 의 10%를 차지하도록 커패시터의 값을 부여하였다. 등가저항은 45.46*kΩ* 이다.

$2\pi \times 20\text{Hz} \times 0.1 = \frac{1}{45.46k\Omega \times C_{1}}$ 에 의해 *C*1 = 1.75nF 이다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image33.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image33.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image34.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image34.bmp)

첫 번째 Plot 은 *R*sig 위 전압을 AC Sweep 으로 나타낸 것이다.

두 번째 Plot 은 Common Collector 를 지나고 난 *V*out 이다.

세 번째 Plot 은 Common Emitter 까지 지나고 난 *V*out 이다.

1mV 가 인가되고, 결과는 90mV 가 출력이 되었다.

설계를 할 때에는 100mV를 출력하는 것을 목적으로 값들을 지정하였지만, 10% 정도의 차이가 있었다.

이를 정확하게 만들기 위해서는 *RC* 을 약간 올릴 필요성이 보였다.

저주파 3dB 는 19.75Hz, 고주파 3dB는 10.29kHz 으로 예상한 것 보다 절반으로 나왔다.

이는 설계의 편의상 *C*be 를 달아주지 않고, *C*bc 로만 해결하려고 한 것에서 발생한 것으로 예상된다.

그래서 *RC* 를 6.4*kΩ* 으로 올리고, 이에 맞게 *Cf* 를 재조절 하여 새로운 Plot 결과를 얻었다.

(조절 과정 : $C_{f} = \frac{1}{2\pi \times 20\text{kHz} \times (R_{L} \parallel R_{C})}$ 으로 2.835nF을 구하였다.)

그리고, 아까의 설계값과는 달리 High Frequency 가 2배 작게 나왔으므로 2.835nF를 2로 나눈 1.417nF를 적용하였다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image35.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image35.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image36.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image36.bmp)

수정을 하고 나니 저주파 3dB 주파수는 19.72Hz, 고주파 3dB 주파수는는 20.56kHz 로 원하는 범위 내의 주파수를 얻었다.

또한, 출력전압도 100mV 가 되었고, 44.24mW 의 전력소모를 가진다.

Bandwidth 는 이 둘의 차인 20540.3 Hz 이다.

Unity gain Frequency 와 Bandwidth 는 다음과 같다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image37.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image37.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image38.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image38.bmp)

입력저항과 출력저항은 Bias Point Analysis 로 구하였다.

- *** SMALL-SIGNAL CHARACTERISTICSV(OUT)/V_V1 = 0.000E+00**INPUT RESISTANCE AT V_V1 = 1.000E+20OUTPUT RESISTANCE AT V(OUT) = 5.000E+03***** 04/05/20 02:37:32 ****** PSpice 16.5.0 (April 2011) ****** ID# 0 ********* Profile: "SCHEMATIC1-2017117876_HW2" [ C:\SPB_DATA\sch\2017117876_hw2-pspicefiles\schematic1\2017117876_hw2.sim ]*** DC SENSITIVITY ANALYSIS TEMPERATURE = 27.000 DEG C*****************************************************************************

3. 입력신호가 1 • sin (2*π* • 103*t*) mV 일 경우, 출력신호를 plot하고 위상차를 구하시오.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image39.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image39.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image40.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image40.bmp)

Vsin 입력에 대한 결과를 얻기 위하여 Time Domain Analysis를 사용하였다.

위 Plot 는 Vin 이고, 아래 Plot 는 Vout 이다.

위상차는 발생하지 않았다.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image41.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image41.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image42.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image42.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image43.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image43.bmp)

Vpulse 입력에 대한 결과를 얻기 위하여 Time Domain Analysis를 사용하였다.

위 Plot 는 Vin 이고, 아래 Plot 는 Vout 이다.

Impulse Response를 구하기 위해 최대한 Rising Time과 Falling Time 은 짧고, 최대한 높은 전압까지 올라가도록 하였다.

5. 문제 1에서 설계된 증폭회로의 step response를 Spice를 사용하여 구하시오.

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image45.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image45.bmp)

![HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image46.bmp](HW2%20f4eef3ba3a754a08ae1f76a2865eddc6/image46.bmp)

Vpulse 입력에 대한 결과를 얻기 위하여 Time Domain Analysis를 사용하였다.

위 Plot 는 Vin 이고, 아래 Plot 는 Vout 이다.

이때 peak 전압은 Unit step function처럼 작동하기 위해 1V로 지정하였다.