NOTE: For more recent development, check out Michel Oosterhof's fork
Kippo

Kippo is a medium interaction SSH honeypot designed to log brute force attacks and, most importantly, the entire shell interaction performed by the attacker.

Kippo is inspired, but not based on Kojoney.
Demo

Some interesting logs from a live Kippo installation below (viewable within a web browser with the help of Ajaxterm). Note that some commands may have been improved since these logs were recorded.

    2009-11-22
    2009-11-23
    2009-11-23
    2010-03-16

Features

Some interesting features:

    Fake filesystem with the ability to add/remove files. A full fake filesystem resembling a Debian 5.0 installation is included
    Possibility of adding fake file contents so the attacker can 'cat' files such as /etc/passwd. Only minimal file contents are included
    Session logs stored in an UML Compatible format for easy replay with original timings
    Just like Kojoney, Kippo saves files downloaded with wget for later inspection
    Trickery; ssh pretends to connect somewhere, exit doesn't really exit, etc

Requirements

Software required:

    An operating system (tested on Debian, CentOS, FreeBSD and Windows 7)
    Python 2.5+
    Twisted 8.0 to 15.1.0
    PyCrypto
    Zope Interface

See Wiki for some installation instructions.
How to run it?

Edit kippo.cfg to your liking and start the honeypot by running:

./start.sh

start.sh is a simple shell script that runs Kippo in the background using twistd. Detailed startup options can be given by running twistd manually. For example, to run Kippo in foreground:

twistd -y kippo.tac -n

By default Kippo listens for ssh connections on port 2222. You can change this, but do not change it to 22 as it requires root privileges. Use port forwarding instead. (More info: MakingKippoReachable).

Files of interest:

    dl/ - files downloaded with wget are stored here
    log/kippo.log - log/debug output
    log/tty/ - session logs
    utils/playlog.py - utility to replay session logs
    utils/createfs.py - used to create fs.pickle
    fs.pickle - fake filesystem
    honeyfs/ - file contents for the fake filesystem - feel free to copy a real system here

Is it secure?

Maybe. See FAQ
I have some questions!

I am might be reachable via e-mail: desaster at gmail dot com, or as desaster on the #honeypots channel in the freenode IRC network.
