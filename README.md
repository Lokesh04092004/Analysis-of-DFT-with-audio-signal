# EXP 1 :  ANALYSIS OF DFT WITH AUDIO SIGNAL

# AIM: 

  To analyze audio signal by removing unwanted frequency. 

# APPARATUS REQUIRED: 
   
   PC installed with SCILAB/Python. 

# PROGRAM: 

// analyze audio signal
clc;
clear;
close;

// Read the audio file from Desktop
[x, Fs] = wavread("C:\\Users\\Intel\\Desktop\\voice.wav");  // Change name if needed

// Convert to mono if stereo
if size(x,2) == 2 then
    x = (x(:,1) + x(:,2)) / 2;
end

// Ensure column vector
x = x(:);

// Time axis
N = length(x);
t = (0:N-1)' / Fs;

// Compute DFT using FFT
X = fft(x);
magX = abs(X);
phaseX = atan(imag(X) ./ real(X));

// Frequency axis
f = (0:N-1)' * (Fs / N);

// Plot time domain signal
figure(1);
plot(t, x);
xlabel("Time (sec)");
ylabel("Amplitude");
title("Time Domain Signal");

// Plot magnitude spectrum (only 0 to Fs/2)
half = 1:floor(N/2);
figure(2);
plot(f(half), magX(half));
xlabel("Frequency (Hz)");
ylabel("Magnitude");
title("Magnitude Spectrum of Audio Signal");

// Plot phase spectrum
figure(3);
plot(f(half), phaseX(half));
xlabel("Frequency (Hz)");
ylabel("Phase (radians)");
title("Phase Spectrum of Audio Signal");




# OUTPUT: 

audio signal: 

<img width="1600" height="900" alt="dtsp 1b out" src="https://github.com/user-attachments/assets/960ce19a-fdf6-4075-a3b6-20fa678dda59" />


<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f859c354-b5e2-4996-a676-939137fa043b" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/8f079452-1ce8-459f-92fb-a5376595f30c" />


# RESULTS
Thus, the audio signal is analyzed using DFT and the output obtained.
