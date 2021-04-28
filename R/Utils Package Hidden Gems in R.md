

# Utils Package Hidden Gems

### `readClipboard` and` writeClipboard`

One of my favorite duo of functions from **utils** is _readCLipboard_ and _writeClipboard_. If you’re doing some manipulation to get a quick answer between R and Excel, these functions can come in handy. _readClipboard_ reads in whatever is currently on the Clipboard.

For example, let’s copy a column of cells from Excel.

![readClipboard in R from Excel](https://i1.wp.com/theautomatic.net/wp-content/uploads/2019/03/readClipboard-in-R.png?w=640)

We can now run _readClipboard()_ in R. The result of running this command is a vector containing the column of cells we just copied. Each cell corresponds to an element in the vector.

![readClipboard result in R](https://i1.wp.com/theautomatic.net/wp-content/uploads/2019/03/readClipboard-result-in-R.png?w=640)

Similarly, if we want to write a vector of elements to the clipboard, we can the _writeClipboard_ command:

```
test <- c("write", "to", "clipboard")
writeClipboard(test)
```

Now, the vector **test** has been copied to the clipboard. If you paste the result in Excel, you’ll see a column of cells corresponding to the vector you just copied.

![writeClipboard result in R](https://i1.wp.com/theautomatic.net/wp-content/uploads/2019/03/writeClipboard-result-in-R.png?w=640)

### `combn`

The _combn_ function is useful for getting the possible combinations of an input vector. For instance, let’s say we want to get all of the possible 2-element combinations of a vector, we could do this:

```
food <- c("apple", "grape", "orange", "pear", "peach", "banana") 
combn(food, 2)
```

![combn get all combinations of a vector's elements in R](https://i2.wp.com/theautomatic.net/wp-content/uploads/2019/03/combn-get-all-combinations-of-a-vector-in-r.png?w=640)

In general, the first parameter of _combn_ is the vector of elements you want to get possible combinations from. The second parameter is the number of elements you want in each combination. So if you need to get all possible 3-element or 4-element combinations, you would just need to change this number to three or four.

```
combn(food, 3)
combn(food, 4)
```

We can also add a parameter called **simplify** to make the function return a list of each combination, rather than giving back a matrix output like above.

```
combn(food, 3, simplify = FALSE)
```

### `fileSnapshot`

The _fileSnapshot_ function is one R’s collection of file manipulation functions. To learn more about file manipulation and getting information on files in R, [check out this post](http://theautomatic.net/2018/07/11/manipulate-files-r/).

_fileSnapshot_ will list and provide details about the files in a directory. This function returns a list of objects.

```
# get file snapshot of current directory
snapshot <- fileSnapshot()

# or file snapshot of another directory
snapshot <- fileSnapshot("C:/some/other/directory")
```

fileSnapshot returns a list, which here we will just call “snapshot”. The most useful piece of information can be garnered from this by referencing “info”:

`snapshot$info`

Here, snapshot$info is a data frame showing information about the files in the input folder parameter. Its headers include:

- size ==> size of file
- isdir ==> is file a directory? ==> TRUE or FALSE
- mode ==> the file permissions in [octal](http://permissions-calculator.org/)
- mtime ==> last modified time stamp
- ctime ==> time stamp created
- atime ==> time stamp last accessed
- exe ==> type of executable (or “no” if not an executable)

### `download.file`

_download.file_ does just what it sounds like – downloads a file from the internet to the destination provided in the function’s input. The first parameter is the URL of the file you wish to download. The second parameter is the name you want to give to the downloaded file. Below, we download a file and call it “census\_data.csv”.

```
download.file("https://www2.census.gov/programs-surveys/popest/datasets/2010/2010-eval-estimates/cc-est2010-alldata.csv", "census_data.csv")
```

### `fix` - **modify an object on the fly**

The **utils** package also has the ability to modify objects on the fly with the _fix_ function. For instance, let’s say you define a function interactively, and you want to make some modification.

```
some_func <- function(num)
{
    3 * num + 1

}
```

Now, let’s modify the function with _fix_: `fix(some_func)`:

![fix function in r](https://i1.wp.com/theautomatic.net/wp-content/uploads/2019/04/fix-function-in-r.png?w=640)

When you call _fix_, it comes up with an editor allowing you to modify the definition of the function. You can also call _fix_ to modify a vector or data frame.

```
fix(iris)
```

![fix data frame in r](https://i1.wp.com/theautomatic.net/wp-content/uploads/2019/04/fix-data-frame-in-r.png?w=640)