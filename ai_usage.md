# AI Use Log
- Tool/model & version: ChatGPT
- What I asked for: Provide pseudocode for the Rosalind problem 18.
- Snippet of prompt(s):
Show me pseudocode for the following problem: Find the most frequent k-mers (with mismatches and reverse complements) in a DNA string.
Given: A DNA string Text as well as integers k and d.
Return: All k-mers Pattern maximizing the sum Countd(Text, Pattern) + Countd(Text, Pattern) over all possible k-mers

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

def reverse_complement(Pattern):
    complement = {'A':'T', 'T':'A', 'C':'G', 'G':'C'}
    return ''.join(complement[nuc] for nuc in reversed(Pattern))

def most_frequent_kmers_with_mismatches_and_rc(Text, k, d):
    freq_map = {}
    max_count = 0
    result = []

    for i in range(len(Text) - k + 1):
        pattern = Text[i:i + k]
        neighborhood = neighbors(pattern, d)
        RC_neighborhood = set(reverse_complement(p) for p in neighborhood)

        for neighbor in neighborhood.union(RC_neighborhood):
            freq_map[neighbor] = freq_map.get(neighbor, 0) + 1
            if freq_map[neighbor] > max_count:
                max_count = freq_map[neighbor]

    for pattern in freq_map:
        if freq_map[pattern] == max_count:
            result.append(pattern)

Text = "ATGGTGCACGGTAAGCGTGCTACGGCTACTTTCGTAAATGGTGCACGATGGTGCACGGTAAGCGTGCTACGGCTGCTACGGCTGTAAGCGTACTTTCGTAAACTTTCGTAAGTAAGCGTATGGTGCACGGCTACGGCTATGGTGCACGATGGTGCACGCTGGTCATCTATGGTGCACGACTTTCGTAAGTAAGCGTGTAAGCGTACTTTCGTAAGTAAGCGTCTGGTCATCTGTAAGCGTGCTACGGCTATGGTGCACGGCTACGGCTGCTACGGCTGTAAGCGTATGGTGCACGGCTACGGCTATGGTGCACGATGGTGCACGATGGTGCACGACTTTCGTAAGTAAGCGTCTGGTCATCTATGGTGCACGGTAAGCGTGTAAGCGTCTGGTCATCTGTAAGCGTGTAAGCGTCTGGTCATCTGCTACGGCTACTTTCGTAAGCTACGGCTGTAAGCGTATGGTGCACGACTTTCGTAACTGGTCATCTCTGGTCATCTATGGTGCACGATGGTGCACGGTAAGCGTATGGTGCACGCTGGTCATCTCTGGTCATCTATGGTGCACGCTGGTCATCTGCTACGGCTATGGTGCACGGCTACGGCTGCTACGGCTGTAAGCGTCTGGTCATCTCTGGTCATCTATGGTGCACGACTTTCGTAAACTTTCGTAAGTAAGCGTGCTACGGCTGCTACGGCTCTGGTCATCTACTTTCGTAAGCTACGGCTATGGTGCACGCTGGTCATCTCTGGTCATCTCTGGTCATCTATGGTGCACGGCTACGGCTACTTTCGTAACTGGTCATCTGTAAGCGTATGGTGCACGATGGTGCACGATGGTGCACGACTTTCGTAACTGGTCATCTACTTTCGTAACTGGTCATCTCTGGTCATCTGTAAGCGTGCTACGGCTGTAAGCGTACTTTCGTAAGTAAGCGTGTAAGCGTCTGGTCATCTACTTTCGTAAGCTACGGCTGCTACGGCTGTAAGCGT" 
k = 7 
d = 2 

print(" ".join(most_frequent_kmers_with_mismatches_andRC(Text, k, d)))

- How I verified correctness (tests, sample data): Checked with rosalind
  
