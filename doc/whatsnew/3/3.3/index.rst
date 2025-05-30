
***************************
 What's New in Pylint 3.3
***************************

.. toctree::
   :maxdepth: 2

:Release:3.3
:Date: 2024-09-20

Summary -- Release highlights
=============================

.. towncrier release notes start

What's new in Pylint 3.3.7?
---------------------------
Release date: 2025-05-04


False Positives Fixed
---------------------

- Comparisons between two calls to `type()` won't raise an ``unidiomatic-typecheck`` warning anymore, consistent with the behavior applied only for ``==`` previously.

  Closes #10161 (`#10161 <https://github.com/pylint-dev/pylint/issues/10161>`_)



Other Bug Fixes
---------------

- Fixed a crash when importing a class decorator that did not exist with the same name as a class attribute after the class definition.

  Closes #10105 (`#10105 <https://github.com/pylint-dev/pylint/issues/10105>`_)

- Fix a crash caused by malformed format strings when using `.format` with keyword arguments.

  Closes #10282 (`#10282 <https://github.com/pylint-dev/pylint/issues/10282>`_)

- Using a slice as a class decorator now raises a ``not-callable`` message instead of crashing. A lot of checks that dealt with decorators (too many to list) are now shortcut if the decorator can't immediately be inferred to a function or class definition.

  Closes #10334 (`#10334 <https://github.com/pylint-dev/pylint/issues/10334>`_)



Other Changes
-------------

- The algorithm used for ``no-member`` suggestions is now more efficient and cuts the
  calculation when the distance score is already above the threshold.

  Refs #10277 (`#10277 <https://github.com/pylint-dev/pylint/issues/10277>`_)



What's new in Pylint 3.3.6?
---------------------------
Release date: 2025-03-20


False Positives Fixed
---------------------

- Fix a false positive for `used-before-assignment` when an inner function's return type
  annotation is a class defined at module scope.

  Closes #9391 (`#9391 <https://github.com/pylint-dev/pylint/issues/9391>`_)



What's new in Pylint 3.3.5?
---------------------------
Release date: 2025-03-09


False Positives Fixed
---------------------

- Fix false positives for `use-implicit-booleaness-not-comparison`, `use-implicit-booleaness-not-comparison-to-string`
  and `use-implicit-booleaness-not-comparison-to-zero` when chained comparisons are checked.

  Closes #10065 (`#10065 <https://github.com/pylint-dev/pylint/issues/10065>`_)

- Fix a false positive for ``invalid-getnewargs-ex-returned`` when the tuple or dict has been assigned to a name.

  Closes #10208 (`#10208 <https://github.com/pylint-dev/pylint/issues/10208>`_)

- Remove `getopt` and `optparse` from the list of deprecated modules.

  Closes #10211 (`#10211 <https://github.com/pylint-dev/pylint/issues/10211>`_)



Other Bug Fixes
---------------

- Fixed conditional import x.y causing false positive possibly-used-before-assignment.

  Closes #10081 (`#10081 <https://github.com/pylint-dev/pylint/issues/10081>`_)

- Fix a crash when something besides a class is found in an except handler.

  Closes #10106 (`#10106 <https://github.com/pylint-dev/pylint/issues/10106>`_)

- Fixed raising invalid-name when using camelCase for private methods with two leading underscores.

  Closes #10189 (`#10189 <https://github.com/pylint-dev/pylint/issues/10189>`_)



Other Changes
-------------

- Upload release assets to PyPI via Trusted Publishing.

  Closes #10256 (`#10256 <https://github.com/pylint-dev/pylint/issues/10256>`_)



What's new in Pylint 3.3.4?
---------------------------
Release date: 2025-01-28


Other Bug Fixes
---------------

- Fixes "skipped files" count calculation; the previous method was displaying an arbitrary number.

  Closes #10073 (`#10073 <https://github.com/pylint-dev/pylint/issues/10073>`_)

- Fixes a crash that occurred when pylint was run in a container on a host with cgroupsv2 and restrictions on CPU usage.

  Closes #10103 (`#10103 <https://github.com/pylint-dev/pylint/issues/10103>`_)

- Relaxed the requirements for isort so pylint can benefit from isort 6.

  Closes #10203 (`#10203 <https://github.com/pylint-dev/pylint/issues/10203>`_)



What's new in Pylint 3.3.3?
---------------------------
Release date: 2024-12-23


False Positives Fixed
---------------------

- Fix false positives for ``undefined-variable`` for classes using Python 3.12
  generic type syntax.

  Closes #9335 (`#9335 <https://github.com/pylint-dev/pylint/issues/9335>`_)

- Fix a false positive for `use-implicit-booleaness-not-len`. No lint should be emitted for
  generators (`len` is not defined for generators).

  Refs #10100 (`#10100 <https://github.com/pylint-dev/pylint/issues/10100>`_)



Other Bug Fixes
---------------

- Fix ``Unable to import 'collections.abc' (import-error)`` on Python 3.13.1.

  Closes #10112 (`#10112 <https://github.com/pylint-dev/pylint/issues/10112>`_)



What's new in Pylint 3.3.2?
---------------------------
Release date: 2024-12-01


False Positives Fixed
---------------------

- Fix a false positive for `potential-index-error` when an indexed iterable
  contains a starred element that evaluates to more than one item.

  Closes #10076 (`#10076 <https://github.com/pylint-dev/pylint/issues/10076>`_)



Other Bug Fixes
---------------

- Fixes the issue with --source-root option not working when the source files are in a subdirectory of the source root (e.g. when using a /src layout).

  Closes #10026 (`#10026 <https://github.com/pylint-dev/pylint/issues/10026>`_)



What's new in Pylint 3.3.1?
---------------------------
Release date: 2024-09-24


False Positives Fixed
---------------------

- Fix regression causing some f-strings to not be inferred as strings.

  Closes #9947 (`#9947 <https://github.com/pylint-dev/pylint/issues/9947>`_)



What's new in Pylint 3.3.0?
---------------------------
Release date: 2024-09-20


Changes requiring user actions
------------------------------

- We migrated ``symilar`` to argparse, from getopt, so the error and help output changed
  (for the better). We exit with 2 instead of sometime 1, sometime 2. The error output
  is not captured by the runner anymore. It's not possible to use a value for the
  boolean options anymore (``--ignore-comments 1`` should become ``--ignore-comments``).

  Refs #9731 (`#9731 <https://github.com/pylint-dev/pylint/issues/9731>`_)



New Features
------------

- Add new `declare-non-slot` error which reports when a class has a `__slots__` member and a type hint on the class is not present in `__slots__`.

  Refs #9499 (`#9499 <https://github.com/pylint-dev/pylint/issues/9499>`_)



New Checks
----------

- Added `too-many-positional-arguments` to allow distinguishing the configuration for too many
  total arguments (with keyword-only params specified after `*`) from the configuration
  for too many positional-or-keyword or positional-only arguments.

  As part of evaluating whether this check makes sense for your project, ensure you
  adjust the value of `--max-positional-arguments`.

  Closes #9099 (`#9099 <https://github.com/pylint-dev/pylint/issues/9099>`_)

- Add `using-exception-groups-in-unsupported-version` and
  `using-generic-type-syntax-in-unsupported-version` for uses of Python 3.11+ or
  3.12+ features on lower supported versions provided with `--py-version`.

  Closes #9791 (`#9791 <https://github.com/pylint-dev/pylint/issues/9791>`_)

- Add `using-assignment-expression-in-unsupported-version` for uses of `:=` (walrus operator)
  on Python versions below 3.8 provided with `--py-version`.

  Closes #9820 (`#9820 <https://github.com/pylint-dev/pylint/issues/9820>`_)

- Add `using-positional-only-args-in-unsupported-version` for uses of positional-only args on
  Python versions below 3.8 provided with `--py-version`.

  Closes #9823 (`#9823 <https://github.com/pylint-dev/pylint/issues/9823>`_)

- Add ``unnecessary-default-type-args`` to the ``typing`` extension to detect the use
  of unnecessary default type args for ``typing.Generator`` and ``typing.AsyncGenerator``.

  Refs #9938 (`#9938 <https://github.com/pylint-dev/pylint/issues/9938>`_)



False Negatives Fixed
---------------------

- Fix computation of never-returning function: `Never` is handled in addition to `NoReturn`, and priority is given to the explicit `--never-returning-functions` option.

  Closes #7565. (`#7565 <https://github.com/pylint-dev/pylint/issues/7565>`_)

- Fix a false negative for `await-outside-async` when await is inside Lambda.

  Refs #9653 (`#9653 <https://github.com/pylint-dev/pylint/issues/9653>`_)

- Fix a false negative for ``duplicate-argument-name`` by including ``positional-only``, ``*args`` and ``**kwargs`` arguments in the check.

  Closes #9669 (`#9669 <https://github.com/pylint-dev/pylint/issues/9669>`_)

- Fix false negative for `multiple-statements` when multiple statements are present on `else` and `finally` lines of `try`.

  Refs #9759 (`#9759 <https://github.com/pylint-dev/pylint/issues/9759>`_)

- Fix false negatives when `isinstance` does not have exactly two arguments.
  pylint now emits a `too-many-function-args` or `no-value-for-parameter`
  appropriately for `isinstance` calls.

  Closes #9847 (`#9847 <https://github.com/pylint-dev/pylint/issues/9847>`_)



Other Bug Fixes
---------------

- `--enable` with `--disable=all` now produces an error, when an unknown msg code is used. Internal `pylint` messages are no longer affected by `--disable=all`.

  Closes #9403 (`#9403 <https://github.com/pylint-dev/pylint/issues/9403>`_)

- Impossible to compile regexes for paths in the configuration or argument given to pylint won't crash anymore but
  raise an argparse error and display the error message from ``re.compile`` instead.

  Closes #9680 (`#9680 <https://github.com/pylint-dev/pylint/issues/9680>`_)

- Fix a bug where a ``tox.ini`` file with pylint configuration was ignored and it exists in the current directory.

  ``.cfg`` and ``.ini`` files containing a ``Pylint`` configuration may now use a section named ``[pylint]``. This enhancement impacts the scenario where these file types are used as defaults when they are present and have not been explicitly referred to, using the ``--rcfile`` option.

  Closes #9727 (`#9727 <https://github.com/pylint-dev/pylint/issues/9727>`_)

- Improve file discovery for directories that are not python packages.

  Closes #9764 (`#9764 <https://github.com/pylint-dev/pylint/issues/9764>`_)



Other Changes
-------------

- Remove support for launching pylint with Python 3.8.
  Code that supports Python 3.8 can still be linted with the ``--py-version=3.8`` setting.

  Refs #9774 (`#9774 <https://github.com/pylint-dev/pylint/issues/9774>`_)

- Add support for Python 3.13.

  Refs #9852 (`#9852 <https://github.com/pylint-dev/pylint/issues/9852>`_)



Internal Changes
----------------

- All variables, classes, functions and file names containing the word 'similar', when it was,
  in fact, referring to 'symilar' (the standalone program for the duplicate-code check) were renamed
  to 'symilar'.

  Closes #9734 (`#9734 <https://github.com/pylint-dev/pylint/issues/9734>`_)

- Remove old-style classes (Python 2) code and remove check for new-style class since everything is new-style in Python 3. Updated doc for exception checker to remove reference to new style class.

  Refs #9925 (`#9925 <https://github.com/pylint-dev/pylint/issues/9925>`_)
