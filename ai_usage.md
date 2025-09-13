# AI Use Log
- Tool/model & version: ChatGPT
- What I asked for: Provide code for the following problem.
- Snippet of prompt(s):
"Give me the code (don't run any code) for the following problem:
Given: A DNA string Text and an integer k.
Return: All most frequent k-mers in Text (in any order)."
- What I changed before committing: added

def most_frequent_kmers(Text, k):
    freq_map = {}
    max_count = 0
    result = []

    for i in range(len(Text) - k + 1):
        pattern = Text[i:i + k]
        if pattern not in freq_map:
            freq_map[pattern] = 1
        else:
            freq_map[pattern] += 1

        if freq_map[pattern] > max_count:
            max_count = freq_map[pattern]

    for pattern in freq_map:
        if freq_map[pattern] == max_count:
            result.append(pattern)

    return result


Text = "TEXT"
k = INTEGER

print(most_frequent_kmers(Text, k))


- How I verified correctness (tests, sample data): Checked with rosalind
- 
