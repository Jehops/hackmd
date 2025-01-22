# FreeBSD Wireless Monthly Discussions

## Discussion #1 - Tuesday, December 3, 2024 at 20:00 UTC

### Invitees and Attendees
- [X] Adrian Chadd
- [X] Bjoern Zeeb
- [X] Ed Maste
- [X] Joe Mingrone
- [X] Tom Jones

### Noteworthy Items

- Adrian created [a wiki page for net80211 ALQ logging](https://wiki.freebsd.org/WiFi/AlqLogging).

- Li-Wen shared information about Alvin Chen's Dell ThinOS group after the meeting.

    Alvin's team has directly ported WiFi6 for Intel and Realtek chips
    from Linux.  Their stack may have large differences from ours, but they are
    willing to discuss integration with us.  They are interested in knowing plans
    for the net80211 API and to see how they can collaborate with us.

    Bjoern is curious how they ported the entire GPL stack (clean room) to a BSD
    license and how they plan to update it.

    Li-Wen is trying to determine this.  Alvin is also putting in effort to
    convince people within the company to work with us.  Ideally they could have
    an NDA with the Foundation and share a private repository with those who
    sign the NDA.  That way, we could inspect their code and cherry-pick useful
    parts.  As is typical in these situations, they also don't want to diverge
    too far from the vanilla FreeBSD kernel.  From Li-Wen's past calls with
    them, they are comfortable upgrading FreeBSD versions every two years,
    aligning with our .0 releases.  However, porting and updating both the Linux
    layer and the FreeBSD ABI/KBI is too challenging.

## Discussion #2 - Wednesday, January 22, 2025 at 15:00 UTC

### Invitees and Attendees
- [ ] Adrian Chadd
- [ ] Alice Sowerby
- [ ] Alvin Chen
- [ ] Bjoern Zeeb
- [ ] Cy Shubert
- [ ] Ed Maste
- [ ] Joe Mingrone
- [ ] Li-Wen Hsu
- [ ] Tom Jones

### Updates

- Adrian

- Alvin

- Bjoern

- Cy

- Tom

### Topic for Discussion: Porting Linux wireless drivers to native FreeBSD drivers.

Bjoern says,

> Another interesting -- possibly research only -- item would be how hard would
> it be to directly take the Linux drivers and port them natively (without other
> BSDs and mangling involded).

> And by that I may not mean the entire 802.11 stack work but maybe the data
> path (skb vs. mbuf) -- an abstraction we have come to in the wired world.  As
> that may be something we could ask vendors to split off possibly (especially
> if we were to do the work)?

> So take what is in sys/contrib/dev/ and "mbuf-tize" it in a way that it could
> be "unifdefed" or similar for the skbuff world?  I do not think yet that it
> may be possible to completely have a driver "common" and an OS-part easily --
> though I know some original vendor drivers not as-in Linux have some
> abstractions for that (or had in the past).

> Given we have three people porting Linux drivers to FreeBSD in different ways
> it would be interesting to compare notes on this.

### Investigate old Wireless bugs

Some useful places to start:

- [Bug 273622 - LinuxKPI based wireless drivers meta-bug](https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=273622)
- [Wireless Bugs](https://bugs.freebsd.org/bugzilla/buglist.cgi?bug_status=__open__&component=wireless&list_id=793440&product=Base%20System&query_format=advanced)

### Other Noteworthy Items

