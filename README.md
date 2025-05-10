# Bottom-up-SLR-Parser

Bottom-up SLR(1) parser for a C like language.

## Project Overview

- Grammar analysis and ambiguity detection
- Grammar refactoring to remove ambiguity
- Construction of SLR(1) parsing table
- Parser implementation including parse-tree generation and error reporting

## Ambiguous Grammar Specification

```
Program    →  DeclList
DeclList   →  Decl DeclList | ε
Decl       →  VarDecl | FuncDecl
VarDecl    →  type id ;
VarDecl    →  type id = Expr ;
FuncDecl   →  type id ( ParamList ) Block
ParamList  →  Param , ParamList | Param | ε
Param      →  type id
Block      →  { StmtList }
StmtList   →  Stmt StmtList | ε
Stmt       →  if ( Expr ) Stmt
Stmt       →  if ( Expr ) Stmt else Stmt
Stmt       →  while ( Expr ) Stmt
Stmt       →  for ( Expr ; Expr ; Expr ) Stmt
Stmt       →  return Expr ;
Stmt       →  ExprStmt
Stmt       →  Block
ExprStmt   →  Expr ;
Expr       →  Expr == Expr
Expr       →  Expr + Expr
Expr       →  Expr * Expr
Expr       →  - Expr
Expr       →  id ( ArgList )
Expr       →  id
Expr       →  num
Expr       →  ( Expr )
ArgList    →  Expr , ArgList | Expr | ε
```
