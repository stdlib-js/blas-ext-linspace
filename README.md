<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# linspace

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Return a new [ndarray][@stdlib/ndarray/ctor] filled with linearly spaced values over a specified interval along one or more [ndarray][@stdlib/ndarray/ctor] dimensions.

<section class="installation">

## Installation

```bash
npm install @stdlib/blas-ext-linspace
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var linspace = require( '@stdlib/blas-ext-linspace' );
```

#### linspace( shape, start, stop\[, endpoint]\[, options] )

Returns a new [ndarray][@stdlib/ndarray/ctor] filled with linearly spaced values over a specified interval along one or more [ndarray][@stdlib/ndarray/ctor] dimensions.

```javascript
var ndarray2array = require( '@stdlib/ndarray-to-array' );

var x = linspace( [ 4 ], 1.0, 4.0 );
// returns <ndarray>

var arr = ndarray2array( x );
// returns [ 1.0, 2.0, 3.0, 4.0 ]
```

The function has the following parameters:

-   **shape**: array shape.
-   **start**: start of interval. May be either a number, a complex number, or an [ndarray][@stdlib/ndarray/ctor] having a numeric or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the complement of the shape defined by `options.dims`. For example, given the input shape `[2, 3, 4]` and `options.dims=[0]`, a start [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. Similarly, when performing the operation over all elements in a provided input shape, a start [ndarray][@stdlib/ndarray/ctor] must be a zero-dimensional [ndarray][@stdlib/ndarray/ctor].
-   **stop**: end of interval. May be either a number, a complex number, or an [ndarray][@stdlib/ndarray/ctor] having a numeric or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the complement of the shape defined by `options.dims`. For example, given the input shape `[2, 3, 4]` and `options.dims=[0]`, a stop [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. Similarly, when performing the operation over all elements in a provided input shape, a stop [ndarray][@stdlib/ndarray/ctor] must be a zero-dimensional [ndarray][@stdlib/ndarray/ctor].
-   **endpoint**: specifies whether to include the end of the interval when writing values to the output [ndarray][@stdlib/ndarray/ctor] (_optional_). May be either a boolean or an [ndarray][@stdlib/ndarray/ctor] having a boolean or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the complement of the shape defined by `options.dims`. For example, given the input shape `[2, 3, 4]` and `options.dims=[0]`, an endpoint [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. Similarly, when performing the operation over all elements in a provided input shape, an endpoint [ndarray][@stdlib/ndarray/ctor] must be a zero-dimensional [ndarray][@stdlib/ndarray/ctor]. Default: `true`.
-   **options**: function options (_optional_).

The function accepts the following options:

-   **dims**: list of dimensions over which to perform operation. If not provided, the function generates linearly spaced values along the last dimension. Default: `[-1]`.
-   **dtype**: output [ndarray][@stdlib/ndarray/ctor] [data type][@stdlib/ndarray/dtypes]. If both `start` and `stop` are real-valued, the output array data type may be any floating-point data type or "generic". However, if either `start` or `stop` are complex-valued, the output array type must be a complex floating-point data type or "generic". If a data type is provided, `start` and `stop` are cast to the specified data type. If a data type is not provided and both `start` and `stop` are the same type (either `'float64'`, `'complex64'`, or `'complex128'`), the default output array data type is the same type as the input values (either `'float64'`, `'complex64'`, or `'complex128'`, respectively). Otherwise, if a data type is not provided and `start` and `stop` have different types, the default output array data type is determined according to type promotion rules.
-   **order**: specifies whether an [ndarray][@stdlib/ndarray/ctor] is `'row-major'` (C-style) or `'column-major'` (Fortran-style). If `start`, `stop`, and `endpoint` are scalar values, the default order is `'row-major'`. If `start`, `stop`, and/or `endpoint` arrays have the same memory layout, the default order is the same layout. Otherwise, the default order is `'row-major'`.
-   **mode**: specifies how to handle indices which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). Default: `'throw'`.
-   **submode**: a mode array which specifies for each dimension how to handle subscripts which exceed array dimensions  (see [`ndarray`][@stdlib/ndarray/ctor]). If provided fewer modes than dimensions, the constructor recycles modes using modulo arithmetic. Default: `[ options.mode ]`.

By default, the function always includes the end of the interval in the list of values written to an output [ndarray][@stdlib/ndarray/ctor]. To exclude the end of the interval, provide an `endpoint` argument.

```javascript
var ndarray2array = require( '@stdlib/ndarray-to-array' );

var x = linspace( [ 4 ], 1.0, 5.0, false );
// returns <ndarray>

var arr = ndarray2array( x );
// returns [ 1.0, 2.0, 3.0, 4.0 ]
```

When provided scalar or zero-dimensional [ndarray][@stdlib/ndarray/ctor] `start`, `stop`, and `endpoint` arguments, the values are broadcast across all elements in the shape defined by the complement of those dimensions specified by `options.dims`. To specify separate sub-array configurations, provide non-zero-dimensional [ndarray][@stdlib/ndarray/ctor] arguments.

```javascript
var array = require( '@stdlib/ndarray-array' );
var BooleanArray = require( '@stdlib/array-bool' );
var ndarray2array = require( '@stdlib/ndarray-to-array' );

var start = array( [ 1.0, 5.0 ] );
var end = array( [ 3.0, 8.0 ] );
var endpoint = array( new BooleanArray( [ true, false ] ) );

var x = linspace( [ 2, 3 ], start, end, endpoint );
// returns <ndarray>

var arr = ndarray2array( x );
// returns [ [ 1.0, 2.0, 3.0 ], [ 5.0, 6.0, 7.0 ] ]
```

By default, the function generates linearly spaced values along the last dimension of an output [ndarray][@stdlib/ndarray/ctor]. To perform the operation over specific dimensions, provide a `dims` option.

```javascript
var ndarray2array = require( '@stdlib/ndarray-to-array' );

var x = linspace( [ 2, 2 ], 1.0, 4.0, {
    'dims': [ 0, 1 ]
});
// returns <ndarray>

var arr = ndarray2array( x );
// returns [ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ]
```

To specify the output [ndarray][@stdlib/ndarray/ctor] [data type][@stdlib/ndarray/dtypes], provide a `dtype` option.

```javascript
var ndarray2array = require( '@stdlib/ndarray-to-array' );

var x = linspace( [ 4 ], 1.0, 4.0, {
    'dtype': 'float32'
});
// returns <ndarray>

var arr = ndarray2array( x );
// returns [ 1.0, 2.0, 3.0, 4.0 ]
```

#### linspace.assign( out, start, stop\[, endpoint]\[, options] )

Fills an [ndarray][@stdlib/ndarray/ctor] with linearly spaced values over a specified interval along one or more [ndarray][@stdlib/ndarray/ctor] dimensions.

```javascript
var ndarray2array = require( '@stdlib/ndarray-to-array' );
var zeros = require( '@stdlib/ndarray-zeros' );

var x = zeros( [ 4 ] );
// returns <ndarray>

var out = linspace.assign( x, 1.0, 4.0 );
// returns <ndarray>

var arr = ndarray2array( out );
// returns [ 1.0, 2.0, 3.0, 4.0 ]

var bool = ( x === out );
// returns true
```

The function has the following parameters:

-   **out**: output [ndarray][@stdlib/ndarray/ctor]. Must have a floating-point or "generic" [data type][@stdlib/ndarray/dtypes].
-   **start**: start of interval. May be either a number, a complex number, or an [ndarray][@stdlib/ndarray/ctor] having a numeric or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the complement of the shape defined by `options.dims`. For example, given the input shape `[2, 3, 4]` and `options.dims=[0]`, a start [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. Similarly, when performing the operation over all elements in a provided output [ndarray][@stdlib/ndarray/ctor], a start [ndarray][@stdlib/ndarray/ctor] must be a zero-dimensional [ndarray][@stdlib/ndarray/ctor].
-   **stop**: end of interval. May be either a number, a complex number, or an [ndarray][@stdlib/ndarray/ctor] having a numeric or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the complement of the shape defined by `options.dims`. For example, given the input shape `[2, 3, 4]` and `options.dims=[0]`, a stop [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. Similarly, when performing the operation over all elements in a provided output [ndarray][@stdlib/ndarray/ctor], a stop [ndarray][@stdlib/ndarray/ctor] must be a zero-dimensional [ndarray][@stdlib/ndarray/ctor].
-   **endpoint**: specifies whether to include the end of the interval when writing values to the output [ndarray][@stdlib/ndarray/ctor] (_optional_). May be either a boolean or an [ndarray][@stdlib/ndarray/ctor] having a boolean or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the complement of the shape defined by `options.dims`. For example, given the input shape `[2, 3, 4]` and `options.dims=[0]`, an endpoint [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. Similarly, when performing the operation over all elements in a provided output [ndarray][@stdlib/ndarray/ctor], an endpoint [ndarray][@stdlib/ndarray/ctor] must be a zero-dimensional [ndarray][@stdlib/ndarray/ctor]. Default: `true`.
-   **options**: function options (_optional_).

The function accepts the following options:

-   **dims**: list of dimensions over which to perform operation. If not provided, the function generates linearly spaced values along the last dimension. Default: `[-1]`.

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Let `M` be the number of linearly spaced values to be written along one or more [ndarray][@stdlib/ndarray/ctor] dimensions. The spacing between values is thus given by

    ```text
    Δ = (stop-start)/(M-1)
    ```

-   If an output [ndarray][@stdlib/ndarray/ctor] has a single element and the function is supposed to include the end of the interval, the set of values written to an output [ndarray][@stdlib/ndarray/ctor] only includes the end of the interval, but not the start of the interval.

-   Otherwise, when an output [ndarray][@stdlib/ndarray/ctor] has a single element and the function is not supposed to include the end of the interval, the set of values written to an output [ndarray][@stdlib/ndarray/ctor] only includes the start of the interval, but not the end of the interval.

-   For a real-valued output [ndarray][@stdlib/ndarray/ctor], if the start of the interval is less than end of the interval, the set of values written to an output [ndarray][@stdlib/ndarray/ctor] will be written in ascending order, and, if the start of the interval is greater than the end of the interval, the set of written values will be in descending order.

-   When an output [ndarray][@stdlib/ndarray/ctor] contains at least two values and the function is supposed to include the end of the interval, the set of values written to an output [ndarray][@stdlib/ndarray/ctor] is guaranteed to include the start and end interval values. Beware, however, that values between the interval bounds are subject to floating-point rounding errors.

-   When writing to a complex floating-point output [ndarray][@stdlib/ndarray/ctor], real-valued start and stop values are treated as complex numbers having a real component equaling the provided value and having an imaginary component equaling zero.

-   When generating linearly spaced complex floating-point numbers, the real and imaginary components are generated separately.

-   Both `start` and `stop` are cast to the data type of the output [ndarray][@stdlib/ndarray/ctor].

-   The function iterates over [ndarray][@stdlib/ndarray/ctor] elements according to the memory layout of an output [ndarray][@stdlib/ndarray/ctor]. Accordingly, performance degradation is possible when operating over multiple dimensions of a large non-contiguous multi-dimensional output [ndarray][@stdlib/ndarray/ctor]. In such scenarios, one may want to copy an output [ndarray][@stdlib/ndarray/ctor] to contiguous memory before filling with linearly spaced values.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var ndarray2array = require( '@stdlib/ndarray-to-array' );
var linspace = require( '@stdlib/blas-ext-linspace' );

// Create two vectors defining interval bounds:
var start = linspace( [ 5 ], 1, 5, true );
var end = linspace( [ 5 ], 5, 9, true );

// Create a grid:
var out = linspace( [ 5, 5 ], start, end, true );
console.log( ndarray2array( out ) );

// Generate linearly spaced values over multiple dimensions:
out = linspace( [ 5, 5 ], 1, 25, true, {
    'dims': [ 0, 1 ]
});
console.log( ndarray2array( out ) );

// Generate linearly spaced values over multiple dimensions in column-major order:
out = linspace( [ 5, 5 ], 1, 25, true, {
    'dims': [ 0, 1 ],
    'order': 'column-major'
});
console.log( ndarray2array( out ) );
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/blas-ext-linspace.svg
[npm-url]: https://npmjs.org/package/@stdlib/blas-ext-linspace

[test-image]: https://github.com/stdlib-js/blas-ext-linspace/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/blas-ext-linspace/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/blas-ext-linspace/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/blas-ext-linspace?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/blas-ext-linspace.svg
[dependencies-url]: https://david-dm.org/stdlib-js/blas-ext-linspace/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/blas-ext-linspace/tree/deno
[deno-readme]: https://github.com/stdlib-js/blas-ext-linspace/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/blas-ext-linspace/tree/umd
[umd-readme]: https://github.com/stdlib-js/blas-ext-linspace/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/blas-ext-linspace/tree/esm
[esm-readme]: https://github.com/stdlib-js/blas-ext-linspace/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/blas-ext-linspace/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/blas-ext-linspace/main/LICENSE

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes

[@stdlib/ndarray/base/broadcast-shapes]: https://github.com/stdlib-js/ndarray-base-broadcast-shapes

</section>

<!-- /.links -->
