# AI Use Log
- Tool/model & version: ChatGPT
- What I asked for: Provide pseudocode for the Rosalind problem 13.
- Snippet of prompt(s): Provide pseudocode for the following problem
"Find a position in a genome minimizing the skew.
Given: A DNA string Genome.
Return: All integer(s) i minimizing Skew(Prefixi (Text)) over all values of i (from 0 to |Genome|).
- What I changed before committing: added

def MinSkewPositions(Genome):
  skew_list = [0]
  min_skew_positions = []
  for i in range(1, len(Genome)+1):
    current_skew = skew_list[i-1]
    if Genome[i-1] == 'C':
      skew_list.append(current_skew - 1)
    elif Genome [i-1] == 'G':
      skew_list.append(current_skew + 1)
    else: # A or T
      skew_list.append(current_skew) # A and T don't change the skew

  min_skew = min(skew_list)

  for i in range(len(skew_list)):
    if skew_list[i] == min_skew:
      min_skew_positions.append(i)

  return (min_skew_positions)

Genome = "CCTATCGGTGGATTAGCATGTCCCTGTACGTTTCGCCGCGAACTAGTTCACACGGCTTGATGGCAAATGGTTTTTCCGGCGACCGTAATCGTCCACCGAG"
print(MinSkewPositions(Genome))

- How I verified correctness (tests, sample data): Checked with rosalind
  
