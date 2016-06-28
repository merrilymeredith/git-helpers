### git-patchify

This came from a discussion of how to post a test case in a GitHub issue that
requires a few files.  Tar and shar came up but they were a little too noisy
for someone to glance at.  Instead, how about leveraging git's diff engine
against a null tree / empty directory?


    ❯ mkdir blah && echo "my rad example" > blah/example.txt
    ❯ git patchify blah
    diff --git a/blah/example.txt b/blah/example.txt
    new file mode 100644
    index 0000000..a116566
    --- /dev/null
    +++ b/blah/example.txt
    @@ -0,0 +1 @@
    +my rad example

### git-bre

Short for "branch edit", a command that I use to quickly open an editor session
with any files changed in the current branch, relative to its upstream.  For
example I could hop into an obscure topic branch I've left around and run `git
bre` to open all the files touched in the branch, or make it `git bre
--remote`, passing that arg to vim, my `$EDITOR`, to add the files to a running
vim session.
