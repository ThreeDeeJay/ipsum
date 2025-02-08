![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:ip
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2025-02-08)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
134.209.120.69|-|9
80.82.77.202|rnd.group-ib.com|8
92.118.39.72|-|8
92.255.85.188|-|8
92.255.85.189|-|8
129.146.67.131|-|8
178.160.211.111|-|8
193.32.162.131|-|8
195.178.110.76|-|8
218.92.0.111|-|8
218.92.0.114|-|8
218.92.0.198|-|8
218.92.0.217|-|8
218.92.0.230|-|8
218.92.0.232|-|8
218.92.0.233|-|8
218.150.246.42|-|8
71.6.135.131|soda.census.shodan.io|7
2.57.122.189|-|7
75.178.99.71|syn-075-178-099-071.res.spectrum.com|7
89.248.172.16|house.census.shodan.io|7
92.118.39.75|-|7
136.27.51.200|136-27-51-200.cab.webpass.net|7
162.142.125.197|-|7
162.142.125.198|-|7
167.94.138.198|-|7
167.94.138.200|-|7
167.94.145.96|-|7
167.94.145.98|-|7
167.94.145.99|-|7
167.94.145.100|scanner-01.fr7.censys-scanner.com|7
167.94.145.106|-|7
167.94.145.109|-|7
167.94.146.53|-|7
167.94.146.58|-|7
181.225.140.68|-|7
185.165.191.27|red.census.shodan.io|7
193.32.162.132|-|7
193.32.162.133|-|7
193.32.162.135|-|7
194.0.234.38|-|7
206.168.34.90|-|7
207.90.244.5|-|7
218.92.0.112|-|7
218.92.0.216|-|7
218.92.0.218|-|7
218.92.0.219|-|7
218.92.0.220|-|7
218.92.0.221|-|7
218.92.0.222|-|7
218.92.0.223|-|7
218.92.0.225|-|7
218.92.0.226|-|7
218.92.0.227|-|7
218.92.0.228|-|7
218.92.0.229|-|7
218.92.0.231|-|7
218.92.0.235|-|7
218.92.0.236|-|7
218.92.0.237|-|7
222.102.21.102|-|7
162.142.125.193|-|7
167.71.163.147|-|7
187.49.152.10|ns1.entertelecom.com.br|7
189.23.51.118|189-23-51-118.embratel.cloud|7
202.157.186.116|-|7
207.231.111.207|-|7
207.90.244.2|-|7
213.55.85.202|-|7
68.183.88.186|-|7
74.73.241.225|syn-074-073-241-225.res.spectrum.com|7
102.211.152.45|45.152.211.102.angolacables.ao|7
103.226.248.206|-|7
111.67.201.36|-|7
193.32.162.134|-|7
193.32.162.137|-|7
211.105.213.144|-|7
50.201.154.234|-|7
64.23.156.175|-|7
87.120.165.56|-|7
89.168.18.25|-|7
92.118.39.71|-|7
97.107.177.139|-|7
