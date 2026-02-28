---
paths:
  - "literature/**"
---

# Robust PDF Processing

## The Safe Processing Workflow

**Step 1: Receive PDF**
- User uploads or references a PDF in `literature/`
- Claude DOES NOT attempt to read large PDFs directly

**Step 2: Check PDF Properties**
```bash
pdfinfo paper_name.pdf | grep "Pages:"
ls -lh paper_name.pdf
```

**Step 3: For Large PDFs (>10 pages), Split into Chunks**
```bash
mkdir -p literature/paper_name/

for i in {0..9}; do
  start=$((i*5 + 1))
  end=$(((i+1)*5))
  gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
     -dFirstPage=$start -dLastPage=$end \
     -sOutputFile="literature/paper_name/paper_name_p$(printf '%03d' $start)-$(printf '%03d' $end).pdf" \
     literature/paper_name.pdf 2>/dev/null
done
```

**Step 4: Process Chunks Intelligently**
- Read chunks ONE AT A TIME using the Read tool
- Extract key information from each chunk
- Build understanding progressively

**Step 5: Selective Deep Reading**
- After scanning all chunks, identify the most relevant sections
- Only read those sections in detail
- Skip appendices, references, or less relevant sections unless needed

## Error Handling Protocol

**If a chunk fails to process:**
1. Note the problematic chunk
2. Try splitting into 1-2 page pieces
3. If still failing, skip and document the gap

**If splitting fails:**
1. Check if Ghostscript is installed: `gs --version`
2. Try alternative: `pdftk paper.pdf burst output paper_%03d.pdf`
3. If all else fails, ask user to upload specific page ranges manually
