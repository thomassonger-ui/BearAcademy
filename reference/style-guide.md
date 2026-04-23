# Bear Academy Style Guide

Design tokens and visual rules for every Moodle page.

---

## Colors

| Token           | Hex       | Use                                        |
|-----------------|-----------|--------------------------------------------|
| Navy (primary)  | `#1B365D` | Header bar, panel left borders, table head |
| Body text       | `#222222` | All copy                                   |
| Panel bg        | `#f7f9fc` | Content panels                             |
| Structured bg   | `#f4f7fb` | Tables and structured breakdowns           |
| Lesson strip bg | `#f4f4f4` | Lesson title strip                         |
| Border gray     | `#d9d9d9` | Main container + table borders             |
| Row alt         | `#ffffff` | Alternating table row                      |
| Button (Next)   | `#000000` | Next button background                     |
| White           | `#ffffff` | Header text, Next button text, Back bg     |

---

## Typography

- **Font stack:** `Arial, Helvetica, sans-serif`
- **Body line-height:** `1.6`
- **Body color:** `#222`
- **Page max-width:** `1000px`, centered via `margin: auto`

---

## Spacing

- **Main container padding:** `24px`
- **Content panel padding:** `16px`
- **Panel left border:** `4px solid #1B365D`
- **Default section gap:** `16px` between panels

---

## Buttons

**Back (outlined)**
```
background: #ffffff;
color: #1B365D;
border: 2px solid #1B365D;
padding: 10px 20px;
text-decoration: none;
font-weight: bold;
```

**Next (filled)**
```
background: #000000;
color: #ffffff;
border: none;
padding: 10px 20px;
text-decoration: none;
font-weight: bold;
```

---

## Mobile

- Single-column by default — no flex/grid required for content
- Nav row may use `display: flex; justify-content: space-between;`
- Images and iframes use `width: 100%; height: auto;`
- Video block uses 16:9 responsive wrapper (see build standard)
