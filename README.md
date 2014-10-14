# Roundcube Majordomo
## Roundcube server-side helper, version 0.1
### by Jaromil @ Dyne.org

Roundcube Majordomo, or Roundomo in brief, is a backend agent for Roundcube webmail setups that takes advantage of Sieve scripting language for server-side filtering into folders.

Roundomo is developed for the Dyne.org webmail and its targeted to be used on a Postfix/Dovecot2 setup supporting multiple domains.  An example of such a configuration is [detailed here](https://www.digitalocean.com/community/tutorials/how-to-configure-a-mail-server-using-postfix-dovecot-mysql-and-spamassasin).

Roundomo runs from /vmail/'s crontab, which is usually the Dovecot user. It reads the users addressbook from roundcube and compiles a set of sieve filters to implement a whitelist system structured as 3-tier imap folder separation a'la [JaroMail](http://www.dyne.org/software/jaro-mail).

# Raison d'être

Roundcube majordomo is there to organize the e-mail workflow so that one's attention is dedicated to important communications, rather than being constantly distracted by various degrees of spam and the need to weed it out of the mailbox. This ambitious task is pursued by realizing an integrated approach consisting of flexible whitelisting and the distinction between mails from known people and the rest.


 Folder         | What goes in there
----------------|--------------------------------------------------
 *INBOX*        | Mails whose sender is known (Whitelist)
 *priv*         | Unknown sender, we are the explicit destination
 *unsorted*     | Unknown sender, we are in cc: or somehow reached

The advantage using such a folder organization is that every time we open up the mail reader (quickly checking INBOX from our phone, for instance) we will be presented with something we are likely to be most interested in (known people replying our mails) and progressively, as we will have the time to scroll through, mails from "new people" or mass mailings of sort. Please note this organization does not includes spam, which is supposedly weeded out on the server via spamlists: White/Blacklisting has more to do with our own selection of content sources than with the generic protection from random pieces of information.


For more information about this 3-tier imap folder system, see JaroMail's manual on:
https://files.dyne.org/jaromail/jaromail-manual.pdf

# Usage

Once installed, roundcube webmail users can add or remove people from the addressbook, import addresses etc. and all the addressbook will be used to compose the whitelist automatically.

# Disclaimer

Roundcube Majordomo is Copyright (C) 2014 Denis Roio <jaromil@dyne.org>

This source code is free software; you can redistribute it and/or
modify it under the terms of the GNU Public License as published by
the Free Software Foundation; either version 3 of the License, or (at
your option) any later version.

This source code is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  Please refer to
the GNU Public License for more details.

You should have received a copy of the GNU Public License along with
this source code; if not, write to: Free Software Foundation, Inc.,
675 Mass Ave, Cambridge, MA 02139, USA.
