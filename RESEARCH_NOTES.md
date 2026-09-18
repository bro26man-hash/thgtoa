# RESEARCH_NOTES.md — Podcast Episode: Digital Rights & Surveillance Technology

> **Source project:** [Anon-Planet/thgtoa](https://github.com/Anon-Planet/thgtoa) — *The Hitchhiker's Guide to Online Anonymity & OpSec*
> **Forked to:** `bro26man-hash/thgtoa`
> **Stars:** 849 | **Forks:** 78 | **License:** CC-BY-SA-4.0
> **Website:** https://anonymousplanet.net/

---

## 1. Project Overview

**THGTOA** (The Hitchhiker's Guide to Online Anonymity) is a community-written, open-source guide covering online tracking techniques, identity verification methods, and detailed instructions for creating and maintaining truly anonymous online identities. It is explicitly written for **activists, journalists, scientists, lawyers, whistle-blowers, and people being oppressed, censored, and harassed**. It has no affiliation with the Anonymous collective and is not sponsored by any commercial or governmental entity.

The guide covers:
- **Network anonymity:** Tor, Whonix, Tails, VPN-over-Tor, Tor-over-VPN, bridges
- **Cryptocurrency privacy:** Bitcoin mixing (CoinJoin), Monero, Zcash, atomic swaps
- **Hardware tamper protection:** HEADS firmware, PureBoot, evil-maid defenses
- **Operating system security:** Qubes OS, VM isolation, stack protection
- **Counter-surveillance:** Detecting and defending against tracking devices (ALPR cameras, body cams, BLE trackers, drones)
- **Operational security (OpSec):** Threat modeling, compartmentalization, communication security

The project is maintained by a small, largely anonymous group of contributors. The primary maintainer (`nopeitsnothing`) is a community member (not the original author) who has been working to reorganize the guide into chapters and improve the PDF toolchain.

---

## 2. Societal Concerns & Ethical Tensions

### 2.1 The "You Cannot Trust" Paradigm

The guide's foundational premise — articulated by a community member — is a list of entities you **cannot trust**:

> You cannot trust ISPs. You cannot trust VPS providers. You cannot trust public Wi-Fi providers. You cannot trust Mobile Network providers. You cannot trust VPN providers. You cannot trust any Online Platform. You cannot trust Tor.

This is not cynicism — it's a **threat-modeling framework**. The guide argues that trust should be based on proven technical properties, not brand reputation or legal jurisdiction. This raises a profound question for the podcast: **Is radical distrust of institutions a rational response to documented surveillance, or does it erode the social trust that democracy requires?**

### 2.2 The Bitcoin vs. Monero Debate (Issue #154)

One of the most heated community discussions centered on whether the guide should include **Bitcoin mixing/obfuscation techniques** (CoinJoin, Whirlpool, etc.) or recommend **Monero** as the only truly anonymous cryptocurrency.

**Key arguments from both sides:**

| Pro-Monero (annoyed/ghost) | Pro-BTC-mixing (dan-kir) |
|---|---|
| Monero provides real anonymity; BTC mixing is "silly" obfuscation | XMR isn't accepted everywhere — SR Securities, Signal donations, Mullvad VPN historically |
| "Ultra paranoid" Zcash + Monero is overkill | Sometimes Best Effort匿名 is better than no匿名 |
| Mixing can be de-anonymized with enough resources | The guide itself accepts BTC donations — shouldn't it show how to do so privately? |
| "Closed, see #158" (maintainer's resolution) | Atomic swaps are coming to Samourai/Sparrow wallets |

**Podcast angle:** This debate mirrors a larger societal tension — **the conflict between ideological purity and pragmatic adoption**. If the only truly private tool isn't widely accepted, do you recommend it anyway (potentially isolating users) or recommend the widely-accepted-but-less-private option (potentially creating a false sense of security)? This is the **privacy version of the "vote with your dollars" dilemma**.

### 2.3 The Accessibility vs. Security Conservatism Debate (Issue #31)

A detailed review by `Lefty-Insider` (a person with disabilities who relies on screen readers) called out the guide's **poor PDF formatting, lack of hyperlinked TOC, and inaccessible design**. The maintainer's responses reveal a **deep tension**:

- The maintainer acknowledged the issues but explained that the toolchain (Pandoc → Markdown → PDF) limits formatting control
- A full LaTeX rewrite was planned but never completed (the original author left)
- The guide is **intentionally conservative** in its recommendations — it only suggests tools with "well-understood security properties"

The maintainer stated:
> I'd rather give people a small set of trustworthy options, as opposed to giving people a large set of less-proven options, which could put certain readers at risk if the recommendation turns out to be premature.

**Podcast angle:** This is the **"safety vs. inclusion" dilemma** that recurs across civil liberties movements. How do you make security tools accessible to non-technical users without diluting the security guarantees? When does accessibility become a form of exclusion? And who gets to decide what's "safe enough" — especially when the stakes are literally life and death for some readers?

### 2.4 The Hardware Security Gap (Issues #313, #335)

Two open issues reveal a **critical blind spot** in the privacy guide: **physical hardware security**.

- **Issue #313** requests adding **HEADS** (open-source custom firmware for physical tamper protection) to the guide's section on physically tamper-protecting laptops. The current guide covers software-level defenses but doesn't address firmware-level attacks.
- **Issue #335** highlights that **Windows 11's Hardware-enforced Stack Protection** (a security feature) conflicts with anti-cheat software, creating a dilemma: gamers must choose between **playing games** and **maintaining system security**. The maintainer notes that anti-cheat vendors are "lazy" for not completing Microsoft's vetting process.

**Podcast angle:** The **"security for whom?"** question. Privacy guides often focus on a specific user profile (Qubes OS + Whonix + Tor Browser on a dedicated laptop). But what about:
- **Gamers** who can't disable stack protection without breaking games?
- **People with disabilities** who rely on specific hardware/software configurations?
- **People in authoritarian regimes** who need physical tamper protection because the state can seize their devices?

The guide's implicit user is a **privileged, technically competent, non-gamer with no physical accessibility needs**. That's a problem when the guide is meant for everyone.

---

## 3. Civil Liberties & Surveillance Concerns

### 3.1 The FBI's Drive-By Exploit Precedent

The maintainer explicitly references the FBI's use of **drive-by Firefox exploits** to deanonymize darknet vendors and other targets:

> The FBI has done this before for darknet vendors and other reasons I won't discuss here.

This is a documented civil liberties concern: **law enforcement agencies have deployed zero-day exploits against individuals using privacy tools**, raising questions about:
- **Due process:** Was a warrant required? Was the target identified before the exploit?
- **Scale of surveillance:** If the FBI exploits Tor Browser vulnerabilities, what does that mean for all Tor users?
- **Vulnerability hoarding:** Should governments disclose security flaws to vendors (as per the VEP) or stockpile them for surveillance?

### 3.2 Anti-Cheat Software as a Security Threat

Issue #335 reveals that **anti-cheat software (e.g., BattlEye) explicitly recommends disabling hardware stack protection**, which:
- Creates a downgrade attack vector for malware
- Forces users to choose between entertainment and security
- Has no transparency — vendors won't explain what their software does because "it would defeat the purpose of Anti Cheat"

**Podcast angle:** This is **surveillance infrastructure masquerading as consumer software**. Anti-cheat systems run at the kernel level, can access all processes on a machine, and often have minimal oversight. The line between "anti-cheat" and "surveillance" is dangerously thin.

### 3.3 The Mobile Phone Exclusion

The maintainer is explicit: **the guide doesn't cover mobile phones because cellular devices are not recommended for privacy**. The rationale:
- No expectation of privacy without severely limiting usability
- The maintainer doesn't use a cell phone and "doesn't know any reason you would want to use one"
- There are already separate guides for mobile OS privacy

**Podcast angle:** This is a **philosophy vs. reality** conflict. For:
- **Activists in authoritarian states:** A smartphone is a lifeline — you can't organize without one
- **Journalists:** Sources contact you via Signal/WhatsApp — you can't ignore mobile
- **Economically marginalized people:** A smartphone may be the only computing device they can afford

The guide's assumption of a computer-only user reflects a **class and geography bias**. Privacy advice that requires $2,000 in hardware and advanced technical knowledge is **privileged privacy**.

### 3.4 The "Known to Work" Conservatism

The maintainer's insistence on only recommending tools with "well-understood security properties" reflects a **risk-averse philosophy**:
- Tor is recommended because "no network overlay has yet to be able to compete with Tor for high threat models"
- VPNs are recommended because "their limitations are well-understood due to the review they've received over the course of multiple decades"
- Mixnets are excluded because they are "new and unproven"

**Podcast angle:** This is the **innovation vs. caution tension** in privacy tech. The unemployment of new tools (I2P, mixnets, dVPNs) isn't just about theoretical risk — it's about **who gets left behind** when the "proven" tools are itself compromised (as the FBI's Tor exploit showed). **Conservative privacy advice can become obsolete advice.**

---

## 4. Community Dynamics & Governance

### 4.1 Anonymity of the Maintainers

The original author(s) remain unidentified. The primary maintainer (`nopeitsnothing`) is a community member who stepped in to maintain the project. This creates interesting questions:
- **Accountability:** How do you ensure a guide that could mean the difference between freedom and imprisonment is accurate, when the authors are anonymous?
- **Sustainability:** What happens if the maintainer burns out? The project has 7 open issues and a small community.
- **Trust:** The guide's CC-BY-SA-4.0 license and Open Collective donations provide some accountability, but the core content is written by ghosts.

### 4.2 The "Too Heated" Lock (Issue #31)

Issue #31 was **locked as "too heated"** — a rare GitHub action. The discussion about document accessibility turned into a **flame war** with personal criticisms, misunderstanding of contribution processes, and mutual frustration. This reveals:
- **Power asymmetry:** The maintainers hold enormous influence over what gets included in the guide, but contributors can't easily effect change
- **Cultural clash:** The maintainer's technical-writing, incremental-update approach clashes with external contributors' desire for fundamental restructuring
- **Emotional stakes:** For people who may face imprisonment for their anonymity, the guide isn't academic — it's survival

---

## 5. Recommended Podcast Angles & Story Ideas

### Angle A: "The Privacy Privilege Paradox"
The guide's recommendations require expensive hardware, advanced technical knowledge, and a lifestyle that doesn't include gaming or mobile phones. Who gets to be "private" in the digital age? Explore how privacy tools reproduce existing inequalities.

### Angle B: "When the FBI Hacks Tor"
The documented case of the FBI's drive-by exploit against Tor users. What does it mean when the world's most famous privacy tool is compromised by law enforcement? And why doesn't this make headlines?

### Angle C: "The Bitcoin vs. Monero Culture War"
The community's bitter debate over whether to recommend "impure" Bitcoin mixing or "pure" Monero. This mirrors larger cultural fights in the crypto world about what privacy *means* — and whether ideological purity is a luxury you can afford when your life depends on it.

### Angle D: "Anti-Cheat Software Is Surveillance Software"
The发现 that BattlEye and other anti-cheat systems recommend disabling hardware security features. Where's the line between game protection and system surveillance? And why do gamers silently comply?

### Angle E: "The Accessibility Gap in Digital Rights"
A disabled community member called for better PDF formatting and was met with maintainer resistance. What does it mean when the civil liberties movement lets accessibility slide? And who is the "digital rights" movement actually for?

### Angle F: "Anonymous Authors, Life-or-Death Stakes"
The guide's original authors are anonymous. The maintainer is a community member. The guide has been cited in court cases, academic papers, and real-world asylum claims. How do you build accountability when anonymity is the point?

### Angle G: "The Mobile Phone Dilemma"
The guide says: don't use smartphones. But for billions of people, a smartphone is their only internet access. For activists, it's a lifeline. The guide's computer-first worldview is a form of **digital colonialism** — imposing Western technologist assumptions on a global audience.

---

## 6. Key Resources & References

| Resource | Link | Relevance |
|---|---|---|
| THGTOA Guide | https://anonymousplanet.net/ | Full guide content |
| GitHub Repository | https://github.com/Anon-Planet/thgtoa | Source code & issues |
| Open Collective | https://opencollective.com/thgtoa | Donation/financial transparency |
| HEADS Firmware | https://osresearch.net/ | Physical tamper protection (Issue #313) |
| BattlEye FAQ | https://www.battleye.com/support/faq/ | Stack protection conflict (Issue #335) |
| Microsoft Stack Protection Blog | https://techcommunity.microsoft.com/t5/windows-os-platform-blog/understanding-hardware-enforced-stack-protection/ba-p/1247815 | Technical background on stack protection |
| Code of Conduct | https://anonymousplanet.org/export/CODE_OF_CONDUCT.html | Community governance |
| CC-BY-SA-4.0 License | https://creativecommons.org/licenses/by-sa/4.0/ | Copyleft content licensing |

---

## 7. Open Issues for Follow-Up

| # | Title | Status | Podcast Relevance |
|---|---|---|---|
| #159 | VPN SECTION | Open | Why is a VPN section controversial? |
| #354 | Blink Comparison | Open | New privacy browser — worth comparing? |
| #352 | Consideration for Brave Search | Open | Privacy browser ecosystem dynamics |
| #343 | Whonix route update for 17.x | Open (sticky) | Tor/VPN configuration best practices |
| #335 | Core isolation & stack protection | Open (5 comments) | Gaming vs. security tension |
| #313 | Tamper protection: add HEADS | Open (2 comments) | Physical security gaps in the guide |

---

*Notes compiled for podcast research. Forked from Anon-Planet/thgtoa on 2026-09-18.*
