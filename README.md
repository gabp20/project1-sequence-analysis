# Identifying and characterising mutations in NGS data 
This program will compare 1000 sequencing reads from three samples treated with a genotoxic agent and three untreated control samples of a fission yeast (S.pombe) with a reference sequence. The program simulates Next Generation Sequencing and the goal to identify nucleotide mismatches and mutations to discover patterns between the two groups.

# How to run the program
Run the program from Google Colab from file -> Open notebook -> GitHub, then paste this repository's URL choosing .ipynb notebook. Select Run all and read each cell in order.   

# Inputs and Outputs
This program inputs a reference DNA sequence and a read dictionary. Outputs return read and sample summaries, printing a group table for read counts, mismatch percentages and substitutions. The three top positions for highest mismatch counts are also printed with means, differences and a Welch's t-test results. 

# Code design
