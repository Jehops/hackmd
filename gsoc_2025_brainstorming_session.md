# GSoC 2025 Brainstorming Session

## Attendees

- Alan Somers (asomers)
- Amyeric Wibo
- Christos Margiolis (christos)
- Jan Bramkamp
- Dave Cottlehuber (dch)
- Ed Maste (emaste)
- Issac Freund
- Harald Eilertsen
- Joe Mingrone (jrm)
- Li-Wen Hsu (lwhsu)
- Mark Linnimon (linimon)
- Moin Rahman (bofh)
- Olivier Certner (olce)
- Pierre Pronchery
- Robert Clausecker (fuz)
- Tom Jones (thj)
- Warner Losh (imp)

## TODOS

- [X] jrm to contact gnn about the [Example Device Driver in Rust project](https://wiki.freebsd.org/SummerOfCodeIdeas#Example_Device_Driver_in_Rust).  (jrm pinged George on 2025-02-02)
    [Some people have already worked on this](https://wiki.freebsd.org/Rust), so we would need a more specific and properly scoped project.
- [X] jrm to contact markj and lwhsu about the [syzkaller improvements](https://wiki.freebsd.org/SummerOfCodeIdeas#syzkaller_improvements) project to determine whether it's still a viable project? (jrm pinged them on 2025-02-02)
- [ ] lwhsu to discuss with oshogbo whether the [Capsicumization of the base system project](https://wiki.freebsd.org/SummerOfCodeIdeas#Capsicumization_of_the_base_system) can be updated to a new, useful project.  There are certain things around syslog that could be done better like when it needs to re-attach.  There are still may utilities in the base that could be capsicumized. (jrm pinged Li-Wen on 2025-02-02)
- [ ] lwhsu to revise and re-scope the [IPv6 support and cleanup of address family dependency in userland utilities project](https://wiki.freebsd.org/SummerOfCodeIdeas#IPv6_support_and_cleanup_of_address_family_dependency_in_userland_utilities). (jrm pinged Li-Wen on 2025-02-02)
- [X] thj to add new [Port FreeBSD to QEMU MicroVM project](https://wiki.freebsd.org/SummerOfCodeIdeas#Port_FreeBSD_to_QEMU_MicroVM).
- [ ] jrm to draft expanded text for [Port FreeBSD to QEMU MicroVM project](https://wiki.freebsd.org/SummerOfCodeIdeas#Port_FreeBSD_to_QEMU_MicroVM).
- [X] Alan Somers to add new [sockstat UI improvements project](https://wiki.freebsd.org/SummerOfCodeIdeas#sockstat_UI_improvements).
- [ ] jrm to put out a call for a co-mentor to Colin's [Speed up the FreeBSD boot process project](https://wiki.freebsd.org/SummerOfCodeIdeas#Speed_up_the_FreeBSD_boot_process).
- [ ] emaste to update [Improve LLDB on FreeBSD](https://wiki.freebsd.org/SummerOfCodeIdeas#Improve_LLDB_on_FreeBSD) project based on details provided by thj.
- [ ] emaste to add new cd9660 projects for makefs.
- [ ] jrm to look into a potential [IME](https://en.wikipedia.org/wiki/Input_method) project that builds on [this 2021 GSoC project](https://github.com/Cycatz/GSoC2021-VT-IME).
- [ ] Jan to investigate a potential networking project to write [if_epair(4)](https://man.freebsd.org/cgi/man.cgi?if_epair(4)), the missing point-to-point IP (not Ethernet) interface to connect vnet jails for routed instead of bridged networking. (jrm pinged Jan on 2025-02-02)
- [ ] Jan to break up his new [Implement a new VLAN filtering software bridge](https://wiki.freebsd.org/SummerOfCodeIdeas#Implement_a_new_VLAN_filtering_software_bridge) project into multiple appropriately scoped projects.  It seems too difficult for a GSoC project. (jrm pinged Jan on 2025-02-02)
- [X] imp to share his ideas page at the bottom [the GSoC Project Ideas wiki page](https://wiki.freebsd.org/SummerOfCodeIdeas)
- [ ] olce/fuz (after hearing from a developer working on exfat) to determine whether an exfat project is viable for this summer

## Other Potential Project Ideas That Need Investigation and Mentors

- (imp) Something related to UFS (not the file system) that someone from Samsung is looking at
- (Issac Freund) Expand test coverage for pkg
- (Issac Freund) Port [turnstyle](https://github.com/chimera-linux/turnstile) to FreeBSD
- (fuz) Supporting [f2fs](https://en.wikipedia.org/wiki/F2FS) could be an interesting project.  It's popular in phones.
