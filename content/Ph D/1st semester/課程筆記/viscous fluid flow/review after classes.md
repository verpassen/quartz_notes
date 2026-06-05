review after classes

### Sep.10th 
cross product rule 不熟
- https://en.wikipedia.org/wiki/Vector_calculus_identities
- [vector calculus](https://math.libretexts.org/Bookshelves/Calculus/CLP-4_Vector_Calculus_(Feldman_Rechnitzer_and_Yeager)/04%3A_Integral_Theorems/4.01%3A_Gradient_Divergence_and_Curl)
- [Vector calculus lector - Vector Operators: Grad, Div and Curl](https://www.cse.iitb.ac.in/~cs749/spr2017/handouts/jem_graddivcurl.pdf)
- [Vector calculus Identities](https://advancedmath.org/Math/Cliff-GA/VectorCalculus/VectCalc_Identities3.pdf)


**no slip condition** : 
一種存在於固液邊界處的邊界條件。
**在固體邊界處，黏性流體的體積速度為零**
更準確的說 是兩者無相對運動, 相對速度為零
而且是在流體為黏性流體的條件下
流體流經物體表面 , 流體與物體的界面之間會有所謂的邊界層
在邊界層之類, 流體的速度梯度與所受的剪力或是drag force 有關,而這個阻力的大小又與黏滯係數相關

N-S Equation的推導會佔一大部分的時間，需要搞清楚

- 舉了兩三個例子來說明，為何需要考慮流體的黏性
	- D'Alembert Paradox
	- flow to flat plat
	- [drag crisis](https://zh.wikipedia.org/zh-tw/%E9%98%BB%E5%8A%9B%E5%8D%B1%E6%A9%9F)

## reading resources
- [NAVIER-STOKES SOLUTIONS, CYLINDRICAL COORDINATES](https://www.me.psu.edu/cimbala/me320/Lesson_Notes/Fluid_Mechanics_Lesson_11C.pdf)
- [N-S Equation cylinderical coord](https://demichie.github.io/NS_cylindrical/)

---

### Sep.17th 

- 推導 Continuity equation 
- 推導 N-S Eqs 
incompressible flow 
## ref 
- [推導的講義](https://ocw.nthu.edu.tw/ocw/upload/2/news/1.%20Differential%20Analysis%20of%20Fluid%20Flow.pdf)

---

### Oct. 03rd 

HW#1 Viscous Fluid flow 
Energy equation 
$\rho \large\frac{Dh}{Dt} = \small \nabla (k\nabla T) + \dot {q} + \Phi + \large\frac{D P}{Dt}$

why we can ignore the term $\frac{DP}{Dt}$ in incompressible fluid?

$h=e + \frac{P}{\rho}$
$\rightarrow \large{}\frac{dh}{dt}=\frac{de}{dt}+\frac{d}{dt}(\frac{P}{\rho})$
$\because$ the density of incompressible flow remain constant
$\rightarrow \large{}\frac{dh}{dt}=\frac{de}{dt}+\frac{1}{\rho}\frac{dP}{dt}$
$\rightarrow \rho \large{}\frac{dh}{dt}=\rho \frac{de}{dt}+\frac{dP}{dt} \small{}-(1)$
substitute eq. (1) into the energy equation and obtain 
$\rightarrow (\rho \large{}\frac{de}{dt}+\frac{dP}{dt}) = \small \nabla \cdot(k \nabla T) + \dot{q} + \Phi + \large{}\frac{dP}{dt}$

cancel out the $\frac{dP}{dt}$ term for both side
$\rightarrow \rho \large{}\frac{de}{dt}  = \small \nabla \cdot(k \nabla T) + \dot{q} + \Phi$

由於 incompressible flow 的特性 ( $\rho$ = constant)
讓原本能量方程式的dP/dt 這一項消失， 
簡化後的式子說明， enthalpy 與 內能 (de/dt ) 

for liquid, the $C_p \approx C_v$
其中 
$C_p$ 為 specific heat at constant pressure  等壓比熱
$C_v$ 為 specific heat at constant volume 等容比熱

----

Another thought
once we replace $$dh= C_p dT$$ , it imply the assumption that the pressure is constant . 

enthalpy h could be written as $$f(V,T)$$ (means function of the volume and temperature) or $$f(p,T)$$ (means the function of the pressure or Temperature) 

then we get the derivative of h become

$$dh= (\frac{\partial h}{\partial T})_P dT + (\frac{\partial h}{\partial p})_T dp$$

Since specific heat at constant pressure is defined as $$C_P = (\partial h/\partial T)_p$$

therefore , $dh = C_p dT$ . $\partial h / \partial p$ term is zero

這個說法有問題。
因為 當 $\partial h / \partial p \neq 0$ ，$dh = C_p dT$ 還是成立

----

### Oct. 10th 
Oct.10 

## Review cross product 
$scalar\ \phi,\psi\\ vector\ A, B$

Differential operator identities

$1. \nabla(\phi\psi)=\phi(\nabla\psi)+\psi(\nabla\phi)$

$2. \nabla \cdot(\phi A) =\phi \nabla \cdot A+A\cdot \nabla \phi$

$3. \nabla \times(\phi A) =\phi \nabla \times A+(\nabla \phi) \times A$

$4. \nabla \cdot (A \times B) = B(\nabla \times A) -A(\nabla \times B)$

$5. \nabla \times (A \times B) = A(\nabla \cdot B) -B(\nabla \cdot A)+ (B \cdot \nabla)A-(A\cdot \nabla)B$

$6. \nabla \times (\nabla \times A) = \nabla (\nabla \cdot A) - \nabla^2 A$

## dimensionless parameters 
- how to choose the dimensionless parameters for anaylsis ?

----

### Nov.20th 
- Gaussian integral 

- Gamma function 

- 如何決定一個情境的 nondimensional variables?
這節課在說明利用 nondimensional variable定義
把原本 non linear 的 pde 變成nondimensional 的 ODE
 
把ODE找出來後, 如何利用找到的解析方程式了解整個情境的狀況

- 探討流體的邊界層的厚度

----

### Dec.17th 

- 建議去修tensor 
tensor 可以表示的更簡潔

### Tensor 
- https://open.oregonstate.education/intermediate-fluid-mechanics/chapter/chapter-1-mathematical-tools/
