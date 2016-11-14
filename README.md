# SmallBasic-Screen-Handler
Handles output to a TextWindow through a handler so that changes can be made on the screen more easily.
This is best used when you want to write a program in which you may want to only change part of the screen rather than the whole thing with each change.

To use, simply call screenInit() at the beginning of your program to set up the variables.  You can now draw text to any line of the TextWindow by setting scrnLine[LINE] where LINE is the line in the TextWindow you would like to change.  Adjust scrnLinesTotal to be equal to the last line in that array you want drawn on the screen, and then commit those changes to the screen with PrintScrn().  You can also have the screen handler highlight select pieces of text with ease.  Using the escape code ## will indicate where the highlighted text begins, and #\ indicates where that highlighted text ends.  To highlight an entire line, just use @ at the beginning of the text for that line.  The highlight will reverse the default colours for that segment of text in the TextWindow.  Note that scrnLine[] uses a 0-based index, unlike the rest of SmallBasic.  The first line is 0, the second line is 1, etc.

Example:

> screenInit()
> scrnLine[0]="Hello World!"
> scrnLinesTotal=0
> PrintScrn()

Output:

> Hello World!

Example 2:

> screenInit()
> scrnLine[0]="Hello and Welcome to the Program!"
> scrnLine[1]=""
> scrnLine[2]="Please enter your ##FIRST NAME#\"
> scrnLinesTotal=2
> PrintScrn()
> name=TextWindow.Read()
> scrnLine[2]="Please enter your ##LAST NAME#\"
> PrintScrn()
> lastname=TextWindow.Read()

Output:

> Hello and Welcome to the Program!
> 
> Please enter your FIRST NAME
> ? _

Note that "FIRST NAME" will be highlighted.  Upon entering the input, the screen will change to the following without having to re-write each line:

> Hello and Welcome to the Program!
> 
> Please enter your LAST NAME
> ? _
