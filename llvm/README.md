### LLVM: Intro Make Compiler
https://www.youtube.com/watch?v=OhkwPSvyBu0

### Useful Articles
https://theantlrguy.atlassian.net/wiki/display/ANTLR3/LLVM

### Terms

** FrontEnd **
- Parse Input Language
- Build Symbol Table
- Perform Semantic Analysis
- Emit Internal Representation

** BackEnd **
- Create Data Structures
  - Control Flow Graphs
  - Optimizes the IR
  - Maps IR Computation to Machine Register
  - Emits Assembly Language as text
    - Assembler converts to binary
