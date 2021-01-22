# DilanScript API Documentation - Java

Okay here you go.

### Accessing the DilanScript file

To have the DilanScript API read your file, create a new instance of the `DilanScript` class. You can do that in two ways:

With a file
    
    DilanScript ds = new DilanScript(new File("urmom.ds");

or with a URL
    
    DilanScript ds = new DilanScript(new URL("https://blockhead7360.com/urmom.ds");

Just by doing that, the entire DilanScript from that file will be loaded and ready for access. You will however need to catch various [exceptions](#Exceptions), which you can do like this:

    DilanScript ds = null;
    
    try {
        ds = new DilanScript(new URL("https://blockhead7360.com/somefile.ds"));
    } catch (Exception ex) {
        ex.printStackTrace(); //or whatever you want
    }

You might get some IO exceptions or URL exceptions depending on whether you gave it an existing file or proper URL, whether you have internet (for the URL), etc., but there may also be some DilanScript parsing exceptions depending on if your file can be read.


### Entering the global structure

DilanScript data is stored in instances of `DStructure`. Each one will include all elements, along with other DStructures that you may have nested inside.

Get the global one from the DilanScript instance with

    DStructure section = ds.enter();
    
where `ds` is the instance of DilanScript you created earlier.



### Getting values

Get a String value (multiline or not) with a key you provide:

    String value = section.get("key");

where `section` is an instance of a DStructure, and `"key"` is the key for the value you want to retrieve.



### Entering nests

You can nest these structures within each other. What I mean by that is you can have like another section in your global section where you can store more keys and values.

    DStructure section2 = section.nest("key");

where `section` is the instance of a DStructure above the one you're trying to get, and `"key"` is the name of the section.



### Setting values

Currently not supported but probably will be at some point.



### Other useful functions

Get the size of a section with

    int l = section.length();
    
where `section` is an instance of a DStructure.

This will be the number of all key-value pairs plus the number of sections (but not the number of each key-value pair or section within each subsection, etc).


You can get a list of all data keys and nest keys with

    Set<String> dataKeys = section.getDataKeys();

and

    Set<String> nestKeys = section.getNestKeys();

This can be useful if you maybe need to loop through a list of a section's subsections or something like that.



### Exceptions

If your file doesn't exist or your URL doesn't work, you'll get the normal Java exceptions (IOException, MalformedURLException, etc).

However, you may experience my own lovely `YoureALoserException`. It'll tell you why you got it when the error was thrown, but some examples include from never closing a [multiline](FileFormattingGuide.md#Multiline Blocks), having a value with no key, or having too many or too little closing section curly brackets.
