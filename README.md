# Overview
This repo contains various sets of `.traineddata` that can be used by Tesseract.js.  This includes the files used by Tesseract.js by default, as well as alternative versions.  The contents of the files, and how to use them with Tesseract.js, are explained below.

## Language Data
A description of each set of files is below.  The source is also listed, although the version used here may not reflect the latest version of the files in the repo linked.

- `4.0.0_best_int` - Integerized Version of "Tessdata Best"
	- OEM: LSTM only
	- Used by Tesseract.js by default: Yes.
		- This is the default data used when OEM is set to LSTM only, which is the default.
	- Published to NPM package: Yes.
- `4.0.0` - "Tessdata"
	- OEM: LSTM + Legacy
		- An integerized version of "Tessdata Best" for the LSTM engine is included, in addition to data for the Legacy data.
	- Used by Tesseract.js by default: Yes.
		- This is the default data used when OEM is set to Legacy or LSTM with Legacy fallback.
	- Published to NPM package: Yes.
	- Source: https://github.com/tesseract-ocr/tessdata
- `4.0.0-fast` - "Tessdata Fast"
	- OEM: LSTM only
	- Used by Tesseract.js by default: No.
	- Published to NPM package: No.
	- Source: https://github.com/tesseract-ocr/tessdata_fast
- `4.0.0_best` - "Tessdata Best"
	- OEM: LSTM only
	- Used by Tesseract.js by default: No.
		- This data can be *significantly* larger than the integerized version and can result in longer runtimes.  Results may be more accurate, however the difference usually ranges from negligible to marginal.
		- Before using this data, developers should review file sizes and run accuracy/performance tests to confirm implementing is worthwhile.
	- Published to NPM package: No.
	- Source: https://github.com/tesseract-ocr/tessdata_best
- `3.0.2` - Historic Tessdata files from Tesseract v3
	- OEM: Legacy only
	- Used by Tesseract.js by default: No.
		- These are old files and may be removed from this repo at some point.
	- Published to NPM package: No.

## NPM Packages
The `4.0.0` and `4.0.0_best_int` files for each language are published in a language-specific NPM package.  Each language has its own package since combining into a single package would lead to an enormous download.  The packages are named `@tesseract.js-data/{lang}`.  For example, the English package is named `@tesseract.js-data/eng`.

# Using Language Data with Tesseract.js
See the Tesseract.js documentation for instructions on how to set `langPath` manually.  Details regarding where the files in this repo can be found are below.
## CDNs
These files can be accessed using any CDN that automatically mirrors NPM.  Popular examples are below.
### JSDelivr (Default)
By default, Tesseract.js uses the JSDelivr CDN.  The link for the default English data on JSDelivr is below.
https://cdn.jsdelivr.net/npm/@tesseract.js-data/eng@1.0.0/4.0.0_best_int/eng.traineddata.gz
### Unpkg
Unpkg is another CDN that mirrors NPM.  In most regions, unpkg appears to be slightly less reliable than JSDelivr (although still usable).  However, users have reported that unpkg is accessible in parts of China that JSDelivr is blocked in, so use unpkg for that reason.  Discussion regarding this issue, as well as example code that switches from JSDelivr to `unkpg`, can be found [here](https://github.com/naptha/tesseract.js/issues/899#issuecomment-1975051720).

The link for the default English data on unkpkg is below.
https://unpkg.com/@tesseract.js-data/eng/4.0.0_best_int/eng.traineddata.gz
## Local Copy
Users are free to use their own local copy of these files rather than relying on a remote CDN.  For Node.js, you can simply add the relevant NPM packages as a dependency, or download the file and include it as a project resource.  For the browser version, simply download the relevant files and host them yourself on your website.
## GitHub Pages Site (Depreciated)
**The `tessdata.projectnaptha.com` site is depreciated, and is no longer updated.  Do not point new code to this site.**

In old versions of Tesseract.js, the default `langPath` location was a simple GitHub pages site that hosted this repo.  However, in addition to users reporting that GitHub pages was unreliable, this repo is now over the GitHub pages size limit.  Therefore, that site is no longer updated.  The site is being left as-is to avoid breaking old code, however developers are encouraged to switch.
