# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
~~~
clc ; 
close ; 
wp=input('Enter the pass band frequency (Radians )= ' ); 
ws=input('Enter the stop band frequency (Radians )= ' ); 
alphap=input( ' Enter the pass band attenuation (dB)=' ); 
alphas=input( ' Enter the stop band attenuation(dB)=' ); 
T=input('Enter the Value of sampling Time='); 
 
 
//Pre warping- Bilinear Transformation 
omegap=(2/T)*tan(wp/2); 
disp(omegap,'omegap='); 
omegas=(2/T)*tan(ws/2); 
disp(omegas,'omegas='); 
 
 
//Order of the filter 
 
N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap)); 
17 
 
disp(N,'N='); 
N=ceil(N); 
disp(N,'Round off value of N='); 
 
 
 
//Cut off frequency 
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
disp(omegac,'omegac='); 
 
 
Epsilon = sqrt ((10^(0.1*alphap))-1); 
disp(Epsilon,'Epsilon='); 
 
 
[pols ,gn] = zpch1(N, Epsilon,omegap ); 
disp(gn,'Gain'); 
disp(pols,'Poles'); 
 
 
 
hs=poly(gn,'s','coeff')/real(poly(pols,'s')); 
 
disp(hs,'Analog Low pass Chebyshev Filter Transfer function'); 
 
 
 
z=poly(0,'z');//Defining variable z 
 
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
disp(Hz,'Digital LPF Transfer function H(Z)='); 
 
 
HW=frmag(Hz,512); // Frequency response 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude '); 
title(' Frequency Response of Chebyshev IIR LPF');
~~~
# CALCULATION:
<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/2b3c13d1-1640-42d7-a39a-79f9e680a564" />
<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/920fb7c0-a4a4-470c-8da8-ec000f7f9e21" />
<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/d9c37ba9-d3c4-4478-a89b-e1c03e2fdf3b" />

# OUTPUT: 
<img width="1600" height="928" alt="image" src="https://github.com/user-attachments/assets/e664c23e-c314-44af-9434-0ad57394cd31" />
<img width="738" height="1600" alt="image" src="https://github.com/user-attachments/assets/e28f7430-6aaf-412f-9c38-ffad17c29bee" />


# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
