# AI Use Log
- Tool/model & version: ChatGPT
- What I asked for: Provide pseudocode for the Rosalind problem 17.
- Snippet of prompt(s):
For the following problem Find the most frequent k-mers with mismatches in a string.
Given: A string Text as well as integers k and d. Return: All most frequent k-mers with up to d mismatches in Text. show me pseudo code that works in the context of k ≤ 12 and d ≤ 3
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

def most_frequent_kmers_with_mismatches(Text, k, d):
    freq_map = {}
    n = len(Text)
    for i in range(n - k + 1):
        pattern = Text[i:i + k]
        neighborhood = neighbors(pattern, d)
        for neighbor in neighborhood:
            if neighbor not in freq_map:
                freq_map[neighbor] = 1
            else:
                freq_map[neighbor] += 1

    max_count = 0
    for pattern in freq_map:
        if freq_map[pattern] > max_count:
            max_count = freq_map[pattern]

    freq_patterns = []
    for pattern in freq_map:
        if freq_map[pattern] == max_count:
            freq_patterns.append(pattern)

    return freq_patterns

Text = "CGGTTGGGGGTGTAGCAAGAGATGGTCGAGATGGTCGAGATGGTCGGTGTAGCAAGCTTACTTACGGTTGGGGGTGTAGCAAGTGGCATCAATCGGTTGGGGCTTACTTACGGTTGGGGCTTACTTAAGATGGTCGGTGTAGCAAGCGGTTGGGGGTGTAGCAAGTGGCATCAATGTGTAGCAAGTGGCATCAATCTTACTTACGGTTGGGGCGGTTGGGGCGGTTGGGGTGGCATCAATGTGTAGCAAGCGGTTGGGGCGGTTGGGGGTGTAGCAAGTGGCATCAATCGGTTGGGGCGGTTGGGGAGATGGTCGCGGTTGGGGCTTACTTAAGATGGTCGGTGTAGCAAGAGATGGTCGGTGTAGCAAGAGATGGTCGTGGCATCAATGTGTAGCAAGTGGCATCAATGTGTAGCAAGCTTACTTACTTACTTAAGATGGTCGTGGCATCAATGTGTAGCAAGCTTACTTAGTGTAGCAAGCTTACTTACGGTTGGGGCGGTTGGGGCGGTTGGGGGTGTAGCAAGTGGCATCAATAGATGGTCGGTGTAGCAAGTGGCATCAATCGGTTGGGGAGATGGTCGCTTACTTACGGTTGGGGCTTACTTAAGATGGTCGCGGTTGGGGAGATGGTCGAGATGGTCGAGATGGTCGAGATGGTCGGTGTAGCAAGAGATGGTCGTGGCATCAATTGGCATCAATAGATGGTCGTGGCATCAATAGATGGTCGTGGCATCAATGTGTAGCAAGTGGCATCAATAGATGGTCGGTGTAGCAAGTGGCATCAATCTTACTTACTTACTTACTTACTTACGGTTGGGGTGGCATCAATTGGCATCAATCGGTTGGGGTGGCATCAATCGGTTGGGGGTGTAGCAAGCGGTTGGGGAGATGGTCGGTGTAGCAAGCTTACTTA"
k = 6
d = 3
print(" ".join(most_frequent_kmers_with_mismatches(Text, k, d)))

- How I verified correctness (tests, sample data): Checked with rosalind
  
