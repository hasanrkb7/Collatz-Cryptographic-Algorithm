# Collatz Cryptographic Algorithm

This is from our B.Sc. thesis "Creating a new Cryptographic Algorithm using Collatz Conjecture" at BRAC University, 2022. We were 3 students: Shoumya Shuprabho Rasheed, Rakibul Hasan Remon (me) and Monwar Labib. Our supervisor was Mobashir Monim.

## How the algorithm works

1. Alice and Bob make a list of shared secret numbers with Diffie-Hellman. In our example, p = 79 and g = 3, and the first shared number is 13.
2. Every shared number becomes a key. The key is the number of Collatz (3n+1) steps the number takes to reach the 4, 2, 1 loop. For 13, the key is 7.
3. Every character of the message is encrypted with 1 of 4 methods, and the key decides which one:
   - Shift cipher, if the key and the next key are both prime
   - X-OR, if the key is a perfect square
   - Byte injection, if the key is prime. An extra byte is added after the character.
   - Byte substitution with the AES S-box, for all other keys
4. Bob uses the same keys and does the steps backwards to get the message.

## What is inside

| File | What it is |
|---|---|
| `proposed_model.ipynb` | My code for the proposed model: encryption and decryption with the 4 methods, and the run time of every cell |
| `reports/pre-thesis-1-report.pdf` | Our pre-thesis 1 report (January 2022) |
| `reports/pre-thesis-2-report.pdf` | Our pre-thesis 2 report (May 2022) |

The notebook uses the key list from our Alice and Bob example in section 4.6 of the thesis, with the message "This is our Algorithm". Making the key list (section 4.4) is explained in the thesis, but it is not in the notebook.

## Who did what

| Member | Part |
|---|---|
| Rakibul Hasan Remon (me) | Chapter 2 (history of cryptography in World War I and II), section 3.1 (definitions), section 4.4 (making the key with Diffie-Hellman and the Collatz step count) and section 4.6 (the full Alice and Bob example). The proposed model code, the paper summaries and the 2 pre-thesis reports |
| Shoumya Shuprabho Rasheed | Abstract and introduction, section 3.2 (related work), sections 4.1 to 4.3 (problems with existing models, the architecture and the design choices) and section 4.5 (the 4 methods). The code that counts primes and perfect squares in random key lists (Figure 4.3), the diagrams and moving the thesis from Word to LaTeX |
| Monwar Labib | Chapter 5 (timing tests, how random the ciphertext is and the comparison with AES and RSA), chapter 6 (conclusion) and the references. The defence demo code, the RSA demo, the timing sheets and the defence slides and presentation |

This repository has my code and our 2 pre-thesis reports. The work of Shoumya and Labib is in the full thesis.

## How to run

Step 1: Open `proposed_model.ipynb` in Google Colab.

Step 2: Run all cells. The first cell installs `line_profiler` and `ipython-autotime`, which show the run time of every cell.

To try another message, change `Message` in cell 4.
