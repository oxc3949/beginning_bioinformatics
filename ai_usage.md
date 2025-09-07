# AI Use Log
- Tool/model & version: Gemini
- What I asked for: How to take a dictionary and turn it into a fasta file
- Snippet of prompt(s): "How can I take this current dictionary (sequences) and save it as a fasta file?"
- What I changed before committing: added

with open("sequences.fasta", "w") as fasta_file:
    for header, sequence in sequences.items():
        fasta_file.write(f">{header}\n{sequence}\n")

print("FASTA file 'sequences.fasta' created successfully.")

- How I verified correctness (tests, sample data): Checked fasta file with example provided in word doc.
- 
