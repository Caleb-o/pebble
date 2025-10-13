# Pebble Compiler

## ✅ Completed
- 4-pass compilation (lexer → parser → type checking → function bodies)
- Out-of-order type resolution
- Self-referential types via pointers
- Tuples with member access (.0, .1, etc.)
- Type aliases
- Forward references
- Structural type equality with cycle detection
- Comprehensive test suite

## 🚧 Missing Language Features

### Core Types
- [ ] **Struct types** - Parse and implement struct type syntax
  - `type Point = struct { x: int; y: int; }`
  - Field access: `point.x`
  - Struct literals: `Point { x: 10, y: 20 }`.
    - There will be some ambiguity here in the parser  since it will think it
    is an expression followed by a block of statements.

- [ ] **Function types as type expressions** - Parse fn types
  - `type BinaryOp = fn(int, int) int;`
  - Function type variables
  - First-class functions (if desired)

### Expressions
- [ ] **Struct literals** - Create struct instances
  - Parse `StructName { field1: value1, field2: value2 }`
  - Type check field names and types

- [ ] **Tuple literals** - Currently parsed but need full checking
  - Verify: `(1, 2, 3)` type inference
  - Tuple destructuring (optional)

- [ ] **Array literals** - Create array instances
  - `[1, 2, 3, 4, 5]`
  - Type inference from elements

- [ ] **Slice literals** - Create slices
  - Syntax TBD (maybe same as arrays?)

### Operators
- [ ] **Pointer operations**
  - Address-of: `&x`
  - Dereference: `*ptr`

- [ ] **Array/slice operations**
  - Slice syntax: `arr[1:5]`
  - Length operation

### Statements
- [ ] **For loops** - If desired
  - `for i in 0..10 { }`
  - Or C-style: `for (i = 0; i < 10; i++) { }`

- [ ] **Switch/match statements** - If desired

- [ ] **Defer statements** - If desired (Go-style)

### Type System Enhancements
- [ ] **Type inference for local variables**
  - `var x = 42;` (infer int)
  - Currently requires explicit types

- [ ] **Const evaluation** - Evaluate constant expressions
  - `const SIZE = 10 * 10;`
  - Currently only supports literals

- [ ] **Method syntax** - If desired
  - `fn (p Point) distance() int { }`

- [ ] **Generic types** - Future (complex)

## 🔨 Code Generation (Next Major Phase)

### Pass 5: C Code Generation
- [ ] **Setup**
  - Create `codegen.c/h`
  - Implement C AST builder (or direct string generation)

- [ ] **Type translation**
  - Map Pebble types → C types
  - Generate struct definitions
  - Generate typedefs

- [ ] **Expression codegen**
  - Literals
  - Variables
  - Binary/unary operations
  - Function calls
  - Array indexing
  - Member access
  - Tuple access → struct field access

- [ ] **Statement codegen**
  - Variable declarations
  - Assignments
  - If/while/for
  - Return
  - Blocks

- [ ] **Function codegen**
  - Function prototypes
  - Function definitions
  - Parameter handling

- [ ] **Self-referential types**
  - Handle circular struct definitions properly
  - Forward declare structs when needed

### Build System Integration
- [ ] **Compilation pipeline**
  - Pebble → C translation
  - Invoke C compiler (gcc/clang)
  - Handle intermediate files
  - Link object files

- [ ] **Runtime library** (if needed)
  - String operations
  - Array/slice operations
  - Memory management helpers

## 🧪 Testing & Quality

### More Tests
- [ ] **Struct tests**
  - Struct type resolution
  - Struct literals
  - Field access
  - Nested structs

- [ ] **Array/slice tests**
  - Bounds checking (compile-time if possible)
  - Multi-dimensional arrays

- [ ] **Error message quality**
  - Add more context to error messages
  - Suggest fixes where possible
  - Show source code snippets

- [ ] **Integration tests**
  - Full programs that compile and run
  - Test against expected output

### Code Quality
- [ ] **Refactoring**
  - Clean up any messy code
  - Improve naming consistency
  - Add comments to complex logic

- [ ] **Performance**
  - Profile compilation speed
  - Optimize hot paths if needed

- [ ] **Memory safety**
  - Ensure no leaks (or document arena usage)
  - Verify bounds checking

## 📚 Documentation

- [ ] **Language specification**
  - Formal grammar
  - Type system rules
  - Semantics documentation

- [ ] **User guide**
  - Getting started
  - Language tour
  - Examples

- [ ] **Implementation notes**
  - Architecture overview
  - Adding new features guide
  - Compiler internals

## 🎯 Nice-to-Have Features

### Language Features
- [ ] String interpolation
- [ ] Multiple return values (or just use tuples)
- [ ] Destructuring assignments
- [ ] Pattern matching
- [ ] Enums/sum types
- [ ] Interfaces/traits
- [ ] Closures/lambdas

### Tooling
- [ ] REPL
- [ ] Package manager
- [ ] Standard library
- [ ] Formatter
- [ ] LSP server (for editor support)
- [ ] Debugger integration

### Optimizations
- [ ] Constant folding
- [ ] Dead code elimination
- [ ] Inline small functions
- [ ] Tail call optimization

## 🚀 Immediate Next Steps

**Recommended order:**
1. ✅ Struct types (most important missing feature)
2. ✅ Struct literals and field access
3. ✅ Function type parsing
4. ✅ Basic codegen (simple programs first)
5. ✅ Expand codegen to handle all features
6. ✅ Integration testing with real C compilation

You've built an excellent foundation. The hard part (semantic analysis) is done! 🎉
