# screenshot-tests-for-android

screenshot-tests-for-android is a library that can generate fast
deterministic screenshots while running instrumentation tests in
android.

We mimic Android's measure(), layout() and draw() to generate screenshots
on the test thread. By not having to do the rendering on a separate
thread we have control over animations and handler callbacks which
makes the screenshots extremely deterministic and reliable for catching
regressions in continuous integration.

We also provide utilities for using screenshot tests during the development
process. With these scripts you can iterate on a view or layout and quickly
see how the view renders in real android code, without having to
build the whole app. You can also render the view in multiple configurations
at one go.

## Documentation

Take a look at the documentation at http://facebook.github.io/screenshot-tests-for-android/#getting-started

## Requirements

screenshot-tests-for-android is known to work with Mac OS X or Linux.

The host tooling probably doesn't work on Windows, but can be made to
work with a little effort. We'll happily accept pull requests!

You need python-2.7 for the gradle plugin to work, and we also
recommending installing the python-pillow library which is required
for recording and verifying screenshots.

## Building screenshot-tests-for-android

You don't have to build screenshot-tests-for-android from scratch if
you don't plan to contribute. All artifacts are available from Maven
Central.

If you plan to contribute, this is the code is broken up into two
parts:

* The `core` library is packaged as part of your instrumentation tests
  and generates screenshots on the device.

* The `plugin` library adds Gradle tasks to make it easier to work
  with screenshot tests.

In addition you'll find python code inside `plugin/src/py`. This code
is packaged into the gradle plugin.

We have tests for the python code and the core library. Run these
commands to run all the tests:

```bash
  $ gradle :plugin:pyTests
  $ gradle :core:connectedAndroidTest
```

Both need a running emulator.

You can install all the artifacts to your local maven repository using

```bash
  $ gradle installAll
```

## Join the screenshot-tests-for-android community

* Website: http://facebook.github.io/screenshot-tests-for-android
* Discussion group:
   https://groups.google.com/forum/#!forum/screenshot-tests-for-android<br />
   screenshot-tests-for-android@googlegroups.com

See the CONTRIBUTING file for how to help out.

## Authors

screenshot-tests-for-android has been written by Arnold Noronha (arnold@fb.com)
You can reach him at @tdrhq on GitHub.

## License

screenshot-tests-for-android is BSD-licensed. We also provide an
additional patent grant.
