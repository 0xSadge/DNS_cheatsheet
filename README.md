# DNS_cheatsheet

## nano /etc/bind/db.[domain]
  $TTL 7200 ; 2 hours
  @ IN SOA romlabolnx.hevs. root.romlabolnx.hevs. (  <!--romlabolnx.hevs. : serveur DNS principal  /////  root.romlabolnx.hevs. :  'faux' email = 'bypass'-->
   2026010904 ; serial
   172800 ; refresh (2 days)
   14400 ; retry (4 hours)
   3628800 ; expire (6 weeks)
   604800 ; minimum (1 week)
   )
   IN NS [hostname].romlabolnx.hevs.
   IN MX 10 mail
  
  mail IN A 192.168.108.5
  [hostname] IN A 192.168.108.5 
  winclient IN A 192.168.108.100
  mywindows IN CNAME winclient


## cat /etc/hosts
127.0.0.1	localhost
#127.0.1.1	Debian.linux.hevs	romdebian    <!-- commented when DNS config is finished-->
