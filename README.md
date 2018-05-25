## ServerTech and APC PDU update/maintenance script

**Supports:**
* ServerTech PRO1/PRO2 and Switched CDU Power Distribution Units
* Schneider Electric APC AP8XXX Rack PDUs

This script does two things for two different kinds of rack/cabinet PDUs:
1. It checks and then performs firmware upgrades of the PDU management cards
2. It can optionall run a list of commands on the PDU prior to the above.

The requirement for this script is a working FTP server where the firmware
for both the STech and APC PDUs will reside, along with an associated
text file which contains the desired version info for each brand of PDU.

The expected directory structure on the FTP server is as follows:

**ServerTech PDUs:**
```
    /pdu/sentry/
             -> current-pro.txt    (PRO series version file. ex: "8.0k")
             -> current-swcdu.txt  (Switched CDU version file. ex: "7.1c")
             -> pro-vXX.bin        (PRO series firmware ex: pro-v80k.bin)
             -> swcdu-vXX.bin      (Switched CDU fimrware ex: swcdu-v71c.bin)
```

**APC PDUs:**
```
    /pdu/apc/
             -> current-apc.txt          (APC PDU version info. See below)
             -> apc_hw05_aos_XXX.bin     (AOS firmware image)
             -> apc_hw05_rpdu2g_652.bin  (App firmware image)
             -> apc_hw05_bootmon_108.bin (Bootmon firmware image)
```

The `current-apc.txt` file format is more than just a version string since we
must track the versions of 3 separate firmware images for APC PDUs. The file
format is as follows:

```
aos=6.5.2
rpdu2g=6.5.2
bootmon=1.0.8
```
