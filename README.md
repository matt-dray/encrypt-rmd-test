# encrypt-rmd-test

<!-- badges: start -->
[![Project Status: Concept – Minimal or no implementation has been done
yet, or the repository is only intended to be a limited example, demo,
or
proof-of-concept.](https://www.repostatus.org/badges/latest/concept.svg)](https://www.repostatus.org/#concept)
[![rostrum.blog
post](https://img.shields.io/badge/rostrum-blog-008900?style=flat&labelColor=black&logo=data:image/gif;base64,R0lGODlhEAAQAPEAAAAAABWCBAAAAAAAACH5BAlkAAIAIf8LTkVUU0NBUEUyLjADAQAAACwAAAAAEAAQAAAC55QkISIiEoQQQgghRBBCiCAIgiAIgiAIQiAIgSAIgiAIQiAIgRAEQiAQBAQCgUAQEAQEgYAgIAgIBAKBQBAQCAKBQEAgCAgEAoFAIAgEBAKBIBAQCAQCgUAgEAgCgUBAICAgICAgIBAgEBAgEBAgEBAgECAgICAgECAQIBAQIBAgECAgICAgICAgECAQECAQICAgICAgICAgEBAgEBAgEBAgICAgICAgECAQIBAQIBAgECAgICAgIBAgECAQECAQIBAgICAgIBAgIBAgEBAgECAgECAgICAgICAgECAgECAgQIAAAQIKAAAh+QQJZAACACwAAAAAEAAQAAAC55QkIiESIoQQQgghhAhCBCEIgiAIgiAIQiAIgSAIgiAIQiAIgRAEQiAQBAQCgUAQEAQEgYAgIAgIBAKBQBAQCAKBQEAgCAgEAoFAIAgEBAKBIBAQCAQCgUAgEAgCgUBAICAgICAgIBAgEBAgEBAgEBAgECAgICAgECAQIBAQIBAgECAgICAgICAgECAQECAQICAgICAgICAgEBAgEBAgEBAgICAgICAgECAQIBAQIBAgECAgICAgIBAgECAQECAQIBAgICAgIBAgIBAgEBAgECAgECAgICAgICAgECAgECAgQIAAAQIKAAA7)](https://www.rostrum.blog/2021/05/07/encrypted-rmd/)
<!-- badges: end -->

Demo of an RMarkdown output that's encrypted and hosted online.

## What

I used [Dirk Schumacher's {encryptedRmd} R package](https://github.com/dirkschumacher/encryptedRmd) to render [an R Markdown file](https://rmarkdown.rstudio.com/) to encrypted HTML, which I've hosted online via [GitHub Pages](https://pages.github.com/). It requires a decryption key if you want to download it.

That means I can give the URL and the decryption key to someone and they can download the contents. If you don't have the decryption key, you can't view it.

Read more in [the accompanying blog post](https://www.rostrum.blog/2021/05/07/encrypted-rmd/).

## Example

For this demo, you can find the encrypted HTML output here: [https://matt-dray.github.io/encrypt-rmd-test/encrypt-test.html.enc.html](https://matt-dray.github.io/encrypt-rmd-test/encrypt-test.html.enc.html)

You'll be prompted for a key, which for this example is: `9ebf5d40b061c59330b9fce16703e4c2fb2fbf90a773996e43e49d562ea17039`

As noted in [the {encryptedRmd} README](https://github.com/dirkschumacher/encryptedRmd/blob/master/README.md#password-protected-html-markdown-documents): _use at your own risk_.

## How to

I did the following to create the contents of this repo:

1. Install {encryptedRmd} from CRAN with `install.packages("encryptedRmd")` (v0.2.1 at time of writing)
1. Write an R Markdown file with the `output:` field in the YAML set to `encryptedRmd::encrypted_html_document`
1. Knit the file to render (i) an unencrypted HTML, (ii) an encrypted HTML, and (iii) a decryption key
1. Commit and push the encrypted file to GitHub and serve it via GitHub Pages (go to 'Settings' > 'Pages' from the GitHub repo)

Of course, you should add the R Markdown file, the unencrypted HTML and the decryption key to your .gitignore. I've retained all the files in this repo for demonstration purposes.

## File structure

I created the R Markdown file `encrypt-test.Rmd` in [the `docs/` folder](https://github.com/matt-dray/encrypt-rmd-test/tree/main/docs) of this repo. When knitted, it generated:

* `encrypt-test.html`, an unencrypted HTML rendered from the Rmd
* `encrypt-test.enc.html`, an `enc`rypted HTML rendered from the Rmd
* `encrypt-test.end.html.key`, the key that must be used to decrypt the encrypted HTML
