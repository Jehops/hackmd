# FreeBSD Wireless Monthly Discussions

## Discussion #11 - Wednesday, November 26, 2025, at 16:00 UTC

- [ ] Adrian Chadd
- [ ] Alice Sowerby
- [ ] Alvin Chen
- [ ] Bjoern Zeeb
- [ ] Cy Shubert
- [ ] Ed Maste
- [ ] En-Wei Wu
- [ ] Joe Mingrone
- [ ] Li-Wen Hsu
- [ ] Tom Jones

### Action Items

### Comments and Updates

#### Adrian

#### Bjoern

#### Li-Wen

#### Tom

## Discussion #10 - Wednesday, October 29, 2025 at 15:00 UTC

- [x] Adrian Chadd
- [x] Alice Sowerby
- [ ] Alvin Chen
- [x] Bjoern Zeeb
- [x] Cy Shubert
- [x] Ed Maste
- [ ] En-Wei Wu
- [x] Joe Mingrone
- [x] Li-Wen Hsu
- [x] Tom Jones

### Action Items

- [ ] Adrian to review Bjoern's email summary about Wi-Fi state machine issues and provide feedback based on his experience.
- [ ] Adrian to look into the Wi-Fi compliance test bench interface and share findings with the team.
- [ ] Adrian to write a wiki page for wireless regulatory domains topics


We reviewed the action items from the previous meeting.
Li-Wen committed the wlanstat(1) renaming patch.
Adrian still has a few items pending since he was sick last month.

### Comments and Updates

#### Li-Wen

Li-Wen asks Bjoern whether the call for testing includes the MediaTek card?
It does not.

Discussions about whether the MeditTek card works in Linux.
It does with a newer kernel.
Daniel from Framework is using Fedora.

Ed mentions the new Framework he'll soon be getting.
He has to order components.
We're hoping olce will do some LinuxKPI work to support the mt76.

En-wei is working with us since last week and one of the first things is rebase pending wtap(4) patches.
Future work:
    - stable interface of wtapctl(8) and push to main
    - future work: adding features like signal strength and distance.

#### Adrian

George sent me a Framework laptop to try out some of the bootloader speed issues on, and I've been testing on other laptops.
I've got to do the Frameworks laptop this week before I hand it off to Colin, but I do have a laptop here.
I think I know what the problem is and what the solution needs to be.

Joe: For the slow bootloader, you should coordinate with Thomas Soome, if you already haven't.
He also has a good idea what the problem is and what needs to be done.
I committed a temporary workaround for the Frameowork 16.
Bjoern found a corner case that it doesn't help, though.

Some bioses map the frame buffer region as non-cacheable, which turns every memory access into a slow memory transfer.
I've got some local patches.
Framework should just fix their BIOS to make the video frame buffer cached.

Adrian has made progress on the encryption cleanup and the packet encryption API documentation.
I want to introduce the MFP crypto keys, even though they don't do anything.
I want to at least get the APIs brought up, but if I want to add two more keys to the list, a whole lot of code will get very sad, because it sometimes it'll think that those keys are valid, normal, unicast keys, so it's forcing me to go do a cleanup.
Hopefully I can get the rest of the key cleanup stuff done, early November, and then I can introduce the, MFP key API, so that I don't know if anyone's noticed, but, every time that you start WPA Supplicant, it complains that two key IDs are invalid.

#### Tom

No Wi-Fi updates from Tom.

#### Bjoern

I got the driver updates in.
I gave a talk at EuroBSDCon.
There's an RTW89 issue that I will fix for the release.
I'm doing 11AC for RealTek, and the MediaTek driver.
I hope to coordinate the NetBSD people and talk about reducing the 802.11 diff.

#### Alice Sowerby/Ed Maste
We would like to get suggestions to be added to a roadmap to go into 2026 for the Foundation's Laptop project.

## Discussion #9 - Wednesday, August 27, 2025 at 15:00 UTC

- [ ] Adrian Chadd
- [x] Alice Sowerby
- [ ] Alvin Chen
- [ ] Bjoern Zeeb
- [x] Cy Shubert
- [x] Ed Maste
- [ ] En-Wei Wu
- [x] Joe Mingrone
- [x] Li-Wen Hsu
- [x] Tom Jones

### Action Items

- [x] Li-Wen to introduce Adrian to Framework laptop representatives for potential collaboration on EFI/BIOS issues.
- [x] Li-Wen to find the notes about Framework's debug interface on desktop/12" models and point out for Tom
- [x] Li-Wen to finish the wlanstat(1) renaming patch
- [ ] Adrian to review Bjoern's email summary about Wi-Fi state machine issues and provide feedback based on his experience.
- [ ] Adrian to look into the Wi-Fi compliance test bench interface and share findings with the team.
- [ ] Adrian to write a wiki page for wireless regulatory domains topics
- [x] Tom will update the WiFi wiki page with WiFi cards supported.

### Comments and Updates

- Alice Sowerby
    - Can this group make regular checks and update the wiki page https://wiki.freebsd.org/WiFi/ with supported WiFi cards and workarounds.
    - Also other info as needed to keep it useful and fresh.
    - (Li-Wen) should we also work on https://www.freebsd.org/releases/15.0R/hardware/#wlan ?

- Cy Shubert
    - No wirless updates; dealing with Kerberos issues.

- Li-Wen Hsu

    * still working on the actions items
    * Don't have too much updats, will try out single usb device bhyve passthuru in wifi testbed
    * En-wei will start in Kitchener 2nd half next month
    * OT: tried a little bit with Meshtastic/LoRa when working with local community, would be nice to be used on FreeBSD with bluetooth

- Tom Jones
 
    - Working on the kismet port.  Due to the state of pkg, there are many missing package depdendencies, which makes progress challenging.
 
     - I was speaking to Framework today about debugging interfaces and they have enabled cpu uart on the ai 300,  framework 12 and framework desktops. This should enable low level debugging to resovle pcie bus and suspend issues. 
     - I'm trying to help them debug, but I need more information on what the hardware is, what it should support or what the crashes are.

## Discussion #8 - Wednesday, August 6, 2025 at 15:00 UTC

- [X] Adrian Chadd
- [ ] Alice Sowerby
- [ ] Alvin Chen
- [X] Bjoern Zeeb
- [X] Cy Shubert
- [X] Ed Maste
- [ ] En-Wei Wu
- [X] Joe Mingrone
- [X] Li-Wen Hsu
- [X] Tom Jones

Review Action items from Discussion #7

### Action Items

- [ ] Adrian to review Bjoern's email summary about Wi-Fi state machine issues and provide feedback based on his experience.
- [ ] Adrian to look into the Wi-Fi compliance test bench interface and share findings with the team.
- [ ] Adrian to write a wiki page for wireless regulatory domains topics
- [ ] Li-Wen to introduce Adrian to Framework laptop representatives for potential collaboration on EFI/BIOS issues.

### Comments and Updates

- Adrian Chadd

Life was busy.  Kept my diff stack up to date.  Been testing out 11ac AP mode to find corner cases, but haven't found anything that breaks the stack.

- Alice Sowerby

    I was speaking with Ed the other day and he mentioned that it would be
    helpful to have a public list of supported WiFi drivers somewhere. To
    contain information such as Hardware type/driver/WiFi standards
    supported. What do people think?  If liked, how do we plan to make the first
    version and processes to keep it up to date, receive feedback and questions
    etc.

    bz: the release notes generated from man pages is the best we currently have:
        https://www.freebsd.org/releases/14.3R/hardware/#wlan
        
    emaste: The wiki is not the right place.
        
    thj: There's https://bsd-hardware.info/?d=FreeBSD
    bz: There's a wireless database at ???
    
    emaste: The Github repo for bsd-hardware.info is stale.  Some things stopped updating with FreeBSD 12.
       
- Bjoern Zeeb
    - begrudged done installer fix for wifi/regdomain (sorry I don't like bsdinstall)
    - Mediatek / PCI debugging; jhb helped; the card's PCI stack goes off to lunch on certain actions
    - Suspend/resume for iwlwifi:
        - the LinuxKPI framework works
        - my test laptop (even without) no longer s/r properly (drm, wifi, other?)
        - pulled in the latest USBDbc and applied fixes to help with first debugging; problem now, xhci gets suspended along and needs a "quirk" 
    - TKIP Errata Notice for 14.3
    - Found more edge cases in LinuxKPI and net80211 panics eating dogfood
        - fixes in LinuxKPI
        - had to turn bgscan off again until locking is fixed
        - HT teardown is also a more constant source of panic
        - adjusted MC updates in LKPI
        - rx csum offloading would be nice but (a) we get a full frame csum now(?), and (b) there are data corruptions
    - net80211 changes for ioctl code to drivers (D51399); pass vap (==ifp) instead ic
    - Trying to sort more net80211 'tech debt' to undo LinuxKPI workarounds and move forward
    - MFCs to stable/14
    - Stabweek is done, working on flushing my tree; blocked on drm vs. LinuxKPI pci; PR out but likely need alternate solution
    - Got an updated iwlwifi to match rtw8x and mt76 version
    - Took time off to debug a cam/sdio problem so that I can try to get SDIO sorted
    - Would love to update LinuxKPI/USB from last year and see if we can get the "breaking bits" in before 15 too?
    - Would love to pull in Linux 6.16 drivers before 15?
    - Funny throughput TCP RX funkyness; need to talk more to tuexen

    - Has anyone figured out why the be200 doesn't work with the Framework?  The Framework will refuse to boot.

- Cy Shubert

Plan on deprecating WPA supplicant 2.9 in ports and have it expire at the end of the year.

- Li-Wen Hsu

Wireless testbed is still a WIP.  The wlanstat(s) renaming patch will be ready for review soon.

- Tom Jones

Nothing on Wi-Fi lately.  Was debugging mesh and started updating net-mgmt/kismet port.  Are there other Wi-Fi tools that need updating?

Adrian: Just kismet.

## Discussion #7 - Wednesday, June 25, 2025 at 15:00 UTC

- [X] Adrian Chadd
- [ ] Alice Sowerby
- [ ] Alvin Chen
- [X] Bjoern Zeeb
- [X] Cy Shubert
- [X] Ed Maste
- [X] En-Wei Wu
- [X] Joe Mingrone
- [X] Li-Wen Hsu
- [ ] Tom Jones

### Action Items

- [X] Bjoern to send email about breaking KBI for Wi-Fi improvements in FreeBSD 15 and 16.
- [ ] Adrian to review Bjoern's email summary about Wi-Fi state machine issues and provide feedback based on his experience.
- [ ] Adrian to look into the Wi-Fi compliance test bench interface and share findings with the team.


- [x] Bjoern to create a wiki page for documenting minor Wi-Fi issues and known problems.
- [ ] Adrian to write a wiki page for wireless regulatory domains topics

### Comments and Updates

- Adrian

    We shouild clean up regulatory domain stuff for 16.

- Bjoern
    - For regulatory domain, we should change the default from FCC US.
    - 14.3 "support fallout"  (one thing is regdomain)
    - ACPI for LinuxKPI so that iwlwifi / rtw89 compile and can query
    - HE (11ax) structs/defines  LinuxKPI -> net80211
    - IE lists update + decoding in ifconfig
    - Documentation updates (man pages, release notes for 15, ..)
    - Merges to stable/14
    - LinuxKPI scanning
    - iwx bits
    - RSSI / S:N, not sure yet if I want it this way or preserve signal
    - LinuxKPI crypto bits
    - RX path
    - Looking into how to solve some of this in net80211 insead of working around in LinuxKPI
    - Short amount to see if I can get mediatek FW to come alive
    - Further LinuxKPI non-802.11 change to be upstreamed
    - Looking at the PCI changes vs. drm-kmod again for suspend/resume
    - I have reviews to do for LinuxKPI and net80211

- Cy

- En-Wei

    - Rebase https://reviews.freebsd.org/D36243 on FreeBSD 15-CURRENT

- Li-Wen
    - wireless testbed
      - WIP for automatic testing after ci.freebsd.org
      - https://hackmd.io/mP8LC4hnSNyObiPufrMcxg?view
      - Intel AX210
      - Intel 8xxx
      - USB rtl8912 (cannot passthru due to only one usb controller)
    - wlanstat(s)

- Tom

## Discussion #6 - Wednesday, May 28, 2025 at 15:00 UTC

- [x] Adrian Chadd
- [x] Alice Sowerby
- [ ] Alvin Chen
- [x] Bjoern Zeeb
- [x] Cy Shubert
- [x] Ed Maste
- [x] Joe Mingrone
- [x] Li-Wen Hsu
- [x] Tom Jones

### Action Items

#### Overview

We discussed stable KBIs and breaking changes across versions 15 and 16, with
consensus reached on implementing necessary changes without seeking user
permission.  Wi-Fi support and driver development were discussed, including
discussions about hardware compatibility, testing environments, and various
driver improvements.

- Tom

    Got suspend and review working on iwx and that's in the tree.  It works
    really well and it doesn't crash.  I sometimes have to bring the interface
    up and down multiple times to get it to work.  Sometimes I can force a bunch
    of UPD through it and it works.  Adrian suggested this might be a WPA issue.
    Other than that, I think the iwx import work is done.  There are a few minor
    issues, then we can start working on 160 MHz channels.

- Adrian

    I started testing iwx and iwlwfifi again.  Hopefully I'll give feedback this
    week.  They both don't panic the kernel frequently, which is nice.  I've
    been doing general Wi-Fi stack cleanup.  I'm going to get back up to
    cleaning up trasmit locking stuff.  I'm trying to encourage anyone
    interested to build that community up again.  I've been working on older
    qualcom atheros Wi-Fi stuff.  I've started working on the Qualcom Snapdragon
    laptop.  That's important because a bunch of the later Qualcom Wi-Fi AP
    chips started sharing code with the Snapsrap laptops.  Hopefully over the
    next few months as I bring up more of the AP support we'll have another
    vehicle for testing Wi-Fi AP testing.  I'm going to do a post about that.
    Bjoern: Which Wi-Fi generation do you have now?

    adrian: I have all of it.  I got the Dakota, which is Wi-Fi 5 and I have one
    of each chip after that.  The problem as you go further up, it starts
    looking more like a cell phone chipset, which means I have a lot of drivers
    to bring up before I can even turn on the ath11 knf 12k chipset, which I
    don't mind doing, but it dovetails quickly.

    bjoern: I'm asking because I still have an old phone around and I do have ???
    APs that I'm using, so I can help test.

    Adrian: Ok. Thanks.  I also did buy the first-gen Wi-Fi 5 ath10k AP chipset.
    I bought a couple of PCI cards and my ath10k driver does do cascade, 4x4,
    160 Mhz, and it does multi-user ?? mode.  I should really Finnish my ath10k
    port.  I should finish my ath10k port, and I could probably build 160 mhz
    4x4 AP today if I debugged that driver before.

    tom: That would be nice.  I cannot get openwrt to do this.

    adrian: It's a pain because as soon as you start speaking at 160 mhz, you
    have to be absolutely certain that you choose a channel set that does not
    overlap with DFS.

    tom: I've got a lab.  The configuration that openwrt generates for hostapd
    only does 80 mhz channel.  If I change anything it gives me a completely
    broken AP.  We need a test target for 160.

    adrian: I bought a 160 mhz dlink ap for testing.  Nothing done with it yet.

    tom: I think my arrows?? should, but they don't.

    adrian: arrows won't do 80 because they want more channels to do more mesh
    with and 160 channels take up all the bandwidth and a higher noise ??

    bz: ??

    adrian: Finding a chipset that does 80/80 is difficult.

    bz: I know wrt is able to do it.

    tom: If it's HE80, it should do Vht160?

    adrian: No.  It's the other way around.  If you're doing vht160 that implies the rest down the line.

    tom: HE, not NT.  It's configured to do HE80.  If I change that, I don't get a working AP.

    adrian: It may not let you do that. Send me the details.  I'll look at the
    config.

    ardian: I spent time trying to figure out how to build a flashable image for
    my dlink AP.  The way that you have to it is to create multi-layer uboot
    images where you take a uboot image and embed it inside a uboot image.....
    It gets unpacked as you flash into the right partition.  It was an absolute
    nightmare, but I know have all the basic pieces to flash a Qualcom platform.

    adrian: GCMP hasn't land.  bz have you been able to test it.

    bz: Yes, I did.

- Bjoern

    Let's start with GCMP.  The hardest part is getting FreeeBSD ?? ap working.
    I have to recycle the interfaces??  It's something we should look into.
    I've got GCMP working

- Cy

- Ed

- Li-Wen
  - wireless testbed
    - WIP for automatic testing after ci.freebsd.org
      - https://hackmd.io/mP8LC4hnSNyObiPufrMcxg?view
      - Intel AX210
      - Intel 8xxx
      - USB rtl8912 (cannot passthru due to only one usb controller)
    - wlanstat(s)

## Discussion #5 - Wednesday, April 30, 2025 at 15:00 UTC

- [ ] Adrian Chadd
- [ ] Alvin Chen
- [X] Bjoern Zeeb
- [X] Cy Shubert
- [X] Ed Maste
- [X] Joe Mingrone
- [X] Li-Wen Hsu
- [X] Tom Jones

### Action Items

- Bjoern (will backup from others) will start communication the KBI plan through
  15/16.  We need to keep Adrian in the loop.

- Tom, as part of his Wi-Fi documentation efforts, to look at adding Wi-Fi
  content to the Handbook.

### Comments and Updates

- Bjoern

    Most of my updates are the wireless mailing list.  Basically for 14.3, I've
    merged everything I can now.  I had to merge three changes from Adrian.
    That's one of the open things for this meeting, i.e.. to see how we deal
    with that because Adrian doesn't MFC, and after a year or so you get stuck
    on changes.

    Other that that, it's moving things along for me trying to fix anything that
    comes up with iwlwifi and dealing with technical debt in net802.11 like race
    conditions and lock.  A bunch of PRs can in last night and I try to deal
    with them as soon as possible to keep things moving forward.  iwlwifi also
    needs PCI changes, which I need to do for LinuxKPI, then I can work on
    MediaTek.

    The other big topic is how to deal with 15 and 16. We'll likely change
    things in incompatible ways and I'd like to have a strategy for 15 and 16.
    Otherwise people will be stuck with what we have now for a really long time.

    Tom: What about the expected breaking changes for 15.0?n

    Bjoern: If we do the channel and method cleanups and locking changes it will
    affect all the drivers.  Tom: So we'll basically be stuck with 14.3
    performance and standards in the 15 branch and 16 will get all this stuff?

    Bjoern: I don't know.  This is my question.  Unless we say 15 WiFi is just
    not going to be stable with respect to WiFi.  If you look like what Sam did
    15-20 years ago, it was massive changes and they basically broke everything
    and then in half a year, the next big block of changes came in.  I can't
    deal with more stuff in LinuxKPI now.  I need to start fixing that 802.11
    and getting things into there.  If you want to add 11ac you have to extend
    the structures and other stuff, which is mostly fine I guess, but KPIs will
    change that will affect drivers.  I don't know the solution and I don't know
    what people think about it because if we can declare 15 as unstable then at
    least 15 and 16 can move forward, and 14 would be kind of at the point where
    it is now plus minor bug fixes improvements that we can do. But keeping
    completely at this level is, I think, way too long, because that's gonna be
    another two and a half years before 16.

    Tom: But we do have A/C now in 15.  We do have drivers now, which will do
    almost a gigabit of traffic.  The only things we need are WPA3 and
    everything to support it.  That's the solution to the "this network doesn't
    work at all with FreeBSD" problem.

    Bjoern: How so?

    Tom: We've had reports that people have had to downgrade the security of
    their AP to use FreeBSD WiFi because we don't have WPA3.  But that's the
    only thing I've heard of where there is a hard break where things just don't
    work at all.  People aren't really complaining about it yet.

    Bjoern: We, as the WiFi group have to make a decision at some point.

    Tom: I think we would probably want bigger buy in from Freebsd developers,
    at least because we're going to get all of the fallout right if we say that
    Wi-fi and 15 is not going to be binary compatible.  So there will be
    breakages.  People might just make jokes and say, Well, Wi-Fi, being
    unstable is better than they're not being Wi-Fi like, I don't know how great
    a response we get from anyone, but at least there would be progress right,
    then, no one could say, we're not making things.  We're not working on
    it. If we're breaking it, we're definitely working on it.

    Bjoern: And we will definitely break things, because all the old drivers, if
    you go and look, that's the next question gonna be, how many of them are we
    gonna carry forward because we still have abg drivers, you know, don't even
    do anything. And I understand why we still have them.  The question is, for
    how long are we gonna still have them?  And who can test them?  Because
    testing 40 different devices, I can tell you, is going to take an awful lot
    of time, and we need to have our users do that or eventually say, okay, it's
    broken. We'll fix it if someone comes up and says, hey, it's broken. I still
    have a device running or something, or they come up because even between 3
    of us or 4 of us, we can't do that.  I can't see us doing it. Let's put it
    that way.

    Tom: Yeah, I agree.  It's difficult to get the diversity of hardware in a
    way you can test it as well. But we could do a best effort.

    Bjoern: What I've done for rtw88/89 is, I've loaded the driver I configured
    Wi-Fi to make sure it can pass packets. I made sure, multicast works,
    broadcast works...

    Tom Jones: We probably need to ask Adrian. Adrian might say that breaking
    things is fine.

    Bjoern: And the next question is, do we actually have out of tree Wi-Fi
    drivers, apart from the one that Adrian started 10 years ago.

    Ed: And do we care?  We already don't have a stable KBI in point releases.
    We pretend we do, but we haven't for year.  My view is that we have to be
    transparent about what we're doing.  I can't imagine anyone is going to say
    they would rather have a fixed, broken KBI than working Wi-Fi throughout the
    course of the 15.

    Bjoern: I agree with you and I would love to keep the momentum going and
    move forward.

    Ed: Oh, I'm sure someone is going to say I have a 15 year old whatever-card
    that I rely on, but I'm gonna buy a small collection of the the $15 TP-Link
    USB dongles, and just, I'll mail one to everyone who complains about all
    hardware, not working. :)

    Joe: A dongle for you, and a dongle for you, and a dongle for everyone!

    Bjoern: Yeah, okay. So in theory, we should communicate this, we should just
    go ahead and do this.

    Ed: I think so.

    Tom: Yeah, yeah, I think we we communicate it.

- Tom

    Tom: I had to check when we last met and so, since we last met, I landed
    iwx, which I did right at the start of April.

    There was some fallout around the build which I fixed, and I think from that
    I learned that I wasn't getting any build failures from anything.  So that
    was that was nice.  It means I haven't broken the build for a long time.
    Also I broke the build, and I didn't know about it, and nobody told me.

    I spent a lot of time writing a series of introductory articles on how to do
    Wi-Fi development.

    I'll be writing debugging stuff as I try and debug some of the outstanding
    stuff with iwx like it not always associating very well.  I just need to do
    more testing. And it's quite opaque what's going on.  I've also not looked
    at it for a while for because I've been doing other things.

    I think, going into May. I'm gonna get some semi automated regressions
    together with the machines I have, so that we have more confidence about
    drive by commits from people.  What we would be able to do is get somebody
    with a Wi-Fi change to run a script for us and self report.

    Bjoern: Are you going to look at the Handbook as well?

    Tom: I can, what what needs to be in the Handbook?

    Bjoern: How to use Wi-Fi.

    Tom: Yeah, I can look at a handbook. I'll add it to my todo list.

    Tom: A bigger thing for me is making Wi-Fi testable from Lua, so that we
    have all the bindings in place and we can ask for tests in Lua rather than
    shell scripts which are going to fall apart.

- Cy

    Someone submmited a pull request for WPA supplicant.

- Li-Wen

    Thanks Bjoern for updating the regdomain.  Things working great now in TW.
    I can help the script and contact the regdb maintainer.

    Still working on doc sending to AMD, including ask them to ask Mediatek to
    share info with FreeBSD.

    Any thoughts for setting up a wireless lab (for ci?) in Kitchener? Can
    initialize it in hackathon after BSDCan.

    Can check if my friend at Ubiquiti can stil help for some hardware (not sure
    if it's useful).

    enweiwu@ will be in BSDCan (for 2 days) and Hackathon (for 4 days).  wtap(4)
    rebase and merge is one of the goals.

## Discussion #4 - Wednesday, March 26, 2025 at 15:00 UTC

- [x] Adrian Chadd
- [x] Alvin Chen
- [x] Bjoern Zeeb
- [x] Cy Shubert
- [x] Ed Maste
- [x] Joe Mingrone
- [x] Li-Wen Hsu
- [x] Tom Jones

### Comments and Updates

- Adrian
    - Fixed compilation issue with mtw(4)
    - Working through the GCMP crypto support code reviews and landing what I can
    - Working on CCMP/GCMP crypto refactoring
    - Verified 256-bit CCMP and GCMP crypto locally; interops with Linux fine
    - Various other small code fixes for things that have shown up in ath(4) AP / STA testing
    - Still working towards getting sequence number refactoring done and removing the TX lock, which should improve performance and also make locking easier for drivers / LinuxKPI.
    - The medium term goal is still 802.11ac / MFP (management frame protection); longer term goal is still WPA3/SAE and channel representation / rate representation cleanups for 802.11ax.

- Bjoern

  - LinuxKPI malloc changes to avoid problems with contiguous memory
    regions in progress and pushed;  rtw88 is the best test platform
  - The drm-kmod, really a REDZONE oversight 8 months ago, took time
    off the plate.
  - jsm done mtw firmware port; fwget USB support is still pending
  - Updated the wifi-firmware ports also for iwx but also turning
    hw_crypto/HT/VHT on by default for iwlwifi AXxxx and BExxx chipets.
  - Announced that in-tree firmware will go away in April
  - Started work on suspend/resume for LinuxKPI based drivers
  - Started catching up with TKIP/WEP but also for newer cipher suites
    for LinuxKPI based drivers
  - Reviews for Adrian
  - Dealt with a crypto bug which slipped through review and MFCed
  - Updated iwlwifi to no longer ask people to submit to but check a
    PR about TXQ problems before the next release ships with it
  - TODO: give iwx a try

- Cy

    - Fixed WAP_Supplicant for 13/14.

- Tom
    - iwx is in review: https://reviews.freebsd.org/D49259

- Alvin

- Li-Wen
    - Mediatek team responsible for MT79xx refused our request of accessing the datasheet because their resource is only for the important customers.
        - Trying to ask help from their customers, AMD (via Framework)
    - Realtek is also still WIP, but mainly for wired NIC (5G NIC is used in Framework Desktop)
        - are we interested (and have time) on Realtek's wireless product?
    - Testing AX210 with iwlwifi(4) in -CURRENT on my Framework (intel 13th gen) and Sheng-Yi (aokblast@)'s intel Ultra 1 during 202503 Tokyo hackathon
        - the same chip AX210
        - mine Cannot assoc to 5GHz ap, got ng/na at best
        - Sheng-Yi can assoc to 5GHz ap, but only once after boot
        - some error/crash in firmware
        - will analysis more and provide useful information later

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
