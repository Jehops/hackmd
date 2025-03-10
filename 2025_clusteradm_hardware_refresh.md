# Clusteradm 2025 Hardware Refresh

## 6x geegee-equivalent configurations
- Intel(R) Xeon(R) Silver 4314 (1 socket, 16 cores)
- 128G RAM
- 4x 1TB SSD
- Intel X710 (copper ports)
- These were about US$6K or so.

These machines will be general-purpose jail hosts for public-facing services
(e.g. Bugzilla, Phabricator, etc).  When the services move out of New Jersey,
we'll turn the machines in New Jersey off.  We can consolidate some services.
We're a bit sparse in New Jersey because the machines we have there are old, and
there are other trade-offs.

## 4x admin-equivalent configuration
- But without the 4x Ethernet card
- And with bigger drives
- Intel(R) Xeon(R) E-2334 (1 socket, 4 cores)
- 32G RAM
- 2x 1TB SSD
- Intel X710 (copper ports)
- These were about about $4K or so.

These machines are for more modest workloads (DNS, Kerberos, LDAP, SSO,...).
The plan is to move the services out of New Jersey and turn off the machines
when they're gone.

## 2x beefy-equivalent configuration
- Intel(R) Xeon(R) Silver 4314 (2 sockets, 16 cores)
- 512G RAM
- 2x 2TB SSD
- Intel X710 (copper ports)
- These were about $10k or more.

One of these will replace releng[1-3].nyi for the release engineering team to
build releases.  They currently have three machines, but with current-generation
hardware, they only need one.  The other one will be the pkgbase builder.  We're
now building pkgbase packages on a machine coopted from the pkgmgr team.  That
machine (costaud01.chi) should become a pkgexp builder again (gohan06.chi).

## 1x lower spec admin-equivalent configuration
- This is the extra 13th server
- Intel(R) Xeon(R) E-2334 (1 socket, 4 cores)
- Or lower.  See if they will sell us a 2 core box.
- 16G RAM
- 2x 500G SSD
- Intel X710 (copper ports)
- Spend at most $3k on this system.

This would be a firetruck box.  I thought about shipping an older, lower-spec
box from New Jersey.  We don't have anything serviceable.  All our idle and
mostly idle kit in New Jersey is end of life and needs to be turned off when
we're done with it.

For the firetruck, we need a low-spec 1U box that "just works".  It'll be
sitting idle pretty much all the time.  Except when we really need it.  So it
does need to be an actual server chassis.  No cutting corners with a single PDU.
That only increases the effort we need over time to keep it running.  Time is
our most precious resource.

## Notes
All these machines are to be delivered to Chicago.  The Asus boxes we have there
work.  They're the devil we know.  If we want to stick with iXSystems that's
acceptable.  However, if prices are good from Dell or Supermicro, they would be
a bit easier to set up.  It's not an issue either way since we've made
everything from iXSystems work.
