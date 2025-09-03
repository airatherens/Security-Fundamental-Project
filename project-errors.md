ITSC 300 – Final Project
Aira Therens, Gia Huy Pham, Chan Quyen Khuu

Project Errors:
PART 4:
The internal hosts (client machine) cannot access box.net for some reason. The site is blocked by something in the three-tiered URL filters. It is specifically online-storage-and-backup. However, enabling and allowing this category across all 3 tiers, as well as the policies they are applied to, seems to not make a difference and when the client tries to go to box.net, the site is always blocked.
Nslookup also does not work, however we tried extensively to try to make it work by:
-	Making sure the sinkhole.txt file was configured correctly on policies
-	Making sure that phproxy.org was in fact inside of the file
-	Syntax of the nslookup command
None of this seemed to work so we decided to just move forward with the project.

PART 5:
Global protect latest version is installed, gateway and portals are configured, as well as authentication profiles, service profiles, tunnels, and correct ip pool ranges.
However, even though all of this is configured as instructed, global protect cannot be connected to through the portals or gateways. I believe that this is a license issue as I have tried several times to reconfigure and make sure everything is configured CORRECTLY, but to no avail. We have also even cross-checked and asked other groups if they have had the same issue, and it seems that no one can get it to work, so unfortunately ours does not work either.





