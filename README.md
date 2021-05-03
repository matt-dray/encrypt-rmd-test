# encrypt-rmd-test

I've used [the {encryptedRmd} R package by Dirk Schumacher](https://github.com/dirkschumacher/encryptedRmd) to password-protect an HTML document knitted from an [R Markdown](https://rmarkdown.rstudio.com/) file and then hosted it via [GitHub Pages](https://pages.github.com/).

The encrypted document is hosted on GitHub Pages at this address: `https://matt-dray.github.io/encrypt-rmd-test/encrypt-test.html.enc.html`

You'll be prompted to enter a key to decrypt the document. For this test, the key is: `9ebf5d40b061c59330b9fce16703e4c2fb2fbf90a773996e43e49d562ea17039`

## How to

1. Install {encryptedRmd} from CRAN with `install.packages("encryptedRmd")` (v0.2.1 at time of writing)
1. Write an R Markdown file with the `output:` field in the YAML set to `encryptedRmd::encrypted_html_document`
1. Knit the file to render (i) an unencrypted HTML, (ii) an encrypted HTML, and (iii) a decryption key
1. Commit and push the encrypted file to GitHub and serve it via GitHub Pages

Of course, you should add the unencrypted HTML, the Rmd and the key to your gitignore so you don't commit them. I haven't done that for the purposes of this test.

## Files

You can find all the files for this test in [the `docs/` folder](https://github.com/matt-dray/encrypt-rmd-test/tree/main/docs), you'll find:

* `encrypt-test.Rmd`, the R Markdown file
* `encrypt-test.html`, the unencrypted HTML rendered from the Rmd
* `encrypt-test.enc.html`, the `enc`rypted HTML knitted from the Rmd
* `encrypt-test.end.html.key`, the key that must be used to decrypt the encrypted HTML

