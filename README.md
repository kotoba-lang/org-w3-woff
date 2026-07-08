# kotoba-lang/org-w3-woff

Zero-dep-beyond-`org-ietf-deflate`+`org-iso-opentype` portable `.cljc` WOFF
1.0 web font decoder (W3C Recommendation). Named `org-w3-woff` — same
`org-w3-<spec>` pattern as `org-w3-svg`/`org-w3-png`.

Extracted from `kotoba-lang/kasane` (kasane.woff, ADR-2606272100). WOFF
wraps an SFNT (TTF/OTF) with per-table zlib compression: this reassembles a
plain SFNT (decompressing each table via `org-ietf-deflate`) and delegates
to `org-iso-opentype` for metadata extraction. WOFF2 (Brotli + transforms)
is out of scope.

## Usage

```clojure
(require '[woff.core :as woff])

(woff/->sfnt woff-bytes)   ; => reassembled plain SFNT byte vector
(woff/parse woff-bytes)    ; => same shape as opentype.core/parse, plus {:woff true}
```

## Test

```sh
clojure -M:test
```
