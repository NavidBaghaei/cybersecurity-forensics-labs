# Cybersecurity Forensics Labs

Hands-on digital forensics labs completed as part of **CSC 153 – Digital Forensics** at Sacramento State University (2024). Each lab covers a core forensic skill area using industry-standard tools.

---

## 🔬 Lab Index

| # | Title | Tools |
|---|-------|-------|
| 1 | [Digital Forensics Case Setup & Evidence Acquisition](#lab-1--digital-forensics-case-setup--evidence-acquisition) | Autopsy |
| 2 | [Digital Forensics Lab Business Case](#lab-2--digital-forensics-lab-business-case-written-assignment) | *(Written assignment)* |
| 3 | [Disk Imaging & Partition Management](#lab-3--disk-imaging--partition-management) | FTK Imager, VirtualBox, Linux (fdisk, mkfs) |
| 4 | [USB Drive Investigation with OSForensics](#lab-4--usb-drive-investigation-with-osforensics) | OSForensics |
| 5 | [Disk Structure Analysis & Registry Forensics](#lab-5--disk-structure-analysis--registry-forensics) | WinHex, OSForensics |
| 6 | [File Slack Space & Secure Data Wiping](#lab-6--file-slack-space--secure-data-wiping) | Hex Workshop, DBAN, VirtualBox, Windows Disk Management |
| 7 | [Linux File System Analysis & Autopsy Forensics](#lab-7--linux-file-system-analysis--autopsy-forensics) | Linux terminal (uname, ls, cat, grep, ip, touch, ln, mkdir, su, sudo), Autopsy (browser-based v2.24), Sleuth Kit |
| 8 | [File Signature Analysis, Header Manipulation & Steganography](#lab-8--file-signature-analysis-header-manipulation--steganography) | Autopsy, HxD, Steghide, Linux terminal |
| 9 | [Hash Set Analysis & Data Obfuscation](#lab-9--hash-set-analysis--data-obfuscation) | Autopsy, WinHex |
| 10 | [Memory Forensics & Network Traffic Analysis](#lab-10--memory-forensics--network-traffic-analysis) | winpmem, OSForensics (Memory Viewer), Volatility Workbench, Wireshark, VirusTotal |
| 11 | [Email Forensics with Autopsy & WinHex](#lab-11--email-forensics-with-autopsy--winhex) | Autopsy, WinHex, MXToolbox |
| 12 | [Mobile Device Forensics with Cellebrite Reader](#lab-12--mobile-device-forensics-with-cellebrite-reader) | Cellebrite Reader 7.68 |
| 13 | [Prefetch File Analysis & Application Execution History](#lab-13--prefetch-file-analysis--application-execution-history) | OSForensics (File System Browser), WinHex |
| 14 & 15 | [Disk Image Investigation: Unauthorized Apps & Email Evidence](#lab-14--15--disk-image-investigation-unauthorized-apps--email-evidence) | Autopsy, WinHex |

---

## Lab Summaries

---

### Lab 1 – Digital Forensics Case Setup & Evidence Acquisition
**Tools:** Autopsy

Created a forensic case in Autopsy, loaded a disk image (.E01 format), and ran ingest modules to analyze file contents. Recovered key evidence files including a document and spreadsheet from a simulated investigation scenario.

---

### Lab 2 – Digital Forensics Lab Business Case *(Written Assignment)*
**Tools:** None

Developed a business case proposal for establishing an in-house digital investigations unit for a law firm. Covered budget justification, hardware/software requirements, vendor selection, and implementation strategy.

---

### Lab 3 – Disk Imaging & Partition Management
**Tools:** FTK Imager, VirtualBox, Linux (fdisk, mkfs)

Created and partitioned a virtual hard disk in Linux using `fdisk`, formatted it as FAT32, and mounted/unmounted it from the filesystem. Created a forensic disk image using FTK Imager with MD5/SHA1 hash verification to confirm image integrity.

---

### Lab 4 – USB Drive Investigation with OSForensics
**Tools:** OSForensics

Created a forensic case in OSForensics and loaded a USB drive image (E01 format). Performed file name searches, indexed all file types across the drive, browsed the file system to examine recovered files including images, text files, and executables, and documented findings within the case management system.

---

### Lab 5 – Disk Structure Analysis & Registry Forensics
**Tools:** WinHex, OSForensics

Used WinHex to examine raw disk structure including the Master Boot Record, partition tables, and file signatures (magic bytes/hex headers) to identify file types. In a second task, loaded a disk image into OSForensics, used the Registry Viewer to examine a user's registry hive, identified and documented artifacts including email accounts, cloud storage, and browser history, then generated a formal forensic case report.

---

### Lab 6 – File Slack Space & Secure Data Wiping
**Tools:** Hex Workshop, DBAN (Darik's Boot and Nuke), VirtualBox, Windows Disk Management

Created and partitioned a virtual disk, then used Hex Workshop to explore file slack space — hiding data in the unused space after a file's end — and analyzed why hidden data in slack space is invisible to standard software. In a second task, used DBAN to perform a DoD-standard secure wipe of the disk and verified all sectors were zeroed out post-wipe.

---

### Lab 7 – Linux File System Analysis & Autopsy Forensics
**Tools:** Linux terminal (uname, ls, cat, grep, ip, touch, ln, mkdir, su, sudo), Autopsy (browser-based, v2.24), Sleuth Kit

Used Linux terminal commands to collect system information into a log file (`my.log`) including kernel version, directory listings, network interface data, user accounts, and shadow file contents (accessed as root). Demonstrated hard links and symbolic links to understand inode structure — confirmed that a hard link and its original file share the same inode number. In a second task, installed Sleuth Kit and Autopsy, loaded a forensic disk image (GCFI-LX) into the browser-based Autopsy tool (v2.24 via localhost), performed a keyword search for "martha" across allocated and unallocated space, and located 77 hits — predominantly email artifacts.

---

### Lab 8 – File Signature Analysis, Header Manipulation & Steganography
**Tools:** Autopsy, HxD, Steghide, Linux terminal

Loaded a disk image into Autopsy and used EXIF metadata analysis and keyword searches to identify files with mismatched extensions. Located a JPEG image disguised as an `.exe` file, then used HxD to manually repair the file's hex header bytes to restore it as a viewable image. In a second task, used Steghide on Linux to embed a secret text file inside a JPEG image and successfully extract it — demonstrating steganography techniques used in real-world data concealment.

---

### Lab 9 – Hash Set Analysis & Data Obfuscation
**Tools:** Autopsy, WinHex

Imported the NIST NSRL hash database into Autopsy and created a custom hash set of notable files of interest. Ran hash lookup ingest modules against a disk image to identify matching files, including a custom set of images flagged as notable. In a second task, used WinHex to compute an MD5 hash of a document for integrity verification. In a third task, demonstrated a basic data obfuscation technique by bit-shifting file contents to make them unreadable, then reversing the shift to recover the original data.

---

### Lab 10 – Memory Forensics & Network Traffic Analysis
**Tools:** winpmem, OSForensics (Memory Viewer), Volatility Workbench, Wireshark, VirusTotal

Captured a live memory dump using winpmem, analyzed running processes (including `lsass.exe`) via OSForensics Memory Viewer, dumped process memory to disk, and loaded the raw image into Volatility Workbench to enumerate processes from the snapshot. Then installed Wireshark with Npcap, opened a PCAP file, analyzed conversations and protocol hierarchy, and filtered to HTTP traffic to identify three downloaded files (a `.txt`, a `.doc`, and a `.exe` from `smart-fax.com`). Resolved network addresses, cross-referenced the domain on VirusTotal (flagged malicious by 7/90 vendors), exported HTTP objects, and confirmed the `.exe` was malware when Windows Defender automatically quarantined it on save.

---

### Lab 11 – Email Forensics with Autopsy & WinHex
**Tools:** Autopsy, WinHex, MXToolbox

Ingested a `.pst` file into Autopsy using the Email Parser module, recovering 26 email messages. Examined a suspicious email with a `.gpj` attachment, extracted and renamed it to `.jpg` to reveal a hidden image. Copied email headers from a specific message and analyzed them in MXToolbox to extract metadata including originating IP, mailer, and spam flags. In a second task, opened a `.tar` archive in WinHex, switched to text view, used Find Text to search for "terrysadler," selected and exported that block to a new `.txt` file, and read the full email in Notepad. Performed keyword searches for "Jim Shu" across the archive, surfacing multiple relevant emails including internal HR correspondence.

---

### Lab 12 – Mobile Device Forensics with Cellebrite Reader
**Tools:** Cellebrite Reader 7.68

Created a Cellebrite account, downloaded and activated Cellebrite Reader, and configured case settings. Opened a Nokia GSM logical extraction file and explored extracted content including 2 call log entries (both zero-duration), 7 contacts, 16 instant messages (mix of personal SMS and automated carrier messages), 18 audio files (preloaded ringtones), and 34 images (wallpapers, clip-arts, and user photos). Analyzed the device timeline to reconstruct usage patterns and generated a formal Cellebrite extraction report documenting device identifiers (IMEI, MSISDN), source extraction metadata, and all recovered artifacts.

---

### Lab 13 – Prefetch File Analysis & Application Execution History
**Tools:** OSForensics (File System Browser), WinHex

Extracted a disk image and created a criminal case in OSForensics with chain of custody metadata. Used the File System Browser to navigate to the Windows Prefetch folder and located `DROPBOX.EXE-AA3E8112.pf`. Opened the file in WinHex, enabled the Data Interpreter panel, and configured it to display Windows FILETIME (64-bit) timestamps. Parsed key offsets: offset `0x80` revealed the most recent runtime, offset `0x88` revealed the last modification date (08/06/2014), and offset `0xD0` revealed an execution counter of 11 — demonstrating how prefetch files can prove an application was run on a system even if it has since been deleted.

---

### Lab 14 & 15 – Disk Image Investigation: Unauthorized Apps & Email Evidence
**Tools:** Autopsy, WinHex

**Lab 14:** Extracted a disk image (`GCFI-tj01.001`) and created an Autopsy case. Navigated the file system to the user profile of "Tom Johnson," examined the Desktop, and tagged `Acrobat Reader DC.lnk` and two steganography applications found in Program Files (`Quick Stego` and `Stegantofile`) under a custom "Unauthorized Applications" tag. Generated an HTML forensic report documenting the tagged artifacts and summarizing the evidentiary significance of steganography tools.

**Lab 15:** Created a new Autopsy case using the same disk image, entering the known MD5 hash to validate evidence integrity and establish chain of custody. Ran only the Email Parser ingest module, which recovered 127 email messages. Tagged all messages from `gmx.us` addresses with a custom "GMX Email" tag and generated an Excel report. Written analysis identified two key findings: financial negotiation emails in which the suspect demanded payment for leaking data (escalating from $100 to $500), and a covert data exfiltration email describing how files were smuggled out by manipulating JPEG headers with a hex editor to evade email monitoring systems.

---

## Tools Reference

| Tool | Category | Labs Used |
|------|----------|-----------|
| Autopsy | Disk/File Forensics | 1, 7, 8, 9, 11, 14, 15 |
| OSForensics | Disk/Memory/Registry Forensics | 4, 5, 10, 13 |
| WinHex | Hex Editor / Forensic Analysis | 5, 9, 11, 13, 14 |
| FTK Imager | Disk Imaging | 3 |
| Wireshark | Network Traffic Analysis | 10 |
| Volatility Workbench | Memory Forensics | 10 |
| Cellebrite Reader | Mobile Device Forensics | 12 |
| Steghide | Steganography | 8 |
| HxD | Hex Editor | 8 |
| Hex Workshop | Hex Editor / Slack Space | 6 |
| DBAN | Secure Disk Wiping | 6 |
| Sleuth Kit | Linux Forensics | 7 |
| winpmem | Memory Acquisition | 10 |
| VirusTotal | Malware/IOC Analysis | 10 |
| MXToolbox | Email Header Analysis | 11 |
| VirtualBox | Virtualization | 3, 6 |

---

## Skills Demonstrated

- Forensic disk imaging and hash verification (MD5/SHA1)
- File system analysis (FAT32, ext3, NTFS)
- Registry forensics and artifact extraction
- Memory acquisition and process analysis
- Network traffic analysis and malware identification
- Email forensics (PST, EML, TAR archives)
- Mobile device data extraction and timeline reconstruction
- Steganography detection and file header manipulation
- Prefetch file parsing and execution history recovery
- Chain of custody documentation and forensic report generation
- Slack space analysis and secure data wiping

---

## Course Info

**Course:** CSC 153 – Digital Forensics  
**Institution:** California State University, Sacramento  
**Year:** 2024
