# Week 7
## 3.4 Managing Software

This week I explored the `sudo` function. 

I started with the `sudo apt update` command. The results were 519 updates required.

I then ran the `sudo apt upgrade` command to install the requested updates.
*Note to self, check updates every login*. I thought I was doing this, but I might have missed a
few weeks-, or forgot to restart. **It takes forever to run 519 updates**.

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
Then installed tldr using the command `sudo apt install tldr`. I installed the `tldr`. I went ahead and installed games too just for the practice learning.

I first used the search feature, `apt search bsdgames`. Then I installed the games, `sudo apt install bsdgames`. 
I had issues with connections with my VM today. I am not sure what the cause was. 

Once the connection issues seemed to stop I came back in and practiced Managing Systems again. I started with `sudo mkdir data' and made a directory titled data. I then used `sudo rmdir data` and removed it. I then put it back again. 

I went through all the snytax and commands to uninstall and then reinstalled tldr, for ***practice***. 
Used `sudo apt --purge remove tldr`, `sudo apt autoremove`, and `sudo apt clean`, before using `sudo apt install tldr` again. 

## Library Search
Exploring Z93.50 protocol. Used `apt search yaz` to find: 

```
yaz/jammy 5.31.1-1build1 amd64
  Z39.50/SRW/SRU toolkit (utilities)
```

Used `sudo apt install yaz` for instalation. 

I went ahead and used the example search queries to confirm that I could reproduce the same results. 
- find @and @attr 1=4 "information" @attr 1=21 "library science" resulting in ***662** results.*
- f @and @attr 1=21 "library science" @attr 1=21 "philosophy" resulting in ***58** results.*
- f @attr 1=1 "mcmurtry, larry" resulting in ***60** results.**
- f @attr 1=1016 "c programming language" resulting in ***1636** results.*

I searched using `f @attr 1=1 "burns, sean"` and came back with 19 results. But I noticed as I reviewed the records one by one that the words *burns* and *sean* were present in the MARC record, but not always together. 

I also searched ` f @attr 1=4 "social emotional"` and returned with 1 record. Which was interesting. It also did not have the term 8social emotional8 in the title, but the record was about this topic. 

I also cannot help but wonder if I would have enjoyed using this function in 601 and 602. Because this was a very fun way to explore the catalog. 



