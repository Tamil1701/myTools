# Filename Format Guide

The whole app is a single file — **index.html**. The filename format is edited
in its own view within that file, reachable only through the "Edit format →"
link on the main screen (it navigates to `index.html#format`). The template is
saved in your browser and the uploader picks it up automatically.

## Default template

```
{month} {day}- {amount}_{invoice}.pdf
```

With date = `2026-07-03`, amount = `1234`, invoice = `129048009`, and decimals
turned **on**, this produces:

```
Jul 03- 1234.00_129048009.pdf
```

With decimals turned **off**, it produces:

```
Jul 03- 1234_129048009.pdf
```

## Available tokens

Use these placeholders anywhere in the template — order, spacing, and
punctuation are entirely up to you:

| Token         | Meaning                                   | Example  |
|---------------|--------------------------------------------|----------|
| `{month}`     | 3-letter month abbreviation                | `Jul`    |
| `{monthnum}`  | 2-digit month number                       | `07`     |
| `{day}`       | 2-digit day of month                       | `03`     |
| `{year}`      | 4-digit year                               | `2026`   |
| `{amount}`    | Amount, decimals on/off per the checkbox   | `1234.00` or `1234` |
| `{invoice}`   | Invoice number, as typed                   | `129048009` |

If your template doesn't end in `.pdf`, the app will append it automatically.

## Example alternate templates

**Include the year:**
```
{month} {day} {year}- {amount}_{invoice}.pdf
```
→ `Jul 03 2026- 1234.00_129048009.pdf`

**Invoice first:**
```
{invoice}_{month} {day}- {amount}.pdf
```
→ `129048009_Jul 03- 1234.00.pdf`

**Numeric month, dash-separated:**
```
{monthnum}-{day}-{year}_{amount}_{invoice}.pdf
```
→ `07-03-2026_1234.00_129048009.pdf`

**No dash, just a space:**
```
{month} {day} {amount}_{invoice}.pdf
```
→ `Jul 03 1234.00_129048009.pdf`

## Notes

- The invoice number has characters that aren't allowed in filenames
  (`\ / : * ? " < > |`) automatically stripped out.
- The "Include decimals" checkbox only affects `{amount}` — everything else
  in the template is unaffected.
- All of this happens locally in your browser; no file ever leaves your
  computer.
