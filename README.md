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


	Intelij keybindings and plugin Settings e very closely emulating OSX sublime text. 

		Import the settings.jar in your ide.   File => Import Settings

		I am using the following plugins, The important one are Lines Sorter and  Extra Actions

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
			http://www.askvg.com/tip-how-to-disable-all-win-keyboard-shortcuts-hotkeys-in-windows/
				1. Type regedit in RUN or Start search box and press Enter. It'll open Registry Editor.
				2. Now go to following key:
				HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer

				3. In right-side pane, create a new DWORD NoWinKeys and set its value to 1
				4. Close Registry Editor and restart your system. After reboot the WIN+ hotkeys will be turned off in your system.
				
				remap windows key to meta key in intellij
					File : Edit Custom Properties
					Add:
						keymap.windows.as.meta=true


		download settings for webstorm from
			https://github.com/joeljensen/settings

			install settings in intellij 
				File : import settings

		install plugins:
			lines-sorter
			database navigator
			sql generator

	cygwin configure:
		add alias for sublime to cygwin.
			in cygwin terminal
			echo 'alias subl="/cygdrive/c/Program\ Files/Sublime\ Text\ 3/sublime_text.exe"' >> ~/.bashrc


		in cygwin install:
			openssh
			git
			python 2
			python pip for python 2
			ruby
			curl
			wget
			lynx
			make
			vim
			nano

		install aws tools
			pip install --index-url=http://pypi.python.org/simple/ --trusted-host pypi.python.org awscli

		install ansible tools
			pip install --index-url=http://pypi.python.org/simple/ --trusted-host pypi.python.org ansible

		set up cygwin as terminal in intellij
			https://engineroom.teamwork.com/using-cygwins-bash-terminal-in-a-jetbrains-ide/

		install a cygwin package manager -- (doesn't work for me, would be nice though)
			https://github.com/transcode-open/apt-cyg

		set up paste in cygwin ( not yet working for me)
			http://www.saltycrane.com/blog/2008/05/how-to-paste-in-cygwin-bash-using-ctrl/
			
