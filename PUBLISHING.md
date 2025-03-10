# Generating a PDF from ecmarkup

In order to produce a PDF, the front matter `title`, `shortname`, `version`, and `date` are **mandatory**. If generating a final annual edition, date should reflect the date of the Ecma GA which will ratify the Standard. For example:

```
title: ECMAScript® 2024 Language Specification
shortname: ECMA-262
version: 15<sup>th</sup> Edition
date: 2024-06-25
```

To generate markup for use in PDF conversion, make sure to include the options `--assets`, `--assets-dir`, and `--printable`. If you have images and styles to include, make sure to move them into your assets directory before running `ecmarkup`. For example:

```shell
mkdir -p out &&
cp -R images out &&
ecmarkup --assets external --assets-dir out --printable spec.html out/index.html
```

Then, from your spec's working directory, run [`prince`](https://www.princexml.com/) to generate your PDF.

```shell
cd path/to/spec
prince --script ./node_modules/ecmarkup/js/print.js out/index.html -o path/to/output.pdf
```

This has been extensively tested with Prince 15. Earlier and later editions not guaranteed.
