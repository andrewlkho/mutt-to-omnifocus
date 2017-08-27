`mutt-to-omnifocus.py` is a short python script to create OmniFocus tasks from
messages in mutt.  Actually, it's a relatively MUA-agnostic script in that it
accepts any RFC-compliant message that the python `email` package can handle on
STDIN.

My use case for developing this script is that I want to acheive some version
of Inbox Zero, and doing so (for me) involves off-loading e-mails into tasks.
If you use Mail.app, of course, OmniFocus provide the Clip-O-Tron for linking
tasks with messages.  One of the (few) drawbacks of using mutt is that it
doesn't readily integrate into Mac OS X.  So I wrote this script that creates a
task in the inbox.  The subject of the e-mail is used for the name of the task,
whilst various headers are placed into the note (enough to identify the e-mail
by).  I tend to use the `Message-ID` field to pull up the e-mail later in mutt
by using the `~i` pattern modifier.


Usage
=====

Place the script somewhere in your `$PATH`, and then use something like the
following in your mutt configuration files:

    macro index,pager \cL "<pipe-message>mutt-to-omnifocus.py<enter>" \
        "Create OmniFocus task from message"

If you want to bring up the task in the quick entry panel instead, use the `-q`
option:

    macro index,pager \cL "<pipe-message>mutt-to-omnifocus.py -q<enter>" \
        "Create OmniFocus task from message"


-- Andrew Ho <andrewho@andrewho.co.uk>
