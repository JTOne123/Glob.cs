Glob.cs
=======

[![Version](https://img.shields.io/nuget/v/Glob.cs.svg)](https://www.nuget.org/packages/Glob.cs)
[![Build status](https://ci.appveyor.com/api/projects/status/knmq8uf073fchkty/branch/master?svg=true)](https://ci.appveyor.com/project/mganss/glob-cs/branch/master)
[![codecov.io](https://codecov.io/github/mganss/Glob.cs/coverage.svg?branch=master)](https://codecov.io/github/mganss/Glob.cs?branch=master)


Single-source-file path <a href="http://en.wikipedia.org/wiki/Glob_(programming)">globbing</a> for .NET (netstandard 1.4 and net40).

Features
--------

* Choose case sensitivity
* Optionally match only directories
* Injectable file system implementation for easy testing (uses [`System.IO.Abstractions`](https://www.nuget.org/packages/System.IO.Abstractions/))
* Can cancel long running match
* Throw or continue on file system errors
* Optionally log errors to supplied log implementation

Syntax
------

* `?` matches a single character
* `*` matches zero or more characters
* `**` matches zero or more recursive directories, e.g. `a\**\x` matches `a\x`, `a\b\x`, `a\b\c\x`, etc.
* `[...]` matches a set of characters, syntax is the same as [character groups](http://msdn.microsoft.com/en-us/library/20bw873z.aspx#PositiveGroup) in Regex.
* `{group1,group2,...}` matches any of the pattern groups. Groups can contain groups and patterns, e.g. `{a\b,{c,d}*}`.

Usage
---

Install the NuGet package [`Glob.cs`](https://www.nuget.org/packages/Glob.cs). Then:

```C#
var dlls = Glob.Expand(@"c:\windows\system32\**\*.dll");
```
