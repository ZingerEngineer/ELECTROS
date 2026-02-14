# CD Change Directory 101

- cd default -> logical [-L]
  - Doesn't substitute symlinks to their physical links immediately.
- cd physical [-P]
  - Substitutes symlinks to their physical links immediately.

- Dirs stack:
  - pushd
    - push a new path to the dirs stack
  - popd
    - pop the top value from the stack ( path number '0' )
  - dirs
    1. -c   clear the directory stack
    2. -l   display directory names in full
    3. -p   display directory entries one per line
    4. -v   display numbered list of directory stack

CD Variables:

$OLDPATH
- Stores the old path before the current change directory.
- Substitutes to the "cd -"

CDPATH
- It is an environment variable that needs to be exported using "export".
- It can hold at least one globbed path.
  - Globaled path means that path can be searched by cd.
  - Meaning that you don't have to type the parents of that path anymore.
- To include the current directory as a globbed path, you can set it at the begining of the seach value likes this "export CDPATH=:[path]" / "export CDPATH=.:[path]"
- You separate the search paths using a colon. ":" ex: "export CDPATH=:/etc:home/zindora/Apps"
- CDPATH won't work If the directory starts with:
  1. / (absolute path)
  2. ./ or  ../ (relative path)
  3. ~ (abreviatted path home)

Dots navigation:

1. Parent Jumps:
   Any number of connected double dots. ex: "cd ../../../" will jump 3 parents up.

2. Double Parent Jump:
   "cd ..." will jump 2 parent up.

3. Parent then adjacent Child:
   - Example:
     pwd: /home/zindora/Apps/learning
     "cd ../AL-Ramy-Blog" This will jump 1 parent up and then enters an adjacent child directory.

Note: This works only on 2 dots not 3 dots jump. "cd .../Apps" this gives an error. it should be "cd ../../Apps".

- This works on any number of parents jumps. "../../../zindora/Apps"

