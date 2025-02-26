# UTAU wavtool arguments documentation
Written by dermi1002

## Preface
  This markdown file details the terminal arguments that are passed down to a wavtool when UTAU asks it to combine all files rendered by a resampler. These arguments are not 100% true terms, but rather conclusions made upon observations. Because of this, it requires verification from various sources.
This won't cover how it's done, but only what those arguments are since I don't yet have much development experience. But I believe some information is better than nothing.

# Wavtool Arguments
  The wavtool receives instructions on how to position and envelope a resampled note through terminal arguments. I am not sure where these commands are setup, but for now we will be focusing on what the wavtool sees, which is only the termainal arguments by default.

  Running `wavtool.exe` in command prompt will give you the format of its call:

```
wavtool2 <outfile> <infile> offset length p1 p2 p3 v1 v2 v3 v4 ovr p4 p5 v5
```

Running the command having entered the arguments and renaming 'wavtool2' to 'wavtool.exe' will output a `.whd` file and a `.dat` file using the name of the output file. Combining data in both files in this order and naming it a `.wav` file will result in a fully working audio file.

## The actual arguments
  Here are a few tables describing each argument included in the result from above:

 | Argument | Description | Example |
 | :---: | --- | --- |
 | \<outfile\> | The path to the output wave file. | \path\to\output.wav |
 | \<infile\> | The path to the input wave file. | \path\to\input.wav |
 | offset | The offset from the start of the sample in milliseconds. Everything before this point is cut off. Essentially the same as offset in the oto, although changeable by modifying the STP in Note Property. | 750 |
 | length | The length of the resampled output in milliseconds. | 1000 |

Below is a table of envelope arguments. These are used by the wavtool to envelope resampled files. In that, I put **p** and **v** arguments together since they are "two sides of the same coin," for lack of better words. I like to think of **p** as the position in time and **v** as the volume.

Here it is, sorted in the order set by UTAU (italics means completely optional arguments, underlined means mandatory arguments):

 | Argument | Description | Example |
 | :---: | --- | --- |
 | <ins>p1</ins>, v1 | The first envelope point. I like to think of this as "Current Overlap Point 1." Positive p values go forwards. p is set as the starting silence when p2p3 is used, set as the end of current overlap when p1p4 is used. | 0, 0 or 60, 100 |
 | <ins>p2</ins>, v2 | The second envelope point. I like to think of this as "Current Overlap Point 2." Positive p values go forwards. p is set as the end of the current overlap when p2p3 is used, unused when p1p4 is used. | 60, 100 or 2, 100 |
  | *p5, v5* | The third envelope point. I like to think of this as "Middle Point." Positive p values go forwards. Is unused by default. | (blank), (blank) |
 | p3, v3 | The fourth envelope point. I like to think of this as "Next Overlap Point 1." Positive p values go backwards. p is set as the start of the next overlap when p2p3 is used, unused when p1p4 is used. | 35, 100 |
 | p4, v4 | The fifth envelope point. I like to think of this as "Next Overlap Point 2." Positive p values go backwards. p is set as the ending silence when p2p3 is used, set as the start of next overlap when p1p4 is used. | (blank), 0 or 60, 100 |

The wavtool argument, **ovr**, is the only argument of which I do not yet have any absolute information. However, according to wavtool4vcv and wavtool-yawu, it seems to be an abbreviation for overlap. This part will be updated if new information or observations arrive.
