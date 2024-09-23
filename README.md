# nxdn-to-xlx

## About

How to set up a standalone NXDN reflector and interconnect it to an XLX reflector.

## Prerequisites

### Install NXDNReflector

```bash
git clone https://github.com/nostar/DVReflectors.git
cd DVReflectors/NXDNReflector
make
make install
```

### Install NXDN2DMR

```bash
git clone https://github.com/juribeparada/MMDVM_CM.git
cd MMDVM_CM/NXDN2DMR
make
make install
```

## Configuration

### reflector/NXDNReflector.ini

```ini
[General]
TG=12345
```

* `12345` — the NXDN group number you interconnect with. Should match the one in NXDN2DMR.ini.

### reflector/NXDN2DMR.ini

Replace the following parts with your actual data:

```ini
[NXDN Network]
Callsign=CALLSIGN
TG=12345
DefaultID=1234
```

* `CALLSIGN` — your callsign. Will be shown if the speaking party has no actual 
* `12345` — the NXDN group number you interconnect with. Should match the one in NXDNReflector.ini.
* `1234` — the default NXDN ID if the speaking party has none assigned.

```ini
[DMR Network]
Id=1234567
XLXReflector=123
XLXModule=A
```

* `1234567` — your DMR ID.
* `123` — the XLX reflector number.
* `A` — the XLX reflector module.

### reflector/XLXHosts.txt

```
123;1.2.3.4;4001
```

* `123` — the XLX reflector number.
* `1.2.3.4` — the XLX reflector IP address.

### Other files

Should be downloaded on regular basis from:

* https://www.radioid.net/static/user.csv
* https://www.radioid.net/static/nxdn.csv
* https://radioid.net/static/dmrid.dat

## Running

```bash
cd reflector
NXDNReflector NXDNReflector.ini &
NXDN2DMR NXDN2DMR.ini &
```
