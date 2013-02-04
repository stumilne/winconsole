Author: Stuart Milne
Date: February 2013

Console Wrapper for Win32 GUI applications
==========================================
This is a wrapper class intended for use in non-console win32 applications.
It will create a seperate console window to the main application and redirect stdin, stdout and stderr to the console. This can be a convienient way to output debug/sanity-check information with minimal fuss.

The class is implemented using a singleton pattern, this does provide 'global' access however the primary motivation is that it is an error to have, or attempt to have, more than one console window per process.

## Usage
The singleton object must be explicitly created and destroyed using the Create() and Destroy() methods. It is an error to call Create() more than once without a call to Destroy() before the second call. Likewise it is an error to call Destroy() more than once without a preceding Create().

Access to the member functions must be performed via the static Get() method.
ie: `stu::Console::Get().Print(10, 10, "Some text");`

## Functionality
 - Print text at optionally specified console location (row, column)
 - Move cursor to specified row/column
 - Clear screen to optionally specified colour
 - Clear line with optionally specified clear character
 - Set text or background colour for future output
 - Switch current text or background colour while retaining current output