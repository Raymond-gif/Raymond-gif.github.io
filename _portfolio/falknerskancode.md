---
title: "Falkner-Skan MATLAB Solution: Finite Difference Method"
excerpt: "I walk you through my MATLAB solution to the Falkner-Skan differential equation."
collection: portfolio
author_profile: false
layout: single
image: /images/velprof.png
caption: "Photo credit: myself"
order: 2

---

<div style="background: #f5f5f5; border-left: 5px solid #007acc; padding: 1rem; border-radius: 8px; margin: 1.5rem 0;">
  <p style="margin: 0; font-size: 1.1rem;">
    📌 <strong>This is an addendum to my previous article.</strong>
    <a href="/portfolio/numericalmethodsBLeqn" 
       style="
         display: inline-block;
         background: linear-gradient(135deg, #4a90e2, #357abd);
         color: white;
         padding: 0.4rem 0.8rem;
         margin-left: 0.5rem;
         text-decoration: none;
         border-radius: 5px;
         font-weight: bold;
         transition: background 0.3s ease, transform 0.2s ease;
       "
       onmouseover="this.style.background='linear-gradient(135deg, #5aa0f2, #468acc)'; this.style.transform='translateY(-3px)';"
       onmouseout="this.style.background='linear-gradient(135deg, #4a90e2, #357abd)'; this.style.transform='translateY(0)';">
      Click here
    </a>
  </p>
</div>

<div class="equation-box">
  <h3>Falkner-Skan Differential Equation</h3>
  <div>

The third order nonlinear differential equation to be solved is, 

$$\begin{equation}
    f''' +f f'' + \beta (1-f'^{ \, 2}) = 0
    \label{thirdordernonlineareqn1}
\end{equation}$$

Boundary Conditions: 

$$\left\{
\begin{aligned}
    f(0) &= 0 \\ 
    f'(0) &= 0 \\
    f'(\eta \to \infty) &= 1
\end{aligned} \right\} \notag
$$
</div>
</div>

We seek to transform this differential equation into a form that is better suited for our purposes. Making the following transformation,

$$\xi = e^{-\eta} \notag$$

Using chain rule,

$$\begin{align*}
    \dfrac{d}{d \eta} &= -\xi \dfrac{d}{d \xi} \\ 
    \dfrac{d^2}{d \eta^2} &= \xi \dfrac{d}{d \xi} + \xi^2 \dfrac{d^2}{d \xi^2} \\ 
    \dfrac{d^3}{d \eta^3} &= -\xi \dfrac{d}{d \xi} - 3\xi^2 \dfrac{d^2}{d \xi^2} - \xi^3 \dfrac{d^3}{d \xi^3}
\end{align*}$$

Eq. \ref{thirdordernonlineareqn1} transforms to, 

$$\begin{equation}
    \xi^3 \dfrac{d^3 f}{d \xi^3}+ 3 \xi^2 \dfrac{d^2 f}{d \xi^2}+\xi \dfrac{df}{d\xi} - f\left(\xi \dfrac{df}{d\xi}+\xi^2 \dfrac{d^2 f}{d \xi^2} \right) - \beta \left[ 1 -\xi^2 \left( \dfrac{df}{d \xi} \right)^2 \right]=0
    \label{thirdordernonlineareqn2}
\end{equation}$$

Let's make another transformation, \\(g = \eta - f \\)

Differentiating with respect to \\( \xi \\),

$$\begin{align*}
    f &= -\ln\xi -g \\
    \dfrac{df}{d \xi} &= -\dfrac{1}{\xi}-\dfrac{dg}{d \xi} \\
    \dfrac{d^2 f}{d \xi^2} &= \dfrac{1}{\xi^2}-\dfrac{d^2 g}{d\xi^2} \\
    \dfrac{d^3 f}{d \xi^3} &= -\dfrac{2}{\xi^3}-\dfrac{d^3 g}{d \xi^3}
\end{align*}$$

Substituting the above chain rule equations into Eq. \ref{thirdordernonlineareqn2}, we obtain, 

$$\begin{equation}
    g''' + \dfrac{3+\ln \xi + g}{\xi} g'' + \dfrac{g+\ln \xi +1-2\beta}{\xi^2} g' - \dfrac{\beta}{\xi }g' \, ^2 =0 
    \label{thirdordernonlineareqn3}
\end{equation}$$

where the \\('\\) denotes differentiation with respect to \\( \xi \\).

For easier numerical analysis, it is preferable to split Eq. \ref{thirdordernonlineareqn3}, which is a third order nonlinear differential equation, into a system of two lower order differential equations.

Let's define a new variable, 

$$\begin{equation}
    \boxed{u=\xi g'}
    \label{uvariable}
\end{equation}$$

, and its derivatives

$$\begin{align*}
    u &= \xi g' \\
    u' &= g' + \xi g'' \\
    u'' &= 2 g'' + \xi g'''
\end{align*}$$

By substituting Eq. \ref{uvariable} and its derivatives into Eq. \ref{thirdordernonlineareqn3}, 

$$\begin{equation*}
    \boxed{u'' = - \dfrac{1 + g + \ln \xi}{\xi} u' + \dfrac{2 \beta}{\xi^2} u + \dfrac{\beta}{\xi^2} u^2}
\end{equation*}$$

To make the equations simpler, we define new variables,

$$\begin{equation}
    \boxed{A=-\dfrac{1+g+\ln \xi}{\xi}, \quad B=\dfrac{\beta}{\xi^2}}
    \label{newvariablesAandB}
\end{equation}$$

<div class="equation-box">
  <h3>Governing Differential Equations</h3>
  <div>
$$\begin{gather}
    u=\xi g' \tag{\ref{uvariable}}\\
    u'' = A u' + 2B u +Bu^2 \label{uprimeprimeeqn}
\end{gather}$$

Boundary Conditions: 
$$\left\{
\begin{aligned}
    g(\xi=1) &= 0 \\ 
    u(\xi=1) &= -1 \\
    u(\xi=0) &= 0
    \end{aligned} \right\} \notag$$
</div>
</div>
    
Now we can replace the derivatives with the finite difference version of them. Eqs. \ref{uvariable}-\ref{uprimeprimeeqn} turns into,

$$\begin{equation}
    \dfrac{u_{j+1}+u_j}{2}= \xi_{1/2+j} \dfrac{g_{j+1}-g_j}{h}= \left(\dfrac{h}{2} + hj \right) \left( \dfrac{g_{j+1} - g_j}{h}\right)
    \label{sysofeqnfinitediffform1}
\end{equation}$$

$$\begin{equation}
    \dfrac{u_{j+1} - 2u_j + u_{j-1}}{h^2}=A_j \left( \dfrac{u_{j+1}-u_{j-1}}{2h}\right) + 2 B_j u_j + B_j u_j^2
    \label{sysofeqnfinitediffform2}
\end{equation}$$

Solve Eq. \ref{sysofeqnfinitediffform1} for \\( g_{j+1} \\) to obtain,

$$\begin{equation}
    \boxed{g_{j+1} = g_j + \dfrac{u_{j+1}+u_j}{1+2j}}
    \label{finalfinitediff1}
\end{equation}$$

Multiplying Eq. \ref{sysofeqnfinitediffform2} through by \\( h^2 \\) and with some rearranging,

$$\begin{equation}
    \boxed{\left(1-\dfrac{h}{2} A_j \right) u_{j+1} - 2 \bigg(h^2 B_j +1 \bigg) u_j + \left(1+\dfrac{h}{2}A_j \right) u_{j-1} - B_j u_j^2h^2 = 0 } 
    \label{finalfinitediff2}
\end{equation}
$$

To summarize, 

<div class="equation-box">
  <h3>Governing Finite Difference Equations</h3>
  <div>
$$\begin{gather*}
    g_{j+1} = g_j + \dfrac{u_{j+1}+u_j}{1+2j} \tag{\ref{finalfinitediff1}}\\[1.5ex]
    \left(1-\dfrac{h}{2} A_j \right) u_{j+1} - 2 \bigg(h^2 B_j +1 \bigg) u_j + \left(1+\dfrac{h}{2}A_j \right) u_{j-1} - B_j u_j^2h^2 = 0 \tag{\ref{finalfinitediff2}}
\end{gather*}$$

    Boundary Conditions: 
$$\left\{
    \begin{aligned}
        g_N &= 0 \\ 
        u_N &= -1 \\
        u_0 &= 0
    \end{aligned} \right\} \notag
    $$
</div>
</div>

## Hand Calculations

I have found that it is helpful to solve this by hand first, using smaller intervals, like \\( N = 5 \\). Once I have the logic down, I can use MATLAB to iterate for more intervals. For \\( N=5 \\), \\( u_0 = 0 \\) and \\( u_5=-1 \\). Looping Eq. \ref{finalfinitediff2} from \\( j=1 \\) to \\( j=4 \\), I obtain the following,

$$\begin{align*}
    -2 \bigg(h^2B_1 + 1 \bigg) u_1+\left(1 - \dfrac{h}{2}A_1 \right)u_2  = B_1 u_1^2 h^2 \\
    \left(1+\dfrac{h}{2}A_2 \right) u_1 -2 \bigg(h^2 B_2 + 1\bigg)u_2+\left(1-\dfrac{h}{2}A_2 \right)u_3= B_2 u_2^2 h^2 \\
    \left(1+\dfrac{h}{2}A_3 \right) u_2 -2 \bigg(h^2 B_3 + 1 \bigg)u_3 + \left(1 - \dfrac{h}{2}A_3 \right)u_4= B_3 u_3^2 h^2 \\
    \left(1+\dfrac{h}{2}A_4 \right)u_3 -2 \bigg(h^2 B_4 +1 \bigg)u_4-\left(1-\dfrac{h}{2}A_4 \right)= B_4 u_4^2 h^2 
\end{align*}$$

This system of equations forms a tridiagonal matrix. 

$$
\begin{bmatrix}
-2 \bigg(h^2B_1 + 1 \bigg) & 1 - \dfrac{h}{2}A_1  & 0   & 0   \\
1+\dfrac{h}{2}A_2  & -2 \bigg(h^2 B_2 + 1\bigg) & 1-\dfrac{h}{2}A_2 & 0   \\
0   & 1+\dfrac{h}{2}A_3 & -2 \bigg(h^2 B_3 + 1 \bigg) & 1 - \dfrac{h}{2}A_3  \\
0   & 0   & 1+\dfrac{h}{2}A_4  & -2 \bigg(h^2 B_4 +1 \bigg)
\end{bmatrix}
\begin{bmatrix}
u_1 \\
u_2 \\
u_3 \\
u_4
\end{bmatrix}
+
\begin{bmatrix}
0 \\
0 \\
0 \\
\dfrac{h}{2} A_4-1
\end{bmatrix}
=
\begin{bmatrix}
B_1 u_1^2 h^2 \\
B_2 u_2^2 h^2 \\
B_3 u_3^2 h^2 \\
B_4 u_4^2 h^2
\end{bmatrix}
\notag
$$

### First Loop: k=1

For the first loop \\( k=1 \\), we assume a linearly spaced \\( \mathbf{u}^{(k)} \\) vector as an initial guess. The independent variable \\( \boldsymbol{\xi} \\) will range from 0 to 1 linearly spaced. 

$$\boldsymbol{\xi}= \begin{bmatrix}
    0 \\
    0.2 \\
    0.4 \\
    0.6 \\ 
    0.8 \\
    1
\end{bmatrix}, \quad \quad \mathbf{u}^{(1)}=\begin{bmatrix}
    0 \\
    u_1^{(1)}\\
    u_2^{(1)} \\
    u_3^{(1)} \\
    u_4^{(1)} \\
    -1
\end{bmatrix} = \begin{bmatrix}
    0 \\
    -1/5\\
    -2/5 \\
    -3/5 \\
    -4/5 \\
    -1
\end{bmatrix}
\notag
$$

To get the \\( \mathbf{g}^{(k)} \\) vector, we apply Eq. \ref{finalfinitediff1} recursively, going backward from \\( g_N=g_5=0 \\)

$$\mathbf{g}^{(1)}=\begin{bmatrix}
    g_0^{(1)} \\
    g_1^{(1)} \\
    g_2^{(1)} \\
    g_3^{(1)} \\
    g_4^{(1)} \\
    0
\end{bmatrix}= \begin{bmatrix}
    1 \\
    0.8 \\
    0.6 \\
    0.4 \\
    0.2 \\
    0
\end{bmatrix}
\notag$$

I use Eq. \ref{newvariablesAandB} to obtain all the A and B variables, 

$$\mathbf{A^{(1)}}= \begin{bmatrix}
    A_1^{(1)} \\
    A_2^{(1)} \\
    A_3^{(1)} \\
    A_4^{(1)} \\
\end{bmatrix} = \begin{bmatrix}
    -0.9528 \\
    -1.709 \\
    -1.482 \\
    -1.221
\end{bmatrix}, \quad \quad \mathbf{B}^{(1)}= \begin{bmatrix}
    B_1^{(1)} \\
    B_2^{(1)} \\
    B_3^{(1)} \\
    B_4^{(1)} \\
\end{bmatrix} = \begin{bmatrix}
    25 \\
    6.25 \\
    2.778 \\
    1.5625
\end{bmatrix} \notag$$

$$
\begin{bmatrix}
-4 & 1.09528 & 0      & 0      \\
0.8291 & -2.5 & 1.1709 & 0      \\
0      & 0.8518 & -2.222 & 1.1482 \\
0      & 0      & 0.8779 & -2.125
\end{bmatrix}
\begin{bmatrix}
u_1^{(2)} \\
u_2^{(2)} \\
u_3^{(2)} \\
u_4^{(2)}
\end{bmatrix}
=
\begin{bmatrix}
0.04 \\
0.04 \\
0.04 \\
1.1621
\end{bmatrix} \xrightarrow{\quad\quad\quad\quad} 
\begin{bmatrix}
    u_1^{(2)} \\
    u_2^{(2)} \\
    u_3^{(2)} \\
    u_4^{(2)}
\end{bmatrix}
= \begin{bmatrix}
    - 0.0897 \\
    -0.2912 \\
    -0.5241 \\
    -0.7634
\end{bmatrix} \notag
$$

With this updated \\( \mathbf{u}^{(2)}\\) vector, I repeat the same process as I did above.

This will be repeated until \\( \mathbf{g} \\) converges 

## MATLAB Code

```matlab
function [eta,fconv,df_deta_conv,alpha_h] = falknerskan(m)
% [eta, f, f', f''(0)] = falknerskan(m) numerically solves the Falkner-Skan equation:
%   f''' + (m+1)/2 f f'' + m(1 - f'^2) = 0
% 
% This function calculates the velocity profile of a boundary layer
% subject to a power-law external velocity profile u_e(x) = U0 * x^m.
% 
% Inputs:
%   m - Power of the external velocity profile (u_e(x) = U0 * x^m).
% 
% Outputs:
%   eta           - The similarity variable (dimensionless distance from the wall).
%   f             - The velocity profile function.
%   f_prime       - The first derivative of f (velocity gradient).
%   f_double_prime - The second derivative of f (curvature of the velocity profile).
%
% Example:
%   [eta, f, f_prime, f_double_prime] = falknerskan(0.5)

beta = (2*m)/(m+1); 
N = 5000;


%%%%%%% INITIALIZATION %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
h = 1/N;
initialu = transpose(linspace(0,-1,N+1));
initialg = zeros(N+1,1);
currentg = zeros(N+1,1);
currentu = transpose(linspace(0,-1,N+1));
prevu = initialu;
prevg = initialg;
diagmat = zeros(N-1,3);

xi = transpose(linspace(0,1,N+1));
eta = -log(xi);
B = calcB(xi(2:N),beta);
maindiag = -2*(h^2.*B+1);
n = length(maindiag);
rhs = zeros(N-1,1);

k = 0;
error = 1;

%%%%%%%%%%% LOOP BEGINS %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

while error > 10^-6
k = k + 1 ; 

    for j = N:-1:1
        currentg(j) = currentg(j+1) - (prevu(j+1) + prevu(j))/(1+2*(j-1));
    end

    A = calcA(xi(2:N),currentg(2:N));
     
    topdiag = 1-h/2.*A(1:N-2);
    botdiag = 1+h/2.*A(2:N-1);

    diagmat(1:end-1,1) = botdiag;
    diagmat(:,2) = maindiag;
    diagmat(2:end,3) = topdiag;

    mat = spdiags(diagmat,[-1 0 1],n,n);
    rhs = B.*prevu(2:N).^2*h^2;
    rhs(end) = rhs(end) - (h/2*A(end)-1);
    
    currentu(2:N) = mat \ rhs;
    error = norm(currentg-prevg);

    prevg = currentg;
    prevu = currentu;

    fprintf(' Iterations: %d   Error: %e\n',k, error);

end

%%%%%% RESULTS %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
df_deta_conv = currentu + 1 ;
uconv = currentu;
gconv = currentg;
fconv = eta - gconv;
alpha_h = -(3*uconv(end)-4*uconv(end-1)+uconv(end-2))/(2*h); 

% Flipping Vectors %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
df_deta_conv = flip(df_deta_conv);
uconv = flip(uconv);
gconv = flip(gconv);
fconv = flip(fconv);
eta = flip(eta);

% Step 1: Identify finite values in eta
finite_indices = isfinite(eta);

% Step 2: Filter vectors in place
eta = eta(finite_indices);
fconv = fconv(finite_indices);
df_deta_conv = df_deta_conv(finite_indices);

% Conversion to Textbook Form %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

eta = eta * (2/(m+1))^(1/2) ;
fconv = fconv * (2/(m+1))^(1/2) ;
alpha_h = alpha_h * ((m+1)/(2))^(1/2) ;

%%%%%%%%%%%%%%%% FUNCTIONS BEGIN HERE %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
function output = calcA(xi,g)
output = -(1./xi).*(1+ g + log(xi)) ;
end

function output = calcB(xi,beta)
output = beta./xi.^2;
end

end
```

### References 

Asai Asaithambi, A second-order finite-difference method for the Falkner–Skan equation, Applied Mathematics and Computation, 2004.