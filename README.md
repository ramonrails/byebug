# Byebug

[![Version][gem]][gem_url]
[![Quality][gpa]][gpa_url]
[![Coverage][cov]][cov_url]
[![Gratipay][tip]][tip_url]
[![Gitter][irc]][irc_url]

[gem]: https://img.shields.io/gem/v/byebug.svg
[gpa]: https://img.shields.io/codeclimate/github/deivid-rodriguez/byebug.svg
[cov]: https://img.shields.io/codeclimate/coverage/github/deivid-rodriguez/byebug.svg
[tip]: https://img.shields.io/gittip/deivid-rodriguez.svg
[irc]: https://img.shields.io/badge/IRC%20(gitter)-devs%20%26%20users-brightgreen.svg

[gem_url]: https://rubygems.org/gems/byebug
[gpa_url]: https://codeclimate.com/github/deivid-rodriguez/byebug
[cov_url]: https://codeclimate.com/github/deivid-rodriguez/byebug
[tip_url]: https://www.gittip.com/deivid-rodriguez
[irc_url]: https://gitter.im/deivid-rodriguez/byebug

_Debugging in Ruby 2_

Byebug is a simple to use, feature rich debugger for Ruby 2. It uses the new
TracePoint API for execution control and the new Debug Inspector API for call
stack navigation, so it doesn't depend on internal core sources. It's developed
as a C extension, so it's fast. And it has a full test suite so it's reliable.

It allows you to see what is going on _inside_ a Ruby program while it executes
and offers many of the traditional debugging features such as:

* Stepping: Running your program one line at a time.
* Breaking: Pausing the program at some event or specified instruction, to
examine the current state.
* Evaluating: Basic REPL functionality, although [pry] does a better job at
that.
* Tracking: Keeping track of the different values of your variables or the
different lines executed by your program.


## Build Status

Linux & OSX [![Tra][tra]][tra_url]

Windows [![Vey][vey]][vey_url]

[tra]: https://img.shields.io/travis/deivid-rodriguez/byebug.svg?branch=master
[vey]: https://ci.appveyor.com/api/projects/status/github/deivid-rodriguez/byebug?svg=true

[tra_url]: https://travis-ci.org/deivid-rodriguez/byebug
[vey_url]: https://ci.appveyor.com/project/deivid-rodriguez/byebug


## Requirements

* Required: MRI 2.0.0 or higher. For debugging ruby 1.9.3 or older, use
[debugger].

* Recommended:
  - MRI 2.1.8 or higher.
  - MRI 2.2.4 or higher.


## Install

    $ gem install byebug


## Usage

Simply drop

    byebug

wherever you want to start debugging and the execution will stop there. If you
are debugging rails, start the server and once the execution gets to your
`byebug` command you will get a debugging prompt.


## Byebug's commands

    Command     | Aliases      | Subcommands
    ----------- |:------------ |:-----------
    `backtrace` | `bt` `where` |
    `break`     |              |
    `catch`     |              |
    `condition` |              |
    `continue`  |              |
    `delete`    |              |
    `debug`     |              |
    `disable`   |              | `breakpoints` `display`
    `display`   |              |
    `down`      |              |
    `edit`      |              |
    `enable`    |              | `breakpoints` `display`
    `finish`    |              |
    `frame`     |              |
    `help`      |              |
    `history`   |              |
    `info`      |              | `args` `breakpoints` `catch` `display` `file` `line` `program`
    `irb`       |              |
    `kill`      |              |
    `list`      |              |
    `method`    |              | `instance`
    `next`      |              |
    `pry`       |              |
    `quit`      |              |
    `restart`   |              |
    `save`      |              |
    `set`       |              | `autoirb` `autolist` `autopry` `autosave` `basename` `callstyle` `fullpath` `histfile` `histsize` `linetrace` `listsize` `post_mortem` `savefile` `stack_on_error` `width`
    `show`      |              | `autoirb` `autolist` `autopry` `autosave` `basename` `callstyle` `fullpath` `histfile` `histsize` `linetrace` `listsize` `post_mortem` `savefile` `stack_on_error` `width`
    `source`    |              |
    `step`      |              |
    `thread`    |              | `current` `list` `resume` `stop` `switch`
    `tracevar`  |              |
    `undisplay` |              |
    `up`        |              |
    `var`       |              | `all` `constant` `global` `instance` `local`


## Semantic Versioning

Byebug tries to follow [semantic versioning](http://semver.org) and tries to
bump major version only when backwards incompatible changes are released.
Backwards compatibility is targeted to [pry-byebug] and any other plugins
relying on `byebug`.


## Getting Started

Read [byebug's markdown
guide](https://github.com/deivid-rodriguez/byebug/blob/master/GUIDE.md) to get
started. Proper documentation will be eventually written.


## Related projects

* [pry-byebug] adds `next`, `step`, `finish`, `continue` and `break` commands
to `pry` using `byebug`.
* [ruby-debug-passenger] adds a rake task that restarts Passenger with Byebug
connected.
* [minitest-byebug] starts a byebug session on minitest failures.
* [sublime_debugger] provides a plugin for ruby debugging on Sublime Text.


## Contribute

See [Getting Started with Development](CONTRIBUTING.md).


## Credits

Everybody who has ever contributed to this forked and reforked piece of
software, especially:

* @ko1, author of the awesome TracePoint API for Ruby.
* @cldwalker, [debugger]'s maintainer.
* @denofevil, author of [debase], the starting point of this.
* @kevjames3 for testing, bug reports and the interest in the project.
* @FooBarWidget for working and helping with remote debugging.

[debugger]: https://github.com/cldwalker/debugger
[pry]: https://github.com/pry/pry
[debase]: https://github.com/denofevil/debase
[pry-byebug]: https://github.com/deivid-rodriguez/pry-byebug
[ruby-debug-passenger]: https://github.com/davejamesmiller/ruby-debug-passenger
[minitest-byebug]: https://github.com/kaspth/minitest-byebug
[sublime_debugger]: https://github.com/shuky19/sublime_debugger

## Cheat sheet

Taken from http://fleeblewidget.co.uk/2014/05/byebug-cheatsheet/ and converted to markdown at http://markitdown.medusis.com

### Starting Byebug

If you’re running Byebug on a Rails application in development mode, you no longer need to start the server with 

--debugger – the debugger is on by default.

To get going, simply type 

byebug (or 

debugger) into your source file at the line you’re interested in and run the program. If you’re running it on a Rails application, remember to switch to your terminal window to look at debugger output.

**Note:** 

byebug invocations are just method calls, so you can make them conditional:

> byebug if foo == “bar”

**Another Note:** As is common with debuggers, hitting ‘Enter’ on an empty line in Byebug repeats the last command.

### Stopping Again

q[uit] — a.k.a. “exit” _unconditionally_

Quit. It stops the thing running. Also exits your program. **Note:** To quit without an ‘are you sure?’ prompt, use 

quit unconditionally (shortened to 

q!)

kill

_Really_ quit. This uses 

kill -9, for situations where quit just isn’t fierce enough.

### Essential Commands

c[ontinue] _&lt;line-number&gt;_

Carry on running until program ends, hits a breakpoint or reaches line _line-number_ (if specified).

n[ext] _&lt;number&gt;_

Go to next line, stepping over function calls. If _number_ specified, go forward that number of lines.

s[tep] _&lt;number&gt;_

Go to next line, stepping into function calls. If _number_is specified, make that many steps.

b[ack]t[race] — a.k.a. “w[here]”

Display [stack trace](http://en.wikipedia.org/wiki/Stack_trace).

h[elp] _&lt;command-name&gt;_

Get help. With no arguments, returns a list of all the commands Byebug accepts. When passed the name of a command, gives help on using that command.

### Breakpoints and Catchpoints

b[reak]

Sets a [breakpoint](http://en.wikipedia.org/wiki/Breakpoint) at the current line. These can be conditional: 

break if foo != bar. Keep reading for more ways to set breakpoints!

b[reak] _&lt;filename&gt;:&lt;line-number&gt;_

Puts a breakpoint at _line-number_ in _filename_ (or the current file if _filename_ is blank). Again, can be conditional: 

b myfile.rb:15 unless my_var.nil?

b[reak] _&lt;class&gt;(.|#)&lt;method&gt;_

Puts a breakpoint at the start of the method _method_ in class _class_. Accepts an optional condition: 

b MyClass#my_method if my_boolean

info breakpoints

List all breakpoints, with status.

cond[ition] &lt;number&gt; _&lt;expression&gt;_

Add condition _expression_ to breakpoint &lt;number&lt;&gt;. If no _expression_ is given, removes any conditions from that breakpoint.

del[ete] _&lt;number&gt;_

Deletes breakpoint &lt;number&gt;. With no arguments, deletes all breakpoints.

disable breakpoints _&lt;number&gt;_

Disable (but don’t delete) breakpoint &lt;number&gt;. With no arguments, disables all breakpoints.

cat[ch] &lt;exception&gt; _off_

Enable or (with _off_ argument) disable catchpoint on &lt;exception&gt;.

cat[ch]

Lists all catchpoints.

cat[ch] off

Deletes all catchpoints.

sk[ip]

Passes a caught exception back to the application, skipping the catchpoint.

### Program Stack

b[ack]t[race] — a.k.a. “w[here]”

Display [stack trace](http://en.wikipedia.org/wiki/Stack_trace).

f[rame] _&lt;frame-number&gt;_

Moves to &lt;frame-number&gt; (frame numbers are shown by 

bt). With no argument, shows the current frame.

up _&lt;number&gt;_

Move up &lt;number&gt; frames (or 1, if no number specified).

down _&lt;number&gt;_

Move down &lt;number&gt; frames (or 1, if no number specified).

info args

Arguments of the current frame.

info locals

Local variables in the current stack frame.

info instance_variables

Instance variables in the current stack frame.

info global_variables

Current global variables.

info variables

Local and instance variables of the current frame.

m[ethod] &lt;class|module&gt;

Shows instance methods of the given class or module.

m[ethod] i[nstance] &lt;object&gt;

Shows methods of &lt;object&gt;.

m[ethod] iv &lt;object&gt;

Shows instance variables of &lt;object&gt;.

v[ar] cl[ass]

Shows class variables of self.

v[ar] co[nst] &lt;object&gt;

Shows constants of &lt;object&gt;.

v[ar] g[lobal]

Shows global variables (same as 

info global_variables).

v[ar] i[nstance] &lt;object&gt;

Shows instance variables of &lt;object&gt (same as 

method iv &lt;object&gt;).

v[ar] l[ocal]

Shows local variables (same as 

info locals).

### Execution Control

c[ontinue] _&lt;line-number&gt;_

Carry on running until program ends, hits a breakpoint or reaches line _line-number_ (if specified).

n[ext] _&lt;number&gt;_

Go to next line, stepping over function calls. If _number_ specified, go forward that number of lines.

s[tep] _&lt;number&gt;_

Go to next line, stepping into function calls. If _number_is specified, make that many steps.

fin[ish] _&lt;num-frames&gt;_

With no argument, run until the current frame returns. Otherwise, run until &lt;num-frames&gt; frames have returned.

irb

Start an IRB session. This will have added commands 

cont, 

n and 

step, but these can’t take arguments (unlike the proper byebug commands of the same name).

restart

Restart the program. This also restarts byebug.

### Threads

th[read]

Show current thread.

th[read] l[ist]

List all threads.

th[read] stop &lt;number&gt;

Stop thread number &lt;number&gt;.

th[read] resume &lt;number&gt;

Resume thread number &lt;number&gt;.

th[read] &lt;number&gt;

Switch context to thread &lt;number&gt;.

### Display

e[val] — a.k.a. “p” &lt;expression&gt;

Evaluate &lt;expression&gt; and display result. By default, you can also just type the expression without any command and get the same thing (disabled by using 

set noautoeval

pp

Evaluate expression and pretty-print the result.

putl

Evaluate an expression with an array result and columnize the output.

ps

Evaluate an expression with an array result, sort and columnize the output.

disp[lay] _&lt;expression&gt;_

Automatically display &lt;expression&gt; every time the program halts. With no argument, lists the current display expressions.

info display

List all current display expressions.

undisp[lay] _&lt;number&gt;_

Remove display expression number &lt;number&gt; (as listed by 

info display). With no argument, cancel all current display expressions.

disable display &lt;number&gt;

Stop displaying expression number &lt;number&gt;. The display expression is kept in the list, though, and can be turned back on again using 

enable display .

enable display &lt;number&gt;

Re-enable previously disabled display expression &lt;number&gt;.

### Controlling Byebug

hist[ory] _&lt;num-commands&gt;_

View last &lt;num-commands&gt; byebug commands (or all, if no argument given).

save &lt;file&gt;

Saves current byebug session options as a script file in &lt;file&gt;.

source &lt;file&gt;

Loads byebug options from a script file at &lt;file&gt;

set &lt;option&gt;

Change value of byebug option &lt;option&gt;.

show &lt;option&gt;

View current value of byebug option &lt;option&gt;.

Options are: autoeval, autoirb, autolist, autoreload, autosave, basename, callstyle, forcestep, fullpath, histfile, histsize, linetrace, tracing_plus, listsize, post_mortem, stack_on_error, testing, verbose and width.

### Source Files and Code

reload

Reload source code.

info file

Information about the current source file.

info files

All currently loaded files.

info line

Shows the current line number and filename.

l[ist]

Shows source code after the current point. Keep reading for more list options.

l[ist] –

Shows source code before the current point.

l[ist] =

Shows source code centred around the current point.

l[ist] &lt;first&gt;-&lt;last&gt;

Shows all source code from &lt;first&gt; to &lt;last&gt; line numbers.

edit _&lt;file:lineno&gt;_

Edit &lt;file&gt;. With no arguments, edits the current file.
