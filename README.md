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