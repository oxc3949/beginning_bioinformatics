# AI Use Log
- Tool/model & version: Gemini
- What I asked for: How to turn GC fraction into percentage.
- Snippet of prompt(s): "Turn this fraction into percentage"
- What I changed before committing: added

    if total_length > 0: # Avoid division by zero
        gc_fraction = (g_count + c_count) / total_length
        gc_percentage = gc_fraction * 100
    else:
        gc_fraction = 0
        gc_percentage = 0

    print (seq_record.id)
    print (seq_record.seq)
    print (len(seq_record.seq))
    print (f"GC content: {gc_percentage:.2f}%") # Print GC percentage
    print (f"GC fraction: {gc_fraction:.4f}") # Print GC fraction
    print (seq_record)

- How I verified correctness (tests, sample data): Checked with rosalind
- 
