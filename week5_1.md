## 상태공간방정식
state variables : 상태변수  
상태변수는 문제를 푸는 체계가 필요하여 만들어짐  
Input과 Output 사이 시스템 안에서 상태변수를 지정하고 이를 중심으로 문제를 풀 수 있다.  

Output : Input과 state로 도출할 수 있음

### Ex1
문제 : 벽 사이에 물체가 끼어있고 위에 스프링으로 연결되어 있음  
  
미분방정식  

$$M\frac{d^2y(t)}{dt^2} + b\frac{dy(t)}{dt}+ky(t) = r(t)$$  

상태 변수 설정

$$x_1(t)=y(t), x_2(t)=\frac{dy(t)}{dt}$$  

$x_1(t)$는 변위, $x_2(t)$는 속도(변위의 미분값)

$$\frac{dx_1(t)}{dt}=x_2(t)$$

$$\frac{dx_2(t)}{dt}=\frac{-b}{M}x_2(t)-\frac{k}{M}x_1(t)+\frac{1}{M}r(t)$$

상태변수 설정을 통해 2차 미분방정식이 연립 1차 미분 방정식으로 변한 것을 볼 수 있다.

* state는 마음대로 설정이 가능하지만 같은 변수를 state로 설정하지 않도록 유의해야함.

### Ex_2
상황 : 전류원 $u(t)$ L과 R이 직렬로 연결되어 있고 병렬 부하로 커패시터 C가 접속되어 있음



미분방정식
키르히호프의 법칙을 이용해 미분방정식을 세우면

$$x_1(t)=v_c(t), x_2(t) = i_L(t)$$

1.
$$u(t) = C\frac{dx_1(t)}{dt}+x_2(t)$$
$$\frac{dx_1(t)}{dt} = \frac{1}{C}[-x_2(t)+u(t)]$$

2.
$$L\frac{dx_2(t)}{dt}+Rx_2(t)-x_1(t)=0$$
$$\frac{dx_2(t)}{dt} = \frac{1}{L}[x_1(t) - Rx_2(t)]$$

$$y(t) = Rx_2(t)$$

## 상태 미분 방정식 - 미분 방정식 유도

$$x^{'}(t)=ax(t)+bu(t)$$
$$sX(s)-x(0) = aX(s) + bU(s)$$
$$(s-a)X(s) = x(0) + bU(s)$$
$$X(s) = \frac{1}{s-a}x(0)+\frac{1}{s-a}bU(s)$$
$$x(t) = e^{at}x(0) + \int{e^{a(t-\tau)}}bu(\tau)d\tau$$
$$x(t) = \Phi(t)x(t)+\int{\Phi(t-\tau)}bU(\tau)dt$$


## 상태 벡터와 상태 공간 방정식

state를 설정해서 다차미분방정식을 1차 미분 방청식으로 바꾼다.

$$x(t) = \begin{pmatrix}
x_1(t) \\
x_2(t) \\
.\\
.\\
.\\
\end{pmatrix}
$$

state differential equation
$$x^{'}(t) = Ax(t) + Bu(t)$$

output equation
$$y(t) = Cx(t) + Du(t)$$

state transition matrix  
1차  
$$x(t) = e^{at}x(0) + \int{e^a(t-\tau)}bu(\tau)dt$$

n차  
$$x(t) = exp(At)x(0) + \int{exp[A(t-\tau)]}Bu(\tau)d\tau$$

$$x(s) = [sI-A]^{-1}x(0) + [sI-A]^{-1}BU(s)$$
$$\Phi(s) = [sI-A]^{-1}$$
$$\Phi(t) = \mathcal{L}^{-1}[\Phi(t)]$$
$$x(t) = \Phi(t)x(0)+\int{\Phi(t-\tau)}bu(\tau)d\tau$$

Ex3

상황 : 벽에 스프링과 뎀퍼가 카트2와 연결되어 있고 카트1이 그 옆에 카트2와 연결되어 있음  

미분 방정식  
$$M_1p^{"}(t) = u(t)-b_1(t)[p^{'}(t)-q^{'}(t)]-k1[p(t)-q(t)]$$  

$$M_2q^{"}(t) = b1[p^{'}(t)-q^{'}(t)]+k_1[p(t)-q(t)]-b_2q^{'}(t)-k_2q(t)$$

$$x(t) = \begin{pmatrix}
x_1(t) \\
x_2(t) \\
x_3(t) \\
x_4(t) \\
\end{pmatrix}
= \begin{pmatrix}
p(t) \\
q(t) \\
p^{'}(t) \\
q^{'}(t) \\
\end{pmatrix}
$$
$$
x^{'}(t) = \begin{bmatrix}
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
-\frac{k_1}{M_1} & \frac{k_1}{M_1} & -\frac{b_1}{M_1} & \frac{b_1}{M_1} \\
\frac{k_1}{M_2} & -\frac{k_1+k_2}{M_2} & \frac{b_1}{M_2} & -\frac{b_1 + b_2}{M_2} \\
\end{bmatrix}
x(t)
+ 
\begin{bmatrix}
0 \\
0 \\
\frac{1}{M_1} \\
0 \\
\end{bmatrix}
u(t)$$
