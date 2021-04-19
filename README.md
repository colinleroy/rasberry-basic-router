=== Edit variables ===

* setup-vars.yml: local_sd is the device name and partitions names of the SD card when inserted in your computer. It's usually mmcblk0(p1,p2) when inserted in an SD card slot, sdb(1,2) when inserted via an USB adapter.

* router-vars.yml: Various settings for DHCP leases (range, static list), DNS server etc.

=== Installing ===

1. Run the first playbook to download a minimal Raspbian and install it to the SD card:

`ansible-playbook -i hosts --ask-become-pass prepare-router.yml`

2. Put the SD card in the Pi, boot it, and wait for it to by connectable via ssh (either root or pi user).

3. Run the second playbook to setup dnsmasq and iptables:

`ansible-playbook -i hosts --user root configure-router.yml`

4. You can now plug in the WAN cable to your Pi, via an USB/GBEth adapter or an USB tethered smartphone.
