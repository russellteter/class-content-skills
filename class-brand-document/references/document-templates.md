# Class Brand Document - Document Templates

Complete template implementations for different document types.

## Template 1: FAQ Document

### Visual Structure

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│              [DOCUMENT TITLE - 24pt Navy Bold Center]       │
│            [Subtitle - 18pt Purple Regular Center]          │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [TABLE OF CONTENTS - 14pt Purple Bold]                      │
│                                                             │
│ 1. Section Name                                             │
│ 2. Section Name                                             │
│ 3. Section Name                                             │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [1. SECTION HEADING - 14pt Purple Bold]                     │
│                                                             │
│ ┌──────────────────┬────────────────────────────────────┐  │
│ │ Q: Question?     │ Answer text here with full         │  │
│ │ (Purple, lt bg)  │ explanation... (Navy, white bg)    │  │
│ ├──────────────────┼────────────────────────────────────┤  │
│ │ Q: Question 2?   │ Another detailed answer...         │  │
│ └──────────────────┴────────────────────────────────────┘  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Complete Code Example

```python
from docx import Document
from docx.shared import Pt, Inches, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.oxml.ns import nsdecls
from docx.oxml import parse_xml

# Colors
NAVY = RGBColor(10, 24, 73)
PURPLE = RGBColor(71, 57, 231)
WHITE = RGBColor(255, 255, 255)

def create_faq_document():
    doc = Document()

    # Set margins
    section = doc.sections[0]
    section.top_margin = Inches(0.5)
    section.bottom_margin = Inches(0.75)
    section.left_margin = Inches(0.75)
    section.right_margin = Inches(0.75)

    # ===== TITLE BLOCK =====
    # Main Title
    title = doc.add_paragraph()
    title.alignment = WD_ALIGN_PARAGRAPH.CENTER
    title_run = title.add_run("Upgrades to Class's Backend Media")
    title_run.font.name = "Roboto"
    title_run.font.size = Pt(24)
    title_run.font.bold = True
    title_run.font.color.rgb = NAVY

    # Subtitle
    subtitle = doc.add_paragraph()
    subtitle.alignment = WD_ALIGN_PARAGRAPH.CENTER
    sub_run = subtitle.add_run("FAQs For Class Resellers  |  November 2025")
    sub_run.font.name = "Roboto"
    sub_run.font.size = Pt(14)
    sub_run.font.color.rgb = PURPLE
    subtitle.paragraph_format.space_after = Pt(18)

    # ===== TABLE OF CONTENTS =====
    toc_heading = doc.add_paragraph()
    toc_run = toc_heading.add_run("Table of Contents")
    toc_run.font.name = "Roboto"
    toc_run.font.size = Pt(19)
    toc_run.font.bold = True
    toc_run.font.color.rgb = PURPLE

    toc_items = [
        "1. Headline Details For Resellers",
        "2. Positioning & Messaging",
        "3. Technical Questions"
    ]

    for item in toc_items:
        para = doc.add_paragraph()
        run = para.add_run(item)
        run.font.name = "Roboto Light"
        run.font.size = Pt(11)
        run.font.color.rgb = NAVY

    doc.add_paragraph()  # Spacer

    # ===== FAQ SECTION =====
    section_heading = doc.add_paragraph()
    sh_run = section_heading.add_run("1. Headline Details For Resellers")
    sh_run.font.name = "Roboto"
    sh_run.font.size = Pt(14)
    sh_run.font.bold = True
    sh_run.font.color.rgb = PURPLE
    section_heading.paragraph_format.space_before = Pt(18)
    section_heading.paragraph_format.space_after = Pt(12)

    # Create FAQ table
    qa_pairs = [
        ("1 - What happened?", "Class & Zoom have agreed to new partnership terms..."),
        ("2 - Why is this good?", "This partnership solves the media migration challenge...")
    ]

    table = doc.add_table(rows=len(qa_pairs), cols=2)

    for row_idx, (question, answer) in enumerate(qa_pairs):
        row = table.rows[row_idx]

        # Question cell (light purple background, purple text)
        q_cell = row.cells[0]
        q_cell.text = question
        q_shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="F8F7FE"/>')
        q_cell._tc.get_or_add_tcPr().append(q_shading)
        for para in q_cell.paragraphs:
            for run in para.runs:
                run.font.name = "Roboto"
                run.font.size = Pt(10)
                run.font.color.rgb = PURPLE

        # Answer cell (white background, navy text)
        a_cell = row.cells[1]
        a_cell.text = answer
        for para in a_cell.paragraphs:
            for run in para.runs:
                run.font.name = "Roboto Light"
                run.font.size = Pt(10)
                run.font.color.rgb = NAVY

    return doc

# Usage
doc = create_faq_document()
doc.save("Class_FAQ_Example.docx")
```

---

## Template 2: Product Roadmap

### Visual Structure

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│              [Class Technologies - 24pt Navy Bold]          │
│         [Product Roadmap 2026-2027+ - 18pt Purple]          │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [SECTION 1: RELEASED THROUGHOUT 2025 - 14pt Purple Bold]    │
│                                                             │
│ [1.1 During-Class Experience - 12pt Navy Bold]              │
│                                                             │
│ [Breakout Room Enhancements - 10pt Purple Bold]             │
│                                                             │
│ •  Next Gen All Breakout Room View: Description...          │
│ •  Breakout Room Templates: Description...                  │
│ •  Improved Breakout Room Launches: Description...          │
│                                                             │
│ [Session Plans - 10pt Purple Bold]                          │
│                                                             │
│ •  Feature description here...                              │
│ •  Another feature description...                           │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [TABLE - Purple header, zebra data rows]                    │
│ ┌──────────────┬──────────────────┬────────────────────┐   │
│ │ Product      │ Current State    │ Post-Migration     │   │
│ ├──────────────┼──────────────────┼────────────────────┤   │
│ │ Class for    │ Status...        │ New status...      │   │
│ │ Zoom         │                  │                    │   │
│ └──────────────┴──────────────────┴────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Complete Code Example

```python
def create_roadmap_document():
    doc = Document()

    # Set margins
    section = doc.sections[0]
    section.top_margin = Inches(0.75)
    section.bottom_margin = Inches(0.75)
    section.left_margin = Inches(0.75)
    section.right_margin = Inches(0.75)

    # ===== TITLE BLOCK =====
    title = doc.add_paragraph()
    title.alignment = WD_ALIGN_PARAGRAPH.CENTER
    title_run = title.add_run("Class Technologies")
    title_run.font.name = "Roboto"
    title_run.font.size = Pt(24)
    title_run.font.bold = True
    title_run.font.color.rgb = NAVY

    subtitle = doc.add_paragraph()
    subtitle.alignment = WD_ALIGN_PARAGRAPH.CENTER
    sub_run = subtitle.add_run("Product Roadmap 2026-2027+")
    sub_run.font.name = "Roboto"
    sub_run.font.size = Pt(18)
    sub_run.font.color.rgb = PURPLE
    subtitle.paragraph_format.space_after = Pt(24)

    # ===== SECTION 1 =====
    h1 = doc.add_paragraph()
    h1_run = h1.add_run("SECTION 1: RELEASED THROUGHOUT 2025")
    h1_run.font.name = "Roboto"
    h1_run.font.size = Pt(14)
    h1_run.font.bold = True
    h1_run.font.color.rgb = PURPLE
    h1.paragraph_format.space_before = Pt(18)
    h1.paragraph_format.space_after = Pt(12)

    # ===== SUBSECTION 1.1 =====
    h2 = doc.add_paragraph()
    h2_run = h2.add_run("1.1 During-Class Experience")
    h2_run.font.name = "Roboto"
    h2_run.font.size = Pt(12)
    h2_run.font.bold = True
    h2_run.font.color.rgb = NAVY
    h2.paragraph_format.space_before = Pt(12)
    h2.paragraph_format.space_after = Pt(6)

    # ===== FEATURE GROUP (H3) =====
    h3 = doc.add_paragraph()
    h3_run = h3.add_run("Breakout Room Enhancements")
    h3_run.font.name = "Roboto"
    h3_run.font.size = Pt(10)
    h3_run.font.bold = True
    h3_run.font.color.rgb = PURPLE
    h3.paragraph_format.space_before = Pt(10)
    h3.paragraph_format.space_after = Pt(4)

    # ===== BULLET POINTS =====
    bullets = [
        "Next Gen All Breakout Room View: Facilitators can view conversation transcripts and activity from all breakout rooms simultaneously.",
        "Breakout Room Templates: Pre-configure settings and room assignments for the most common breakout configurations.",
        "Improved Breakout Room Launches: Single-action creation, user picker for assignments, and streamlined workflow."
    ]

    for bullet_text in bullets:
        para = doc.add_paragraph()
        # Add bullet character in purple
        bullet_run = para.add_run("•  ")
        bullet_run.font.name = "Roboto"
        bullet_run.font.size = Pt(9)
        bullet_run.font.color.rgb = PURPLE

        # Add text in navy
        text_run = para.add_run(bullet_text)
        text_run.font.name = "Roboto Light"
        text_run.font.size = Pt(9)
        text_run.font.color.rgb = NAVY

    # ===== COMPARISON TABLE =====
    doc.add_paragraph()

    table = doc.add_table(rows=4, cols=3)

    # Header row
    headers = ["Product", "Current State", "Post-Migration (Q1 2026)"]
    header_row = table.rows[0]
    for idx, header_text in enumerate(headers):
        cell = header_row.cells[idx]
        cell.text = header_text

        # Purple background
        shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="4739E7"/>')
        cell._tc.get_or_add_tcPr().append(shading)

        for para in cell.paragraphs:
            para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            for run in para.runs:
                run.font.name = "Roboto"
                run.font.size = Pt(10)
                run.font.bold = True
                run.font.color.rgb = WHITE

    # Data rows
    data = [
        ["Class for Zoom", "Zoom SDK video", "Microsoft Azure video"],
        ["Class for Teams", "Microsoft Teams video", "Microsoft Azure video"],
        ["Class Studio", "AWS video", "Microsoft Azure video"]
    ]

    for row_idx, row_data in enumerate(data):
        row = table.rows[row_idx + 1]
        fill = "FFFFFF" if row_idx % 2 == 0 else "F0F0F5"

        for col_idx, cell_value in enumerate(row_data):
            cell = row.cells[col_idx]
            cell.text = cell_value

            shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="{fill}"/>')
            cell._tc.get_or_add_tcPr().append(shading)

            for para in cell.paragraphs:
                # First column bold
                for run in para.runs:
                    run.font.name = "Roboto" if col_idx == 0 else "Roboto Light"
                    run.font.size = Pt(10)
                    run.font.bold = (col_idx == 0)
                    run.font.color.rgb = NAVY

    return doc
```

---

## Template 3: Pricing Workbook / Schedule

### Visual Structure

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│         [Class Pricing Workbook - 16pt Navy Bold]           │
│    [Schedule B Reference Document... - 10pt Navy Light]     │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [Platform Comparison: Zoom vs. Teams - 14pt Purple Bold]    │
│                                                             │
│ ┌──────────────┬───────────────────┬────────────────────┐  │
│ │ Feature      │ Class for Zoom    │ Class for Teams    │  │
│ │ (lt purple)  │ (lt purple)       │ (lt purple)        │  │
│ ├──────────────┼───────────────────┼────────────────────┤  │
│ │ Video        │ Azure Media       │ Azure Media        │  │
│ │ Recording    │ ✓ Included        │ ✓ Included         │  │
│ └──────────────┴───────────────────┴────────────────────┘  │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [1. Corporate & Government Pricing - 14pt Purple Bold]      │
│                                                             │
│ Applies to: Commercial enterprises, state/local...          │
│ (10pt Roboto Light Navy)                                    │
│                                                             │
│ [1.1 Learner Fees (Annual) - 12pt Navy Bold]                │
│                                                             │
│ Class for Zoom & Class for Teams — Tiered by total...       │
│                                                             │
│ ┌──────────────┬───────────────────┬────────────────────┐  │
│ │ Tier         │ Learner Range     │ Annual Fee         │  │
│ ├──────────────┼───────────────────┼────────────────────┤  │
│ │ 1            │ 1 - 500           │ $12,000            │  │
│ │ 2            │ 501 - 2,000       │ $25,000            │  │
│ └──────────────┴───────────────────┴────────────────────┘  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Complete Code Example

```python
def create_pricing_document():
    doc = Document()

    # Set margins
    section = doc.sections[0]
    section.top_margin = Inches(0.5)
    section.bottom_margin = Inches(0.75)
    section.left_margin = Inches(0.75)
    section.right_margin = Inches(0.75)

    # ===== TITLE BLOCK =====
    title = doc.add_paragraph()
    title_run = title.add_run("Class Pricing Workbook")
    title_run.font.name = "Roboto"
    title_run.font.size = Pt(16)
    title_run.font.bold = True
    title_run.font.color.rgb = NAVY

    subtitle = doc.add_paragraph()
    sub_run = subtitle.add_run("Schedule B Reference Document for Reseller Agreements")
    sub_run.font.name = "Roboto Light"
    sub_run.font.size = Pt(10)
    sub_run.font.color.rgb = NAVY
    subtitle.paragraph_format.space_after = Pt(18)

    # ===== COMPARISON TABLE =====
    comparison_heading = doc.add_paragraph()
    ch_run = comparison_heading.add_run("Platform Comparison: Zoom vs. Teams")
    ch_run.font.name = "Roboto"
    ch_run.font.size = Pt(14)
    ch_run.font.bold = True
    ch_run.font.color.rgb = PURPLE
    comparison_heading.paragraph_format.space_after = Pt(12)

    # Create comparison table with light purple headers
    table = doc.add_table(rows=5, cols=3)
    headers = ["Feature", "Class for Zoom", "Class for Teams"]
    data = [
        ["Video Infrastructure", "Azure Media Services", "Azure Media Services"],
        ["Recording Storage", "Included", "Included"],
        ["Max Participants", "1,000", "1,000"],
        ["Integration", "Zoom Marketplace", "Teams App Store"]
    ]

    # Style header row (light purple)
    header_row = table.rows[0]
    for idx, header_text in enumerate(headers):
        cell = header_row.cells[idx]
        cell.text = header_text
        shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="EBE9FC"/>')
        cell._tc.get_or_add_tcPr().append(shading)
        for para in cell.paragraphs:
            para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            for run in para.runs:
                run.font.name = "Roboto"
                run.font.size = Pt(10)
                run.font.bold = True
                run.font.color.rgb = NAVY

    # Style data rows
    for row_idx, row_data in enumerate(data):
        row = table.rows[row_idx + 1]
        for col_idx, cell_value in enumerate(row_data):
            cell = row.cells[col_idx]
            cell.text = cell_value
            for para in cell.paragraphs:
                para.alignment = WD_ALIGN_PARAGRAPH.CENTER
                for run in para.runs:
                    run.font.name = "Roboto Light"
                    run.font.size = Pt(10)
                    run.font.color.rgb = NAVY

    doc.add_paragraph()

    # ===== PRICING SECTION =====
    pricing_heading = doc.add_paragraph()
    ph_run = pricing_heading.add_run("1. Corporate & Government Pricing")
    ph_run.font.name = "Roboto"
    ph_run.font.size = Pt(14)
    ph_run.font.bold = True
    ph_run.font.color.rgb = PURPLE
    pricing_heading.paragraph_format.space_before = Pt(18)
    pricing_heading.paragraph_format.space_after = Pt(6)

    applies_to = doc.add_paragraph()
    at_run = applies_to.add_run("Applies to: Commercial enterprises, state/local government, non-FedRAMP federal agencies")
    at_run.font.name = "Roboto Light"
    at_run.font.size = Pt(10)
    at_run.font.color.rgb = NAVY
    applies_to.paragraph_format.space_after = Pt(12)

    # ===== SUBSECTION =====
    learner_heading = doc.add_paragraph()
    lh_run = learner_heading.add_run("1.1 Learner Fees (Annual)")
    lh_run.font.name = "Roboto"
    lh_run.font.size = Pt(12)
    lh_run.font.bold = True
    lh_run.font.color.rgb = NAVY
    learner_heading.paragraph_format.space_after = Pt(6)

    tier_desc = doc.add_paragraph()
    td_run = tier_desc.add_run("Class for Zoom & Class for Teams — Tiered by total registered learners")
    td_run.font.name = "Roboto Light"
    td_run.font.size = Pt(10)
    td_run.font.color.rgb = NAVY
    tier_desc.paragraph_format.space_after = Pt(8)

    # ===== PRICING TABLE =====
    price_table = doc.add_table(rows=6, cols=3)
    price_headers = ["Tier", "Learner Range", "Annual Fee"]
    price_data = [
        ["1", "1 - 500", "$12,000"],
        ["2", "501 - 2,000", "$25,000"],
        ["3", "2,001 - 5,000", "$50,000"],
        ["4", "5,001 - 10,000", "$85,000"],
        ["5", "10,001+", "Custom"]
    ]

    # Light purple header
    header_row = price_table.rows[0]
    for idx, header_text in enumerate(price_headers):
        cell = header_row.cells[idx]
        cell.text = header_text
        shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="EBE9FC"/>')
        cell._tc.get_or_add_tcPr().append(shading)
        for para in cell.paragraphs:
            para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            for run in para.runs:
                run.font.name = "Roboto"
                run.font.size = Pt(10)
                run.font.bold = True
                run.font.color.rgb = NAVY

    # Data rows
    for row_idx, row_data in enumerate(price_data):
        row = price_table.rows[row_idx + 1]
        for col_idx, cell_value in enumerate(row_data):
            cell = row.cells[col_idx]
            cell.text = cell_value
            for para in cell.paragraphs:
                para.alignment = WD_ALIGN_PARAGRAPH.CENTER
                for run in para.runs:
                    run.font.name = "Roboto Light"
                    run.font.size = Pt(10)
                    run.font.color.rgb = NAVY

    return doc
```

---

## Template 4: Standard Report

### Visual Structure

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│              [Report Title - 24pt Navy Bold Center]         │
│              [Date | Context - 14pt Purple Center]          │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [Executive Summary - 14pt Purple Bold]                      │
│                                                             │
│ Body text in Roboto Light, 10pt, Navy. Multiple sentences   │
│ providing overview of the report content and key findings.  │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [Key Findings - 14pt Purple Bold]                           │
│                                                             │
│ [Finding Category 1 - 12pt Navy Bold]                       │
│                                                             │
│ Explanation text in Roboto Light...                         │
│                                                             │
│ •  Bullet point with supporting detail                      │
│ •  Another bullet point                                     │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ [Data Summary - 14pt Purple Bold]                           │
│                                                             │
│ ┌──────────────┬──────────────────┬────────────────────┐   │
│ │ Metric       │ Q3 2025          │ Q4 2025            │   │
│ ├──────────────┼──────────────────┼────────────────────┤   │
│ │ Users        │ 15,000           │ 18,500             │   │
│ │ Sessions     │ 45,000           │ 52,000             │   │
│ └──────────────┴──────────────────┴────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Complete Code Example

```python
def create_report_document(title, date, sections):
    """Create a standard Class-branded report.

    Args:
        title: Report title
        date: Report date or context
        sections: List of dicts with 'heading', 'content', 'bullets', 'table'
    """
    doc = Document()

    # Set margins
    section = doc.sections[0]
    section.top_margin = Inches(0.75)
    section.bottom_margin = Inches(0.75)
    section.left_margin = Inches(0.75)
    section.right_margin = Inches(0.75)

    # ===== TITLE BLOCK =====
    title_para = doc.add_paragraph()
    title_para.alignment = WD_ALIGN_PARAGRAPH.CENTER
    title_run = title_para.add_run(title)
    title_run.font.name = "Roboto"
    title_run.font.size = Pt(24)
    title_run.font.bold = True
    title_run.font.color.rgb = NAVY

    date_para = doc.add_paragraph()
    date_para.alignment = WD_ALIGN_PARAGRAPH.CENTER
    date_run = date_para.add_run(date)
    date_run.font.name = "Roboto"
    date_run.font.size = Pt(14)
    date_run.font.color.rgb = PURPLE
    date_para.paragraph_format.space_after = Pt(24)

    # ===== SECTIONS =====
    for sect in sections:
        # Section heading (H1)
        h1 = doc.add_paragraph()
        h1_run = h1.add_run(sect['heading'])
        h1_run.font.name = "Roboto"
        h1_run.font.size = Pt(14)
        h1_run.font.bold = True
        h1_run.font.color.rgb = PURPLE
        h1.paragraph_format.space_before = Pt(18)
        h1.paragraph_format.space_after = Pt(12)

        # Content paragraphs
        if 'content' in sect:
            for para_text in sect['content']:
                para = doc.add_paragraph()
                run = para.add_run(para_text)
                run.font.name = "Roboto Light"
                run.font.size = Pt(10)
                run.font.color.rgb = NAVY
                para.paragraph_format.line_spacing = 1.15
                para.paragraph_format.space_after = Pt(6)

        # Subsections
        if 'subsections' in sect:
            for subsect in sect['subsections']:
                # Subsection heading (H2)
                h2 = doc.add_paragraph()
                h2_run = h2.add_run(subsect['heading'])
                h2_run.font.name = "Roboto"
                h2_run.font.size = Pt(12)
                h2_run.font.bold = True
                h2_run.font.color.rgb = NAVY
                h2.paragraph_format.space_before = Pt(12)
                h2.paragraph_format.space_after = Pt(6)

                if 'content' in subsect:
                    para = doc.add_paragraph()
                    run = para.add_run(subsect['content'])
                    run.font.name = "Roboto Light"
                    run.font.size = Pt(10)
                    run.font.color.rgb = NAVY

        # Bullet points
        if 'bullets' in sect:
            for bullet_text in sect['bullets']:
                para = doc.add_paragraph()
                bullet_run = para.add_run("•  ")
                bullet_run.font.name = "Roboto"
                bullet_run.font.size = Pt(9)
                bullet_run.font.color.rgb = PURPLE

                text_run = para.add_run(bullet_text)
                text_run.font.name = "Roboto Light"
                text_run.font.size = Pt(9)
                text_run.font.color.rgb = NAVY

        # Table
        if 'table' in sect:
            doc.add_paragraph()
            headers = sect['table']['headers']
            data = sect['table']['data']

            table = doc.add_table(rows=1 + len(data), cols=len(headers))

            # Purple header
            header_row = table.rows[0]
            for idx, header_text in enumerate(headers):
                cell = header_row.cells[idx]
                cell.text = header_text
                shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="4739E7"/>')
                cell._tc.get_or_add_tcPr().append(shading)
                for para in cell.paragraphs:
                    para.alignment = WD_ALIGN_PARAGRAPH.CENTER
                    for run in para.runs:
                        run.font.name = "Roboto"
                        run.font.size = Pt(10)
                        run.font.bold = True
                        run.font.color.rgb = WHITE

            # Zebra data rows
            for row_idx, row_data in enumerate(data):
                row = table.rows[row_idx + 1]
                fill = "FFFFFF" if row_idx % 2 == 0 else "F0F0F5"
                for col_idx, cell_value in enumerate(row_data):
                    cell = row.cells[col_idx]
                    cell.text = str(cell_value)
                    shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="{fill}"/>')
                    cell._tc.get_or_add_tcPr().append(shading)
                    for para in cell.paragraphs:
                        para.alignment = WD_ALIGN_PARAGRAPH.CENTER
                        for run in para.runs:
                            run.font.name = "Roboto Light"
                            run.font.size = Pt(10)
                            run.font.color.rgb = NAVY

    return doc


# Example usage
sections = [
    {
        'heading': 'Executive Summary',
        'content': [
            'This report provides an overview of Q4 2025 performance metrics for Class Technologies products.',
            'Key findings indicate strong growth in user adoption and session activity.'
        ]
    },
    {
        'heading': 'Key Findings',
        'subsections': [
            {
                'heading': 'User Growth',
                'content': 'Active users increased by 23% compared to the previous quarter.'
            }
        ],
        'bullets': [
            'Class for Zoom: 12,500 active users (+18%)',
            'Class for Teams: 6,000 active users (+31%)',
            'Class Studio: 2,500 active users (+15%)'
        ]
    },
    {
        'heading': 'Data Summary',
        'table': {
            'headers': ['Metric', 'Q3 2025', 'Q4 2025', 'Change'],
            'data': [
                ['Active Users', '15,000', '18,500', '+23%'],
                ['Sessions', '45,000', '52,000', '+16%'],
                ['Avg Session Length', '42 min', '45 min', '+7%']
            ]
        }
    }
]

doc = create_report_document(
    "Q4 2025 Performance Report",
    "January 2026 | Class Technologies",
    sections
)
doc.save("Class_Q4_Report.docx")
```
