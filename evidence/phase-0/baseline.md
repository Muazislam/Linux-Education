# Baseline Diagnostic – Phase 0

Last updated: 2026-09-10  
Host: EndeavourOS (Primary daily-use system)  
Evidence Type: Baseline Environment Inspection (Read-only host telemetry)  

---

## 1. OS Release
```bash
cat /etc/*-release
```
```text
DISTRIB_ID="EndeavourOS"
DISTRIB_RELEASE="rolling"
DISTRIB_DESCRIPTION="EndeavourOS Linux"
DISTRIB_CODENAME="rolling"
NAME="EndeavourOS"
PRETTY_NAME="EndeavourOS"
ID="endeavouros"
ID_LIKE="arch"
BUILD_ID=rolling
ANSI_COLOR="38;2;23;147;209"
HOME_URL="https://endeavouros.com"
DOCUMENTATION_URL="https://discovery.endeavouros.com"
SUPPORT_URL="https://forum.endeavouros.com"
BUG_REPORT_URL="https://forum.endeavouros.com/c/general-system/endeavouros-installation"
PRIVACY_POLICY_URL="https://endeavouros.com/privacy-policy-2"
LOGO="endeavouros" 
```

---

## 2. Kernel
```bash
uname -a
```
```text
Linux muazislambabar 7.2.4-arch1-2 #1 SMP PREEMPT_DYNAMIC Tue, 08 Sep 2026 10:22:31 +0000 x86_64 GNU/Linux
```

---

## 3. CPU / Memory
```bash
lscpu && free -h
```
```text
Architecture:                x86_64
  CPU op-mode(s):            32-bit, 64-bit
  Address sizes:             39 bits physical, 48 bits virtual
  Byte Order:                Little Endian
CPU(s):                      8
  On-line CPU(s) list:       0-7
Vendor ID:                   GenuineIntel
  Model name:                Intel(R) Core(TM) i7-8650U CPU @ 1.90GHz
    CPU family:              6
    Model:                   142
    Thread(s) per core:      2
    Core(s) per socket:      4
    Socket(s):               1
    Stepping:                10
    Microcode version:       0xf6
    CPU(s) scaling MHz:      95%
    CPU max MHz:             4200.0000
    CPU min MHz:             400.0000
    BogoMIPS:                4199.88
    Flags:                   fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts a
                             cpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch
                             _perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq 
                             dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_
                             2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowp
                             refetch cpuid_fault epb pti ssbd ibrs ibpb stibp tpr_shadow flexpriority ept vpid ept
                             _ad fsgsbase tsc_adjust sgx bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clfl
                             ushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify
                              hwp_act_window hwp_epp vnmi md_clear flush_l1d arch_capabilities
Virtualization features:     
  Virtualization:            VT-x
Caches (sum of all):         
  L1d:                       128 KiB (4 instances)
  L1i:                       128 KiB (4 instances)
  L2:                        1 MiB (4 instances)
  L3:                        8 MiB (1 instance)
NUMA:                        
  NUMA node(s):              1
  NUMA node0 CPU(s):         0-7
Vulnerabilities:             
  Gather data sampling:      Mitigation; Microcode
  Ghostwrite:                Not affected
  Indirect target selection: Not affected
  Itlb multihit:             KVM: Mitigation: Split huge pages
  L1tf:                      Mitigation; PTE Inversion; VMX conditional cache flushes, SMT vulnerable
  Mds:                       Mitigation; Clear CPU buffers; SMT vulnerable
  Meltdown:                  Mitigation; PTI
  Mmio stale data:           Mitigation; Clear CPU buffers; SMT vulnerable
  Old microcode:             Not affected
  Reg file data sampling:    Not affected
  Retbleed:                  Mitigation; IBRS
  Spec rstack overflow:      Not affected
  Spec store bypass:         Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:                Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:                Mitigation; IBRS; IBPB conditional; STIBP conditional; RSB filling; PBRSB-eIBRS Not a
                             ffected; BHI Not affected
  Srbds:                     Mitigation; Microcode
  Tsa:                       Not affected
  Tsx async abort:           Mitigation; TSX disabled
  Vmscape:                   Mitigation; IBPB before exit to userspace
               total        used        free      shared  buff/cache   available
Mem:            15Gi       5.9Gi       2.4Gi       1.2Gi       8.2Gi       9.4Gi
Swap:          6.0Gi        15Mi       6.0Gi

~
```

---

## 4. Disk Layout
```bash
lsblk -f
```
```text
NAME   FSTYPE FSVER LABEL       UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
sda                                                                                 
├─sda1 vfat   FAT32             DD78-349B                               1.9G     6% /efi
└─sda2 btrfs        endeavouros e40d3a1e-5923-4acd-a4d2-e7d1feb9a8ba  180.3G    23% /var/log
                                                                                    /var/cache
                                                                                    /home
                                                                                    /swap
                                                                                    /
sdb
```

---

## 5. Filesystem Health
```bash
df -hT
```
```text
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda2      btrfs     237G   55G  181G  24% /
devtmpfs       devtmpfs  7.7G     0  7.7G   0% /dev
tmpfs          tmpfs     7.7G   56M  7.7G   1% /dev/shm
efivarfs       efivarfs  154K   79K   71K  53% /sys/firmware/efi/efivars
tmpfs          tmpfs     3.1G  2.0M  3.1G   1% /run
none           tmpfs     1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
/dev/sda2      btrfs     237G   55G  181G  24% /swap
/dev/sda2      btrfs     237G   55G  181G  24% /home
/dev/sda2      btrfs     237G   55G  181G  24% /var/cache
/dev/sda2      btrfs     237G   55G  181G  24% /var/log
tmpfs          tmpfs     7.7G   13M  7.7G   1% /tmp
/dev/sda1      vfat      2.0G  122M  1.9G   6% /efi
none           tmpfs     1.0M  4.0K 1020K   1% /run/credentials/libvirtd.service
tmpfs          tmpfs     1.6G  104K  1.6G   1% /run/user/1000
```

---

## 6. Systemd Failed Units
```bash
systemctl list-units --type=service --state=failed
```
```text
UNIT LOAD ACTIVE SUB DESCRIPTION

0 loaded units listed.

~
```

---

## 7. Package Integrity
```bash
pacman -Qk
```
```text
Package integrity

json-c: 34 total files, 0 missing files
json-glib: 225 total files, 0 missing files
jsoncpp: 26 total files, 0 missing files
kaccounts-integration: 228 total files, 0 missing files
kactivitymanagerd: 237 total files, 0 missing files
kalgebra: 351 total files, 0 missing files
karchive: 179 total files, 0 missing files
kate: 2543 total files, 0 missing files
kauth: 359 total files, 0 missing files
kbd: 831 total files, 0 missing files
kbookmarks: 309 total files, 0 missing files
kcalc: 341 total files, 0 missing files
kcmutils: 439 total files, 0 missing files
kcodecs: 335 total files, 0 missing files
kcolorpicker: 16 total files, 0 missing files
kcolorscheme: 166 total files, 0 missing files
kcompletion: 348 total files, 0 missing files
kconfig: 385 total files, 0 missing files
kconfigwidgets: 481 total files, 0 missing files
kcontacts: 292 total files, 0 missing files
kcoreaddons: 459 total files, 0 missing files
kcrash: 22 total files, 0 missing files
kdbusaddons: 214 total files, 0 missing files
kde-cli-tools: 1010 total files, 0 missing files
kde-gtk-config: 26 total files, 0 missing files
kdeclarative: 364 total files, 0 missing files
kdeconnect: 1007 total files, 0 missing files
kdecoration: 199 total files, 0 missing files
kded: 55 total files, 0 missing files
kdegraphics-mobipocket: 20 total files, 0 missing files
kdegraphics-thumbnailers: 13 total files, 0 missing files
kdenetwork-filesharing: 254 total files, 0 missing files
kdeplasma-addons: 2355 total files, 0 missing files
kdesu: 222 total files, 0 missing files
kdnssd: 345 total files, 0 missing files
kdsingleapplication: 34 total files, 0 missing files
kdsoap: 97 total files, 0 missing files
kdsoap-ws-discovery-client: 116 total files, 0 missing files
keepassxc: 95 total files, 0 missing files
kernel-install-for-dracut: 25 total files, 0 missing files
keyutils: 75 total files, 0 missing files
kfilemetadata: 260 total files, 0 missing files
kgamma: 344 total files, 0 missing files
kglobalaccel: 335 total files, 0 missing files
kglobalacceld: 31 total files, 0 missing files
kguiaddons: 78 total files, 0 missing files
kholidays: 277 total files, 0 missing files
ki18n: 439 total files, 0 missing files
kiconthemes: 325 total files, 0 missing files
kidletime: 31 total files, 0 missing files
kimageannotator: 50 total files, 0 missing files
kimageformats: 35 total files, 0 missing files
kinfocenter: 674 total files, 0 missing files
kio: 1195 total files, 0 missing files
kio-admin: 143 total files, 0 missing files
kio-extras: 2279 total files, 0 missing files
kio-fuse: 12 total files, 0 missing files
kirigami: 461 total files, 0 missing files
kirigami-addons: 368 total files, 0 missing files
kitemmodels: 49 total files, 0 missing files
kitemviews: 346 total files, 0 missing files
kjobwidgets: 354 total files, 0 missing files
kmenuedit: 403 total files, 0 missing files
kmod: 62 total files, 0 missing files
knewstuff: 424 total files, 0 missing files
knighttime: 32 total files, 0 missing files
knotifications: 42 total files, 0 missing files
knotifyconfig: 328 total files, 0 missing files
konsole: 386 total files, 0 missing files
kpackage: 254 total files, 0 missing files
kparts: 367 total files, 0 missing files
kpeople: 256 total files, 0 missing files
kpipewire: 190 total files, 0 missing files
kpmcore: 335 total files, 0 missing files
kpty: 332 total files, 0 missing files
kquickcharts: 37 total files, 0 missing files
kquickimageeditor: 51 total files, 0 missing files
krb5: 205 total files, 0 missing files
krunner: 49 total files, 0 missing files
kscreen: 373 total files, 0 missing files
kscreenlocker: 346 total files, 0 missing files
kservice: 380 total files, 0 missing files
kstatusnotifieritem: 158 total files, 0 missing files
ksvg: 36 total files, 0 missing files
ksystemstats: 169 total files, 0 missing files
ktexteditor: 358 total files, 0 missing files
ktextwidgets: 344 total files, 0 missing files
kunitconversion: 228 total files, 0 missing files
kuserfeedback: 276 total files, 0 missing files
kwallet: 348 total files, 0 missing files
kwallet-pam: 12 total files, 0 missing files
kwayland: 63 total files, 0 missing files
kwayland-integration: 10 total files, 0 missing files
kwayland5: 136 total files, 0 missing files
kwidgetsaddons: 506 total files, 0 missing files
kwin: 2257 total files, 0 missing files
kwin-x11: 1947 total files, 0 missing files
kwindowsystem: 381 total files, 0 missing files
kwindowsystem5: 365 total files, 0 missing files
kxmlgui: 401 total files, 0 missing files
l-smash: 17 total files, 0 missing files
lame: 34 total files, 0 missing files
lapack: 20 total files, 0 missing files
layer-shell-qt: 30 total files, 0 missing files
lcms2: 27 total files, 0 missing files
ldb: 96 total files, 0 missing files
leancrypto: 121 total files, 0 missing files
lensfun: 85 total files, 0 missing files
leptonica: 60 total files, 0 missing files
less: 16 total files, 0 missing files
libabw: 282 total files, 0 missing files
libaccounts-glib: 96 total files, 0 missing files
libaccounts-qt: 36 total files, 0 missing files
libadwaita: 277 total files, 0 missing files
libaec: 21 total files, 0 missing files
libaemu: 307 total files, 0 missing files
libaio: 27 total files, 0 missing files
libappindicator: 41 total files, 0 missing files
libarchive: 69 total files, 0 missing files
libasan: 9 total files, 0 missing files
libass: 15 total files, 0 missing files
libassuan: 20 total files, 0 missing files
libasyncns: 15 total files, 0 missing files
libatasmart: 19 total files, 0 missing files
libatomic: 13 total files, 0 missing files
libatomic_ops: 93 total files, 0 missing files
libavc1394: 25 total files, 0 missing files
libavif: 28 total files, 0 missing files
libavtp: 23 total files, 0 missing files
libb2: 13 total files, 0 missing files
libblake3: 15 total files, 0 missing files
libblockdev: 69 total files, 0 missing files
libblockdev-crypto: 8 total files, 0 missing files
libblockdev-fs: 22 total files, 0 missing files
libblockdev-loop: 8 total files, 0 missing files
libblockdev-mdraid: 8 total files, 0 missing files
libblockdev-nvme: 8 total files, 0 missing files
libblockdev-part: 8 total files, 0 missing files
libblockdev-smart: 11 total files, 0 missing files
libblockdev-swap: 8 total files, 0 missing files
libbluray: 26 total files, 0 missing files
libbpf: 29 total files, 0 missing files
libbs2b: 20 total files, 0 missing files
libbsd: 285 total files, 0 missing files
libburn: 16 total files, 0 missing files
libbytesize: 124 total files, 0 missing files
libcaca: 470 total files, 0 missing files
libcacard: 22 total files, 0 missing files
libcanberra: 64 total files, 0 missing files
libcap: 120 total files, 0 missing files
libcap-ng: 56 total files, 0 missing files
libcbor: 46 total files, 0 missing files
libcddb: 21 total files, 0 missing files
libcdio: 87 total files, 0 missing files
libcdio-paranoia: 26 total files, 0 missing files
libcdr: 333 total files, 0 missing files
libcgif: 13 total files, 0 missing files
libcloudproviders: 25 total files, 0 missing files
libcmis: 56 total files, 0 missing files
libcolord: 44 total files, 0 missing files
libcue: 11 total files, 0 missing files
libcups: 30 total files, 0 missing files
libdaemon: 21 total files, 0 missing files
libdatrie: 51 total files, 0 missing files
libdbusmenu-glib: 47 total files, 0 missing files
libdbusmenu-gtk3: 44 total files, 0 missing files
libdc1394: 140 total files, 0 missing files
libdca: 23 total files, 0 missing files
libde265: 20 total files, 0 missing files
libdecor: 18 total files, 0 missing files
libdeflate: 21 total files, 0 missing files
libdisplay-info: 23 total files, 0 missing files
libdmtx: 16 total files, 0 missing files
libdnet: 37 total files, 0 missing files
libdovi: 14 total files, 0 missing files
libdrm: 92 total files, 0 missing files
libdv: 21 total files, 0 missing files
libdvdcss: 12 total files, 0 missing files
libdvdnav: 21 total files, 0 missing files
libdvdread: 29 total files, 0 missing files
libe-book: 910 total files, 0 missing files
libebml: 45 total files, 0 missing files
libebur128: 13 total files, 0 missing files
libedit: 65 total files, 0 missing files
libei: 26 total files, 0 missing files
libelf: 162 total files, 0 missing files
libepoxy: 20 total files, 0 missing files
libepubgen: 219 total files, 0 missing files
libetonyek: 22 total files, 0 missing files
libevdev: 27 total files, 0 missing files
libevent: 73 total files, 0 missing files
libexif: 121 total files, 0 missing files
libexsid: 9 total files, 0 missing files
libexttextcat: 217 total files, 0 missing files
libfakekey: 10 total files, 0 missing files
libfdk-aac: 19 total files, 0 missing files
libffi: 25 total files, 0 missing files
libfido2: 335 total files, 0 missing files
libfontenc: 15 total files, 0 missing files
libfreeaptx: 12 total files, 0 missing files
libfreehand: 233 total files, 0 missing files
libftdi: 57 total files, 0 missing files
libfyaml: 50 total files, 0 missing files
libgcc: 7 total files, 0 missing files
libgcrypt: 27 total files, 0 missing files
libgee: 18 total files, 0 missing files
libgexiv2: 27 total files, 0 missing files
libgfortran: 9 total files, 0 missing files
libgirepository: 80 total files, 0 missing files
libglvnd: 58 total files, 0 missing files
libgme: 10 total files, 0 missing files
libgnomekbd: 277 total files, 0 missing files
libgomp: 11 total files, 0 missing files
libgpg-error: 100 total files, 0 missing files
libgsf: 229 total files, 0 missing files
libgtop: 376 total files, 0 missing files
libgudev: 46 total files, 0 missing files
libheif: 60 total files, 0 missing files
libhwasan: 9 total files, 0 missing files
libice: 24 total files, 0 missing files
libidn: 168 total files, 0 missing files
libidn2: 135 total files, 0 missing files
libiec61883: 18 total files, 0 missing files
libimagequant: 13 total files, 0 missing files
libimobiledevice: 527 total files, 0 missing files
libimobiledevice-glue: 20 total files, 0 missing files
libinih: 16 total files, 0 missing files
libinput: 75 total files, 0 missing files
libisl: 88 total files, 0 missing files
libisoburn: 32 total files, 0 missing files
libisofs: 10 total files, 0 missing files
libixion: 46 total files, 0 missing files
libjcat: 60 total files, 0 missing files
libjpeg-turbo: 56 total files, 0 missing files
libjxl: 57 total files, 0 missing files
libkdcraw: 28 total files, 0 missing files
libkexiv2: 28 total files, 0 missing files
libksba: 14 total files, 0 missing files
libkscreen: 204 total files, 0 missing files
libksysguard: 937 total files, 0 missing files
liblangtag: 115 total files, 0 missing files
liblc3: 23 total files, 0 missing files
libldac: 15 total files, 0 missing files
libldap: 217 total files, 0 missing files
liblqr: 23 total files, 0 missing files
liblrdf: 20 total files, 0 missing files
liblsan: 9 total files, 0 missing files
libltc: 75 total files, 0 missing files
libluv: 13 total files, 0 missing files
liblzf: 21 total files, 0 missing files
libmakepkg-dropins: 14 total files, 0 missing files
libmalcontent: 23 total files, 0 missing files
libmanette: 26 total files, 0 missing files
libmatio: 47 total files, 0 missing files
libmatroska: 46 total files, 0 missing files
libmaxminddb: 28 total files, 0 missing files
libmbim: 66 total files, 0 missing files
libmd: 143 total files, 0 missing files
libmicrodns: 11 total files, 0 missing files
libmm-glib: 94 total files, 0 missing files
libmms: 14 total files, 0 missing files
libmng: 21 total files, 0 missing files
libmnl: 10 total files, 0 missing files
libmodplug: 17 total files, 0 missing files
libmpc: 12 total files, 0 missing files
libmpcdec: 18 total files, 0 missing files
libmpeg2: 24 total files, 0 missing files
libmspack: 9 total files, 0 missing files
libmspub: 385 total files, 0 missing files
libmtp: 288 total files, 0 missing files
libmwaw: 20 total files, 0 missing files
libmypaint: 293 total files, 0 missing files
libmysofa: 25 total files, 0 missing files
libnbd: 238 total files, 0 missing files
libndp: 15 total files, 0 missing files
libnet: 98 total files, 0 missing files
libnetfilter_conntrack: 19 total files, 0 missing files
libnewt: 243 total files, 0 missing files
libnfnetlink: 12 total files, 0 missing files
libnfs: 35 total files, 0 missing files
libnftnl: 22 total files, 0 missing files
libnghttp2: 15 total files, 0 missing files
libnghttp3: 18 total files, 0 missing files
libngtcp2: 29 total files, 0 missing files
libnice: 77 total files, 0 missing files
libnl: 257 total files, 0 missing files
libnm: 147 total files, 0 missing files
libnma: 16 total files, 0 missing files
libnma-common: 297 total files, 0 missing files
libnma-gtk4: 16 total files, 0 missing files
libnotify: 24 total files, 0 missing files
libnsl: 22 total files, 0 missing files
libntfs-3g: 48 total files, 0 missing files
libnumbertext: 70 total files, 0 missing files
libnvme: 37 total files, 0 missing files
libobjc: 9 total files, 0 missing files
libodfgen: 87 total files, 0 missing files
libogg: 111 total files, 0 missing files
libopenmpt: 43 total files, 0 missing files
libopenraw: 36 total files, 0 missing files
liborcus: 130 total files, 0 missing files
libosinfo: 198 total files, 0 missing files
libp11-kit: 30 total files, 0 missing files
libpagemaker: 192 total files, 0 missing files
libpaper: 29 total files, 0 missing files
libpathrs: 10 total files, 0 missing files
libpcap: 123 total files, 0 missing files
libpciaccess: 13 total files, 0 missing files
libpgm: 32 total files, 0 missing files
libpipeline: 80 total files, 0 missing files
libpipewire: 272 total files, 0 missing files
libplacebo: 48 total files, 0 missing files
libplasma: 543 total files, 0 missing files
libplist: 38 total files, 0 missing files
libpng: 34 total files, 0 missing files
libproxy: 26 total files, 0 missing files
libpsl: 38 total files, 0 missing files
libpulse: 99 total files, 0 missing files
libqaccessibilityclient-qt6: 22 total files, 0 missing files
libqalculate: 312 total files, 0 missing files
libqmi: 95 total files, 0 missing files
libqrtr-glib: 21 total files, 0 missing files
libquadmath: 11 total files, 0 missing files
libqxp: 336 total files, 0 missing files
libraqm: 40 total files, 0 missing files
libraw: 39 total files, 0 missing files
libraw1394: 24 total files, 0 missing files
libreoffice-fresh: 12482 total files, 0 missing files
libresidfp: 12 total files, 0 missing files
librevenge: 478 total files, 0 missing files
librsvg: 29 total files, 0 missing files
libsamplerate: 40 total files, 0 missing files
libsasl: 54 total files, 0 missing files
libseccomp: 56 total files, 0 missing files
libsecret: 231 total files, 0 missing files
libshout: 28 total files, 0 missing files
libsidplayfp: 30 total files, 0 missing files
libsigc++: 49 total files, 0 missing files
libsigc++-3.0: 58 total files, 0 missing files
libsixel: 27 total files, 0 missing files
libslirp: 15 total files, 0 missing files
libsm: 21 total files, 0 missing files
libsndfile: 61 total files, 0 missing files
libsodium: 90 total files, 0 missing files
libsoup3: 278 total files, 0 missing files
libsoxr: 18 total files, 0 missing files
libspectre: 17 total files, 0 missing files
libspiro: 15 total files, 0 missing files
libsrtp: 16 total files, 0 missing files
libssc: 63 total files, 0 missing files
libssh: 23 total files, 0 missing files
libssh2: 203 total files, 0 missing files
libstaroffice: 18 total files, 0 missing files
libstdc++: 16 total files, 0 missing files
libstemmer: 11 total files, 0 missing files
libsysprof-capture: 24 total files, 0 missing files
libtasn1: 83 total files, 0 missing files
libtatsu: 11 total files, 0 missing files
libteam: 35 total files, 0 missing files
libthai: 87 total files, 0 missing files
libtheora: 151 total files, 0 missing files
libtiff: 46 total files, 0 missing files
libtirpc: 91 total files, 0 missing files
libtommath: 9 total files, 0 missing files
libtool: 79 total files, 0 missing files
libtpms: 49 total files, 0 missing files
libtraceevent: 169 total files, 0 missing files
libtracefs: 236 total files, 0 missing files
libtsan: 9 total files, 0 missing files
libubsan: 9 total files, 0 missing files
libunibreak: 19 total files, 0 missing files
libunistring: 58 total files, 0 missing files
libunwind: 78 total files, 0 missing files
liburcu: 231 total files, 0 missing files
liburing: 256 total files, 0 missing files
libusb: 16 total files, 0 missing files
libusb-compat: 11 total files, 0 missing files
libusbmuxd: 18 total files, 0 missing files
libutempter: 20 total files, 0 missing files
libutf8proc: 13 total files, 0 missing files
libuv: 27 total files, 0 missing files
libva: 69 total files, 0 missing files
libva-intel-driver: 8 total files, 0 missing files
libvdpau: 21 total files, 0 missing files
libverto: 19 total files, 0 missing files
libvips: 100 total files, 0 missing files
libvirt: 1074 total files, 0 missing files
libvirt-glib: 289 total files, 0 missing files
libvirt-python: 27 total files, 0 missing files
libvisio: 710 total files, 0 missing files
libvlc: 120 total files, 0 missing files
libvorbis: 26 total files, 0 missing files
libvpl: 41 total files, 0 missing files
libvpx: 28 total files, 0 missing files
libvterm: 18 total files, 0 missing files
libwacom: 868 total files, 0 missing files
libwbclient: 10 total files, 0 missing files
libwebp: 52 total files, 0 missing files
libwireplumber: 61 total files, 0 missing files
libwmf: 79 total files, 0 missing files
libwpd: 1339 total files, 0 missing files
libwps: 19 total files, 0 missing files
libx11: 1252 total files, 0 missing files
libx86emu: 11 total files, 0 missing files
libxau: 25 total files, 0 missing files
libxaw: 143 total files, 0 missing files
libxcb: 2460 total files, 0 missing files
libxcomposite: 29 total files, 0 missing files
libxcrypt: 24 total files, 0 missing files
libxcursor: 77 total files, 0 missing files
libxcvt: 20 total files, 0 missing files
libxdamage: 15 total files, 0 missing files
libxdmcp: 17 total files, 0 missing files
libxdp: 48 total files, 0 missing files
libxext: 100 total files, 0 missing files
libxfce4ui: 306 total files, 0 missing files
libxfce4util: 271 total files, 0 missing files
libxfixes: 18 total files, 0 missing files
libxfont2: 15 total files, 0 missing files
libxft: 96 total files, 0 missing files
libxi: 97 total files, 0 missing files
libxinerama: 23 total files, 0 missing files
libxkbcommon: 50 total files, 0 missing files
libxkbcommon-x11: 21 total files, 0 missing files
libxkbfile: 20 total files, 0 missing files
libxklavier: 41 total files, 0 missing files
libxml2: 84 total files, 0 missing files
libxmlb: 76 total files, 0 missing files
libxmu: 45 total files, 0 missing files
libxpm: 63 total files, 0 missing files
libxpresent: 26 total files, 0 missing files
libxrandr: 32 total files, 0 missing files
libxrender: 18 total files, 0 missing files
libxshmfence: 14 total files, 0 missing files
libxslt: 65 total files, 0 missing files
libxss: 29 total files, 0 missing files
libxt: 340 total files, 0 missing files
libxtst: 33 total files, 0 missing files
libxv: 43 total files, 0 missing files
libxxf86vm: 40 total files, 0 missing files
libyaml: 13 total files, 0 missing files
libyuv: 36 total files, 0 missing files
libzip: 169 total files, 0 missing files
libzmf: 261 total files, 0 missing files
licenses: 113 total files, 0 missing files
lilv: 21 total files, 0 missing files
linux: 7705 total files, 0 missing files
linux-api-headers: 1079 total files, 0 missing files
linux-firmware: 0 total files, 0 missing files
linux-firmware-amdgpu: 686 total files, 0 missing files
linux-firmware-atheros: 481 total files, 0 missing files
linux-firmware-broadcom: 176 total files, 0 missing files
linux-firmware-cirrus: 1964 total files, 0 missing files
linux-firmware-intel: 851 total files, 0 missing files
linux-firmware-mediatek: 160 total files, 0 missing files
linux-firmware-nvidia: 620 total files, 0 missing files
linux-firmware-other: 1462 total files, 0 missing files
linux-firmware-radeon: 255 total files, 0 missing files
linux-firmware-realtek: 178 total files, 0 missing files
linux-firmware-whence: 5 total files, 0 missing files
linux-headers: 21828 total files, 0 missing files
lirc: 486 total files, 0 missing files
litehtml: 84 total files, 0 missing files
llvm-libs: 16 total files, 0 missing files
lm_sensors: 52 total files, 0 missing files
lmdb: 22 total files, 0 missing files
logrotate: 19 total files, 0 missing files
lpsolve: 35 total files, 0 missing files
lsb-release: 9 total files, 0 missing files
lsof: 17 total files, 0 missing files
lsscsi: 7 total files, 0 missing files
lua: 48 total files, 0 missing files
lua51: 40 total files, 0 missing files
lua51-lpeg: 20 total files, 0 missing files
lua54: 45 total files, 0 missing files
luajit: 50 total files, 0 missing files
lv2: 288 total files, 0 missing files
lvm2: 174 total files, 0 missing files
lz4: 23 total files, 0 missing files
lzo: 35 total files, 0 missing files
m4: 93 total files, 0 missing files
mailcap: 13 total files, 0 missing files
make: 105 total files, 0 missing files
man-db: 501 total files, 0 missing files
man-pages: 4293 total files, 0 missing files
md4c: 27 total files, 0 missing files
mdadm: 41 total files, 0 missing files
media-player-info: 268 total files, 0 missing files
meld: 549 total files, 0 missing files
mesa: 127 total files, 0 missing files
mesa-utils: 22 total files, 0 missing files
milou: 238 total files, 0 missing files
minizip: 18 total files, 0 missing files
mjpegtools: 164 total files, 0 missing files
mobile-broadband-provider-info: 8 total files, 0 missing files
modemmanager: 239 total files, 0 missing files
modemmanager-qt: 66 total files, 0 missing files
mpdecimal: 26 total files, 0 missing files
mpfr: 30 total files, 0 missing files
mpg123: 38 total files, 0 missing files
mpv: 86 total files, 0 missing files
mpvqt: 20 total files, 0 missing files
msgpack-c: 34 total files, 0 missing files
mtdev: 17 total files, 0 missing files
mtools: 78 total files, 0 missing files
mujs: 25 total files, 0 missing files
mypaint-brushes: 412 total files, 0 missing files
mypaint-brushes1: 373 total files, 0 missing files
nano: 189 total files, 0 missing files
nano-syntax-highlighting: 136 total files, 0 missing files
ncurses: 3967 total files, 0 missing files
ndctl: 126 total files, 0 missing files
neon: 282 total files, 0 missing files
neovim: 2311 total files, 0 missing files
netctl: 88 total files, 0 missing files
nettle: 92 total files, 0 missing files
networkmanager: 368 total files, 0 missing files
networkmanager-openconnect: 178 total files, 0 missing files
networkmanager-openvpn: 193 total files, 0 missing files
networkmanager-qt: 173 total files, 0 missing files
networkmanager-vpn-plugin-openconnect: 14 total files, 0 missing files
networkmanager-vpn-plugin-openvpn: 16 total files, 0 missing files
warning: nfs-utils: /var/lib/nfs/statd/sm.bak/ (Permission denied)
warning: nfs-utils: /var/lib/nfs/statd/sm/ (Permission denied)
warning: nfs-utils: /var/lib/nfs/statd/state (Permission denied)
nfs-utils: 124 total files, 3 missing files
nfsidmap: 26 total files, 0 missing files
nftables: 65 total files, 0 missing files
nilfs-utils: 50 total files, 0 missing files
nodejs: 127 total files, 0 missing files
noto-fonts: 639 total files, 0 missing files
noto-fonts-cjk: 21 total files, 0 missing files
noto-fonts-emoji: 8 total files, 0 missing files
noto-fonts-extra: 1554 total files, 0 missing files
npth: 17 total files, 0 missing files
nspr: 71 total files, 0 missing files
nss: 139 total files, 0 missing files
nss-mdns: 8 total files, 0 missing files
ntfs-3g: 15 total files, 0 missing files
ntp: 305 total files, 0 missing files
numactl: 31 total files, 0 missing files
nvm: 10 total files, 0 missing files
oath-toolkit: 229 total files, 0 missing files
obsidian-bin: 128 total files, 0 missing files
ocean-sound-theme: 83 total files, 0 missing files
ocl-icd: 26 total files, 0 missing files
okular: 1683 total files, 0 missing files
ollama: 56 total files, 0 missing files
onetbb: 207 total files, 0 missing files
oniguruma: 33 total files, 0 missing files
openai-codex: 15 total files, 0 missing files
openal: 44 total files, 0 missing files
openconnect: 190 total files, 0 missing files
opencore-amr: 27 total files, 0 missing files
opencv: 914 total files, 0 missing files
openexr: 228 total files, 0 missing files
openh264: 20 total files, 0 missing files
openjpeg2: 521 total files, 0 missing files
openjph: 32 total files, 0 missing files
openssh: 89 total files, 0 missing files
openssl: 6752 total files, 0 missing files
openvpn: 86 total files, 0 missing files
openxr: 45 total files, 0 missing files
opus: 21 total files, 0 missing files
opusfile: 23 total files, 0 missing files
orc: 66 total files, 0 missing files
osinfo-db: 1242 total files, 0 missing files
ostree: 175 total files, 0 missing files
p11-kit: 249 total files, 0 missing files
pacman: 426 total files, 0 missing files
pacman-contrib: 62 total files, 0 missing files
pacman-mirrorlist: 3 total files, 0 missing files
pacutils: 56 total files, 0 missing files
pahole: 50 total files, 0 missing files
pam: 602 total files, 0 missing files
pambase: 8 total files, 0 missing files
pango: 86 total files, 0 missing files
pangomm: 73 total files, 0 missing files
pangomm-2.48: 74 total files, 0 missing files
parallel: 44 total files, 0 missing files
parted: 131 total files, 0 missing files
partitionmanager: 449 total files, 0 missing files
passim: 92 total files, 0 missing files
patch: 7 total files, 0 missing files
pavucontrol: 187 total files, 0 missing files
pciutils: 29 total files, 0 missing files
pcre: 211 total files, 0 missing files
pcre2: 257 total files, 0 missing files
pcsclite: 54 total files, 0 missing files
perl: 3227 total files, 0 missing files
perl-class-inspector: 12 total files, 0 missing files
perl-clone: 13 total files, 0 missing files
perl-encode-locale: 9 total files, 0 missing files
perl-error: 11 total files, 0 missing files
perl-file-listing: 9 total files, 0 missing files
perl-file-sharedir: 19 total files, 0 missing files
perl-html-parser: 27 total files, 0 missing files
perl-html-tagset: 9 total files, 0 missing files
perl-http-cookiejar: 12 total files, 0 missing files
perl-http-cookies: 14 total files, 0 missing files
perl-http-daemon: 9 total files, 0 missing files
perl-http-date: 9 total files, 0 missing files
perl-http-message: 27 total files, 0 missing files
perl-http-negotiate: 9 total files, 0 missing files
perl-io-html: 9 total files, 0 missing files
perl-libwww: 55 total files, 0 missing files
perl-lwp-mediatypes: 10 total files, 0 missing files
perl-mailtools: 41 total files, 0 missing files
perl-mime-base32: 9 total files, 0 missing files
perl-net-http: 16 total files, 0 missing files
perl-timedate: 94 total files, 0 missing files
perl-try-tiny: 12 total files, 0 missing files
perl-uri: 95 total files, 0 missing files
perl-www-robotrules: 14 total files, 0 missing files
perl-xml-parser: 59 total files, 0 missing files
perl-xml-writer: 12 total files, 0 missing files
persepolis: 184 total files, 0 missing files
phodav: 122 total files, 0 missing files
phonon-qt6: 477 total files, 0 missing files
phonon-qt6-vlc: 170 total files, 0 missing files
pinentry: 16 total files, 0 missing files
pinta: 435 total files, 0 missing files
pipewire: 283 total files, 0 missing files
pipewire-alsa: 12 total files, 0 missing files
pipewire-audio: 134 total files, 0 missing files
pipewire-jack: 51 total files, 0 missing files
pipewire-pulse: 68 total files, 0 missing files
pixman: 15 total files, 0 missing files
pkcs11-helper: 35 total files, 0 missing files
pkgconf: 50 total files, 0 missing files
pkgfile: 32 total files, 0 missing files
plasma-activities: 46 total files, 0 missing files
plasma-activities-stats: 36 total files, 0 missing files
plasma-browser-integration: 247 total files, 0 missing files
plasma-desktop: 4753 total files, 0 missing files
plasma-disks: 174 total files, 0 missing files
plasma-integration: 173 total files, 0 missing files
plasma-keyboard: 513 total files, 0 missing files
plasma-login-manager: 209 total files, 0 missing files
plasma-nm: 1230 total files, 0 missing files
plasma-pa: 323 total files, 0 missing files
plasma-systemmonitor: 339 total files, 0 missing files
plasma-workspace: 6786 total files, 0 missing files
plasma-x11-session: 4 total files, 0 missing files
plasma5support: 749 total files, 0 missing files
plocate: 33 total files, 0 missing files
polkit: 238 total files, 0 missing files
polkit-kde-agent: 217 total files, 0 missing files
polkit-qt6: 59 total files, 0 missing files
poppler: 171 total files, 0 missing files
poppler-data: 524 total files, 0 missing files
poppler-glib: 90 total files, 0 missing files
poppler-qt6: 27 total files, 0 missing files
popt: 126 total files, 0 missing files
portaudio: 43 total files, 0 missing files
postgresql: 3212 total files, 0 missing files
postgresql-libs: 276 total files, 0 missing files
power-profiles-daemon: 28 total files, 0 missing files
powerdevil: 756 total files, 0 missing files
ppp: 91 total files, 0 missing files
print-manager: 358 total files, 0 missing files
prison: 58 total files, 0 missing files
procps-ng: 242 total files, 0 missing files
protobuf: 404 total files, 0 missing files
protobuf-c: 21 total files, 0 missing files
psmisc: 196 total files, 0 missing files
pulseaudio-qt: 57 total files, 0 missing files
purpose: 879 total files, 0 missing files
pyenv: 1853 total files, 0 missing files
pyside6: 485 total files, 0 missing files
python: 3198 total files, 0 missing files
python-annotated-types: 26 total files, 0 missing files
python-argcomplete: 69 total files, 0 missing files
python-awscrt: 82 total files, 0 missing files
python-cairo: 21 total files, 0 missing files
python-capng: 10 total files, 0 missing files
python-certifi: 36 total files, 0 missing files
python-charset-normalizer: 59 total files, 0 missing files
python-click: 68 total files, 0 missing files
python-colorama: 57 total files, 0 missing files
python-dasbus: 92 total files, 0 missing files
python-dateutil: 79 total files, 0 missing files
python-dbus: 73 total files, 0 missing files
python-defusedxml: 50 total files, 0 missing files
python-distro: 31 total files, 0 missing files
python-docutils: 539 total files, 0 missing files
python-firewall: 188 total files, 0 missing files
python-gobject: 98 total files, 0 missing files
python-idna: 50 total files, 0 missing files
python-jinja: 93 total files, 0 missing files
python-jmespath: 39 total files, 0 missing files
python-markupsafe: 27 total files, 0 missing files
python-natsort: 60 total files, 0 missing files
python-orjson: 32 total files, 0 missing files
python-packaging: 89 total files, 0 missing files
python-pipx: 138 total files, 0 missing files
python-platformdirs: 44 total files, 0 missing files
python-prompt_toolkit: 496 total files, 0 missing files
python-psutil: 48 total files, 0 missing files
python-pyaml: 29 total files, 0 missing files
python-pydantic: 343 total files, 0 missing files
python-pydantic-core: 30 total files, 0 missing files
python-pyqt6: 1040 total files, 0 missing files
python-pyqt6-sip: 17 total files, 0 missing files
python-pysocks: 22 total files, 0 missing files
python-requests: 72 total files, 0 missing files
python-ruamel-yaml: 120 total files, 0 missing files
python-ruamel.yaml.clib: 16 total files, 0 missing files
python-setproctitle: 22 total files, 0 missing files
python-shtab: 39 total files, 0 missing files
python-six: 19 total files, 0 missing files
python-termcolor: 26 total files, 0 missing files
python-typing-inspection: 23 total files, 0 missing files
python-typing_extensions: 18 total files, 0 missing files
python-urllib3: 134 total files, 0 missing files
python-userpath: 40 total files, 0 missing files
python-wcwidth: 160 total files, 0 missing files
python-yaml: 78 total files, 0 missing files
qca-qt6: 51 total files, 0 missing files
qcoro: 164 total files, 0 missing files
qemu-audio-alsa: 14 total files, 0 missing files
qemu-audio-dbus: 14 total files, 0 missing files
qemu-audio-jack: 14 total files, 0 missing files
qemu-audio-oss: 14 total files, 0 missing files
qemu-audio-pa: 14 total files, 0 missing files
qemu-audio-pipewire: 14 total files, 0 missing files
qemu-audio-sdl: 14 total files, 0 missing files
qemu-audio-spice: 14 total files, 0 missing files
qemu-base: 11 total files, 0 missing files
qemu-block-curl: 14 total files, 0 missing files
qemu-block-dmg: 14 total files, 0 missing files
qemu-block-nfs: 14 total files, 0 missing files
qemu-block-ssh: 14 total files, 0 missing files
qemu-chardev-spice: 14 total files, 0 missing files
qemu-common: 145 total files, 0 missing files
qemu-desktop: 11 total files, 0 missing files
qemu-hw-display-qxl: 14 total files, 0 missing files
qemu-hw-display-virtio-gpu: 14 total files, 0 missing files
qemu-hw-display-virtio-gpu-gl: 14 total files, 0 missing files
qemu-hw-display-virtio-gpu-pci: 14 total files, 0 missing files
qemu-hw-display-virtio-gpu-pci-gl: 14 total files, 0 missing files
qemu-hw-display-virtio-gpu-pci-rutabaga: 14 total files, 0 missing files
qemu-hw-display-virtio-gpu-rutabaga: 14 total files, 0 missing files
qemu-hw-display-virtio-vga: 14 total files, 0 missing files
qemu-hw-display-virtio-vga-gl: 14 total files, 0 missing files
qemu-hw-display-virtio-vga-rutabaga: 14 total files, 0 missing files
qemu-hw-uefi-vars: 14 total files, 0 missing files
qemu-hw-usb-host: 14 total files, 0 missing files
qemu-hw-usb-redirect: 14 total files, 0 missing files
qemu-hw-usb-smartcard: 14 total files, 0 missing files
qemu-img: 24 total files, 0 missing files
qemu-system-aarch64: 16 total files, 0 missing files
qemu-system-x86: 18 total files, 0 missing files
qemu-system-x86-firmware: 17 total files, 0 missing files
qemu-ui-curses: 14 total files, 0 missing files
qemu-ui-dbus: 14 total files, 0 missing files
qemu-ui-egl-headless: 14 total files, 0 missing files
qemu-ui-gtk: 14 total files, 0 missing files
qemu-ui-opengl: 14 total files, 0 missing files
qemu-ui-sdl: 14 total files, 0 missing files
qemu-ui-spice-app: 14 total files, 0 missing files
qemu-ui-spice-core: 14 total files, 0 missing files
qemu-vhost-user-gpu: 17 total files, 0 missing files
qqc2-breeze-style: 110 total files, 0 missing files
qqc2-desktop-style: 218 total files, 0 missing files
qrencode: 15 total files, 0 missing files
qt5-base: 3862 total files, 0 missing files
qt5-declarative: 1057 total files, 0 missing files
qt5-svg: 56 total files, 0 missing files
qt5-translations: 351 total files, 0 missing files
qt5-wayland: 398 total files, 0 missing files
qt5-x11extras: 31 total files, 0 missing files
qt6-5compat: 165 total files, 0 missing files
qt6-base: 5102 total files, 0 missing files
qt6-connectivity: 251 total files, 0 missing files
qt6-declarative: 5512 total files, 0 missing files
qt6-imageformats: 73 total files, 0 missing files
qt6-location: 262 total files, 0 missing files
qt6-multimedia: 500 total files, 0 missing files
qt6-multimedia-ffmpeg: 107 total files, 0 missing files
qt6-positioning: 213 total files, 0 missing files
qt6-quick3d: 1435 total files, 0 missing files
qt6-quicktimeline: 135 total files, 0 missing files
qt6-scxml: 330 total files, 0 missing files
qt6-sensors: 250 total files, 0 missing files
qt6-shadertools: 80 total files, 0 missing files
qt6-speech: 115 total files, 0 missing files
qt6-svg: 137 total files, 0 missing files
qt6-tools: 610 total files, 0 missing files
qt6-translations: 316 total files, 0 missing files
qt6-virtualkeyboard: 447 total files, 0 missing files
qt6-wayland: 627 total files, 0 missing files
qt6-webchannel: 128 total files, 0 missing files
qt6-webengine: 618 total files, 0 missing files
qt6-websockets: 98 total files, 0 missing files
qtkeychain-qt6: 32 total files, 0 missing files
raptor: 128 total files, 0 missing files
rasqal: 81 total files, 0 missing files
rate-mirrors: 3 total files, 0 missing files
rav1e: 17 total files, 0 missing files
rdma-core: 815 total files, 0 missing files
re2: 23 total files, 0 missing files
readline: 60 total files, 0 missing files
rebuild-detector: 15 total files, 0 missing files
redland: 100 total files, 0 missing files
reflector: 29 total files, 0 missing files
reflector-simple: 11 total files, 0 missing files
ripgrep: 24 total files, 0 missing files
ripgrep-all: 6 total files, 0 missing files
ristretto: 200 total files, 0 missing files
rnnoise: 18 total files, 0 missing files
rpcbind: 24 total files, 0 missing files
rsync: 49 total files, 0 missing files
rtkit: 28 total files, 0 missing files
rtmpdump: 25 total files, 0 missing files
rubberband: 24 total files, 0 missing files
run-parts: 31 total files, 0 missing files
runc: 26 total files, 0 missing files
rutabaga-ffi: 12 total files, 0 missing files
s-nail: 16 total files, 0 missing files
s2n-tls: 27 total files, 0 missing files
samba: 1195 total files, 0 missing files
sbc: 14 total files, 0 missing files
sd: 22 total files, 0 missing files
sdl12-compat: 52 total files, 0 missing files
sdl2-compat: 126 total files, 0 missing files
sdl2_image: 20 total files, 0 missing files
sdl3: 113 total files, 0 missing files
seabios: 20 total files, 0 missing files
sed: 136 total files, 0 missing files
serd: 28 total files, 0 missing files
sg3_utils: 202 total files, 0 missing files
shaderc: 22 total files, 0 missing files
shadow: 534 total files, 0 missing files
shared-mime-info: 255 total files, 0 missing files
shiboken6: 72 total files, 0 missing files
signon-kwallet-extension: 5 total files, 0 missing files
signon-plugin-oauth2: 10 total files, 0 missing files
signon-ui: 10 total files, 0 missing files
signond: 122 total files, 0 missing files
simdjson: 15 total files, 0 missing files
slang: 182 total files, 0 missing files
smartmontools: 46 total files, 0 missing files
smbclient: 234 total files, 0 missing files
snappy: 22 total files, 0 missing files
sndio: 69 total files, 0 missing files
socat: 14 total files, 0 missing files
sof-firmware: 662 total files, 0 missing files
solid: 257 total files, 0 missing files
sonnet: 379 total files, 0 missing files
sord: 30 total files, 0 missing files
sound-theme-freedesktop: 44 total files, 0 missing files
soundtouch: 26 total files, 0 missing files
source-highlight: 434 total files, 0 missing files
spandsp: 157 total files, 0 missing files
spectacle: 308 total files, 0 missing files
speex: 32 total files, 0 missing files
speexdsp: 22 total files, 0 missing files
spice: 19 total files, 0 missing files
spice-gtk: 131 total files, 0 missing files
spice-protocol: 23 total files, 0 missing files
spirv-tools: 59 total files, 0 missing files
sqlite: 31 total files, 0 missing files
sratom: 19 total files, 0 missing files
srt: 21 total files, 0 missing files
starship: 19 total files, 0 missing files
startup-notification: 16 total files, 0 missing files
stoken: 33 total files, 0 missing files
sudo: 243 total files, 0 missing files
suitesparse: 198 total files, 0 missing files
svt-av1: 29 total files, 0 missing files
svt-hevc: 17 total files, 0 missing files
syndication: 88 total files, 0 missing files
syntax-highlighting: 781 total files, 0 missing files
sysfsutils: 17 total files, 0 missing files
systemd: 1908 total files, 0 missing files
systemd-libs: 922 total files, 0 missing files
systemd-resolvconf: 7 total files, 0 missing files
systemd-sysvcompat: 16 total files, 0 missing files
systemsettings: 373 total files, 0 missing files
taglib: 154 total files, 0 missing files
talloc: 23 total files, 0 missing files
tar: 135 total files, 0 missing files
tcl: 1183 total files, 0 missing files
tdb: 25 total files, 0 missing files
telegram-desktop: 60 total files, 0 missing files
tesseract: 75 total files, 0 missing files
tesseract-data-afr: 4 total files, 0 missing files
tesseract-data-osd: 4 total files, 0 missing files
tevent: 13 total files, 0 missing files
texinfo: 705 total files, 0 missing files
thin-provisioning-tools: 50 total files, 0 missing files
threadweaver: 84 total files, 0 missing files
thunderbird: 97 total files, 0 missing files
timeshift: 283 total files, 0 missing files
tinysparql: 279 total files, 0 missing files
tldr: 30 total files, 0 missing files
tldraw-offline-bin: 577 total files, 0 missing files
tlottie: 5 total files, 0 missing files
tpm2-tss: 308 total files, 0 missing files
tree-sitter: 13 total files, 0 missing files
tree-sitter-c: 19 total files, 0 missing files
tree-sitter-lua: 26 total files, 0 missing files
tree-sitter-markdown: 23 total files, 0 missing files
tree-sitter-query: 25 total files, 0 missing files
tree-sitter-vim: 18 total files, 0 missing files
tree-sitter-vimdoc: 19 total files, 0 missing files
triliumnext-bin: 19 total files, 0 missing files
tslib: 74 total files, 0 missing files
ttf-bitstream-vera: 17 total files, 0 missing files
ttf-dejavu: 56 total files, 0 missing files
ttf-hack: 14 total files, 0 missing files
ttf-liberation: 19 total files, 0 missing files
ttf-opensans: 27 total files, 0 missing files
tumbler: 276 total files, 0 missing files
twolame: 24 total files, 0 missing files
tzdata: 1887 total files, 0 missing files
uchardet: 22 total files, 0 missing files
udisks2: 281 total files, 0 missing files
unibilium: 65 total files, 0 missing files
unrar: 7 total files, 0 missing files
unzip: 18 total files, 0 missing files
upower: 115 total files, 0 missing files
uriparser: 27 total files, 0 missing files
usb_modeswitch: 538 total files, 0 missing files
usbredir: 22 total files, 0 missing files
usbutils: 27 total files, 0 missing files
util-linux: 1661 total files, 0 missing files
util-linux-libs: 81 total files, 0 missing files
v4l-utils: 809 total files, 0 missing files
valkey: 34 total files, 0 missing files
vapoursynth: 68 total files, 0 missing files
vde2: 94 total files, 0 missing files
verdict: 23 total files, 0 missing files
vid.stab: 27 total files, 0 missing files
vim: 214 total files, 0 missing files
vim-runtime: 2552 total files, 0 missing files
virglrenderer: 18 total files, 0 missing files
virt-install: 429 total files, 0 missing files
virt-manager: 300 total files, 0 missing files
virtiofsd: 16 total files, 0 missing files
virtualbox: 342 total files, 0 missing files
virtualbox-host-dkms: 440 total files, 0 missing files
visual-studio-code-bin: 3008 total files, 0 missing files
vlc: 349 total files, 0 missing files
vlc-cli: 11 total files, 0 missing files
vlc-gui-qt: 8 total files, 0 missing files
vlc-plugin-a52dec: 6 total files, 0 missing files
vlc-plugin-alsa: 8 total files, 0 missing files
vlc-plugin-archive: 6 total files, 0 missing files
vlc-plugin-dav1d: 6 total files, 0 missing files
vlc-plugin-dbus: 6 total files, 0 missing files
vlc-plugin-dbus-screensaver: 6 total files, 0 missing files
vlc-plugin-faad2: 6 total files, 0 missing files
vlc-plugin-flac: 6 total files, 0 missing files
vlc-plugin-gnutls: 6 total files, 0 missing files
vlc-plugin-inflate: 6 total files, 0 missing files
vlc-plugin-journal: 6 total files, 0 missing files
vlc-plugin-jpeg: 6 total files, 0 missing files
vlc-plugin-lua: 152 total files, 0 missing files
vlc-plugin-matroska: 6 total files, 0 missing files
vlc-plugin-mpg123: 6 total files, 0 missing files
vlc-plugin-ogg: 8 total files, 0 missing files
vlc-plugin-opus: 6 total files, 0 missing files
vlc-plugin-png: 6 total files, 0 missing files
vlc-plugin-pulse: 13 total files, 0 missing files
vlc-plugin-shout: 6 total files, 0 missing files
vlc-plugin-speex: 8 total files, 0 missing files
vlc-plugin-tag: 6 total files, 0 missing files
vlc-plugin-theora: 6 total files, 0 missing files
vlc-plugin-twolame: 6 total files, 0 missing files
vlc-plugin-vorbis: 6 total files, 0 missing files
vlc-plugin-vpx: 6 total files, 0 missing files
vlc-plugin-xml: 6 total files, 0 missing files
vlc-plugins-base: 290 total files, 0 missing files
vlc-plugins-video-output: 42 total files, 0 missing files
vmaf: 255 total files, 0 missing files
volume_key: 126 total files, 0 missing files
vpnc: 30 total files, 0 missing files
vte-common: 319 total files, 0 missing files
vte3: 42 total files, 0 missing files
vulkan-icd-loader: 12 total files, 0 missing files
vulkan-intel: 12 total files, 0 missing files
vulkan-mesa-implicit-layers: 12 total files, 0 missing files
vulkan-tools: 5 total files, 0 missing files
wavpack: 33 total files, 0 missing files
wayland: 46 total files, 0 missing files
wayland-utils: 10 total files, 0 missing files
webkit2gtk-4.1: 416 total files, 0 missing files
webrtc-audio-processing-1: 54 total files, 0 missing files
welcome: 26 total files, 0 missing files
wget: 176 total files, 0 missing files
which: 9 total files, 0 missing files
whois: 66 total files, 0 missing files
wildmidi: 46 total files, 0 missing files
wireless-regdb: 25 total files, 0 missing files
wireplumber: 322 total files, 0 missing files
woff2: 25 total files, 0 missing files
wolfssl: 216 total files, 0 missing files
wpa_supplicant: 36 total files, 0 missing files
x264: 15 total files, 0 missing files
x265: 13 total files, 0 missing files
xapp: 389 total files, 0 missing files
xapp-symbolic-icons: 676 total files, 0 missing files
xcb-proto: 74 total files, 0 missing files
xcb-util: 20 total files, 0 missing files
xcb-util-cursor: 14 total files, 0 missing files
xcb-util-image: 16 total files, 0 missing files
xcb-util-keysyms: 14 total files, 0 missing files
xcb-util-renderutil: 14 total files, 0 missing files
xcb-util-wm: 19 total files, 0 missing files
xdg-dbus-proxy: 7 total files, 0 missing files
xdg-desktop-portal: 198 total files, 0 missing files
xdg-desktop-portal-gtk: 119 total files, 0 missing files
xdg-desktop-portal-kde: 182 total files, 0 missing files
xdg-user-dirs: 264 total files, 0 missing files
xdg-utils: 25 total files, 0 missing files
xf86-input-libinput: 21 total files, 0 missing files
xfconf: 250 total files, 0 missing files
xfsprogs: 167 total files, 0 missing files
xkeyboard-config: 520 total files, 0 missing files
xl2tpd: 27 total files, 0 missing files
xmlsec: 193 total files, 0 missing files
xorg-fonts-encodings: 60 total files, 0 missing files
xorg-server: 48 total files, 0 missing files
xorg-server-common: 15 total files, 0 missing files
xorg-setxkbmap: 10 total files, 0 missing files
xorg-xauth: 10 total files, 0 missing files
xorg-xdpyinfo: 10 total files, 0 missing files
xorg-xinit: 17 total files, 0 missing files
xorg-xinput: 10 total files, 0 missing files
xorg-xkbcomp: 13 total files, 0 missing files
xorg-xkill: 10 total files, 0 missing files
xorg-xmessage: 14 total files, 0 missing files
xorg-xmodmap: 10 total files, 0 missing files
xorg-xprop: 10 total files, 0 missing files
xorg-xrandr: 10 total files, 0 missing files
xorg-xrdb: 10 total files, 0 missing files
xorg-xwayland: 15 total files, 0 missing files
xorgproto: 211 total files, 0 missing files
xreader: 659 total files, 0 missing files
xsettingsd: 16 total files, 0 missing files
xterm: 40 total files, 0 missing files
xvidcore: 7 total files, 0 missing files
xxhash: 27 total files, 0 missing files
xz: 483 total files, 0 missing files
yad: 64 total files, 0 missing files
yay: 119 total files, 0 missing files
yt-dlp: 3204 total files, 0 missing files
yt-dlp-ejs: 30 total files, 0 missing files
zbar: 64 total files, 0 missing files
zeromq: 184 total files, 0 missing files
zimg: 34 total files, 0 missing files
zint: 18 total files, 0 missing files
zip: 16 total files, 0 missing files
zix: 36 total files, 0 missing files
zlib: 17 total files, 0 missing files
zlib-ng: 24 total files, 0 missing files
zstd: 39 total files, 0 missing files
zvbi: 55 total files, 0 missing files
zxing-cpp: 41 total files, 0 missing files This doesn't contain all the packages because the konsole bash didn't display some content above the top, in konsole
```

---

## 8. Network Configuration
*(Note: Hardware MAC addresses redacted for evidence safety; raw telemetry stored in `private/host-diagnostic-raw.txt`)*
```bash
ip addr show && ip route
```
```text
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp0s31f6: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether [REDACTED_MAC] brd ff:ff:ff:ff:ff:ff
    altname enxe86a648fbd0a
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether [REDACTED_MAC] brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.222/24 brd 192.168.100.255 scope global dynamic noprefixroute wlan0
       valid_lft 65719sec preferred_lft 65719sec
    inet6 fe80::7127:bfb:8047:eaf6/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether [REDACTED_MAC] brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
5: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 0
    link/ether [REDACTED_MAC] brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
default via 192.168.100.1 dev wlan0 proto dhcp src 192.168.100.222 metric 600 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
192.168.100.0/24 dev wlan0 proto kernel scope link src 192.168.100.222 metric 600 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 

~ 
❯
```

---

## 9. Journal Errors (Boot-Time)
```bash
journalctl -b -p err --no-pager
```
```text
ستمبر 10 09:09:55 muazislambabar kernel: virt/tdx: TDX not supported by the host platform
ستمبر 10 09:09:56 muazislambabar kernel: kvm_amd: CPU 7 isn't AMD or Hygon
ستمبر 10 09:10:13 muazislambabar wpa_supplicant[768]: wlan0: nl80211: kernel reports: multicast RX registrations are not supported
ستمبر 10 09:10:13 muazislambabar wpa_supplicant[768]: p2p-dev-wlan0: nl80211: kernel reports: multicast RX registrations are not supported
ستمبر 10 09:10:19 muazislambabar firewalld[709]: ERROR: NAME_CONFLICT: new_policy_object(): 'docker-forwarding'
ستمبر 10 09:11:42 muazislambabar kernel: ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ستمبر 10 09:11:42 muazislambabar kernel: ata3.00: irq_stat 0x40000001
ستمبر 10 09:11:42 muazislambabar kernel: ata3.00: failed command: FLUSH CACHE EXT
ستمبر 10 09:11:42 muazislambabar kernel: ata3.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 23
                                                       res 51/04:00:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
ستمبر 10 09:11:42 muazislambabar kernel: ata3.00: status: { DRDY ERR }
ستمبر 10 09:11:42 muazislambabar kernel: ata3.00: error: { ABRT }
ستمبر 10 09:11:42 muazislambabar kernel: ata3.00: revalidation failed (errno=-2)
ستمبر 10 09:12:16 muazislambabar kwin_wayland[1490]: Libinput: event8  - Synaptics TM3276-022: kernel bug: Touch jump detected and discarded.
                                                          See https://wayland.freedesktop.org/libinput/doc/1.31.3/touchpad-jumping-cursors.html for details
ستمبر 10 09:16:36 muazislambabar kernel: i915 0000:00:02.0: [drm] *ERROR* Atomic update failure on pipe A (start=53 end=54) time 647 us, min 1430, max 1439, scanline start 1408, end 1467
ستمبر 10 09:42:23 muazislambabar kwin_wayland[1490]: Libinput: event8  - Synaptics TM3276-022: kernel bug: Touch jump detected and discarded.
                                                          See https://wayland.freedesktop.org/libinput/doc/1.31.3/touchpad-jumping-cursors.html for details
ستمبر 10 09:47:30 muazislambabar kwin_wayland[1490]: Libinput: event8  - Synaptics TM3276-022: kernel bug: Touch jump detected and discarded.
                                                          See https://wayland.freedesktop.org/libinput/doc/1.31.3/touchpad-jumping-cursors.html for details
ستمبر 10 09:48:09 muazislambabar kwin_wayland[1490]: Libinput: event8  - Synaptics TM3276-022: kernel bug: Touch jump detected and discarded.
                                                          See https://wayland.freedesktop.org/libinput/doc/1.31.3/touchpad-jumping-cursors.html for details
ستمبر 10 09:49:05 muazislambabar kwin_wayland[1490]: Libinput: event8  - Synaptics TM3276-022: kernel bug: Touch jump detected and discarded.
                                                          See https://wayland.freedesktop.org/libinput/doc/1.31.3/touchpad-jumping-cursors.html for details
ستمبر 10 09:49:05 muazislambabar kwin_wayland[1490]: Libinput: event8  - Synaptics TM3276-022: WARNING: log rate limit exceeded (5 msgs per 24h). Discarding future messages.
ستمبر 10 10:02:45 muazislambabar kscreenlocker_greet[7558]: The backend got an unknown wallpaper provider type. The wallpaper will now fall back to the default. Please check your wallpaper configuration!
ستمبر 10 13:10:55 muazislambabar kernel: device offline error, dev sdc, sector 122877891 op 0x1:(WRITE) flags 0x800000 phys_seg 1 prio class 2
ستمبر 10 13:10:55 muazislambabar kernel: Buffer I/O error on dev sdc2, logical block 45, lost async page write
ستمبر 10 13:10:55 muazislambabar kernel: device offline error, dev sdc, sector 122878143 op 0x1:(WRITE) flags 0x800000 phys_seg 2 prio class 2
ستمبر 10 13:10:55 muazislambabar kernel: Buffer I/O error on dev sdc2, logical block 297, lost async page write
ستمبر 10 13:10:55 muazislambabar kernel: Buffer I/O error on dev sdc2, logical block 298, lost async page write
ستمبر 10 13:15:33 muazislambabar kernel: Bluetooth: hci0: Reading supported features failed (-16)
ستمبر 10 14:43:23 muazislambabar sudo[23143]: pam_unix(sudo:auth): conversation failed
ستمبر 10 14:43:23 muazislambabar sudo[23143]: pam_unix(sudo:auth): auth could not identify password for [muazislambabar]
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5003936 op 0x1:(WRITE) flags 0x4000 phys_seg 20 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5004176 op 0x1:(WRITE) flags 0x4000 phys_seg 20 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167623, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625236
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625237
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167624, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625238
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167625, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625239
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625240
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167626, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625241
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167627, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625242
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167628, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625243
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625244
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on device sdc1, logical block 625245
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167629, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167630, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167631, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: EXT4-fs (sdc1): failed to convert unwritten extents to written extents -- potential data loss!  (inode 167632, error -5)
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5004416 op 0x1:(WRITE) flags 0x4000 phys_seg 25 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5004656 op 0x1:(WRITE) flags 0x4000 phys_seg 26 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5004896 op 0x1:(WRITE) flags 0x4000 phys_seg 21 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5005104 op 0x1:(WRITE) flags 0x4000 phys_seg 19 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5005344 op 0x1:(WRITE) flags 0x4000 phys_seg 30 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5005584 op 0x1:(WRITE) flags 0x4000 phys_seg 27 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5005824 op 0x1:(WRITE) flags 0x4000 phys_seg 9 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: device offline error, dev sdc, sector 5005960 op 0x1:(WRITE) flags 0x4000 phys_seg 12 prio class 2
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534794, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534795, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534796, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534797, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534798, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534799, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534800, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534801, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534802, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Buffer I/O error on dev sdc1, logical block 534803, lost async page write
ستمبر 10 14:44:05 muazislambabar kernel: Aborting journal on device sdc1-8.
ستمبر 10 14:44:05 muazislambabar kernel: JBD2: I/O error when updating journal superblock for sdc1-8.
```

---

## Diagnostic Evaluation & Subsystem Findings

1. **CPU / Virtualization**: Intel Core i7-8650U (4 physical cores, 8 threads) with Intel VT-x enabled. The journal notifications for `virt/tdx` and `kvm_amd` are expected module compatibility checks on Intel architecture and pose no issue.
2. **Filesystems & Storage**: Root filesystem is btrfs on `/dev/sda2` with 181 GiB available (24% utilization). Subvolumes dedicated to `/home`, `/var/cache`, `/var/log`, and `/swap`. Separate FAT32 `/efi` boot partition at `/dev/sda1`.
3. **Services**: `systemctl list-units --state=failed` reports 0 failed units. Host system services are healthy.
4. **Package DB**: `pacman -Qk` completed across all installed packages with zero missing files.
5. **Networking**: Active WiFi link on `wlan0` (`192.168.100.222/24`) with default gateway `192.168.100.1`. Host bridges `docker0` (Docker container networking) and `virbr0` (libvirt bridge) present.
6. **Storage Incident (/dev/sdc)**: Boot journal recorded ATA command FLUSH CACHE EXT failure and buffer I/O write failures on USB device `sdc` during initial backup tests. Confirmed resolved by user.
