# bus-scsi

Expose SCSI disk information via automatic attributes under the `bus.scsi`
namespace.

## Requirements

This cookbook requires Chef 12.7+.

### Platforms
* Linux with libudev-183+ (tested with CentOS 7)
* Windows (tested with Windows Server 2012R2 & 2016)

## Usage

You just need to load the cookbook to get access to the SCSI automatic
attributes.
* In a cookbook, add a dependency to `bus-scsi` in your cookbook's metadata.
* On a node, add the `bus-scsi::default` recipe to your run-list.

You can disable these attributes by turning the `bus_scsi_disabled` setting to
`true` in the Chef config.

## Attributes

The `bus.scsi` namespace is a hash with one entry per SCSI disk.
For each disk, the hash key is the "host:channel:target:lun" quadruplet and the
value is another hash with the following attributes exposed:

Attribute     | Description
--------------|---------------------------------------------
`host`        | SCSI adapter number
`channel`     | SCSI channel number
`target`      | SCSI id number
`lun`         | SCSI Logical unit number
`model`       | Vendor model string
`fwrev`       | Firmware revision identifier
`serial`      | Disk serial number
`size`        | Size of the disk in bytes
`wwn`         | World wide number identifier (only in Linux)

## Recipes

This cookbook has a single `bus-scsi::default` recipe which does nothing. It can
be used to load the cookbook from a run-list.