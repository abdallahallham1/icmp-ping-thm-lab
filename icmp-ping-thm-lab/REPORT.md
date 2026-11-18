# Lab Report: ICMP Echo and Ping

## 1. Objective

Use the Linux `ping` command in the TryHackMe learning environment to test ICMP reachability to the exercise target, then interpret the result and connect it to packet analysis in Wireshark.

## 2. Environment and scope

- Platform: TryHackMe
- Room: What is Networking?
- Section: Ping (ICMP)
- Target: `8.8.8.8`
- Scope: the task's provided, authorized lab environment

## 3. Procedure

The following command was entered in the lab terminal:

```bash
ping -c 4 8.8.8.8
```

The `-c 4` option limits the Linux ping process to four Echo Requests.

## 4. Observed results

The supplied terminal summary stated:

```text
4 packets transmitted, 4 received, 0% packet loss
rtt min/avg/max/mdev = 8.132/9.428/10.957/1.057 ms
```

The reply lines showed `ttl=56`. The task also returned a completion flag, which is saved in the local, Git-ignored file `private/flag.txt`.

## 5. Analysis

The summary indicates that four requests were transmitted and four replies were received, with 0% packet loss for this short test. The reported average RTT was 9.428 ms. This supports the conclusion that the destination responded to ICMP Echo Requests during the test window.

This result does not establish that a web server or any other application service is reachable. ICMP and application protocols are different; a host may reply to Ping while a particular TCP service is unavailable, or it may block ICMP while its services remain available.

In ICMPv4, Echo Request uses Type 8 / Code 0 and Echo Reply uses Type 0 / Code 0. The IPv4 Protocol field value for ICMP is 1. ICMP has no TCP/UDP port number.

## 6. Data-quality caveat

The copied output should be checked before treating every displayed field as verified evidence:

- Each of the four visible replies reports `icmp_seq=1` instead of a normally increasing sequence number.
- The visible per-reply times are 9.92, 8.97, 7.38, and 7.48 ms, which do not match the reported summary statistics of 8.132 / 9.428 / 10.957 / 1.057 ms.

A fresh run or screenshot of the original terminal should be used to resolve this discrepancy. No values have been silently altered in this report.

## 7. Wireshark follow-up

For the earlier capture, use the display filter `icmp`. Then compare:

- Echo Request: `icmp.type == 8`
- Echo Reply: `icmp.type == 0`

Inspect IPv4 addresses, local-link Ethernet MAC addresses, ICMP Type/Code, sequence information, timestamps, and TTL. Add the relevant screenshots to the `evidence/` directory after redacting personal or sensitive information.

## 8. Conclusion

The TryHackMe Ping task was completed and a flag was obtained. The command-line summary reports successful replies and 0% packet loss in the test. The next portfolio step is to attach the actual TryHackMe and Wireshark screenshots, verify the copied output discrepancy, and publish only the sanitized documentation.
