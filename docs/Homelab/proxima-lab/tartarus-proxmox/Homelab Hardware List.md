# Tartarus Hardware

## Synopsis

The tartarus server is a collection of consumer and enterprise grade equipment. Here are some hardware references:

## ASUS P11C-M/4L

Main server MOBO was a mistake due to low number of PCIe lanes, poor IOOMU and lack of iGPU passthought.

https://servers.asus.com/products/Servers/Server-Motherboards/P11C-M-4L#Specifications

An example of a home-server build with this motherboard:

https://www.reddit.com/r/unRAID/comments/huof80/thanks_for_all_the_help_new_unraid_server_is/

### Limitations of C242 Chipset

*"The number of PCIe lanes for this chipset series is rather low, limiting the possibilities to upgrade. This may or may not be a problem for your particular use case. (For instance, you cannot have 10Gb ethernet, a GPU for transcoding video streams/passthrough to VM, and a SAS HBA to be able to add more hard drives.) Also, be aware that if you want to use two M.2 nvme drives with this board, they will both be limited to two lanes."* 

Ref: https://www.reddit.com/r/HomeServer/comments/ecmvfb/gigabyte_c246mwu4_micro_atx_board/ (Credit: naamval)

## ASUS ASMB9-iKVM

IPMI for ASUS P11C-M/4L. 

https://www.asus.com/uk/Commercial-Servers-Workstations/ASMB9-iKVM/

## RAM

The board/CPU for ASUS P11C-M/4L only takes _unbuffered_ ECC RAM, which is uncommon on the enterprise server market.

RAM: Kingston Server Premier 16GB (1x 16GB) 2666MHz (KSM26ED8/16HD):

https://www.kingstonmemoryshop.co.uk/kingston-ksm26ed8-16hd-16gb-ddr4-2666mt-s-ecc-unbuffered-memory-ram-dimm

## Getting Started with the LSI 9220-8i

Not my particular HBA card - but this is great resource for why is this necessary:

https://www.servethehome.com/ibm-m1015-part-1-started-lsi-92208i/

### Alternatives

* https://www.kingstonmemoryshop.co.uk/motherboard/asus/p11-series/asus-p11c-m4l-motherboard
* https://www.kingstonmemoryshop.co.uk/kingston-ksm26ed8-32hc-32gb-ddr4-2666mt-s-ecc-unbuffered-ram-memory-dimm