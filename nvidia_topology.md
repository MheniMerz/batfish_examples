graph batfish_examples_network{
   
   "fake" [function="fake"]
   "oob-mgmt-server"  [function="oob-server" cpu="4" memory="2048"]
   "oob-mgmt-switch"  [function="oob-switch" mgmt_ip="192.168.200.251" ports="64"]

   "as1core1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.11" ports="54"]
   "as1border1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.12" ports="54"]
   "as1border2" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.13" ports="54"]

   "as2core1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.21" ports="54"]
   "as2core2" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.22" ports="54"]
   "as2border1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.23" ports="54"]
   "as2border2" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.24" ports="54"]
   "as2dist1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.25" ports="54"]
   "as2dist2" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.26" ports="54"]
   "as2dept1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.27" ports="54"]
   "host1" [function="host"  os="generic/ubuntu1804" mgmt_ip="192.168.200.28" nic_model="e1000" memory="1024"]
   "host2" [function="host"  os="generic/ubuntu1804" mgmt_ip="192.168.200.29" nic_model="e1000" memory="1024"]

   "as3core1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.31" ports="54"]
   "as3border1" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.32" ports="54"]
   "as3border2" [function="not-provisioned"  os="sonic-202012-f6f4c7f4" mgmt_ip="192.168.200.33" ports="54"]

   "as1core1":"swp1" -- "as1border1":"swp1"
   "as1core1":"swp2" -- "as1border2":"swp1"

   "as1border1":"swp2" -- "as2border1":"swp1"

   "as1border2":"swp2" -- "as3border2":"swp2"

   "as2border1":"swp2" -- "as2core1":"swp1"
   "as2border1":"swp3" -- "as2core2":"swp1"
   
   "as2border2":"swp1" -- "as3border1":"swp2"
   "as2border2":"swp3" -- "as2core2":"swp2"

   "as2core1":"swp2" -- "as2border2":"swp2"
   "as2core1":"swp3" -- "as2dist1":"swp1"
   "as2core1":"swp4" -- "as2dist2":"swp1"
   
   "as2core2":"swp3" -- "as2dist1":"swp2"
   "as2core2":"swp4" -- "as2dist2":"swp2"

   "as2dist1":"swp3" -- "as2dept1":"swp1"
   "as2dist2":"swp3" -- "as2dept1":"swp2"

   "as2dept1":"swp3" -- "host1":"eth1"
   "as2dept1":"swp4" -- "host2":"eth1"

   "as3core1":"swp1" -- "as3border1":"swp1"
   "as3core1":"swp2" -- "as3border2":"swp1"

   "oob-mgmt-server":"eth1" -- "oob-mgmt-switch":"swp1"   [left_mac="44:38:50:22:01:01"] 
   "as1core1":"eth0"        -- "oob-mgmt-switch":"swp2"   [left_mac="44:38:50:22:01:02"] 
   "as1border1":"eth0"      -- "oob-mgmt-switch":"swp3"   [left_mac="44:38:50:22:01:03"]
   "as1border2":"eth0"      -- "oob-mgmt-switch":"swp4"   [left_mac="44:38:50:22:01:04"]
   "as2core1":"eth0"        -- "oob-mgmt-switch":"swp5"   [left_mac="44:38:50:22:01:05"]
   "as2core2":"eth0"        -- "oob-mgmt-switch":"swp6"   [left_mac="44:38:50:22:01:06"]
   "as2border1":"eth0"      -- "oob-mgmt-switch":"swp7"   [left_mac="44:38:50:22:01:07"]
   "as2border2":"eth0"      -- "oob-mgmt-switch":"swp8"   [left_mac="44:38:50:22:01:08"]
   "as2dist1":"eth0"        -- "oob-mgmt-switch":"swp9"   [left_mac="44:38:50:22:01:09"]
   "as2dist2":"eth0"        -- "oob-mgmt-switch":"swp10"  [left_mac="44:38:50:22:01:10"]
   "as2dept1":"eth0"        -- "oob-mgmt-switch":"swp11"  [left_mac="44:38:50:22:01:11"]
   "as3core1":"eth0"        -- "oob-mgmt-switch":"swp12"  [left_mac="44:38:50:22:01:12"]
   "as3border1":"eth0"      -- "oob-mgmt-switch":"swp13"  [left_mac="44:38:50:22:01:13"]
   "as3border2":"eth0"      -- "oob-mgmt-switch":"swp14"  [left_mac="44:38:50:22:01:14"]
   "host1":"eth0"           -- "oob-mgmt-switch":"swp15"  [left_mac="44:38:50:22:01:15"]
   "host2":"eth0"           -- "oob-mgmt-switch":"swp16"  [left_mac="44:38:50:22:01:16"]

}

