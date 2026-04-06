---
name: class-brand-document
description: Create professional, Class Technologies branded Word documents (.docx) and PDFs with comprehensive styling. Includes complete typography hierarchy, table styles, FAQ layouts, and document templates following Class brand guidelines.
---

# Class Brand Document

Create professional, polished Word documents and PDFs using Class Technologies brand standards. This skill provides complete typography hierarchy, table styling, and document templates for reports, FAQs, roadmaps, pricing documents, and more.

## Mandatory Trigger Conditions

**ALWAYS use this skill when:**
- Creating Word documents (.docx)
- Generating PDFs
- Writing reports, FAQs, briefs, or guides
- Any professional document for Class

**Trigger keywords:** document, report, FAQ, brief, guide, Word, .docx, PDF, write up

## Brand Color Palette

| Color | Hex | RGB | Usage |
|-------|-----|-----|-------|
| Navy | `#0A1849` | `(10, 24, 73)` | Primary text, titles, body copy |
| Purple | `#4739E7` | `(71, 57, 231)` | Section headings, accents, links, table headers |
| Gold | `#FFBA00` | `(255, 186, 0)` | Accent highlights (use sparingly) |
| White | `#FFFFFF` | `(255, 255, 255)` | Backgrounds, text on dark fills |
| Light Purple | `#EBE9FC` | `(235, 233, 252)` | Table header backgrounds (alt style) |
| Light Gray | `#F0F0F5` | `(240, 240, 245)` | Table row striping |
| FAQ Purple BG | `#F8F7FE` | `(248, 247, 254)` | FAQ question cell backgrounds |

**Critical Rule:** Never use black (#000000) - always use Navy (#0A1849).

## Typography System

### Font Families
- **Primary:** Roboto (titles, headings, bold text, emphasis)
- **Body:** Roboto Light (body text, paragraphs, descriptions)

### Complete Hierarchy

| Element | Font | Size | Weight | Color | Spacing |
|---------|------|------|--------|-------|---------|
| Document Title | Roboto | 24pt | Bold | Navy | Center aligned |
| Subtitle | Roboto | 18pt | Regular | Purple | Center aligned |
| Section Heading (H1) | Roboto | 14pt | Bold | Purple | 18pt before, 12pt after |
| Subsection (H2) | Roboto | 12pt | Bold | Navy | 12pt before, 6pt after |
| Sub-subsection (H3) | Roboto | 10pt | Bold | Purple | 10pt before, 4pt after |
| Body Text | Roboto Light | 10pt | Regular | Navy | 1.15 line spacing |
| Bullet Points | Roboto Light | 9-10pt | Regular | Navy | Purple bullet character |
| Captions | Roboto Light | 9pt | Italic | Navy | 6pt after |
| Table Text | Roboto/Roboto Light | 10pt | Varies | Navy | Center or left aligned |

### Alternative Sizes (for dense documents)
For pricing workbooks or detailed technical documents:
- Body: 10pt
- Bullets: 9pt
- Table cells: 9-10pt

## Page Layout

```python
# Standard Page Margins
TOP_MARGIN = Inches(0.5)      # or Inches(0.75) for reports
BOTTOM_MARGIN = Inches(0.75)
LEFT_MARGIN = Inches(0.75)
RIGHT_MARGIN = Inches(0.75)

# Paragraph Spacing
LINE_SPACING = 1.15           # Standard for body text
SPACE_AFTER_PARA = Pt(6)      # Between paragraphs
SPACE_AFTER_HEADING = Pt(12)  # After section headings
```

## Table Styling

### Style 1: Purple Header (Primary)
Use for data tables, comparison tables, feature lists.

```python
# Header Row
HEADER_FILL = "#4739E7"       # Purple background
HEADER_TEXT = "#FFFFFF"       # White text
HEADER_FONT = "Roboto"        # Bold, 10pt

# Data Rows
DATA_FILL_ODD = "#FFFFFF"     # White
DATA_FILL_EVEN = "#F0F0F5"    # Light gray (zebra stripe)
DATA_TEXT = "#0A1849"         # Navy
DATA_FONT = "Roboto Light"    # Regular, 10pt

# Borders
BORDER_COLOR = "#E0E0E0"      # Light gray, thin
```

### Style 2: Light Purple Header (Secondary)
Use for pricing tables, detailed specifications.

```python
# Header Row
HEADER_FILL = "#EBE9FC"       # Light purple background
HEADER_TEXT = "#0A1849"       # Navy text, Bold

# Data Rows
DATA_FILL = "#FFFFFF"         # White
DATA_TEXT = "#0A1849"         # Navy
```

### Style 3: FAQ/Q&A Table
Use for FAQ documents, Q&A layouts.

```python
# Question Column (Left)
Q_FILL = "#F8F7FE"            # Very light purple
Q_TEXT = "#4739E7"            # Purple text
Q_FONT = "Roboto"             # Bold or regular

# Answer Column (Right)
A_FILL = "#FFFFFF"            # White
A_TEXT = "#0A1849"            # Navy text
A_FONT = "Roboto Light"       # Regular
```

## Document Templates

### 1. FAQ Document

```
[HEADER BAR - Optional Navy background with title]

[DOCUMENT TITLE]
Document Title Here
Subtitle or Date | Additional Context
═══════════════════════════════════════

[TABLE OF CONTENTS - If >5 sections]
Table of Contents
────────────────
1. Section Name
2. Section Name
...

[SECTION HEADING - H1, Purple, 14pt Bold]
1. Section Title

[Q&A TABLE or BULLET FORMAT]
Q: Question text here?
A: Answer text with complete explanation...

[REPEAT FOR EACH SECTION]
```

### 2. Product Roadmap

```
[TITLE BLOCK]
Class Technologies                    ← 24pt, Bold, Navy
Product Roadmap 2026-2027+           ← 18pt, Regular, Purple

[SECTION - H1]
SECTION 1: RELEASED THROUGHOUT 2025  ← 14pt, Bold, Purple, ALL CAPS

[SUBSECTION - H2]
1.1 Feature Category                 ← 12pt, Bold, Navy

[FEATURE GROUP - H3]
Feature Name                         ← 10pt, Bold, Purple

[BULLET POINTS]
•  Feature description text here...  ← 9pt, Roboto Light, Navy
                                       (Purple bullet, Navy text)

[TABLE - If comparing features]
| Product | Current State | Future State |
Purple header, zebra striped data rows
```

### 3. Pricing Workbook / Schedule

```
[TITLE]
Class Pricing Workbook               ← 16pt, Bold, Navy
Schedule B Reference Document...     ← 10pt, Roboto Light, Navy

[SECTION HEADING]
1. Corporate & Government Pricing    ← 14pt, Bold, Purple

[SUBSECTION]
1.1 Learner Fees (Annual)           ← 12pt, Bold, Navy

[DESCRIPTION]
Class for Zoom & Teams — Tiered...  ← 10pt, Roboto Light, Navy

[PRICING TABLE]
| Tier | Learner Range | Annual Fee |
Light purple header (#EBE9FC), white data rows
```

### 4. Standard Report/Brief

```
[CENTERED TITLE]
Report Title                         ← 24pt, Bold, Navy, Centered
Subtitle or Date                     ← 14pt, Regular, Purple, Centered

[SECTION]
Executive Summary                    ← 14pt, Bold, Purple

Body text in Roboto Light, 10pt, Navy...

[SUBSECTION]
Key Findings                         ← 12pt, Bold, Navy

• Bullet point one                   ← 10pt, Roboto Light, Navy
• Bullet point two
```

## Implementation Code

### Quick Start (Python-docx)

```python
from docx import Document
from docx.shared import Pt, Inches, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.oxml.ns import qn
from docx.oxml import OxmlElement

# Brand Colors
NAVY = RGBColor(10, 24, 73)        # #0A1849
PURPLE = RGBColor(71, 57, 231)     # #4739E7
WHITE = RGBColor(255, 255, 255)    # #FFFFFF

def create_class_document(title, subtitle=None):
    """Create a new Class-branded document."""
    doc = Document()

    # Set page margins
    section = doc.sections[0]
    section.top_margin = Inches(0.5)
    section.bottom_margin = Inches(0.75)
    section.left_margin = Inches(0.75)
    section.right_margin = Inches(0.75)

    # Add title
    add_title(doc, title)
    if subtitle:
        add_subtitle(doc, subtitle)

    return doc

def add_title(doc, text):
    """Add document title (24pt, Bold, Navy, Centered)."""
    para = doc.add_paragraph()
    para.alignment = WD_ALIGN_PARAGRAPH.CENTER
    run = para.add_run(text)
    run.font.name = "Roboto"
    run.font.size = Pt(24)
    run.font.bold = True
    run.font.color.rgb = NAVY
    para.paragraph_format.space_after = Pt(6)

def add_subtitle(doc, text):
    """Add subtitle (18pt, Regular, Purple, Centered)."""
    para = doc.add_paragraph()
    para.alignment = WD_ALIGN_PARAGRAPH.CENTER
    run = para.add_run(text)
    run.font.name = "Roboto"
    run.font.size = Pt(18)
    run.font.color.rgb = PURPLE
    para.paragraph_format.space_after = Pt(18)

def add_section_heading(doc, text):
    """Add H1 section heading (14pt, Bold, Purple)."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    run.font.name = "Roboto"
    run.font.size = Pt(14)
    run.font.bold = True
    run.font.color.rgb = PURPLE
    para.paragraph_format.space_before = Pt(18)
    para.paragraph_format.space_after = Pt(12)

def add_subsection_heading(doc, text):
    """Add H2 subsection heading (12pt, Bold, Navy)."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    run.font.name = "Roboto"
    run.font.size = Pt(12)
    run.font.bold = True
    run.font.color.rgb = NAVY
    para.paragraph_format.space_before = Pt(12)
    para.paragraph_format.space_after = Pt(6)

def add_h3_heading(doc, text):
    """Add H3 heading (10pt, Bold, Purple)."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    run.font.name = "Roboto"
    run.font.size = Pt(10)
    run.font.bold = True
    run.font.color.rgb = PURPLE
    para.paragraph_format.space_before = Pt(10)
    para.paragraph_format.space_after = Pt(4)

def add_body_text(doc, text):
    """Add body paragraph (10pt, Roboto Light, Navy)."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    run.font.name = "Roboto Light"
    run.font.size = Pt(10)
    run.font.color.rgb = NAVY
    para.paragraph_format.line_spacing = 1.15
    para.paragraph_format.space_after = Pt(6)

def add_bullet_point(doc, text, level=0):
    """Add bullet point (9pt, Roboto Light, Navy)."""
    para = doc.add_paragraph(style='List Bullet')
    run = para.add_run(text)
    run.font.name = "Roboto Light"
    run.font.size = Pt(9)
    run.font.color.rgb = NAVY
    para.paragraph_format.left_indent = Inches(0.25 * (level + 1))
```

### Table Creation

```python
from docx.oxml.ns import nsdecls
from docx.oxml import parse_xml

def add_class_table(doc, headers, data, style="purple"):
    """Create a Class-branded table."""
    table = doc.add_table(rows=1 + len(data), cols=len(headers))

    # Header row styling
    header_row = table.rows[0]
    for idx, header_text in enumerate(headers):
        cell = header_row.cells[idx]
        cell.text = header_text

        # Set header cell shading
        if style == "purple":
            set_cell_shading(cell, "4739E7")  # Purple
            set_cell_text_style(cell, "Roboto", 10, True, "FFFFFF")
        else:  # light purple
            set_cell_shading(cell, "EBE9FC")
            set_cell_text_style(cell, "Roboto", 10, True, "0A1849")

    # Data rows with zebra striping
    for row_idx, row_data in enumerate(data):
        row = table.rows[row_idx + 1]
        fill = "FFFFFF" if row_idx % 2 == 0 else "F0F0F5"

        for col_idx, cell_text in enumerate(row_data):
            cell = row.cells[col_idx]
            cell.text = str(cell_text)
            set_cell_shading(cell, fill)
            set_cell_text_style(cell, "Roboto Light", 10, False, "0A1849")

    return table

def set_cell_shading(cell, color_hex):
    """Set cell background color."""
    shading = parse_xml(
        f'<w:shd {nsdecls("w")} w:fill="{color_hex}"/>'
    )
    cell._tc.get_or_add_tcPr().append(shading)

def set_cell_text_style(cell, font_name, size, bold, color_hex):
    """Style text in a cell."""
    for para in cell.paragraphs:
        for run in para.runs:
            run.font.name = font_name
            run.font.size = Pt(size)
            run.font.bold = bold
            r, g, b = int(color_hex[0:2], 16), int(color_hex[2:4], 16), int(color_hex[4:6], 16)
            run.font.color.rgb = RGBColor(r, g, b)
```

## Quality Checklist

Before delivering any document, verify:

- [ ] All text uses Navy (#0A1849) or Purple (#4739E7) - NO black text
- [ ] Document title: Roboto 24pt Bold Navy, centered
- [ ] Subtitle (if any): Roboto 18pt Purple, centered
- [ ] Section headings (H1): Roboto 14pt Bold Purple
- [ ] Subsections (H2): Roboto 12pt Bold Navy
- [ ] Body text: Roboto Light 10pt Navy
- [ ] Line spacing: 1.15 throughout
- [ ] Margins: 0.5-0.75 inches
- [ ] Tables use brand styling (purple or light purple headers)
- [ ] Bullet points: Purple bullets, Navy text
- [ ] No default Word styling remains

## Critical Rules

### ALWAYS
1. Use Navy (#0A1849) for all text - never black
2. Use Purple (#4739E7) for section headings and accents
3. Use Roboto/Roboto Light fonts only
4. Apply proper typography hierarchy
5. Style tables with brand colors
6. Set proper margins and spacing

### NEVER
1. Use black (#000000) text
2. Use default Word fonts (Calibri, Times New Roman)
3. Leave tables unstyled
4. Skip the title hierarchy
5. Use colors outside the brand palette
6. Center-align body text (only titles/subtitles)

## File Naming Convention

```
Class_[DocumentType]_[Topic]_[Date].docx
```

Examples:
- `Class_FAQ_Media_Backend_Q4_2025.docx`
- `Class_Roadmap_2026-2027.docx`
- `Class_Pricing_Schedule_B.docx`

## Additional Resources

See the `/references` folder for:
- `style-guide.md` - Complete python-docx code reference
- `document-templates.md` - Full template implementations
- `/scripts/class_doc_styles.py` - Importable Python module
