# Class Brand Document - Complete Style Guide

This reference contains all python-docx style definitions and helper code for creating Class-branded Word documents.

## Table of Contents

1. [Color Constants](#color-constants)
2. [Font Definitions](#font-definitions)
3. [Paragraph Styles](#paragraph-styles)
4. [Table Styles](#table-styles)
5. [Helper Functions](#helper-functions)
6. [Complete Examples](#complete-examples)

---

## Color Constants

```python
from docx.shared import RGBColor

# Primary Brand Colors
NAVY = RGBColor(10, 24, 73)        # #0A1849 - Primary text, titles
PURPLE = RGBColor(71, 57, 231)     # #4739E7 - Section headings, accents
GOLD = RGBColor(255, 186, 0)       # #FFBA00 - Accent (use sparingly)
WHITE = RGBColor(255, 255, 255)    # #FFFFFF - Text on dark backgrounds

# Background/Fill Colors (hex strings for XML)
NAVY_HEX = "0A1849"
PURPLE_HEX = "4739E7"
LIGHT_PURPLE_HEX = "EBE9FC"        # Table header alt style
LIGHT_GRAY_HEX = "F0F0F5"          # Zebra stripe rows
FAQ_BG_HEX = "F8F7FE"              # FAQ question cells
WHITE_HEX = "FFFFFF"
BORDER_GRAY_HEX = "E0E0E0"         # Table borders
```

---

## Font Definitions

### Typography Hierarchy

```python
from docx.shared import Pt

# Document Title
TITLE_FONT = "Roboto"
TITLE_SIZE = Pt(24)
TITLE_BOLD = True
TITLE_COLOR = NAVY

# Subtitle
SUBTITLE_FONT = "Roboto"
SUBTITLE_SIZE = Pt(18)
SUBTITLE_BOLD = False
SUBTITLE_COLOR = PURPLE

# Section Heading (H1)
H1_FONT = "Roboto"
H1_SIZE = Pt(14)
H1_BOLD = True
H1_COLOR = PURPLE

# Subsection Heading (H2)
H2_FONT = "Roboto"
H2_SIZE = Pt(12)
H2_BOLD = True
H2_COLOR = NAVY

# Sub-subsection Heading (H3)
H3_FONT = "Roboto"
H3_SIZE = Pt(10)
H3_BOLD = True
H3_COLOR = PURPLE

# Body Text
BODY_FONT = "Roboto Light"
BODY_SIZE = Pt(10)
BODY_BOLD = False
BODY_COLOR = NAVY

# Bullet Points
BULLET_FONT = "Roboto Light"
BULLET_SIZE = Pt(9)
BULLET_COLOR = NAVY

# Table Header
TABLE_HEADER_FONT = "Roboto"
TABLE_HEADER_SIZE = Pt(10)
TABLE_HEADER_BOLD = True

# Table Data
TABLE_DATA_FONT = "Roboto Light"
TABLE_DATA_SIZE = Pt(10)
TABLE_DATA_BOLD = False
```

---

## Paragraph Styles

### Spacing Constants

```python
from docx.shared import Pt, Inches

# Page Margins
MARGIN_TOP = Inches(0.5)
MARGIN_BOTTOM = Inches(0.75)
MARGIN_LEFT = Inches(0.75)
MARGIN_RIGHT = Inches(0.75)

# Paragraph Spacing
LINE_SPACING = 1.15

# Space Before/After
TITLE_SPACE_AFTER = Pt(6)
SUBTITLE_SPACE_AFTER = Pt(18)
H1_SPACE_BEFORE = Pt(18)
H1_SPACE_AFTER = Pt(12)
H2_SPACE_BEFORE = Pt(12)
H2_SPACE_AFTER = Pt(6)
H3_SPACE_BEFORE = Pt(10)
H3_SPACE_AFTER = Pt(4)
BODY_SPACE_AFTER = Pt(6)
```

### Style Application Functions

```python
from docx import Document
from docx.shared import Pt, Inches, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH

def apply_title_style(para):
    """Apply document title styling."""
    para.alignment = WD_ALIGN_PARAGRAPH.CENTER
    para.paragraph_format.space_after = Pt(6)
    for run in para.runs:
        run.font.name = "Roboto"
        run.font.size = Pt(24)
        run.font.bold = True
        run.font.color.rgb = RGBColor(10, 24, 73)

def apply_subtitle_style(para):
    """Apply subtitle styling."""
    para.alignment = WD_ALIGN_PARAGRAPH.CENTER
    para.paragraph_format.space_after = Pt(18)
    for run in para.runs:
        run.font.name = "Roboto"
        run.font.size = Pt(18)
        run.font.bold = False
        run.font.color.rgb = RGBColor(71, 57, 231)

def apply_h1_style(para):
    """Apply section heading (H1) styling."""
    para.alignment = WD_ALIGN_PARAGRAPH.LEFT
    para.paragraph_format.space_before = Pt(18)
    para.paragraph_format.space_after = Pt(12)
    for run in para.runs:
        run.font.name = "Roboto"
        run.font.size = Pt(14)
        run.font.bold = True
        run.font.color.rgb = RGBColor(71, 57, 231)

def apply_h2_style(para):
    """Apply subsection heading (H2) styling."""
    para.alignment = WD_ALIGN_PARAGRAPH.LEFT
    para.paragraph_format.space_before = Pt(12)
    para.paragraph_format.space_after = Pt(6)
    for run in para.runs:
        run.font.name = "Roboto"
        run.font.size = Pt(12)
        run.font.bold = True
        run.font.color.rgb = RGBColor(10, 24, 73)

def apply_h3_style(para):
    """Apply sub-subsection heading (H3) styling."""
    para.alignment = WD_ALIGN_PARAGRAPH.LEFT
    para.paragraph_format.space_before = Pt(10)
    para.paragraph_format.space_after = Pt(4)
    for run in para.runs:
        run.font.name = "Roboto"
        run.font.size = Pt(10)
        run.font.bold = True
        run.font.color.rgb = RGBColor(71, 57, 231)

def apply_body_style(para):
    """Apply body text styling."""
    para.alignment = WD_ALIGN_PARAGRAPH.LEFT
    para.paragraph_format.line_spacing = 1.15
    para.paragraph_format.space_after = Pt(6)
    for run in para.runs:
        run.font.name = "Roboto Light"
        run.font.size = Pt(10)
        run.font.bold = False
        run.font.color.rgb = RGBColor(10, 24, 73)
```

---

## Table Styles

### Style 1: Purple Header (Primary)

```python
from docx.oxml.ns import nsdecls
from docx.oxml import parse_xml

def create_purple_header_table(doc, headers, data):
    """Create table with purple header row."""
    table = doc.add_table(rows=1 + len(data), cols=len(headers))

    # Style header row
    header_row = table.rows[0]
    for idx, header_text in enumerate(headers):
        cell = header_row.cells[idx]
        cell.text = header_text

        # Purple background
        shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="4739E7"/>')
        cell._tc.get_or_add_tcPr().append(shading)

        # White bold text
        for para in cell.paragraphs:
            para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            for run in para.runs:
                run.font.name = "Roboto"
                run.font.size = Pt(10)
                run.font.bold = True
                run.font.color.rgb = RGBColor(255, 255, 255)

    # Style data rows with zebra striping
    for row_idx, row_data in enumerate(data):
        row = table.rows[row_idx + 1]
        fill_color = "FFFFFF" if row_idx % 2 == 0 else "F0F0F5"

        for col_idx, cell_value in enumerate(row_data):
            cell = row.cells[col_idx]
            cell.text = str(cell_value)

            # Background
            shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="{fill_color}"/>')
            cell._tc.get_or_add_tcPr().append(shading)

            # Navy text
            for para in cell.paragraphs:
                para.alignment = WD_ALIGN_PARAGRAPH.CENTER
                for run in para.runs:
                    run.font.name = "Roboto Light"
                    run.font.size = Pt(10)
                    run.font.color.rgb = RGBColor(10, 24, 73)

    return table
```

### Style 2: Light Purple Header (Secondary)

```python
def create_light_purple_header_table(doc, headers, data):
    """Create table with light purple header row."""
    table = doc.add_table(rows=1 + len(data), cols=len(headers))

    # Style header row
    header_row = table.rows[0]
    for idx, header_text in enumerate(headers):
        cell = header_row.cells[idx]
        cell.text = header_text

        # Light purple background
        shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="EBE9FC"/>')
        cell._tc.get_or_add_tcPr().append(shading)

        # Navy bold text
        for para in cell.paragraphs:
            para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            for run in para.runs:
                run.font.name = "Roboto"
                run.font.size = Pt(10)
                run.font.bold = True
                run.font.color.rgb = RGBColor(10, 24, 73)

    # Style data rows (white background)
    for row_idx, row_data in enumerate(data):
        row = table.rows[row_idx + 1]

        for col_idx, cell_value in enumerate(row_data):
            cell = row.cells[col_idx]
            cell.text = str(cell_value)

            for para in cell.paragraphs:
                para.alignment = WD_ALIGN_PARAGRAPH.CENTER
                for run in para.runs:
                    run.font.name = "Roboto Light"
                    run.font.size = Pt(10)
                    run.font.color.rgb = RGBColor(10, 24, 73)

    return table
```

### Style 3: FAQ/Q&A Table

```python
def create_faq_table(doc, qa_pairs):
    """Create FAQ-style table with question/answer columns.

    Args:
        qa_pairs: List of tuples [(question, answer), ...]
    """
    table = doc.add_table(rows=len(qa_pairs), cols=2)

    # Set column widths
    for row in table.rows:
        row.cells[0].width = Inches(2.5)  # Question column
        row.cells[1].width = Inches(4.5)  # Answer column

    for row_idx, (question, answer) in enumerate(qa_pairs):
        row = table.rows[row_idx]

        # Question cell
        q_cell = row.cells[0]
        q_cell.text = question

        # Light purple background for question
        shading = parse_xml(f'<w:shd {nsdecls("w")} w:fill="F8F7FE"/>')
        q_cell._tc.get_or_add_tcPr().append(shading)

        for para in q_cell.paragraphs:
            for run in para.runs:
                run.font.name = "Roboto"
                run.font.size = Pt(10)
                run.font.color.rgb = RGBColor(71, 57, 231)  # Purple

        # Answer cell
        a_cell = row.cells[1]
        a_cell.text = answer

        for para in a_cell.paragraphs:
            for run in para.runs:
                run.font.name = "Roboto Light"
                run.font.size = Pt(10)
                run.font.color.rgb = RGBColor(10, 24, 73)  # Navy

    return table
```

### Adding Table Borders

```python
from docx.oxml import OxmlElement
from docx.oxml.ns import qn

def set_table_borders(table, color="E0E0E0", size="4"):
    """Add thin gray borders to all table cells."""
    tbl = table._tbl
    tblPr = tbl.find(qn('w:tblPr'))
    if tblPr is None:
        tblPr = OxmlElement('w:tblPr')
        tbl.insert(0, tblPr)

    tblBorders = OxmlElement('w:tblBorders')

    for border_name in ['top', 'left', 'bottom', 'right', 'insideH', 'insideV']:
        border = OxmlElement(f'w:{border_name}')
        border.set(qn('w:val'), 'single')
        border.set(qn('w:sz'), size)
        border.set(qn('w:color'), color)
        tblBorders.append(border)

    tblPr.append(tblBorders)
```

---

## Helper Functions

### Document Initialization

```python
def create_class_document():
    """Create a new document with Class brand settings."""
    doc = Document()

    # Set margins
    section = doc.sections[0]
    section.top_margin = Inches(0.5)
    section.bottom_margin = Inches(0.75)
    section.left_margin = Inches(0.75)
    section.right_margin = Inches(0.75)

    return doc
```

### Adding Elements

```python
def add_title(doc, text):
    """Add centered document title."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    apply_title_style(para)
    return para

def add_subtitle(doc, text):
    """Add centered subtitle."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    apply_subtitle_style(para)
    return para

def add_section_heading(doc, text):
    """Add H1 section heading."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    apply_h1_style(para)
    return para

def add_subsection_heading(doc, text):
    """Add H2 subsection heading."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    apply_h2_style(para)
    return para

def add_h3_heading(doc, text):
    """Add H3 heading."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    apply_h3_style(para)
    return para

def add_body_text(doc, text):
    """Add body paragraph."""
    para = doc.add_paragraph()
    run = para.add_run(text)
    apply_body_style(para)
    return para

def add_bullet_point(doc, text, level=0):
    """Add a bullet point with proper styling."""
    para = doc.add_paragraph(style='List Bullet')
    run = para.add_run(text)
    run.font.name = "Roboto Light"
    run.font.size = Pt(9)
    run.font.color.rgb = RGBColor(10, 24, 73)
    para.paragraph_format.left_indent = Inches(0.25 * (level + 1))
    return para
```

### Hyperlinks

```python
def add_hyperlink(paragraph, url, text):
    """Add a purple hyperlink to a paragraph."""
    part = paragraph.part
    r_id = part.relate_to(url, "http://schemas.openxmlformats.org/officeDocument/2006/relationships/hyperlink", is_external=True)

    hyperlink = OxmlElement('w:hyperlink')
    hyperlink.set(qn('r:id'), r_id)

    new_run = OxmlElement('w:r')
    rPr = OxmlElement('w:rPr')

    # Purple color
    color = OxmlElement('w:color')
    color.set(qn('w:val'), '4739E7')
    rPr.append(color)

    # Underline
    u = OxmlElement('w:u')
    u.set(qn('w:val'), 'single')
    rPr.append(u)

    new_run.append(rPr)
    new_run.text = text
    hyperlink.append(new_run)

    paragraph._p.append(hyperlink)
    return hyperlink
```

---

## Complete Examples

### FAQ Document

```python
def create_faq_document(title, subtitle, sections):
    """Create a complete FAQ document.

    Args:
        title: Document title
        subtitle: Subtitle with date/context
        sections: Dict of {section_name: [(q, a), ...]}
    """
    doc = create_class_document()

    # Title block
    add_title(doc, title)
    add_subtitle(doc, subtitle)

    # Table of Contents (if multiple sections)
    if len(sections) > 1:
        add_section_heading(doc, "Table of Contents")
        for idx, section_name in enumerate(sections.keys(), 1):
            add_body_text(doc, f"{idx}. {section_name}")

    # Sections with Q&A
    for section_name, qa_pairs in sections.items():
        add_section_heading(doc, section_name)
        create_faq_table(doc, qa_pairs)
        doc.add_paragraph()  # Spacer

    return doc
```

### Product Roadmap

```python
def create_roadmap_document(title, subtitle, sections):
    """Create a product roadmap document.

    Args:
        sections: Dict of {section_name: {subsection: [features...]}}
    """
    doc = create_class_document()

    # Title block
    add_title(doc, title)
    add_subtitle(doc, subtitle)

    for section_name, subsections in sections.items():
        # H1 section (often ALL CAPS for sections)
        add_section_heading(doc, section_name.upper())

        for subsection_name, features in subsections.items():
            # H2 subsection
            add_subsection_heading(doc, subsection_name)

            for feature_group, feature_list in features.items():
                # H3 feature group
                add_h3_heading(doc, feature_group)

                # Bullet points
                for feature in feature_list:
                    add_bullet_point(doc, feature)

    return doc
```

### Pricing Document

```python
def create_pricing_document(title, subtitle, pricing_sections):
    """Create a pricing/schedule document."""
    doc = create_class_document()

    add_title(doc, title)
    add_subtitle(doc, subtitle)

    for section in pricing_sections:
        add_section_heading(doc, section['title'])

        if 'description' in section:
            add_body_text(doc, section['description'])

        if 'subsections' in section:
            for subsection in section['subsections']:
                add_subsection_heading(doc, subsection['title'])

                if 'description' in subsection:
                    add_body_text(doc, subsection['description'])

                if 'table' in subsection:
                    create_light_purple_header_table(
                        doc,
                        subsection['table']['headers'],
                        subsection['table']['data']
                    )
                    doc.add_paragraph()  # Spacer

    return doc
```
