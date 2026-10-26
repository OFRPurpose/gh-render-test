# Mermaid Security Tests — antiscript mode

## Test 1: Form injection in flowchart label
```mermaid
flowchart LR
    A["<form action='https://github.com/OFRPurpose/gh-render-test/issues/new?title=INJECTED&body=form-works'><input type='submit' value='View Details' style='cursor:pointer;padding:5px;background:#0366d6;color:white;border:none;border-radius:3px'></form>"]
```

## Test 2: Anchor tag with target
```mermaid
flowchart TD
    A["<a href='https://github.com/OFRPurpose/gh-render-test/issues' target='_top'>📊 View Statistics</a>"]
```

## Test 3: Image tag (should render without onerror)
```mermaid
flowchart LR
    A["<img src='https://github.com/fluidicon.png' width='100'>"]
```

## Test 4: Style injection for data exfil (CSS only)
```mermaid
flowchart LR
    A["<style>*{background:url('https://github.com/OFRPurpose/gh-render-test/issues/new?title=CSS-EXFIL')}</style>CSS Test"]
```

## Test 5: SVG within label
```mermaid
flowchart LR
    A["<svg width='100' height='100'><circle cx='50' cy='50' r='40' fill='red'/><text x='50' y='55' text-anchor='middle'>XSS</text></svg>"]
```

## Test 6: Iframe injection (should be stripped by DOMPurify)
```mermaid
flowchart LR
    A["<iframe src='https://github.com'></iframe>"]
```
