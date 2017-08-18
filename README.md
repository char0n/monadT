# monadT

Transformers for monadic algebraic structures bridging types from various monadic libraries.

## Example

```javascript
const { MonetEitherT: EitherT, FlutureTMonetEither: FutureTEither } = require('monadT');
const { Future } = require('fluture');
const { Identity, Either, Maybe } = require('monet');


EitherT(Identity.of(1)); //=> Either.Right(1)
EitherT(Either.Right(1)); //=> FlutureTMonetEither(1)
EitherT(Future.of(1)); //=> FlutureTMonetEither(1)
EitherT.of(Maybe.Some(1)); //=> EitherT<Maybe.Some(1)

FutureTEither.of(Future.of(Either.Right(1))); //=> FlutureTMonetEither(1)
FutureTEither(Identity.of(1)); //=> FlutureTMonetEither(1)
FutureTEither(Future.of(1)); //=> FlutureTMonetEither(1)
FutureTEither(Either.Right(1)); //=> FlutureTMonetEither(1)
```

## Optional dependencies

Usually developers use one or two monadic libraries in their projects. For example
developer can use `monet` and `fluture` in a project and it is not convenient
to install all of the optional dependencies of this package (there may be quite a lot in the future).
We recommend to use requires from a specific modules of this library so that
you won't end up with  `Cannot find module` error when requiring.

```javascript
const { MonetEitherT: EitherT } = require('monadT/MonetEitherT');
const { FlutureTMonetEither: FutureTEither } = require('monadT');


EitherT(Identity.of(1)); //=> Either.Right(1)
EitherT(Either.Right(1)); //=> FlutureTMonetEither(1)
EitherT(Future.of(1)); //=> FlutureTMonetEither(1)
EitherT.of(Maybe.Some(1)); //=> EitherT<Maybe.Some(1)

FutureTEither.of(Future.of(Either.Right(1))); //=> FlutureTMonetEither(1)
FutureTEither(Identity.of(1)); //=> FlutureTMonetEither(1)
FutureTEither(Future.of(1)); //=> FlutureTMonetEither(1)
FutureTEither(Either.Right(1)); //=> FlutureTMonetEither(1)
```
