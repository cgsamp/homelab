# Dell Poweredge T620

[Bill of Materials]()
Dell PowerEdge T620 ordered used for just under $3,000 in 2018.

Of note:

* 256 GB of RAM - 16x16GB 2RX4 PC3-12800R
    * 16 modules of 16GB each
    * PC3-12800R
        * R means Registered - https://en.wikipedia.org/wiki/Registered_memory
        * PC3-12800 is a type of DDR3-1600 memory DIMM
            * https://en.wikipedia.org/wiki/DDR3_SDRAM
            * 1600 is the Transfer Rate in MT/s - the number of millions of operations per second
            * 12800 is MB/s bandwidth in Megabytes (not bits) per second
    * In early 2024, the most popular server memory on Newegg is Kingston 32GB ECC Registered DDR5 4800 (PC5 38400) for $120. Each module in this T620 was $45, refurbished. So they are approximately the same cost per gigabyte, but modern RAM is at least 4x as fast.
    * The memory is configured in such a way that each processor has direct access to half of it.

* 2x 2.5 GHz Hex-Core Intel Xeon Processor with 15MB Cache--E5-2640
    * Two processors with six physical cores each, 12 logical cores each
        * https://unix.stackexchange.com/questions/88283/so-what-are-logical-cpu-cores-as-opposed-to-physical-cpu-cores
    * Intel Xeon E5-2640
        * https://ark.intel.com/content/www/us/en/ark/products/64591/intel-xeon-processor-e5-2640-15m-cache-2-50-ghz-7-20-gt-s-intel-qpi.html
        * https://en.wikipedia.org/wiki/List_of_Intel_Xeon_processors
        * Manufactured between 2012 and 2020, officially EOL 2020.
        * About $880 new, I purchased for $60 each in 2018. In 2024, they sell for ... well mine is V1 and all I see is V3 for $7.
        * They are Sandy Lake architecture and use the LGA2011 socket.
        * https://en.wikipedia.org/wiki/LGA_2011
        * Parsing through the Arhiecture and Socket / Chipset is important because that indicates what types of processors will fit in the board. One cannot simply buy a new processor into an old board. It all moves together. I could get a faster/better E5 v1, but not an E5 v2 or anything beyond.
        * This looks like the best processor I could get: https://ark.intel.com/content/www/us/en/ark/products/64622/intel-xeon-processor-e5-4650-20m-cache-2-70-ghz-8-00-gt-s-intel-qpi.html
        * There is one for ten bucks on ebay!

* Drives
    * PERC 720 RAID Controller
        * Connects to SATA HDD or SDD drives
        * I have two consumer SDDs and two enterprise HDDs
        * Recent testing showed that the HDDs are faster than the SDDs? Need to investigate
    * PCIe
        I bought 2 modern nvme flash drives and installed them using PCIe 4x cards. They work fine and are fast!

## Bill of materials additions

2x NVME 2GB SDD + PCIe 4 adapter


## Original Bill of materials

ESXi Host: Refurbished Dell PowerEdge T620 8-Port (Configure To Order)

	2x 1TB consumer flash drives


	256GB Memory Upgrade Kit (16x16GB) 2RX4 PC3-12800R $720.00
	1 x Dell PowerEdge T620 8-Port Chassis $900.00
	1 x 2.5 GHz Hex-Core Intel Xeon Processor with 15MB Cache--E5-2640 $60.00
	1 x 2.5 GHz Hex-Core Intel Xeon Processor with 15MB Cache--E5-2640 $60.00
	1 x PERC H710P 1GB Lvl 0-60 PCIE RAID $350.00
	1 x 3TB 7.2K RPM SAS 3.5" Dell Hard Drive $95.00
	1 x 3TB 7.2K RPM SAS 3.5" Dell Hard Drive $95.00
	1 x No HDD / Dell 3.5" Filler Only $0.00
	1 x No HDD / Dell 3.5" Filler Only $0.00
	1 x No HDD / Dell 3.5" Filler Only $0.00
	1 x No HDD / Dell 3.5" Filler Only $0.00
	1 x No HDD / Dell 3.5" Filler Only $0.00
	1 x No HDD / Dell 3.5" Filler Only $0.00
	1 x No RAID Installation $0.00
	1 x Dell Dual Internal SD Card Reader w/ two 8GB SD Cards $120.00
	1 x iDRAC7 Enterprise License (600+ Series) - Remote Console Access, Power Control, and ISO Mounting $350.00
	1 x On-Board Dual Port 1GbE LOM $0.00
	1 x No Additional NIC $0.00
	1 x Dell Half-Height SATA DVD-ROM Optical Drive Included $0.00
	1 x No Media $0.00
	1 x (2) Dell 12G 750 Watt PSU $90.00
	1 x No Bezel $0.00
	1 x No VMware $0.00

	Subtotal
	$2,840.00
	Shipping & Handling
	$60.00
	Grand Total
	$2,900.00



