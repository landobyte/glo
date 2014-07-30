glo
===

A powerful implementation of the Git-fLOw management pattern. Currently stable but in beta.<br>
Make a simlink to glo in this repo or add it to your path and run 'glo help' - that should get you going.<br>
Glo is 100% written in bash-script.

### Basics
Glo works with two main branches (master and dev) that is shared accorss repos. With every command that reads or modifies these branches they are sync first. This way they may always be fast forwarded and will never diverge from local coppies of the branches.

Development is done in task branches and merged into dev if the task is complete.

To create a task, run:<br>
`glo task <Name>`, `glo feature <Name>` or `glo bug <Name>`<br>
To merge a task into dev, run:<br>
`glo apply`<br>

When it is time to create a release of your repo, run:<br>
`glo release`<br>
which will automatically create a release version of the latest state of the dev branch and mark it with the next version number. This release commit is merged into master, which is the 'release branch'.

### Many more features
Glo has many feature to ease the process of keeping your repo neat and synced so that you can get on with your work. One  powerful features of glo is `glo view` which shows you the repo branch structure in an intuitive way. It is much like `git log --graph` but it handles master and dev as special, thus displaying more natural representation of the repo.

```shell
   $           dev Dev commit: Quick work           2014-02-22 FJ   6e3fbc7
   |  @      * task/task21 Work                     2014-02-21 AP   e0e6fe6
   |  |  @   * task/task20 Committing file3         2014-02-20 FJ   a7c7ae3
   |  |  •     Only committing file1 and 2          2014-02-19 FJ   44906c4
   |--'--'   
   o<-,        Completed task task19                2014-02-18 FJ   a170bc3
   |  •        task/task19 Work                     2014-02-17 FJ   5b99204
   |--'      
   o<-,        Completed task task18                2014-02-16 FR   ecc0afe
   |  •        Work                                 2014-02-15 FR   1f2b3a7
   |--'      
   o<-,        Completed task task16                2014-02-14 GYP  16a38cc
   |  •        task/task16 Work                     2014-02-13 GYP  7b1248b
   |->x        Updated task task16 from dev         2014-02-12 GYP  2a2069d
   |  •        Work                                 2014-02-11 GYP  5c2687e
   o<-|--,     Completed task task17                2014-02-10 FJ   3e4ecb2
   |  |  •     task/task17 Work                     2014-02-09 FJ   97378ab
   |  |  •     Work                                 2014-02-08 FJ   594d09b
   |  •  |     Work                                 2014-02-07 GYP  2c8b338
X<-|  |  |     [1.0.0] master Released 1.0.0        2014-02-06 FJ   3870f9d
|  |--'--'   
|  o<-,        Completed task task15                2014-02-05 OP   ab8343e
|  |  •        task/task15 Work                     2014-02-04 OP   99a2d2f
X<-|  |        [0.2.1] Released 0.2.1               2014-02-03 FJ   f45182c
|  |--'      
|  o<-,        Completed task task14                2014-02-02 TJ   e8461bf
|  |  •        task/task14 Work                     2014-02-01 TJ   0aac127
X<-|  |        [0.2.0] Released 0.2.0               2014-01-31 FJ   ceba7aa
|  |--'      
|  o<-,        Completed task task13                2014-01-30 AP   8c4dd80
|  |  •        task/task13 Work                     2014-01-29 AP   221ac29
...
```
Branch master is always first from the left, dev second and thereafter task branches follow. Compare this with a<br>
`git log --graph` printout:
```shell
$> git log --graph --oneline
* 6e3fbc7 Dev commit: Quick work
*   a170bc3 Completed task task19
|\  
| * 5b99204 Work
|/  
*   ecc0afe Completed task task18
|\  
| * 1f2b3a7 Work
|/  
*   16a38cc Completed task task16
|\  
| * 7b1248b Work
| *   2a2069d Updated task task16 from dev
| |\  
| |/  
|/|   
* |   3e4ecb2 Completed task task17
|\ \  
| * | 97378ab Work
| * | 594d09b Work
|/ /  
| * 5c2687e Work
| * 2c8b338 Work
|/  
*   ab8343e Completed task task15
|\  
| * 99a2d2f Work
|/  
*   e8461bf Completed task task14
|\  
| * 0aac127 Work
|/  
*   8c4dd80 Completed task task13
|\  
| * 221ac29 Work
| * c99c7c2 Work
|/  
*   2c60ace Completed task task9
|\  
| * 5ee6a34 Work
* |   b206413 Completed partial task task9
|\ \  
| |/  
| * 5eb9d53 Work
|/  
*   688363f Fixed bug ticket-0034
|\  
| * b67698e Work
|/  
*   d827188 Added feature feature8
:
```

### Plugins
Glo even allow you to extend it's behavior with plugins. An example plugin is available in the plugins directory.

### Comments

Please log any feedback or bugs on github!<br>


