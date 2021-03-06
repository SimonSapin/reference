# Structs

> **<sup>Syntax</sup>**  
> _Struct_ :  
> &nbsp;&nbsp; &nbsp;&nbsp; _StructStruct_  
> &nbsp;&nbsp; | _TupleStruct_  
>  
> _StructStruct_ :  
> &nbsp;&nbsp; `struct`
>   [IDENTIFIER]&nbsp;
>   [_Generics_]<sup>?</sup>
>   [_WhereClause_]<sup>?</sup>
>   ( `{` _StructFields_<sup>?</sup> `}` | `;` )  
>  
> _TupleStruct_ :  
> &nbsp;&nbsp; `struct`
>   [IDENTIFIER]&nbsp;
>   [_Generics_]<sup>?</sup>
>   `(` _TupleFields_<sup>?</sup> `)`
>   [_WhereClause_]<sup>?</sup>
>   `;`  
>  
> _StructFields_ :  
> &nbsp;&nbsp; _StructField_ (`,` _StructField_)<sup>\*</sup> `,`<sup>?</sup>  
>  
> _StructField_ :  
> &nbsp;&nbsp; [_OuterAttribute_]<sup>\*</sup>  
> &nbsp;&nbsp; [_Visibility_]
> &nbsp;&nbsp; [IDENTIFIER] `:` [_Type_]  
>  
> _TupleFields_ :  
> &nbsp;&nbsp; _TupleField_ (`,` _TupleField_)<sup>\*</sup> `,`<sup>?</sup>  
>  
> _TupleField_ :  
> &nbsp;&nbsp; [_OuterAttribute_]<sup>\*</sup>  
> &nbsp;&nbsp; [_Visibility_]
> &nbsp;&nbsp; [_Type_]  

A _struct_ is a nominal [struct type] defined with the keyword `struct`.

An example of a `struct` item and its use:

```rust
struct Point {x: i32, y: i32}
let p = Point {x: 10, y: 11};
let px: i32 = p.x;
```

A _tuple struct_ is a nominal [tuple type], also defined with the keyword
`struct`. For example:

[struct type]: types.html#struct-types
[tuple type]: types.html#tuple-types

```rust
struct Point(i32, i32);
let p = Point(10, 11);
let px: i32 = match p { Point(x, _) => x };
```

A _unit-like struct_ is a struct without any fields, defined by leaving off the
list of fields entirely. Such a struct implicitly defines a constant of its
type with the same name. For example:

```rust
struct Cookie;
let c = [Cookie, Cookie {}, Cookie, Cookie {}];
```

is equivalent to

```rust
struct Cookie {}
const Cookie: Cookie = Cookie {};
let c = [Cookie, Cookie {}, Cookie, Cookie {}];
```

The precise memory layout of a struct is not specified. One can specify a
particular layout using the [`repr` attribute].

[`repr` attribute]: attributes.html#ffi-attributes

[_OuterAttribute_]: attributes.html
[IDENTIFIER]: identifiers.html
[_Generics_]: items/generics.html
[_WhereClause_]: items/generics.html#where-clauses
[_Visibility_]: visibility-and-privacy.html
[_Type_]: types.html
