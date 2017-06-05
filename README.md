# This package 
- will setup a windows machine with mac keybindings ( remapping the windows key to be a Meta key )
- will set up intellij with keybindings from Sublime text for mac
- will set up a windows machine with something resembling spotlight for file launching
- will set up windows machine with an ok Terminal basic unix commands
- will set up a decent ssh client over terminal
- will set up AWS tools 
- will set up Ansible

## How to set up on Windows machine

	install cygwin ( unix tools for windows, when installing see below for packages to install)
	install intellij IDE  ( webstorm, rubymine ... a decent ide )
	install launchy ( something like spotlight )
	install sublime 

	Launchy config
		launchy settings
			plugins
				runner (map)
					iterm => C:/cygwin64/bin/mintty.exe
					mine => C:/Program Files/JetBrains/WebStorm 2017.1.3/bin/webstorm64.exe
			catalog
				C:/Program Files (x86) => *.exe
				C:/Program Files/Sublime Text 3  => *.exe
				C:/Program Files/JetBrains/WebStorm 2017.1.3/bin  => *.exe



	cygwin configure:
		add alias for sublime to cygwin.
			in cygwin terminal
			echo 'alias subl="/cygdrive/c/Program\ Files/Sublime\ Text\ 3/sublime_text.exe"' >> ~/.bashrc


		in cygwin install:
			openssh
			git
			zip
			unzip
			bind-utils
			gnupg
			python2
			dos2unix
			python2-pip
			ruby
			curl
			wget
			jq
			lynx
			make
			vim
			nano
			tmux
			cygutils-extra

			todo ---install zsh,  tab completions, git completions, oh-my-zsh

		open cygwin shell, and make symlinks
			cd /bin
			ln -s pip2.7 pip
			ln -s getclip pbcopy
			ln -s putclip pbpaste
			ln -s easy_install-2.7 easy_install
			

        git config --global core.eol lf
        git config --global core.autocrlf input
        
        edit your .basrhc file:
        
        alias subl="/cygdrive/c/Program\ Files/Sublime\ Text\ 3/sublime_text.exe"
        alias open='cygstart'
        if [[ ${INTELLIJ} == "true" ]]; then
          cd ${OLDPWD}
        fi      
        wstorm() {
            /cygdrive/c/Program\ Files/JetBrains/WebStorm\ 2017.1.3/bin/webstorm.exe $1
        }
        stty lnext ^q stop undef start undef
        
        configure pip to work in corporate network:
        
            cd ~
            mkdir .pip
            cd .pip
            vi pip.conf
            add:
                [global]
                index-url=http://pypi.python.org/simple/
                trusted-host=pypi.python.org

		install aws tools
			pip install --index-url=http://pypi.python.org/simple/ --trusted-host pypi.python.org awscli

        install eb tools
            pip install --upgrade --user --index-url=http://pypi.python.org/simple/ --trusted-host pypi.python.org urllib3
            pip install --upgrade --user --index-url=http://pypi.python.org/simple/ --trusted-host pypi.python.org awsebcli
            add to end of your .bashrc
                export PATH=~/.local/bin:$PATH
		install ansible tools
			pip install --index-url=http://pypi.python.org/simple/ --trusted-host pypi.python.org ansible
			
		set up cygwin as terminal in intellij
			https://engineroom.teamwork.com/using-cygwins-bash-terminal-in-a-jetbrains-ide/

		install a cygwin package manager
		    curl -k -L rawgit.com/transcode-open/apt-cyg/master/apt-cyg > apt-cyg
            install apt-cyg /bin

		set up paste in cygwin ( not yet working for me)
			http://www.saltycrane.com/blog/2008/05/how-to-paste-in-cygwin-bash-using-ctrl/



	Intelij keybindings and plugin Settings very closely emulating OSX sublime text. 
	    If you don't want Mac keybindings, dont install the settings file.
        
		Import the settings.jar in your ide.   File => Import Settings

		I am using the following plugins, The important one are Lines Sorter,  Extra Actions and Database Navigator

		- Database Navigator
		- EJS
		- Javascript Intensions
		- Ember.js
		- Extra Actions
		- Handlebars/mustache
		- JavaScript.next Support Plugin
		- Karma
		- Lines Sorter    
		- Markdown support
		- React-Templates
		- Shell Process
		- YAML/Ansible support


	Set up intellij keybindings
		disable windows hotkeys	(use method 1 regedit)
		    
		    If your Windows + P key pulls up a switch to projector popup, disable in the bios.
		    -- otherwise It is otherwise mapped to alt + P 
		    
			http://www.askvg.com/tip-how-to-disable-all-win-keyboard-shortcuts-hotkeys-in-windows/
				1. Type regedit in RUN or Start search box and press Enter. It'll open Registry Editor.
				2. Now go to following key:
				HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer

				3. In right-side pane, create a new DWORD NoWinKeys and set its value to 1
				4. Close Registry Editor and restart your system. After reboot the WIN+ hotkeys will be turned off in your system.
				
				5. export this registry setting, if you are in a corporate env, you will most likely need to reapply every so often.
				
				remap windows key to meta key in intellij
					File : Edit Custom Properties
					Add:
						keymap.windows.as.meta=true

                in intellij terminal settings set the run file as
                "C:\cygwin64\bin\bash.exe" --login -i
                
                in C:\cygwin\etc\bash.bashrc

         
         
        on bottom of file
             cd "cd ${OLDPWD}"
               
                in your .bashrc set:
                    if [[ ${INTELLIJ} == "true" ]]; then
                      cd ${OLDPWD}
                    fi




		download settings for webstorm from
			https://github.com/joeljensen/settings
			
			install settings in intellij if you want mac sublime keybindings.
			    you probabally don't want this...
				File : import settings

		install plugins:
			lines-sorter
			database navigator
			sql generator

