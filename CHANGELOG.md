- [v1.1.0](#v1.1.0)
- [v1.0.0](#v1.0.0)

## v1.1.0 - To be released
* Daily file handler. The file handler rollover every 24 hours
* Rotating file handler. The file handler will rollover based on the size of the file
* MinGW compatibility
* Added a CMake option `QUILL_VERBOSE_MAKEFILE`. Building Quill as a master project now defaults to non verbose makefile output unless `-DQUILL_VERBOSE_MAKEFILE=ON` is passed to CMake. Fixes #6
* Flush policy improvement. Previously Quill backend worker thread would never `flush`. This made watching the live log of the application harder because the user has to wait for the operating system to flush or `quill::flush()` had to be called on the caller threads. This has now been fixed, when the backend thread worker has no more log messages to process it will automatically `flush`. Fixes #8
* The log level names have been changed from `"LOG_INFO"`, `"LOG_DEBUG"`, etc to `"INFO"`, `"DEBUG"`, etc .. The default formatter string is now using `"LOG_"%(level_name)` instead of `%(level_name)` therefore there is now change in the behaviour. This change gives a lot of more flexibility to users who prefer to see e.g. `INFO` instead of `LOG_INFO` in the logs. Fixes #7
* An option has been added to append the date to the filename when using a FileHandler `quill::file_handler(filename, mode, FilenameAppend);` Fixes #7
* It is now possible to specify the timezone of each handler timestamp. A new parameter is added to `file_handler->set_pattern(...)`. See `PatternFormatter::Timezone`  
## v1.0.0
Initial release