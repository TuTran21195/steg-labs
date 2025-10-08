# Audio Steganography Techniques - Lab Exercises
![Audio Steganography Banner](https://img.shields.io/badge/Steganography-Audio-C5BAFF)
![License](https://img.shields.io/badge/License-MIT-B0DB9C)
![Python](https://img.shields.io/badge/Python-3\.x-C4D9FF?logo=python)
[![Docs](https://img.shields.io/badge/Documents-tutran21195\.github\.io-FF8282)](https://tutran21195.github.io/steg-labs/)
[![README-vi](https://img.shields.io/badge/README-vie-FFE99A)](https://tutran21195.github.io/steg-labs/)


## Introduce

This repository contains **lab exercises on steganography and steganalysis techniques in the audio domain**. The exercises are based on the detailed theoretical content from the textbook **["Information Hiding Techniques" - Do Xuan Cho, Posts and Telecommunications Institute of Technology](https://github.com/TuTran21195/steg-labs/blob/main/docs/Ch%E1%BB%A3%20%C4%90X%20gi%C3%A1o%20tr%C3%ACnh%20c%C3%A1c%20k%E1%BB%B9%20thu%E1%BA%ADt%20gi%E1%BA%A5u%20tin.pdf)**.

The goal of this repository is to provide a practical lab environment for students and enthusiasts to apply their theoretical knowledge of audio steganography directly to the implementation, testing, and evaluation of various methods.

-----

## Reference Theoretical Content

The lab exercises in this repository focus primarily on **Chapter 3: Information Hiding in Audio** from the "Information Hiding Techniques" textbook. This chapter provides foundational and advanced knowledge on:

  * **Characteristics of Audio Steganography**: Describes how audio signals are used as cover media and the associated challenges.
  * **Some Audio File Formats and Processing Tools**: Introduces common formats like WAV, AIFF, AU, RealAudio, MIDI, QuickTime and supporting tools.
  * **Classification of Audio Steganography Methods**: An overview of the main approaches.
  * **Specific Hiding and Extraction Methods**: Dives deep into techniques such as LSB, Phase Coding, Self-Marking, Spread Spectrum (DSSS, FHSS), and Echo Hiding.

-----

## Implemented Audio Steganography and Steganalysis Techniques

The labs in this repository include the implementation and testing of the following techniques:

1.  **LSB (Least Significant Bit) & LSB Matching Methods**:

      * **Hiding**: Implements the process of hiding information by replacing the least significant bits of audio samples with the bits of the secret message.
      * **Extraction**: Performs the reverse process to extract the hidden message.

2.  **Phase Coding Method**:

      * **Hiding**: Implements the process of hiding information by adjusting the phase of the audio signal after a Discrete Fourier Transform (DFT) on audio segments.
      * **Extraction**: Extracts the initial phase segment and reconstructs the message.

3.  **Spread Spectrum Method**:

      * **Hiding**: Implements the technique of hiding information by modulating a carrier wave.
      * **Extraction**: Performs despreading and demodulation to recover the information.
      * **Representation**: Visualizes the bits of the hidden message, pseudo-random code, and modulated code.
      * **Attack Test**: Evaluates the robustness of the method against attacks such as adding noise.

4.  **Self-Marking with STSM Technique**:

      * **Hiding**: Implements the technique of hiding information by modifying the sum of three consecutive samples to hide the message bits, combined with using a Hamming code for the hidden message string.
      * **Extraction**: Calculates the sum of three consecutive samples and uses Hamming code to recover the hidden message.
      * **Attack Test**: Evaluates the robustness of the method against attacks such as audio compression.

5.  **Echo Hiding Method**:

      * **Hiding**: Implements the method of hiding information by adding an echo to the original audio signal with different delays for bit 0 and bit 1.
      * **Extraction**: Calculates the Cepstrum and Autocorrelation Cepstrum values to detect the echo delay and extract the hidden information.

-----

## Directory Structure

The directory structure is organized by steganography technique for easy management and practice:

```
.
├── README.md
├── <labs-code>/
│   ├── imodule.rar/         # The imodule file for the lab
│   └── README.md/           # Some code descriptions for the lab
└── docs/
    └── <Theoretical reference materials>/
```

-----

## How to Use

> [!NOTE]
> All lab instructions are located at: [https://tutran21195.github.io/steg-labs/](https://tutran21195.github.io/steg-labs/)
>
> The lab creator's theoretical lecture notes: [TuTran Digital notes - Audio Steganography Series](https://tutran-garden.vercel.app/2025/stego/lecture_notes_colection/)

-----

## Contributions

All contributions to improve the labs, add new techniques, or optimize the source code are welcome\! Please create an issue or submit a pull request.

-----

## Author

[![TuTran21195](https://img.shields.io/badge/TuTran21195%20GitHub-096B68?logo=github&logoColor=fff&style=flat)](https://github.com/TuTran21195/)
