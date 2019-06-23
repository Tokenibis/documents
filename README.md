# Overview
---

This repository holds all text-formatted official documents for Token
Ibis Inc. Documents are categorized by their markup language.

# Org
---

We use org mode for most static documents that only need only need to
be shared in its final compiled form. These documents are compiled
into either latex->pdf for human readability or semi-automatically
into ascii for reference on the bitcoin blockchain.

Only the original org file and supporting inputs are stored in the
repository.

## Build

The build is guaranteed to work with the following setup:

- texlive (apt package)
- emacs26 (apt package)
- org-ref (emacs package)

Finally, here is the relevant emacs.d configuration:

```elisp
  (with-eval-after-load 'ox-latex
    (add-to-list 'org-latex-classes
                 '("custom"
                   "\\documentclass{custom}"
		   ("\\section{%s}" . "\\section*{%s}")
		   ("\\subsection{%s}" . "\\subsection*{%s}")
		   ("\\subsubsection{%s}" . "\\subsubsection*{%s}")
		   ("\\paragraph{%s}" . "\\paragraph*{%s}")
		   ("\\subparagraph{%s}" . "\\subparagraph*{%s}"))))
  (setq org-latex-pdf-process
	'("pdflatex -interaction nonstopmode -output-directory %o %f"
          "bibtex %b"
          "pdflatex -interaction nonstopmode -output-directory %o %f"
          "pdflatex -interaction nonstopmode -output-directory %o %f"))
```

# Markdown
---

We use markdown files templates to ensure portability.
