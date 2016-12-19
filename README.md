# check-git

`check-git` is a command line tool.  It scans the current directory
for git repositories that are dirty.  It looks for five things:

* Repositories with changed or untracked files

* Repositories with unpushed changes

* Repositories with stashes

* Repositories with no remotes

* Repositories with a branch other than `master` checked out

The first three indicate a "dirty" repository.  The last two
are just noted.

`check-git` prints a summary of every dirty repository, then it lists
remoteless repos, branched repos, and clean repos.

`check-git --summary` just prints the number of repositories in each
category.

## Example

    $ check-git
    Documents/Code/Audio/SoundScope
       M SoundScope/Base.lproj/MainMenu.xib
       M SoundScope/GraphView.m
      ?? SoundScope.xcodeproj/project.xcworkspace/xcuserdata/
      ?? SoundScope.xcodeproj/xcuserdata/
      ?? kqdemo
      ?? kqdemo.c
      ?? kqdemo.c~

    Documents/Making/Blink Eras
      Your branch is ahead of 'origin/master' by 1 commit.
      ?? KiCAD/BlinkyFeet.pretty/Mushroom.kicad_mod
      stash@{0}: WIP on master: da5589c README: added link for KiCAD graphics tutorial.

    Repositories without Remotes
      Documents/Code/Audio/AUFX 1
      Documents/Code/Audio/AUFX 2
      Documents/Code/Audio/CH11_MIDItoAUGraph

    Branched Repositories
      oscuino-input Desktop/Machine-Learning-Class/wekinator_examples
           DMA-LC-2 Documents/Code/github/PaulStoffregen/cores
            develop Documents/Code/github/audiokit/AudioKit
            buffers Documents/Code/github/kbob/fork
                 kb Documents/Making/Laser/Other Lasers/Software/LasaurApp
            impulse Documents/Making/Rostock MAX/git/RepetierMAX

    Clean Repositories:
      Documents/Code/Angular/angular-seed
      Documents/Code/Audio/MVS 3
      Documents/Code/Rust/multiboot-kernel
      Documents/Code/Scheme/Lisp-In-Small-Pieces
      Documents/Code/Scheme/elco
      Documents/Code/github/1Bitsy/1bitsy-hardware
    
    ------
    Summary
      6 clean repositories
        0 branched
        0 remoteless
      2 dirty repositories
        2 branched
        1 remoteless
      ------
      8 total repositories



## Rust

There is special code to ignore repositories in `.cargo` and
`.multirust` since the Rust tools create dirty repositories there
without user intervention.
