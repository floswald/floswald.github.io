---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Create and Rename Files with Fish"
subtitle: ""
summary: ""
authors: []
tags: [fish]
categories: []
date: 2023-09-13T22:54:39+02:00
lastmod: 2023-09-13T22:54:39+02:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

I am an avid user of the [fish shell](https://fishshell.com/). Here is a small demo of a common task I have. How to efficiently rename a long list of files in a directory?

```bash
# lets create 10 empty text files:
floswald@PTL11077 ~/test> for i in (seq 1 10)
                              touch testfile$i.txt
                          end

floswald@PTL11077 ~/test> ls
testfile1.txt   testfile2.txt   testfile4.txt   testfile6.txt   testfile8.txt
testfile10.txt  testfile3.txt   testfile5.txt   testfile7.txt   testfile9.txt
```

no suppose I realize that `testfile` is actually a poor name for this. I want to call them `trainfile` instead. Here is how to change those filenames in batch instead of manually one by one. The concept is called [command substition](https://fishshell.com/docs/current/language.html#command-substitution), as in

```
echo (pwd)  
```
which evalutes first the command in the bracket before giving it to the `echo` command.

in our case, we use a `sed` call to substitute parts of each filename. `sed` is extremeley powerful, look here for a concise [manual](https://www.grymoire.com/Unix/Sed.html). In our case, we want to substitute `test` with `train`. The `s` command in `sed` does that. The syntax is `s/old/new/`. So we want to substitute `test` with `train`. We can do that like this:


```bash
floswald@PTL11077 ~/test [64]> for i in *.txt
                                   mv $i ( echo $i | sed 's/test/train/g' )
                               end

floswald@PTL11077 ~/test> ls
trainfile1.txt   trainfile2.txt   trainfile4.txt   trainfile6.txt   trainfile8.txt
trainfile10.txt  trainfile3.txt   trainfile5.txt   trainfile7.txt   trainfile9.txt
```

