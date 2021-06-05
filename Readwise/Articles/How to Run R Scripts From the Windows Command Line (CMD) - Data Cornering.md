%%
ID: 4084927
Updated: 2020-08-26
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[How to Run R Scripts From the Windows Command Line (CMD) - Data Cornering]]
Author: 
Category: #articles
Number of Highlights: ==4==
Last Highlighted: *2020-08-22*
Readwise URL: https://readwise.io/bookreview/4084927
Source URL: http://datacornering.com/how-to-run-r-scripts-from-the-windows-command-line-cmd/


# Highlights 
"C:\Program Files\R\R-3.4.3\bin\Rscript.exe" C:\Users\myusername\Documents\R\Send_Outlook_Email.R  ^79544794

---

C:\Program Files\R\R-3.4.3\bin\R.exe" CMD BATCH C:\Users\myusername\Documents\R\Send_Outlook_Email.R  ^79544796

---

Find the path to R.exe or Rscript.exe on your computer. If you try to run R.exe from the command line, you enter an R terminal  ^79544798

---

In Rscript.exe case you can see additional usage options.


2. Find the path to R file.

3. Open Notepad and combine paths together (with quotation marks if needed and additional commands “CMD BATCH” if you choose to go with R.exe).

1
"C:\Program Files\R\R-3.4.3\bin\R.exe" CMD BATCH C:\Users\myusername\Documents\R\Send_Outlook_Email.R
4. Save as file with extension .bat (for example send_email.bat).

5. Run that batch file to execute R script.  ^79544800

