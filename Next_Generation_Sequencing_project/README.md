# DNA Compression using Burrows-Wheeler Transform (BWT)
This project demonstrates the application of the Burrows-Wheeler Transform (BWT), Run-Length Encoding (RLE), and Move-to-Front (MTF) Encoding on DNA sequences. It was developed as part of coursework for the NGS (Next-Generation Sequencing) module for the MSc Bioinformatics program.


### The code includes:

- Forward and inverse BWT implementation

- RLE compression on the BWT output

- Bit size calculation for compression efficiency

- MTF encoding demonstration


### Features
- Rotates and sorts DNA sequences to compute the Forward BWT

- Reconstructs the original sequence from BWT (Inverse BWT)

- Applies Run-Length Encoding (RLE) to compress BWT output

- Calculates bit size of original, BWT, and RLE sequences

- Computes compression gain (score) based on bit reduction

- Includes an implementation of Move-to-Front (MTF) Encoding for additional compression analysis


### Requirements
Python 3 (no external packages required)


### Input
Modify the dna_sequences variable in the code to include your list of DNA sequences.


### Output
For each sequence, it prints:

- Original sequence

- Sequence prepared for BWT

- Forward BWT result

- Inverse BWT result

- RLE-compressed sequence

- Bit sizes for original, BWT, and RLE versions

- Compression gain


### License
MIT License. Feel free to reuse, modify, and share.