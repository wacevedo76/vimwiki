--------------------------------------------------------------------------------
Terms
  CTCP                       | client-to-client-protocol
                             |
  DCC                        | Direct Client Communication
                             |
Command list
                             |
                             |
  Set/change nick            | /set nick whatyouwant
                             |
  Quit                       | /quit
                             |
  List networks              | /network
                             |
  Connect to a network       | /connect <networkname>
                             |
  Join a Channel             | /join #nameofchannel
                             |
  Hide aspects of the chat   | /window hidelevel +joins +parts +quits
  window                     |
                             |
  Get them Back              | /window hidelevel -joins -parts -quits
                             |
  Hide by default            | /set window_default_hidelevel hidden joins parts quits
                             |
  Add new network, example:  | /network add hackint
  (irc.hackint.org, port 6697| /server add -tls -network hackint irc.hackint.org 6697
   ssl(TLS)                  |
                             |
  command help               | /help commandname
                             |
  Enable server auto connect | /SERVER MODIFY -auto irc.libera.chat
                             |
  Disable serv auto connect  | /SERVER MODIFY -noauto
                             |
  Enable channel auto connect| /CHANNEL ADD -auto #channelname NetworkName
                             |
  Config all open channels   | /ADDALLCHANS
  to auto connect            |
                             |
  List channels              | /LIST    # often very large
                             |
                             |
  List all users on a channel| /NAMES #channel-name
                             |
  Leave a channel            | /LEAVE
                             | /PART #channelname
                             |
  Show information on        | /WHOIS <name>
  specific user              |
                             |
  Set away msg               | /AWAY what ever msg you want to leave
                             |
  list all open windows      | /window list
                             |
Private conversation commands
  Send private message       | /MSG <what ever message you want to send>
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
