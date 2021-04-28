Links: [010-PROGRAMMING](010-PROGRAMMING.md)
Tags: #windows #dev #cli #tool

---

# Windows New Command Line Tool - `diskusage`

If you are running a Windows Insider Preview build (20277, 21277, or later) you can now utilize a great new Windows CLI feature: `diskusage`. Note that I am writing this as of December 17, 2020.

Remember that this tool is still in development so some features aren't completely stable, but whatever, let's look into it!

## Using `diskusage`

**Disk Usage** allows you to check out how much space your drives are taking up using the Command Prompt. There are some other handy parameters for analysis, too.

Open up your command prompt and run `diskusage /?`:

As of can see the command comes fully loaded with a suite of flags, commands, and arguments.

### Caveat: Bytes Only

One caveat of the tool is that it currently only recognizes *bytes*, so if you wanted to search for file larger than 1.73 gigabytes you would have to input 1,857,573,355.52 bytes!

I suggest using a simple tool to convert from GB/KB/MB \<-> Bytes like [a search engine's unit conversion tool](https://www.bing.com/search?PC=U523&q=convert+bytes+to+gbs&pglt=547&FORM=ANNTA1), a dedicated website like [Byte Converter](https://whatsabyte.com/P1/byteconverter.htm) or better yet a command line utility like [humaize-bytes](https://github.com/plribeiro3000/humanize-bytes/blob/master/README.md).

For those who cannot remember the [binary prefix multipliers](https://en.wikipedia.org/wiki/Binary_prefix) here's a reference conversion table:

![](https://i.pinimg.com/originals/d5/92/48/d5924822305e112de21e549a2a9c469b.gif)

When Disk Usage is fully functional, you'll be able to create specific configuration files that contain the search and analysis options you regularly use, saving you additional time when analyzing your data.
