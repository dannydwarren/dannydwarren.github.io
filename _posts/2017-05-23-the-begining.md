# The begining of my blog...

## Setting up Jekyll for GitHub Pages

[Jekyll Installation Instructions](https://jekyllrb.com/docs/installation/)

[Using Windows 10 Anniversay+](https://jekyllrb.com/docs/windows/)


[Install Bash](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide)

Note for noobs: [Admin access in Linux aka Root Access](https://msdn.microsoft.com/en-us/commandline/wsl/user_support#permissions)
- Open Bash from Admin CMD/PowerShell to have Root Access rights in Bash

Encoutering Errno::EACCES
- Make sure you ran Bash from an Admin CMD/PowerShell prompt
- IF that still does not help then try using ```sudo``` in front of the command which is failing. [More info...](https://stackoverflow.com/questions/11496591/ruby-gem-permission-denied-var-lib-gems-using-ubuntu)

Install missing GCC and Make
- ```sudo apt-get install gcc```
- ```sudo apt-get install make```

[Install Ruby](https://stackoverflow.com/a/18541768/1558446)
- apt-get seems to not install Ruby 2.0 so you'll need to use rvm instead

[Helpful info about using Jekyll](https://jekyllrb.com/docs/templates/#code-snippet-highlighting)

Seem to need to run ```source /home/[username]/.rvm/scripts/rvm``` each time I start bash.




