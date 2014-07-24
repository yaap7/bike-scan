# bike-scan

## The what?
bike-scan is a wrapper to turn ike-scan into a brute-force tool. It does this by testing a remote host with every possible combination of transforms, in the chosen order of 'rarity'. Eg. all DES, 3DES, AES, MD5, SHA1, PSK, MOD1 types before testing less common combinations.
By default, bike-scan will try and brute-force transforms in main mode first, then move onto aggressive mode.

## The why?
*"Doesn't ike-scan already do this?"*

Well, no. ike-scan is great for finding hosts running ike on UDP port 500, however I've found some VPN servers to quite finicky requiring exact transform requests before kicking off a handshake and revealing their secrets.
As a penetration tester I just wanted one tool I could point at a VPN server and discover all the transforms it supports.

*"Main mode? aren't you only really interested in aggressive mode / dump PSK / crack etc?"*

Yes, certainly handy, however discovering all the main mode transforms can give a penetration tester more insight into how WAN VPN connections may be configured. Also, I like to know if crappy DES / MD5 / PSK / MOD 768 main mode transforms are supported. You should report on those too, right?

*"Bash? Why didn't you use python, ruby, assembly, Cobol or some other obscure language?"*

Because ike-scan does everything needed except brute-force. It handles sockets, sets up the handshake and tells you what it finds. It's also very quick. And because pure Bash, look Ma, no grep!

*"Why did, or didn't you do $blah?"*

This is github, you have the power :) 

## To do
* bike-scan certainly speeds up getting a full list of supported transforms, however when specifying all transform combinations 'Common, Rare and Very rare' (option -Rcrv) - 10800 combinations, it can take a while. Still quicker than doing it manually :) Ike-scan supports specifying multiple transforms per request, so its possible to add this functionality to greatly increase the speed.
* Some kind of progress output.
* Perhaps different output formats, XML etc.
 
