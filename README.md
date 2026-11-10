# Identifying and characterising mutations in NGS data 
This program will compare 1000 sequencing reads from three samples treated with a genotoxic agent and three untreated control samples of a fission yeast (S.pombe) with a reference sequence. The program simulates Next Generation Sequencing and the goal to identify nucleotide mismatches and mutations to discover patterns between the two groups.

# How to run the program
Run the program from Google Colab from file -> Open notebook -> GitHub, then paste this repository's URL choosing .ipynb notebook. Select Run all and read each cell in order.   

# Inputs and Outputs
This program inputs a reference DNA sequence and a read dictionary. Outputs return read and sample summaries, printing a group table for read counts, mismatch percentages and substitutions. The three top positions for highest mismatch counts are also printed with means, differences and a Welch's t-test results. 

# Code design
In step 4 i used .append() to build a list of reads for each sample before counting them. However, i later changed this to update counts in summaries[sample] as each read arrived. This built separate lists per sample which saved building extra lists for each sample. 

In step 5 i began by starting enumerate at zero and adding one after the sort to have a zero-based list index. Instead, i fixed this with start = 1 to give the reference position while sorting. One was then taken from reference position (position - 1) which gave the list index of the position where its pooled count was stored. I could then directly use the position as a key in each sample's position_counts to further calculate mismatch percentages.   

# Testing
1. assert summarise_samples([]) == {}   
Using [] means the data has no reads. If there isn't any samples the expected result in {} which checks that this function returns the right result.
   
2. sample1 = summaries["sample1"]
assert sum(sample1["substitution_counts"].values()) == 846
assert sample1["mismatch_events"] == 846
Using .values() gives the counts for all substiution types e.g. A>C or C>A. If we add those counts and check its the same as the total calculated by data['mismatch_events'] += len(mutations) it checks that they both agree. (846 is used as it is the total).

3. assert [row["position"] for row in position_results] == [97, 98, 99]
If we extract the position from each dictionary we can assert which positions were selected and the order. 97 had 454 mismatches but 98 and 99 had 453. 




