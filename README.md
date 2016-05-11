# ld64
Historic and current versions of Apple's ld64 for the purpose of easy
comparison and forward-porting of PPC support

This repository contains all publicly released versions of ld64 on the master
branch. Each version has been imported as a single commit and tagged as
ld64-VERSION. This way, they can easily be compared and changes extracted.

This has been used to forward-port PPC support from version 127.2 to all the
later ones, with special focus on 128.2, 236.2 and 241.9. For this, a branch
called ld64-VERSION-ppc has been branched off at each version's tag. PPC
functionality was first applied as a plain patch between version 127.2 and
128.2 and then cherry-picked over to the later versions' PPC branches.

So if you now want to extract all the patches necessary to add PPC support back
into ld64-241.9, you just need check out the PPC branch and format-patch
everything relative to the release tag. So you run:

```
git checkout ld64-241.9-ppc
git format-patch ld64-241.9
```

If you want one big patch with everything, just run:

```
git diff ld64-241.9 ld64-241.9-ppc
```

Obviously you can also just compile the patched version directly from the
respective checked out branch.

I sincerely hope this will be of some use to someone. Unfortunately it didn't
solve my mis-linking problem when trying to compile llvm/clang on OS X
10.4/10.5. But it doesn't work any worse either. ;)
