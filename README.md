# Digital-Signal-Processing--Design-of-Adaptive-Filter

## AIM:
To Design and Implementation of Adaptive filters using MATLAB.

## SOFTWARE REQUIRED:
MAT LAB R2012

## ALGORITHM:
Step 1: Open mat lab. Write the program.

Step 2: Generating the desired signal. 

Step 3: Generating a signal corrupted with noise

Step 4: Estimating the signal. 

Step 5: Computing the Error signal. 

Step 6: Plot all the signals with x-label and y-label with suitable title

Step 7: Terminate the program.

## PROGRAM:
ADAPTIVE FILTER<br>
clc;<br>
clear all;<br>
close all;<br>
%Generating the desired signal<br>
t=0.001:0.001:1<br>
D=2*sin(2*pi*50*t);<br>
%Generating a signal corrupted with noise<br>
n=numel(D);<br>
A=D(1, n) +0.9*randn(1, n);<br>
l=D-A;<br>
rr=[];<br>
k=1;<br>
r=xcorr(A);<br>
M=25;<br>
for i=1:1:M<br>
 rr(i) =r(n-i+1);<br>
end<br>
R=toeplitz(rr);<br>
I=inv(R);<br>
p=xcorr(D,A);<br>
for i=1:1:M<br>
 P(i) =p(n-i+1);<br>
end<br>
w=inv(R') *P';<br>
k=1;<br>
%Estimating the signal<br>
Est=zeros(n, 1);<br>
for i=M:n<br>
 j=A(i:-1:i-M+1);<br>
 Est(i) =(w)'*(j)';<br>
end<br>
%Computing the Error signal<br>
Err=Est'-D;<br>
%Display of signal<br>
subplot (4,1,1), plot(D)<br>
title('Desired Signal');<br>
subplot (4,1,2), plot(A)<br>
title('Signal corrupted with noise');<br>
subplot (4,1,3), plot(Est)<br>
title('Estimated Signal');<br>
subplot (4,1,4), plot(Err)<br>
title('Error Signal');<br>

## OUTPUT:
![WhatsApp Image 2025-11-26 at 08 53 17_7b39c357](https://github.com/user-attachments/assets/44b73536-2c70-4357-92c7-fdafd1906120)


## RESULT:
![WhatsApp Image 2025-11-28 at 22 32 08_b90623ae](https://github.com/user-attachments/assets/37e73dd6-ffa2-41f0-b650-6a441d49e6b1)

