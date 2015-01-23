# AnyHTTP

AnyHTTP is an implementation-agnostic JavaScript interface for making
HTTP calls from the browser or a NodeJS environment.

Libraries requiring HTTP calls can depend on the interface while
letting the caller provide the implementation.  That way, a library
doesn't have to explicitly depend on an HTTP library; it merely
depends on the abstract interface.

## Example

``` javascript
/* == library.js == */

export function getFirstWord(anyHttp, url) {
  return anyHttp.get(url).then(response => {
    return response.body.split(' ')[0];
  })
}


/* == consumer.js == */
import {getFirstWord} from 'library';
import {Http} from 'any-http-reqwest';

var httpImplem = new Http;
var uri = 'http://example.com';

getFirstWord(httpImplem, uri).then(word => {
  console.log("first word:", word);
})
```

## Interface

TODO: describe the interface

## Adapters

Adapters are thin wrapper libraries that implement the AnyHTTP
interface on top of existing HTTP libraries:

- [reqwest](https://github.com/argo-rest/any-http-reqwest)
- [jQuery](https://github.com/argo-rest/any-http-jquery)
- [AngularJS](https://github.com/argo-rest/any-http-angular)
- (to be extracted into its own repo) request (NodeJS)

## Known uses

- [theseus](https://github.com/argo-rest/theseus)

## See also

- [AnyPromise](https://github.com/argo-rest/any-promise)
