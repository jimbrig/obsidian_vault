%%
ID: 2810342
Updated: 2020-05-26
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article3.5c705a01b476.png)

# About
Title: [[Persistent Config and Data for R Packages - R-Hub Blog]]
Author: 
Category: #articles
Number of Highlights: ==22==
Last Highlighted: *2020-05-25*
Readwise URL: https://readwise.io/bookreview/2810342
Source URL: https://blog.r-hub.io/2020/03/12/user-preferences/


# Highlights 
Does your R package work best with some configuration? You probably want it to be easily found by your package. Does your R package download huge datasets that don’t change much on the provider side? Maybe you want to save the corresponding data somewhere persistent so that things will go faster during the next R session. In this blog post we shall explain how an R package developer can go about using and setting persistent configuration and data on the user’s machine.  ^62607176

---

“Applications can actually store user level configuration information, cached data, logs, etc. in the user’s home directory, and there is a standard way to do this [depending on the operating system]." R packages that are on CRAN cannot write to the home directory without getting confirmation from the user, but they can and should use standard locations. To find where those are, package developers can use the rappdirs package.  ^62607177

---

On top of these non-R specific standard locations, we’ll also mention the standard homes of R options and environment variables, .Rprofile and .Renviron  ^62607178

---

As an R package developer, what can you do for your R package to correctly assess user preferences and settings?  ^62607179

---

options allow the user to set and examine a variety of global options which affect the way in which R computes and displays its results  ^62607180

---

For more startup tweaks, the user could adopt the startup package  ^62607181

---

As a package developer in your code you can retrieve options by using getOption() whose second argument is a fallback for when the option hasn’t been set by the user. Note that an option can be any R object.  ^62607207

---

Environment variables, found via Sys.getenv() rather than getOption(), are often used for storing secrets (like GITHUB_PAT for the gh package) or the path to secrets on disk (like TWITTER_PAT for rtweet), or not secrets (e.g. the browser to use for chromote).  ^62607208

---

the user could use Sys.setenv(). Obviously, secrets should not be written at the top of a script that’s public. To make environment variables persistent they need to be stored in a startup file, .Renviron. .Renviron does not contain R code like .Rprofile, but rather key-value pairs that are only called via Sys.getenv().  ^62607209

---

The keyring package allows to interact with such credential stores. You could either take it on as a dependency like e.g. gh, or recommend the user of your package to use keyring and to add a line like

Sys.setenv(SUPERSECRETKEY = keyring::key_get("myservice"))  ^62607210

---

Using a config file

The batchtools package expect its users to setup a config file somewhere if they don’t want to use the defaults. That somewhere can be several locations, as explained in the batchtools::findConfFile() manual page. Two of the possibilities are rappdirs::user_config_dir("batchtools", expand = FALSE) and rappdirs::site_config_dir("batchtools") which refer to standard locations that are different depending on the operating system.  ^62607211

---

the gert package can find and return Git’s preferences via gert::git_config_global()  ^62607212

---

recommend using such standard locations when caching data.  ^62607213

---

Persist as much relevant and fresh data as possible.  ^62607214

---

A package that exemplifies doing so is getlandsat that downloads “Landsat 8 data from AWS public data sets” from the web. The first time the user downloads an image, the result is cached so next time no query needs to be made. A very nice aspect of getlandsat is its providing cache management functions  ^62607215

---

If you hesitate to use e.g. rappdirs::user_cache_dir() vs rappdirs::user_data_dir(), use a GitHub code search.  ^62607216

---

Package developers might also like the hoardr package that basically creates an R6 object building on rappdirs with a few more methods (directory creation, deletion).  ^62607217

---

R-devel “just gained support for OS-agile user-specific #rstats cache/config/data folders” which is big (but if you use the base R implementation available after R 4.x.y, unless your package depends on R above that version you’ll need to backport the functionality ).  ^62607218

---

Caching results within an R session

To cache results within an R session, you could use a temporary directory for data. For any function call you could use memoise that supports, well memoization which is best explained with an example.  ^62607219

---

Only the first call to time() actually calls Sys.time(), after that the results is saved for the entire session unless memoise::forget() is called. It is great for speeding up code, and for not abusing internet resources which is why the polite package wraps memoise.  ^62607220

---

Providing a ready-to-use dataset in a non-CRAN package

If your package depends on the use of a huge dataset, the same for all users, that is by definition too huge for CRAN, you can use a setup like the one presented by Brooke Anderson and Dirk Eddelbuettel in which the data is packaged up in a separate package not on CRAN, that the user will install therefore saving the data on disk somewhere where you can find it easily.  ^62607221

---

Conclusion

In this blog post we presented ways of saving configuration options and data in a not so temporary way in R packages. We mentioned R startup files (options in .Rprofile and secrets in .Renviron, the startup package); the rappdirs and hoardr packages as well as an exciting similar feature in R devel; the keyring package. Writing in the user home directory can be viewed as invasive (and can trigger CRAN archival), hence there is a need for a good package design (asking for confirmation; providing cache management functions like getlandsat does) and documentation for transparency. Do you use any form of caching on disk with a default location in one of your packages? Do you know where your rhub email token lives? 😉  ^62607222

