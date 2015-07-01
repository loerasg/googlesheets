## Test environments
* local OS X install, R 3.2.1
* ubuntu 12.04 on travis-ci, R 3.2.1
* win-builder, devel and release 3.2.1

This is a resubmission. The first time Kurt said "You misuse file LICENSE: for MIT it should only be the completed template." So I have fixed that.

## R CMD check results

There were no ERRORs or WARNINGs. 

There are two NOTEs:

Note #1:

* checking CRAN incoming feasibility ... NOTE
Maintainer: 'Jennifer Bryan <jenny@stat.ubc.ca>'
New submission

License components with restrictions and base license permitting such:
  MIT + file LICENSE
File 'LICENSE':
  YEAR: 2015
  COPYRIGHT HOLDER: Jennifer Bryan, Joanna Zhao

Note #2, seen on winbuilder, both R 3.2.1 and R Under development (unstable):

* checking re-building of vignette outputs ... NOTE
Error in re-building vignettes:
  ...
Quitting from lines 31-35 (basic-usage.Rmd) 
Error: processing vignette 'basic-usage.Rmd' failed with diagnostics:
oauth_listener() needs an interactive environment.
Execution halted

My vignette uses my package with OAuth2 to read and write via the Google Sheets API. Since there is no way to securely upload the necessary token to CRAN, it  seems inevitable that my vignette cannot be rebuilt by CRAN. I do rebuild it regularly locally and on Travis-CI, where I can upload the token as an encrypted file.
