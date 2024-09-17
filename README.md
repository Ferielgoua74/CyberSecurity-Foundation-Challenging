# Vigenère Cipher Cryptanalysis

This project demonstrates the process of decrypting a ciphertext encoded with the **Vigenère Cipher** using frequency analysis.

## Overview

The Vigenère cipher is a method of encrypting alphabetic text by using a simple form of polyalphabetic substitution. This program performs cryptanalysis of the cipher by analyzing the frequency of letters in the ciphertext, which helps in determining the key length and subsequently the key used for decryption.

### Ciphertext

The following ciphertext was provided for Instructionss :
Cryptanalysis of the Vigen`ere Cipher This following ciphertext was encrypted using the Vigen`ere Cipher, where all spaces and punctuation were removed. Decrypt it, using any tool you like: XUKW LGEE YINN WBVL BWKU VXUC XLQY FJSH NHNV PRCW GQRP GMAA SHTP VHIO TSJU IGJI JGFS QVFQ QRMM AFIE IEEV IAEV LRXB VSBN WNUC BWWR GWRX IECP BHXU GQNT INXE VNEO NINP HNTI DWMG GEON IGQT RTJB TQNH VRSY RPGL CRNN CFKW NPHG JYFV SRXI AIYR UWGJ IFGG EGXX GCBH XUKW PKTU GVCN ELKR TCVB WRQY MGJX UGQP CROG EYQX BHJH PFHV RBYT YGEF GJBT KRVE OQYG VLVU EAEM RPXF VYSH JBTX UGVR UXBH XUKW PQYE UIVP XUGV ROEV PHRT SSVL RESH TWRY IJKP YHSP WWBP QBTI RNEO QVNV ISQV ZUSS UIPW VVVC GJEG EEAP SGDI OTSX GROA WHEL NUMZ RPRV IPJR VSYR

## Code

### 1. Frequency Analysis

The first step in decrypting the cipher is performing **frequency analysis** on the ciphertext. This analysis will help to identify the most common letters, which are likely to correspond to high-frequency letters in the plaintext (such as 'E', 'T', 'A' in English).

python
from collections import Counter
import re

# Defining the ciphertext
ciphertext = """<Insert Your Ciphertext Here>"""

# Function to perform frequency analysis
def get_frequency(text):
    # Remove all non-alphabetic characters and count the frequency of each letter
    cleaned_text = re.sub(r'[^A-Z]', '', text.upper())
    return Counter(cleaned_text)

# Frequency analysis of the ciphertext
frequency = get_frequency(ciphertext)
print(frequency)
# Function to calculate the Index of Coincidence (IC)
def index_of_coincidence(text):
    # Clean the text to contain only uppercase letters
    cleaned_text = re.sub(r'[^A-Z]', '', text.upper())
    N = len(cleaned_text)
    frequency = Counter(cleaned_text)
    ic = sum(f * (f - 1) for f in frequency.values()) / (N * (N - 1))
    return ic

# Calculating the IC for the ciphertext
ic_value = index_of_coincidence(ciphertext)
print(ic_value)


