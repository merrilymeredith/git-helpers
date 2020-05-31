git-helpers
-----------

git stuff that doesn't fit in aliases 💖

### git-attic

Lists deleted files by walking back through `git log`

### git-histedit

`histedit` lets you edit the current branch using interactive rebase, but
without actually *moving* the fork point of your branch, avoiding the
complications of fixing up your history and dealing with merge conflicts at
the same time.

See also: `hg histedit`

### git-archive-branch

Converts an unmerged branch to a tag with "old." prefixed, because I'm afraid
to delete things but want them out of sight.

### git-ctags

Helps me run ctags on all tracked files, including as a hook when updating my
repository.  Waits a bit to only rerun once in a series of operations.

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

### git-get

Fetches some perhaps-useful info about the git repository.  This was written as
a personal curiosity after seeing mjd's version and how convoluted coding
against the "plumbing" felt to me.  Instead, this git-get uses the `Rugged`
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


