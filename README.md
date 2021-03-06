
Mark Reference Counts
-------------------------------------------------------------------------------
An IDA Pro function and data reference count commenter plug-in.
Version 1.3
By Sirmabus


--= Introduction =--
This simple plug-in will enumerate functions, and or, optionally
data references in your IDB and add a simple count comment for them.

It dawned on me one day.. how I spent a lot of time looking at relative
reference counts when looking through a target and reversing a particular
function of interest.
To really grok it I need to know what sub-functions and data are local to it.
I would have to mouse over and press the xref shortcut 'X' to get at least some
kind of summery.
Now, if I could just see counts at glance on my IDA screen things could be more
productive!

Just knowing the overall reference count can tell useful information.
If one considers a ref count vs the entire target's count one can draw some
theoretical inferences.
If there is just one ref it is almost certainly local.
If there are many references then one can make some initial assumption that it
has some kind of common support/utility relationship, etc.

At first I just did the function counts then later added data too.
One can make useful inferences to data ref counts as well.
In particular assert, and debug strings, labels, etc., that have telling
information where ref counts can give you some idea of significance et al.

See my related "Function String Associate" plug-in too.


--= Installation =--
Copy the plug-in to your IDA Pro "plugins" directory.
Edit your "plugins.cfg' with a hotkey to run it as you would install any other
plug-in. See the IDA documentation for more about plug-in setups.


--= Running it =--
1. Save, and, or make a backup of your IDB first.
   Particularly important because there is no "undo" feature here.

2. Run the plug-in.
   Choose if you want to make functions, and, or data reference count comments.

3. Click continue and let it do it's thing.
   It should be very fast on a modern PC even for very large IDBs.

When it's done your functions, and, or data refs should have references counts
as visible "repeatable" comments. See example image.


--= Operational info  =--
The resulting quality is only as good as how complete and clean your IDB is.
If there is for an example a missing function reference you might see a '1'
thinking the function is "local" when in fact it isn't.
If the target is particularly large, and, or messed up with a lot of stray
unprocessed blocks then consider running my "Extra Pass" plug-in at least once
prior to this one.
Also if you run my other plug-ins or similar that adds comments, you should run
those first.
Else the resulting numbers might end up at the end of the comment rather then
the beginning.

The rule for function counting is simple. The plug-in just walks every function
and counts the refs to it.
If the function already has a comment it will prefix this number to it, else it
will create a new one for it.
Will only add these for functions that have ref counts, thus skips disconnected
C++ vftable member functions et al.

The rule for data refs: Also only counts are shown for ones that actually have
references. Only data that has references to code are counted, not data to data
references.
If the data is a string and has no existing comment then the string will be
suffixed to the count. IE. "; 2 'Some random string'"
This is necessary to duplicate default IDA behavior of showing strings with
out comments; they would be obscured by the count comment otherwise.


--= Changes =--
1.3  - 1) Added E64 version.
       2) Custom UI updates.

1.02 - Fixed crash bug.

1.01 - 1) Fixed and updated some custom UI elements.
       2) Some speed optimization.

1.0b - May 2011 Created.


Support forum: http://www.macromonkey.com/bb/index.php/topic,20.0.html

Terms of Use
------------
This software is provided "as is", without any guarantee made as to its
suitability or fitness for any particular use. It may contain bugs, so use
this software is at your own risk.  The author(s) no responsibly for any
damage that may unintentionally be caused through its use.
