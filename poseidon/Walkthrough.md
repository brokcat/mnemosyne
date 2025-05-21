## Challenge Context:

You are given a single file named `hash.txt`, containing the following MD5 hash:

```
242f77b4e65671a55e103b8b26df46a7
```

Your task is to investigate the origin, nature, and infrastructure of the malware associated with this hash. You must use publicly available sources (OSINT) and threat intelligence techniques.

---

## General Instructions

- Use the hash as the starting point.
    
- Combine multiple sources (VirusTotal, CYFIRMA, Malpedia, MITRE ATT&CK, etc.).
    
- Think like a threat analyst: pivot on IOC, find connections, and validate.
    

---

## Question 1: What is the name of the malware family associated with the given hash?

Step-by-step:

1. Start with VirusTotal:
    
    - Go to https://www.virustotal.com
        
    - Paste the hash `242f77b4e65671a55e103b8b26df46a7` in the search bar.
        
    - View the scan report.
        
2. Look under "File names" or "Detection" tab:
    
    - Several antivirus engines label the file as "Poseidon."
        
3. Cross-reference:
    
    - Search on Google: `poseidon malware site:cyfirma.com`
        
    - First result: CYFIRMA article: OSINT Investigation – Hunting Malicious Infrastructure Linked to Transparent Tribe.
        
    - Source: https://www.cyfirma.com/research/osint-investigation-hunting-malicious-infrastructure-linked-to-transparent-tribe/
        
4. Validation:
    
    - The article directly links the hash to the Linux malware Poseidon.
        

Answer: Poseidon

---

## Question 2: What APT group is behind this malware?

Step-by-step:

1. From VirusTotal, note any vendor tagging it as related to an APT.
    
2. Google search: `poseidon malware apt group`
    
3. CYFIRMA confirms:
    
    - "Poseidon, a malware attributed to Transparent Tribe, a Pakistan-linked APT."
        
    - Source: https://www.cyfirma.com/research/osint-investigation-hunting-malicious-infrastructure-linked-to-transparent-tribe/
        
4. Cross-check on Malpedia:
    
    - https://malpedia.caad.fkie.fraunhofer.de/actor/transparent_tribe
        

Answer: Transparent Tribe

---

## Question 3: Provide the IP addresses used by the malware for C2 communication.

Step-by-step:

1. Visit VirusTotal and search the hash.
    
2. Go to the "Relations" tab, then "Contacted IP addresses."
    
3. You’ll find:
    
    - 206.189.134.185
        
    - 143.198.64.151
        
4. CYFIRMA lists these as part of the command-and-control infrastructure:
    
    - Source: https://www.cyfirma.com/research/osint-investigation-hunting-malicious-infrastructure-linked-to-transparent-tribe/
        
5. Optionally validate with AbuseIPDB or Shodan.
    

Answer: 206.189.134.185 and 143.198.64.151

---

## Question 4: What hosting provider is used by the attackers for C2 infrastructure?

Step-by-step:

1. Use an IP WHOIS lookup tool like ipinfo.io or domaintools.com.
    
2. Query 206.189.134.185 and 143.198.64.151.
    
3. Both belong to DigitalOcean.
    
4. CYFIRMA also confirms this:
    
    - "The attacker leveraged VPS hosted by DigitalOcean."
        
    - Source: https://www.cyfirma.com/research/osint-investigation-hunting-malicious-infrastructure-linked-to-transparent-tribe/
        

Answer: DigitalOcean

---

## Question 5: List three MITRE ATT&CK techniques used by the malware.

Step-by-step:

1. Read the CYFIRMA technical blog:
    
    - Describes obfuscation: T1027
        
    - Hidden directories like .system: T1564.001
        
    - File/log deletion: T1070.004
        
2. Use MITRE ATT&CK framework:
    
    - https://attack.mitre.org/groups/G0134/
        
    - Map behaviors to techniques
        

Answer: T1027, T1564.001, T1070.004

---

## Question 6: What is the target country of this campaign?

Step-by-step:

1. CYFIRMA outlines targets in its "Target Profile" section.
    
    - Primary target: Indian government and defense.
        
2. Confirm with Malpedia and MITRE profiles for Transparent Tribe (G0134).
    
3. Additional confirmation by searching: `Transparent Tribe targets India`.
    

Answer: India

---

## Question 7: Which Pakistani intelligence agency is Transparent Tribe (APT36) suspected to be affiliated with?

Step-by-step:

1. Search on Google: `Transparent Tribe ISI affiliation`
    
2. Use the GINC report: https://www.ginc.org/apt36/
    
    - States the group is suspected to be backed by Pakistan’s ISI.
        
3. Validate with threat context and long-standing strategic targeting pattern against India.
    

Answer: Inter-Services Intelligence (ISI)

---

## Question 8: What operating system does Poseidon target?

Step-by-step:

1. VirusTotal clearly identifies the file as ELF 64-bit → Linux binary.
    
2. CYFIRMA confirms: Poseidon is a Linux backdoor.
    
3. Additional sources such as Google: `Poseidon Linux malware Transparent Tribe`
    

Answer: Linux

---

## Question 9: In which year did Transparent Tribe launch the Poseidon campaign?

Step-by-step:

1. CYFIRMA specifies in its introduction: "Poseidon used during a campaign in 2023."
    
    - Source: https://www.cyfirma.com/research/osint-investigation-hunting-malicious-infrastructure-linked-to-transparent-tribe/
        
2. VirusTotal shows first uploads around February 2023.
    
3. Search GitHub, blogs, etc. for corroborating posts on Poseidon in 2023.
    

Answer: 2023

---

## Final Notes

- All answers can be found using OSINT and publicly available tools.
    
- CYFIRMA is the most detailed and central source for this challenge.
    
- No access to private CTI tools is required.
    
- This walkthrough is designed to be beginner-friendly while ensuring analytical depth.
