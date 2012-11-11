NAME
----
taro - a tool to anchor directory trees to scripts

SYNOPSIS
---------
`taro <args>`

DESCRIPTION
-----------
Taro is a tool that anchors a directory tree to a utility script, called the
"taro script". Executing `taro <args>` within such an anchored tree results in
a call to `execv("/path/to/taro/script", <args>)`.

If a directory contains a file whose name matches the Python regular
expression `\A[._+]taro\Z`, then that tree is anchored to a taro script. The
file matching the regular expression is called the "taro link". To find the
taro script, the taro link is used as follows:

- If the taro link is executable, then it is the taro script.
- If the taro link is a Microsoft-style ini file, then it must contain
  a section named `[taro]` which contains an option `script`. For example,
  here is a valid file:

        [taro]
        script: /usr/local/bin/magic

  If the `script` option is a relative path, then the path is relative to the
  directory that contains the link file.

An error occurs if the taro link exists but fails to satisfy either of the
above conditions.

NOTES
-----
- home page: http://github.com/chadversary/taro
- source code: git://github.com/chadversary/taro.git

BUGS
----
If you find any bugs in this tiny script, then mail the author:
mailto:chad@chad-versace.us
