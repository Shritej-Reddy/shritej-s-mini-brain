https://semver.org/

A semantic version number consists of three parts separated by dots:

- MAJOR: Incremented when there are incompatible API changes.
- MINOR: Incremented when new functionality is added in a backwards-compatible manner.
- PATCH: Incremented when bug fixes are made without affecting the API.


When we do a npm install and if the dependencies has ^ symbol then it means it will install the latest minor version

When we do a npm install and if the dependencies has ~ symbol then it means it will install the latest patch version

When we do a npm install and if the dependencies has no symbol then it means it will install the exact same version

When we do a npm install and if the dependencies has ** symbol then it means it will install the latest package version