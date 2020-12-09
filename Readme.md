## Introduction

In this repository presented my tool which is simple in use constructor of console menu for fast run often repeat commands during software develop.

During software develop there is need often to run commands for unit tests, rebuild frontend, stop/run docker containers and etc.

Many of these commands is very verbose, plus they needs certain params which we should to remember.

For solution this problem was create this tool.

## How use it

The console menu configure with one config-file `menu.uml`. He located in same directory with `env` or in `menu` directory (if the meny is complex and his settings spaced in some files)

**Example simple settings in one file `menu.yml`**

    items:
	    1:
		    title: '1. Command 1'
			env: 'dev'
			commands:
				- 'echo %(currentDir)_%(str)'
			catch:
				- 'echo cach'
			vars:
				- str

As result we get follow console meny (after run `./env`)

    0. Exit
    1. Command 1

Not necessary param `catch` sets commands list which runs if at least one command from` commands` section throw error (exit code is not 0).

**Example of submenu setting**

Let we add still one item to our menu:

    items:
	    1:
		    title: '1. Command 1'
			env: 'dev'
			commands:
				- 'echo %(currentDir)_%(str)'
			catch:
				- 'echo cach'
			vars:
				- str
		2:
			title: '2. Sub menu'
			items:
				1:
					title: '1. Command 1'
					env: 'dev'
					commands:
						- 'echo %(currentDir)_%(str)'
					catch:
						- 'echo cach'
					vars:
						- str

The menu will now look like this:

    0. Exit
    1. Command 1
    2. Sub menu

When we chose item 2 then we have look submenu:

**An example for setting up a menu spaced across multiple files you can see in this repository**

An example for use in web development can be viewed in the repository `https://github.com/hrustbb2/env-example.git`