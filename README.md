svn-ws
======

`svn-ws` is a shell script which performs operations on a related set of svn-controlled directories contained within a common subdirectory 'workspace'.

It allows svn commands to be applied across a set of workspace directories. A common example is to query the status of all the svn repositories in your workspace:

    svn-ws status


Will run `svn status` across all of the svn directories in the workspace defined by `$SVN_WORKSPACE`.


#### GIT_WORKSPACE

SVN_WORKSPACE is an environment variable specifying the workspace directory. It can be overridden usind the `-d <dir>` argument.


#### Usage

From the help:

    Usage: svn-ws [-d <dir>] [-f] [-i] <cmd>
           svn-ws -l
    Runs given svn command on all svn directories in $SVN_WORKSPACE
    
    Arguments:
    
      [-d <dir>] [-f] [-i] <cmd>:
          -d <dir>: use given directory instead of $SVN_WORKSPACE
          -f: force - ignore errors if they occur on individual directories
          -i: interactive - ask before running command on each directory
    
        <cmd>: The svn command to execute.
               The 'svn' part of the command is optional (assumed) and can be left out.
    
      -l: list - list the svn directories in workspace
    
    Using a .svnwsinclude file
    The file ${SVN_WORKSPACE}/.svnwsinclude, if present, specifies a list of directories to include.
    If this file is given then only the files listed are included.
    Use one directory name per line in file, directory name only.
    
    Using a .svnwsignore file
    The file ${SVN_WORKSPACE}/.svnwsignore, if present, specifies a list of directories to ignore.
    Use one directory name per line in file, directory name only.
    
    Examples:
    svn-ws svn status | short form: svn-ws status
    svn-ws svn rebase | short form: svn-ws svn rebase
    svn-ws -i commit
    svn-ws -d /path/to/other/workspace status
    svn-ws -l



