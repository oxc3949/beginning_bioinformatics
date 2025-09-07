# AI Use Log
- Tool/model & version: Gemini
- What I asked for: How to take the given fasta file to then print each protein and tell me their GC content.
- Snippet of prompt(s): "How can I take edit this current code which identifies each sequence so that it does the same and then also tells me their GC content"
- What I changed before committing: added

  print (gc_fraction(seq_record))

- How I verified correctness (tests, sample data): Checked with rosalind sample data, showed that it needed to be turned into a percentage (meaning multiply by 100)
- 
