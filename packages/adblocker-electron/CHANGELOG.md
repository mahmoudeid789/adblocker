# v1.14.1 (Thu Apr 09 2020)

### Release Notes

_From #746_

* Make sure that all unsupported procedural selectors from cosmetic filters are dropped to ensure that we only inject valid CSS selectors.
* Fix matching of `domain=` option for domain filters in cases where specified domain is a subdomain instead of full hostname or full domain.
* Fix partyness detection for requests without a valid domain (but having a valid hostname). This fixes matching against localhost request (for instance).
* Fix engine updates stress test which allows to replay all day-to-day diffs since the beginning of times... (currently about a year) and make sure that all updates work and resulting engine is byte-identical with diff-update or full initialization.
* Fix script to analyze size of serialized engines for all presets as well as all kinds of compression (i.e. none, gzip and brotli). This allows to keep track of final size after small-strings compression was applied.

---

#### :nail_care: Polish

- Fix domain options with subdomains and more... [#746](https://github.com/cliqz-oss/adblocker/pull/746) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.14.0 (Wed Apr 08 2020)

### Release Notes

_From #738_

* Add `guessRequestTypeFromUrl` config option to all blocker classes which allows to automatically guess the type of network requests based on their URLs. This can be useful for cases where the type is either not available or not accurately inferred (e.g. when requests have time 'other').
* Fix a case where `PuppeteerBlocker` could show an async unhandled exception in console when trying to remove blocked iframes in pages.
* Fix redirection to binary resources (i.e. base64 encoded). An issue caused these resources to be corrupted which means that redirected resources were not valid (e.g. invalid PNG image).
* Redirection to local resources has been improved and will now always succeed thanks to a system of fallback. More types are also available for redirection.
* Improve API of blocker classes (i.e. PuppeteerBlocker, ElectronBlocker and WebExtensionBlocker) to allow creating custom blocking logic of resources using: `blockScripts`, `blockImages`, `blockMedias`, `blockFrames`, `blockFonts`, and `blockStyles`. These helpers can be called on any existing blocker instance, or on a new one created with the `empty()` static method.
* Add initial DSL (Domain Specific Language) to create blocking rules with a high-level API. This is used behind the scene to implement the new blocking methods now exposed by blocker instances. This new DSL should be considered alpha-quality and the API will likely change (and break) in the future. It might also be extended to handle hiding rules (a.k.a cosmetic filters).
* Fix behavior of `NetworkFilter#toString` which should now return a better pretty-printed version of the original filters whenever the `debug` option was false (in which case some information about the original raw string is lost and the string version needs to be inferred back).
* Implement handling of data: URLs. This means that the Request abstraction will now treat them as valid requests and that their type should always be inferred correctly. Moreover, the matching of data: URLs will now only take into account the prefix and ignore anything following the ',' separator.
* Requests with empty domain will not be treated as third-party anymore (this should not happen in the wild and was mostly impacting our unit tests).

---

#### :rocket: New Feature

- Various improvements [#738](https://github.com/cliqz-oss/adblocker/pull/738) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.13.1 (Fri Apr 03 2020)

#### :house: Internal

- Move from jest to mocha + chai [#682](https://github.com/cliqz-oss/adblocker/pull/682) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.12.3 (Sat Mar 28 2020)

#### :house: Internal

- Update README.md [#670](https://github.com/cliqz-oss/adblocker/pull/670) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.10.1 (Wed Mar 25 2020)

#### :bug: Bug Fix

- Abstract DOM monitoring away and fix #573 [#657](https://github.com/cliqz-oss/adblocker/pull/657) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.8.6 (Thu Feb 13 2020)

#### :nail_care: Polish

- Move BlockingContext methods back into Blocker class. [#496](https://github.com/cliqz-oss/adblocker/pull/496) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.8.4 (Thu Feb 13 2020)

#### :bug: Bug Fix

- Fix implicit tslib dependency [#494](https://github.com/cliqz-oss/adblocker/pull/494) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.8.1 (Wed Feb 12 2020)

#### :nail_care: Polish

- Expose original request details through Request class [#490](https://github.com/cliqz-oss/adblocker/pull/490) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))

---

# v1.8.0 (Wed Feb 12 2020)

#### :running_woman: Performance

- Target ES6 instead of ES3 [#489](https://github.com/cliqz-oss/adblocker/pull/489) ([@remusao](https://github.com/remusao))

#### Authors: 1

- Rémi ([@remusao](https://github.com/remusao))