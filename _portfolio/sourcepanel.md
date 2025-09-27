---
title: "Source Panel Method"
excerpt: "A numerical method to calculate the pressure distribution in a steady, irrotational flow."
order: 1
layout: splash
image: /images/sourcepanelmain.png
caption: "Photo credit: https://web.itu.edu.tr/"
header:
  overlay_color: "#2a4d8f"           
  hero_title: "Source Panel Method"
  hero_excerpt: "A numerical method to calculate the pressure distribution in a steady, irrotational flow."
---

<a href="/portfolio/" class="button-gradient" style="display: inline-block; margin-top: 20px;">
  ← Back to Portfolio Page
</a>

## Introduction

### Basics of Source Panel

Potential flow theory allows engineers to find fluid properties by making the following assumptions about the flow: it is incompressible, inviscid, and irrotational. When the flow is irrotational (or potential) and it satisfies conservation of mass, the flow is said to satisfy Laplace's equation, or

$$\begin{equation} \label{laplace}
    \nabla^2\phi=0 \  \longrightarrow \ \frac{\partial^2 \phi}{\partial x^2} + \frac{\partial^2 \phi}{\partial y^2} = 0 . 
\end{equation}$$

If Laplace's equation is satisfied, the solutions can be superimposed to form a more complex flow. The source panel method is simply the superposition of an infinite number of sources with infinitesimal strength along an arbitrary shape. To make the calculation easier, the source strength is assumed to be constant along each panel, which is a straight line that approximates the shape geometry. 

## Governing Equations and Conditions

### Fundamental Velocity Potential Equation

Every jth panel induces a small change of velocity potential at a point. When summed together for all jth panels, 

$$\begin{equation}
    \boxed{\sum_{j=1}^{n} \Delta\phi_j = \sum_{j=1}^{n}\frac{\lambda_j}{2\pi}\int_j{\ln(r_{ij}) ds_j}},
\end{equation}$$

where 

$$\begin{equation}
    r_{ij} =\sqrt{((x_i-x_j)^2+(y_i-y_j)^2)}
\end{equation}$$

The point where the sum of the velocity potentials is evaluated at is called the control point, denoted with a subscript i. The control points are placed at the midpoint of each panel. 

### Boundary Conditions

In order for the flow to make sense physically, the arbitrary body must be a streamline of the flow. This means that the normal velocity of each panel must be equal to 0. The following equations must be true,

$$\begin{gather}
    V_{\infty,n,i} + V_{n,i} = 0 \\
    \boxed{\frac{\lambda_i}{2} + \sum_{\substack{j=1 \\ j\neq i}}^{n}\frac{\lambda_j}{2\pi}I_{i,j} + V_{\infty} \cos{(\beta_i)} = 0,} \label{vn}
\end{gather}$$

where

$$\begin{equation}
    I_{i,j} = \int_j{\frac{\partial}{\partial n_i}}(\ln{r_{ij}}) \, ds_j
\end{equation}$$

When \\( i = j \\), there is a singular point because \\( r_{ij} \\) is equal to 0. However, it can be shown that the contribution of the panel to itself is \\( \lambda/2 \\), which is the leading term in Equation (\ref{vn}).

### Tangential Velocity Calculation

At the surface of the panel, there exists only a tangential velocity, so it will simply be labeled as \\( V_i \\), 

$$\begin{equation}
    \boxed{V_i = V_{\infty,s} + V_s = V_{\infty}\sin{(\beta_i)} + \sum_{j=1}^n \frac{\lambda_j}{2\pi}J_{i,j}}
\end{equation},$$

where 

$$\begin{equation}
    J_{i,j} = \int_j \frac{\partial}{\partial s} \ln{r_{ij}} \, ds_j
\end{equation}$$

### Pressure Coefficient

Using Bernoulli's equation, it is possible to convert velocity into pressure, 

$$\begin{equation}
    \boxed{C_{p,i} = 1 - \Bigl(\frac{V_i}{V_\infty}\Bigr)^2}
\end{equation}$$

## Evaluating Integral

To evaluate the integral, Anderson derives the formula. Here are the results, 

$$\begin{equation}
I_{i,j} = \frac{C}{2} \ln{\biggr(\frac{S_j^2+2AS_j+B}{B}\biggl)} + \frac{D-AC}{E} \biggl({\text{tan}}^{-1}{\frac{S_j+A}{E}}-{\text{tan}}^{-1}{\frac{A}{E}} \biggr), \\
\end{equation}$$

where 

$$\begin{gather*}
A = -(x_i - X_j)\cos{\Phi_j} - (y_i - Y_j)\sin{\Phi_j} \\ 
B = (x_i-X_j)^2 + (y_i-Y_j)^2 \\ 
C = \sin{(\Phi_i-\Phi_j)} \\
D = (y_i - Y_j)\cos{\Phi_i} - (x_i-X_j)\sin{\Phi_i} \\ 
S_j = \sqrt{(X_{j+1}-X_j)^2+(Y_{j+1}-Y_j)^2} 
\end{gather*}.$$

For calculating the tangential velocities,

$$\begin{equation}
    J_{i,j} = \frac{D-AC}{2E} \ln{\frac{S_j^2+2AS_j+B}{B}} - C\biggl({\text{tan}}^{-1}{\frac{S_j+A}{E}}-{\text{tan}}^{-1}{\frac{A}{E}} \biggr)
\end{equation}$$

## Results

<!-- Figure 1 -->
<div style="display: flex; justify-content: center; gap: 1rem;">

  <figure style="flex: 1; text-align: center;">
    <img src="/images/panels3.jpg" alt="Coarse Approximation of Circle" style="width:100%;">
    <figcaption>(a) Coarse Approximation of Circle</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center;">
    <img src="/images/panels8.jpg" alt="Medium Approximation of Circle" style="width:100%;">
    <figcaption>(b) Medium Approximation of Circle</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center;">
    <img src="/images/panels64.jpg" alt="Fine Approximation of Circle" style="width:100%;">
    <figcaption>(c) Fine Approximation of Circle</figcaption>
  </figure>

</div>

<p style="text-align:center;"><strong>Figure 1:</strong> Panel Approximation of Circle (In Increasing Order)</p>


<!-- Figure 2 -->
<div style="display: flex; justify-content: center; gap: 1rem;">

  <figure style="flex: 1; text-align: center;">
    <img src="/images/cp8.jpg" alt="Coarse Approximation of Circle" style="width:100%;">
    <figcaption>(a) Coarse Approximation of Circle</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center;">
    <img src="/images/cp64.jpg" alt="Medium Approximation of Circle" style="width:100%;">
    <figcaption>(b) Medium Approximation of Circle</figcaption>
  </figure>

</div>

<p style="text-align:center;"><strong>Figure 2:</strong> Source Panel Method for Circle</p>


<!-- Figure 3 -->
<div style="display: flex; justify-content: center; gap: 1rem;">

  <figure style="flex: 1; text-align: center;">
    <img src="/images/ellipsepanel.jpg" alt="Panel Approximation of Ellipse" style="width:100%;">
    <figcaption>(a) Panel Approximation of Ellipse</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center;">
    <img src="/images/ellipsesource.jpg" alt="Ellipse Pressure Coefficient vs Angle" style="width:100%;">
    <figcaption>(b) Ellipse Pressure Coefficient vs Angle</figcaption>
  </figure>

</div>

<p style="text-align:center;"><strong>Figure 3:</strong> Source Panel Method for Ellipse</p>

## Conclusions

### Concepts Learned From Results

As the number of panels increase, the accuracy of the source panel method improves. This is because a greater number of panels is able to resemble the geometry of the actual shape more. For example, Fig. 1a shows a crude approximation of a circle, with 3 panels. Fig. 1b shows a better approximation with 8 panels, and Fig. 1c is most indistinguishable from the actual geometry with 64 panels.

Fig. 2a shows that the source panel method closely resemble the analytical solution. As the number of panels increase, more pressure points are shown, and the reader gains a better understanding of the actual distribution, as shown in Fig. 2b 

The ellipse pressure coefficient has the same sinusoidal shape as the circle pressure distribution, but the amplitude appears to be less than the circle, as shown in Fig. 3b. In addition, at the crest of the wave, the scatter points are closer together, likely because of the uneven geometry of the ellipse. 

### Differences From Real Life

Potential theory, which the source panel method is based on, neglects viscosity. Because of this, there is no boundary layer separation, which is caused by adverse pressure gradient. In other words, the pressure on the left and right side balance out. 

When boundary layer separation occurs, the pressure in the wake region decreases drastically and remains constant. This difference in pressure creates a drag force, which is not present in the source panel method. 


## Code

In order to run the code, the user must have the .txt files downloaded with the coordinates for the arbitrary shape. This will be attached to the report within submission. In line 3 of the code, it is crucial **to change the name of the .txt file**. At the end of the first script, a supplemental script file is provided to generate coordinates for any number of panels for a circle. 

```matlab
clear,clc, close all 

A = readmatrix('Circle_8.txt'); % NATHAN, simply change the name of the text file to get source panel method for any geometry you want, just put the coordinates in 
sz = size(A) ; %gets the size of the matrix A 
n = sz(1) ; % picks the number of panels based on length of vector 
beta = zeros(n,1);  % preallocating matrix
theta=zeros(n,1); %preallocating vector

for i = 1:n-1 % nested for loop begins 
        Xi = A(i,1); Yi = A(i,2); % control points boundary (Xi,Yi)
        Xi1 = A(i+1,1); Yi1 = A(i+1,2); % control points boundary (X_i+1,Y_i+1)
        xi = (Xi+Xi1)/2; yi = (Yi+Yi1)/2 ; % finds control points by taking the average 
        phii = atan2(Yi1-Yi,Xi1-Xi); % calculates angle of ith panel
        beta(i) = phii + pi/2 ; % calculates beta: angle bet freestream and normal
        if beta(i)>2*pi, % if beta is greater than 2pi, subtract 2pi. if less than zero, add 2pi
            beta(i)=beta(i)-2*pi; 
        elseif beta(i)<0, 
            beta(i)=beta(i)+2*pi;
        end 
    for j = 1:n-1 %populates the columns of a matrix, holding the row constant (nested for loop)
            I(i,j) = calcI(A(j,1),A(j,2),A(j+1,1),A(j+1,2),xi,yi,phii); %here, I used a local function (look below for function)
            J(i,j) = calcJ(A(j,1),A(j,2),A(j+1,1),A(j+1,2),xi,yi,phii) ;%here, I used a local function (look below for function)
    end
end

for i = 1:n
    I(i,i) = pi; %replace all diagonals with pi
    J(i,i) = 0 ; % replace all diagonals with 0 
end

I(isnan(I)|isinf(I))=0; %removes any NaN and inf terms 
J(isnan(J)|isinf(J))=0; %removes any NaN and inf terms

b = -cos(beta) ; 
lambda_norm = I^(-1) * b ; %normalized lambda = lambda/(2 * pi * vinf)

vi_vinf = J*lambda_norm+sin(beta); % ratio of v and v_inf 
cpi = 1-(vi_vinf).^2 ; % cp at each panel

figure; hold on ; grid on
title('Cirlce Source Panel Pressure Distribution','FontSize',18)
str2 = sprintf('(n = %d)',n-1)
subtitle(str2,'FontWeight','bold','FontSize',18)
theta = linspace(0,2*pi) ; cp_anal = 1-4*(sin(theta)).^2; %analytical solution 
plot(theta,cp_anal,'k','linewidth',1); 
scatter(beta,cpi,80,'^','filled','MarkerFaceColor','b') ; % scatter 
xlabel('Surface Location Angle \theta (rad)','FontSize',12)
ylabel('Pressure Coefficient (C_p)','FontSize',12)
xticks([0, pi/2, pi, 3*pi/2, 2*pi])
xticklabels({'0','\pi/2','\pi','3\pi/2','2\pi'})
legend('Analytic Result','Numerical Result')
hold off 

figure; hold on; 
str1 = sprintf('Panel Approximation of Circle (n = %d)',n-1)
title(str1,'fontsize',20)
plot(A(:,1),A(:,2),'g','linewidth',8) ;
t = linspace(0,2*pi,1000) ; 
X = cos(t);
Y = sin(t);
plot(X,Y,'r:','linewidth',8)
xlabel('X-Axis','FontSize',15)
ylabel('Y-Axis','FontSize',15)
legend('Panels','Actual Circle','Location','southeast')
hold off

%% Functions Begin %% 

function I = calcI(Xj,Yj,Xj1,Yj1,xi,yi,phii) % equations from Anderson's book: normal velocity component 
phij = atan2(Yj1-Yj,Xj1-Xj);
A = -(xi-Xj)*cos(phij)-(yi-Yj)*sin(phij) ;
B = (xi-Xj)^2+(yi-Yj)^2 ; 
C = sin(phii-phij) ; 
D = (yi-Yj)*cos(phii)-(xi-Xj)*sin(phii) ; 
Sj = sqrt((Xj1-Xj)^2+(Yj1-Yj)^2) ; 
E = sqrt(B-A^2) ; 
I = (C/2)*log((Sj^2+2*A*Sj+B)/B) + (D-A*C)/E*(atan((Sj+A)/E)-atan(A/E)) ; 
end

function J = calcJ(Xj,Yj,Xj1,Yj1,xi,yi,phii) % equations from Anderson's book: tangential velocity
phij = atan2(Yj1-Yj,Xj1-Xj);
A = -(xi-Xj)*cos(phij)-(yi-Yj)*sin(phij) ;
B = (xi-Xj)^2+(yi-Yj)^2 ; 
C = sin(phii-phij) ; 
D = (yi-Yj)*cos(phii)-(xi-Xj)*sin(phii) ; 
Sj = sqrt((Xj1-Xj)^2+(Yj1-Yj)^2) ; 
E = sqrt(B-A^2) ; 
J = (D-A*C)/(2*E)*log((Sj^2+2*A*Sj+B)/B) - C*(atan((Sj+A)/E)-atan(A/E)) ; 
end
```

```matlab
n = 3;
dtheta = 2*pi/n;
theta = pi+pi/n:-dtheta:-pi+pi/n; 
X = cos(theta);
Y = sin(theta);
A = [X',Y'];

writematrix(A,'circle_3','Delimiter',';'); 
```

## References

J. D. Anderson. Fundamentals of aerodynamics. Mcgraw-hill Publishing Co., 2007.

<a href="/portfolio/" class="button-gradient" style="display: inline-block; margin-top: 20px;">
  ← Back to Portfolio Page
</a>