# The begining of my blog...

## Setting up Jekyll for GitHub Pages

[Jekyll Installation Instructions](https://jekyllrb.com/docs/installation/)

[Using Windows 10 Anniversay+](https://jekyllrb.com/docs/windows/)


[Install Bash](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide)

Note for noobs: [Admin access in Linux aka Root Access](https://msdn.microsoft.com/en-us/commandline/wsl/user_support#permissions)
- Open Bash from Admin CMD/PowerShell to have Root Access rights in Bash

Encoutering Errno::EACCES
- Make sure you ran Bash from an Admin CMD/PowerShell prompt
- IF that still does not help then try using `sudo` in front of the command which is failing. [More info...](https://stackoverflow.com/questions/11496591/ruby-gem-permission-denied-var-lib-gems-using-ubuntu)

Install missing GCC and Make
- `sudo apt-get install gcc`
- `sudo apt-get install make`

### Installing Ruby

[Install Ruby](https://stackoverflow.com/a/18541768/1558446)
- apt-get seems to not install Ruby 2.0 so you'll need to use rvm instead
- After installing Ruby via rvm you will need to run `source /home/[username]/.rvm/scripts/rvm` each time you start bash. This is because the environment needs to load Ruby and Gems into CLI memory. To fix this you need to add the rvm scripts directory to the "bashrc" file.
    - Modify bashrc via nano `nano ~/.bashrc` ([info](https://ubuntuforums.org/showthread.php?t=2158436))
    - Add the following to the end of the file: `[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"` ([info](https://stackoverflow.com/a/4842674/1558446))
    - Exit with _CTRL+X_ and enter _y_ when prompted to save
    - Reload "bashrc" with the command `source ~/.bashrc` ([info](https://stackoverflow.com/a/2518150/1558446))
    - Commands for gem are now available when bash is started!

_NOTE:_ You may see the error message _"Unknown ruby interpreter version (do not know how to handle): RUBY_VERSION."_ Based on [this](https://stackoverflow.com/questions/38765138/how-to-fix-unknown-ruby-interpreter-version-do-not-know-how-to-handle-ruby-v) you can ignore this error.

### Using Jekyll

[Helpful info about using Jekyll](https://jekyllrb.com/docs/templates/#code-snippet-highlighting)

I found that in Windows 10 Anniversary Update the file watcher fails so the command `jekyll serve` does not work. Instead I used `jekyll serve --no-watch`, but that comes at the cost of needing to stop the server, build, then start the server again each time I made a file change I wanted to see. Based on research this is a known issue that should be solved in Windows 10 Creators Update.

I also found that the default port 4000 was also occupied so I use the command `jekyll serve --no-watch --port 9876` to force another unused port.

**FIXED:** Bash in Windows 10 Creators Update now correctly supports file watching so you can use the command `jekyll serve --port 9876` without any issues!

### Theme
In order to use a Jekyll theme on GitHub pages follow these [instructions](https://jekyllrb.com/docs/themes/#installing-a-theme).  

_NOTE:_ I found that `gem "theme-name"` did not work for me, but `gem install "theme-name"` did work.

#### Themes don't work for me...
I think I'm going to bail on themes for now. I cannot figure out how to get a theme to work. I tried to apply "jekyll-theme-minimal" and "jekyll-theme-midnight" but both epically failed. The index page would not render at all after applying one of those themes. I'd like themes to work because "minima" is a bit boring, but there are more important things in life right now than styling my blog posts.
  
install github-pages..



