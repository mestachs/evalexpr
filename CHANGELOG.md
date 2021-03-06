# Change Log

## Unreleased

### Notes

### Added

 * String constants

### Removed

### Changed

### Fixed

### Deprecated

## [3.1.0](https://github.com/ISibboI/evalexpr/compare/3.0.0...3.1.0) - 2019-03-28

### Added

 * Add serde support to `HashMapContext`
 * Make `HashMapContext` derive `Default` and `Debug`

### Changed

 * Changed name of serde feature flag to `serde_support`

## [3.0.0](https://github.com/ISibboI/evalexpr/compare/2.0.0...3.0.0) - 2019-03-28

### Notes

The 3.0.0 update transforms the expression evaluator `evalexpr` to a tiny scripting language.
It allows assignments and chaining of expressions.
Some changes in this update are breaking, hence the major release.

### Added

 * Methods `Node::eval_<type>_with_context_mut` and crate level `eval_<type>_with_context_mut`
 * Empty type and corresponding shortcut methods. The empty type is emitted by empty expressions or empty subexpressions `()`.
 * The assignment operator `=`
 * The expression chaining operator `;`

### Removed

 * Generic arguments from `Context` traits are now static to allow using trait objects of `Context`
 * `EvalexprError::EmptyExpression` is not required anymore since empty expressions now evaluate to the empty type

### Changed

 * Merge `ContextMut` trait into `Context` trait

## [2.0.0](https://github.com/ISibboI/evalexpr/compare/1.2.0...2.0.0) - 2019-03-28

### Notes

The 2.0.0 update is the first step to transform evalexpr to a tiny scripting language with support of at least variable assignment.
The main change for now is that `Configuration` is called `Context`, which seems to be a more proper naming for a set of variables that can not only be read, but also manipulated via expressions.
This update includes further renamings and some inconsistencies in the API were fixed.
For more details, see the following subsections.

### Added

 * Add the `ContextMut` trait, that is a manipulable configuration/context
 * Add `ContextNotManipulable` error variant for the `EmptyContext`
 * Make the `TupleType` alias public
 * Add the `ValueType` enum that represents the type of a value for easier comparisons and matchings
 * Add `EvalexprResult<T>` type that uses the `EvalexprError` type (renamed from `Error`)
 * Add `Node::eval_number` and `Node::eval_number_with_context` to evaluate to int or float and silently converting to float
 * Add `eval_number` and `eval_number_with_context` crate methods to evaluate to int or float and silently converting to float

### Changed

 * Get rid of some unwraps to improve safety
 * Rename `Error` to `EvalexprError`
 * Rename `Configuration` to `Context`
 * Rename `HashMapConfiguration` to `HashMapContext` and `EmptyConfiguration` to `EmptyContext`
 * Rename `Value::as_float` to `Value::as_number` and add new `Value::as_float` that fails if value is an integer

## [1.2.0](https://github.com/ISibboI/evalexpr/compare/1.1.0...1.2.0) - 2019-03-23

### Added

 * Add `serde` feature
 * Implement `serde::de::Deserialize` for `Node`
 * Document `serde` usage
 * Add custom error type with a `String` message

### Changed

 * Highlighting in documentation

## [1.1.0](https://github.com/ISibboI/evalexpr/compare/1.0.0...1.1.0) - 2019-03-20

### Added

 * Internal aliases `IntType` and `FloatType` used by the `Value` enum are now public
 * Type alias `TupleType` used to represent tuples was added
 * Error types like `Error::ExpectedInt` for expecting each value type were added
 * Shortcut functions like `eval_int` or `eval_int_with_configuration` to evaluate directly into a value type were added
 * Documentation for the shortcut functions was added
 * Functions to decompose `Value`s were added and documented

### Removed

 * Integration tests were removed from shipped crate

### Fixed

 * Wording of some documentation items was changed to improve readability

## [1.0.0](https://github.com/ISibboI/evalexpr/tree/1.0.0) - 2019-03-20

 * First stable release