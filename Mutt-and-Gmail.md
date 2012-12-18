# Using Mutt with Gmail

## Install mutt  
```text
$ brew install mutt
```  

## Configure mutt (~/.muttrc)  
```text
# A basic .muttrc for use with Gmail

# Change the following six lines to match your Gmail account details
set imap_user = "YOUR.EMAIL@gmail.com"
set imap_pass = "PASSWORD" # If you dont save your password, you will be prompted every time
set smtp_url = "smtp://YOUR.EMAIL@smtp.gmail.com:587/"
set smtp_pass = "PASSWORD"
set from = "YOUR.EMAIL@gmail.com"
set realname = "YOUR NAME"

# Change the following line to a different editor you prefer.
set editor = "nano"

# Basic config, you can leave this as is
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set imap_check_subscribed
set hostname = gmail.com
set mail_check = 120
set timeout = 300
set imap_keepalive = 300
set postponed = "+[GMail]/Drafts"
set record = "+[GMail]/Sent Mail"
set header_cache=~/.mutt/cache/headers
set message_cachedir=~/.mutt/cache/bodies
set certificate_file=~/.mutt/certificates
set move = no
set include
set sort = 'threads'
set sort_aux = 'reverse-last-date-received'
set auto_tag = yes
ignore "Authentication-Results:"
ignore "DomainKey-Signature:"
ignore "DKIM-Signature:"
hdr_order Date From To Cc
alternative_order text/plain text/html *
auto_view text/html
bind editor <Tab> complete-query
bind editor ^T complete
bind editor <space> noop 

# Gmail-style keyboard shortcuts
macro index,pager y "<enter-command>unset trash\n <delete-message>" "Gmail archive message"
macro index,pager d "<enter-command>set trash=\"imaps://imap.googlemail.com/[GMail]/Bin\"\n <delete-message>" "Gmail delete message"
macro index,pager gi "<change-folder>=INBOX<enter>" "Go to inbox"
macro index,pager ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
macro index,pager gs "<change-folder>=[Gmail]/Starred<enter>" "Go to starred messages"
macro index,pager gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"
```  

## Shortcuts for navigating mutt  
- j: to move down  
- k: to move up  
- d: to delete a message  
- y: to archive a message  
- gi: to view your inbox  
- ga: to view all mail (ALL mail, it will take time to load)  
- gd: to view all drafts  
- gs: to view all starred messages  

### Mutt specific  
- t will mark a message  
- s will save a message, or more  
- c lets you change to a different folder  
- / lets you search the current folder  

## Asynchronous  
For some of the above commands, mutt will not do anything immediately. Instead it will mark tasks to carry out. Once youve made all the changes that you wanted, hitting the $ key will apply all the changes to your Gmail inbox.  

## Sending email with mutt  
The basics look like this:  
- Type m (or r if you are replying to a mail)  
- Enter the recipients email address; hit Return  
- Enter a subject; hit Return  
- Write your message  
- Save it  
- Type y and your message will be sent  

All done ? Type 'q' to exit mutt!  

## Useful Links  
http://lifehacker.com/5574557/how-to-use-the-fast-and-powerful-mutt-email-client-with-gmail  
http://www.andrews-corner.org/mutt.html  

