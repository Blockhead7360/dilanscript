# DilanScript File Formatting Guide

There are a bunch of fun things you can do with a DilanScript file.

### Initialization

It doesn't matter what the file extension is. You can use .txt if you want, or .ds for DilanScript if you want, but it doesn't matter at all. Ultimately, it's a normal text file and you're *supposed* to be able to edit it.

Wherever you want the DilanScript to start, you'll need to put this line in your file **exactly as shown below**:

    // DilanScript 2
    
The API will read from top to bottom, skipping over every line until it sees that one. That means you can put whatever you want above it without any problems.



### Background information

Other than in [multilines](#Multiline-Blocks), any sort of blank lines or indentation with spaces is ignored. Feel free to indent using spaces or spread everything out as much as you want.


### Keys and Values

Store data like this:

    key: value
    
Basically, you're giving the value an identifier so you know how to get it with the API. For example, you might have the key as `name` and the value as `Blockhead7360`, so when you use the API to [get](API-Java.md#Getting-values) a value, you'd get "Blockhead7360" when you use the key "name" to get it.

The API looks for the first `: ` (a colon followed by a space) to know where the key ends and the value starts, so I recommend you try not to use colons or spaces in your key name. After the first colon space, you're able to use it more on the same line.



### Multiline blocks

Rather than storing a long value with a bunch of `\n`s, it might be nicer to just write it on multiple lines so you can see how it'll look. While the line break character would certainly work, here's a better way:

    key [
    Hi this is line 1!
    
    This is line 3!
    What's up?
    This is line 5!
    ]

The API converts this to one string with line break characters in place of each new line.

In this case, line breaks and leading spaces are **not** ignored, so having a blank line will reflect in your retrieved value of "key".

The API checks if the line ends with ` [` (a space followed by an open square bracket) to know where the multiline starts. The multiline ends when the line is equal to `]` (a close square bracket) excluding any leading or trailing spaces.



### Sections

Split stuff up in sections! It'll be more organized, plus you can do neat things with [nesting](API-Java.md#Entering-Nests) and [other things](API-Java.md#Other-useful-functions).

    sectionName {
    
        key1: value1
        key2: value2
        
        subsection {
        
            key1: value1
            key2: value2
            
        }
        
    }

You can even store sections in other sections. You can also get [how big a section is](API-Java.md#Other-useful-functions) and [loop through each value or subsection in a section](API-Java.md#Other-useful-functions).

The API checks if the line ends with ` {` (a space followed by an open curly bracket) to know where a new section starts. The section ends when the line is equal to '}' (a close curly bracket) excluding any leading or trailing spaces.

Of course, the indentation is optional, but it can help stay organized.
