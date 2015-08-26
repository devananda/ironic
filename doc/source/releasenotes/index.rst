4.0.0   First semver release
============================

This is the first semver-versioned release of Ironic, created during the
OpenStack "Liberty" development cycle.  It marks a pivot in our
versioning schema from date-based versioning; the previous released
version was 2015.1. Full release details are available on Launchpad:
https://launchpad.net/ironic/liberty/4.0.0

* Raised API version to 1.11

  v1.7 exposes a new 'clean_step' property on the Node resource.
  v1.8 and v1.9 improve query and filter support
  v1.10 is a bug fix for Node logical names
  v1.11 changes the default state of newly created Nodes from AVAILABLE to ENROLL

* Support for the new ENROLL workflow during Node creation

  Previously, all Nodes were created in the "available" provision state - before
  management credentials were validated, hardware was burned in, etc. This could lead
  to workloads being scheduled to Nodes that were not yet ready for it.

  Beginning with API v1.11, newly created Nodes begin in the ENROLL state,
  and must be "validated" and "provided" before they are made available for provisioning.
  Clients must be updated to handle the new workflow when they begin sending the
  X-OpenStack-Ironic-API-Version header with a value >= 1.11.

* Migrations from Nova "baremetal" have been removed

  After a deprecation period, the scripts and support for migrating from
  the old Nova "baremetal" driver to the new Nova "ironic" driver have
  been removed from Ironic's tree.

* Removal of deprecated vendor driver methods

  A new @passthru decorator was introduced to the driver API in a previous
  release. In this release, support for vendor_passthru and
  driver_vendor_passthru methods has been removed. All in-tree drivers have
  been updated. Any out of tree drivers which did not update to the
  @passthru decorator during the previous release will need to do so to be
  compatible with this release.

* Introduce new BootInterface to the Driver API

  Drivers may optionally add a new BootInterface. This is merely a
  refactoring of the Driver API to support future improvements.

* Several hardware drivers have been added or enhanced

 - Add OCS Driver
 - Add UCS Driver
 - Add Wake-On-Lan Power Driver
 - ipmitool driver supports IPMI v1.5
 - Add support to SNMP driver for "APC MasterSwitchPlus" series PDU's
 - pxe_ilo driver now supports UEFI Secure Boot (previous releases of the
   iLO driver only supported this for agent_ilo and iscsi_ilo)
 - Add Virtual Media support to iRMC Driver
 - Add BIOS config to DRAC Driver
 - PXE drivers now support GRUB2


2015.1.0    OpenStack "Kilo" Release
====================================

Release notes: https://wiki.openstack.org/wiki/ReleaseNotes/Kilo#OpenStack_Bare_Metal_service_.28Ironic.29


2014.2.0    OpenStack "Juno" Release
====================================

Release notes: https://wiki.openstack.org/wiki/Ironic/ReleaseNotes/Juno

