# SECTION 11 — OPERATING SYSTEMS (15 Questions)

### Q1. What is a PROCESS?

A. A hardware thread of the CPU

B. A section of code stored in a library

C. A program in execution, with its own address space, heap/stack, and resources

D. A scheduling queue

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Process

**Explanation:**
A process is an executing program instance holding its own memory image (code, data, heap, stack) and resources. Hardware threads, libraries, and queues are different entities.

**Why the other options are wrong:**
- A: That's a hardware thread/core.
- B: Code on disk is not executing.
- D: The scheduler's structure, not the process itself.

**Key Concept:** Process = running program with private resources.

---

### Q2. What do THREADS within the same process SHARE?

A. Each thread has a totally isolated address space

B. The address space (memory, globals/static data, open files) of the parent process is shared

C. Threads share only CPU registers

D. Threads share nothing

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Threads

**Explanation:**
Threads of one process share code, data, heap, and open file descriptors — they differ in their own stack and program counter. That sharing makes context switches lightweight but raises concurrency risks.

**Why the other options are wrong:**
- A/C/D: All contradict how threads share process resources.

**Key Concept:** Threads share memory; each keeps its own stack.

---

### Q3. Which FOUR conditions must hold simultaneously for a DEADLOCK to occur?

A. Preemption, priority, segmentation, caching

B. Mutual exclusion, hold-and-wait, no preemption, circular wait

C. Hold, wait, starvation, throughput

D. Exclusive access, aging, paging, locking

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Deadlock Conditions

**Explanation:**
All four — mutual exclusion, hold-and-wait, no preemption, and circular wait — must exist at once. Removing any one prevents deadlock. The other lists mix unrelated OS concepts.

**Why the other options are wrong:**
- A/C/D: Include non-deadlock concepts (priorities, aging, paging).

**Key Concept:** The four conditions: ME, hold-and-wait, no-preemption, circular wait.

---

### Q4. First-Come-First-Served (FCFS) scheduling is:

A. Always preemptive

B. Round-robin in disguise

C. Priority-based

D. Non-preemptive — once running, a process keeps the CPU until it blocks or finishes

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** CPU Scheduling — FCFS

**Explanation:**
FCFS serves in arrival order without interrupting the running process. RR preempts after a quantum; priority scheduling uses priorities. FCFS is simple but can cause conv/rear starvation called the convoy effect.

**Why the other options are wrong:**
- A: FCFS does not preempt mid-execution.
- B: RR is preemptive with time quantum.
- C: No priority logic.

**Key Concept:** FCFS = non-preemptive, arrival order.

---

### Q5. Why is creating THREADS cheaper than creating PROCESSES?

A. Threads use a different programming language

B. Processes are scheduled first

C. Threads share the parent's address space — no new memory/address-space setup or IPC bookkeeping is required

D. Threads require no CPU at all

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Process vs Thread

**Explanation:**
Spawning a thread reuses the process's address space, whereas a process needs its own memory layout and context. That makes thread creation and context-switching cheaper — at the cost of shared-memory hazards.

**Why the other options are wrong:**
- A: Language is irrelevant.
- B: Scheduling order is unrelated.
- D: Threads absolutely consume CPU.

**Key Concept:** Threads reuse the process image → cheaper to create/switch.

---

### Q6. Which scheduling algorithm MINIMISES average waiting time for a batch of independent processes?

A. SJF (Shortest-Job-First) — running the shortest remaining job first reduces average wait

B. FCFS

C. LIFO

D. Random

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** SJF

**Explanation:**
SJF completes short jobs early, dragging down the average waiting time. Its catch: it needs burst-time estimates and can cause starvation of long jobs.

**Why the other options are wrong:**
- B: Blind arrival order elongates waits.
- C/D: No optimality guarantees.

**Key Concept:** SJF = best average waiting; starving long jobs.

---

### Q7. In Round Robin, making the TIME QUANTUM too small causes:

A. Better dispatch accuracy only

B. Excessive context-switch overhead — the CPU spends more time switching than computing

C. Starvation guaranteed

D. Memory thrash

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Round Robin

**Explanation:**
Each preemption costs a context switch. A tiny quantum forces switches far more often than useful work, killing throughput. A very large quantum would degrade RR toward FCFS.

**Why the other options are wrong:**
- A: The overhead dominates.
- C: RR's fairness prevents starvation.
- D: That's memory, unrelated.

**Key Concept:** Quantum ↔ context-switch overhead trade-off.

---

### Q8. A process waits forever but no circular wait exists. This is best described as:

A. Deadlock

B. Livelock

C. Thrashing

D. STARVATION — resource shortage repeatedly passes the process over without circular waiting

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Deadlock vs Starvation

**Explanation:**
Starvation is indefinite postponement (e.g., SJF never scheduling a long job); deadlock is a blocked circular wait where nobody can proceed. They have different causes and fixes (aging cures starvation).

**Why the other options are wrong:**
- A: Deadlock requires circular wait.
- B: Livelock is active repeating attempts.
- C: Thrashing is memory pressure.

**Key Concept:** Starvation ≠ deadlock; aging mitigates starvation.

---

### Q9. In PAGING, the PAGE TABLE maps:

A. Logical/virtual page numbers to the physical frames where the pages reside

B. IP addresses to MAC addresses

C. File names to blocks

D. Users to sessions

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Paging

**Explanation:**
Every process has a page table translating virtual pages into physical frames. Unmapped entries trigger a page fault. The other pairs describe ARP, filesystems, and sessions.

**Why the other options are wrong:**
- B: That's ARP's job (networks).
- C: Filesystem indexing.
- D: Authentication sessions.

**Key Concept:** Page table = virtual page → physical frame.

---

### Q10. Which situation is VIRTUAL MEMORY designed to handle?

A. The disk is full

B. More threads than cores

C. Programs whose working set does not fit entirely in physical RAM — demand paging loads pages on demand

D. Network latency

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Virtual Memory

**Explanation:**
Virtual memory lets programs reference and execute spaces, loading needed pages into RAM on demand. Programs can run larger than RAM (as long as the working set fits), and processes are isolated per page table.

**Why the other options are wrong:**
- A/B/D: Disk space, thread oversubscription, and latency aren't virtual-memory problems.

**Key Concept:** Virtual memory = illusion of bigger memory via demand paging.

---

### Q11. Two threads increment the same shared counter and the final value is wrong. What primitive prevents this?

A. A larger time quantum

B. Mutual-exclusion (e.g., a mutex/lock around the critical section)

C. More page frames

D. FCFS scheduling

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Synchronization

**Explanation:**
The read-modify-write on the shared counter is a race condition. Serialising the critical section with a mutex guarantees only one thread mutates it at a time — the standard fix.

**Why the other options are wrong:**
- A/C/D: None provide atomicity.

**Key Concept:** Race conditions → mutual exclusion.

---

### Q12. A process references a page that is NOT in RAM. What happens?

A. The process is killed immediately

B. The reference is silently skipped

C. Nothing — pages never miss

D. A page fault: the OS loads the page from disk (swap/backing store) and resumes the process

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Page Fault

**Explanation:**
On a fault, the kernel traps, brings the page in from the backing store (possibly evicting a victim page), updates the page table, and restarts the instruction. Not a kill or a skip.

**Why the other options are wrong:**
- A/B/C: All contradict fault-handling semantics.

**Key Concept:** Page fault = OS-driven demand-paging load.

---

### Q13. To PREVENT deadlock, a system redesigns so that a process requests all needed resources AT ONCE (no hold-and-wait). Which condition did they break?

A. Hold-and-wait — processes no longer hold resources while waiting for more

B. Mutual exclusion

C. No preemption

D. Circular wait

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Deadlock Prevention

**Explanation:**
Guaranteed 'request all upfront' eliminates the state where a process holds resources it keeps while blocking for more. Breaking any of the four conditions prevents deadlock; this one targets hold-and-wait.

**Why the other options are wrong:**
- B: Exclusivity is unchanged.
- C: No resource is forcibly taken.
- D: Cycles can still be avoided only indirectly here.

**Key Concept:** Four conditions; break one to prevent deadlock.

---

### Q14. What is the difference between a BINARY semaphore and a MUTEX?

A. A mutex can count; a semaphore is binary

B. Both are interchangeable with no distinction

C. A semaphore counts resources (a counting semaphore can be >1); a mutex is strictly a binary ownership lock (usually must be released by the owner)

D. Semaphores are for files, mutexes for CPU

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Mutex vs Semaphore

**Explanation:**
Semaphores track an availability count (0..N) and are signalled by any thread; mutexes are binary, owner-based locks. A binary semaphore (0/1) resembles a mutex but lacks strict ownership semantics.

**Why the other options are wrong:**
- A: Reverses their roles.
- B: Important behavioural differences exist.
- D: Wrong domain split.

**Key Concept:** Counting semaphore vs owner-holding binary mutex.

---

### Q15. The system spends most of its time swapping pages (page-fault rate is extreme). What is this condition?

A. Deadlock

B. Priority inversion

C. THRASHING — the working set exceeds RAM; performance collapses into disk I/O

D. Segmentation

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Thrashing

**Explanation:**
When processes collectively require more pages than RAM, every reference faults and pages by repeatedly evicted — CPU utilisation collapses. Fixes: reduce degree of multiprogramming, give more memory, or better locality.

**Why the other options are wrong:**
- A: Lock-based blocking, not memory.
- B: Scheduling anomaly.
- D: A memory-organization scheme unrelated to the symptom.

**Key Concept:** Thrashing = too much memory pressure, constant swapping.

---

# SECTION 12 — COMPUTER NETWORKS (15 Questions)

### Q1. How many LAYERS does the OSI reference model have?

A. 5

B. 7

C. 4

D. 6

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** OSI Model

**Explanation:**
The OSI model has seven layers: Physical, Data Link, Network, Transport, Session, Presentation, Application. The TCP/IP model collapses these into 4.

**Why the other options are wrong:**
- A: That's Johannes... no standard 5-layer.
- C: TCP/IP's four.
- D: Not a standard count.

**Key Concept:** OSI = 7; TCP/IP = 4.

---

### Q2. What is the default port for HTTP (non-secure)?

A. 21

B. 22

C. 443

D. 80

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** HTTP

**Explanation:**
HTTP default = 80; HTTPS = 443; FTP control = 21; SSH = 22. These are the classic default ports.

**Why the other options are wrong:**
- A: FTP.
- B: SSH.
- C: HTTPS.

**Key Concept:** Remember 80 (HTTP), 443 (HTTPS), 22 (SSH), 21 (FTP).

---

### Q3. What does DNS enable?

A. Compression of audio streams

B. Encryption of web traffic

C. Translating human-friendly domain names into IP addresses

D. Assigning IP addresses to devices on a LAN

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** DNS

**Explanation:**
DNS is the internet's phone book: it resolves names like www.example.com to IP addresses. IP assignment on LANs is DHCP's job; TLS is encryption.

**Why the other options are wrong:**
- A: Codecs/encoders.
- B: TLS/HTTPS.
- D: DHCP.

**Key Concept:** DNS = domain → IP resolution.

---

### Q4. Which transport protocol is CONNECTIONLESS?

A. UDP — datagrams with no handshake, no delivery guarantee

B. TCP

C. SCTP with handshakes

D. TLS

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** UDP

**Explanation:**
UDP sends standalone datagrams with no connection setup and no guarantees — low overhead, good for real-time media. TCP is connection-oriented with reliability.

**Why the other options are wrong:**
- B: Connection-oriented, reliable.
- C: Connection-oriented.
- D: Runs on top of TCP usually; not a transport alternative here.

**Key Concept:** UDP = send and pray (fast); TCP = connect and ensure.

---

### Q5. How does TCP guarantee reliable, in-order delivery?

A. By retransmitting every packet twice

B. Sequence numbers + acknowledgements (ACKs) + retransmission of lost/ damaged segments

C. By keeping the network lazy

D. By using UDP headers

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** TCP Reliability

**Explanation:**
Each byte is numbered; the receiver ACKs, the sender retransmits what wasn't ACKed. Checksums catch damage. This machinery is what TCP adds over UDP.

**Why the other options are wrong:**
- A: No blanket duplication.
- C: Not a protocol property.
- D: TCP has its own header.

**Key Concept:** SEQ/ACK + retransmission = TCP's reliability.

---

### Q6. What makes HTTPS more secure than HTTP?

A. TLS/SSL encryption of the HTTP traffic via a certificate-based handshake

B. A faster TCP window

C. A new port number only

D. DNS filtering

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** HTTPS

**Explanation:**
HTTPS = HTTP over TLS, encrypting payloads, authenticating the server via certificates, and providing integrity. The port change (443) is a consequence, not the security.

**Why the other options are wrong:**
- B: Performance, not security.
- C: Port alone encrypts nothing.
- D: Unrelated.

**Key Concept:** HTTPS = HTTP + TLS.

---

### Q7. How many bits are in an IPv4 vs an IPv6 address?

A. 32 and 64

B. 128 and 32

C. 32 and 128

D. 64 and 128

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** IP Addressing

**Explanation:**
IPv4 = 32 bits (four octets); IPv6 = 128 bits (hexadecimal groups), solving address exhaustion.

**Why the other options are wrong:**
- A/B/D: Wrong pairings/sizes.

**Key Concept:** IPv4 32-bit, IPv6 128-bit.

---

### Q8. ROUTERS operate primarily at which OSI layer?

A. Physical

B. Data link

C. Transport

D. Network — routing/forwarding packets across networks by IP address

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** OSI Layer Responsibilities

**Explanation:**
Routers make network-layer decisions using IP addresses (Layer 3). Switches/bridges are data-link (L2); hubs/repeaters are physical (L1).

**Why the other options are wrong:**
- A: That's hubs/repeaters.
- B: That's switches/bridges (MAC-based).
- C: TCP/UDP live at transport.

**Key Concept:** Layer 3 = network = routers/IP.

---

### Q9. HTTP, SMTP, and FTP all belong to which OSI layer?

A. Transport

B. Application

C. Session

D. Presentation

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Application Layer

**Explanation:**
These end-user protocols live at the Application layer (L7). TCP/UDP are transport; session/presentation layers exist in OSI but host these protocols' services.

**Why the other options are wrong:**
- A: TCP/UDP there.
- C/D: Not where the protocols sit.

**Key Concept:** HTTP/SMTP/FTP = Application.

---

### Q10. Which sequence describes the TCP 3-WAY HANDSHAKE?

A. ACK, SYN, SYN-ACK

B. SYN-ACK, SYN, ACK

C. SYN → SYN-ACK → ACK

D. SYN → ACK → FIN

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** TCP Handshake

**Explanation:**
Client sends SYN; server replies SYN-ACK; client ACKs. Both sides now have a synchronised connection. FIN appears in teardown, not setup.

**Why the other options are wrong:**
- A/B: Wrong ordering sets.
- D: Includes the teardown FIN.

**Key Concept:** Establish with SYN → SYN-ACK → ACK.

---

### Q11. A live video-streaming app sends frames; an occasional dropped frame is acceptable, but delay must be minimal. Which protocol and why?

A. UDP — low latency, no retransmission delays for old frames

B. TCP — guaranteed delivery of every frame, even stale ones

C. HTTP only

D. DNS

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** TCP vs UDP Choice

**Explanation:**
Real-time media prefers UDP: no retransmission delays, and a missing frame is skipped. TCP's reliability would stall playback waiting for old packets.

**Why the other options are wrong:**
- B: Delays hurt live streams.
- C/D: Not transport-layer choices for this.

**Key Concept:** Live media → UDP; files/accuracy → TCP.

---

### Q12. On a local network, which protocol translates a device's IP address into its MAC address so a frame can be delivered?

A. DHCP

B. HTTP

C. RIP

D. ARP

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** ARP

**Explanation:**
ARP resolves the next-hop IP to an L2 MAC within the same subnet so frames can be addressed. DHCP assigns IPs; HTTP serves web; RIP routes.

**Why the other options are wrong:**
- A: Assigns addresses, doesn't resolve MACs.
- B/C: Higher-layer/non-local protocols.

**Key Concept:** ARP = IP → MAC on the local segment.

---

### Q13. A user can PING an external IP but cannot reach the company website by NAME. What is the most likely failure?

A. Physical link

B. DNS resolution of the domain name

C. The ping protocol being blocked only

D. The switch is off

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** Networking Troubleshooting Scenario

**Explanation:**
Ping to an IP proves connectivity works; failing by name points at name resolution — DNS can't map the hostname. Routing, switch, and link are shown healthy by the successful ping.

**Why the other options are wrong:**
- A: Link is working (ping succeeded).
- C: Ping succeeded, additional symptom unexplained.
- D: Would break ping too.

**Key Concept:** IP reachable + name fails = DNS problem.

---

### Q14. Which DNS RECORD TYPE maps a hostname to an IPv4 address?

A. A record

B. MX

C. CNAME

D. TXT

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** DNS Record Types

**Explanation:**
The A record holds an IPv4 address (AAAA holds IPv6). MX = mail servers, CNAME = alias, TXT = arbitrary text/verification.

**Why the other options are wrong:**
- B: Mail routing.
- C: Hostname aliasing.
- D: Metadata.

**Key Concept:** A = IPv4; AAAA = IPv6; MX = mail.

---

### Q15. A user types "https://www.example.com". What network event happens FIRST?

A. The TCP handshake

B. The TLS handshake

C. DNS resolution of www.example.com to an IP

D. The HTTP GET request

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Request Lifecycle Sequence

**Explanation:**
Before the browser can handshake or send HTTP, it must resolve the hostname to an IP via DNS. Only then do TCP, TLS, and HTTP proceed.

**Why the other options are wrong:**
- A/B/D: All require the destination IP that DNS provides first.

**Key Concept:** DNS → TCP → TLS → HTTP.

---

# SECTION 13 — GIT & SOFTWARE ENGINEERING (10 Questions)

### Q1. What does `git commit` create?

A. A nightly server backup

B. A permanent, versioned snapshot of the (staged) changes in the repository's history

C. A copy of the repository on a remote server

D. A diff against the current branch only

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Commit

**Explanation:**
A commit records staged changes as an immutable point in history with a hash, author, message, and parent pointer. It isn't a backup tool or a remote push, and it stores the snapshot, not just a diff.

**Why the other options are wrong:**
- A: Git is not a filesystem backup.
- C: That's git push/clone.
- D: Commits capture state plus metadata.

**Key Concept:** Commit = hash-identified snapshot in history.

---

### Q2. What does `git clone` do?

A. Copies a remote repository into a new local directory including its full history

B. Starts a new empty repository

C. Merges two branches

D. Reverts the last commit

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Clone

**Explanation:**
Clone performs a full copy of a remote repo — all commits, branches, and working files — into a local directory. `git init`, merge, and revert are separate commands.

**Why the other options are wrong:**
- B: That's git init.
- C: That's git merge.
- D: That's revert/reset.

**Key Concept:** clone = copy remote repo with history.

---

### Q3. What is a git BRANCH?

A. A copy of the entire repository for every developer

B. A single commit

C. A movable pointer to a commit/tip of an independent line of development

D. The staging area

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Branch

**Explanation:**
A branch is just a pointer to a commit; committing on it moves the pointer forward, letting work proceed in parallel. It is not a storage copy and not the index/staging area.

**Why the other options are wrong:**
- A: Branches are cheap pointers, not copies.
- B: Branches point at series of commits.
- D: The staging area is `git add`'s target.

**Key Concept:** Branch = lightweight pointer to a development line's tip.

---

### Q4. When does git report a MERGE CONFLICT?

A. When the remote is unreachable

B. When the same file path exists in both branches with identical content

C. Whenever you run git merge

D. When the two branches changed the SAME lines of the SAME file differently

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Merge Conflicts

**Explanation:**
Git auto-merges independent changes; it stops only when the same hunks were edited differently on both sides — a true ambiguity. Different files or non-overlapping edits merge cleanly.

**Why the other options are wrong:**
- A: Network issues are unrelated.
- B: Identical content merges cleanly.
- C: Most merges are automatic.

**Key Concept:** Conflicts need overlapping same-line edits.

---

### Q5. `git pull` is equivalent to which combination?

A. git fetch + git merge of the tracking branch

B. git clone + git add

C. git push + git commit

D. git status + git diff

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Pull vs Fetch

**Explanation:**
`git pull` fetches remote changes and then integrates them (merge/rebase) into the current branch. `fetch` alone only downloads objects. Push/commit/status are unrelated to pulling.

**Why the other options are wrong:**
- B/C/D: Wrong command pairings.

**Key Concept:** pull = fetch + integrate.

---

### Q6. What does `git status` show?

A. The remote server's health

B. Historical commit messages only

C. The current state of the working tree: staged, unstaged, and untracked files

D. The credentials saved for pushing

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Status / Working Tree

**Explanation:**
`git status` reports what's modified, staged, or untracked — the difference between working tree, index, and HEAD. It doesn't inspect remotes, log-only history, or credentials.

**Why the other options are wrong:**
- A/B/D: Outside git status's scope.

**Key Concept:** Look at `git status` to see pending changes.

---

### Q7. Which order best describes the classic SOFTWARE DEVELOPMENT LIFECYCLE (SDLC)?

A. Deploy → Code → Test → Design

B. Requirements → Design → Development → Testing → Deployment → Maintenance

C. Testing → Requirements → Deployment → Design

D. Maintenance → Deployment → Design → Code

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** SDLC

**Explanation:**
The classic waterfall-style phases run requirements, design, implementation, testing, deployment, then maintenance. Practical models (agile) iterate these phases rather than dropping them.

**Why the other options are wrong:**
- A/C/D: Reorder or omit essential phases.

**Key Concept:** Requirements → Design → Build → Test → Deploy → Maintain.

---

### Q8. Which statement about `git rebase` is FALSE?

A. It reapplies your branch's commits on top of another base commit

B. It creates a cleaner, linear history than merge

C. It can rewrite commit hashes of your existing commits

D. It is always safe to rebase shared public branches that others have based work on

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Merge vs Rebase

**Explanation:**
Rewriting hashes on shared branches breaks teammates' local history. Rebase is for local/feature branches only — 'never rebase published commits' is the golden rule. A/B/C are all accurate.

**Why the other options are wrong:**
- A: That's exactly what rebase does.
- B: History becomes linear.
- C: New bases → new hashes.

**Key Concept:** Rebasing rewrites history — never on shared branches.

---

### Q9. Teams develop v3 on main while a critical bug exists in the released v2. Which workflow best fixes v2 without disturbing main?

A. Fix directly on main and tag it v2

B. Delete v2 and re-release v3

C. Checkout a branch from the v2 tag, fix + test, then ship a hotfix and merge/cherry-pick the fix as appropriate

D. Rewrite all of v2's history

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Hotfix Workflow

**Explanation:**
Branches isolate work: start from the v2 tag, patch it, release, and optionally port the fix to main via merge/cherry-pick. Editing main or erasing v2 uncontrolled is wrong.

**Why the other options are wrong:**
- A: Mixes v3 line with the release.
- B: Destroys a known-good release.
- D: History rewriting is destructive.

**Key Concept:** Fix releases on a branch from the release tag.

---

### Q10. Why should you commit .env / credentials files and add them to .gitignore / refuse to commit them?

A. Secrets in the repository become visible to anyone with access and survive forever in history — never commit them

B. Secrets speed up the build

C. Committing secrets is required for CI to work

D. .gitignore cannot affect commits anyway

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Secure Git Usage

**Explanation:**
Committed secrets leak into history (clone/to other teams) and remain recoverable after simple deletion. Best practice: secrets managers + environment configuration, and `.gitignore` for local env files.

**Why the other options are wrong:**
- B/C: No functional benefit, huge risk.
- D: .gitignore specifically prevents tracking.

**Key Concept:** Never commit secrets; use secrets managers.