# Summary

This tests contains an app with a main page and sub pages.
The main page contains a list of buttons; each button leads to a designated sub page when tapped on.
Each sub page should displays some simple UIs to screenshot tested.

The flutter driver test runs the app and opens each page to take a screenshot.
Then it compares the screenshots with golden files stored on Flutter Gold.

Note that new binaries can't be checked in the Flutter repo, so use [Flutter Gold](https://github.com/flutter/flutter/wiki/Writing-a-golden-file-test-for-package:flutter) instead.

# Reconstruction

We are currently in the process of moving this test to use golden API. The configuration guide below might need to be updated after that is done.

# Add a new page to test

1. Create a new class which extends `Page` and implement the UI to be tested in the `build` method.
2. The new class should set a static `title` and `key`
3. Add an instance of the new class to the `_allPages` list in the `main.dart`
4. Create a new test case similar to `"'A page with an image screenshot"` in `test_driver/main_test.dart` to run the screenshot test.
5. Create directories for the test: `test_driver/goldens/<some_test_page_name>` should be created before running the test based on the target platform the test is designed to run.

An example of a `Page` subclass can be found in `lib/image_page.dart`

# Environments

* Device Lab which runs the app on iPhone 6.
* LUCI which runs the app on a Fuchsia NUC device.
