  ### 🎯 What is Next: Task D6 (Permissions Recognition)
  
  From baseline-diagnostic.md, we only have two tasks left in Phase 0: D6 (Permissions) and
  D7 (Troubleshooting)!
  
  Here is your challenge for Task D6:
  
  Take a look at this harmless ls -l line from a Linux system:
  
    -rw-r--r-- 1 muazislambabar muazislambabar 2744617 Sep 22 22:15 'Linux Fundamentals.   
  pdf'
  
  In your own words, break down that line and explain:
  
  1. The Permission String (-rw-r--r--):
      • What do the r, w, and - letters stand for?
      • It is divided into 3 groups of three letters—who do those three groups represent?
      ```
      r : stands for read
      w : stands for write
      - : stands for bank statment

      Yes, it is divided into three groups. I guess, it would be user, admin and root. But i am not sure about it!

      So, guide me about it. I tried to search it from the man pages.
      i types folowing commands:
      
      > man -k permission
      > man -k permission string
      > man chmod
      > man access
      man flatpak-permission
      man cgroup

      I don't know, how to search in man with multiple words, example: i want to search for file permission, then if i type 'man -k file permission', then it would not seacrh it. So, is there a way or not!?

      But i couldn't find information about groups. ANd the permission string, i new about it. i gained this prior knowledge from elsewhere.

      ```
      ***
  2. The Owner and Group:
      • Who is the owner of this file?
        ```
        I don't know even how to find it.
        ```
      • What group owns this file?
      ```
      I don't know

      ```
  3. Directory Bonus Question:
      • If this were a directory instead of a regular file, you would see an x (execute)   
      bit, like drwxr-xr-x.
      • What does the x (execute) permission allow you to do on a directory? (Hint: You    
      cannot "run" a directory like a program, so what does execute mean here?)           
      ```
        I have been unable to know about that. But I would think that maybe,,, i don't know
        
      ``` 
  
