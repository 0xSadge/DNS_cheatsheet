# DNS_cheatsheet


## nano /etc/bind/named.conf         <!--Pour specifié les connexions authorisé -->
acl internals {
  127.0.0.0/8;
  [IP_RESEAU]/24;                    <!-- IP_RESEAU exercice = 192.168.108.0/24 -->
  };      
  
## nano /etc/bind/named.conf.options  <!-- Configurer les paramètres globaux d'un serveur DNS BIND9 -->
options{
  allow-query { internals; };         <!-- Allowing only clients inside the internals ACL are allowed to to a query -->
  forwarders { 8.8.8.8; };            <!-- Using google DNS servers for forwarding -->
}


## nano /etc/default/named            <!-- Limiter requêtes à IPV4 -->
OPTIONS="-u bind -4"


## nano /etc/bind/db.[domain]         <!-- Configuration de la local zone (DNS ?) -->
  $TTL 7200 ; 2 hours
  @ IN SOA romlabolnx.hevs. root.romlabolnx.hevs. (  <!--romlabolnx.hevs. : serveur DNS principal |||||| root.romlabolnx.hevs. :  'faux' email = 'bypass'-->
   2026010904 ; serial                <!-- !!!!! INCREMENTER A CHAQUE FOIS LE SERIAL NUMBER !!!!! -->
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


## cat /etc/hosts                  <!-- Configurer/résoudre le hostname si DNS perso -->
127.0.0.1	localhost
#127.0.1.1	Debian.linux.hevs	romdebian    <!-- commented when DNS config is finished-->
