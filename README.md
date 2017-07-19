# [Contbuild](https://eigenstate.org/contbuild/)

Contbuild is a simple continuous build system that can build any projects.
It is simple and easy to set up, and can run on most Unix systems, and
Plan 9.

Builds for contbuild are defined in a simple ini file, generally looks
something like:

	# globally scoped options act as defaults for all
	# build targets
	repo=git+ssh://git.eigenstate.org/git/ori/mc.git
	# there are 3 builtin notifiers, but you can also do
	# a script:
	notify-email=ori@eigenstate.org
	notify-irc=irc.eigenstate.org/myrddin-dev
	# static html pages are generated with build status.
	notify-http=/path/to/website/build/
	[basic]
		# contbuild can also run some tools that will
		# attempt to fix the build, which is useful for
		# os-specific generation steps.
		fix=regen-bootstrap.sh
	[self-hosting]
		# we default to master, but other branches are ok too.
		branch=self-hosting
		# custom build commands? no problem!
		build=mbld
		test=mbld test
		clean=mbld clean
	[qbe]
		# Of course, global options can be overridden
		# in any rule
		repo=git://c9x.me/qbe.git

Full documentation is available on [the website](https://eigenstate.org/contbuild/)
