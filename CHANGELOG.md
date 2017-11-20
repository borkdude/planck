# Change Log
All notable changes to this project will be documented in this file. This change log follows the conventions of [keepachangelog.com](http://keepachangelog.com/).

## [Unreleased]
### Added
- Site docs for `--fn-invoke-direct` ([#547](https://github.com/mfikes/planck/issues/547))

### Changed
- Update build to use Lein 2.8.1
- Eliminate doc site reference to `:static-fns` as a workaround for (fixed) JavaScriptCore perf bug.
- Update to Closure v20170910
- Update build to allow alternate `xxd -i` implementation ([#549](https://github.com/mfikes/planck/issues/549))

## [2.9.0] - 2017-11-14
### Changed
- transit-cljs 0.8.243
- Show completion candidates when hitting tab ([#527](https://github.com/mfikes/planck/issues/527))
- Remove `planck.repl/get-arglists` spec (it is non-user supplied and present by default)

### Fixed
- Fix issue where source/doc would work on private planck.repl Vars ([#542](https://github.com/mfikes/planck/issues/542))
- Fix issue where global a/b/c shadowed by locals ([#543](https://github.com/mfikes/planck/issues/543))
- Eliminate stale reference to `coercible-file?` spec ([#544](https://github.com/mfikes/planck/issues/544))

## [2.8.1] - 2017-10-03
### Fixed
- Fix Linux PPA build issue with build box home dir

## [2.8.0] - 2017-10-03
### Added
- Optimizations for source map loading when first exception is printed.
- Honor `cljs.core/*main-cli-fn*`, calling if set.
- Facsimile of `cljs.nodejs` for code calling `enable-util-print!`.

### Changed
- ClojureScript 1.9.946.

### Fixed
- Eliminate leaks and properly initialize memory.
- `planck.repl/get-arglists` now resolves symbols in current namespace.
- It is now possible to require `goog`.
- Fix SIGSEGV with glibc 2.26.

## [2.7.3] - 2017-08-17
### Fixed
- Fix issue with Ubuntu PPA release.

## [2.7.0] - 2017-08-16
### Added
- Ability to specify `-O` / `--optimizations` to apply Closure.
- Closure applied to bundled deps.
- Pretty print records.
- Update deps management for global exports, `:libs`.
- Auto-completion for symbols in Closure Library.

### Changed
- ClojureScript 1.9.908.
- Add checked-arrays to `-h` output.
- No longer bundle `goog.structs.weak` (not available).

### Fixed
- Disable `:def-emits-var` in code-loading forms.
- Increas buffers used for paths to be `PATH_MAX`.

## [2.6.0] - 2017-07-28
### Added
- Alpha support for TCP sockets in `planck.socket.alpha`.
- Support passing Maven coordinates for JAR deps.
- Hook up flush for writers and output streams.
- Hook up planck.shell/sh :in for smallish strings.
- Support for `:fn-invoke-direct` compiler option.
- Support `cljs.core/*command-line-args*`.
- Support for `:checked-arrays`.
- Make `*print-fn*` and `*print-err-fn*` like noderepljs for JavaScript objects.
- Pretty print JavaScript arrays and objects.

### Changed
- ClojureScript 1.9.854.
- Update transit-clj to 0.8.300.
- Update fipp to 0.6.8.
- Revise dump SDK option to be `-S`.

### Fixed
- Fixes crashes when using HTTP.
- Don't print `doc`s for macros that haven't been referred.
- Auto-complete after arrow and other special chars.
- Don’t demunge Planck native fns.
- Suppress additional meta printing for unknown types.
- Do a distinct in apropros to provide one response for fn-macros.

## [2.5.0] - 2017-05-26
### Changed
- ClojureScript 1.9.562.
- Pretty-print Eductions.

### Fixed
- Fix crash when making HTTP post.

## [2.4.0] - 2017-05-12
### Changed
- ClojureScript 1.9.542.
- Improve completions.

### Fixed
- Fix crash when making HTTP request.
- Fix find-doc implementation to be more accurate.
- Properly cache internal `run_timeout_fn`.

## [2.3.0] - 2017-04-18
### Added
- Show version with `-V` / `--version`.
- Ability to `-D` / `--dump-sdk`.
- SDK docs on website.
- Imitation of clojure.java.io/resource.
- Add get-arglists function (emacs integration).
- Ability to instrument bundled speced fns.

### Changed
- ClojureScript 1.9.521
- Don’t bundle cljs/core$macros.cljc or the bundle namespace.
- Make path-separator private.
- Make planck.io/build-uri private.
- Load source maps for more bundled namespaces.

### Removed
- Don't bundle `tailrecursion/cljson`.

### Fixed
- Crash if specify dumb as theme.
- Ctrl-C leads to a space after prompt.

## [2.2.0] - 2017-02-25
### Added
- Support for namespaced maps.

### Changed
- ClojureScript 1.9.494
- Deumunge $macros in symbols in macroexpand.

### Fixed
- pprint wrapping honor width.
- Better support for pasting into REPL.
- Handle comments entered in REPL.

## [2.1.0] - 2017-02-10
### Added
- Ability to use Ctrl-R to `reverse-i-search` in the REPL.
- Print `ex-data` in `pst`.
- Better error reporting for malformed scripts.
- Available via `apt-get` on Ubuntu.

### Changed
- ClojureScript 1.9.473.
- Use `poll` instead of `select` in order to async more than 1024 shell processes.

### Fixed
- Add `::body` to spec of `planck.http/post`.

## [2.0.0] - 2017-02-04
### Added
- Support for Linux.
- Async Shell.
- Hi-Res Timer.
- Interrupt Forms Generating Output.
- Source for REPL-defined forms.
- Planck Classpath Environment Variable.

### Changed
- ClojureScript 1.9.456.

## [2.0.0-rc.1] - 2017-01-27
### Changed
- ClojureScript 1.9.456.

### Fixed
- Keep script running until `sh-async` completes.

## [2.0.0-beta.6] - 2017-01-21
### Added
- `source` works for `def` forms evaluated in the REPL.

### Changed
- ClojureScript 1.9.397
- Shut down JavaScriptCore when Planck is shut down.

### Fixed
- Fix a leak.
- Fix bugs related to caching native function references.
- Fix bugs related to `JSValueRef` lifetimes.
- Fix bug when Ctrl-C out of long form.

## [2.0.0-beta.5] - 2017-01-04
### Changed
- ClojureScript 1.9.380.
- Updates to error indicator (caret).
- Optimize `-read-line` perf.
- No longer use source requiring C99 support.
- Improvements waiting for ClojureScript runtime initialization.
- Flow control when writing to Socket REPL.

### Fixed
- Fix a corner case in `BufferedReader` implementation.
- Properly handle bad file descriptors.
- Fix bugs related to secondary prompt display with `-d`.
- Fix a memory leak converting strings.
- Better handling of Socket REPL lifecycle.
- Fix a few buffer overruns.
- Properly route Socket REPL printing when under load.
- Fix crash in `file-seq`.

## [2.0.0-beta.4] - 2016-12-17
### Added
- Can compile with either gcc or clang.
- Use nanosecond-resolution timers for `time` function.
- Use Planck's `eval` when needed by `cljs.spec.test` macros.

### Changed
- ClojureScript 1.9.376.
- Syntax-hightlight specs in `doc` output.
- Various robustness revisions in C source.
- Update the copyright notices (in `-l` output).
- Pre-compile `cljs.spec.test`.

### Fixed
- Don't reload goog JS that has already been loaded.
- Avoid stack overflow with deep require tree.
- Fix the ability to do HTTP POSTs.
- Support `planck.shell/sh` child processes that produce lots of output.

## [2.0.0-beta.3] - 2016-11-27
### Added
- Now builds on NixOS and Centos.
- High resolution timer for `time` macro.
- Added `load` REPL special.

### Changed
- Use the new `require`, `require-macros`, `import`, macros from ClojureScript.

### Fixed
- Fix build on OS X 10.9.5.
- Properly serialize callbacks.
- Fix `sh-async`.
- Guard against missing JARs on classpath causing crash.
- Fix socket REPL indication display (was interleaved with other text).
- Fix endless loop hitting Ctrl-D to stop when using dumb terminal mode.

## [2.0.0-beta.2] - 2016-11-20
### Added
- Ability to install via `brew install --devel planck`.

### Changed
- ClojureScript 1.9.330.
- Add keyword completion candidates `:refer-clojure` `:exclude`.
- Build native portion (C code) with release optimizations.

### Fixed
- Properly initialize `*assert*`.
- Fix issue when cursor has to hop left.
- Fix ability to `(exit 0)`.
- Fix blocking initializing JavaScriptCore on some Unixes.

## [2.0.0-beta.1] - 2016-11-20
### Added
- Support for Linux.
- Support for `PLANCK_CLASSPATH` env var.
- Interruptibility of REPL forms producing output.
- Warn if Planck can’t write to cache path.

### Changed
- ClojureScript 1.9.293.
- Bundle `goog.labs.format.csv`.
- Abort if `-k` and `-K` specified.
- Eliminate double analysis of forms at REPL.
- Update `ns` docstring.

### Fixed
- Preserve `ns-interns` when failing to load a namespace.
- Properly track loaded foreign-libs.
- Fix segfault typing `]` after an error.

## [1.17] - 2016-09-11
### Added
- Report filename for compiler warnings and errors.

### Changed
- ClojureScript 1.9.229.
- Update bundled version of Transit to 0.8.239.
- Update bundled version of Fipp to 0.6.6.

### Fixed
- Close pipes in shell/sh.

## [1.16] - 2016-08-15
### Added
- Support reading namespaced maps.
- Support IOFactory on std streams.

### Changed
- ClojureScript 1.9.216
- Use `org.clojure/tools.reader` 1.0.0-beta3.
- Improvements to tab completions.
- Many revsions for 2.0 alpha C-based port.

### Fixed
- Properly initialize `*assert*` with session state (for `--elide-asserts`).
- Changes to support building on case-sensitive file system.

## [1.15] - 2016-06-18
### Added
- Add indicators for warnings.
- Format macroexpand output as code.
- Spec functions exposed in Planck namespaces.
- Format specs in docstrings.

### Changed
- ClojureScript 1.9.76.

### Fixed
- Wait for timers to complete before exiting (useful for `core.async`).

## [1.14] - 2016-06-16
### Added
- Support for cljs.spec.

### Changed
- ClojureScript 1.9.14.

### Fixed
- Partial fix for `eval` (#288).

## [1.13] - 2016-05-27
### Added
- Column indicators for analysis errors.
- Elide pasted prompts when pasting into REPL.

### Changed
- Isolation for Socket REPLs (`*1`, _etc._).
- Better handling of async printing.
- Add `console.error` (previously only had `console.log`).
- Align secondary prompts for 1-char namespaces.

### Fixed
- Properly handle case when `*print-newline*` is set to `false`.

## [1.12.1] - 2016-05-18
### Fixed
- Fix slurp failing on Mavericks.
- Fix crash with multi-line forms and single-character namespaces.

## [1.12] - 2016-05-15
### Added
- Pretty print REPL results using Fipp with syntax highlighting.
- A new `planck.http` namespace supporting `get` and `post`.
- Support `:foreign-libs` in `deps.cljs` embedded in JARs.
- Support re-configuring control keys used in REPL.
- Support disabling asserts at launch time (like `:elide-asserts`).
- Add simpler cache support via `-K` to create `.planck_cache` dir.

### Changed
- console log simply logs text (w/o NSLog info).
- Don't refer to Maven (brew install w/o Java).
- Use `tools.reader` 1.0.0-beta1.
- Use Parinfer 1.8.1.
- Clean up stack traces (demunge symbols, elide `-invoke`).
- Mark a few vars as private.
- Minimal OS required Mavericks (was Lion).

### Fixed
- Properly align docstring output for vars like `some->`.
- Fix a bug where caches were not invalided when using an updated JAR.

## [1.11] - 2016-04-25
### Added
- A quiet mode that disables banner and other output.
- Support for `clojure.core.reducers`.
- Ability to use `cljs.js` itself within Plank via `planck.core/init-empty-state`.
- Autocompletion on commonly used keywords and other autocomplete improvements.

### Changed
- Update to ClojureScript 1.8.51.
- Use CloureScript `cljs.test` (instead of previous port).

### Fixed
- Fix for multi-arg file, add File/toString.
- Exit with failure when port is bound.
- Fix for caching top-level files.
- Don't inadvertently load bundled artifacts from classpath.

## [1.10] - 2016-03-02
### Added
- Bundle port of `cljs.test` for use in bootstrap ([post](http://blog.fikesfarm.com/posts/2016-02-27-testing-with-planck.html)).
- Colors (with light and dark theme) ([post](http://blog.fikesfarm.com/posts/2016-02-04-planck-colors.html)).
- Indentation (via Parinfer) ([post](http://blog.fikesfarm.com/posts/2016-02-10-indenting-with-parinfer.html)).
- `eval` and friends `resolve`, `ns-resolve`, `intern` ([post](http://blog.fikesfarm.com/posts/2016-01-22-clojurescript-eval.html)).
- Securely prompt for and read password.
- Source mapping for user code.
- `with-open` and `line-seq`.
- `with-sh-dir` and `with-sh-env`.
- `sh` accepts string and file.
- Honor `:forms` in `doc` output.
- `planck.io/file-attributes` (like `fstat`).
- `find-doc`.
- Startup banner with helpful instructions.

### Changed
- Use ClojureScript master (1.8.28).
- Throw exception on error from `sh`.
- `doc` for `catch`, `finally`, `&`.
- AOT compile Planck macro namespaces ([post](http://blog.fikesfarm.com/posts/2016-02-03-planck-macros-aot.html)).

### Fixed
- Throw if using closed file.
- Properly index open JARs (needed for large classpaths).
- You can now `require` `planck.repl` namespace.
- Don't let `cljs.env` be inadvertently reloaded (clears `*compiler*`).
- Search all loaded macro namespaces for docs.

## [1.9] - 2016-01-20
### Added
- New website with comprehensive User Guide: [http://planck-repl.org](http://planck-repl.org).
- Socket REPL.
- Lazily load core analysis caches (2x faster in some cases).
- `apropos` and `dir` support.
- Protocol method doc output.
- Doc support for namespaces.
- Bundle `clojure.zip`, `clojure.data`.
- Multiple forms on a single REPL line.

### Changed
- Use ClojureScript 1.7.228.
- Eliminate noisy var code when in verbose mode.
- Don't use default classpath of `.`.
- Add = signs in `-h` output for long args.
- Mention namespace for `*command-line-args*` in `-h`.
- Improve exception printing.

### Fixed
- Fix crash if command line arg missing.
- Fix so you can use reader literals.
- Fix `source` failing on VMs.
- Purge analysis cache when reloading (allows reloading namespace with constant).
- Fix extra blank lines that appear when pasting.
- Proper caching of macro namespaces.
- If require fails, restore analysis cache state.
- Fix for syntax quote.
- Honor `:static-fns` for cache invalidation.
- Fix for `load-file`.

## [1.8] - 2015-11-06
### Added
- Tab completion for core macros.
- Support for `:static-fns` (via `-s` or `--static-fns`).
- Analysis / compilation cache (`-k <cache dir>` option).
- `planck.core/*planck-version*`.

### Changed
- Use ClojureScript 1.7.170.
- Can now `(require 'cljs.analyzer)`.

### Fixed
- `0` is truthy.
- `doc` fix when using namespace alias.
- `source` fix when using namespace alias.

## [1.7] - 2015-10-03
### Added
- Support OS X 10.11 El Capitan.
- Support OS X 10.7 Lion.
- Support for setTimeout.
- Errors emitted when `spit` and `slurp` fail.
- Support terminating REPL by typing `quit` or `exit`.

### Changed
- Use ClojureScript 1.7.122.
- Experimental analysis / compilation cache (`-k <cache dir>` option).

### Fixed
- `source` REPL special for `planck` namespace code.
- Fall back to ASCII encoding if needed when using `planck.shell`.
- Eliminate residual processing of `b` option.
- Properly merge requires (honoring established namespace aliases).
- Proper VT100 escape sequences (brace matching in iTerm).

## [1.6] - 2015-08-22
### Added
- Support JAR deps.
- Support `-c` / `--classpath` for specifying source directories and JAR deps.
- Support for OS X 10.8 Mountain Lion.
- Ship with bundled `cljs.pprint` and `cljs.test`.
- Support `source` REPL special.
- Support `import` REPL special.
- Support for `planck.core/*command-line-args*`.
- Support `:encoding` option for file I/O.
- Support for byte-oriented streams (`planck.io/input-stream` and `planck.io/output-stream`).
- `doc` output for macros.
- `doc` and tab completion for special forms.

### Changed
- Read pre-compiled namespaces and analysis metadata for faster loading.
- Deprecate `-s` / `--src` in favor of using `-c` / `--classpath`.
- Revise `planck.core/file-seq` to be lazy (in terms of `tree-seq`).

### Fixed
- Capture stderr for `planck.shell/sh`.
- Fix a glitch in brace highlighting when vertically aligned.
- Properly exit if `planck.core/exit` is called with `0`.
- Don't block on I/O in `planck.core/shell/sh`.
- Properly decode UTF-8 from stdin.

## [1.5] - 2015-08-15
### Added
- Brace highlighting (cursor temporarily jumps to previous matching brace).
- Improved `require` & `require-macros` (`:as` _etc._, error reporting).
- `file-seq` support
- `load-file` REPL special.
- Exit codes (`1` if unhandled exception, or explcit via `planck.core/exit`).
- Hit Ctrl-C to get out of a form and get a new prompt.
- Doc output improvement.
- Google Closure indexed so you can require things from there.
- Ship with `cljs.test` / `cljs.pprint` and lots of Google Closure.
- `-d` / `--dumb-terminal` option (facilitates `rlwrap`).
- `-l` / `--legal` to show licenses / copyrights.

### Changed
- Rearranged so that there is now a `planck.core` to hold core fns.
- Smaller binary (gzipped ClojureScript runtime internally).

### Fixed
- Don't lock up on syntax error.

## [1.4] - 2015-08-09
### Added
- 2× launch perf improvement (for scripts).
- Execute host commands via `planck.shell` namespace.
- Streaming file I/O: `reader`/`writer` using `IOFactory`.
- Repeated ordered `-e` `-i` options.
- Improved tab completion (considers namespaces, specials, _etc_.).
- `pst` (print stack trace) support.
- Mavericks support.

### Changed
- ClojureScript 1.7.28 -> 1.7.48.
- Work towards improved `doc` support.

### Fixed
- Crash with single-char ns.
- Printing to `stderr` via `*print-err-fn*`.
- Properly suppress printing of `nil` values for launch opts.
- Fixes some crashes mishandling UTF-8.

## [1.3] - 2015-08-03
### Changed
- Updated to no longer depend on CocoaPods.
- Fast startup even with readline support.
- Tweaks for tab completion (macros included, private vars excluded).
- Cleanup startup options, especially with respect to those used for dev.

## [1.2] - 2015-08-02
### Added
- Source mapping of stack traces.
- Readline support and auto-completion.

## [1.1] - 2015-08-01
### Added
- Adds `read-line` support.

### Fixed
- Fixes ^D so that it exits REPL.

## [1.0] - 2015-07-31
### Added
- Initial release.

[Unreleased]: https://github.com/mfikes/planck/compare/2.9.0...HEAD
[2.9.0]: https://github.com/mfikes/planck/compare/2.8.1...2.9.0
[2.8.1]: https://github.com/mfikes/planck/compare/2.8.0...2.8.1
[2.8.0]: https://github.com/mfikes/planck/compare/2.7.3...2.8.0
[2.7.3]: https://github.com/mfikes/planck/compare/2.7.0...2.7.3
[2.7.0]: https://github.com/mfikes/planck/compare/2.6.0...2.7.0
[2.6.0]: https://github.com/mfikes/planck/compare/2.5.0...2.6.0
[2.5.0]: https://github.com/mfikes/planck/compare/2.4.0...2.5.0
[2.4.0]: https://github.com/mfikes/planck/compare/2.3.0...2.4.0
[2.3.0]: https://github.com/mfikes/planck/compare/2.2.0...2.3.0
[2.2.0]: https://github.com/mfikes/planck/compare/2.1.0...2.2.0
[2.1.0]: https://github.com/mfikes/planck/compare/2.0.0...2.1.0
[2.0.0]: https://github.com/mfikes/planck/compare/2.0.0-rc.1...2.0.0
[2.0.0-rc.1]: https://github.com/mfikes/planck/compare/2.0.0-beta.6...2.0.0-rc.1
[2.0.0-beta.6]: https://github.com/mfikes/planck/compare/2.0.0-beta.5...2.0.0-beta.6
[2.0.0-beta.5]: https://github.com/mfikes/planck/compare/2.0.0-beta.4...2.0.0-beta.5
[2.0.0-beta.4]: https://github.com/mfikes/planck/compare/2.0.0-beta.3...2.0.0-beta.4
[2.0.0-beta.3]: https://github.com/mfikes/planck/compare/2.0.0-beta.2...2.0.0-beta.3
[2.0.0-beta.2]: https://github.com/mfikes/planck/compare/2.0.0-beta.1...2.0.0-beta.2
[2.0.0-beta.1]: https://github.com/mfikes/planck/compare/1.17...2.0.0-beta.1
[1.17]: https://github.com/mfikes/planck/compare/1.16...1.17
[1.16]: https://github.com/mfikes/planck/compare/1.15...1.16
[1.15]: https://github.com/mfikes/planck/compare/1.14...1.15
[1.14]: https://github.com/mfikes/planck/compare/1.13...1.14
[1.13]: https://github.com/mfikes/planck/compare/1.12.1...1.13
[1.12.1]: https://github.com/mfikes/planck/compare/1.12...1.12.1
[1.12]: https://github.com/mfikes/planck/compare/1.11...1.12
[1.11]: https://github.com/mfikes/planck/compare/1.10...1.11
[1.10]: https://github.com/mfikes/planck/compare/1.9...1.10
[1.9]: https://github.com/mfikes/planck/compare/1.8...1.9
[1.8]: https://github.com/mfikes/planck/compare/1.7...1.8
[1.7]: https://github.com/mfikes/planck/compare/1.6...1.7
[1.6]: https://github.com/mfikes/planck/compare/1.5...1.6
[1.5]: https://github.com/mfikes/planck/compare/1.4...1.5
[1.4]: https://github.com/mfikes/planck/compare/1.3...1.4
[1.3]: https://github.com/mfikes/planck/compare/1.2...1.3
[1.2]: https://github.com/mfikes/planck/compare/1.1...1.2
[1.1]: https://github.com/mfikes/planck/compare/1.0...1.1
[1.0]: https://github.com/mfikes/planck/compare/63d50fe673c147e2d5810424daa75344f36b33bb...1.0