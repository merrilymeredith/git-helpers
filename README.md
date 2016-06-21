git-helpers
-----------

git stuff that doesn't fit in aliases 💖

### git-get

Fetches some perhaps-useful info about the git repository.  This was written as
a personal curiosity after seeing mjd's version and how convoluted coding
against the "plumbing" felt to me.  Instead, this git-get leverages the Rugged
ruby gem.

    git get usage:
     root
       repository workdir path

     root_rel
       repository workdir path as relative to cwd

     cwd_rel
       cwd path as relative to workdir

     is_head_detached
       exit 0 if detached head

     branch
       short refname of current branch

     branch_config
       fetch config value for specified branch and key

     branch_remote
       remote for this branch or specified branch

     branch_tracking
       remote tracking for this branch or specified branch

     is_working_tree_clean

     heads
       bare list of local branches

     is_remote
       exit 0 if specified remote exists

     is_ancestor_of
       exit 0 if 1st ref is ancestor to all following

     is_same_object
       exit 0 if specified refs are the same object

     config_keys
       all config keys matching specified pattern (or just all)

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


