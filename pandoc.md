# HOW TO WRITE PANDOC DOCS

# YAML HEADER FOR BEAMER

```markdown
---
title: Presentation title
author: Author's Name
theme: Berlin
colortheme: seahorse
---
```

# EXAMPLE COMMANDS FOR BEAMER

> $ pandoc  -V theme=Berlin --highlight-style=zenburn -t beamer bash.md -o bash.pdf

# EXAMPLE COMMANDS FOR PANDOC

> $ pandoc -V geometry:margin=5mm -V theme=Berlin --highlight-style=zenburn -t beamer bash.md -o bash.pdf

# SYNTAX

```markdown
# H1 ## H2
[text](link)
```

# SYNTAX FOR

* tables
* bold
* italic
