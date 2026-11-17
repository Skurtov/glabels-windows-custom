# Patches

Any `*.patch` file dropped in this directory is applied to the upstream `glabels-qt`
checkout with `git apply`, in alphabetical order, before the build is configured.

Use this for fixes that are needed to build a given upstream revision on Windows and that
have not landed upstream yet. Keep each patch minimal, name it `NNNN-short-description.patch`,
and add a comment at the top explaining why it exists and what makes it removable.

## Current patches

| Patch | Why |
|:--|:--|
| `0001-no-lupdate-during-build.patch` | The upstream build regenerates the two C-locale `.ts` files with `lupdate` on every build. Qt 6's `lupdate` is the clang-based parser and needs `libclang.dll`, which the `qttools` archive fetched by aqtinstall does not contain, so it dies with `STATUS_DLL_NOT_FOUND`. Both `.ts` files are committed upstream, so the patch compiles them with `lrelease` instead — which is all a packaging build needs. |
| `0002-merge-filter-box.patch` | **Feature, not a build fix.** Adds a filter box, a shown/selected record counter and "Select shown" / "Unselect shown" buttons to the Merge record list, so one record can be found and ticked in a long merge file. Not unmodified upstream: keep this patch only in a fork that wants the feature. Removable if upstream adds an equivalent. |
| `0003-date-field.patch` | **Feature, not a build fix.** Adds a built-in `${DATE}` substitution field that is replaced by just the date when the label is printed, plus a "Date when printed" section in the editor's Insert substitution field menu offering the common date formats (system default, ISO, dd/MM/yyyy, MM/dd/yyyy, dd.MM.yyyy, dd-MM-yyyy, yyyy/MM/dd, written month, compact). Not unmodified upstream: keep this patch only in a fork that wants the feature. Removable if upstream adds an equivalent. |
