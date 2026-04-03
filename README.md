# Digital-Signal-Processing--FIR-HIGH-PASS-FILTER-DESIGN
## AIM:
To generate design of High pass FIR digital filter using Window.
## Software Required:
MAT LAB R2012.
## Algorithm:
Step 1: Open MATLAB and Write the program.

Step 2: Read the values of cut off frequency wc.

Step 2: Read the values of Order of the filter N.

Step 3: Find out the desired impulse response of the hIGH Pass filter Coefficient.

Step 4: Find out the windowing sequence.

Step 5: Plot the magnitude spectrum with x-label and y-label with suitable title.

Step 6: Terminate the program.

## PROGRAM:
```
clc;
clear all;
close all;

wc = pi/4;        % Cutoff frequency
N = 23;           % Filter length
alpha = (N-1)/2;
eps = 0.001;

% Ideal High Pass Filter (using spectral inversion)
n = 0:1:N-1;

% Low pass first
hd_lp = (sin((n-alpha+eps)*wc))./(pi*(n-alpha+eps));

% Convert to High Pass
hd = -hd_lp;
hd(alpha+1) = 1 - hd_lp(alpha+1);

% Blackman Window
wn = 0.42 - 0.5*cos((2*pi*n)/(N-1)) + 0.08*cos((4*pi*n)/(N-1));

% Final impulse response
hn = hd .* wn;

% Frequency response
w = 0:0.01:pi;
h = freqz(hn,1,w);

% Plot
plot(w/pi, abs(h), 'b');
xlabel('Normalized Frequency');
ylabel('Magnitude');
title('High Pass Filter using Blackman Window');
grid on;
```

## OUTPUT:
<img width="692" height="525" alt="image" src="https://github.com/user-attachments/assets/f99ea09d-c713-4c27-8a16-294d9f51e298" />


## RESULT:
<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/3b2583af-6ce9-4862-b4bd-9a51e7118900" />

