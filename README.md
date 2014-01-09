# doxy-coverage

**doxy-coverage** is a source code documentation coverage measurement tool. Its primary use case is to gate on the percentage of API and structures documented on software projects.

***

## How it works

First, Doxygen must be run on your project's source code to generate some XML documentation files. Doxy-coverage consumes those files and reports the documentation coverage.

A non-zero exit code will be returned if the source code documentation is below certain treshold, which allows to integrate this script with CI systems seamlessly.

## Getting Started
First create a doxygen.conf file. If you have one already, make sure `GENERATE_XML` is set to `YES`. If not, create it with the following lines:

```
GENERATE_XML=YES
GENERATE_HTML=NO
GENERATE_LATEX=NO
```

Then, execute `doxygen -w doxygen.conf` in your source directory. It will generate an `xml` directory with the files that doxy-coverage consumes.

Lastly, execute doxy-coverage with the path to the `xml` directory:

```
doxy-coverage.py /path/to/xml
```

## Example

The [libhpack](https://github.com/alobbs/libhpack) library [CI](https://travis-ci.org/alobbs/libhpack) system uses doxy-coverage to ensure the its documentation level is high enough and it doesn't suffer regressions over the time.

--  
Alvaro Lopez Ortega  
[alvaro@gnu.org](mail:alvaro@gnu.org)

