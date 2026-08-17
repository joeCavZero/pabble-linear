<h1 align="center">PABBLE LINEAR</h1>

<p align="center">
A linear algebra library for the Penguin programming language and the Pabble ecosystem.
</p>

<p align="center">
Simple - Educational - Expressive - Extensible
</p>

---

## About

Pabble Linear is a linear algebra library written in Penguin for the [Pabble](https://github.com/joeCavZero/pabble) ecosystem.

The library provides vector, matrix and linear transformation abstractions together with algorithms commonly used in introductory and intermediate linear algebra.

It was designed especially for studying and experimenting with concepts such as:

- vector spaces
- linear combinations
- linear dependence and independence
- bases and dimension
- matrices
- linear systems
- linear transformations
- eigenvalues and eigenvectors
- diagonalization
- inner products
- orthogonality
- projections
- Gram-Schmidt
- QR decomposition

---

## Features

- `Vec2`, `Vec3` and `Vec4`
- General-purpose `Vector`
- Matrix operations
- Matrix transpose
- Determinant
- Matrix inverse
- Identity and zero matrices
- REF and RREF
- Matrix rank and nullity
- Null space
- Column space
- Linear systems
- Linear combinations
- Linear dependence and independence
- Basis extraction
- Vector coordinates
- Change of basis
- Subspaces
- Linear transformations
- Transformation composition
- Kernel and image
- Injectivity and surjectivity
- Isomorphism checks
- Matrix representation of transformations
- Characteristic polynomial
- Eigenvalues
- Eigenvectors
- Eigenspaces
- Algebraic and geometric multiplicities
- Diagonalization
- Inner products
- Norm and distance
- Orthogonality
- Orthogonal projection
- Gram-Schmidt orthogonalization
- Orthonormal bases
- Projection onto subspaces
- QR decomposition

---

## Example

A simple example using vectors:

```go
import("io") as io
import("linear") as linear

func main() {
    var a = linear:Vector([1, 2, 3])
    var b = linear:Vector([4, 5, 6])

    io:println("a:", a)
    io:println("b:", b)

    io:println("a + b:", a + b)
    io:println("dot(a, b):", a.dot(b))
    io:println("norm(a):", a.length())
}
````

Example output:

```text
a: Vector(1, 2, 3)
b: Vector(4, 5, 6)
a + b: Vector(5, 7, 9)
dot(a, b): 32
norm(a): 3.7416573867739413
```

---

## Matrices

Matrices support common arithmetic and linear algebra operations.

```go
var A = linear:Matrix([
    [1, 2],
    [3, 4]
])

var B = linear:Matrix([
    [5, 6],
    [7, 8]
])

io:println(A + B)
io:println(A * B)
io:println(A.transpose())
io:println(A.determinant())
io:println(A.inverse())
```

Example:

```text
Matrix[
    [19, 22]
    [43, 50]
]
```

---

## Vector Spaces

Pabble Linear provides utilities for working with generated vector spaces.

```go
var e1 = linear:Vector([1, 0, 0])
var e2 = linear:Vector([0, 1, 0])
var e3 = linear:Vector([0, 0, 1])

var vectors = [e1, e2, e3]

io:println(linear:is_linearly_independent(vectors))
io:println(linear:dimension(vectors))
```

Subspaces can also be represented directly:

```go
var xy = linear:Subspace([
    e1,
    e2
])

io:println(xy.dimension())
io:println(xy.contains(linear:Vector([3, -2, 0])))
```

---

## Linear Systems

Linear systems of the form

```text
Ax = b
```

can be solved directly.

```go
var A = linear:Matrix([
    [2, 1],
    [1, -1]
])

var b = linear:Vector([5, 1])

var x = A.solve(b)

io:println(x)
```

Output:

```text
Vector(2, 1)
```

---

## Linear Transformations

Linear transformations are represented by matrices and can be called directly.

```go
var T = linear:LinearTransformation(
    linear:Matrix([
        [2, 0],
        [0, 3]
    ])
)

var v = linear:Vector([4, 5])

io:println(T(v))
```

Output:

```text
Vector(8, 15)
```

Transformations also expose information such as:

```go
T.kernel()
T.image()
T.rank()
T.nullity()
T.is_injective()
T.is_surjective()
T.is_isomorphism()
T.is_operator()
```

Transformations can also be composed.

```go
var R = T.compose(S)
```

---

## Eigenvalues and Eigenvectors

Matrices support eigenvalue and eigenspace operations.

```go
var A = linear:Matrix([
    [2, 0],
    [0, 3]
])

io:println(A.eigenvalues())
io:println(A.eigenspace(2))
io:println(A.algebraic_multiplicity(2))
io:println(A.geometric_multiplicity(2))
```

Characteristic polynomials are represented using the `Polynomial` type.

```go
var p = A.characteristic_polynomial()

io:println(p)
io:println(p.evaluate(2))
```

---

## Diagonalization

Diagonalizable matrices can be decomposed as

```text
A = P D P⁻¹
```

```go
var A = linear:Matrix([
    [4, 1],
    [0, 2]
])

var decomposition = A.diagonalize()

io:println(decomposition.P)
io:println(decomposition.D)
io:println(decomposition.P_inverse)
```

---

## Orthogonality

The library includes inner-product-space operations.

```go
var a = linear:Vector([1, 2, 3])
var b = linear:Vector([4, -2, 0])

io:println(a.dot(b))
io:println(a.length())
io:println(a.distance(b))
io:println(a.is_orthogonal_to(b))
```

Orthogonal projection is also supported:

```go
var v = linear:Vector([2, 3, 4])
var u = linear:Vector([1, 0, 0])

io:println(v.project_onto(u))
```

Output:

```text
Vector(2, 0, 0)
```

---

## Gram-Schmidt

A linearly independent set can be transformed into an orthonormal set using Gram-Schmidt.

```go
var vectors = [
    linear:Vector([1, 1, 0]),
    linear:Vector([1, 0, 1])
]

var orthonormal = linear:gram_schmidt(vectors)

io:println(orthonormal)
io:println(linear:is_orthonormal_set(orthonormal))
```

---

## QR Decomposition

Matrices support QR decomposition:

```go
var A = linear:Matrix([
    [1, 0],
    [1, 1],
    [0, 1]
])

var qr = A.qr()

io:println(qr.Q)
io:println(qr.R)
io:println(qr.Q * qr.R)
```

The decomposition follows:

```text
A = QR
```

QR iteration is also used internally for numerical eigenvalue approximation in larger matrices.

---

## Numerical Considerations

Pabble Linear operates with floating-point arithmetic where necessary.

Because of this, operations involving normalization, QR decomposition, eigenvalue approximation and similar numerical algorithms may produce small floating-point errors.

For example:

```text
0.9999999999999998
```

should generally be interpreted as numerically equivalent to:

```text
1.0
```

within an appropriate tolerance.

The library currently focuses on finite-dimensional real linear algebra.

---

## Goals

The main goals of Pabble Linear are:

* Provide a practical linear algebra library for Penguin
* Keep the API simple and readable
* Make mathematical concepts easy to experiment with
* Support the main topics of an undergraduate linear algebra course
* Serve as a real-world library for testing Penguin and Pabble
* Keep most algorithms implemented directly in Penguin
* Provide a foundation for more advanced numerical libraries

---

## Ecosystem

Pabble Linear is part of the Penguin/Pabble ecosystem.

* [Penguin](https://github.com/joeCavZero/penguin) - programming language and runtime
* [Pabble](https://github.com/joeCavZero/pabble) - Penguin package and execution ecosystem
* **Pabble Linear** - linear algebra library

---

## Status

Pabble Linear currently supports the core functionality planned for vector spaces, linear transformations, eigenvalues and eigenvectors, diagonalization, inner-product spaces and orthogonality.

The library is under active development as Penguin and Pabble evolve.
