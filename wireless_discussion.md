# FreeBSD Wireless Monthly Discussions

## Discussion #1 - Tuesday, December 3, 2024 at 20:00 UTC

### Attendees
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

## Discussion #2 - Wednesday, January 22, 2025 at 16:00 UTC

### Attendees
- [X] Adrian Chadd
- [X] Alice Sowerby
- [ ] Alvin Chen
- [X] Bjoern Zeeb
- [X] Cy Shubert
- [X] Ed Maste
- [X] Joe Mingrone
- [X] Li-Wen Hsu
- [X] Tom Jones

### Comments/Updates

- Adrian

  * rtwn(4) fixes and 11ac support
  * what's currently left for review
      * RTL8192EU fixes
      * AMRR clean-up
  * what's coming up for review
      * transmit rate refactoring
      * MVP 11ac rate control
      * rtwn(4) 11ac TX
  * what needs some discussion
      * ioctl ABI breakage before stable/15
      * get ready for 256/384 bit encryption keys, AES-GCMP 128/256 bit support, AES-CCMP 256 bit support
      * proper TX rates in ioctl/ifconfig for 11n/11ac
      * any extra VHT information we want available to userland
  * FC's iwx code
      * I've put it in github (https://github.com/erikarn/iwx)
      * works on my AX210 wifi
      * some initial comments on it
  * What I'm working towards:
      * better net80211 rate control (port ath_rate_sample, openbsd's rate control, fix up APIs, etc)
      * MFP support (management frame protection)
      * WPA3-SAE support (requires MFP, needed for 6GHz)
      * channel representation cleanup
      * Remove global TX lock in net80211, refactor seqno allocation, push it into driver
  * ToDos
    * i can prio the seqno refactoring higher to remove the net80211 tx locking, and allow tx queuing / delayed transmitting stuff in net80211; would unblock linux stuff too
    * rtwn radiotap HT/VHT field support?
    * yes ok I will go through the old wifi PRs in Jan/Feb
    * braindump for waterfall towards some concrete goals, eg 11ac, 11ax, etc

- Alice:
https://github.com/FreeBSDFoundation/proj-laptop Ed suggested that I could attend this call as there was a wish for some input on how to collate and organise work going forward. I've been doing something similar with the cloud native (OCI) group and can potentially show that on the call by way of example. Otherwise, as this is a technical call I wouldn't expect to be a regular attendee.

- Alvin

- Bjoern

- Cy

- Tom
    - working on iwx port from openbsd incorporating changes from Future Crew.
    - ht/20 is working
    - 80211abg is working
    - firmware crashes are the main issue right now for wider testing

- Li-Wen
    * Still trying to push Realtek & Mediatek
        * share spec with us, even under NDA
        * officially permit their engineers answer our questions
        * hope to have response after Lunar New Year
        * if possilbe, have the Linux driver release under dual license
    * It's hard for Dell to open their wifi work currently, due to license issue and needs to clean up.
    * The intern working on syzkaller/net80211 is implementing some necessary commands in netlink (inject frame, join IBSS, etc.)
    * Any project ideas for a new graduate who has experience with wtap(4)?
        * e.g. 802.11 k/v/r ?
        * setting up testbed in Kitchener?
        * radiotap for rtwan(4) (HT/VHT fields)

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

* jsm's mt7601 11n usb driver, in review

## Discussion #3 - Wednesday, February 22, 2025 at 16:00 UTC

### Attendees
- [x] Adrian Chadd
- [ ] Alice Sowerby
- [ ] Alvin Chen
- [x] Bjoern Zeeb
- [ ] Cy Shubert
- [x] Ed Maste
- [x] Joe Mingrone
- [x] Li-Wen Hsu
- [x] Tom Jones

### Comments and Updates

- Adrian
    - Status of self-assigned ToDos?
    - Slow progress on #1
    - It would be really good getting eyballs on the issue where kernel panics
      from X are not viewable.
    - Ed: This used to work, but it's a regression in a drm update.  We've had
      Mitchell Horne tring to get hrs's USB debug into the tree which would
      allow us to debug the crash and also use it to debug the debugger.  It's a
      valid, but tricky situation to resolve.
    - Tom: Mitchell says it didn't work.
    - Ed: On specific hardware it does.  If we can find some model to demo that
      it works on Windows or Linux and use it to debug the VT switching issue,
      that would be good.
    - Tom: I stared setting this up last week.
    - Adrian: I would also like to have kernel crashing during VT switching.
    - bz: I know it works on my laptop b/c I tried hrs's patch before.
    - Tom: I would like it if we could get suspend/resume in quemu.  Right now
      it doesn't work very well.
    - bz: TODO: I can try it out in the next days.
    - Ed: If we can at least have it in the tree and if bz has hardware that's
      known to work.... It's been a long time where it's been in an uncertain
      state.

    - Mediatek driver for the mt7601 USB landed a few weeks ago.  fwget was the last
      roadblock.

    - I will be working on the sequence handling next to help unblock Bjoern.

- Bjoern
    - Plan for old wireless PRs?  Mark Linimon has started to clean them up.  Adrian
      picked some up as well.  The meta-pr is helpful to get the bigger picture.

    - More discussion about porting Linux drivers to native drivers?  Trying to
      change the datapath is somsething we didn't try.  It would be interesting
      to see if someone could do a project to investigate.

      Adrian: I wrote a shim layer.. you can write an intermediary layer.  The
      Linux devs don't want to add accessor methods becasuse it was viewed as
      extranious overhead.  Turing skbs in and out of mbufs is really hard.
      There are enough weird semantic diffs....???
    - Updates on jsm's mt7601 11n usb driver, in review?

    - Roaming question?  I've been using my own code.. it won't roam.
    
      Adrian: There are a bunch of different paths to make it work. You have to
      do a background scan.  A lot of plumbing has to be done.  I got that all
      mostly working a while ago.  The second part: supplicant has to do
      preauth.  Depending on which way you do roaming...???
    
      I don't think it's too hard to do dumb roaming....
    
      Adrian TODO: Create a wiki page for roaming (Created a skeleton page
      during the meeting.)
    
    - WTAP question?
    
      bz: Can I just go through these reviews and close them.
    
      Li-Wen: Student wanted to return for a Canadian working holiday, but he
      can't because of changes to Canadian immigration.  He'll stay with his job
      at Canonical.
    
      bz: Do you mind if I do that work.
    
      Li-Wen: If you have time, that would be great.
    
    - Development progress?

- Tom
    - My iwx work is almost ready for review.
    - Not getting same rates as Adrian.
    TODO: Adrian to send list of devices to Tom.

- Li-Wen
    - Talking to Mediatek friend to see if we can get datasheet of MT7922
      (wifi6) and MT7925 (wifi7) used in Framework Laptop/Desktop AMD models.

## Discussion #4 - Wednesday, March 26, 2025 at 15:00 UTC

- [ ] Adrian Chadd
- [ ] Alice Sowerby
- [ ] Alvin Chen
- [ ] Bjoern Zeeb
- [ ] Cy Shubert
- [ ] Ed Maste
- [ ] Joe Mingrone
- [ ] Li-Wen Hsu
- [ ] Tom Jones

### Comments and Updates

- Adrian

- Bjoern

- Cy

- Tom
