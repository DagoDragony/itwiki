# Various

## Tcl

TCL(Tool Command Language, pronounce tickle) - simple textual programming language, inteded for issuing commands to interactive programs such as text editors,
debuggers and shells.
Has 2 parts
* Language
* Library

### Extensions

* Tk(pronounced "tee-kay") - is an extension to Tcl which provides the programmer with an interface to the X11
windowing system.
* BLT - allows for developers to add new widgets, geometry managers,and all sorts of commands to the Tcl interpretter
* Expect - allows to place a friendly front-end inside the most cli based UNIX applications, such as
  ftp, telnet, rlogin, passwd, fsck and so on

#### Expect

Global protect asks to write reason interactively, you could do it by:
`expect -c 'spawn globalprotect disable; expect "reason:"; send "work session end\r"; interact'`
