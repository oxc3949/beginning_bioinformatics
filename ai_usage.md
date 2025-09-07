# AI Use Log
- Tool/model & version: Gemini
- What I asked for: Create a word count and then print said word count
- Snippet of prompt(s): "How to print every word's occurences"
- What I changed before committing: added
  word_counts = {} # Create an empty dictionary to store word counts

for word in line.split():
    # For each word, update its count in the dictionary
    word_counts[word] = word_counts.get(word, 0) + 1

# Print the word counts
for word, count in word_counts.items():
    print(f"{word}: {count}")
- How I verified correctness (tests, sample data): Rosalind checked
- 
