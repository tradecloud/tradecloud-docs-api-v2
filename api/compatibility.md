# Compatibility

## Backward compatibility

**Tradecloud** promises and is responsible that the **order integration API** and **web hook request URL and body** are **backwards** compatible. **Other API's may change without notice.**

The ****order integration API and web hook request URL and body are compatible with previous versions of itself, which means

* Fields will not be removed, renamed or become mandatory
* Values will not be removed, renamed or become mandatory

## Forward compatibility

The **customer** is responsible that the **API client** and **web hook service** is **forward** compatible.  
  
The API client and web hook service are compatible with future versions of itself, which means:

* Fields can be added in the future
* Values can be added in the future
* Events can be added to the web hook in the future

In practice:

* The API client should only expect fields in the response body it is actually using
* The web hook service should only expect fields in the request body it is actually using
* fields may move according to the [JSON](https://tradecloud.gitbook.io/api/api/standards#json) standard, especially:  _An object is an unordered collection of zero or more name/value pairs_

