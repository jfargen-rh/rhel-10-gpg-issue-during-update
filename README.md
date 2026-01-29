# RHEL 10 GPG issue during dnf update
When updating packages on Red Hat Enterprise Linux 10 (RHEL10) to the latest versions you may encounter an  error ```Error: GPG check FAILED``` when running ```dnf update```.

You can see the system is already using RHEL10.1, but this may also affect RHEL10.0 releases they haven't been tested:
```
# cat /etc/redhat-release 
Red Hat Enterprise Linux release 10.1 (Coughlan)
```

Here is the output of the dnf update:

```
# dnf update
Updating Subscription Management repositories.
Red Hat Enterprise Linux 10 for x86_64 - BaseOS (RPMs)                                                            7.7 MB/s |  43 MB     00:05    
Red Hat Enterprise Linux 10 for x86_64 - AppStream (RPMs)                                                         2.0 MB/s | 4.2 MB     00:02    
Last metadata expiration check: 0:00:01 ago on Wed 28 Jan 2026 04:25:23 PM PST.
Dependencies resolved.
==================================================================================================================================================
 Package                                      Architecture  Version                                Repository                                Size
==================================================================================================================================================
Installing:
 kernel                                       x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.4 M
Upgrading:
 NetworkManager                               x86_64        1:1.54.0-2.el10_1                      rhel-10-for-x86_64-baseos-rpms           2.2 M
 NetworkManager-libnm                         x86_64        1:1.54.0-2.el10_1                      rhel-10-for-x86_64-baseos-rpms           1.9 M
 NetworkManager-tui                           x86_64        1:1.54.0-2.el10_1                      rhel-10-for-x86_64-baseos-rpms           233 k
 amd-gpu-firmware                             noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-appstream-rpms         28 M
 amd-ucode-firmware                           noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           466 k
 at                                           x86_64        3.2.5-14.el10_1                        rhel-10-for-x86_64-baseos-rpms            66 k
 atheros-firmware                             noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            41 M
 bind-libs                                    x86_64        32:9.18.33-10.el10_1.2                 rhel-10-for-x86_64-appstream-rpms        1.3 M
 bind-license                                 noarch        32:9.18.33-10.el10_1.2                 rhel-10-for-x86_64-appstream-rpms         13 k
 bind-utils                                   x86_64        32:9.18.33-10.el10_1.2                 rhel-10-for-x86_64-appstream-rpms        227 k
 binutils                                     x86_64        2.41-58.el10_1.2                       rhel-10-for-x86_64-baseos-rpms           6.4 M
 binutils-gold                                x86_64        2.41-58.el10_1.2                       rhel-10-for-x86_64-baseos-rpms           797 k
 brcmfmac-firmware                            noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           9.6 M
 ca-certificates                              noarch        2025.2.80_v9.0.305-102.el10_1          rhel-10-for-x86_64-baseos-rpms           1.1 M
 cirrus-audio-firmware                        noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           2.3 M
 cmake-filesystem                             x86_64        3.30.5-3.el10_0                        rhel-10-for-x86_64-appstream-rpms         24 k
 device-mapper-multipath-libs                 x86_64        0.9.9-12.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           305 k
 expat                                        x86_64        2.7.1-1.el10_1.3                       rhel-10-for-x86_64-baseos-rpms           119 k
 fprintd                                      x86_64        1.94.5-1.el10_0                        rhel-10-for-x86_64-appstream-rpms        187 k
 fprintd-pam                                  x86_64        1.94.5-1.el10_0                        rhel-10-for-x86_64-appstream-rpms         23 k
 glib2                                        x86_64        2.80.4-10.el10_1.12                    rhel-10-for-x86_64-baseos-rpms           3.1 M
 glibc                                        x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           2.1 M
 glibc-common                                 x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           326 k
 glibc-devel                                  x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-appstream-rpms        588 k
 glibc-gconv-extra                            x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           1.7 M
 glibc-langpack-en                            x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           671 k
 gnupg2                                       x86_64        2.4.5-3.el10_1                         rhel-10-for-x86_64-baseos-rpms           2.7 M
 gnupg2-smime                                 x86_64        2.4.5-3.el10_1                         rhel-10-for-x86_64-appstream-rpms        266 k
 intel-audio-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           3.3 M
 intel-gpu-firmware                           noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-appstream-rpms        8.9 M
 iwlwifi-dvm-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           1.9 M
 iwlwifi-mvm-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            68 M
 kernel-headers                               x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-appstream-rpms        3.2 M
 kernel-modules-extra-matched                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.4 M
 kernel-tools                                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.9 M
 kernel-tools-libs                            x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.4 M
 kpartx                                       x86_64        0.9.9-12.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            52 k
 libbrotli                                    x86_64        1.1.0-7.el10_1                         rhel-10-for-x86_64-baseos-rpms           344 k
 libdnf-plugin-subscription-manager           x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms            41 k
 libfprint                                    x86_64        1.94.9-1.el10_0                        rhel-10-for-x86_64-appstream-rpms        344 k
 libipa_hbac                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            34 k
 libnftnl                                     x86_64        1.2.8-4.el10_1                         rhel-10-for-x86_64-baseos-rpms            85 k
 libpng                                       x86_64        2:1.6.40-8.el10_1.1                    rhel-10-for-x86_64-baseos-rpms           119 k
 librepo                                      x86_64        1.18.0-6.el10_1                        rhel-10-for-x86_64-baseos-rpms            95 k
 libssh                                       x86_64        0.11.1-5.el10_1                        rhel-10-for-x86_64-baseos-rpms           233 k
 libssh-config                                noarch        0.11.1-5.el10_1                        rhel-10-for-x86_64-baseos-rpms           8.6 k
 libsss_certmap                               x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            81 k
 libsss_idmap                                 x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            41 k
 libsss_nss_idmap                             x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            44 k
 libsss_sudo                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            33 k
 libtpms                                      x86_64        0.9.6-11.el10_0                        rhel-10-for-x86_64-appstream-rpms        185 k
 libuv                                        x86_64        1:1.51.0-1.el10_0                      rhel-10-for-x86_64-appstream-rpms        262 k
 libvirt                                      x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         19 k
 libvirt-client                               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        449 k
 libvirt-client-qemu                          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         43 k
 libvirt-daemon                               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        209 k
 libvirt-daemon-common                        x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        145 k
 libvirt-daemon-config-network                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         24 k
 libvirt-daemon-config-nwfilter               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         37 k
 libvirt-daemon-driver-interface              x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        215 k
 libvirt-daemon-driver-network                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        268 k
 libvirt-daemon-driver-nodedev                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        238 k
 libvirt-daemon-driver-nwfilter               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        251 k
 libvirt-daemon-driver-qemu                   x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        1.0 M
 libvirt-daemon-driver-secret                 x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        212 k
 libvirt-daemon-driver-storage                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         18 k
 libvirt-daemon-driver-storage-core           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        268 k
 libvirt-daemon-driver-storage-disk           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         33 k
 libvirt-daemon-driver-storage-iscsi          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         30 k
 libvirt-daemon-driver-storage-logical        x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         34 k
 libvirt-daemon-driver-storage-mpath          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         28 k
 libvirt-daemon-driver-storage-rbd            x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         39 k
 libvirt-daemon-driver-storage-scsi           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         30 k
 libvirt-daemon-lock                          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         60 k
 libvirt-daemon-log                           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         64 k
 libvirt-daemon-plugin-lockd                  x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         34 k
 libvirt-daemon-proxy                         x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        207 k
 libvirt-libs                                 x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        5.2 M
 linux-firmware                               noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            54 M
 linux-firmware-whence                        noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           112 k
 man-pages                                    noarch        6.06-12.el10_1                         rhel-10-for-x86_64-baseos-rpms           3.7 M
 mesa-dri-drivers                             x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms         11 M
 mesa-filesystem                              x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms         13 k
 mesa-libEGL                                  x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms        131 k
 mesa-libGL                                   x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms        160 k
 mesa-libgbm                                  x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms         19 k
 microcode_ctl                                noarch        4:20250812-1.20251111.1.el10_1         rhel-10-for-x86_64-baseos-rpms            14 M
 mt7xxx-firmware                              noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            20 M
 nftables                                     x86_64        1:1.1.1-6.el10_1                       rhel-10-for-x86_64-baseos-rpms           437 k
 nvidia-gpu-firmware                          noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-appstream-rpms         99 M
 nxpwireless-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           980 k
 openssh                                      x86_64        9.9p1-12.el10_1                        rhel-10-for-x86_64-baseos-rpms           351 k
 openssh-clients                              x86_64        9.9p1-12.el10_1                        rhel-10-for-x86_64-baseos-rpms           761 k
 openssh-server                               x86_64        9.9p1-12.el10_1                        rhel-10-for-x86_64-baseos-rpms           539 k
 openssl                                      x86_64        1:3.5.1-7.el10_1                       rhel-10-for-x86_64-baseos-rpms           1.3 M
 openssl-devel                                x86_64        1:3.5.1-7.el10_1                       rhel-10-for-x86_64-appstream-rpms        4.2 M
 openssl-libs                                 x86_64        1:3.5.1-7.el10_1                       rhel-10-for-x86_64-baseos-rpms           2.3 M
 passt                                        x86_64        0^20250512.g8ec1341-4.el10_1           rhel-10-for-x86_64-appstream-rpms        265 k
 passt-selinux                                noarch        0^20250512.g8ec1341-4.el10_1           rhel-10-for-x86_64-appstream-rpms         28 k
 python-unversioned-command                   noarch        3.12.12-1.el10_1                       rhel-10-for-x86_64-appstream-rpms         11 k
 python3                                      x86_64        3.12.12-1.el10_1                       rhel-10-for-x86_64-baseos-rpms            28 k
 python3-cloud-what                           x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms            70 k
 python3-librepo                              x86_64        1.18.0-6.el10_1                        rhel-10-for-x86_64-baseos-rpms            51 k
 python3-libs                                 x86_64        3.12.12-1.el10_1                       rhel-10-for-x86_64-baseos-rpms           9.4 M
 python3-nftables                             x86_64        1:1.1.1-6.el10_1                       rhel-10-for-x86_64-baseos-rpms            22 k
 python3-perf                                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-appstream-rpms        2.7 M
 python3-subscription-manager-rhsm            x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms           181 k
 python3-urllib3                              noarch        1.26.19-2.el10_1.1                     rhel-10-for-x86_64-baseos-rpms           291 k
 realmd                                       x86_64        0.17.1-13.el10_1                       rhel-10-for-x86_64-baseos-rpms           251 k
 realtek-firmware                             noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           5.8 M
 redhat-release                               x86_64        10.1-18.el10                           rhel-10-for-x86_64-baseos-rpms            61 k
 redhat-release-eula                          x86_64        10.1-18.el10                           rhel-10-for-x86_64-baseos-rpms            15 k
 sos                                          noarch        4.10.1-2.el10                          rhel-10-for-x86_64-baseos-rpms           1.4 M
 sssd                                         x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            25 k
 sssd-ad                                      x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           195 k
 sssd-client                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           153 k
 sssd-common                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           1.5 M
 sssd-common-pac                              x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            89 k
 sssd-ipa                                     x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           274 k
 sssd-kcm                                     x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           103 k
 sssd-krb5                                    x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            62 k
 sssd-krb5-common                             x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            93 k
 sssd-ldap                                    x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           132 k
 sssd-nfs-idmap                               x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            36 k
 sssd-proxy                                   x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            70 k
 subscription-manager                         x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms           958 k
 tar                                          x86_64        2:1.35-9.el10_1                        rhel-10-for-x86_64-baseos-rpms           866 k
 tiwilink-firmware                            noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           4.7 M
 tuned                                        noarch        2.26.0-1.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           560 k
 tzdata                                       noarch        2025c-1.el10                           rhel-10-for-x86_64-baseos-rpms           904 k
 unbound-anchor                               x86_64        1.20.0-15.el10_1                       rhel-10-for-x86_64-appstream-rpms         35 k
 unbound-libs                                 x86_64        1.20.0-15.el10_1                       rhel-10-for-x86_64-appstream-rpms        547 k
 vim-common                                   x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-appstream-rpms        7.7 M
 vim-data                                     noarch        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-baseos-rpms            17 k
 vim-enhanced                                 x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-appstream-rpms        1.9 M
 vim-filesystem                               noarch        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-baseos-rpms            16 k
 vim-minimal                                  x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-baseos-rpms           799 k
 which                                        x86_64        2.21-44.el10_0                         rhel-10-for-x86_64-baseos-rpms            42 k
 xxd                                          x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-appstream-rpms         31 k
Installing dependencies:
 kernel-core                                  x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms            18 M
 kernel-modules                               x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms            41 M
 kernel-modules-core                          x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms            30 M
 kernel-modules-extra                         x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           2.8 M
Installing weak dependencies:
 kernel-devel                                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-appstream-rpms         23 M

Transaction Summary
==================================================================================================================================================
Install    6 Packages
Upgrade  139 Packages

Total download size: 580 M
Is this ok [y/N]: y
Downloading Packages:
(1/145): kernel-6.12.0-124.29.1.el10_1.x86_64.rpm                                                                 889 kB/s | 1.4 MB     00:01    
(2/145): kernel-core-6.12.0-124.29.1.el10_1.x86_64.rpm                                                            3.1 MB/s |  18 MB     00:05    
(3/145): kernel-modules-extra-6.12.0-124.29.1.el10_1.x86_64.rpm                                                   3.8 MB/s | 2.8 MB     00:00    
(4/145): kernel-modules-6.12.0-124.29.1.el10_1.x86_64.rpm                                                         4.7 MB/s |  41 MB     00:08    
(5/145): which-2.21-44.el10_0.x86_64.rpm                                                                          148 kB/s |  42 kB     00:00    
(6/145): at-3.2.5-14.el10_1.x86_64.rpm                                                                            245 kB/s |  66 kB     00:00    
(7/145): libdnf-plugin-subscription-manager-1.30.10.1-1.el10_1.x86_64.rpm                                         149 kB/s |  41 kB     00:00    
(8/145): libipa_hbac-2.11.1-2.el10_1.1.x86_64.rpm                                                                 133 kB/s |  34 kB     00:00    
(9/145): kernel-modules-core-6.12.0-124.29.1.el10_1.x86_64.rpm                                                    3.5 MB/s |  30 MB     00:08    
(10/145): libnftnl-1.2.8-4.el10_1.x86_64.rpm                                                                      263 kB/s |  85 kB     00:00    
(11/145): libsss_certmap-2.11.1-2.el10_1.1.x86_64.rpm                                                             322 kB/s |  81 kB     00:00    
(12/145): libsss_idmap-2.11.1-2.el10_1.1.x86_64.rpm                                                               167 kB/s |  41 kB     00:00    
(13/145): kernel-devel-6.12.0-124.29.1.el10_1.x86_64.rpm                                                          6.2 MB/s |  23 MB     00:03    
(14/145): libsss_sudo-2.11.1-2.el10_1.1.x86_64.rpm                                                                148 kB/s |  33 kB     00:00    
(15/145): libsss_nss_idmap-2.11.1-2.el10_1.1.x86_64.rpm                                                           175 kB/s |  44 kB     00:00    
(16/145): nftables-1.1.1-6.el10_1.x86_64.rpm                                                                      1.7 MB/s | 437 kB     00:00    
(17/145): python3-nftables-1.1.1-6.el10_1.x86_64.rpm                                                               86 kB/s |  22 kB     00:00    
(18/145): python3-cloud-what-1.30.10.1-1.el10_1.x86_64.rpm                                                        256 kB/s |  70 kB     00:00    
(19/145): python3-subscription-manager-rhsm-1.30.10.1-1.el10_1.x86_64.rpm                                         650 kB/s | 181 kB     00:00    
(20/145): sssd-2.11.1-2.el10_1.1.x86_64.rpm                                                                       100 kB/s |  25 kB     00:00    
(21/145): realmd-0.17.1-13.el10_1.x86_64.rpm                                                                      866 kB/s | 251 kB     00:00    
(22/145): sssd-ad-2.11.1-2.el10_1.1.x86_64.rpm                                                                    728 kB/s | 195 kB     00:00    
(23/145): sssd-client-2.11.1-2.el10_1.1.x86_64.rpm                                                                593 kB/s | 153 kB     00:00    
(24/145): sssd-common-pac-2.11.1-2.el10_1.1.x86_64.rpm                                                            313 kB/s |  89 kB     00:00    
(25/145): sssd-common-2.11.1-2.el10_1.1.x86_64.rpm                                                                3.1 MB/s | 1.5 MB     00:00    
(26/145): sssd-ipa-2.11.1-2.el10_1.1.x86_64.rpm                                                                   1.0 MB/s | 274 kB     00:00    
(27/145): sssd-kcm-2.11.1-2.el10_1.1.x86_64.rpm                                                                   369 kB/s | 103 kB     00:00    
(28/145): sssd-krb5-2.11.1-2.el10_1.1.x86_64.rpm                                                                  251 kB/s |  62 kB     00:00    
(29/145): sssd-krb5-common-2.11.1-2.el10_1.1.x86_64.rpm                                                           368 kB/s |  93 kB     00:00    
(30/145): sssd-nfs-idmap-2.11.1-2.el10_1.1.x86_64.rpm                                                             142 kB/s |  36 kB     00:00    
(31/145): sssd-proxy-2.11.1-2.el10_1.1.x86_64.rpm                                                                 286 kB/s |  70 kB     00:00    
(32/145): sssd-ldap-2.11.1-2.el10_1.1.x86_64.rpm                                                                  452 kB/s | 132 kB     00:00    
(33/145): tuned-2.26.0-1.el10_1.1.noarch.rpm                                                                      1.6 MB/s | 560 kB     00:00    
(34/145): vim-data-9.1.083-6.el10_1.noarch.rpm                                                                     52 kB/s |  17 kB     00:00    
(35/145): subscription-manager-1.30.10.1-1.el10_1.x86_64.rpm                                                      2.3 MB/s | 958 kB     00:00    
(36/145): vim-minimal-9.1.083-6.el10_1.x86_64.rpm                                                                 2.2 MB/s | 799 kB     00:00    
(37/145): vim-filesystem-9.1.083-6.el10_1.noarch.rpm                                                               38 kB/s |  16 kB     00:00    
(38/145): ca-certificates-2025.2.80_v9.0.305-102.el10_1.noarch.rpm                                                2.5 MB/s | 1.1 MB     00:00    
(39/145): redhat-release-10.1-18.el10.x86_64.rpm                                                                  275 kB/s |  61 kB     00:00    
(40/145): expat-2.7.1-1.el10_1.3.x86_64.rpm                                                                       322 kB/s | 119 kB     00:00    
(41/145): redhat-release-eula-10.1-18.el10.x86_64.rpm                                                              68 kB/s |  15 kB     00:00    
(42/145): openssh-9.9p1-12.el10_1.x86_64.rpm                                                                      1.2 MB/s | 351 kB     00:00    
(43/145): openssh-server-9.9p1-12.el10_1.x86_64.rpm                                                               1.7 MB/s | 539 kB     00:00    
(44/145): openssh-clients-9.9p1-12.el10_1.x86_64.rpm                                                              2.3 MB/s | 761 kB     00:00    
(45/145): libssh-0.11.1-5.el10_1.x86_64.rpm                                                                       977 kB/s | 233 kB     00:00    
(46/145): libssh-config-0.11.1-5.el10_1.noarch.rpm                                                                 35 kB/s | 8.6 kB     00:00    
(47/145): tzdata-2025c-1.el10.noarch.rpm                                                                          2.2 MB/s | 904 kB     00:00    
(48/145): NetworkManager-tui-1.54.0-2.el10_1.x86_64.rpm                                                           677 kB/s | 233 kB     00:00    
(49/145): NetworkManager-1.54.0-2.el10_1.x86_64.rpm                                                               3.8 MB/s | 2.2 MB     00:00    
(50/145): NetworkManager-libnm-1.54.0-2.el10_1.x86_64.rpm                                                         2.8 MB/s | 1.9 MB     00:00    
(51/145): amd-ucode-firmware-20251111-19.1.el10_1.noarch.rpm                                                      1.4 MB/s | 466 kB     00:00    
(52/145): binutils-gold-2.41-58.el10_1.2.x86_64.rpm                                                               1.9 MB/s | 797 kB     00:00    
(53/145): binutils-2.41-58.el10_1.2.x86_64.rpm                                                                    4.6 MB/s | 6.4 MB     00:01    
(54/145): cirrus-audio-firmware-20251111-19.1.el10_1.noarch.rpm                                                   3.0 MB/s | 2.3 MB     00:00    
(55/145): brcmfmac-firmware-20251111-19.1.el10_1.noarch.rpm                                                       4.8 MB/s | 9.6 MB     00:01    
(56/145): iwlwifi-dvm-firmware-20251111-19.1.el10_1.noarch.rpm                                                    2.5 MB/s | 1.9 MB     00:00    
(57/145): intel-audio-firmware-20251111-19.1.el10_1.noarch.rpm                                                    2.6 MB/s | 3.3 MB     00:01    
(58/145): librepo-1.18.0-6.el10_1.x86_64.rpm                                                                      408 kB/s |  95 kB     00:00    
(59/145): atheros-firmware-20251111-19.1.el10_1.noarch.rpm                                                        6.6 MB/s |  41 MB     00:06    
(60/145): linux-firmware-whence-20251111-19.1.el10_1.noarch.rpm                                                   325 kB/s | 112 kB     00:00    
(61/145): man-pages-6.06-12.el10_1.noarch.rpm                                                                     3.4 MB/s | 3.7 MB     00:01    
(62/145): mt7xxx-firmware-20251111-19.1.el10_1.noarch.rpm                                                         5.1 MB/s |  20 MB     00:03    
(63/145): nxpwireless-firmware-20251111-19.1.el10_1.noarch.rpm                                                    2.3 MB/s | 980 kB     00:00    
(64/145): python3-librepo-1.18.0-6.el10_1.x86_64.rpm                                                              209 kB/s |  51 kB     00:00    
(65/145): iwlwifi-mvm-firmware-20251111-19.1.el10_1.noarch.rpm                                                    7.0 MB/s |  68 MB     00:09    
(66/145): tiwilink-firmware-20251111-19.1.el10_1.noarch.rpm                                                       4.9 MB/s | 4.7 MB     00:00    
(67/145): python3-3.12.12-1.el10_1.x86_64.rpm                                                                     128 kB/s |  28 kB     00:00    
(68/145): realtek-firmware-20251111-19.1.el10_1.noarch.rpm                                                        2.7 MB/s | 5.8 MB     00:02    
(69/145): tar-1.35-9.el10_1.x86_64.rpm                                                                            1.9 MB/s | 866 kB     00:00    
(70/145): sos-4.10.1-2.el10.noarch.rpm                                                                            1.8 MB/s | 1.4 MB     00:00    
(71/145): libpng-1.6.40-8.el10_1.1.x86_64.rpm                                                                     437 kB/s | 119 kB     00:00    
(72/145): python3-libs-3.12.12-1.el10_1.x86_64.rpm                                                                5.4 MB/s | 9.4 MB     00:01    
(73/145): device-mapper-multipath-libs-0.9.9-12.el10_1.1.x86_64.rpm                                               1.3 MB/s | 305 kB     00:00    
(74/145): kpartx-0.9.9-12.el10_1.1.x86_64.rpm                                                                     249 kB/s |  52 kB     00:00    
(75/145): linux-firmware-20251111-19.1.el10_1.noarch.rpm                                                          4.3 MB/s |  54 MB     00:12    
(76/145): libbrotli-1.1.0-7.el10_1.x86_64.rpm                                                                     1.2 MB/s | 344 kB     00:00    
(77/145): gnupg2-2.4.5-3.el10_1.x86_64.rpm                                                                        3.8 MB/s | 2.7 MB     00:00    
(78/145): python3-urllib3-1.26.19-2.el10_1.1.noarch.rpm                                                           854 kB/s | 291 kB     00:00    
(79/145): kernel-modules-extra-matched-6.12.0-124.29.1.el10_1.x86_64.rpm                                          1.9 MB/s | 1.4 MB     00:00    
(80/145): glib2-2.80.4-10.el10_1.12.x86_64.rpm                                                                    2.3 MB/s | 3.1 MB     00:01    
(81/145): microcode_ctl-20250812-1.20251111.1.el10_1.noarch.rpm                                                   6.3 MB/s |  14 MB     00:02    
(82/145): kernel-tools-6.12.0-124.29.1.el10_1.x86_64.rpm                                                          4.7 MB/s | 1.9 MB     00:00    
(83/145): kernel-tools-libs-6.12.0-124.29.1.el10_1.x86_64.rpm                                                     2.9 MB/s | 1.4 MB     00:00    
(84/145): glibc-2.39-58.el10_1.7.x86_64.rpm                                                                       5.3 MB/s | 2.1 MB     00:00    
(85/145): glibc-common-2.39-58.el10_1.7.x86_64.rpm                                                                707 kB/s | 326 kB     00:00    
(86/145): glibc-gconv-extra-2.39-58.el10_1.7.x86_64.rpm                                                           3.8 MB/s | 1.7 MB     00:00    
(87/145): glibc-langpack-en-2.39-58.el10_1.7.x86_64.rpm                                                           1.8 MB/s | 671 kB     00:00    
(88/145): openssl-3.5.1-7.el10_1.x86_64.rpm                                                                       2.3 MB/s | 1.3 MB     00:00    
(89/145): cmake-filesystem-3.30.5-3.el10_0.x86_64.rpm                                                              70 kB/s |  24 kB     00:00    
(90/145): openssl-libs-3.5.1-7.el10_1.x86_64.rpm                                                                  3.5 MB/s | 2.3 MB     00:00    
(91/145): fprintd-1.94.5-1.el10_0.x86_64.rpm                                                                      791 kB/s | 187 kB     00:00    
(92/145): fprintd-pam-1.94.5-1.el10_0.x86_64.rpm                                                                   91 kB/s |  23 kB     00:00    
(93/145): libtpms-0.9.6-11.el10_0.x86_64.rpm                                                                      742 kB/s | 185 kB     00:00    
(94/145): libfprint-1.94.9-1.el10_0.x86_64.rpm                                                                    1.1 MB/s | 344 kB     00:00    
(95/145): libuv-1.51.0-1.el10_0.x86_64.rpm                                                                        1.0 MB/s | 262 kB     00:00    
(96/145): mesa-libEGL-25.0.7-6.el10_1.x86_64.rpm                                                                  477 kB/s | 131 kB     00:00    
(97/145): mesa-filesystem-25.0.7-6.el10_1.x86_64.rpm                                                               41 kB/s |  13 kB     00:00    
(98/145): mesa-libGL-25.0.7-6.el10_1.x86_64.rpm                                                                   639 kB/s | 160 kB     00:00    
(99/145): mesa-libgbm-25.0.7-6.el10_1.x86_64.rpm                                                                   73 kB/s |  19 kB     00:00    
(100/145): passt-selinux-0^20250512.g8ec1341-4.el10_1.noarch.rpm                                                   79 kB/s |  28 kB     00:00    
(101/145): passt-0^20250512.g8ec1341-4.el10_1.x86_64.rpm                                                          658 kB/s | 265 kB     00:00    
(102/145): vim-enhanced-9.1.083-6.el10_1.x86_64.rpm                                                               3.9 MB/s | 1.9 MB     00:00    
(103/145): mesa-dri-drivers-25.0.7-6.el10_1.x86_64.rpm                                                            6.7 MB/s |  11 MB     00:01    
(104/145): xxd-9.1.083-6.el10_1.x86_64.rpm                                                                        116 kB/s |  31 kB     00:00    
(105/145): bind-license-9.18.33-10.el10_1.2.noarch.rpm                                                             51 kB/s |  13 kB     00:00    
(106/145): bind-libs-9.18.33-10.el10_1.2.x86_64.rpm                                                               3.6 MB/s | 1.3 MB     00:00    
(107/145): bind-utils-9.18.33-10.el10_1.2.x86_64.rpm                                                              787 kB/s | 227 kB     00:00    
(108/145): vim-common-9.1.083-6.el10_1.x86_64.rpm                                                                 4.6 MB/s | 7.7 MB     00:01    
(109/145): libvirt-11.5.0-4.2.el10_1.x86_64.rpm                                                                    53 kB/s |  19 kB     00:00    
(110/145): intel-gpu-firmware-20251111-19.1.el10_1.noarch.rpm                                                     8.9 MB/s | 8.9 MB     00:00    
(111/145): libvirt-client-11.5.0-4.2.el10_1.x86_64.rpm                                                            1.4 MB/s | 449 kB     00:00    
(112/145): libvirt-client-qemu-11.5.0-4.2.el10_1.x86_64.rpm                                                       187 kB/s |  43 kB     00:00    
(113/145): libvirt-daemon-11.5.0-4.2.el10_1.x86_64.rpm                                                            814 kB/s | 209 kB     00:00    
(114/145): libvirt-daemon-common-11.5.0-4.2.el10_1.x86_64.rpm                                                     627 kB/s | 145 kB     00:00    
(115/145): libvirt-daemon-config-network-11.5.0-4.2.el10_1.x86_64.rpm                                             115 kB/s |  24 kB     00:00    
(116/145): libvirt-daemon-config-nwfilter-11.5.0-4.2.el10_1.x86_64.rpm                                            177 kB/s |  37 kB     00:00    
(117/145): libvirt-daemon-driver-interface-11.5.0-4.2.el10_1.x86_64.rpm                                           807 kB/s | 215 kB     00:00    
(118/145): libvirt-daemon-driver-network-11.5.0-4.2.el10_1.x86_64.rpm                                             963 kB/s | 268 kB     00:00    
(119/145): libvirt-daemon-driver-nodedev-11.5.0-4.2.el10_1.x86_64.rpm                                             810 kB/s | 238 kB     00:00    
(120/145): libvirt-daemon-driver-nwfilter-11.5.0-4.2.el10_1.x86_64.rpm                                            945 kB/s | 251 kB     00:00    
(121/145): amd-gpu-firmware-20251111-19.1.el10_1.noarch.rpm                                                        11 MB/s |  28 MB     00:02    
(122/145): libvirt-daemon-driver-secret-11.5.0-4.2.el10_1.x86_64.rpm                                              888 kB/s | 212 kB     00:00    
(123/145): libvirt-daemon-driver-qemu-11.5.0-4.2.el10_1.x86_64.rpm                                                2.3 MB/s | 1.0 MB     00:00    
(124/145): libvirt-daemon-driver-storage-core-11.5.0-4.2.el10_1.x86_64.rpm                                        1.0 MB/s | 268 kB     00:00    
(125/145): libvirt-daemon-driver-storage-disk-11.5.0-4.2.el10_1.x86_64.rpm                                        136 kB/s |  33 kB     00:00    
(126/145): libvirt-daemon-driver-storage-11.5.0-4.2.el10_1.x86_64.rpm                                              47 kB/s |  18 kB     00:00    
(127/145): libvirt-daemon-driver-storage-logical-11.5.0-4.2.el10_1.x86_64.rpm                                     152 kB/s |  34 kB     00:00    
(128/145): libvirt-daemon-driver-storage-iscsi-11.5.0-4.2.el10_1.x86_64.rpm                                       106 kB/s |  30 kB     00:00    
(129/145): libvirt-daemon-driver-storage-mpath-11.5.0-4.2.el10_1.x86_64.rpm                                       115 kB/s |  28 kB     00:00    
(130/145): libvirt-daemon-driver-storage-scsi-11.5.0-4.2.el10_1.x86_64.rpm                                        126 kB/s |  30 kB     00:00    
(131/145): libvirt-daemon-lock-11.5.0-4.2.el10_1.x86_64.rpm                                                       244 kB/s |  60 kB     00:00    
(132/145): libvirt-daemon-driver-storage-rbd-11.5.0-4.2.el10_1.x86_64.rpm                                         103 kB/s |  39 kB     00:00    
(133/145): libvirt-daemon-plugin-lockd-11.5.0-4.2.el10_1.x86_64.rpm                                               145 kB/s |  34 kB     00:00    
(134/145): libvirt-daemon-log-11.5.0-4.2.el10_1.x86_64.rpm                                                        165 kB/s |  64 kB     00:00    
(135/145): libvirt-daemon-proxy-11.5.0-4.2.el10_1.x86_64.rpm                                                      640 kB/s | 207 kB     00:00    
(136/145): unbound-anchor-1.20.0-15.el10_1.x86_64.rpm                                                             121 kB/s |  35 kB     00:00    
(137/145): libvirt-libs-11.5.0-4.2.el10_1.x86_64.rpm                                                              7.3 MB/s | 5.2 MB     00:00    
(138/145): unbound-libs-1.20.0-15.el10_1.x86_64.rpm                                                               1.5 MB/s | 547 kB     00:00    
(139/145): python-unversioned-command-3.12.12-1.el10_1.noarch.rpm                                                  45 kB/s |  11 kB     00:00    
(140/145): gnupg2-smime-2.4.5-3.el10_1.x86_64.rpm                                                                 876 kB/s | 266 kB     00:00    
(141/145): kernel-headers-6.12.0-124.29.1.el10_1.x86_64.rpm                                                       5.2 MB/s | 3.2 MB     00:00    
(142/145): glibc-devel-2.39-58.el10_1.7.x86_64.rpm                                                                1.7 MB/s | 588 kB     00:00    
(143/145): python3-perf-6.12.0-124.29.1.el10_1.x86_64.rpm                                                         3.0 MB/s | 2.7 MB     00:00    
(144/145): openssl-devel-3.5.1-7.el10_1.x86_64.rpm                                                                7.0 MB/s | 4.2 MB     00:00    
(145/145): nvidia-gpu-firmware-20251111-19.1.el10_1.noarch.rpm                                                    9.1 MB/s |  99 MB     00:10    
--------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                              11 MB/s | 580 MB     00:50     
Red Hat Enterprise Linux 10 for x86_64 - BaseOS (RPMs)                                                            3.2 MB/s | 3.7 kB     00:00    
Importing GPG key 0xFD431D51:
 Userid     : "Red Hat, Inc. (release key 2) <security@redhat.com>"
 Fingerprint: 567E 347A D004 4ADE 55BA 8A5F 199E 2F91 FD43 1D51
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Is this ok [y/N]: y
Key imported successfully
Importing GPG key 0x5A6340B3:
 Userid     : "Red Hat, Inc. (auxiliary key 3) <security@redhat.com>"
 Fingerprint: 7E46 2425 8C40 6535 D56D 6F13 5054 E4A4 5A63 40B3
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Is this ok [y/N]: y
Key imported successfully
Import of key(s) didn't help, wrong key(s)?
Red Hat Enterprise Linux 10 for x86_64 - AppStream (RPMs)                                                         3.6 MB/s | 3.7 kB     00:00    
GPG key at file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release (0xFD431D51) is already installed
GPG key at file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release (0x5A6340B3) is already installed
Public key for kernel-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-core-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-core-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-modules-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-modules-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-modules-core-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-modules-core-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-modules-extra-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-modules-extra-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
The GPG keys listed for the "Red Hat Enterprise Linux 10 for x86_64 - AppStream (RPMs)" repository are already installed but they are not correct for this package.
Check that the correct key URLs are configured for this repository.. Failing package is: kernel-devel-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for gnupg2-2.4.5-3.el10_1.x86_64.rpm is not installed. Failing package is: gnupg2-2.4.5-3.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for glib2-2.80.4-10.el10_1.12.x86_64.rpm is not installed. Failing package is: glib2-2.80.4-10.el10_1.12.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for python3-urllib3-1.26.19-2.el10_1.1.noarch.rpm is not installed. Failing package is: python3-urllib3-1.26.19-2.el10_1.1.noarch
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-modules-extra-matched-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-modules-extra-matched-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-tools-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-tools-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-tools-libs-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-tools-libs-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for glibc-2.39-58.el10_1.7.x86_64.rpm is not installed. Failing package is: glibc-2.39-58.el10_1.7.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for glibc-common-2.39-58.el10_1.7.x86_64.rpm is not installed. Failing package is: glibc-common-2.39-58.el10_1.7.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for glibc-gconv-extra-2.39-58.el10_1.7.x86_64.rpm is not installed. Failing package is: glibc-gconv-extra-2.39-58.el10_1.7.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for glibc-langpack-en-2.39-58.el10_1.7.x86_64.rpm is not installed. Failing package is: glibc-langpack-en-2.39-58.el10_1.7.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for openssl-3.5.1-7.el10_1.x86_64.rpm is not installed. Failing package is: openssl-1:3.5.1-7.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for openssl-libs-3.5.1-7.el10_1.x86_64.rpm is not installed. Failing package is: openssl-libs-1:3.5.1-7.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for gnupg2-smime-2.4.5-3.el10_1.x86_64.rpm is not installed. Failing package is: gnupg2-smime-2.4.5-3.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for kernel-headers-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: kernel-headers-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for python3-perf-6.12.0-124.29.1.el10_1.x86_64.rpm is not installed. Failing package is: python3-perf-6.12.0-124.29.1.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for glibc-devel-2.39-58.el10_1.7.x86_64.rpm is not installed. Failing package is: glibc-devel-2.39-58.el10_1.7.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Public key for openssl-devel-3.5.1-7.el10_1.x86_64.rpm is not installed. Failing package is: openssl-devel-1:3.5.1-7.el10_1.x86_64
 GPG Keys are configured as: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
The downloaded packages were saved in cache until the next successful transaction.
You can remove cached packages by executing 'dnf clean packages'.
Error: GPG check FAILED
```

The fix is pretty simple, but took a while to dig out:
```
# dnf whatprovides "*/RPM-GPG-KEY-redhat-release"
Updating Subscription Management repositories.
Red Hat Enterprise Linux 10 for x86_64 - BaseOS (RPMs)                                                            8.3 MB/s |  46 MB     00:05    
Red Hat Enterprise Linux 10 for x86_64 - AppStream (RPMs)                                                         7.0 MB/s |  27 MB     00:03    
Last metadata expiration check: 0:00:01 ago on Wed 28 Jan 2026 04:29:11 PM PST.
redhat-release-10.0-30.el10.x86_64 : Red Hat Enterprise Linux release file
Repo        : rhel-10-for-x86_64-baseos-rpms
Matched from:
Filename    : /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
```

So the package which provide the GPG keys is redhat-release, so lets update that package:
```
# dnf install redhat-release
Updating Subscription Management repositories.
Last metadata expiration check: 0:01:11 ago on Wed 28 Jan 2026 04:29:11 PM PST.
Package redhat-release-10.1-16.el10.x86_64 is already installed.
Dependencies resolved.
==================================================================================================================================================
 Package                          Architecture             Version                         Repository                                        Size
==================================================================================================================================================
Upgrading:
 redhat-release                   x86_64                   10.1-18.el10                    rhel-10-for-x86_64-baseos-rpms                    61 k

Transaction Summary
==================================================================================================================================================
Upgrade  1 Package

Total size: 61 k
Is this ok [y/N]: y
Downloading Packages:
[SKIPPED] redhat-release-10.1-18.el10.x86_64.rpm: Already downloaded                                                                             
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                          1/1 
  Upgrading        : redhat-release-10.1-18.el10.x86_64                                                                                       1/2 
  Cleanup          : redhat-release-10.1-16.el10.x86_64                                                                                       2/2 
  Running scriptlet: redhat-release-10.1-16.el10.x86_64                                                                                       2/2 
Failed to connect to user scope bus via machine transport: No medium found

Installed products updated.

Upgraded:
  redhat-release-10.1-18.el10.x86_64                                                                                                              

Complete!
```

Now try running ```# dnf update```:
```
# dnf update
Updating Subscription Management repositories.
Last metadata expiration check: 0:01:31 ago on Wed 28 Jan 2026 04:29:11 PM PST.
Dependencies resolved.
==================================================================================================================================================
 Package                                      Architecture  Version                                Repository                                Size
==================================================================================================================================================
Installing:
 kernel                                       x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.4 M
Upgrading:
 NetworkManager                               x86_64        1:1.54.0-2.el10_1                      rhel-10-for-x86_64-baseos-rpms           2.2 M
 NetworkManager-libnm                         x86_64        1:1.54.0-2.el10_1                      rhel-10-for-x86_64-baseos-rpms           1.9 M
 NetworkManager-tui                           x86_64        1:1.54.0-2.el10_1                      rhel-10-for-x86_64-baseos-rpms           233 k
 amd-gpu-firmware                             noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-appstream-rpms         28 M
 amd-ucode-firmware                           noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           466 k
 at                                           x86_64        3.2.5-14.el10_1                        rhel-10-for-x86_64-baseos-rpms            66 k
 atheros-firmware                             noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            41 M
 bind-libs                                    x86_64        32:9.18.33-10.el10_1.2                 rhel-10-for-x86_64-appstream-rpms        1.3 M
 bind-license                                 noarch        32:9.18.33-10.el10_1.2                 rhel-10-for-x86_64-appstream-rpms         13 k
 bind-utils                                   x86_64        32:9.18.33-10.el10_1.2                 rhel-10-for-x86_64-appstream-rpms        227 k
 binutils                                     x86_64        2.41-58.el10_1.2                       rhel-10-for-x86_64-baseos-rpms           6.4 M
 binutils-gold                                x86_64        2.41-58.el10_1.2                       rhel-10-for-x86_64-baseos-rpms           797 k
 brcmfmac-firmware                            noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           9.6 M
 ca-certificates                              noarch        2025.2.80_v9.0.305-102.el10_1          rhel-10-for-x86_64-baseos-rpms           1.1 M
 cirrus-audio-firmware                        noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           2.3 M
 cmake-filesystem                             x86_64        3.30.5-3.el10_0                        rhel-10-for-x86_64-appstream-rpms         24 k
 device-mapper-multipath-libs                 x86_64        0.9.9-12.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           305 k
 expat                                        x86_64        2.7.1-1.el10_1.3                       rhel-10-for-x86_64-baseos-rpms           119 k
 fprintd                                      x86_64        1.94.5-1.el10_0                        rhel-10-for-x86_64-appstream-rpms        187 k
 fprintd-pam                                  x86_64        1.94.5-1.el10_0                        rhel-10-for-x86_64-appstream-rpms         23 k
 glib2                                        x86_64        2.80.4-10.el10_1.12                    rhel-10-for-x86_64-baseos-rpms           3.1 M
 glibc                                        x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           2.1 M
 glibc-common                                 x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           326 k
 glibc-devel                                  x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-appstream-rpms        588 k
 glibc-gconv-extra                            x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           1.7 M
 glibc-langpack-en                            x86_64        2.39-58.el10_1.7                       rhel-10-for-x86_64-baseos-rpms           671 k
 gnupg2                                       x86_64        2.4.5-3.el10_1                         rhel-10-for-x86_64-baseos-rpms           2.7 M
 gnupg2-smime                                 x86_64        2.4.5-3.el10_1                         rhel-10-for-x86_64-appstream-rpms        266 k
 intel-audio-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           3.3 M
 intel-gpu-firmware                           noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-appstream-rpms        8.9 M
 iwlwifi-dvm-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           1.9 M
 iwlwifi-mvm-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            68 M
 kernel-headers                               x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-appstream-rpms        3.2 M
 kernel-modules-extra-matched                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.4 M
 kernel-tools                                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.9 M
 kernel-tools-libs                            x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           1.4 M
 kpartx                                       x86_64        0.9.9-12.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            52 k
 libbrotli                                    x86_64        1.1.0-7.el10_1                         rhel-10-for-x86_64-baseos-rpms           344 k
 libdnf-plugin-subscription-manager           x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms            41 k
 libfprint                                    x86_64        1.94.9-1.el10_0                        rhel-10-for-x86_64-appstream-rpms        344 k
 libipa_hbac                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            34 k
 libnftnl                                     x86_64        1.2.8-4.el10_1                         rhel-10-for-x86_64-baseos-rpms            85 k
 libpng                                       x86_64        2:1.6.40-8.el10_1.1                    rhel-10-for-x86_64-baseos-rpms           119 k
 librepo                                      x86_64        1.18.0-6.el10_1                        rhel-10-for-x86_64-baseos-rpms            95 k
 libssh                                       x86_64        0.11.1-5.el10_1                        rhel-10-for-x86_64-baseos-rpms           233 k
 libssh-config                                noarch        0.11.1-5.el10_1                        rhel-10-for-x86_64-baseos-rpms           8.6 k
 libsss_certmap                               x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            81 k
 libsss_idmap                                 x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            41 k
 libsss_nss_idmap                             x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            44 k
 libsss_sudo                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            33 k
 libtpms                                      x86_64        0.9.6-11.el10_0                        rhel-10-for-x86_64-appstream-rpms        185 k
 libuv                                        x86_64        1:1.51.0-1.el10_0                      rhel-10-for-x86_64-appstream-rpms        262 k
 libvirt                                      x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         19 k
 libvirt-client                               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        449 k
 libvirt-client-qemu                          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         43 k
 libvirt-daemon                               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        209 k
 libvirt-daemon-common                        x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        145 k
 libvirt-daemon-config-network                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         24 k
 libvirt-daemon-config-nwfilter               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         37 k
 libvirt-daemon-driver-interface              x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        215 k
 libvirt-daemon-driver-network                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        268 k
 libvirt-daemon-driver-nodedev                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        238 k
 libvirt-daemon-driver-nwfilter               x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        251 k
 libvirt-daemon-driver-qemu                   x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        1.0 M
 libvirt-daemon-driver-secret                 x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        212 k
 libvirt-daemon-driver-storage                x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         18 k
 libvirt-daemon-driver-storage-core           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        268 k
 libvirt-daemon-driver-storage-disk           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         33 k
 libvirt-daemon-driver-storage-iscsi          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         30 k
 libvirt-daemon-driver-storage-logical        x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         34 k
 libvirt-daemon-driver-storage-mpath          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         28 k
 libvirt-daemon-driver-storage-rbd            x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         39 k
 libvirt-daemon-driver-storage-scsi           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         30 k
 libvirt-daemon-lock                          x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         60 k
 libvirt-daemon-log                           x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         64 k
 libvirt-daemon-plugin-lockd                  x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms         34 k
 libvirt-daemon-proxy                         x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        207 k
 libvirt-libs                                 x86_64        11.5.0-4.2.el10_1                      rhel-10-for-x86_64-appstream-rpms        5.2 M
 linux-firmware                               noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            54 M
 linux-firmware-whence                        noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           112 k
 man-pages                                    noarch        6.06-12.el10_1                         rhel-10-for-x86_64-baseos-rpms           3.7 M
 mesa-dri-drivers                             x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms         11 M
 mesa-filesystem                              x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms         13 k
 mesa-libEGL                                  x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms        131 k
 mesa-libGL                                   x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms        160 k
 mesa-libgbm                                  x86_64        25.0.7-6.el10_1                        rhel-10-for-x86_64-appstream-rpms         19 k
 microcode_ctl                                noarch        4:20250812-1.20251111.1.el10_1         rhel-10-for-x86_64-baseos-rpms            14 M
 mt7xxx-firmware                              noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms            20 M
 nftables                                     x86_64        1:1.1.1-6.el10_1                       rhel-10-for-x86_64-baseos-rpms           437 k
 nvidia-gpu-firmware                          noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-appstream-rpms         99 M
 nxpwireless-firmware                         noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           980 k
 openssh                                      x86_64        9.9p1-12.el10_1                        rhel-10-for-x86_64-baseos-rpms           351 k
 openssh-clients                              x86_64        9.9p1-12.el10_1                        rhel-10-for-x86_64-baseos-rpms           761 k
 openssh-server                               x86_64        9.9p1-12.el10_1                        rhel-10-for-x86_64-baseos-rpms           539 k
 openssl                                      x86_64        1:3.5.1-7.el10_1                       rhel-10-for-x86_64-baseos-rpms           1.3 M
 openssl-devel                                x86_64        1:3.5.1-7.el10_1                       rhel-10-for-x86_64-appstream-rpms        4.2 M
 openssl-libs                                 x86_64        1:3.5.1-7.el10_1                       rhel-10-for-x86_64-baseos-rpms           2.3 M
 passt                                        x86_64        0^20250512.g8ec1341-4.el10_1           rhel-10-for-x86_64-appstream-rpms        265 k
 passt-selinux                                noarch        0^20250512.g8ec1341-4.el10_1           rhel-10-for-x86_64-appstream-rpms         28 k
 python-unversioned-command                   noarch        3.12.12-1.el10_1                       rhel-10-for-x86_64-appstream-rpms         11 k
 python3                                      x86_64        3.12.12-1.el10_1                       rhel-10-for-x86_64-baseos-rpms            28 k
 python3-cloud-what                           x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms            70 k
 python3-librepo                              x86_64        1.18.0-6.el10_1                        rhel-10-for-x86_64-baseos-rpms            51 k
 python3-libs                                 x86_64        3.12.12-1.el10_1                       rhel-10-for-x86_64-baseos-rpms           9.4 M
 python3-nftables                             x86_64        1:1.1.1-6.el10_1                       rhel-10-for-x86_64-baseos-rpms            22 k
 python3-perf                                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-appstream-rpms        2.7 M
 python3-subscription-manager-rhsm            x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms           181 k
 python3-urllib3                              noarch        1.26.19-2.el10_1.1                     rhel-10-for-x86_64-baseos-rpms           291 k
 realmd                                       x86_64        0.17.1-13.el10_1                       rhel-10-for-x86_64-baseos-rpms           251 k
 realtek-firmware                             noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           5.8 M
 redhat-release-eula                          x86_64        10.1-18.el10                           rhel-10-for-x86_64-baseos-rpms            15 k
 sos                                          noarch        4.10.1-2.el10                          rhel-10-for-x86_64-baseos-rpms           1.4 M
 sssd                                         x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            25 k
 sssd-ad                                      x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           195 k
 sssd-client                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           153 k
 sssd-common                                  x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           1.5 M
 sssd-common-pac                              x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            89 k
 sssd-ipa                                     x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           274 k
 sssd-kcm                                     x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           103 k
 sssd-krb5                                    x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            62 k
 sssd-krb5-common                             x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            93 k
 sssd-ldap                                    x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           132 k
 sssd-nfs-idmap                               x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            36 k
 sssd-proxy                                   x86_64        2.11.1-2.el10_1.1                      rhel-10-for-x86_64-baseos-rpms            70 k
 subscription-manager                         x86_64        1.30.10.1-1.el10_1                     rhel-10-for-x86_64-baseos-rpms           958 k
 tar                                          x86_64        2:1.35-9.el10_1                        rhel-10-for-x86_64-baseos-rpms           866 k
 tiwilink-firmware                            noarch        20251111-19.1.el10_1                   rhel-10-for-x86_64-baseos-rpms           4.7 M
 tuned                                        noarch        2.26.0-1.el10_1.1                      rhel-10-for-x86_64-baseos-rpms           560 k
 tzdata                                       noarch        2025c-1.el10                           rhel-10-for-x86_64-baseos-rpms           904 k
 unbound-anchor                               x86_64        1.20.0-15.el10_1                       rhel-10-for-x86_64-appstream-rpms         35 k
 unbound-libs                                 x86_64        1.20.0-15.el10_1                       rhel-10-for-x86_64-appstream-rpms        547 k
 vim-common                                   x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-appstream-rpms        7.7 M
 vim-data                                     noarch        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-baseos-rpms            17 k
 vim-enhanced                                 x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-appstream-rpms        1.9 M
 vim-filesystem                               noarch        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-baseos-rpms            16 k
 vim-minimal                                  x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-baseos-rpms           799 k
 which                                        x86_64        2.21-44.el10_0                         rhel-10-for-x86_64-baseos-rpms            42 k
 xxd                                          x86_64        2:9.1.083-6.el10_1                     rhel-10-for-x86_64-appstream-rpms         31 k
Installing dependencies:
 kernel-core                                  x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms            18 M
 kernel-modules                               x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms            41 M
 kernel-modules-core                          x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms            30 M
 kernel-modules-extra                         x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-baseos-rpms           2.8 M
Installing weak dependencies:
 kernel-devel                                 x86_64        6.12.0-124.29.1.el10_1                 rhel-10-for-x86_64-appstream-rpms         23 M

Transaction Summary
==================================================================================================================================================
Install    6 Packages
Upgrade  138 Packages

Total download size: 580 M
Is this ok [y/N]: y
Downloading Packages:
(1/144): kernel-6.12.0-124.29.1.el10_1.x86_64.rpm                                                                 815 kB/s | 1.4 MB     00:01    
(2/144): kernel-core-6.12.0-124.29.1.el10_1.x86_64.rpm                                                            5.7 MB/s |  18 MB     00:03    
(3/144): kernel-modules-extra-6.12.0-124.29.1.el10_1.x86_64.rpm                                                   5.0 MB/s | 2.8 MB     00:00    
(4/144): kernel-modules-6.12.0-124.29.1.el10_1.x86_64.rpm                                                         7.3 MB/s |  41 MB     00:05    
(5/144): which-2.21-44.el10_0.x86_64.rpm                                                                          144 kB/s |  42 kB     00:00    
(6/144): at-3.2.5-14.el10_1.x86_64.rpm                                                                            213 kB/s |  66 kB     00:00    
(7/144): libdnf-plugin-subscription-manager-1.30.10.1-1.el10_1.x86_64.rpm                                         182 kB/s |  41 kB     00:00    
(8/144): kernel-devel-6.12.0-124.29.1.el10_1.x86_64.rpm                                                           8.9 MB/s |  23 MB     00:02    
(9/144): kernel-modules-core-6.12.0-124.29.1.el10_1.x86_64.rpm                                                    6.3 MB/s |  30 MB     00:04    
(10/144): libipa_hbac-2.11.1-2.el10_1.1.x86_64.rpm                                                                149 kB/s |  34 kB     00:00    
(11/144): libnftnl-1.2.8-4.el10_1.x86_64.rpm                                                                      381 kB/s |  85 kB     00:00    
(12/144): libsss_certmap-2.11.1-2.el10_1.1.x86_64.rpm                                                             354 kB/s |  81 kB     00:00    
(13/144): libsss_idmap-2.11.1-2.el10_1.1.x86_64.rpm                                                               186 kB/s |  41 kB     00:00    
(14/144): libsss_nss_idmap-2.11.1-2.el10_1.1.x86_64.rpm                                                           212 kB/s |  44 kB     00:00    
(15/144): libsss_sudo-2.11.1-2.el10_1.1.x86_64.rpm                                                                155 kB/s |  33 kB     00:00    
(16/144): python3-cloud-what-1.30.10.1-1.el10_1.x86_64.rpm                                                        303 kB/s |  70 kB     00:00    
(17/144): python3-nftables-1.1.1-6.el10_1.x86_64.rpm                                                              100 kB/s |  22 kB     00:00    
(18/144): python3-subscription-manager-rhsm-1.30.10.1-1.el10_1.x86_64.rpm                                         801 kB/s | 181 kB     00:00    
(19/144): realmd-0.17.1-13.el10_1.x86_64.rpm                                                                      1.1 MB/s | 251 kB     00:00    
(20/144): nftables-1.1.1-6.el10_1.x86_64.rpm                                                                      615 kB/s | 437 kB     00:00    
(21/144): sssd-2.11.1-2.el10_1.1.x86_64.rpm                                                                       113 kB/s |  25 kB     00:00    
(22/144): sssd-ad-2.11.1-2.el10_1.1.x86_64.rpm                                                                    870 kB/s | 195 kB     00:00    
(23/144): sssd-client-2.11.1-2.el10_1.1.x86_64.rpm                                                                706 kB/s | 153 kB     00:00    
(24/144): sssd-common-pac-2.11.1-2.el10_1.1.x86_64.rpm                                                            370 kB/s |  89 kB     00:00    
(25/144): sssd-common-2.11.1-2.el10_1.1.x86_64.rpm                                                                3.6 MB/s | 1.5 MB     00:00    
(26/144): sssd-ipa-2.11.1-2.el10_1.1.x86_64.rpm                                                                   1.2 MB/s | 274 kB     00:00    
(27/144): sssd-kcm-2.11.1-2.el10_1.1.x86_64.rpm                                                                   479 kB/s | 103 kB     00:00    
(28/144): sssd-krb5-common-2.11.1-2.el10_1.1.x86_64.rpm                                                           432 kB/s |  93 kB     00:00    
(29/144): sssd-krb5-2.11.1-2.el10_1.1.x86_64.rpm                                                                  248 kB/s |  62 kB     00:00    
(30/144): sssd-ldap-2.11.1-2.el10_1.1.x86_64.rpm                                                                  598 kB/s | 132 kB     00:00    
(31/144): sssd-proxy-2.11.1-2.el10_1.1.x86_64.rpm                                                                 327 kB/s |  70 kB     00:00    
(32/144): sssd-nfs-idmap-2.11.1-2.el10_1.1.x86_64.rpm                                                             149 kB/s |  36 kB     00:00    
(33/144): subscription-manager-1.30.10.1-1.el10_1.x86_64.rpm                                                      3.6 MB/s | 958 kB     00:00    
(34/144): vim-data-9.1.083-6.el10_1.noarch.rpm                                                                     65 kB/s |  17 kB     00:00    
(35/144): vim-filesystem-9.1.083-6.el10_1.noarch.rpm                                                               70 kB/s |  16 kB     00:00    
(36/144): tuned-2.26.0-1.el10_1.1.noarch.rpm                                                                      1.5 MB/s | 560 kB     00:00    
(37/144): vim-minimal-9.1.083-6.el10_1.x86_64.rpm                                                                 3.1 MB/s | 799 kB     00:00    
(38/144): expat-2.7.1-1.el10_1.3.x86_64.rpm                                                                       484 kB/s | 119 kB     00:00    
(39/144): redhat-release-eula-10.1-18.el10.x86_64.rpm                                                              68 kB/s |  15 kB     00:00    
(40/144): openssh-9.9p1-12.el10_1.x86_64.rpm                                                                      1.5 MB/s | 351 kB     00:00    
(41/144): ca-certificates-2025.2.80_v9.0.305-102.el10_1.noarch.rpm                                                1.8 MB/s | 1.1 MB     00:00    
(42/144): openssh-clients-9.9p1-12.el10_1.x86_64.rpm                                                              2.9 MB/s | 761 kB     00:00    
(43/144): openssh-server-9.9p1-12.el10_1.x86_64.rpm                                                               2.2 MB/s | 539 kB     00:00    
(44/144): libssh-0.11.1-5.el10_1.x86_64.rpm                                                                       1.0 MB/s | 233 kB     00:00    
(45/144): tzdata-2025c-1.el10.noarch.rpm                                                                          3.0 MB/s | 904 kB     00:00    
(46/144): libssh-config-0.11.1-5.el10_1.noarch.rpm                                                                 43 kB/s | 8.6 kB     00:00    
(47/144): NetworkManager-tui-1.54.0-2.el10_1.x86_64.rpm                                                           696 kB/s | 233 kB     00:00    
(48/144): NetworkManager-1.54.0-2.el10_1.x86_64.rpm                                                               4.4 MB/s | 2.2 MB     00:00    
(49/144): NetworkManager-libnm-1.54.0-2.el10_1.x86_64.rpm                                                         3.7 MB/s | 1.9 MB     00:00    
(50/144): amd-ucode-firmware-20251111-19.1.el10_1.noarch.rpm                                                      1.4 MB/s | 466 kB     00:00    
(51/144): binutils-gold-2.41-58.el10_1.2.x86_64.rpm                                                               1.6 MB/s | 797 kB     00:00    
(52/144): binutils-2.41-58.el10_1.2.x86_64.rpm                                                                    6.6 MB/s | 6.4 MB     00:00    
(53/144): cirrus-audio-firmware-20251111-19.1.el10_1.noarch.rpm                                                   2.2 MB/s | 2.3 MB     00:01    
(54/144): brcmfmac-firmware-20251111-19.1.el10_1.noarch.rpm                                                       6.2 MB/s | 9.6 MB     00:01    
(55/144): iwlwifi-dvm-firmware-20251111-19.1.el10_1.noarch.rpm                                                    3.7 MB/s | 1.9 MB     00:00    
(56/144): intel-audio-firmware-20251111-19.1.el10_1.noarch.rpm                                                    4.8 MB/s | 3.3 MB     00:00    
(57/144): librepo-1.18.0-6.el10_1.x86_64.rpm                                                                      364 kB/s |  95 kB     00:00    
(58/144): atheros-firmware-20251111-19.1.el10_1.noarch.rpm                                                        9.9 MB/s |  41 MB     00:04    
(59/144): linux-firmware-whence-20251111-19.1.el10_1.noarch.rpm                                                   458 kB/s | 112 kB     00:00    
(60/144): man-pages-6.06-12.el10_1.noarch.rpm                                                                     6.5 MB/s | 3.7 MB     00:00    
(61/144): mt7xxx-firmware-20251111-19.1.el10_1.noarch.rpm                                                         9.5 MB/s |  20 MB     00:02    
(62/144): nxpwireless-firmware-20251111-19.1.el10_1.noarch.rpm                                                    4.1 MB/s | 980 kB     00:00    
(63/144): python3-librepo-1.18.0-6.el10_1.x86_64.rpm                                                              221 kB/s |  51 kB     00:00    
(64/144): realtek-firmware-20251111-19.1.el10_1.noarch.rpm                                                        7.7 MB/s | 5.8 MB     00:00    
(65/144): linux-firmware-20251111-19.1.el10_1.noarch.rpm                                                          9.2 MB/s |  54 MB     00:05    
(66/144): iwlwifi-mvm-firmware-20251111-19.1.el10_1.noarch.rpm                                                     11 MB/s |  68 MB     00:06    
(67/144): tiwilink-firmware-20251111-19.1.el10_1.noarch.rpm                                                       5.6 MB/s | 4.7 MB     00:00    
(68/144): python3-3.12.12-1.el10_1.x86_64.rpm                                                                     128 kB/s |  28 kB     00:00    
(69/144): tar-1.35-9.el10_1.x86_64.rpm                                                                            2.2 MB/s | 866 kB     00:00    
(70/144): sos-4.10.1-2.el10.noarch.rpm                                                                            3.0 MB/s | 1.4 MB     00:00    
(71/144): libpng-1.6.40-8.el10_1.1.x86_64.rpm                                                                     568 kB/s | 119 kB     00:00    
(72/144): python3-libs-3.12.12-1.el10_1.x86_64.rpm                                                                 15 MB/s | 9.4 MB     00:00    
(73/144): device-mapper-multipath-libs-0.9.9-12.el10_1.1.x86_64.rpm                                               1.3 MB/s | 305 kB     00:00    
(74/144): kpartx-0.9.9-12.el10_1.1.x86_64.rpm                                                                     242 kB/s |  52 kB     00:00    
(75/144): libbrotli-1.1.0-7.el10_1.x86_64.rpm                                                                     759 kB/s | 344 kB     00:00    
(76/144): gnupg2-2.4.5-3.el10_1.x86_64.rpm                                                                        5.0 MB/s | 2.7 MB     00:00    
(77/144): microcode_ctl-20250812-1.20251111.1.el10_1.noarch.rpm                                                    12 MB/s |  14 MB     00:01    
(78/144): glib2-2.80.4-10.el10_1.12.x86_64.rpm                                                                    5.6 MB/s | 3.1 MB     00:00    
(79/144): python3-urllib3-1.26.19-2.el10_1.1.noarch.rpm                                                           540 kB/s | 291 kB     00:00    
(80/144): kernel-tools-6.12.0-124.29.1.el10_1.x86_64.rpm                                                          6.3 MB/s | 1.9 MB     00:00    
(81/144): kernel-tools-libs-6.12.0-124.29.1.el10_1.x86_64.rpm                                                     4.6 MB/s | 1.4 MB     00:00    
(82/144): kernel-modules-extra-matched-6.12.0-124.29.1.el10_1.x86_64.rpm                                          3.8 MB/s | 1.4 MB     00:00    
(83/144): glibc-common-2.39-58.el10_1.7.x86_64.rpm                                                                1.4 MB/s | 326 kB     00:00    
(84/144): glibc-2.39-58.el10_1.7.x86_64.rpm                                                                       7.4 MB/s | 2.1 MB     00:00    
(85/144): glibc-langpack-en-2.39-58.el10_1.7.x86_64.rpm                                                           2.2 MB/s | 671 kB     00:00    
(86/144): glibc-gconv-extra-2.39-58.el10_1.7.x86_64.rpm                                                           3.2 MB/s | 1.7 MB     00:00    
(87/144): openssl-3.5.1-7.el10_1.x86_64.rpm                                                                       3.8 MB/s | 1.3 MB     00:00    
(88/144): cmake-filesystem-3.30.5-3.el10_0.x86_64.rpm                                                             141 kB/s |  24 kB     00:00    
(89/144): fprintd-1.94.5-1.el10_0.x86_64.rpm                                                                      892 kB/s | 187 kB     00:00    
(90/144): openssl-libs-3.5.1-7.el10_1.x86_64.rpm                                                                  7.3 MB/s | 2.3 MB     00:00    
(91/144): fprintd-pam-1.94.5-1.el10_0.x86_64.rpm                                                                  135 kB/s |  23 kB     00:00    
(92/144): libtpms-0.9.6-11.el10_0.x86_64.rpm                                                                      1.2 MB/s | 185 kB     00:00    
(93/144): libfprint-1.94.9-1.el10_0.x86_64.rpm                                                                    1.5 MB/s | 344 kB     00:00    
(94/144): libuv-1.51.0-1.el10_0.x86_64.rpm                                                                        1.6 MB/s | 262 kB     00:00    
(95/144): mesa-filesystem-25.0.7-6.el10_1.x86_64.rpm                                                               84 kB/s |  13 kB     00:00    
(96/144): mesa-libEGL-25.0.7-6.el10_1.x86_64.rpm                                                                  675 kB/s | 131 kB     00:00    
(97/144): mesa-libGL-25.0.7-6.el10_1.x86_64.rpm                                                                   1.0 MB/s | 160 kB     00:00    
(98/144): mesa-libgbm-25.0.7-6.el10_1.x86_64.rpm                                                                  108 kB/s |  19 kB     00:00    
(99/144): passt-0^20250512.g8ec1341-4.el10_1.x86_64.rpm                                                           1.5 MB/s | 265 kB     00:00    
(100/144): passt-selinux-0^20250512.g8ec1341-4.el10_1.noarch.rpm                                                  195 kB/s |  28 kB     00:00    
(101/144): mesa-dri-drivers-25.0.7-6.el10_1.x86_64.rpm                                                             11 MB/s |  11 MB     00:01    
(102/144): vim-enhanced-9.1.083-6.el10_1.x86_64.rpm                                                               3.5 MB/s | 1.9 MB     00:00    
(103/144): vim-common-9.1.083-6.el10_1.x86_64.rpm                                                                  11 MB/s | 7.7 MB     00:00    
(104/144): bind-libs-9.18.33-10.el10_1.2.x86_64.rpm                                                               5.2 MB/s | 1.3 MB     00:00    
(105/144): xxd-9.1.083-6.el10_1.x86_64.rpm                                                                         90 kB/s |  31 kB     00:00    
(106/144): bind-license-9.18.33-10.el10_1.2.noarch.rpm                                                             70 kB/s |  13 kB     00:00    
(107/144): bind-utils-9.18.33-10.el10_1.2.x86_64.rpm                                                              1.2 MB/s | 227 kB     00:00    
(108/144): libvirt-11.5.0-4.2.el10_1.x86_64.rpm                                                                    92 kB/s |  19 kB     00:00    
(109/144): libvirt-client-11.5.0-4.2.el10_1.x86_64.rpm                                                            2.7 MB/s | 449 kB     00:00    
(110/144): libvirt-client-qemu-11.5.0-4.2.el10_1.x86_64.rpm                                                       164 kB/s |  43 kB     00:00    
(111/144): libvirt-daemon-11.5.0-4.2.el10_1.x86_64.rpm                                                            1.2 MB/s | 209 kB     00:00    
(112/144): intel-gpu-firmware-20251111-19.1.el10_1.noarch.rpm                                                     8.9 MB/s | 8.9 MB     00:00    
(113/144): libvirt-daemon-common-11.5.0-4.2.el10_1.x86_64.rpm                                                     949 kB/s | 145 kB     00:00    
(114/144): libvirt-daemon-config-network-11.5.0-4.2.el10_1.x86_64.rpm                                             122 kB/s |  24 kB     00:00    
(115/144): libvirt-daemon-config-nwfilter-11.5.0-4.2.el10_1.x86_64.rpm                                            220 kB/s |  37 kB     00:00    
(116/144): libvirt-daemon-driver-interface-11.5.0-4.2.el10_1.x86_64.rpm                                           1.1 MB/s | 215 kB     00:00    
(117/144): libvirt-daemon-driver-network-11.5.0-4.2.el10_1.x86_64.rpm                                             1.5 MB/s | 268 kB     00:00    
(118/144): libvirt-daemon-driver-nodedev-11.5.0-4.2.el10_1.x86_64.rpm                                             1.1 MB/s | 238 kB     00:00    
(119/144): libvirt-daemon-driver-nwfilter-11.5.0-4.2.el10_1.x86_64.rpm                                            1.1 MB/s | 251 kB     00:00    
(120/144): libvirt-daemon-driver-secret-11.5.0-4.2.el10_1.x86_64.rpm                                              1.2 MB/s | 212 kB     00:00    
(121/144): libvirt-daemon-driver-qemu-11.5.0-4.2.el10_1.x86_64.rpm                                                3.1 MB/s | 1.0 MB     00:00    
(122/144): amd-gpu-firmware-20251111-19.1.el10_1.noarch.rpm                                                        14 MB/s |  28 MB     00:02    
(123/144): libvirt-daemon-driver-storage-11.5.0-4.2.el10_1.x86_64.rpm                                              99 kB/s |  18 kB     00:00    
(124/144): libvirt-daemon-driver-storage-core-11.5.0-4.2.el10_1.x86_64.rpm                                        1.5 MB/s | 268 kB     00:00    
(125/144): libvirt-daemon-driver-storage-disk-11.5.0-4.2.el10_1.x86_64.rpm                                        227 kB/s |  33 kB     00:00    
(126/144): libvirt-daemon-driver-storage-iscsi-11.5.0-4.2.el10_1.x86_64.rpm                                       214 kB/s |  30 kB     00:00    
(127/144): libvirt-daemon-driver-storage-logical-11.5.0-4.2.el10_1.x86_64.rpm                                     241 kB/s |  34 kB     00:00    
(128/144): libvirt-daemon-driver-storage-mpath-11.5.0-4.2.el10_1.x86_64.rpm                                       165 kB/s |  28 kB     00:00    
(129/144): libvirt-daemon-driver-storage-rbd-11.5.0-4.2.el10_1.x86_64.rpm                                         253 kB/s |  39 kB     00:00    
(130/144): libvirt-daemon-driver-storage-scsi-11.5.0-4.2.el10_1.x86_64.rpm                                        150 kB/s |  30 kB     00:00    
(131/144): libvirt-daemon-log-11.5.0-4.2.el10_1.x86_64.rpm                                                        401 kB/s |  64 kB     00:00    
(132/144): libvirt-daemon-lock-11.5.0-4.2.el10_1.x86_64.rpm                                                       307 kB/s |  60 kB     00:00    
(133/144): libvirt-daemon-plugin-lockd-11.5.0-4.2.el10_1.x86_64.rpm                                               195 kB/s |  34 kB     00:00    
(134/144): libvirt-daemon-proxy-11.5.0-4.2.el10_1.x86_64.rpm                                                      1.1 MB/s | 207 kB     00:00    
(135/144): unbound-anchor-1.20.0-15.el10_1.x86_64.rpm                                                             220 kB/s |  35 kB     00:00    
(136/144): unbound-libs-1.20.0-15.el10_1.x86_64.rpm                                                               2.2 MB/s | 547 kB     00:00    
(137/144): python-unversioned-command-3.12.12-1.el10_1.noarch.rpm                                                  60 kB/s |  11 kB     00:00    
(138/144): gnupg2-smime-2.4.5-3.el10_1.x86_64.rpm                                                                 1.1 MB/s | 266 kB     00:00    
(139/144): libvirt-libs-11.5.0-4.2.el10_1.x86_64.rpm                                                              4.7 MB/s | 5.2 MB     00:01    
(140/144): python3-perf-6.12.0-124.29.1.el10_1.x86_64.rpm                                                         5.1 MB/s | 2.7 MB     00:00    
(141/144): kernel-headers-6.12.0-124.29.1.el10_1.x86_64.rpm                                                       4.7 MB/s | 3.2 MB     00:00    
(142/144): glibc-devel-2.39-58.el10_1.7.x86_64.rpm                                                                1.2 MB/s | 588 kB     00:00    
(143/144): openssl-devel-3.5.1-7.el10_1.x86_64.rpm                                                                6.0 MB/s | 4.2 MB     00:00    
(144/144): nvidia-gpu-firmware-20251111-19.1.el10_1.noarch.rpm                                                     14 MB/s |  99 MB     00:07    
--------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                              17 MB/s | 580 MB     00:33     
Red Hat Enterprise Linux 10 for x86_64 - BaseOS (RPMs)                                                             20 MB/s |  20 kB     00:00    
GPG key at file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release (0xFD431D51) is already installed
GPG key at file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release (0x5A6340B3) is already installed
Importing GPG key 0x05707A62:
 Userid     : "Red Hat, Inc. (release key 4) <security@redhat.com>"
 Fingerprint: FCD3 55B3 0570 7A62 DA14 3AB6 E422 397E 50FE 8467 A2A9 5343 D246 D627 6AFE DF8F
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
Is this ok [y/N]: y
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Running scriptlet: nvidia-gpu-firmware-20251111-19.1.el10_1.noarch                                                                          1/1 
  Preparing        :                                                                                                                          1/1 
  Upgrading        : linux-firmware-whence-20251111-19.1.el10_1.noarch                                                                      1/282 
  Upgrading        : tzdata-2025c-1.el10.noarch                                                                                             2/282 
  Upgrading        : glibc-gconv-extra-2.39-58.el10_1.7.x86_64                                                                              3/282 
  Running scriptlet: glibc-gconv-extra-2.39-58.el10_1.7.x86_64                                                                              3/282 
  Running scriptlet: glibc-2.39-58.el10_1.7.x86_64                                                                                          4/282 
  Upgrading        : glibc-2.39-58.el10_1.7.x86_64                                                                                          4/282 
  Running scriptlet: glibc-2.39-58.el10_1.7.x86_64                                                                                          4/282 
  Upgrading        : glibc-common-2.39-58.el10_1.7.x86_64                                                                                   5/282 
  Upgrading        : glibc-langpack-en-2.39-58.el10_1.7.x86_64                                                                              6/282 
  Upgrading        : glib2-2.80.4-10.el10_1.12.x86_64                                                                                       7/282 
  Upgrading        : libsss_idmap-2.11.1-2.el10_1.1.x86_64                                                                                  8/282 
  Upgrading        : expat-2.7.1-1.el10_1.3.x86_64                                                                                          9/282 
  Upgrading        : NetworkManager-libnm-1:1.54.0-2.el10_1.x86_64                                                                         10/282 
  Upgrading        : passt-0^20250512.g8ec1341-4.el10_1.x86_64                                                                             11/282 
  Running scriptlet: passt-selinux-0^20250512.g8ec1341-4.el10_1.noarch                                                                     12/282 
  Upgrading        : passt-selinux-0^20250512.g8ec1341-4.el10_1.noarch                                                                     12/282 
  Running scriptlet: passt-selinux-0^20250512.g8ec1341-4.el10_1.noarch                                                                     12/282 
  Running scriptlet: ca-certificates-2025.2.80_v9.0.305-102.el10_1.noarch                                                                  13/282 
  Upgrading        : ca-certificates-2025.2.80_v9.0.305-102.el10_1.noarch                                                                  13/282 
  Running scriptlet: ca-certificates-2025.2.80_v9.0.305-102.el10_1.noarch                                                                  13/282 
  Upgrading        : openssl-libs-1:3.5.1-7.el10_1.x86_64                                                                                  14/282 
  Upgrading        : libsss_certmap-2.11.1-2.el10_1.1.x86_64                                                                               15/282 
  Upgrading        : python-unversioned-command-3.12.12-1.el10_1.noarch                                                                    16/282 
  Upgrading        : python3-3.12.12-1.el10_1.x86_64                                                                                       17/282 
  Upgrading        : python3-libs-3.12.12-1.el10_1.x86_64                                                                                  18/282 
  Upgrading        : python3-cloud-what-1.30.10.1-1.el10_1.x86_64                                                                          19/282 
  Upgrading        : openssh-9.9p1-12.el10_1.x86_64                                                                                        20/282 
  Upgrading        : librepo-1.18.0-6.el10_1.x86_64                                                                                        21/282 
  Upgrading        : vim-data-2:9.1.083-6.el10_1.noarch                                                                                    22/282 
  Upgrading        : libdnf-plugin-subscription-manager-1.30.10.1-1.el10_1.x86_64                                                          23/282 
  Upgrading        : python3-librepo-1.18.0-6.el10_1.x86_64                                                                                24/282 
  Upgrading        : python3-subscription-manager-rhsm-1.30.10.1-1.el10_1.x86_64                                                           25/282 
  Running scriptlet: subscription-manager-1.30.10.1-1.el10_1.x86_64                                                                        26/282 
  Upgrading        : subscription-manager-1.30.10.1-1.el10_1.x86_64                                                                        26/282 
  Running scriptlet: subscription-manager-1.30.10.1-1.el10_1.x86_64                                                                        26/282 
  Upgrading        : unbound-anchor-1.20.0-15.el10_1.x86_64                                                                                27/282 
  Running scriptlet: unbound-anchor-1.20.0-15.el10_1.x86_64                                                                                27/282 
  Running scriptlet: unbound-libs-1.20.0-15.el10_1.x86_64                                                                                  28/282 
  Upgrading        : unbound-libs-1.20.0-15.el10_1.x86_64                                                                                  28/282 
  Upgrading        : python3-perf-6.12.0-124.29.1.el10_1.x86_64                                                                            29/282 
  Upgrading        : libfprint-1.94.9-1.el10_0.x86_64                                                                                      30/282 
  Upgrading        : fprintd-1.94.5-1.el10_0.x86_64                                                                                        31/282 
  Upgrading        : openssl-devel-1:3.5.1-7.el10_1.x86_64                                                                                 32/282 
  Running scriptlet: NetworkManager-1:1.54.0-2.el10_1.x86_64                                                                               33/282 
  Upgrading        : NetworkManager-1:1.54.0-2.el10_1.x86_64                                                                               33/282 
  Running scriptlet: NetworkManager-1:1.54.0-2.el10_1.x86_64                                                                               33/282 
  Upgrading        : which-2.21-44.el10_0.x86_64                                                                                           34/282 
  Upgrading        : libipa_hbac-2.11.1-2.el10_1.1.x86_64                                                                                  35/282 
  Upgrading        : libnftnl-1.2.8-4.el10_1.x86_64                                                                                        36/282 
  Upgrading        : nftables-1:1.1.1-6.el10_1.x86_64                                                                                      37/282 
  Running scriptlet: nftables-1:1.1.1-6.el10_1.x86_64                                                                                      37/282 
  Upgrading        : libsss_nss_idmap-2.11.1-2.el10_1.1.x86_64                                                                             38/282 
  Upgrading        : sssd-client-2.11.1-2.el10_1.1.x86_64                                                                                  39/282 
  Running scriptlet: sssd-client-2.11.1-2.el10_1.1.x86_64                                                                                  39/282 
  Upgrading        : libsss_sudo-2.11.1-2.el10_1.1.x86_64                                                                                  40/282 
  Upgrading        : sssd-nfs-idmap-2.11.1-2.el10_1.1.x86_64                                                                               41/282 
  Running scriptlet: sssd-common-2.11.1-2.el10_1.1.x86_64                                                                                  42/282 
  Upgrading        : sssd-common-2.11.1-2.el10_1.1.x86_64                                                                                  42/282 
  Running scriptlet: sssd-common-2.11.1-2.el10_1.1.x86_64                                                                                  42/282 
  Upgrading        : sssd-krb5-common-2.11.1-2.el10_1.1.x86_64                                                                             43/282 
  Upgrading        : sssd-common-pac-2.11.1-2.el10_1.1.x86_64                                                                              44/282 
  Upgrading        : sssd-krb5-2.11.1-2.el10_1.1.x86_64                                                                                    45/282 
  Upgrading        : sssd-ldap-2.11.1-2.el10_1.1.x86_64                                                                                    46/282 
  Upgrading        : sssd-proxy-2.11.1-2.el10_1.1.x86_64                                                                                   47/282 
  Upgrading        : binutils-2.41-58.el10_1.2.x86_64                                                                                      48/282 
  Running scriptlet: binutils-2.41-58.el10_1.2.x86_64                                                                                      48/282 
  Upgrading        : binutils-gold-2.41-58.el10_1.2.x86_64                                                                                 49/282 
  Running scriptlet: binutils-gold-2.41-58.el10_1.2.x86_64                                                                                 49/282 
  Upgrading        : gnupg2-2.4.5-3.el10_1.x86_64                                                                                          50/282 
  Upgrading        : gnupg2-smime-2.4.5-3.el10_1.x86_64                                                                                    51/282 
  Upgrading        : kernel-tools-libs-6.12.0-124.29.1.el10_1.x86_64                                                                       52/282 
  Running scriptlet: kernel-tools-libs-6.12.0-124.29.1.el10_1.x86_64                                                                       52/282 
  Upgrading        : kernel-tools-6.12.0-124.29.1.el10_1.x86_64                                                                            53/282 
  Upgrading        : libuv-1:1.51.0-1.el10_0.x86_64                                                                                        54/282 
  Upgrading        : xxd-2:9.1.083-6.el10_1.x86_64                                                                                         55/282 
  Upgrading        : amd-ucode-firmware-20251111-19.1.el10_1.noarch                                                                        56/282 
  Upgrading        : atheros-firmware-20251111-19.1.el10_1.noarch                                                                          57/282 
  Upgrading        : brcmfmac-firmware-20251111-19.1.el10_1.noarch                                                                         58/282 
  Upgrading        : cirrus-audio-firmware-20251111-19.1.el10_1.noarch                                                                     59/282 
  Upgrading        : intel-audio-firmware-20251111-19.1.el10_1.noarch                                                                      60/282 
  Upgrading        : mt7xxx-firmware-20251111-19.1.el10_1.noarch                                                                           61/282 
  Upgrading        : nxpwireless-firmware-20251111-19.1.el10_1.noarch                                                                      62/282 
  Upgrading        : realtek-firmware-20251111-19.1.el10_1.noarch                                                                          63/282 
  Upgrading        : tiwilink-firmware-20251111-19.1.el10_1.noarch                                                                         64/282 
  Upgrading        : amd-gpu-firmware-20251111-19.1.el10_1.noarch                                                                          65/282 
  Upgrading        : intel-gpu-firmware-20251111-19.1.el10_1.noarch                                                                        66/282 
  Upgrading        : nvidia-gpu-firmware-20251111-19.1.el10_1.noarch                                                                       67/282 
  Upgrading        : linux-firmware-20251111-19.1.el10_1.noarch                                                                            68/282 
  Installing       : kernel-modules-core-6.12.0-124.29.1.el10_1.x86_64                                                                     69/282 
  Installing       : kernel-core-6.12.0-124.29.1.el10_1.x86_64                                                                             70/282 
  Running scriptlet: kernel-core-6.12.0-124.29.1.el10_1.x86_64                                                                             70/282 
  Installing       : kernel-modules-6.12.0-124.29.1.el10_1.x86_64                                                                          71/282 
  Running scriptlet: kernel-modules-6.12.0-124.29.1.el10_1.x86_64                                                                          71/282 
  Installing       : kernel-modules-extra-6.12.0-124.29.1.el10_1.x86_64                                                                    72/282 
  Running scriptlet: kernel-modules-extra-6.12.0-124.29.1.el10_1.x86_64                                                                    72/282 
  Upgrading        : kernel-headers-6.12.0-124.29.1.el10_1.x86_64                                                                          73/282 
  Upgrading        : bind-license-32:9.18.33-10.el10_1.2.noarch                                                                            74/282 
  Upgrading        : bind-libs-32:9.18.33-10.el10_1.2.x86_64                                                                               75/282 
  Upgrading        : bind-utils-32:9.18.33-10.el10_1.2.x86_64                                                                              76/282 
  Upgrading        : sssd-ad-2.11.1-2.el10_1.1.x86_64                                                                                      77/282 
  Upgrading        : sssd-ipa-2.11.1-2.el10_1.1.x86_64                                                                                     78/282 
  Upgrading        : mesa-filesystem-25.0.7-6.el10_1.x86_64                                                                                79/282 
  Upgrading        : mesa-dri-drivers-25.0.7-6.el10_1.x86_64                                                                               80/282 
  Upgrading        : mesa-libgbm-25.0.7-6.el10_1.x86_64                                                                                    81/282 
  Upgrading        : libssh-config-0.11.1-5.el10_1.noarch                                                                                  82/282 
  Upgrading        : libssh-0.11.1-5.el10_1.x86_64                                                                                         83/282 
  Upgrading        : libvirt-libs-11.5.0-4.2.el10_1.x86_64                                                                                 84/282 
  Upgrading        : libvirt-client-11.5.0-4.2.el10_1.x86_64                                                                               85/282 
  Running scriptlet: libvirt-daemon-common-11.5.0-4.2.el10_1.x86_64                                                                        86/282 
  Upgrading        : libvirt-daemon-common-11.5.0-4.2.el10_1.x86_64                                                                        86/282 
  Running scriptlet: libvirt-daemon-driver-storage-core-11.5.0-4.2.el10_1.x86_64                                                           87/282 
  Upgrading        : libvirt-daemon-driver-storage-core-11.5.0-4.2.el10_1.x86_64                                                           87/282 
  Running scriptlet: libvirt-daemon-driver-network-11.5.0-4.2.el10_1.x86_64                                                                88/282 
  Upgrading        : libvirt-daemon-driver-network-11.5.0-4.2.el10_1.x86_64                                                                88/282 
  Running scriptlet: libvirt-daemon-driver-network-11.5.0-4.2.el10_1.x86_64                                                                88/282 
  Running scriptlet: libvirt-daemon-driver-nwfilter-11.5.0-4.2.el10_1.x86_64                                                               89/282 
  Upgrading        : libvirt-daemon-driver-nwfilter-11.5.0-4.2.el10_1.x86_64                                                               89/282 
  Running scriptlet: libvirt-daemon-lock-11.5.0-4.2.el10_1.x86_64                                                                          90/282 
  Upgrading        : libvirt-daemon-lock-11.5.0-4.2.el10_1.x86_64                                                                          90/282 
  Running scriptlet: libvirt-daemon-log-11.5.0-4.2.el10_1.x86_64                                                                           91/282 
  Upgrading        : libvirt-daemon-log-11.5.0-4.2.el10_1.x86_64                                                                           91/282 
  Running scriptlet: libvirt-daemon-driver-qemu-11.5.0-4.2.el10_1.x86_64                                                                   92/282 
  Upgrading        : libvirt-daemon-driver-qemu-11.5.0-4.2.el10_1.x86_64                                                                   92/282 
  Upgrading        : libvirt-daemon-plugin-lockd-11.5.0-4.2.el10_1.x86_64                                                                  93/282 
  Running scriptlet: libvirt-daemon-config-nwfilter-11.5.0-4.2.el10_1.x86_64                                                               94/282 
  Upgrading        : libvirt-daemon-config-nwfilter-11.5.0-4.2.el10_1.x86_64                                                               94/282 
  Running scriptlet: libvirt-daemon-config-nwfilter-11.5.0-4.2.el10_1.x86_64                                                               94/282 
  Running scriptlet: libvirt-daemon-config-network-11.5.0-4.2.el10_1.x86_64                                                                95/282 
  Upgrading        : libvirt-daemon-config-network-11.5.0-4.2.el10_1.x86_64                                                                95/282 
  Running scriptlet: libvirt-daemon-config-network-11.5.0-4.2.el10_1.x86_64                                                                95/282 
  Upgrading        : libvirt-daemon-driver-storage-disk-11.5.0-4.2.el10_1.x86_64                                                           96/282 
  Upgrading        : libvirt-daemon-driver-storage-iscsi-11.5.0-4.2.el10_1.x86_64                                                          97/282 
  Upgrading        : libvirt-daemon-driver-storage-logical-11.5.0-4.2.el10_1.x86_64                                                        98/282 
  Upgrading        : libvirt-daemon-driver-storage-mpath-11.5.0-4.2.el10_1.x86_64                                                          99/282 
  Upgrading        : libvirt-daemon-driver-storage-rbd-11.5.0-4.2.el10_1.x86_64                                                           100/282 
  Upgrading        : libvirt-daemon-driver-storage-scsi-11.5.0-4.2.el10_1.x86_64                                                          101/282 
  Upgrading        : libvirt-daemon-driver-storage-11.5.0-4.2.el10_1.x86_64                                                               102/282 
  Running scriptlet: libvirt-daemon-driver-interface-11.5.0-4.2.el10_1.x86_64                                                             103/282 
  Upgrading        : libvirt-daemon-driver-interface-11.5.0-4.2.el10_1.x86_64                                                             103/282 
  Running scriptlet: libvirt-daemon-driver-nodedev-11.5.0-4.2.el10_1.x86_64                                                               104/282 
  Upgrading        : libvirt-daemon-driver-nodedev-11.5.0-4.2.el10_1.x86_64                                                               104/282 
  Running scriptlet: libvirt-daemon-driver-secret-11.5.0-4.2.el10_1.x86_64                                                                105/282 
  Upgrading        : libvirt-daemon-driver-secret-11.5.0-4.2.el10_1.x86_64                                                                105/282 
  Upgrading        : libvirt-client-qemu-11.5.0-4.2.el10_1.x86_64                                                                         106/282 
  Running scriptlet: libvirt-daemon-proxy-11.5.0-4.2.el10_1.x86_64                                                                        107/282 
  Upgrading        : libvirt-daemon-proxy-11.5.0-4.2.el10_1.x86_64                                                                        107/282 
  Running scriptlet: libvirt-daemon-11.5.0-4.2.el10_1.x86_64                                                                              108/282 
  Upgrading        : libvirt-daemon-11.5.0-4.2.el10_1.x86_64                                                                              108/282 
  Upgrading        : vim-filesystem-2:9.1.083-6.el10_1.noarch                                                                             109/282 
  Upgrading        : vim-common-2:9.1.083-6.el10_1.x86_64                                                                                 110/282 
  Upgrading        : vim-enhanced-2:9.1.083-6.el10_1.x86_64                                                                               111/282 
  Upgrading        : libvirt-11.5.0-4.2.el10_1.x86_64                                                                                     112/282 
  Upgrading        : mesa-libEGL-25.0.7-6.el10_1.x86_64                                                                                   113/282 
  Upgrading        : mesa-libGL-25.0.7-6.el10_1.x86_64                                                                                    114/282 
  Upgrading        : sssd-2.11.1-2.el10_1.1.x86_64                                                                                        115/282 
  Upgrading        : glibc-devel-2.39-58.el10_1.7.x86_64                                                                                  116/282 
  Installing       : kernel-6.12.0-124.29.1.el10_1.x86_64                                                                                 117/282 
  Upgrading        : tuned-2.26.0-1.el10_1.1.noarch                                                                                       118/282 
  Running scriptlet: tuned-2.26.0-1.el10_1.1.noarch                                                                                       118/282 
  Upgrading        : sssd-kcm-2.11.1-2.el10_1.1.x86_64                                                                                    119/282 
  Running scriptlet: sssd-kcm-2.11.1-2.el10_1.1.x86_64                                                                                    119/282 
  Upgrading        : python3-nftables-1:1.1.1-6.el10_1.x86_64                                                                             120/282 
  Upgrading        : NetworkManager-tui-1:1.54.0-2.el10_1.x86_64                                                                          121/282 
  Installing       : kernel-devel-6.12.0-124.29.1.el10_1.x86_64                                                                           122/282 
  Running scriptlet: kernel-devel-6.12.0-124.29.1.el10_1.x86_64                                                                           122/282 
  Upgrading        : fprintd-pam-1.94.5-1.el10_0.x86_64                                                                                   123/282 
  Upgrading        : vim-minimal-2:9.1.083-6.el10_1.x86_64                                                                                124/282 
  Upgrading        : openssh-clients-9.9p1-12.el10_1.x86_64                                                                               125/282 
  Running scriptlet: openssh-clients-9.9p1-12.el10_1.x86_64                                                                               125/282 
  Running scriptlet: openssh-server-9.9p1-12.el10_1.x86_64                                                                                126/282 
  Upgrading        : openssh-server-9.9p1-12.el10_1.x86_64                                                                                126/282 
  Running scriptlet: openssh-server-9.9p1-12.el10_1.x86_64                                                                                126/282 
  Upgrading        : sos-4.10.1-2.el10.noarch                                                                                             127/282 
  Upgrading        : python3-urllib3-1.26.19-2.el10_1.1.noarch                                                                            128/282 
  Upgrading        : openssl-1:3.5.1-7.el10_1.x86_64                                                                                      129/282 
  Upgrading        : libtpms-0.9.6-11.el10_0.x86_64                                                                                       130/282 
  Upgrading        : realmd-0.17.1-13.el10_1.x86_64                                                                                       131/282 
  Running scriptlet: realmd-0.17.1-13.el10_1.x86_64                                                                                       131/282 
  Upgrading        : at-3.2.5-14.el10_1.x86_64                                                                                            132/282 
  Running scriptlet: at-3.2.5-14.el10_1.x86_64                                                                                            132/282 
  Upgrading        : tar-2:1.35-9.el10_1.x86_64                                                                                           133/282 
  Upgrading        : libpng-2:1.6.40-8.el10_1.1.x86_64                                                                                    134/282 
  Upgrading        : device-mapper-multipath-libs-0.9.9-12.el10_1.1.x86_64                                                                135/282 
  Upgrading        : kpartx-0.9.9-12.el10_1.1.x86_64                                                                                      136/282 
  Upgrading        : libbrotli-1.1.0-7.el10_1.x86_64                                                                                      137/282 
  Upgrading        : iwlwifi-dvm-firmware-20251111-19.1.el10_1.noarch                                                                     138/282 
  Upgrading        : iwlwifi-mvm-firmware-20251111-19.1.el10_1.noarch                                                                     139/282 
  Upgrading        : cmake-filesystem-3.30.5-3.el10_0.x86_64                                                                              140/282 
  Upgrading        : kernel-modules-extra-matched-6.12.0-124.29.1.el10_1.x86_64                                                           141/282 
  Upgrading        : microcode_ctl-4:20250812-1.20251111.1.el10_1.noarch                                                                  142/282 
  Running scriptlet: microcode_ctl-4:20250812-1.20251111.1.el10_1.noarch                                                                  142/282 
  Running scriptlet: man-pages-6.06-12.el10_1.noarch                                                                                      143/282 
  Upgrading        : man-pages-6.06-12.el10_1.noarch                                                                                      143/282 
  Running scriptlet: man-pages-6.06-12.el10_1.noarch                                                                                      143/282 
  Upgrading        : redhat-release-eula-10.1-18.el10.x86_64                                                                              144/282 
  Cleanup          : NetworkManager-tui-1:1.54.0-1.el10.x86_64                                                                            145/282 
  Running scriptlet: NetworkManager-1:1.54.0-1.el10.x86_64                                                                                146/282 
  Cleanup          : NetworkManager-1:1.54.0-1.el10.x86_64                                                                                146/282 
  Running scriptlet: NetworkManager-1:1.54.0-1.el10.x86_64                                                                                146/282 
  Cleanup          : openssl-1:3.5.1-3.el10.x86_64                                                                                        147/282 
  Cleanup          : mesa-libEGL-25.0.7-3.el10.x86_64                                                                                     148/282 
  Cleanup          : vim-enhanced-2:9.1.083-5.el10_0.1.x86_64                                                                             149/282 
  Running scriptlet: binutils-2.41-58.el10.x86_64                                                                                         150/282 
  Cleanup          : binutils-2.41-58.el10.x86_64                                                                                         150/282 
  Running scriptlet: binutils-2.41-58.el10.x86_64                                                                                         150/282 
  Cleanup          : device-mapper-multipath-libs-0.9.9-12.el10_1.x86_64                                                                  151/282 
  Running scriptlet: openssh-server-9.9p1-11.el10.x86_64                                                                                  152/282 
  Cleanup          : openssh-server-9.9p1-11.el10.x86_64                                                                                  152/282 
  Running scriptlet: openssh-server-9.9p1-11.el10.x86_64                                                                                  152/282 
  Cleanup          : mesa-libGL-25.0.7-3.el10.x86_64                                                                                      153/282 
  Cleanup          : mesa-libgbm-25.0.7-3.el10.x86_64                                                                                     154/282 
  Cleanup          : mesa-dri-drivers-25.0.7-3.el10.x86_64                                                                                155/282 
  Cleanup          : tar-2:1.35-7.el10.x86_64                                                                                             156/282 
  Running scriptlet: openssh-clients-9.9p1-11.el10.x86_64                                                                                 157/282 
  Cleanup          : openssh-clients-9.9p1-11.el10.x86_64                                                                                 157/282 
  Cleanup          : openssh-9.9p1-11.el10.x86_64                                                                                         158/282 
  Cleanup          : gnupg2-2.4.5-2.el10.x86_64                                                                                           159/282 
  Cleanup          : NetworkManager-libnm-1:1.54.0-1.el10.x86_64                                                                          160/282 
  Running scriptlet: unbound-anchor-1.20.0-13.el10.x86_64                                                                                 161/282 
  Cleanup          : unbound-anchor-1.20.0-13.el10.x86_64                                                                                 161/282 
  Running scriptlet: unbound-anchor-1.20.0-13.el10.x86_64                                                                                 161/282 
  Cleanup          : unbound-libs-1.20.0-13.el10.x86_64                                                                                   162/282 
  Cleanup          : vim-minimal-2:9.1.083-5.el10_0.1.x86_64                                                                              163/282 
  Running scriptlet: sssd-kcm-2.11.1-2.el10.x86_64                                                                                        164/282 
  Cleanup          : sssd-kcm-2.11.1-2.el10.x86_64                                                                                        164/282 
  Running scriptlet: sssd-kcm-2.11.1-2.el10.x86_64                                                                                        164/282 
  Cleanup          : libvirt-11.5.0-4.el10.x86_64                                                                                         165/282 
  Cleanup          : linux-firmware-20250812-19.el10.noarch                                                                               166/282 
  Running scriptlet: libvirt-daemon-driver-qemu-11.5.0-4.el10.x86_64                                                                      167/282 
  Cleanup          : libvirt-daemon-driver-qemu-11.5.0-4.el10.x86_64                                                                      167/282 
  Running scriptlet: libvirt-daemon-11.5.0-4.el10.x86_64                                                                                  168/282 
  Cleanup          : libvirt-daemon-11.5.0-4.el10.x86_64                                                                                  168/282 
  Running scriptlet: libvirt-daemon-driver-interface-11.5.0-4.el10.x86_64                                                                 169/282 
  Cleanup          : libvirt-daemon-driver-interface-11.5.0-4.el10.x86_64                                                                 169/282 
  Running scriptlet: libvirt-daemon-driver-nodedev-11.5.0-4.el10.x86_64                                                                   170/282 
  Cleanup          : libvirt-daemon-driver-nodedev-11.5.0-4.el10.x86_64                                                                   170/282 
  Running scriptlet: libvirt-daemon-driver-secret-11.5.0-4.el10.x86_64                                                                    171/282 
  Cleanup          : libvirt-daemon-driver-secret-11.5.0-4.el10.x86_64                                                                    171/282 
  Running scriptlet: libvirt-daemon-proxy-11.5.0-4.el10.x86_64                                                                            172/282 
  Cleanup          : libvirt-daemon-proxy-11.5.0-4.el10.x86_64                                                                            172/282 
  Cleanup          : passt-0^20250512.g8ec1341-2.el10.x86_64                                                                              173/282 
  Running scriptlet: libvirt-daemon-log-11.5.0-4.el10.x86_64                                                                              174/282 
  Cleanup          : libvirt-daemon-log-11.5.0-4.el10.x86_64                                                                              174/282 
  Cleanup          : gnupg2-smime-2.4.5-2.el10.x86_64                                                                                     175/282 
  Running scriptlet: binutils-gold-2.41-58.el10.x86_64                                                                                    176/282 
  Cleanup          : binutils-gold-2.41-58.el10.x86_64                                                                                    176/282 
  Cleanup          : libtpms-0.9.6-11.el10.x86_64                                                                                         177/282 
  Running scriptlet: at-3.2.5-13.el10_0.x86_64                                                                                            178/282 
  Cleanup          : at-3.2.5-13.el10_0.x86_64                                                                                            178/282 
  Running scriptlet: at-3.2.5-13.el10_0.x86_64                                                                                            178/282 
  Cleanup          : libvirt-daemon-driver-storage-11.5.0-4.el10.x86_64                                                                   179/282 
  Cleanup          : glibc-devel-2.39-58.el10.x86_64                                                                                      180/282 
  Cleanup          : sssd-2.11.1-2.el10.x86_64                                                                                            181/282 
  Running scriptlet: tuned-2.26.0-1.el10.noarch                                                                                           182/282 
  Cleanup          : tuned-2.26.0-1.el10.noarch                                                                                           182/282 
  Running scriptlet: tuned-2.26.0-1.el10.noarch                                                                                           182/282 
  Cleanup          : vim-common-2:9.1.083-5.el10_0.1.x86_64                                                                               183/282 
  Cleanup          : openssl-devel-1:3.5.1-3.el10.x86_64                                                                                  184/282 
  Cleanup          : libvirt-client-qemu-11.5.0-4.el10.x86_64                                                                             185/282 
  Cleanup          : python3-urllib3-1.26.19-2.el10.noarch                                                                                186/282 
  Cleanup          : sos-4.10.0-4.el10_1.noarch                                                                                           187/282 
  Cleanup          : python3-nftables-1:1.1.1-5.el10.x86_64                                                                               188/282 
  Cleanup          : sssd-ipa-2.11.1-2.el10.x86_64                                                                                        189/282 
  Cleanup          : python3-perf-6.12.0-124.8.1.el10_1.x86_64                                                                            190/282 
  Cleanup          : sssd-ad-2.11.1-2.el10.x86_64                                                                                         191/282 
  Cleanup          : kernel-tools-6.12.0-124.8.1.el10_1.x86_64                                                                            192/282 
  Cleanup          : sssd-proxy-2.11.1-2.el10.x86_64                                                                                      193/282 
  Cleanup          : sssd-ldap-2.11.1-2.el10.x86_64                                                                                       194/282 
  Cleanup          : sssd-common-pac-2.11.1-2.el10.x86_64                                                                                 195/282 
  Cleanup          : bind-utils-32:9.18.33-5.el10.x86_64                                                                                  196/282 
  Cleanup          : bind-libs-32:9.18.33-5.el10.x86_64                                                                                   197/282 
  Cleanup          : libuv-1:1.51.0-1.el10.x86_64                                                                                         198/282 
  Running scriptlet: subscription-manager-1.30.10-1.el10.x86_64                                                                           199/282 
  Cleanup          : subscription-manager-1.30.10-1.el10.x86_64                                                                           199/282 
  Running scriptlet: subscription-manager-1.30.10-1.el10.x86_64                                                                           199/282 
  Cleanup          : sssd-krb5-2.11.1-2.el10.x86_64                                                                                       200/282 
  Cleanup          : sssd-krb5-common-2.11.1-2.el10.x86_64                                                                                201/282 
  Running scriptlet: sssd-common-2.11.1-2.el10.x86_64                                                                                     202/282 
  Cleanup          : sssd-common-2.11.1-2.el10.x86_64                                                                                     202/282 
  Running scriptlet: sssd-common-2.11.1-2.el10.x86_64                                                                                     202/282 
  Running scriptlet: sssd-client-2.11.1-2.el10.x86_64                                                                                     203/282 
  Cleanup          : sssd-client-2.11.1-2.el10.x86_64                                                                                     203/282 
  Cleanup          : libsss_nss_idmap-2.11.1-2.el10.x86_64                                                                                204/282 
  Cleanup          : sssd-nfs-idmap-2.11.1-2.el10.x86_64                                                                                  205/282 
  Cleanup          : libdnf-plugin-subscription-manager-1.30.10-1.el10.x86_64                                                             206/282 
  Cleanup          : libvirt-daemon-plugin-lockd-11.5.0-4.el10.x86_64                                                                     207/282 
  Running scriptlet: libvirt-daemon-lock-11.5.0-4.el10.x86_64                                                                             208/282 
  Cleanup          : libvirt-daemon-lock-11.5.0-4.el10.x86_64                                                                             208/282 
  Cleanup          : python3-librepo-1.18.0-5.el10.x86_64                                                                                 209/282 
  Cleanup          : librepo-1.18.0-5.el10.x86_64                                                                                         210/282 
  Cleanup          : libvirt-daemon-driver-storage-iscsi-11.5.0-4.el10.x86_64                                                             211/282 
  Cleanup          : libvirt-daemon-driver-storage-logical-11.5.0-4.el10.x86_64                                                           212/282 
  Cleanup          : libvirt-daemon-driver-storage-scsi-11.5.0-4.el10.x86_64                                                              213/282 
  Cleanup          : libpng-2:1.6.40-8.el10.x86_64                                                                                        214/282 
  Cleanup          : libsss_certmap-2.11.1-2.el10.x86_64                                                                                  215/282 
  Cleanup          : python3-subscription-manager-rhsm-1.30.10-1.el10.x86_64                                                              216/282 
  Cleanup          : libvirt-daemon-driver-storage-disk-11.5.0-4.el10.x86_64                                                              217/282 
  Cleanup          : libvirt-daemon-driver-storage-mpath-11.5.0-4.el10.x86_64                                                             218/282 
  Cleanup          : libvirt-daemon-driver-storage-rbd-11.5.0-4.el10.x86_64                                                               219/282 
  Running scriptlet: libvirt-daemon-driver-storage-core-11.5.0-4.el10.x86_64                                                              220/282 
  Cleanup          : libvirt-daemon-driver-storage-core-11.5.0-4.el10.x86_64                                                              220/282 
  Cleanup          : fprintd-pam-1.94.5-1.el10.x86_64                                                                                     221/282 
  Running scriptlet: fprintd-pam-1.94.5-1.el10.x86_64                                                                                     221/282 
  Cleanup          : fprintd-1.94.5-1.el10.x86_64                                                                                         222/282 
  Cleanup          : libfprint-1.94.9-1.el10.x86_64                                                                                       223/282 
  Cleanup          : kpartx-0.9.9-12.el10_1.x86_64                                                                                        224/282 
  Running scriptlet: realmd-0.17.1-12.el10.x86_64                                                                                         225/282 
  Cleanup          : realmd-0.17.1-12.el10.x86_64                                                                                         225/282 
  Running scriptlet: realmd-0.17.1-12.el10.x86_64                                                                                         225/282 
  Cleanup          : python3-cloud-what-1.30.10-1.el10.x86_64                                                                             226/282 
  Cleanup          : amd-gpu-firmware-20250812-19.el10.noarch                                                                             227/282 
  Cleanup          : amd-ucode-firmware-20250812-19.el10.noarch                                                                           228/282 
  Cleanup          : atheros-firmware-20250812-19.el10.noarch                                                                             229/282 
  Cleanup          : brcmfmac-firmware-20250812-19.el10.noarch                                                                            230/282 
  Cleanup          : cirrus-audio-firmware-20250812-19.el10.noarch                                                                        231/282 
  Cleanup          : intel-audio-firmware-20250812-19.el10.noarch                                                                         232/282 
  Cleanup          : intel-gpu-firmware-20250812-19.el10.noarch                                                                           233/282 
  Cleanup          : mt7xxx-firmware-20250812-19.el10.noarch                                                                              234/282 
  Cleanup          : nvidia-gpu-firmware-20250812-19.el10.noarch                                                                          235/282 
  Cleanup          : nxpwireless-firmware-20250812-19.el10.noarch                                                                         236/282 
  Cleanup          : realtek-firmware-20250812-19.el10.noarch                                                                             237/282 
  Cleanup          : tiwilink-firmware-20250812-19.el10.noarch                                                                            238/282 
  Cleanup          : libvirt-daemon-config-network-11.5.0-4.el10.x86_64                                                                   239/282 
  Cleanup          : libvirt-daemon-config-nwfilter-11.5.0-4.el10.x86_64                                                                  240/282 
  Cleanup          : iwlwifi-mvm-firmware-20250812-19.el10.noarch                                                                         241/282 
  Cleanup          : iwlwifi-dvm-firmware-20250812-19.el10.noarch                                                                         242/282 
  Cleanup          : linux-firmware-whence-20250812-19.el10.noarch                                                                        243/282 
  Cleanup          : bind-license-32:9.18.33-5.el10.noarch                                                                                244/282 
  Cleanup          : vim-data-2:9.1.083-5.el10_0.1.noarch                                                                                 245/282 
  Cleanup          : vim-filesystem-2:9.1.083-5.el10_0.1.noarch                                                                           246/282 
  Cleanup          : kernel-headers-6.12.0-124.8.1.el10_1.x86_64                                                                          247/282 
  Cleanup          : passt-selinux-0^20250512.g8ec1341-2.el10.noarch                                                                      248/282 
  Running scriptlet: passt-selinux-0^20250512.g8ec1341-2.el10.noarch                                                                      248/282 
  Cleanup          : mesa-filesystem-25.0.7-3.el10.x86_64                                                                                 249/282 
  Cleanup          : cmake-filesystem-3.30.5-3.el10.x86_64                                                                                250/282 
  Cleanup          : kernel-modules-extra-matched-6.12.0-124.8.1.el10_1.x86_64                                                            251/282 
  Running scriptlet: microcode_ctl-4:20250812-1.el10.noarch                                                                               252/282 
  Cleanup          : microcode_ctl-4:20250812-1.el10.noarch                                                                               252/282 
  Running scriptlet: microcode_ctl-4:20250812-1.el10.noarch                                                                               252/282 
  Running scriptlet: man-pages-6.06-8.el10_0.noarch                                                                                       253/282 
  Cleanup          : man-pages-6.06-8.el10_0.noarch                                                                                       253/282 
  Running scriptlet: man-pages-6.06-8.el10_0.noarch                                                                                       253/282 
  Cleanup          : redhat-release-eula-10.1-16.el10.x86_64                                                                              254/282 
  Running scriptlet: libvirt-daemon-driver-network-11.5.0-4.el10.x86_64                                                                   255/282 
  Cleanup          : libvirt-daemon-driver-network-11.5.0-4.el10.x86_64                                                                   255/282 
  Running scriptlet: libvirt-daemon-driver-network-11.5.0-4.el10.x86_64                                                                   255/282 
  Running scriptlet: libvirt-daemon-driver-nwfilter-11.5.0-4.el10.x86_64                                                                  256/282 
  Cleanup          : libvirt-daemon-driver-nwfilter-11.5.0-4.el10.x86_64                                                                  256/282 
  Running scriptlet: libvirt-daemon-common-11.5.0-4.el10.x86_64                                                                           257/282 
  Cleanup          : libvirt-daemon-common-11.5.0-4.el10.x86_64                                                                           257/282 
  Cleanup          : libvirt-client-11.5.0-4.el10.x86_64                                                                                  258/282 
  Cleanup          : libvirt-libs-11.5.0-4.el10.x86_64                                                                                    259/282 
  Cleanup          : glib2-2.80.4-4.el10_0.7.x86_64                                                                                       260/282 
  Running scriptlet: nftables-1:1.1.1-5.el10.x86_64                                                                                       261/282 
  Cleanup          : nftables-1:1.1.1-5.el10.x86_64                                                                                       261/282 
  Running scriptlet: nftables-1:1.1.1-5.el10.x86_64                                                                                       261/282 
  Cleanup          : libssh-0.11.1-4.el10_0.x86_64                                                                                        262/282 
  Cleanup          : libsss_sudo-2.11.1-2.el10.x86_64                                                                                     263/282 
  Cleanup          : xxd-2:9.1.083-5.el10_0.1.x86_64                                                                                      264/282 
  Cleanup          : which-2.21-44.el10.x86_64                                                                                            265/282 
  Cleanup          : libbrotli-1.1.0-6.el10.x86_64                                                                                        266/282 
  Cleanup          : libnftnl-1.2.8-3.el10.x86_64                                                                                         267/282 
  Cleanup          : python3-3.12.11-3.el10.x86_64                                                                                        268/282 
  Cleanup          : python3-libs-3.12.11-3.el10.x86_64                                                                                   269/282 
  Cleanup          : openssl-libs-1:3.5.1-3.el10.x86_64                                                                                   270/282 
  Cleanup          : expat-2.7.1-1.el10_0.3.x86_64                                                                                        271/282 
  Cleanup          : libsss_idmap-2.11.1-2.el10.x86_64                                                                                    272/282 
  Cleanup          : kernel-tools-libs-6.12.0-124.8.1.el10_1.x86_64                                                                       273/282 
  Running scriptlet: kernel-tools-libs-6.12.0-124.8.1.el10_1.x86_64                                                                       273/282 
  Cleanup          : libipa_hbac-2.11.1-2.el10.x86_64                                                                                     274/282 
  Cleanup          : ca-certificates-2024.2.69_v8.0.303-102.3.el10.noarch                                                                 275/282 
  Cleanup          : python-unversioned-command-3.12.11-3.el10.noarch                                                                     276/282 
  Cleanup          : libssh-config-0.11.1-4.el10_0.noarch                                                                                 277/282 
  Cleanup          : glibc-2.39-58.el10.x86_64                                                                                            278/282 
  Cleanup          : glibc-langpack-en-2.39-58.el10.x86_64                                                                                279/282 
  Cleanup          : glibc-gconv-extra-2.39-58.el10.x86_64                                                                                280/282 
  Running scriptlet: glibc-gconv-extra-2.39-58.el10.x86_64                                                                                280/282 
  Cleanup          : glibc-common-2.39-58.el10.x86_64                                                                                     281/282 
  Cleanup          : tzdata-2025b-2.el10.noarch                                                                                           282/282 
  Running scriptlet: passt-selinux-0^20250512.g8ec1341-4.el10_1.noarch                                                                    282/282 
  Running scriptlet: ca-certificates-2025.2.80_v9.0.305-102.el10_1.noarch                                                                 282/282 
  Running scriptlet: subscription-manager-1.30.10.1-1.el10_1.x86_64                                                                       282/282 
  Running scriptlet: sssd-common-2.11.1-2.el10_1.1.x86_64                                                                                 282/282 
  Running scriptlet: kernel-modules-core-6.12.0-124.29.1.el10_1.x86_64                                                                    282/282 
  Running scriptlet: kernel-core-6.12.0-124.29.1.el10_1.x86_64                                                                            282/282 
Generating grub configuration file ...
Adding boot menu entry for UEFI Firmware Settings ...
done

  Running scriptlet: kernel-modules-6.12.0-124.29.1.el10_1.x86_64                                                                         282/282 
  Running scriptlet: libvirt-daemon-common-11.5.0-4.2.el10_1.x86_64                                                                       282/282 
  Running scriptlet: libvirt-daemon-driver-storage-core-11.5.0-4.2.el10_1.x86_64                                                          282/282 
  Running scriptlet: libvirt-daemon-driver-network-11.5.0-4.2.el10_1.x86_64                                                               282/282 
  Running scriptlet: libvirt-daemon-driver-nwfilter-11.5.0-4.2.el10_1.x86_64                                                              282/282 
  Running scriptlet: libvirt-daemon-lock-11.5.0-4.2.el10_1.x86_64                                                                         282/282 
  Running scriptlet: libvirt-daemon-log-11.5.0-4.2.el10_1.x86_64                                                                          282/282 
  Running scriptlet: libvirt-daemon-driver-qemu-11.5.0-4.2.el10_1.x86_64                                                                  282/282 
  Running scriptlet: libvirt-daemon-config-nwfilter-11.5.0-4.2.el10_1.x86_64                                                              282/282 
  Running scriptlet: libvirt-daemon-config-network-11.5.0-4.2.el10_1.x86_64                                                               282/282 
  Running scriptlet: libvirt-daemon-driver-interface-11.5.0-4.2.el10_1.x86_64                                                             282/282 
  Running scriptlet: libvirt-daemon-driver-nodedev-11.5.0-4.2.el10_1.x86_64                                                               282/282 
  Running scriptlet: libvirt-daemon-driver-secret-11.5.0-4.2.el10_1.x86_64                                                                282/282 
  Running scriptlet: libvirt-daemon-proxy-11.5.0-4.2.el10_1.x86_64                                                                        282/282 
  Running scriptlet: libvirt-daemon-11.5.0-4.2.el10_1.x86_64                                                                              282/282 
  Running scriptlet: tuned-2.26.0-1.el10_1.1.noarch                                                                                       282/282 
  Running scriptlet: microcode_ctl-4:20250812-1.20251111.1.el10_1.noarch                                                                  282/282 
  Running scriptlet: tzdata-2025b-2.el10.noarch                                                                                           282/282 
Failed to connect to user scope bus via machine transport: No medium found

Installed products updated.

Upgraded:
  NetworkManager-1:1.54.0-2.el10_1.x86_64                                NetworkManager-libnm-1:1.54.0-2.el10_1.x86_64                           
  NetworkManager-tui-1:1.54.0-2.el10_1.x86_64                            amd-gpu-firmware-20251111-19.1.el10_1.noarch                            
  amd-ucode-firmware-20251111-19.1.el10_1.noarch                         at-3.2.5-14.el10_1.x86_64                                               
  atheros-firmware-20251111-19.1.el10_1.noarch                           bind-libs-32:9.18.33-10.el10_1.2.x86_64                                 
  bind-license-32:9.18.33-10.el10_1.2.noarch                             bind-utils-32:9.18.33-10.el10_1.2.x86_64                                
  binutils-2.41-58.el10_1.2.x86_64                                       binutils-gold-2.41-58.el10_1.2.x86_64                                   
  brcmfmac-firmware-20251111-19.1.el10_1.noarch                          ca-certificates-2025.2.80_v9.0.305-102.el10_1.noarch                    
  cirrus-audio-firmware-20251111-19.1.el10_1.noarch                      cmake-filesystem-3.30.5-3.el10_0.x86_64                                 
  device-mapper-multipath-libs-0.9.9-12.el10_1.1.x86_64                  expat-2.7.1-1.el10_1.3.x86_64                                           
  fprintd-1.94.5-1.el10_0.x86_64                                         fprintd-pam-1.94.5-1.el10_0.x86_64                                      
  glib2-2.80.4-10.el10_1.12.x86_64                                       glibc-2.39-58.el10_1.7.x86_64                                           
  glibc-common-2.39-58.el10_1.7.x86_64                                   glibc-devel-2.39-58.el10_1.7.x86_64                                     
  glibc-gconv-extra-2.39-58.el10_1.7.x86_64                              glibc-langpack-en-2.39-58.el10_1.7.x86_64                               
  gnupg2-2.4.5-3.el10_1.x86_64                                           gnupg2-smime-2.4.5-3.el10_1.x86_64                                      
  intel-audio-firmware-20251111-19.1.el10_1.noarch                       intel-gpu-firmware-20251111-19.1.el10_1.noarch                          
  iwlwifi-dvm-firmware-20251111-19.1.el10_1.noarch                       iwlwifi-mvm-firmware-20251111-19.1.el10_1.noarch                        
  kernel-headers-6.12.0-124.29.1.el10_1.x86_64                           kernel-modules-extra-matched-6.12.0-124.29.1.el10_1.x86_64              
  kernel-tools-6.12.0-124.29.1.el10_1.x86_64                             kernel-tools-libs-6.12.0-124.29.1.el10_1.x86_64                         
  kpartx-0.9.9-12.el10_1.1.x86_64                                        libbrotli-1.1.0-7.el10_1.x86_64                                         
  libdnf-plugin-subscription-manager-1.30.10.1-1.el10_1.x86_64           libfprint-1.94.9-1.el10_0.x86_64                                        
  libipa_hbac-2.11.1-2.el10_1.1.x86_64                                   libnftnl-1.2.8-4.el10_1.x86_64                                          
  libpng-2:1.6.40-8.el10_1.1.x86_64                                      librepo-1.18.0-6.el10_1.x86_64                                          
  libssh-0.11.1-5.el10_1.x86_64                                          libssh-config-0.11.1-5.el10_1.noarch                                    
  libsss_certmap-2.11.1-2.el10_1.1.x86_64                                libsss_idmap-2.11.1-2.el10_1.1.x86_64                                   
  libsss_nss_idmap-2.11.1-2.el10_1.1.x86_64                              libsss_sudo-2.11.1-2.el10_1.1.x86_64                                    
  libtpms-0.9.6-11.el10_0.x86_64                                         libuv-1:1.51.0-1.el10_0.x86_64                                          
  libvirt-11.5.0-4.2.el10_1.x86_64                                       libvirt-client-11.5.0-4.2.el10_1.x86_64                                 
  libvirt-client-qemu-11.5.0-4.2.el10_1.x86_64                           libvirt-daemon-11.5.0-4.2.el10_1.x86_64                                 
  libvirt-daemon-common-11.5.0-4.2.el10_1.x86_64                         libvirt-daemon-config-network-11.5.0-4.2.el10_1.x86_64                  
  libvirt-daemon-config-nwfilter-11.5.0-4.2.el10_1.x86_64                libvirt-daemon-driver-interface-11.5.0-4.2.el10_1.x86_64                
  libvirt-daemon-driver-network-11.5.0-4.2.el10_1.x86_64                 libvirt-daemon-driver-nodedev-11.5.0-4.2.el10_1.x86_64                  
  libvirt-daemon-driver-nwfilter-11.5.0-4.2.el10_1.x86_64                libvirt-daemon-driver-qemu-11.5.0-4.2.el10_1.x86_64                     
  libvirt-daemon-driver-secret-11.5.0-4.2.el10_1.x86_64                  libvirt-daemon-driver-storage-11.5.0-4.2.el10_1.x86_64                  
  libvirt-daemon-driver-storage-core-11.5.0-4.2.el10_1.x86_64            libvirt-daemon-driver-storage-disk-11.5.0-4.2.el10_1.x86_64             
  libvirt-daemon-driver-storage-iscsi-11.5.0-4.2.el10_1.x86_64           libvirt-daemon-driver-storage-logical-11.5.0-4.2.el10_1.x86_64          
  libvirt-daemon-driver-storage-mpath-11.5.0-4.2.el10_1.x86_64           libvirt-daemon-driver-storage-rbd-11.5.0-4.2.el10_1.x86_64              
  libvirt-daemon-driver-storage-scsi-11.5.0-4.2.el10_1.x86_64            libvirt-daemon-lock-11.5.0-4.2.el10_1.x86_64                            
  libvirt-daemon-log-11.5.0-4.2.el10_1.x86_64                            libvirt-daemon-plugin-lockd-11.5.0-4.2.el10_1.x86_64                    
  libvirt-daemon-proxy-11.5.0-4.2.el10_1.x86_64                          libvirt-libs-11.5.0-4.2.el10_1.x86_64                                   
  linux-firmware-20251111-19.1.el10_1.noarch                             linux-firmware-whence-20251111-19.1.el10_1.noarch                       
  man-pages-6.06-12.el10_1.noarch                                        mesa-dri-drivers-25.0.7-6.el10_1.x86_64                                 
  mesa-filesystem-25.0.7-6.el10_1.x86_64                                 mesa-libEGL-25.0.7-6.el10_1.x86_64                                      
  mesa-libGL-25.0.7-6.el10_1.x86_64                                      mesa-libgbm-25.0.7-6.el10_1.x86_64                                      
  microcode_ctl-4:20250812-1.20251111.1.el10_1.noarch                    mt7xxx-firmware-20251111-19.1.el10_1.noarch                             
  nftables-1:1.1.1-6.el10_1.x86_64                                       nvidia-gpu-firmware-20251111-19.1.el10_1.noarch                         
  nxpwireless-firmware-20251111-19.1.el10_1.noarch                       openssh-9.9p1-12.el10_1.x86_64                                          
  openssh-clients-9.9p1-12.el10_1.x86_64                                 openssh-server-9.9p1-12.el10_1.x86_64                                   
  openssl-1:3.5.1-7.el10_1.x86_64                                        openssl-devel-1:3.5.1-7.el10_1.x86_64                                   
  openssl-libs-1:3.5.1-7.el10_1.x86_64                                   passt-0^20250512.g8ec1341-4.el10_1.x86_64                               
  passt-selinux-0^20250512.g8ec1341-4.el10_1.noarch                      python-unversioned-command-3.12.12-1.el10_1.noarch                      
  python3-3.12.12-1.el10_1.x86_64                                        python3-cloud-what-1.30.10.1-1.el10_1.x86_64                            
  python3-librepo-1.18.0-6.el10_1.x86_64                                 python3-libs-3.12.12-1.el10_1.x86_64                                    
  python3-nftables-1:1.1.1-6.el10_1.x86_64                               python3-perf-6.12.0-124.29.1.el10_1.x86_64                              
  python3-subscription-manager-rhsm-1.30.10.1-1.el10_1.x86_64            python3-urllib3-1.26.19-2.el10_1.1.noarch                               
  realmd-0.17.1-13.el10_1.x86_64                                         realtek-firmware-20251111-19.1.el10_1.noarch                            
  redhat-release-eula-10.1-18.el10.x86_64                                sos-4.10.1-2.el10.noarch                                                
  sssd-2.11.1-2.el10_1.1.x86_64                                          sssd-ad-2.11.1-2.el10_1.1.x86_64                                        
  sssd-client-2.11.1-2.el10_1.1.x86_64                                   sssd-common-2.11.1-2.el10_1.1.x86_64                                    
  sssd-common-pac-2.11.1-2.el10_1.1.x86_64                               sssd-ipa-2.11.1-2.el10_1.1.x86_64                                       
  sssd-kcm-2.11.1-2.el10_1.1.x86_64                                      sssd-krb5-2.11.1-2.el10_1.1.x86_64                                      
  sssd-krb5-common-2.11.1-2.el10_1.1.x86_64                              sssd-ldap-2.11.1-2.el10_1.1.x86_64                                      
  sssd-nfs-idmap-2.11.1-2.el10_1.1.x86_64                                sssd-proxy-2.11.1-2.el10_1.1.x86_64                                     
  subscription-manager-1.30.10.1-1.el10_1.x86_64                         tar-2:1.35-9.el10_1.x86_64                                              
  tiwilink-firmware-20251111-19.1.el10_1.noarch                          tuned-2.26.0-1.el10_1.1.noarch                                          
  tzdata-2025c-1.el10.noarch                                             unbound-anchor-1.20.0-15.el10_1.x86_64                                  
  unbound-libs-1.20.0-15.el10_1.x86_64                                   vim-common-2:9.1.083-6.el10_1.x86_64                                    
  vim-data-2:9.1.083-6.el10_1.noarch                                     vim-enhanced-2:9.1.083-6.el10_1.x86_64                                  
  vim-filesystem-2:9.1.083-6.el10_1.noarch                               vim-minimal-2:9.1.083-6.el10_1.x86_64                                   
  which-2.21-44.el10_0.x86_64                                            xxd-2:9.1.083-6.el10_1.x86_64                                           
Installed:
  kernel-6.12.0-124.29.1.el10_1.x86_64                                    kernel-core-6.12.0-124.29.1.el10_1.x86_64                               
  kernel-devel-6.12.0-124.29.1.el10_1.x86_64                              kernel-modules-6.12.0-124.29.1.el10_1.x86_64                            
  kernel-modules-core-6.12.0-124.29.1.el10_1.x86_64                       kernel-modules-extra-6.12.0-124.29.1.el10_1.x86_64                      

Complete!
```

There, the update ran successfully!

This is just a guess, I am not sure if I will have time to check the various packages, but seems there is a dependency missing to force the redhat-release package to get the latest GPG keys before other packages are updated.
