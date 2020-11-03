# HW1

**PSpice 연습 I**

**제출마감 일시 : 2020년 3월 28일 17:00**

**마감일시까지 제출한 수강생에 대해 출석 인정**

Two-stage capacitively coupled amplifier

![HW1%208f53db1b95cc44098fbc40801b447845/image1.jpeg](HW1%208f53db1b95cc44098fbc40801b447845/image1.jpeg)

Q2N2222, Driven by a 75 ohm, 50 uV, 1 kHz sine wave source and 18 kohm load.

1. I-V characteristic curves for Q2N2222 (DC sweep analysis)
2. Draw the circuit diagram (Getting the parts, Placing the parts, Connecting the parts, Changing the name of the parts, Changing the value of the part)
3. Operating point of each transistor (Bias point detail and Save bias point analysis)
4. Voltage gain of each stage and overall voltage gain (AC sweep analysis and Probe)
5. 3dB frequency with respect to C4 (Parametric analysis for 100 uF, 300 uF, 500 uF and Probe)
6. Transient analysis with 75 ohm, 50 uV, 1 kHz sine wave source (5 cycles and Probe)
7. Fourier analysis with 75 ohm, 50 uV, 1 kHz sine wave source (10cycles)

$v\left( 2\pi ft \right) = C_{0} + \ \sum_{n = 1}^{\infty}{C_{n} \bullet \sin\left( n \bullet 2\pi ft + \varnothing_{n} \right)}$

where C0 is DC component and Cn is nth harmonic component.

1. Check the output file



# HW1

HW1 : PSpice 연습 I

Pspice Version : OrCad 16.5

2017117876

김승현

Two-stage capacitively coupled amplifier

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image0.jpeg](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image0.jpeg)

Q2N2222, Driven by a 75 ohm, 50 uV, 1 kHz sine wave source and 18 kohm load.

A) I-V characteristic curves for Q2N2222 (DC sweep analysis)

I-V 특성을 구하기 위하여 Q2N2222를 PSpice 에 다음와 같이 배치하였다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image1.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image1.png)

V와 I는 계속해서 바뀌는 모습이 나와야 하므로 DC Sweep을 하였다.

Primary Sweep 으로 V1을 0V ~ 15V 까지 바꾸며 이때 증가폭은 0.1V 로 지정했다.

Secondary Sweep 으로 I1을 0mA ~ 10mA 까지 바꾸며 이때 증가폭은 1mA 로 지정했다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image2.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image2.png)

위와 같은 I-V 특성 그래프를 얻을 수 있었다. 이에 대한 Simulation Settings 는 다음과 같다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image3.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image3.png)

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image4.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image4.png)

B) Draw the circuit diagram (Getting the parts, Placing the parts, Connecting the parts, Changing the name of the parts, Changing the value of the part)

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image5.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image5.png)

C) Operating point of each transistor (Bias point detail and Save bias point analysis)

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image6.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image6.png)

Bias Point 로 해석하였고, 각 노드에서의 전압과 각 소자에서의 전류, 전력을 표시하였다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image7.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image7.png)

왼쪽 그림과 같이 Save Bias Point를 활성화 하고 Simulation 파일을 저장하였다.

이 바이어스 포인트에 대한 내용은 다음과 같다.

- ******************************************************************************PSpice Bias Point Save File from: **CIRCUIT: 2017117876_HW1.cir *TITLE: "** Profile: "SCHEMATIC1-2017117876_HW1" [ C:\SPB_DATA\..."*DATE OF RUN: 03/16/20 *TIME OF RUN: 23:01:28 *ANALYSIS: "Small Signal Bias Point (OP)" *TEMP: 27.0 *******************************************************************************.NODESET+ V(IN) = 0.0000000000+ V(OUT) = 0.0000000000+ V(VCC) = 15.0000000000+ V(N00203) = 2.8986147042+ V(N00246) = 2.2335031453+ V(N00271) = 7.6730624765+ V(N00599) = 2.8986147042+ V(N00647) = 2.2335031453+ V(N00667) = 7.6730624765+ V(N08260) = .8774367945+ V(N08264) = 5.0000000000+ V(N10334) = 0.0000000000*****************************************************************************

D) Voltage gain of each stage and overall voltage gain (AC sweep analysis and Probe)

AC Sweep을 하기위해 전압원을 VSIN 이 아닌, VAC를 사용하였다.

주파수별 전압 이득을 구하기 위해서 AC Sweep 해석을 하고, 1단과 2단 별도로 전압이득을 구했다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image8.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image8.png)

여기서 맨 위의 Plot 는 signal 50uV 이며, 두 번째 Plot 는 1단 Amp 의 Output 이다.

세 번째 Plot 는 2단 Amp 의 Output 이다. (Overall voltage gain)

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image9.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image9.png)

1KHz, 50uV 의 Sine wave 로 이득을 구하기 위해서 X Value를 1K로 두었다. 1단에서는 4.2657mV를 출력하고있고, 2단에서는 927.767mV를 출력하고 있다. 실제 입력은 50uV 였지만, 내부저항 75옴에서 전압강하 생겨 47.825uV 가 찍힌다. *Av*1 은 89.153 이며, *Av*2 는 217.49 이다. *Gv* = *Av*1*Av*2 이므로 19389.88이다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image10.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image10.png)

주파수의 변화를 위해 AC Sweep 설정은 왼쪽 그림처럼 하였다.

(시작 주파수 1, 끝 주파수는 100K)

E) -3dB frequency with respect to C4 (Parametric analysis for 100 uF, 300 uF, 500 uF and Probe)

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image11.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image11.png)

AC Sweep을 하기위해 전압원을 VSIN 이 아닌, VAC를 사용하였다.

C4 소자의 값이 바뀔 때 마다 출력전압이 바뀌는 것을 확인하기 위하여 Parameters를 추가하였다. 이 때 설정은 AC Sweep에서 Parametic Sweep을 이용해 Global parameter로 CVAR을 두었고, 100uF, 300uF, 500uF를 추가했다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image12.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image12.png)

여기서 파란색 선이 500uF 일 때, 보라색 선이 300uF 일 때, 초록색선이 100uF 일 때 이다.

3dB 주파수를 구하기 위하여 Measurement를 이용해 Cutoff_Highpass_3dB를 사용하였다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image13.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image13.png)

C4가 100uF 일 때 3dB 주파수가 163.21Hz 이다.

300uF 일 때는 140.70Hz, 500uF 일 때는 138.21Hz 이다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image14.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image14.png)

F) Transient analysis with 75 ohm, 50 uV, 1 kHz sine wave source (5 cycles and Probe)

주파수가 1kHz 인 sine wave를 5번 반복하기 위해서 1/1kHz = 1ms를 5번 곱해 Run to time을 5ms로 지정하였다. 그리고 선이 자연스럽게 이어지도록 하기 위해 10000 개 정도의 점을 찍도록 maximum step size 는 0.5u로 지정했다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image15.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image15.png)

첫 번째 plot 는 입력을 나타내고, 두 번째 plot 는 출력을 나타낸다.

peak를 구해보면 입력은 47.473uV, 출력은 934.337mV 이다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image16.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image16.png)

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image17.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image17.png)

G) Fourier analysis with 75 ohm, 50 uV, 1 kHz sine wave source (10cycles)

$v(2\pi\text{ft}) = C_{0} + \sum_{n = 1}^{\infty}C_{n}*\sin(n*2\pi\text{ft} + \varphi_{n})$

where C0 is DC component and Cn is nth harmonic component.

주파수가 1kHz 인 sine wave를 10번 반복하기 위해서 1/1kHz = 1ms를 10번 곱해 Run to time을 10ms로 지정하였다. 그리고 선이 자연스럽게 이어지도록 하기 위해 10000 개 정도의 점을 찍도록 maximum step size 는 1u로 지정했다.

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image18.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image18.png)

![HW1%2054ae4879579d4a108a8bf2716aeca5ae/image19.png](HW1%2054ae4879579d4a108a8bf2716aeca5ae/image19.png)

sine wave 가 1kHz 의 주파수 특성만을 가지고 있었기 때문에, 푸리에 변환에서 1KHz 주파수를 가지고 있음을 확인할 수 있다.

H) Check the output file

시뮬레이션 Output 파일은 다음과 같다.

- *** 03/23/20 18:35:47 ****** PSpice 16.5.0 (April 2011) ****** ID# 0 ********* Profile: "SCHEMATIC1-2017117876_HW1" [ C:\SPB_DATA\sch\2017117876_hw1-pspicefiles\schematic1\2017117876_hw1.sim ]*** CIRCUIT DESCRIPTION****************************************************************************** Creating circuit file "2017117876_HW1.cir"* WARNING: THIS AUTOMATICALLY GENERATED FILE MAY BE OVERWRITTEN BY SUBSEQUENT SIMULATIONSLibraries:Profile Libraries :Local Libraries :From [PSPICE NETLIST] section of C:\Cadence\SPB_16.5\tools\PSpice\PSpice.ini file:.lib "nom.lib"Analysis directives:.TRAN 0 10m 0 1u.PROBE V(alias(*)) I(alias(*)) W(alias(*)) D(alias(*)) NOISE(alias(*)).INC "..\SCHEMATIC1.net"*** INCLUDING SCHEMATIC1.net ****source 2017117876_HW1C_C1 IN N00203 10u TC=0,0R_R1 N00203 VCC 33k TC=0,0R_R2 0 N00203 8.2k TC=0,0Q_Q1 N00271 N00203 N00246 Q2N2222R_R3 N00271 VCC 3.3k TC=0,0R_R4 0 N00246 1k TC=0,0C_C2 0 N00246 100u TC=0,0C_C3 N00599 N00271 10u TC=0,0Q_Q2 N00667 N00599 N00647 Q2N2222R_R8 0 N00647 1k TC=0,0C_C4 0 N00647 100u TC=0,0R_R6 0 N00599 8.2k TC=0,0R_R5 N00599 VCC 33k TC=0,0C_C5 OUT N00667 10u TC=0,0R_R7 N00667 VCC 3.3k TC=0,0V_V1 VCC 0 15VR_R9 0 OUT 18k TC=0,0V_V3 N08264 0 5VQ_Q3 N08264 N08260 0 Q2N2222I_I1 0 N08260 DC 5mAR_R10 N10334 IN 75 TC=0,0V_V4 N10334 0 AC 1+SIN 0 50u 1k 0 0 0.PARAM cvar=100u*** RESUMING 2017117876_HW1.cir ****.END*** 03/23/20 18:35:47 ****** PSpice 16.5.0 (April 2011) ****** ID# 0 ********* Profile: "SCHEMATIC1-2017117876_HW1" [ C:\SPB_DATA\sch\2017117876_hw1-pspicefiles\schematic1\2017117876_hw1.sim ]*** BJT MODEL PARAMETERS*****************************************************************************Q2N2222NPNLEVEL 1IS 14.340000E-15BF 255.9NF 1VAF 74.03IKF .2847ISE 14.340000E-15NE 1.307BR 6.092NR 1ISS 0RB 10RE 0RC 1CJE 22.010000E-12VJE .75MJE .377CJC 7.306000E-12VJC .75MJC .3416XCJC 1CJS 0VJS .75TF 411.100000E-12XTF 3VTF 1.7ITF .6TR 46.910000E-09XTB 1.5KF 0AF 1CN 2.42D .87*** 03/23/20 18:35:47 ****** PSpice 16.5.0 (April 2011) ****** ID# 0 ********* Profile: "SCHEMATIC1-2017117876_HW1" [ C:\SPB_DATA\sch\2017117876_hw1-pspicefiles\schematic1\2017117876_hw1.sim ]*** INITIAL TRANSIENT SOLUTION TEMPERATURE = 27.000 DEG C*****************************************************************************NODE VOLTAGE NODE VOLTAGE NODE VOLTAGE NODE VOLTAGE( IN) 0.0000 ( OUT) 0.0000 ( VCC) 15.0000 (N00203) 2.8986(N00246) 2.2335 (N00271) 7.6731 (N00599) 2.8986 (N00647) 2.2335(N00667) 7.6731 (N08260) .8774 (N08264) 5.0000 (N10334) 0.0000VOLTAGE SOURCE CURRENTSNAME CURRENTV_V1 -5.174E-03V_V3 -4.628E-01V_V4 0.000E+00TOTAL POWER DISSIPATION 2.39E+00 WATTSJOB CONCLUDED*** 03/23/20 18:35:47 ****** PSpice 16.5.0 (April 2011) ****** ID# 0 ********* Profile: "SCHEMATIC1-2017117876_HW1" [ C:\SPB_DATA\sch\2017117876_hw1-pspicefiles\schematic1\2017117876_hw1.sim ]*** JOB STATISTICS SUMMARY*****************************************************************************Total job time (using Solver 1) = .47