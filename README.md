# dotnetcore-training
A roughly one-hour introduction to dotnetcore notes for an instructor-led professional development session

## download and setup 

Start by downloading the dotnetcore SDK here note the tabs on the page for windows/macOS https://dotnet.microsoft.com/download ensure that you are downloading version **.NET Core 3.1** *at a minimum*.

Run the installer for your OS and test within a terminal, powershell, command window. 

Run the command line `dotnet` if you see a result like the following it's set up correctly.

```
PS C:\www> dotnet

Usage: dotnet [options]
Usage: dotnet [path-to-application]

Options:
  -h|--help         Display help.
  --info            Display .NET Core information.
  --list-sdks       Display the installed SDKs.
  --list-runtimes   Display the installed runtimes.

path-to-application:
  The path to an application .dll file to execute.
```

## additional tools

**Visual Studio Code**: https://code.visualstudio.com/ a robust code editor capable of handling all the major tasks of working with dotnetcore.

**Visual Studio 2019(+)**: https://visualstudio.microsoft.com/ important to note that the core framework 3.1 is *NOT SUPPORTED* in any versions of visual studio lower than 2019. This can lead to a number of compilation and package errors that are not obviously related to the lower version of visual studio.

