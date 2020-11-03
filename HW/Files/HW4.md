# HW4

**전자회로설계(2020년 1학기) 개인별 설계과제 #4**

**제출일자 : 2020년 5월 9일(토) 17:00까지**

1. PSpice에서 사용되는 uA741 op amp macromodel(Part name : ua741)의 electrical characteristics 조사하시오. (단, supply voltage=±15 V)

Input offset voltage

Input offset current

Input bias current

Input resistance

Output resistance

Output short circuit current

Supply current

Power consumption

Input voltage range for a voltage follower

Output voltage swing for a voltage follower

Common mode rejection ratio

Open loop voltage gain as a function of frequency

Open loop phase response as a function of frequency

Unity gain bandwidth

Gain/phase margin

Slew rate

2. Find the slew rate-limited cutoff frequency for a voltage follower circuit using a 741 op-amp if the sine wave output is to be 5 V.

3. Find the distortion-free output amplitude of the sinusoidal output voltage at the unity-gain frequency.

HW4 : 개인별 설계과제 #4

Pspice Version : OrCad 17.4

2017117876

김승현

**1. PSpice에서 사용되는 uA741 op amp macromodel(Part name : ua741)의 electrical characteristics 조사하시오. (단, supply voltage=±15 V)**

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image92.jpeg](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image92.jpeg)

PSpice를 이용해 electrical characterstics를 조사하기 전에 datasheet를 먼저 확인하였다.

먼저 확인해 볼 전압은 input offset voltage 인데, datasheet 에서는 Typically 1mV 정도로 나와 있다.

여기서 한가지 유심히 볼게 있는데 min 값이 표시되어 있지 않다.

이는 ideal 한 Op-Amp 의 경우 모두 존재하지 않는 값이고 낮으면 낮을수록 좋기 때문이다.

[Untitled](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/Untitled%20Database%205ed1efd70b5546008077fd58fcb8f058.csv)

**Input offset voltage :** 19.337uV

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image93.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image93.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image94.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image94.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image95.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image95.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image96.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image96.bmp)

위와 같이 V3 에 대해 DC Sweep을 하여 *V*out 이 0V가 되는 V3를 구하면 *V*OS 를 얻을 수 있다.

datasheet 와는 차이가 있었지만 실제로는 19.337uV 가 확인되었다.

이 외의 방법으로 Series-shunt feedback amplifier를 구성한 후 출력전압을 측정으로 *V*OS 를 얻을 수 있다.

하지만, 이 방법은 출력전압이 0이 되는 differential input voltage를 구분하기 어렵다.

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image97.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image97.bmp)

다른 방법으로 non-inverse amplifier를 구성하여서 *V*OS 를 얻으려 했다.

Pspice에서 제공하는 uA741 part 는 Offset-free op amp 가 아니라서 구할 수 없다.

그리고, *R*1, *R*2 의 저항비를 같게 맞춤에도 출력 전압에 오차가 생긴다.

이 이유는 input bias current 때문이다.

*R*1, *R*2 에 흐르는 전류가 클수록 input bias current 의 영향을 최소화 할 수 있다.

**Input offset current :** 0.038nA

**Input bias current :** 79.742nA

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image98.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image98.bmp)

Input offset current 는 *I*OS = ∣ *IB*1 − *IB*2∣ 이며 Input bais current 는 $I_{B} = \frac{I_{B1} + I_{B2}}{2}$ 이다.

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image99.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image99.bmp)

1kΩ 씩 inverting 회로에서 바이어스 전류를 구하였지만, 내부의 BJT base 전류에 기인하므로 어떤 저항이 와도 같은 결과가 나올 것이다.

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image100.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image100.bmp)

*IB*1 = 79.761nA, *IB*2 = 79.723nA 이므로 *I*OS = 0.038nA, *IB* = 79.742nA 이다.

**Input resistance :** 996.3*kΩ*

**Output resistance :** 152*Ω*

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image101.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image101.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image102.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image102.bmp)

**Output short circuit current :** 25.29mA

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image103.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image103.bmp)

**Supply current :** 1.667mA

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image104.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image104.bmp)

**Power consumption :** 50.01mW

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image105.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image105.bmp)

**Input voltage range for a voltage follower : 실제로는 Input을 넣는데는 제한이 없지만 앞 단에서 ua741을 걸치고 나온 출력이라면, 마찬가지로** 14.816*V* **까지 밖에 입력하지 못할 것이다.**

**Output voltage swing for a voltage follower :** 14.816*V*

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image106.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image106.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image107.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image107.bmp)

**Common mode rejection ratio :** 90dB

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image108.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image108.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image109.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image109.bmp)

**Open loop voltage gain as a function of frequency**

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image110.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image110.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image111.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image111.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image112.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image112.bmp)

**Open loop phase response as a function of frequency**

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image113.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image113.bmp)

**Unity gain bandwidth :** 888.083KHz

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image114.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image114.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image115.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image115.bmp)

**Gain/phase margin :** 54.245dB / 62.801∘

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image116.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image116.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image117.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image117.bmp)

**0dB 일 때 -117.199도 이므로, -180도와 62.801도 차이가 난다. 따라서 PM는 62.801 도 이다.**

- **180도 일 때 –54.245dB 이므로 GM는 54.245dB 이다.**

**Slew rate :** 0.4 *V*/us

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image118.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image118.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image119.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image119.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image120.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image120.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image121.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image121.bmp)

$\frac{V_{\text{out}\, 90\%} - V_{\text{out}\, 10\%}}{t_{90\%} - t_{10\%}}$ 로 구할 수 있다.

$\frac{0.9V - 0.1V}{15.002\text{ms} - 15.000m} = \frac{0.8V}{0.002\text{ms}} = \frac{0.8V}{2\text{us}} = 0.4\lbrack V/\text{us}\rbrack$ 이다.

**2. Find the slew rate-limited cutoff frequency for a voltage follower circuit using a 741 op-amp if the sine wave output is to be 5 V.**

slew rate의 경우 SR ≥ 2*π*fV*p*(out) 을 만족해야 한다. slew rate를 앞선 문제에서 0.277 *V*/uS 라고 구했다.

따라서, 0.4*V*/uS = 2*πf* × 5 를 만족하는 주파수를 찾아보면 12.738KHz 가 나오게 된다.

datasheet 에 적힌 slew rate를 그대로 적용하면 0.5*V*/uS = 2*πf* × 5 를 만족하는 주파수는 15.9235KHz 이다.

8KHz, 20KHz 인 VSIN을 입력하여 어떤 차이를 내는지 확인해봤다.

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image122.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image122.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image123.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image123.bmp)

첫 번째 plot 는 8KHz 일 때이며, 두 번째 plot는 20KHz 일 때이다.

cutoff frequency 보다 낮은 주파수는 입력 파형을 그대로 잘 따라 간다.

이보다 높은 주파수에서는 입력 파형을 잘 따라가지 못하는 모습이다.

**3. Find the distortion-free output amplitude of the sinusoidal output voltage at the unity-gain frequency.**

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image124.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image124.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image125.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image125.bmp)

unity-gain frequency 는 888.121KHz 이다.

이 주파수 일 때 출력전압이 왜곡이 없는 사인파의 출력 Amplitude를 구하여야 한다.

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image126.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image126.bmp)

SR ≥ 2*π*fV*p*(out) 를 만족하는 *Vp*(out) 을 찾으면 된다.

datasheet 에 적힌 slew rate를 그대로 적용하면 0.5*V*/uS = 2*π* × 888.121KHz × *Vp*(out)

*Vp*(out) = 89.64mV 를 구할 수 있다.

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image127.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image127.bmp)

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image128.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image128.bmp)

89.64mV 를 입력으로 넣었을 때의 출력 plot 이다.

실제로는 주파수가 높아 입력이 그대로 출력으로는 나오지 않고 있다.

출력이 78.14mV 가 나오면서 사인파의 왜곡이 없음을 확인할 수 있다.

![HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image129.bmp](HW4%20e52c1bee62b84d59b1ab749ee9d4c39a/image129.bmp)

250mV를 입력으로 넣었을 때의 출력 plot 이다.

입력과 출력의 사인파 모양만을 비교하기 위해 입력과 출력전압이 비슷하게 Trace 할 때에는 V(in) / 1.5 로 하였다. 106.5mV 의 출력을 나타내고 있고 사인파의 peak 부분들이 찌그러져있다.

실제로 출력이 89.64mV 가 넘으니 왜곡이 슬슬 생기기 시작함을 볼 수 있다.