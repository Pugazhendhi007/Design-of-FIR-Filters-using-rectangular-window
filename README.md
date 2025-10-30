# Design-of-FIR-Filters-using-rectangular-window
#          DESIGN OF LOW PASS FIR DIGITAL FILTER 
## NAME : S PUGAZHENDHI
## REG NO.:212223060214

# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
clear;
close;

// FIR Low Pass Filter Design using Fourier Series Method
// with Rectangular Window

// Step 1: Input specifications
M = input("Enter the Odd Filter Length = ");      // e.g., 21
Wc = input("Enter the Digital Cutoff Frequency (in radians) = "); // e.g., 0.4*%pi

alpha = (M - 1) / 2;     // Center index

// Step 2: Compute ideal impulse response (sinc function)
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc / %pi;   // At center, sinc(0) = 1
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

// Step 3: Define window coefficients (Rectangular window)
for n = 1:M
    W(n) = 1;    // Rectangular window → all ones
end

// Step 4: Apply window to impulse response
h = hd .* W;
disp(h, "Filter Coefficients are:");

// Step 5: Compute Frequency Response
[hzm, fr] = frmag(h, 256);  // 256-point frequency response

// Step 6: Plot magnitude and magnitude (dB)
subplot(2,1,1);
plot(2*fr, hzm);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude");
title("Frequency Response of FIR LPF using Rectangular Window");

subplot(2,1,2);
hzm_dB = 20 * log10(hzm);
plot(2*fr, hzm_dB);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude (dB)");
title("Frequency Response of FIR LPF using Rectangular Window (in dB)");

```

# OUTPUT
<img width="764" height="576" alt="Screenshot 2025-10-30 134049" src="https://github.com/user-attachments/assets/8b33cd5b-7e66-497c-a290-9cbbc214ee43" />


# RESULT
Thus the design of low pass FIR digital filter was generated using SCILAB.
