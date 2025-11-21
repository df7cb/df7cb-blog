---
title: "Using multiple IMAP accounts with Mutt"
date: 2010-02-17T13:21:52+01:00
tags:
- debian
- unix
---

Mutt's configuration is sometime more a toolbox than something offering ready
solutions, and "how to I use multiple accounts?" is one of the most FAQs.
Here's a condensed version of my setup.

In the most simple solution, just 'c'hange folders to the IMAP server:

    c imaps://imap.example.com <enter>
    c imaps://imap.otherdomain.tld <enter>

That's cumbersome to type, so let's automate it:

    # .mutt/muttrc
    macro index <f2> '<change-folder>imaps://imap.example.com<enter>'
    macro index <f3> '<change-folder>imaps://imap.otherdomain.tld<enter>'

That would be the basic setup.

The two accounts have settings associated with them, we put them in two files:

    # .mutt/account.example
    set from=me@example.com
    set hostname="example.com"
    set folder="imaps://imap.example.com/"
    set postponed="=Drafts"
    set spoolfile="imaps://imap.example.com/INBOX"
    set signature="~/.mutt/signature.example"
    set smtp_url="smtp://me@mail.example.com" smtp_pass="$my_pw_example"

    # .mutt/account.otherdomain
    set from=myself@otherdomain.tld
    set hostname="otherdomain.tld"
    set folder="imaps://imap.otherdomain.tld/"
    set postponed="=Drafts"
    set spoolfile="imaps://imap.otherdomain.tld/INBOX"
    set signature="~/.mutt/signature.otherdomain"
    set smtp_url="smtp://myself@mail.otherdomain.tld" smtp_pass="$my_pw_otherdomain"

Now all that's left to do is two folder-hooks to load the files:

    # .mutt/muttrc
    folder-hook 'example.com' 'source ~/.mutt/account.example'
    folder-hook 'otherdomain.tld' 'source ~/.mutt/account.otherdomain'
    # switch to default account on startup
    source ~/.mutt/account.example

A slight variation of the macros also uses the account files:

    macro index <f2> '<sync-mailbox><enter-command>source ~/.mutt/account.example<enter><change-folder>!<enter>'
    macro index <f3> '<sync-mailbox><enter-command>source ~/.mutt/account.otherdomain<enter><change-folder>!<enter>'

To save entering the password all the time, we use account-hooks:

    account-hook example.org 'set imap_user=me imap_pass=pw1'
    account-hook otherdomain.tld 'set imap_user=myself imap_pass=pw2'

Putting passwords in configs isn't something I like, so I pull them from the
Gnome keyring:

    set my_pw_example=`gnome-keyring-query get mutt_example`
    set my_pw_otherdomain=`gnome-keyring-query get mutt_otherdomain`
    account-hook example.org 'set imap_user=me imap_pass=$my_pw_example'
    account-hook otherdomain.tld 'set imap_user=myself imap_pass=$my_pw_otherdomain'

(I found gnome-keyring-query in the
<a href="http://www.gentoo-wiki.info/HOWTO_Use_gnome-keyring_to_store_SSH_passphrases">Gentoo Wiki</a>.)

Martti Rahkila has <a href="http://www.acoustics.hut.fi/~mara/mutt/profiles.html">more verbose article</a> with similar ideas.

*Update 2013-01-02:* smtp_url and smtp_pass added
