# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 

clc;
clear;
close;

// Input values
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = ');

// Centre value
alpha = (M - 1)/2;

// Ideal LPF impulse response
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc/%pi;
    else
        hd(n) = sin(Wc*((n-1)-alpha)) / (((n-1)-alpha)*%pi);
    end
end

// Hamming Window
for n = 1:M
    W(n) = 0.54 - (0.46*cos((2*%pi*(n-1))/(M-1)));
end

// Windowing process
h = hd .* W;

// Display filter coefficients
disp(h, 'Filter Coefficients are');

// Frequency response
[hzm, fr] = frmag(h, 256);

// Magnitude response
subplot(2,1,1);
plot(2*fr, hzm);
xlabel('Normalized Digital Frequency W');
ylabel('Magnitude');
title('Frequency Response of FIR LPF using Hamming Window');

// Magnitude response in dB
hzm_dB = 20*log10(hzm);

subplot(2,1,2);
plot(2*fr, hzm_dB);
xlabel('Normalized Digital Frequency W');
ylabel('Magnitude in dB');
title('Frequency Response of FIR LPF using Hamming Window');


# OUTPUT
<img width="755" height="707" alt="image" src="https://github.com/user-attachments/assets/054783cf-0148-4d80-a46d-3031d968873f" />

# RESULT
Thus design of low pass FIR digital filter waveforms were plotted and output was verified. 
