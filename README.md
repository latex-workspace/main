# LaTeX Workspace

Una collezione dei miei appunti e file scritti in **LaTeX**.

---

## Introduzione

Questo repository contiene due componenti principali:

1. **Collezione di sottomoduli** — uno per ogni progetto. Alcuni includono più progetti collegati tra loro (ad esempio `ripetizioni`, `mergify`).
2. **Preambolo condiviso** (`.preamble.tex`) — utilizzato dalla maggior parte dei progetti.

---

## Getting Started

#### Clonare la repository

```bash
git clone https://github.com/latex-workspace/main.git
```

#### Inizializzare i sottomoduli

```bash
git submodule update --init
```

#### Eseguire il pull delle modifiche da remoto

* Per un singolo sottomodulo:

  ```bash
  cd <nome_sottomodulo>
  git pull
  ```
* Per tutti i sottomoduli:

  ```bash
  git pull --recurse-submodules
  ```

>  In alternativa, puoi clonare un singolo repository e copiare manualmente il file `.preamble.fmt` nella directory parent del progetto.

---

## Compilazione

I progetti utilizzano la **feature di esternalizzazione delle immagini TikZ** per ridurre i tempi di compilazione.

Assicurati che esista la directory `./tikz` nella root di ogni progetto/sottomodulo.

#### Compilare il documento principale

```bash
pdflatex -shell-escape main.tex
```

Oppure:

```bash
latexmk -shell-escape -pdf main.tex
```

#### Compilare il preambolo condiviso

```bash
pdftex -ini -jobname=".preamble" "&pdflatex" mylatexformat.ltx .preamble.tex
```
