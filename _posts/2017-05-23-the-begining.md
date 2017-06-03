## Setting up Jekyll for GitHub Pages

[Jekyll Installation Instructions](https://jekyllrb.com/docs/installation/)

[Using Windows 10 Anniversary+](https://jekyllrb.com/docs/windows/)


[Install Bash](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide)

Note for noobs: [Admin access in Linux aka Root Access](https://msdn.microsoft.com/en-us/commandline/wsl/user_support#permissions)
- Open Bash from Admin CMD/PowerShell to have Root Access rights in Bash

Encountering Errno::EACCES
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

### Installing Gem "github-pages"
_NOTE:_ I tried to get themes working first, but after adding this package the "minima" theme now works for posts locally so I suggest installing "github-pages" first, then worrying about themes.

Still not entirely sure why github-pages is required, needed, wanted, suggested... but I'm going ahead and installing it since that's where I'm hosting my jekyll site.

- Modify Gemfile
    - Remove/Comment: `gem "jekyll", "3.4.3"`
    - Add/Uncomment: `gem "github-pages", group: :jekyll_plugins`
- Run `gem install github-pages`
    - This took a while, like more than 15 min...
    - NOTE: You can ignore the warning: "warning: insecure world writable dir in /home/username/.rvm/rubies/ruby-2.4.0/bin path, mode 04077 bash windows". [For more info](https://stackoverflow.com/questions/5380671/getting-the-warning-insecure-world-writable-dir-home-chance-in-path-mode-04).
- Run `bundle update`
- Run `bundle install`
    - Not sure if this is necessary after a `bundle update`

_ISSUE:_ I got the following error: "jekyll 3.4.3 | Error:  Could not find a JavaScript runtime. Seettps://github.com/rails/execjs for a list of available runtimes."  
_SOLUTION:_ To fix this I followed the suggestion [here](https://stackoverflow.com/questions/7092107/rails-could-not-find-a-javascript-runtime) to install nodejs, which I thought was already installed.

_ISSUE:_ Next I got the following error: "Error: No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository..."  
_SOLUTION:_ I found my solution in part [here](https://www.hieule.info/programming/fix-errors-github-metadata-ssl-certificate-running-jekyll-serve/). I learned I needed a personal token from GitHub to access metadata. When I created my token I only applied _read_ access to _user info_ and _user email_. Then I used the token like suggested [here](https://github.com/jekyll/github-metadata) like this: `JEKYLL_GITHUB_TOKEN=123abc [bundle exec] jekyll serve --port 9876'

_ISSUE:_ Then I got the error: "Regenerating: 1 file(s) changed at 2017-06-03 16:08:06 ...error: Error: No such file or directory - git". From just a little reading [here](https://github.com/jekyll/github-metadata/issues/57) this apparently indicates git is not in the PATH or maybe not even installed at all.  
_SOLUTION:_ So I followed the "Installation" and "Configuration" steps in [this article](https://help.ubuntu.com/lts/serverguide/git.html).

WOOT! NO MORE ERRORS!!!

### Theme
In order to use a Jekyll theme on GitHub pages follow these [instructions](https://jekyllrb.com/docs/themes/#installing-a-theme).  

_NOTE:_ I found that `gem "theme-name"` did not work for me, but `gem install "theme-name"` did work.

#### Themes don't work for me...
I think I'm going to bail on themes for now. I cannot figure out how to get a theme to work. I tried to apply "jekyll-theme-minimal" and "jekyll-theme-midnight" but both epically failed. The index page would not render at all after applying one of those themes. I'd like themes to work because "minima" is a bit boring, but there are more important things in life right now than styling my blog posts.

It's also worth mentioning that even with "minima" I have not figured out how to get my local server to serve up the theme for posts. It works for index but not for post pages.
