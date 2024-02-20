# Week 7
## 3.4 Managing Software

This week I explored the `sudo` function. 

I started with the `sudo apt update` command. The results were 519 updates required.

I then ran the `sudo apt upgade` command to install the requested updates.
*Note to self, check updates every login*. I thought I was doing this, but I might have missed a
few weeks, or forgot to restart. **It takes forever to run 519 updates**.

![movie-one-eternity-later](https://github.com/JConley1344/SysLib690/assets/157387139/0fe335de-837d-4d3d-b1fd-139acf2e4b8a)

**Updates Installed!**

I then used the command `sudo search tldr`. These were the files that came back.
```
Full Text Search... Done
libghc-tldr-dev/jammy 0.6.4-1build6.3 amd64
  Haskell tldr client

libghc-tldr-doc/jammy 0.6.4-1build6.3 all
  Haskell tldr client; documentation

libghc-tldr-prof/jammy 0.6.4-1build6.3 amd64
  Haskell tldr client; profiling libraries

tldr/jammy 0.6.4-1build6.3 amd64
  Haskell tldr client

tldr-py/jammy 0.7.0-4 all
  Python client for tldr: simplified and community-driven man pages
```

Then I entered `apt show tldr` like in the video. 
Then installed tldr using command `sudo apt install tldr`. I installed the `tldr`. I went ahead and installed games too just for the practice learning.

I first used the search feature, `apt search bsdgames`. Then I installed the games, `sudo apt install bsdgames`. 
I had issues with connections with my VM today. I am not sure what the cause was. 

Once the connection issues seemed to stop I came back in and practiced Managing Systems again. I started with `sudo mkdir data' and made a directory titled data. I then used `sudo rmdir data` and removed it. I then put it back again. 

I went through all the snytax and commands to uninstall and then reinstalled tldr, for ***practice***. 
Used `sudo apt --purge remove tldr`, `sudo apt autoremove`, and `sudo apt clean`, before using `sudo apt install tldr` again. 
