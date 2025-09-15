# AI Use Log
- Tool/model & version: ChatGPT
- What I asked for: Provide pseudocode for the Rosalind problem 15.
- Snippet of prompt(s): Provide pseudocode for the following problem
"Given: A DNA string Pattern and an integer d.
Return: The collection of strings Neighbors(Pattern, d)."
Return: All integer(s) i minimizing Skew(Prefixi (Text)) over all values of i (from 0 to |Genome|).
- What I changed before committing: added

def hamming_distance(s1, s2):
    return sum(1 for a, b in zip(s1, s2) if a != b)

def neighbors(Pattern, d):
    if d == 0:
        return {Pattern}
    if len(Pattern) == 1:
        return {"A", "C", "G", "T"}

    Neighborhood = set()
    SuffixNeighbors = neighbors(Pattern[1:], d)

    for text in SuffixNeighbors:
        if hamming_distance(Pattern[1:], text) < d:
            for nucleotide in ["A", "C", "G", "T"]:
                Neighborhood.add(nucleotide + text)
        else:
            Neighborhood.add(Pattern[0] + text)
    return Neighborhood
s1="ACG"
d= 1
print('\n'.join(neighbors(s1, d)))


- How I verified correctness (tests, sample data): Checked with rosalind
  
