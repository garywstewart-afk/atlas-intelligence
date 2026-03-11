**ATLAS STRATEGIC CONSULTANTS**

**INTELLIGENCE KNOWLEDGE BASE**

**PILLAR 3 --- PENETRATION TESTING & OSINT**

March 2026 \| Caves Beach, NSW, Australia \| Version 1.1 \|
Classification: Internal Use Only

**1. Purpose and Scope**

This brief constitutes the Pillar 3 intelligence reference for
penetration testing methodology, AI-native offensive security tooling,
OSINT platforms, exploitation frameworks, and CVE/vulnerability
intelligence feeds. It is the primary reference document for all
security assessment, threat intelligence, and open-source investigation
work conducted under the Atlas Strategic Consultants research programme.

Two significant AI-native pentest frameworks shipped in the six weeks
prior to the v1.0 brief: Zen-AI-Pentest (February 11, 2026) and
BlacksmithAI (March 2, 2026). Both implement multi-agent architectures
modelling real penetration testing team structures. A third framework,
PentAGI, released February 24, 2026 with the deepest toolchain
integration to date. These releases represent a structural shift in the
offensive security landscape: full-lifecycle automated assessments are
now accessible via open-source frameworks, lowering the expertise bar
for adversaries and creating new demand for continuous security
validation.

Version 1.1 additions: Section 9 --- Web Document Retrieval and Search
Engine Dorking, covering the full cross-engine operator reference for
passive document discovery, updated to reflect the deprecation of the
cache: operator (2024) and the cross-engine operator matrix across
Google, Bing, Yandex, DuckDuckGo, and Brave as of February 2026. ATT&CK
version updated to v18.1. PentAGI date corrected to February 24, 2026.

This brief covers seven domains: Methodological Frameworks, AI-Native
Pentest Platforms (2025--2026), Reconnaissance and Recon OSINT Tools,
Exploitation Frameworks, OSINT Investigation Platforms,
CVE/Vulnerability Intelligence Feeds, Strategic Notes, and Web Document
Retrieval and Search Engine Dorking (v1.1 addition).

> Source notes: BlacksmithAI --- Help Net Security, March 2, 2026.
> Zen-AI-Pentest --- Help Net Security, February 11, 2026. PentAGI ---
> github.com/vxcontrol/pentagi, February 24, 2026. MITRE ATT&CK v18.1
> --- attack.mitre.org, October 2025. All tool URLs verified March 6,
> 2026. Max Intel Google Dorking Reference 2026 --- maxintel.org,
> February 9, 2026.

**2. Methodological Frameworks**

The following frameworks constitute the formal methodology layer for all
Atlas penetration testing engagements. No single framework is
comprehensive in isolation. Current best practice (2026) combines PTES
for engagement lifecycle, MITRE ATT&CK v18.1 for TTP mapping, and OWASP
WSTG for web surface coverage.

  -------------------------------------------------------------------------------------------------------------------------------------
  **Framework**   **Full Name**     **URL**                                                      **Atlas Application**     **Status**
  --------------- ----------------- ------------------------------------------------------------ ------------------------- ------------
  PTES            Penetration       https://pentest-standard.org                                 Practitioner-written      Active
                  Testing Execution                                                              end-to-end lifecycle:     
                  Standard                                                                       pre-engagement → recon →  
                                                                                                 threat modelling →        
                                                                                                 exploitation →            
                                                                                                 post-exploitation →       
                                                                                                 reporting. Reference      
                                                                                                 baseline for scoping all  
                                                                                                 Atlas assessments.        

  OWASP WSTG v4.2 Web Security      https://owasp.org/www-project-web-security-testing-guide     Definitive web            Active ---
                  Testing Guide                                                                  application test          v4.2 current
                                                                                                 checklist. 91 test cases  
                                                                                                 across authentication,    
                                                                                                 session management,       
                                                                                                 injection, business       
                                                                                                 logic. Reference for all  
                                                                                                 web surface assessments.  

  OSSTMM 3        Open Source       https://isecom.org/OSSTMM.3.pdf                              Scientific metrics-driven Active
                  Security Testing                                                               framework covering        
                  Methodology                                                                    physical, human,          
                  Manual                                                                         wireless, telecoms, data  
                                                                                                 networks. Produces        
                                                                                                 quantifiable attack       
                                                                                                 surface measurement (RAV  
                                                                                                 score).                   

  NIST SP 800-115 Technical Guide   https://csrc.nist.gov/publications/detail/sp/800-115/final   US federal standard for   Active
                  to Information                                                                 planning, executing and   
                  Security Testing                                                               analysing security tests. 
                                                                                                 Documentation-heavy; used 
                                                                                                 for compliance-grade      
                                                                                                 evidence. NIST CSF 2.0    
                                                                                                 (2024) is the companion   
                                                                                                 risk framework.           

  MITRE ATT&CK    Adversarial       https://attack.mitre.org                                     14 Enterprise tactics,    v18.1 ---
  v18.1           Tactics                                                                        200+ techniques, 400+     Oct 2025
                  Techniques &                                                                   sub-techniques. v18 (Oct  
                  Common Knowledge                                                               2025) replaced Detections 
                                                                                                 with Detection            
                                                                                                 Strategies. v18.1 is the  
                                                                                                 current release.          
                                                                                                 Cross-referenced with CVE 
                                                                                                 via Mappings Explorer.    

  MITRE ATLAS     AI/ML Adversarial https://atlas.mitre.org                                      AI-specific extension of  Expanding
                  Threat Landscape                                                               ATT&CK. Covers            2026
                                                                                                 adversarial inputs, model 
                                                                                                 theft, prompt injection,  
                                                                                                 agentic AI control        
                                                                                                 boundary violations.      
                                                                                                 Actively expanding for    
                                                                                                 LLM/agent threat          
                                                                                                 modelling (2026).         

  MITRE D3FEND    Defensive         https://d3fend.mitre.org                                     Defensive complement to   v1.3.0 ---
  1.3.0           Countermeasures                                                                ATT&CK. Maps              Dec 2025
                  Knowledge Graph                                                                countermeasures directly  
                                                                                                 to ATT&CK technique IDs.  
                                                                                                 v1.3.0 added OT extension 
                                                                                                 (Dec 2025). Use for       
                                                                                                 defensive gap analysis    
                                                                                                 post-red-team engagement. 

  CMMC 2.0        Cybersecurity     https://dodcmmc.com                                          DoD supplier framework    Active
                  Maturity Model                                                                 referencing               
                  Certification                                                                  ATT&CK-aligned threat     
                                                                                                 modelling. Relevant for   
                                                                                                 any Atlas work touching   
                                                                                                 US federal or             
                                                                                                 defence-adjacent clients. 
  -------------------------------------------------------------------------------------------------------------------------------------

> Source notes: MITRE ATT&CK v18.1 released October 2025. D3FEND v1.3.0
> added OT/ICS extension December 2025. NIST SP 800-115 revision overdue
> --- last updated 2008; no confirmed 2026 release date.

**3. AI-Native Penetration Testing Platforms (2025--2026)**

The AI-native pentest tool category matured rapidly through 2025--2026,
moving from prompt-wrapper chat assistants to Dockerised, tool-grounded,
multi-agent pipelines with full observability and structured reporting.
The key architectural innovation common to all leading 2026 frameworks
is the hierarchical multi-agent model: a central orchestrator delegates
discrete engagement phases to specialist sub-agents, mirroring real red
team structures rather than relying on a single super-agent.

BlacksmithAI explicitly articulates this design philosophy: each
specialist agent holds domain expertise across recon, enumeration,
vulnerability analysis, exploitation, and post-exploitation.
BlacksmithAI supports OpenRouter, vLLM, and custom LLM endpoints,
enabling on-premises inference for sensitive engagements. PentAGI goes
furthest in toolchain depth, integrating 20+ tools and implementing
long-term memory via Neo4j knowledge graphs. For data sovereignty
requirements, both BlacksmithAI and PentAGI support local Ollama or vLLM
inference endpoints.

  -----------------------------------------------------------------------------------------------------------------------------
  **Tool**         **Released**   **GitHub / URL**                                **Architecture & Key Features** **Licence**
  ---------------- -------------- ----------------------------------------------- ------------------------------- -------------
  BlacksmithAI     March 2, 2026  https://github.com/yohannesgk/blacksmith        Hierarchical multi-agent:       Open Source
                                                                                  orchestrator → recon →          
                                                                                  scan/enum → vuln analysis →     
                                                                                  exploit → post-exploitation.    
                                                                                  Docker + mini-Kali.             
                                                                                  OpenRouter/vLLM/custom LLM      
                                                                                  backends. Terminal and web UI.  
                                                                                  Metasploit/BeEF integration     
                                                                                  roadmapped.                     

  Zen-AI-Pentest   Feb 11, 2026   https://github.com/SHAdd0WTAka/Zen-Ai-Pentest   State-machine agent             Open Source
                                                                                  orchestration: recon → vuln     
                                                                                  scan → exploit → report agents. 
                                                                                  Integrates Nmap, Metasploit.    
                                                                                  CLI, API, and web interfaces.   
                                                                                  Compliance reporting output.    

  PentAGI          Feb 24, 2026   https://github.com/vxcontrol/pentagi            20+ integrated tools (Nmap,     Open Source
                                                                                  Metasploit, sqlmap).            
                                                                                  Researcher/developer/executor   
                                                                                  multi-agent roles. Long-term    
                                                                                  memory via Neo4j/Graphiti.      
                                                                                  Claude/GPT/Gemini/Ollama LLM    
                                                                                  support. Full observability     
                                                                                  stack (OpenTelemetry, Loki).    
                                                                                  Docker Compose deploy.          

  PentestGPT       2024 ---       https://github.com/GreyDGL/PentestGPT           GPT-guided interactive          Open Source
                   active                                                         pentesting assistant. Task      
                                                                                  decomposition and guidance      
                                                                                  model. Less autonomous than     
                                                                                  2026 frameworks but             
                                                                                  well-documented and widely      
                                                                                  deployed.                       

  Kali AI Mode     Early 2026     https://www.kali.org                            Native AI-assisted pentesting   Built into
                                                                                  integrated directly into Kali   Kali
                                                                                  Linux OS. Tool suggestion,      
                                                                                  command generation, workflow    
                                                                                  guidance. Reduces               
                                                                                  context-switching.              
  -----------------------------------------------------------------------------------------------------------------------------

> Source notes: BlacksmithAI --- github.com/yohannesgk/blacksmith.
> Zen-AI-Pentest --- github.com/SHAdd0WTAka/Zen-Ai-Pentest. PentAGI ---
> github.com/vxcontrol/pentagi, February 24, 2026. Kali AI mode ---
> kali.org. AI pentesting landscape --- spark42.tech January 30, 2026;
> escape.tech updated March 2026.

**4. Reconnaissance and Recon OSINT Tools**

Recon tools serve the pre-exploitation intelligence-gathering phase
across both penetration testing engagements and standalone OSINT
investigations. The tools below are ordered by typical deployment
sequence in an engagement.

  ------------------------------------------------------------------------------------------------------------------
  **Tool**       **URL**                                         **Function**                           **Access**
  -------------- ----------------------------------------------- -------------------------------------- ------------
  Nmap 7.98      https://nmap.org                                Network discovery, port scanning,      Free / OSS
                                                                 OS/service fingerprinting. NSE         
                                                                 scripting engine. First tool in every  
                                                                 engagement. Pre-installed Kali.        

  Masscan        https://github.com/robertdavidgraham/masscan    Internet-scale port scanner. Up to 10M Free / OSS
                                                                 packets/sec. Faster than Nmap for      
                                                                 large-scope recon. Outputs             
                                                                 Nmap-compatible XML.                   

  RustScan       https://github.com/RustScan/RustScan            Rust-based port scanner. Scans all     Free / OSS
                                                                 65,535 ports in under 3 seconds; hands 
                                                                 off to Nmap for service detection.     
                                                                 Speed layer before Nmap.               

  Amass          https://github.com/owasp-amass/amass            OWASP-maintained DNS enumeration,      Free / OSS
                                                                 subdomain mapping, ASN intelligence.   
                                                                 Integrates certificate transparency,   
                                                                 passive DNS.                           

  Subfinder      https://github.com/projectdiscovery/subfinder   Passive subdomain discovery from 40+   Free / OSS
                                                                 sources (Shodan, VirusTotal, Censys,   
                                                                 SecurityTrails). ProjectDiscovery      
                                                                 tool; complements Amass.               

  httpx          https://github.com/projectdiscovery/httpx       Fast HTTP probe. Takes subdomain list, Free / OSS
                                                                 validates active hosts, collects       
                                                                 status codes, titles, tech stack.      
                                                                 Pipeline link between Subfinder/Amass  
                                                                 and Nuclei.                            

  Nuclei         https://github.com/projectdiscovery/nuclei      Template-based vulnerability scanner.  Free / OSS
                                                                 11,000+ community templates covering   
                                                                 CVEs, misconfigs, exposed panels,      
                                                                 default creds. Fast pipeline-native    
                                                                 scanning.                              

  theHarvester   https://github.com/laramies/theHarvester        Email addresses, subdomains, IPs from  Free / OSS
                                                                 search engines, PGP servers.           
                                                                 First-stage org footprinting.          
                                                                 Pre-installed Kali.                    

  SpiderFoot     https://www.spiderfoot.net                      200+ modules; automated OSINT across   Free / OSS
                                                                 domains, IPs, emails, usernames. Web   
                                                                 UI and CLI. Best for comprehensive     
                                                                 automated recon pipelines.             

  Shodan         https://shodan.io                               Search engine for internet-facing      Freemium
                                                                 devices, open ports, banners,          
                                                                 ICS/SCADA. API integration with        
                                                                 Maltego, SpiderFoot.                   

  Censys         https://censys.io                               Internet-wide device and certificate   Freemium
                                                                 scanning. Strong TLS/SSL coverage.     
                                                                 REST API. Complements Shodan.          

  Recon-ng       https://github.com/lanmaster53/recon-ng         Modular web intelligence framework     Free / OSS
                                                                 (CLI). Module marketplace for passive  
                                                                 recon. Structured workspace/reporting  
                                                                 model.                                 

  Maltego        https://maltego.com                             Visual link-analysis platform.         Freemium
                                                                 Transform-based entity graph: people,  
                                                                 domains, IPs, emails, social accounts. 
                                                                 500+ transform integrations. Used by   
                                                                 law enforcement and Bellingcat.        

  DNSDumpster    https://dnsdumpster.com                         Domain infrastructure mapping:         Free
                                                                 subdomains, DNS records, IP            
                                                                 relationships. Browser-based, free, no 
                                                                 login.                                 

  ExifTool       https://exiftool.org                            Metadata extraction from images,       Free / OSS
                                                                 documents, audio, video. Geolocation,  
                                                                 timestamps, device info. Pre-installed 
                                                                 Kali.                                  
  ------------------------------------------------------------------------------------------------------------------

> Source notes: Nuclei 11,000+ templates as of March 2026 ---
> projectdiscovery.io. RustScan and Masscan deployment sequence from
> PTES pre-engagement phase. Subfinder/httpx/Nuclei pipeline from
> ProjectDiscovery documentation.

**5. Exploitation Frameworks**

Exploitation frameworks provide the technical capability layer for
validating identified vulnerabilities, simulating adversary
post-exploitation, and demonstrating business impact during authorised
red team engagements. All tools below require explicit authorisation
before deployment against any target. Their inclusion here is for
research and authorised security assessment purposes only.

  ------------------------------------------------------------------------------------------------------
  **Tool**     **URL**                                   **Function**                       **Access**
  ------------ ----------------------------------------- ---------------------------------- ------------
  Metasploit   https://metasploit.com                    Industry-standard exploitation     Free / Pro
  6.x                                                    framework. 2,000+ modules.         tier
                                                         Post-exploitation, pivoting,       
                                                         payload generation. msfconsole     
                                                         CLI. Pre-installed Kali.           
                                                         Roadmapped into                    
                                                         BlacksmithAI/PentAGI.              

  Cobalt       https://cobaltstrike.com                  Commercial adversary simulation    Commercial
  Strike 4.12                                            platform. Beacon C2, lateral       
                                                         movement, team collaboration. De   
                                                         facto red team standard. Cloned in 
                                                         open-source (Sliver, Havoc).       

  Sliver 1.7.3 https://github.com/BishopFox/sliver       Open-source adversary simulation   Free / OSS
                                                         C2 framework (Cobalt Strike        
                                                         alternative). gRPC-based,          
                                                         cross-platform, modern.            

  Havoc        https://github.com/HavocFramework/Havoc   Modern C2 framework with GUI       Free / OSS
                                                         teamserver. Demon agent with sleep 
                                                         obfuscation. Open-source Cobalt    
                                                         Strike alternative with active     
                                                         development.                       

  Brute Ratel  https://bruteratel.com                    Commercial red team C2 platform.   Commercial
  C4                                                     Evasion-focused; designed to       
                                                         bypass EDR. Cadmium agent. Used in 
                                                         advanced adversary simulation.     

  Empire /     https://github.com/BC-Security/Empire     PowerShell/Python                  Free / OSS
  Starkiller                                             post-exploitation framework. GUI   
                                                         via Starkiller. Active BC-Security 
                                                         fork of original Empire.           

  sqlmap       https://sqlmap.org                        Automated SQL injection detection  Free / OSS
                                                         and exploitation. Database         
                                                         fingerprinting, data extraction,   
                                                         privilege escalation.              
                                                         Pre-installed Kali.                

  Burp Suite   https://portswigger.net/burp              Web application security testing   Freemium /
                                                         proxy. Intercept, modify, replay   Pro
                                                         HTTP/S traffic. Spider, scanner,   
                                                         intruder, repeater. Industry       
                                                         standard for web engagements.      

  Nikto        https://github.com/sullo/nikto            Web server vulnerability scanner.  Free / OSS
                                                         Checks 6,700+ potential            
                                                         vulnerabilities and                
                                                         misconfigurations. Pre-installed   
                                                         Kali.                              

  John the     https://hashcat.net                       Password cracking and hash         Free / OSS
  Ripper /                                               analysis. GPU-accelerated          
  Hashcat                                                (Hashcat). Essential for           
                                                         credential exposure assessment     
                                                         post-breach simulation.            
  ------------------------------------------------------------------------------------------------------

> Source notes: Cobalt Strike 4.12 as of Q1 2026. Sliver 1.7.3 ---
> BishopFox GitHub. Havoc and Brute Ratel C4 added at v1.1; both active
> alternatives to Cobalt Strike in advanced red team engagements.
> BlacksmithAI and PentAGI roadmap Metasploit as their next major
> integration milestone.

**6. OSINT Investigation Platforms**

OSINT platforms serve both the recon phase of penetration testing and
standalone intelligence investigations. The Atlas research programme
maintains active interest in multilingual OSINT capability given the
eight-language foreign source programme under Pillar 1; Babel X is
flagged as the primary tool for cross-language social monitoring.

  ------------------------------------------------------------------------------------------------------------
  **Platform**   **URL**                                        **Function**                      **Access**
  -------------- ---------------------------------------------- --------------------------------- ------------
  ShadowDragon   https://shadowdragon.io                        Commercial OSINT and threat       Commercial
  Horizon                                                       intelligence platform. 600+ data  
                                                                sources including dark web. Link  
                                                                analysis, continuous monitoring,  
                                                                identity validation. Law          
                                                                enforcement grade.                

  Maltego        https://maltego.com                            Primary entity relationship       Freemium
                                                                visualisation tool for OSINT      
                                                                investigations. Transform-based   
                                                                entity graph. 500+ transform      
                                                                integrations. Transforms automate 
                                                                data enrichment.                  

  Sherlock       https://github.com/sherlock-project/sherlock   Username enumeration across 400+  Free / OSS
                                                                platforms. Python/MIT. Rapidly    
                                                                maps social footprint from single 
                                                                identifier.                       

  Recorded       https://recordedfuture.com                     Commercial threat intelligence    Commercial
  Future                                                        platform. Predictive analytics,   
                                                                dark web monitoring, real-time    
                                                                SIEM integration.                 

  DeHashed       https://dehashed.com                           Breach data search engine.        Freemium
                                                                Billions of records: emails,      
                                                                usernames, IPs, passwords,        
                                                                addresses. Credential exposure    
                                                                checks.                           

  GreyNoise      https://greynoise.io                           Distinguishes targeted attack     Freemium
                                                                traffic from internet background  
                                                                noise. API-driven. Reduces false  
                                                                positives in threat hunting.      
                                                                Integrated into SpiderFoot module 
                                                                ecosystem.                        

  VirusTotal     https://virustotal.com                         Multi-engine malware analysis,    Free / API
                                                                URL/file reputation, IOC lookup.  tiers
                                                                70+ AV engines. API for           
                                                                automation.                       

  OSINT          https://osintframework.com                     Curated directory of OSINT tools  Free
  Framework                                                     organised by target type.         
                                                                Web-based navigation map.         
                                                                Reference for tool selection.     

  Have I Been    https://haveibeenpwned.com                     Breach notification service. API  Free / API
  Pwned                                                         for bulk email/domain exposure    
                                                                checks. Integrates with Maltego   
                                                                transforms.                       

  Babel X        https://babelstreet.com/babel-x                Multilingual social media and web Commercial
                                                                monitoring across 200+ languages. 
                                                                Real-time threat tracking.        
                                                                Directly relevant to Atlas        
                                                                8-language research programme.    

  FOCA           https://github.com/ElevenPaths/FOCA            Document metadata extraction and  Free / OSS
                                                                analysis tool. Finds metadata and 
                                                                hidden information in publicly    
                                                                indexed documents (PDF, DOCX,     
                                                                XLSX, PPTX). Extracts usernames,  
                                                                software versions, email          
                                                                addresses, server paths from      
                                                                document properties. Integrates   
                                                                with Google/Bing dork queries to  
                                                                discover documents automatically. 
  ------------------------------------------------------------------------------------------------------------

> Source notes: ShadowDragon expanded to 600+ data sources as of early
> 2026. FOCA added at v1.1 --- directly relevant to Section 9 document
> retrieval workflows; extracts metadata from dork-discovered files.
> GreyNoise API integrated into SpiderFoot module ecosystem.

**7. CVE and Vulnerability Intelligence Feeds**

Vulnerability intelligence feeds provide the raw data layer for both
pre-engagement surface mapping and ongoing security monitoring. CISA\'s
Known Exploited Vulnerabilities catalogue is the highest-signal feed
available: every CVE listed has confirmed in-the-wild exploitation.
Note: the NVD backlog crisis continues into 2026 --- NIST paused
enrichment of CVEs submitted after February 2024, creating a gap between
CVE publication and full CVSS/CWE/CPE enrichment. Cross-reference with
EPSS scores and CISA KEV for triage.

  --------------------------------------------------------------------------------------------------------------------------------------
  **Source**     **URL**                                                                  **Function**                      **Access**
  -------------- ------------------------------------------------------------------------ --------------------------------- ------------
  NVD (NIST)     https://nvd.nist.gov                                                     US National Vulnerability         Free
                                                                                          Database. Authoritative CVE       
                                                                                          enrichment with CVSS scores, CWE  
                                                                                          mappings, CPE data. Note: backlog 
                                                                                          crisis ongoing --- enrichment     
                                                                                          paused for CVEs submitted after   
                                                                                          Feb 2024.                         

  CVE Programme  https://cve.mitre.org                                                    Root CVE identifier authority.    Free
  (MITRE)                                                                                 All CVE IDs originate here. Check 
                                                                                          for newly published CVEs before   
                                                                                          engagements.                      

  CISA KEV       https://cisa.gov/known-exploited-vulnerabilities-catalog                 Known Exploited Vulnerabilities   Free
                                                                                          catalogue. CISA-mandated patching 
                                                                                          list. Highest-priority CVEs       
                                                                                          confirmed exploited in the wild.  
                                                                                          Updated frequently. Subscribe via 
                                                                                          RSS or API.                       

  Exploit-DB     https://exploit-db.com                                                   Offensive Security public exploit Free
                                                                                          archive. CVE cross-referenced.    
                                                                                          Proof-of-concept code repository. 
                                                                                          Pre-indexed in Metasploit. Also   
                                                                                          hosts the Google Hacking Database 
                                                                                          (GHDB) with 7,000+ dork entries.  

  CVSS           https://nvd.nist.gov/vuln-metrics/cvss                                   CVSS v3.1/v4.0                    Free
  Calculator                                                                              base/temporal/environmental score 
  (NIST)                                                                                  calculator. v4.0 released October 
                                                                                          2023; adopted in NVD.             

  Vulners        https://vulners.com                                                      Unified vulnerability search      Freemium
                                                                                          across NVD, Exploit-DB, vendor    
                                                                                          advisories, Packetstorm.          
                                                                                          API-driven. Good for bulk triage. 

  Google OSV     https://osv.dev                                                          Open Source Vulnerabilities       Free
                                                                                          database. Covers npm, PyPI, Go,   
                                                                                          Maven, NuGet, RubyGems, Hex,      
                                                                                          CRAN, Packagist. JSON-based API.  
                                                                                          Maintained by Google. Fills gaps  
                                                                                          in NVD for open-source dependency 
                                                                                          chains.                           

  GitHub         https://github.com/advisories                                            GitHub Security Advisory          Free
  Advisories                                                                              database. Auto-published for      
                                                                                          dependencies with CVE or GHSA     
                                                                                          identifiers. Integrated with      
                                                                                          Dependabot. Actionable at the     
                                                                                          repo level.                       

  EPSS (FIRST)   https://www.first.org/epss                                               Exploit Prediction Scoring        Free
                                                                                          System. Probability score (0--1)  
                                                                                          predicting exploitation in the    
                                                                                          wild within 30 days. Complements  
                                                                                          CVSS for triage prioritisation.   
                                                                                          Updated daily.                    

  VulnDB         https://flashpoint.io/vulndb                                             Commercial vulnerability database Commercial
  (Flashpoint)                                                                            with faster publication than NVD. 
                                                                                          Covers vulnerabilities not in CVE 
                                                                                          programme. Useful during NVD      
                                                                                          backlog gaps.                     

  ATT&CK         https://center-for-threat-informed-defense.github.io/mappings-explorer   MITRE CVE-to-ATT&CK technique     Free
  Mappings                                                                                mapping. Links CVE exploitation   
  Explorer                                                                                methods to Enterprise matrix      
                                                                                          technique IDs. Bridges            
                                                                                          vulnerability management and      
                                                                                          threat modelling.                 
  --------------------------------------------------------------------------------------------------------------------------------------

> Source notes: NVD backlog crisis --- NIST paused enrichment Feb 2024;
> CISA and MITRE assisting with triage. Google OSV and GitHub Advisories
> added at v1.1 to cover open-source dependency gaps. EPSS v3 ---
> first.org/epss; updated daily. CVSS v4.0 adopted from October 2023.

**8. Strategic Notes and Workflow Integration**

**8.1 AI-Native Tool Deployment Guidance**

BlacksmithAI and PentAGI are the two most operationally mature AI-native
frameworks as of March 2026. For Atlas assessments, the recommended
deployment sequence is: PentAGI for deep engagements requiring long-term
memory and 20+ tool orchestration; BlacksmithAI for faster, lighter
engagements where LLM backend flexibility (local vLLM) is the priority.
Both require Docker. Neither yet integrates Metasploit natively, meaning
exploit validation still requires manual handoff to Metasploit or Burp
Suite.

For any engagement where data sovereignty matters --- client NDA,
Australian Privacy Act compliance --- run PentAGI or BlacksmithAI
against a local Ollama or vLLM inference endpoint rather than OpenAI or
OpenRouter cloud APIs. BlacksmithAI\'s config.json supports custom
provider endpoints; PentAGI supports Ollama natively.

**8.2 OSINT Workflow Recommendation**

The recommended OSINT stack for Atlas investigations: SpiderFoot for
automated initial recon pipeline (200+ modules, API integration);
Maltego for visual relationship mapping and hypothesis testing; Sherlock
for username-based social account mapping; Shodan/Censys for
infrastructure exposure. For dark web coverage or continuous monitoring,
ShadowDragon Horizon is the commercial option. For multilingual
monitoring across Atlas\'s eight language domains, Babel X is the only
platform with adequate coverage depth. Add FOCA to any workflow
involving dork-discovered document sets --- it extracts metadata
(usernames, software versions, server paths) from publicly indexed files
that standard recon tools miss.

**8.3 Framework Update Calendar**

MITRE ATT&CK releases bi-annually (April and October). v19 is scheduled
for April 2026. Monitor ATLAS quarterly given its active AI-specific
expansion. OWASP WSTG v4.3 is in preparation; check owasp.org for
release. NIST SP 800-115 revision is overdue (last updated 2008); no
confirmed 2026 release date. EU AI Act full implementation deadline
August 2, 2026 --- mandatory red teaming provisions apply to high-risk
AI systems. Monitor for CFTC and EU AI Act enforcement guidance
affecting any AI-enabled security tooling used on behalf of regulated
clients.

**8.4 Identified Gaps**

Three gaps remain. Physical security assessment tooling (social
engineering, RFID cloning, lock picking frameworks) is not covered.
ICS/OT AI-native security frameworks are absent --- D3FEND\'s new OT
extension (Dec 2025) partially addresses this defensively but offensive
ICS tooling (Claroty, Dragos, Grassmarlin) is not catalogued. Supply
chain validation tooling (Sigstore, SLSA framework) is absent. These
will be addressed in v1.2 if any of these engagement surfaces become
active.

**9. Web Document Retrieval and Search Engine Dorking**

Web document retrieval via search engine dorking is a passive OSINT
technique that exploits publicly indexed content without direct
interaction with target infrastructure. All traffic flows between the
investigator\'s browser and the search engine\'s servers --- the
target\'s intrusion detection systems are not triggered. The technique
ranges from simple filetype filtering to layered multi-operator queries
that surface misconfigured directories, exposed credentials, and
inadvertently published sensitive documents.

As of early 2026, the operator landscape has fragmented significantly.
Google has deprecated 12+ operators since 2010, including cache: (fully
removed March 2024, documentation removed September 2024) and related:
(removed July 2023). No new Google operators have been added since 2019.
The practical consequence is that effective document recon now requires
multi-engine discipline: Bing offers operators Google lacks entirely
(ip:, linkfromdomain:, near:N); Yandex provides unique proximity and
date operators plus AI-powered facial recognition in reverse image
search; Perplexity AI is the first AI engine to formally support
structured operators (site:, filetype:, before:, after:). Using only
Google for OSINT document discovery in 2026 is incomplete methodology.

**9.1 Google Operators --- Current Status (2026)**

Google Search Central formally documents only four operators as of
December 2025: site:, filetype:, imagesize:, and src:. In practice,
significantly more operators function reliably. The table below reflects
real-world testing consensus as of February 2026.

  ------------------------------------------------------------------------------------------
  **Operator**   **Syntax Example**       **Function**                          **Status**
  -------------- ------------------------ ------------------------------------- ------------
  \" \"          \"annual report 2025\"   Forces exact phrase matching.         STABLE
                                          Prevents Google\'s synonym            
                                          substitution. Single most important   
                                          operator for document retrieval.      

  site:          site:target.com          Restricts results to a domain,        STABLE
                                          subdomain, specific directory, or TLD 
                                          class (e.g. site:.gov.au).            
                                          Universally supported across all six  
                                          major engines.                        

  filetype: /    filetype:pdf OR ext:xlsx Restricts to specific file            STABLE
  ext:                                    extensions. Both operators are        
                                          identical in behaviour. Key document  
                                          types: pdf, doc, docx, xls, xlsx,     
                                          pptx, csv, txt, xml, json, sql, env,  
                                          log, bak.                             

  intitle:       intitle:\"board          Requires keyword in the HTML title    STABLE
                 minutes\"                tag. More precise than intext: for    
                                          document discovery --- title text is  
                                          set by the author, not the crawler.   

  allintitle:    allintitle:procurement   All words must appear in the page     STABLE
                 tender 2025              title. Do not combine with other      
                                          operators in the same query ---       
                                          produces unpredictable results.       

  inurl:         inurl:reports            Requires keyword in the URL.          STABLE
                 inurl:finance            Effective for targeting directory     
                                          structures (e.g. inurl:/docs/         
                                          inurl:/internal/).                    

  allinurl:      allinurl:admin login     All words must appear in the URL.     STABLE
                 portal                   Same caveat as allintitle: --- do not 
                                          combine with other operators.         

  intext:        intext:\"not for public  Requires keyword in the page body.    STABLE
                 release\"                Broad; use to surface documents       
                                          containing specific phrases           
                                          regardless of title or URL structure. 

  allintext:     allintext:confidential   All words must appear in body text.   STABLE
                 draft embargo            Same caveat applies --- use           
                                          standalone.                           

  OR / \|        filetype:pdf OR          Returns results matching either term. STABLE
                 filetype:docx            Must be uppercase. Essential for      
                                          multi-format document sweeps.         

  \- (exclude)   -site:linkedin.com       Excludes results containing the term. STABLE
                 -inurl:blog              Use to suppress noisy domains or      
                                          irrelevant subdirectories.            

  \* (wildcard)  \"Q\* financial results  Wildcard matching any word within     STABLE
                 2025\"                   quoted phrases. Useful for catching   
                                          Q1/Q2/Q3/Q4 variants in a single      
                                          query.                                

  ( ) grouping   (site:gov.au OR          Groups terms for complex Boolean      STABLE
                 site:gov) filetype:pdf   logic. Combine with OR to sweep       
                                          multiple TLDs or domains.             

  before:        before:2025-01-01        Filters results published before a    BETA ---
                                          date (YYYY-MM-DD or YYYY format).     unreliable
                                          Beta since April 2019; Danny Sullivan 
                                          confirmed YYYY-MM-DD is the required  
                                          format. Inconsistent --- Google\'s    
                                          built-in Tools date filter is often   
                                          more reliable.                        

  after:         after:2024-06-01         Filters results published after a     BETA ---
                                          date. Same reliability caveat as      unreliable
                                          before:. Use in combination for       
                                          narrow date windows.                  

  source:        source:reuters           Restricts Google News results to a    STABLE (News
                                          specific publication. Useful for      only)
                                          monitoring coverage of a target       
                                          organisation.                         

  define:        define:OSINT             Returns dictionary definitions.       STABLE
                                          Limited intelligence value but useful 
                                          for standardising terminology in      
                                          reports.                              
  ------------------------------------------------------------------------------------------

> Source notes: Google Search Central operator documentation --- last
> updated December 10, 2025. cache: removal confirmed by Danny Sullivan
> March 2024. Max Intel Google Dorking Reference 2026 (maxintel.org,
> February 9, 2026). StationX Google Dorks Cheat Sheet 2026
> (stationx.net, February 2, 2026).

**9.2 Deprecated Google Operators --- Graveyard**

The following operators are frequently cited in outdated guides as
functional. They are not. Using them in automated pipelines will produce
incorrect results.

  --------------------------------------------------------------------------------------
  **Operator**   **What It Did**   **Removed**   **Current Status**
  -------------- ----------------- ------------- ---------------------------------------
  cache:         Displayed         2024          Cache links disappeared Dec 2023--Jan
                 Google\'s stored                2024. Danny Sullivan confirmed removal
                 version of a page               March 2024. Documentation removed
                 --- cornerstone                 September 17, 2024. Replace with
                 of OSINT for                    Wayback Machine (web.archive.org).
                 viewing deleted                 
                 or modified pages               

  related:       Found websites    2023          Removed from Search Central
                 similar to a                    documentation July 18, 2023. Sullivan
                 given URL ---                   noted it \'hasn\'t really worked that
                 useful for                      well for some time.\'
                 competitor and                  
                 ecosystem mapping               

  info: / id:    Displayed page    2017          Now redirects to a normal search result
                 metadata and                    for the URL. No intelligence value.
                 useful navigation               
                 links for a URL                 

  link:          Found pages       2017          Officially killed. May return
                 linking to a URL                sampled/inaccurate results. Replace
                 --- backlink                    with Bing\'s linkfromdomain: or
                 discovery                       Ahrefs/Majestic.

  \+ (force      Forced exact      2011          Deprecated when Google+ launched; never
  match)         match on a word,                restored. Replace with double-quotes
                 preventing                      around the word.
                 synonym expansion               

  \~ (synonym)   Included synonyms 2013          Removed because Google now includes
                 of a search term                synonyms by default.

  phonebook:     Searched for      2010          Removed for privacy reasons.
                 phone numbers                   
                 associated with a               
                 name                            
  --------------------------------------------------------------------------------------

> Source notes: Max Intel Google Dorking Reference 2026 (maxintel.org,
> February 9, 2026). Danny Sullivan cache: deprecation confirmation via
> X/Twitter, March 2024. Google Search Central changelog.

**9.3 Cross-Engine Operator Matrix**

Single-engine dorking is insufficient methodology in 2026. Each engine
indexes different content and supports a different operator set. Bing\'s
ip: and linkfromdomain: operators have no Google equivalent; Yandex\'s
proximity operator /N and date: syntax expose capabilities unavailable
elsewhere; DuckDuckGo disabled most operators in April 2023 and only
partially restored them.

  --------------------------------------------------------------------------------------------------------------------------------
  **Operator**      **Google**       **Bing**      **Yandex**      **DuckDuckGo**   **Brave**   **Notes**
  ----------------- ---------------- ------------- --------------- ---------------- ----------- ----------------------------------
  site:             YES              YES           YES             YES              YES         Universally supported. Only
                                                                                                operator reliable across all six
                                                                                                major engines.

  filetype: / ext:  YES              YES           mime: only      Unreliable       YES         Bing uses filetype:; Yandex
                                     (filetype:)                                                requires mime:pdf syntax;
                                                                                                DuckDuckGo partial.

  intitle:          YES              YES           title:          Unreliable       YES         Yandex uses title: not intitle:.
                                                   (different                                   
                                                   syntax)                                      

  inurl:            YES              NO (suspended YES             Unreliable       NO          Bing suspended inurl: in 2007 to
                                     2007)                                                      prevent data mining --- never
                                                                                                restored.

  intext: / inbody: intext:          inbody:       NO              NO               inbody:     Bing and Brave use inbody: ---
                                                                                                identical function to Google\'s
                                                                                                intext:.

  ip:               NO               YES (Bing     NO              NO               NO          Bing-exclusive. ip:203.0.113.1
                                     only)                                                      returns all indexed pages hosted
                                                                                                at that IP. Essential for
                                                                                                infrastructure recon.

  linkfromdomain:   NO               YES (Bing     NO              NO               NO          Bing-exclusive. Maps all external
                                     only)                                                      sites a target domain links to.
                                                                                                Useful for supply chain and
                                                                                                partnership mapping.

  near:N /          AROUND(X) ---    near:N ---    NO              NO               NO          Proximity operator. Bing\'s near:N
  AROUND(X)         unreliable       reliable                                                   is more reliable than Google\'s
                                                                                                AROUND(X). Finds co-occurrence
                                                                                                within N words.

  date: / before: / before:/after:   UI only       date:YYYYMMDD   UI only          NO          Yandex date: operator is the most
  after:            (beta)                         (reliable)                                   reliable structured date filter
                                                                                                across all engines.

  \" \" (exact      YES              YES           YES             Partial          YES         Most reliable operator across all
  phrase)                                                                                       engines for locking in specific
                                                                                                document titles or phrases.

  \- (exclude)      YES              YES           \~\~ (different Partial          YES         Yandex uses \~\~ instead of - for
                                                   syntax)                                      exclusion.

  \* (wildcard)     YES (in quotes   YES           YES             NO               NO          Google wildcard only works within
                    only)                                                                       quoted phrases.

  OR / \|           OR (uppercase)   OR            \| (pipe)       OR               OR          Yandex uses pipe \| for OR logic.

  ( ) grouping      YES              YES           YES             Partial          YES         Boolean grouping generally
                                                                                                supported except DuckDuckGo.
  --------------------------------------------------------------------------------------------------------------------------------

> Source notes: Max Intel Google Dorking Reference 2026 (maxintel.org,
> February 9, 2026) --- cross-engine compatibility matrix. DuckDuckGo
> operator degradation --- April 2023. Bing ip: and linkfromdomain:
> operators --- Microsoft Bing Webmaster documentation. Yandex operator
> syntax --- Yandex Search operator reference.

**9.4 Document Discovery Workflow --- Layered Query Construction**

Effective document retrieval uses layered query construction: start
broad, narrow progressively, then extract and analyse. The methodology
below applies across both penetration testing engagements (passive recon
phase) and Atlas research intelligence gathering.

Phase 1 --- Domain mapping. Run site:target.com without additional
filters to establish total indexed page count. Then scope to
document-hosting directories: site:target.com inurl:/docs OR
inurl:/reports OR inurl:/uploads OR inurl:/files. Note any directory
patterns for use in subsequent queries.

Phase 2 --- Filetype sweep. Sweep for all high-value document types in a
single query: site:target.com (filetype:pdf OR filetype:docx OR
filetype:xlsx OR filetype:pptx OR filetype:csv). For configuration and
code exposure, run separately: site:target.com (ext:env OR ext:log OR
ext:sql OR ext:bak OR ext:config OR ext:xml OR ext:json). The
env/log/sql/bak sweep is specifically relevant to penetration testing
pre-engagement recon.

Phase 3 --- Content filtering. Add intext: or intitle: filters to target
documents by likely content rather than by type alone. Examples:
site:target.com filetype:pdf intitle:\"board\" OR intitle:\"strategy\"
OR intitle:\"roadmap\"; site:target.com filetype:xlsx intext:\"salary\"
OR intext:\"payroll\"; site:gov.au filetype:pdf intext:\"not for public
release\" -inurl:media. The minus operator is critical for suppressing
noise --- strip press release directories, career pages, and legal
sections before reviewing results.

Phase 4 --- Cross-engine validation. Re-run the highest-yield queries on
Bing (substituting inbody: for intext:, filetype: unchanged) and on
Yandex with adapted syntax. Bing indexes content that Google does not,
particularly in government and enterprise domains. Yandex\'s date:
operator is useful for surfacing recently indexed documents that
Google\'s before:/after: beta operators may miss.

Phase 5 --- Metadata extraction. Feed dork-discovered document URLs into
FOCA for automated metadata extraction. FOCA will extract usernames,
software versions, printer names, email addresses, and server path
strings embedded in document properties --- this data is invisible to
standard text review but frequently reveals internal infrastructure
naming conventions and staff identities.

**9.5 High-Value Document Dork Patterns**

The following patterns are organised by intelligence objective. All are
passive queries against public search engine indexes. The Google Hacking
Database (GHDB) at exploit-db.com/google-hacking-database catalogues
7,000+ validated dork patterns organised by category; cross-reference
before constructing novel queries.

  ------------------------------------------------------------------------
  **Objective**   **Query Pattern**              **Notes**
  --------------- ------------------------------ -------------------------
  Public company  site:target.com (filetype:pdf  Strip noise first.
  documents ---   OR filetype:docx OR            Removes press releases
  general sweep   filetype:xlsx) -inurl:blog     and blog attachments from
                  -inurl:press                   results.

  Board and       site:target.com filetype:pdf   Minutes, policies,
  governance      (intitle:\"board\" OR          committee papers. Often
  documents       intitle:\"committee\" OR       indexed inadvertently.
                  intitle:\"minutes\" OR         
                  intitle:\"governance\")        

  Financial and   site:target.com filetype:xlsx  Spreadsheets containing
  budget          (intext:\"budget\" OR          financial data. xlsx
  documents       intext:\"forecast\" OR         sweeps often surface
                  intext:\"P&L\")                internal working files.

  Configuration   site:target.com (ext:env OR    High-priority pentest
  and credential  ext:config OR ext:log OR       recon sweep. env files
  exposure        ext:sql OR ext:bak)            frequently contain API
                                                 keys and database
                                                 credentials.

  Personnel and   site:target.com filetype:pdf   Org charts and staff
  HR documents    (intitle:\"staff\" OR          directories are
                  intitle:\"organisation chart\" frequently indexed.
                  OR intitle:\"directory\")      Valuable for social
                                                 engineering
                                                 pre-engagement.

  Government      site:tenders.gov.au OR         Australian government
  tendering (AU)  site:qtenders.gov.au           procurement portals.
                  filetype:pdf \"target          Named organisation in
                  organisation name\"            scope documents.

  Academic and    site:target.edu OR             Academic institutions.
  research        site:target.edu.au             Often richest publicly
  documents       filetype:pdf                   indexed document set for
                  (intitle:\"thesis\" OR         any given organisation.
                  intitle:\"dissertation\" OR    
                  intitle:\"working paper\")     

  Specific person \"First Last\" (filetype:pdf   Returns CVs,
  document sweep  OR filetype:docx OR            presentations, authored
                  filetype:pptx)                 papers. Broad --- run
                                                 without site: restriction
                                                 first.

  Exposed         site:target.com (ext:sql OR    Database file exposure.
  database dumps  ext:db OR ext:sqlite) OR       Index-of queries surface
                  intitle:\"index of\"           directory listings with
                  \"db_backup\"                  backup files.

  Open directory  site:target.com                Misconfigured
  listings        intitle:\"index of\" (\"parent Apache/Nginx servers
                  directory\" OR \"last          exposing directory trees.
                  modified\")                    High value for file
                                                 enumeration.

  Sensitive       site:target.com filetype:pdf   Documents containing
  internal        (intext:\"confidential\" OR    standard confidentiality
  documents       intext:\"internal use only\"   markers. Frequently
                  OR intext:\"not for            indexed despite those
                  distribution\")                markers.

  Multi-engine    site:target.com filetype:env   Bing sometimes indexes
  credential      OR filetype:log (run on Bing   content Google has
  sweep (Bing)    only)                          deindexed. Run separately
                                                 --- Bing uses identical
                                                 filetype: syntax.
  ------------------------------------------------------------------------

> Source notes: Google Hacking Database (GHDB) ---
> exploit-db.com/google-hacking-database; 7,000+ entries as of March
> 2026. Seek Your Data Google Dorking guide (seekyourdata.com, 2026) ---
> layered query methodology. Recosint Google Dorking Guide 2026
> (recosint.com, January 11, 2026). CybelAngel Google Dorks Cheat Sheet
> 2026 (cybelangel.com, February 2026).

**9.6 Automated Dorking Tools**

Manual query construction is the correct starting approach but
automation becomes necessary for large-scope engagements. The following
tools extend the dorking workflow into systematic, repeatable pipelines.

  ----------------------------------------------------------------------------------------------------------------------------------------
  **Tool**     **URL**                                          **Function**                        **Notes**
  ------------ ------------------------------------------------ ----------------------------------- --------------------------------------
  Google       https://exploit-db.com/google-hacking-database   Crowdsourced repository of 7,000+   Primary reference before constructing
  Hacking                                                       proven dork queries categorised by  novel queries. Categories include:
  Database                                                      target type and vulnerability       files containing passwords, sensitive
  (GHDB)                                                        class. Maintained by Offensive      directories, exposed credentials,
                                                                Security via Exploit-DB.            network devices, web server detection.

  DorkSint     https://github.com/vertex-coder/DorkSint         OSINT dork tool supporting          Multi-engine query dispatch from a
                                                                simultaneous query execution across single command. Reduces manual
                                                                Google, Bing, Yandex, and           re-entry across engines.
                                                                DuckDuckGo. Python-based CLI.       

  SerpScan     https://github.com/th3unkn0n/google-dorks        PHP-based dorking tool that         Useful for bulk target sweeps.
                                                                leverages Google, Bing, Yahoo,      Requires SERP API access.
                                                                Yandex, and Baidu simultaneously    
                                                                via SERP API.                       

  Pagodo       https://github.com/opsdisk/pagodo                Automates passive Google dork       The authoritative automation layer for
                                                                searches using the GHDB. Python.    GHDB. Run against target domains
                                                                Respects rate limits. Designed for  during pentest pre-engagement.
                                                                large-scale GHDB sweeps against a   
                                                                target domain.                      

  DorkGenius / https://dorkgenius.com                           AI-powered dork generator. Describe Useful for novel objectives not
  DorkGPT                                                       the target and objective in natural covered in GHDB. Output must be
                                                                language; returns structured        reviewed before use --- AI-generated
                                                                Google, Bing, and DuckDuckGo        dorks can be imprecise.
                                                                queries.                            

  FOCA         https://github.com/ElevenPaths/FOCA              Metadata extraction from            Critical post-discovery step. Extracts
                                                                dork-discovered documents.          usernames, software, server paths from
                                                                Integrates with Google/Bing to      PDF/DOCX/XLSX/PPTX metadata.
                                                                automate document discovery and     
                                                                metadata extraction in a single     
                                                                workflow.                           

  Wayback      https://web.archive.org                          Replacement for deprecated Google   Essential since cache: removal March
  Machine                                                       cache: operator. Retrieves archived 2024. Use
                                                                versions of pages and documents.    web.archive.org/web/\*/target.com/\*
                                                                Max Intel Wayback Recon tool        for full site crawl history.
                                                                (maxintel.org/wayback-recon.html)   
                                                                extends this for OSINT workflows.   
  ----------------------------------------------------------------------------------------------------------------------------------------

> Source notes: GHDB --- exploit-db.com/google-hacking-database; over
> 7,000 entries March 2026. DorkSint ---
> github.com/vertex-coder/DorkSint. Pagodo ---
> github.com/opsdisk/pagodo. DorkGenius --- dorkgenius.com. cache:
> deprecation --- March 2024 confirmed; Wayback Machine is the
> authoritative replacement.

**9.7 Ethical and Legal Boundaries**

Dorking operates entirely against publicly indexed data and does not
interact with target systems directly. All queries flow through the
search engine\'s servers. However, the following boundaries apply
without exception in all Atlas engagements.

Query only; do not interact. Clicking a dork-discovered link and
downloading or viewing content constitutes interaction with the target
system. In penetration testing pre-engagement passive recon, document
links are recorded but not followed without explicit scope
authorisation. Browsing to a URL is a different legal position to
running a search query.

Respect robots.txt as an indicator. robots.txt is not a technical
barrier but its contents indicate what the owner does not want indexed.
Content appearing in search results despite Disallow directives may have
been indexed before the directive was added. Document the robots.txt
state for the target before executing any dork sweep.

Cache: is gone --- do not attempt to view deleted pages via Google. The
Wayback Machine is the appropriate mechanism for archived content
retrieval; its terms of service apply. Attempting to access cached
versions of pages via third-party cache proxies may constitute
unauthorised access if those proxies bypass access controls.

GDPR, Privacy Act compliance. For Australian engagements, the Privacy
Act 1988 governs collection of personal information even from publicly
available sources. Dork-discovered documents containing personal
information (staff directories, email addresses, HR records) must be
handled under the applicable privacy framework. EU-based targets add
GDPR obligations. Scope legal review before using dork-discovered
personal data in deliverables.

Responsible disclosure. If a dork sweep reveals sensitive data exposure
that was clearly unintentional --- production credentials, live database
dumps, PII --- pause collection, document with screenshots and
timestamps, and report to the organisation\'s security contact or
through a responsible disclosure programme before proceeding.

**10. Web Document Access --- Full Parameter Reference**

This section is the operational parameter reference for accessing
documents on the public web using search engine operators, URL
parameters, and archive access mechanisms. It consolidates every working
parameter combination into a practitioner-ready format. Section 9 covers
the methodology and cross-engine matrix; this section covers the
parameters themselves in maximum specificity. All queries assume passive
reconnaissance against publicly indexed content. For penetration testing
engagements, apply these parameters during the pre-engagement passive
recon phase only; no interaction with target systems occurs.

**10.1 Filetype and Document Format Parameters**

The filetype: and ext: operators are functionally identical on Google
and Bing. Both restrict results to pages where the URL or HTTP
Content-Type header indicates a specific file format. The following
table covers every format with operational intelligence value. Google
officially recognises over 50 filetypes; the subset below is ordered by
OSINT yield priority.

  ---------------------------------------------------------------------------------
  **Parameter**   **Format**    **Primary Use      **Atlas Application**
                                Case**             
  --------------- ------------- ------------------ --------------------------------
  filetype:pdf    PDF           Reports, policies, Primary document sweep for all
                                presentations,     Atlas research pillars.
                                academic papers,   Highest-density intelligence
                                government         format. Run as first pass on any
                                documents, tender  target domain.
                                submissions        

  filetype:docx   Word (2007+)  Internal drafts,   Often contains tracked changes,
                                HR documents,      revision history, embedded
                                contracts,         metadata including author names
                                policies, memos,   and company names.
                                proposals          

  filetype:doc    Word (legacy) Older internal     Legacy format still common in
                                documents, legacy  government and older
                                contracts,         organisations. Contains rich
                                pre-2007           metadata via FOCA extraction.
                                government         
                                publications       

  filetype:xlsx   Excel (2007+) Budget files,      Highest value for financial and
                                financial models,  personnel intelligence.
                                data extracts, HR  Spreadsheets are frequently
                                payroll, project   published with live formula
                                trackers           references revealing internal
                                                   structures.

  filetype:xls    Excel         Older financial    Legacy format. Same metadata
                  (legacy)      data, government   exposure as docx/doc.
                                statistical        
                                releases           

  filetype:pptx   PowerPoint    Board              Board and investor decks
                  (2007+)       presentations,     frequently indexed. Often
                                strategy decks,    contain revenue figures,
                                investor           strategy details, and org charts
                                presentations,     not in public press releases.
                                conference slides  

  filetype:ppt    PowerPoint    Older              Legacy format. Metadata
                  (legacy)      presentations,     extraction via FOCA yields
                                academic slide     useful author and software data.
                                decks              

  filetype:csv    CSV data      Data exports,      Raw structured data. High value
                                statistical        for Mining Exploration ASIC
                                releases, ASIC     company data and government
                                extracts,          statistical datasets under
                                government open    Pillar 1.
                                data               

  filetype:txt    Plain text    Log files, README  Low-frequency but high-yield on
                                files,             pentest engagements. Plain text
                                configuration      config files and credential
                                snippets,          stores are occasionally indexed.
                                credential dumps   

  filetype:xml    XML           Configuration      Pentest-relevant. XML config
                                files, SOAP        files can expose database
                                responses, API     connection strings and API
                                schemas, sitemap   credentials.
                                files              

  filetype:json   JSON          API responses,     Modern web apps frequently
                                configuration      expose JSON config files. High
                                objects, package   pentest value for API key and
                                metadata,          endpoint discovery.
                                geospatial data    

  ext:env         .env          Application        Highest-priority pentest
                  environment   environment        credential sweep. .env files
                  files         variables          indexed via misconfiguration are
                                containing API     the most direct path to
                                keys, database     credential exposure.
                                credentials,       
                                secret keys        

  ext:log         Log files     Application error  Log files frequently contain
                                logs, access logs, usernames, session tokens, IP
                                authentication     addresses, and error stack
                                logs               traces revealing internal
                                                   software versions.

  ext:sql         SQL dump      Database export    Database dumps containing table
                  files         files, backup      structures, user credentials
                                scripts, migration (hashed), and PII. Occasionally
                                files              indexed on development servers.

  ext:bak         Backup files  Application and    Backup files of config files and
                                database backup    databases. Often named with .bak
                                archives           extension and left on
                                                   web-accessible directories.

  ext:config      Config files  IIS, Apache,       Web server and application
                                application        config files. Can expose
                                configuration      database credentials, SMTP
                                                   passwords, and internal network
                                                   paths.

  ext:htpasswd    .htpasswd     Apache directory   Direct credential exposure.
                  files         authentication     These files should never be
                                credential stores  web-accessible but are
                                                   occasionally indexed.

  ext:pem /       Certificate   SSL/TLS private    Critical credential exposure.
  ext:key         and key files keys, SSH private  Private key files discovered via
                                keys, certificate  dork should be immediately
                                files              escalated in penetration testing
                                                   context.

  ext:kdbx /      KeePass       Password manager   Rare but extremely high value.
  ext:kdb         databases     database files     KeePass databases left on
                                                   web-accessible directories.

  ext:ps1         PowerShell    Administrative     Often contain hardcoded
                  scripts       automation         credentials, server names, and
                                scripts,           internal network paths.
                                deployment scripts 

  ext:sh /        Shell scripts Linux/macOS        Same exposure pattern as ps1.
  ext:bash                      automation,        Hardcoded credentials and
                                deployment scripts internal paths common.

  ext:py          Python        Web application    Source code with hardcoded
                  scripts       code, automation   credentials, API keys, and
                                scripts, data      database connection strings.
                                processing         
  ---------------------------------------------------------------------------------

> Source notes: Google Search Central --- filetype: operator
> documentation, December 2025. Google officially recognises 50+ file
> types. StationX Google Dorks Cheat Sheet 2026 (stationx.net, February
> 2026). CybelAngel 2026 cheat sheet. Cyble threat intelligence: 1.4M+
> exposed .env files indexed since January 2024. GHDB credential
> exposure categories (exploit-db.com/google-hacking-database).

**10.2 URL and Path Structure Parameters**

The inurl: operator restricts results to pages where the specified
string appears anywhere in the URL. This is the most precise operator
for targeting specific directory structures, application paths, and URL
patterns. Combine with filetype: to scope document types within specific
directories. Note: Bing suspended inurl: in 2007 and has never restored
it --- these patterns are Google and Yandex only.

  ------------------------------------------------------------------------------------------------
  **Parameter / Pattern**     **Target        **Example Query**           **Intelligence Yield**
                              Structure**                                 
  --------------------------- --------------- --------------------------- ------------------------
  inurl:/docs                 Documentation   site:target.com inurl:/docs Technical documentation,
                              directories     filetype:pdf                API guides, product
                                                                          manuals published for
                                                                          internal or partner
                                                                          audiences.

  inurl:/reports              Report          site:target.com             Annual reports,
                              directories     inurl:/reports filetype:pdf quarterly updates, audit
                                                                          findings, research
                                                                          outputs.

  inurl:/uploads              File upload     site:target.com             User-uploaded files on
                              directories     inurl:/uploads              CMS platforms. Often
                                              (filetype:pdf OR            contain internal
                                              filetype:docx)              documents uploaded via
                                                                          web forms.

  inurl:/files                Generic file    site:target.com             Miscellaneous file
                              hosting         inurl:/files filetype:xlsx  directories. Common on
                                                                          legacy intranets and
                                                                          SharePoint deployments.

  inurl:/wp-content/uploads   WordPress       site:target.com             All media and document
                              upload          inurl:/wp-content/uploads   uploads for WordPress
                              directory       filetype:pdf                sites. High coverage for
                                                                          SME and media
                                                                          organisation targets.

  inurl:/assets               Asset           site:target.com             Static asset
                              directories     inurl:/assets (ext:pdf OR   directories. Often
                                              ext:docx)                   contain document
                                                                          templates and published
                                                                          PDFs.

  inurl:/download             Download links  site:target.com             Explicitly published
                                              inurl:/download             download targets.
                                              filetype:pdf                High-confidence that
                                                                          these are intentionally
                                                                          hosted but may include
                                                                          inadvertent exposures.

  inurl:admin                 Admin           site:target.com inurl:admin Administrative login
                              interfaces      (intext:login OR            panels. Not document
                                              intitle:login)              access but critical for
                                                                          pentest attack surface
                                                                          enumeration.

  inurl:login                 Login pages     site:target.com inurl:login All login interfaces.
                                              -inurl:blog                 Enumeration of
                                                                          authentication surfaces
                                                                          for pentest scope.

  inurl:backup                Backup          site:target.com             Backup file directories.
                              directories     inurl:backup (ext:sql OR    Highest-priority pentest
                                              ext:bak OR ext:zip)         infrastructure sweep.

  inurl:config                Configuration   site:target.com             Configuration file
                              paths           inurl:config (ext:xml OR    paths. Direct credential
                                              ext:json OR ext:env)        and infrastructure
                                                                          disclosure risk.

  inurl:api                   API endpoints   site:target.com inurl:api   API endpoint discovery.
                                              (ext:json OR                JSON responses and
                                              intext:\"api_key\")         documentation pages
                                                                          reveal endpoint
                                                                          structure.

  inurl:.git                  Exposed Git     site:target.com             Git repository config
                              repositories    inurl:.git/config           files exposed on
                                                                          web-accessible
                                                                          directories. Reveals
                                                                          remote URLs,
                                                                          credentials, and branch
                                                                          structure.

  intitle:\"index of\"        Open directory  site:target.com             Misconfigured web
                              listings        intitle:\"index of\"        servers exposing full
                                              \"parent directory\"        directory trees. Enables
                                                                          file enumeration without
                                                                          filetype guessing.

  intitle:\"index of\" +      Scoped          site:target.com             Directory listings
  filetype                    directory       intitle:\"index of\"        scoped to specific file
                              listings        \"\*.pdf\" OR \"\*.docx\"   types. Surfaces backup
                                                                          archives and bulk
                                                                          document dumps.
  ------------------------------------------------------------------------------------------------

> Source notes: Recosint Google Dorking Guide 2026 (recosint.com,
> January 11, 2026). StationX cheat sheet 2026. GHDB categories:
> sensitive directories, files containing passwords, web server
> detection. WordPress upload path documented by OWASP. inurl: Bing
> suspension --- Microsoft Bing Webmaster documentation, 2007, never
> restored.

**10.3 Content Filter Parameters**

Content filter operators restrict results by text appearing in the page
body (intext:), the HTML title tag (intitle:), or the page anchor text
(inanchor:, now unreliable). These parameters are most powerful when
combined with filetype: and site: to scope both format and content
simultaneously. The allintitle: and allintext: variants require all
specified terms to appear; never combine them with other operators in
the same query.

  --------------------------------------------------------------------------------------------------
  **Parameter**                  **Scope**         **Combination Pattern**   **Notes**
  ------------------------------ ----------------- ------------------------- -----------------------
  intext:\"keyword\"             Page body text    site:target.com           Forces the exact phrase
                                                   filetype:pdf              to appear in document
                                                   intext:\"internal use     body. Double-quotes
                                                   only\"                    enforce exact match ---
                                                                             without quotes, Google
                                                                             may substitute
                                                                             synonyms.

  intext:\"not for public        Confidentiality   site:gov.au filetype:pdf  Standard government
  release\"                      markers           intext:\"not for public   document classification
                                                   release\" -inurl:media    language. High
                                                                             probability these are
                                                                             inadvertent exposures.
                                                                             Strip media directories
                                                                             to reduce noise.

  intext:\"confidential\"        Confidentiality   site:target.com           Common header/footer
                                 markers           filetype:docx             label in corporate
                                                   intext:\"confidential\"   documents. High volume
                                                   -inurl:template           --- filter by
                                                                             additional terms to
                                                                             scope.

  intext:\"password\"            Credential        site:target.com (ext:log  Log files and text
                                 exposure          OR ext:txt)               files containing the
                                                   intext:\"password\"       word password. Combine
                                                                             with filetype scope to
                                                                             reduce false positives.

  intext:\"api_key\" OR          API credential    site:target.com (ext:env  Source code and config
  intext:\"secret_key\"          exposure          OR ext:py OR ext:js)      files containing API
                                                   intext:\"api_key\"        key assignments. High
                                                                             pentest value.

  intext:\"BEGIN RSA PRIVATE     Private key       intext:\"BEGIN RSA        SSH and SSL private key
  KEY\"                          exposure          PRIVATE KEY\"             headers. Any result
                                                   site:target.com           here is a critical
                                                                             finding requiring
                                                                             immediate responsible
                                                                             disclosure.

  intext:\"DB_PASSWORD\" OR      Database          site:target.com ext:env   Environment file
  intext:\"database_password\"   credential        intext:\"DB_PASSWORD\"    variable names for
                                 exposure                                    database credentials.
                                                                             Specific enough to
                                                                             eliminate most false
                                                                             positives.

  intitle:\"keyword\"            HTML page title   site:target.com           Restricts to documents
                                                   filetype:pdf              where the keyword
                                                   intitle:\"board minutes\" appears in the
                                                                             document\'s title or
                                                                             HTML title tag. More
                                                                             precise than intext:
                                                                             for named document
                                                                             types.

  intitle:\"index of\"           Directory listing site:target.com           Apache/Nginx directory
                                 titles            intitle:\"index of\"      listing pages.
                                                   -inurl:htm -inurl:html    Stripping .htm/.html
                                                                             pages removes most blog
                                                                             and CMS pages from
                                                                             results.

  allintitle:term1 term2         Multi-term title  allintitle:annual report  Both terms must appear
                                 match             2025 target company       in title. Do not
                                                                             combine with site: or
                                                                             filetype: ---
                                                                             allintitle: degrades
                                                                             when combined.

  allintext:term1 term2          Multi-term body   allintext:salary payroll  All terms must appear
                                 match             Q4                        in body. Same
                                                                             restriction --- use
                                                                             standalone, not
                                                                             combined.

  inanchor:\"keyword\"           Link anchor text  inanchor:\"download       Unreliable in 2026 ---
                                                   report\" site:target.com  Google returns
                                                                             incomplete data.
                                                                             Document for
                                                                             completeness but do not
                                                                             rely on for production
                                                                             queries.
  --------------------------------------------------------------------------------------------------

> Source notes: Max Intel Google Dorking Reference 2026 (maxintel.org,
> February 9, 2026). allintitle:/allintext: combined operator
> restriction --- Google Search Central documentation. inanchor:
> unreliability noted across multiple 2025--2026 practitioner guides.
> Cyble: 1.4M+ exposed .env files confirming DB_PASSWORD and API_KEY as
> highest-frequency exposed variable names.

**10.4 Scope and Domain Parameters**

The site: operator is the most universally supported and reliable
scoping parameter across all search engines. It accepts full domains,
subdomains, directories, and TLD patterns. The following patterns cover
the full range of site: scope configurations relevant to Atlas research
and penetration testing engagements.

  -------------------------------------------------------------------------------------------------
  **Parameter Pattern**        **Scope**    **Example**                    **Notes**
  ---------------------------- ------------ ------------------------------ ------------------------
  site:example.com             Full domain  site:acmecorp.com filetype:pdf Indexes all pages on the
                                                                           root domain including
                                                                           subdomains in most
                                                                           engines. Most common
                                                                           starting pattern.

  site:subdomain.example.com   Specific     site:intranet.acmecorp.com     Scopes to a single
                               subdomain                                   subdomain. Useful for
                                                                           targeting development,
                                                                           staging, or internal
                                                                           portal subdomains
                                                                           discovered during DNS
                                                                           enumeration.

  site:example.com/path/       Directory    site:acmecorp.com/investors/   Restricts to a specific
                               scope        filetype:pdf                   directory path. Highly
                                                                           precise when directory
                                                                           structure is known.

  site:.gov.au                 TLD pattern  site:.gov.au filetype:pdf      Sweeps all Australian
                                            intext:\"critical              government domains
                                            infrastructure\"               simultaneously. Replace
                                                                           with .gov, .edu, .mil
                                                                           for US equivalents.

  site:.edu.au                 Education    site:.edu.au filetype:pdf      All Australian
                               TLD          intitle:\"thesis\"             universities.
                                            author:\"surname\"             High-density academic
                                                                           document set.

  site:.gov filetype:pdf       US           site:.gov filetype:pdf         All US federal
                               government   \"classified\"                 government domains.
                               sweep        -inurl:reading-room            Strip FOIA reading rooms
                                                                           to isolate inadvertent
                                                                           exposures.

  -site:example.com            Domain       \"target company\"             Finds documents about
                               exclusion    filetype:pdf                   the target organisation
                                            -site:targetcompany.com        hosted on OTHER domains
                                                                           --- third-party reports,
                                                                           competitor analysis,
                                                                           media coverage, leaked
                                                                           documents mirrored
                                                                           elsewhere.

  site:example.com             Subdomain    site:acmecorp.com              Returns only non-www
  -site:www.example.com        isolation    -site:www.acmecorp.com         subdomains. Surfaces
                                                                           development, staging,
                                                                           API, and internal portal
                                                                           subdomains.

  site:pastebin.com OR         Paste and    site:pastebin.com OR           Credential and source
  site:github.com OR           code site    site:github.com \"target.com\" code exposure on paste
  site:gitlab.com              sweep        \"password\"                   and code hosting sites.
                                                                           High-priority pentest
                                                                           sweep.

  site:docs.google.com         Google Docs  site:docs.google.com \"target  Publicly shared Google
                               exposure     company\" \"confidential\"     Docs and Sheets.
                                                                           Frequently contain
                                                                           internal data shared
                                                                           with too-broad
                                                                           permissions.

  site:sharepoint.com          SharePoint   site:sharepoint.com \"target   SharePoint Online sites
                               exposure     company\" filetype:pdf         with public access.
                                                                           Organisations frequently
                                                                           misconfigure SharePoint
                                                                           sharing policies.

  site:scribd.com OR           Document     site:scribd.com \"target       Document sharing
  site:slideshare.net          platforms    company\" filetype:pdf         platforms where internal
                                                                           documents are often
                                                                           uploaded for external
                                                                           distribution and
                                                                           inadvertently remain
                                                                           discoverable.
  -------------------------------------------------------------------------------------------------

> Source notes: StationX Google Dorks Cheat Sheet 2026. DorkFinder blog
> --- site: scoping patterns (dorkfinder.com). Google Search Central ---
> site: operator documentation. Pastebin and GitHub credential exposure
> documented in GHDB categories: passwords in files, sensitive
> information. SharePoint misconfiguration noted in OWASP WSTG v4.2.

**10.5 Date and Temporal Parameters**

Temporal scoping is critical for two distinct OSINT tasks: finding
recently published documents (new exposures, current filings) and
finding historically published documents that may have been deleted from
the live site. The before:/after: operators in Google remain in beta
status as of March 2026 and produce inconsistent results --- Yandex\'s
date: operator is the most reliable structured date filter across all
engines. The Wayback Machine provides the definitive archive access
layer for deleted or modified content.

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Parameter / Mechanism**              **Engine**    **Syntax**                                                                                             **Notes**
  -------------------------------------- ------------- ------------------------------------------------------------------------------------------------------ -------------------------
  after:YYYY-MM-DD                       Google (beta) site:target.com filetype:pdf after:2025-01-01                                                          Returns pages indexed or
                                                                                                                                                              published after the
                                                                                                                                                              specified date. Beta
                                                                                                                                                              status since April 2019
                                                                                                                                                              --- unreliable on precise
                                                                                                                                                              date boundaries. Use
                                                                                                                                                              Google\'s built-in Tools
                                                                                                                                                              \> Custom Date Range as a
                                                                                                                                                              more reliable alternative
                                                                                                                                                              for one-off queries.

  before:YYYY-MM-DD                      Google (beta) site:target.com filetype:xlsx before:2024-12-31                                                        Returns pages published
                                                                                                                                                              before the specified
                                                                                                                                                              date. Combine with after:
                                                                                                                                                              to define a date window.
                                                                                                                                                              Format must be YYYY-MM-DD
                                                                                                                                                              or YYYY --- other formats
                                                                                                                                                              silently ignored.

  after: + before: combined              Google (beta) site:gov.au filetype:pdf after:2025-06-01 before:2025-12-31                                            Date window query. Useful
                                                                                                                                                              for scoping to a specific
                                                                                                                                                              reporting period,
                                                                                                                                                              financial year, or
                                                                                                                                                              incident window.
                                                                                                                                                              Unreliability increases
                                                                                                                                                              with narrow date windows.

  date:YYYYMMDD                          Yandex        site:target.com mime:pdf date:20250101                                                                 Yandex date filter ---
                                                                                                                                                              most reliable temporal
                                                                                                                                                              operator across major
                                                                                                                                                              engines. Format is
                                                                                                                                                              YYYYMMDD (no hyphens).
                                                                                                                                                              Returns pages indexed
                                                                                                                                                              after the specified date.
                                                                                                                                                              Combine with mime:
                                                                                                                                                              (Yandex filetype
                                                                                                                                                              equivalent).

  date:YYYYMMDD..YYYYMMDD                Yandex        site:target.com mime:pdf date:20250101..20251231                                                       Yandex date range using
                                                                                                                                                              double-dot syntax. More
                                                                                                                                                              reliable than Google\'s
                                                                                                                                                              before:/after: for window
                                                                                                                                                              queries.

  Tools \> Custom Date Range             Google (UI)   Any query + Tools \> Any time \> Custom range                                                          Google\'s UI date filter
                                                                                                                                                              is more reliable than the
                                                                                                                                                              before:/after: operators
                                                                                                                                                              for most purposes. Not
                                                                                                                                                              available in
                                                                                                                                                              automated/API contexts
                                                                                                                                                              --- use before:/after:
                                                                                                                                                              for programmatic queries
                                                                                                                                                              despite their
                                                                                                                                                              unreliability.

  web.archive.org/web/YYYYMMDD\*/URL     Wayback       web.archive.org/web/20250101\*/target.com/reports/                                                     Archive.org URL pattern
                                         Machine                                                                                                              for retrieving all
                                                                                                                                                              snapshots of a URL on or
                                                                                                                                                              after a specific date.
                                                                                                                                                              The \* wildcard returns
                                                                                                                                                              all available snapshots.
                                                                                                                                                              Use for recovering
                                                                                                                                                              deleted documents.

  web.archive.org/web/\*/target.com/\*   Wayback       web.archive.org/web/\*/acmecorp.com/financials/\*                                                      Full wildcard site crawl
                                         Machine                                                                                                              history. Returns all
                                                                                                                                                              indexed URLs matching the
                                                                                                                                                              path pattern across all
                                                                                                                                                              time. Essential for
                                                                                                                                                              mapping what a site has
                                                                                                                                                              previously hosted.

  site:web.archive.org target.com        Wayback via   site:web.archive.org acmecorp.com filetype:pdf                                                         Google-indexed Wayback
                                         Google                                                                                                               snapshots. Surfaces
                                                                                                                                                              archived documents that
                                                                                                                                                              have been deindexed from
                                                                                                                                                              the live site but remain
                                                                                                                                                              in Google\'s index via
                                                                                                                                                              their Wayback URLs.

  CDX API --- Wayback Machine            Archive.org   http://web.archive.org/cdx/search/cdx?url=target.com/\*&output=json&fl=original,timestamp,statuscode   Programmatic access to
                                         API                                                                                                                  the Wayback CDX index.
                                                                                                                                                              Returns structured JSON
                                                                                                                                                              of all crawled URLs for a
                                                                                                                                                              domain. The definitive
                                                                                                                                                              mechanism for full
                                                                                                                                                              historical URL
                                                                                                                                                              enumeration. No rate
                                                                                                                                                              limit authentication
                                                                                                                                                              required for public
                                                                                                                                                              queries.
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

> Source notes: Max Intel Google Dorking Reference 2026 (February 9,
> 2026) --- before:/after: beta status confirmed; Yandex date:
> reliability noted. Danny Sullivan confirmed before:/after: have been
> beta since April 2019. Wayback Machine CDX API documentation ---
> archive.org/help/wayback_api.php. cache: removal March 2024 ---
> Wayback Machine is the authoritative replacement.

**10.6 Boolean and Combination Parameters**

Boolean operators control how multiple search terms are combined and
excluded. Mastery of Boolean logic is what separates a precise
intelligence query from a broad, noisy sweep. The following rules and
patterns are specific to search engine boolean behaviour --- which
differs from standard programming boolean logic in important ways.

  -------------------------------------------------------------------------------
  **Parameter**    **Function**     **Correct Usage**       **Common Errors**
  ---------------- ---------------- ----------------------- ---------------------
  \" \" (exact     Forces exact     intitle:\"board         Omitting quotes
  phrase)          phrase match --- minutes\" OR            allows Google to
                   prevents synonym intitle:\"board meeting substitute synonyms
                   substitution and minutes\"               or reorder terms.
                   word reordering                          Always quote
                                                            multi-word phrases in
                                                            OSINT queries.

  OR (uppercase)   Returns results  site:target.com         Lowercase \'or\' is
                   matching either  filetype:pdf            treated as a search
                   term             (intitle:\"strategy\"   keyword, not a
                                    OR intitle:\"roadmap\") boolean operator.
                                                            Must be uppercase.
                                                            Google\'s \| pipe is
                                                            equivalent.

  \- (minus /      Excludes results site:target.com         No space between -
  exclusion)       containing the   filetype:pdf            and the term. Most
                   term             -inurl:press            effective when
                                    -inurl:blog             chaining multiple
                                    -inurl:careers          exclusions to strip
                                                            noise directories.

  \* (wildcard in  Matches any      \"chief \* officer\"    Only works within
  quotes)          single word      site:target.com         quoted phrases on
                   within a quoted  filetype:pdf            Google. Does not
                   phrase                                   function as a
                                                            standalone wildcard
                                                            outside quotes.

  ( ) (grouping)   Groups terms for site:target.com         Without grouping,
                   complex Boolean  (filetype:pdf OR        operator precedence
                   logic            filetype:docx OR        is unpredictable.
                                    filetype:xlsx)          Always group OR terms
                                    (intitle:\"budget\" OR  explicitly.
                                    intitle:\"forecast\")   

  AROUND(N)        Proximity ---    \"database\" AROUND(5)  Unreliable on Google
                   terms within N   \"password\"            in 2026 ---
                   words of each    site:target.com         frequently ignores
                   other                                    proximity constraint.
                                                            Use Bing\'s near:N
                                                            for proximity queries
                                                            where precision
                                                            matters.

  near:N (Bing     Proximity ---    \"API key\" near:3      Bing\'s
  only)            terms within N   \"secret\"              implementation is
                   words            site:target.com         more reliable than
                                                            Google\'s AROUND. No
                                                            Google equivalent
                                                            with reliable
                                                            behaviour.

  \+ (obsolete)    Formerly forced  Do not use              Deprecated 2011. Now
                   exact word match                         treated as a regular
                                                            character.
                                                            Double-quotes provide
                                                            the same function
                                                            more reliably.

  .. (numeric      Numeric range    site:target.com         Works more reliably
  range)           between two      filetype:pdf            with currency (\$)
                   values           \"revenue\"             than plain numbers.
                                    \$50M..\$500M           Useful for financial
                                                            document scoping by
                                                            scale.

  Chained          Strip multiple   site:target.com         The standard
  exclusions       noise paths in   filetype:pdf            noise-reduction
  pattern          one query        -inurl:press            pattern for corporate
                                    -inurl:news -inurl:blog site sweeps. Apply
                                    -inurl:legal            before reviewing
                                    -inurl:careers          results rather than
                                    -inurl:privacy          after. Sequence does
                                                            not affect results.

  Multi-filetype   Sweep all        site:target.com         The standard document
  OR pattern       document types   (filetype:pdf OR        sweep opener. Run
                   simultaneously   filetype:docx OR        this first, then
                                    filetype:xlsx OR        scope by content
                                    filetype:pptx OR        filters.
                                    filetype:csv)           

  Multi-engine     Same query       Google: site:t.com      Always run high-yield
  replication      adapted across   intext:\"pw\"           Google queries
                   engines          filetype:env --- Bing:  adapted for Bing
                                    site:t.com              (inbody: replaces
                                    inbody:\"pw\"           intext:; no inurl:)
                                    filetype:env ---        and Yandex (mime:
                                    Yandex: site:t.com      replaces filetype:;
                                    mime:env \"pw\"         title: replaces
                                                            intitle:; \~\~
                                                            replaces -). Bing
                                                            indexes content
                                                            Google has deindexed.
  -------------------------------------------------------------------------------

> Source notes: Google Search Central --- operator syntax rules
> (December 2025). Max Intel 2026: 32-keyword limit and 2048-character
> limit per keyword. allintitle:/allinurl: must not be combined ---
> Google Search Central. AROUND(X) unreliability documented in multiple
> practitioner sources 2025--2026. Bing near:N reliability --- Microsoft
> Bing Webmaster documentation.

**10.7 Specialised Discovery Parameters**

Beyond the core operator set, the following parameters and mechanisms
address specific document access objectives relevant to Atlas research
and penetration testing pre-engagement reconnaissance. These are
lower-frequency but high-yield for their specific applications.

  ----------------------------------------------------------------------------------------------------------------------
  **Parameter /       **Engine /   **Application**                     **Query Example**
  Mechanism**         Tool**                                           
  ------------------- ------------ ----------------------------------- -------------------------------------------------
  source: (Google     Google News  Restricts Google News results to a  site:reuters.com source:reuters \"target
  News)                            specific publication. Use for       company\" after:2025-01-01
                                   monitoring how specific outlets     
                                   have covered a target. Does not     
                                   apply outside Google News.          

  imagesize: and src: Google       imagesize: finds pages with images  imagesize:1920x1080 site:target.com --- finds HD
                      Images       of specific pixel dimensions. src:  screenshot-style images
                                   finds pages referencing a specific  
                                   image URL. Used in image-based      
                                   OSINT workflows.                    

  Publicwww.com       Publicwww    Searches the actual source code of  publicwww.com/websites/\"target_api_key_value\"
  source code search               indexed pages for specific strings. 
                                   Finds API keys, JavaScript tracking 
                                   codes, and technology fingerprints  
                                   in page source without crawling.    

  SearchCode.com code SearchCode   Searches source code in public      searchcode.com/?q=target.com+api_key
  search                           repositories (GitHub, GitLab,       
                                   Bitbucket, Google Code). Covers     
                                   20B+ lines of code. More            
                                   comprehensive than GitHub search    
                                   for cross-platform code discovery.  

  FOFA.info (Chinese) FOFA         Chinese internet asset search       fofa.info/result?qbase64=\[base64 of query\]
                                   engine similar to Shodan and        
                                   Censys. Covers Chinese-hosted       
                                   infrastructure extensively.         
                                   Operator: domain=\"target.com\" --- 
                                   returns all indexed assets.         

  ZoomEye             ZoomEye      Chinese Shodan equivalent.          zoomeye.org/searchResult?q=site:target.com
                                   app=\"Apache\" country=\"AU\" ---   
                                   find Apache servers in Australia.   
                                   Strong coverage of Asian-Pacific    
                                   infrastructure.                     

  GreyNoise Tags API  GreyNoise    Classifies IP addresses as benign   viz.greynoise.io/ip/\[IP\] --- per-IP
                                   background scanners or targeted     intelligence
                                   attackers. API parameter:           
                                   tags=\[\'mirai\'\] returns IPs      
                                   associated with specific threat     
                                   actor tools.                        

  Certificate         crt.sh / SSL Searches Certificate Transparency   crt.sh/?q=%.target.com --- wildcard subdomain
  Transparency        Labs         logs for all SSL/TLS certificates   enumeration via CT logs
  (crt.sh)                         issued to a domain. Returns         
                                   subdomain names revealed in         
                                   certificate Subject Alternative     
                                   Names --- bypasses DNS enumeration. 

  DuckDuckGo !bang    DuckDuckGo   DuckDuckGo\'s 13,000+ !bang         !scholar \"Hamiltonian decomposition\"
  operators                        operators redirect queries directly site:arxiv.org
                                   to specific sites\' own search.     
                                   !pdf, !scholar, !wa (Wolfram        
                                   Alpha), !archive (Wayback), !gi     
                                   (Google Images).                    

  Google Verbatim     Google (UI)  Disables all synonym substitution,  Any query via Tools \> Verbatim for literal-only
  mode                             spelling correction, and            matching
                                   personalisation. Equivalent to      
                                   wrapping every term in quotes.      
                                   Access via Tools \> All results \>  
                                   Verbatim. Not available in API.     

  Perplexity AI       Perplexity   First AI search engine to support   Find PDFs from target.com published after 2025
  operator support    AI           structured operators. site:,        about quarterly earnings site:target.com
                                   filetype:, before:, after: can be   filetype:pdf after:2025-01-01
                                   embedded in natural language        
                                   prompts. Useful for complex         
                                   document retrieval queries that     
                                   combine operator logic with         
                                   semantic context.                   

  inurl:.git/config   Google /     Finds exposed Git repository config inurl:.git/config site:target.com ---
  credential sweep    Yandex       files containing remote URLs, which high-priority pentest finding
                                   may include credentials embedded in 
                                   HTTPS remote URLs                   
                                   (https://user:password@repo.git).   
  ----------------------------------------------------------------------------------------------------------------------

> Source notes: Publicwww.com --- indexed source code search, 2026.
> SearchCode.com --- 20B+ lines of code across repositories. FOFA and
> ZoomEye --- Chinese infrastructure search engines; relevant to Pillar
> 3 threat landscape. crt.sh --- Certificate Transparency log search
> (crt.sh). DuckDuckGo !bang documentation --- help.duckduckgo.com.
> Perplexity AI operator support --- first AI engine to support
> structured operators, noted in Max Intel 2026.

**10.8 Complete Compound Query Templates**

The following are complete, production-ready query templates combining
multiple parameters. These represent the standard Atlas document
retrieval patterns for each major intelligence objective. Adapt
target.com to the specific domain for each engagement. All templates are
passive queries against publicly indexed content.

  -------------------------------------------------------------------------------
  **Template     **Complete Query**                          **Purpose**
  Name**                                                     
  -------------- ------------------------------------------- --------------------
  Full document  site:target.com (filetype:pdf OR            Opening sweep for
  sweep          filetype:docx OR filetype:xlsx OR           all high-value
                 filetype:pptx OR filetype:csv) -inurl:press document formats on
                 -inurl:blog -inurl:news -inurl:careers      a target domain with
                 -inurl:legal                                standard noise
                                                             reduction applied.

  Credential     site:target.com (ext:env OR ext:log OR      Full credential and
  exposure sweep ext:sql OR ext:bak OR ext:config OR         config file exposure
                 ext:xml) OR (site:target.com filetype:txt   sweep. Run on Google
                 intext:\"password\")                        then replicate on
                                                             Bing.

  Executive and  site:target.com filetype:pdf                Board and governance
  governance     (intitle:\"board\" OR intitle:\"committee\" document sweep
                 OR intitle:\"minutes\" OR intitle:\"AGM\"   scoped to last two
                 OR intitle:\"annual general\")              years.
                 after:2024-01-01                            

  Financial      site:target.com (filetype:xlsx OR           Financial document
  intelligence   filetype:pdf) (intitle:\"budget\" OR        sweep stripping
                 intitle:\"forecast\" OR intitle:\"P&L\" OR  press release
                 intext:\"EBITDA\" OR intext:\"revenue\")    directories.
                 -inurl:press                                

  Personnel and  site:target.com filetype:pdf                Personnel
  org structure  (intitle:\"directory\" OR                   intelligence sweep.
                 intitle:\"organisation\" OR intitle:\"org   Combine with
                 chart\" OR intext:\"staff list\" OR         person-specific
                 intext:\"team members\")                    queries below.

  Specific       \"First Last\" (filetype:pdf OR             All publicly indexed
  person sweep   filetype:docx OR filetype:pptx OR           documents associated
                 filetype:xlsx) -site:linkedin.com           with a named
                 -site:facebook.com                          individual. Strip
                                                             social platforms to
                                                             focus on document
                                                             files.

  Australian     site:.gov.au filetype:pdf (intext:\"request Government
  government     for tender\" OR intext:\"request for        procurement
  tender         proposal\" OR intext:\"procurement\")       documents naming a
                 \"target organisation\"                     specific supplier or
                                                             contractor.

  Open directory site:target.com intitle:\"index of\"        Misconfigured
  sweep          (\"parent directory\" OR \".pdf\" OR        directory listing
                 \".docx\" OR \".xlsx\") -inurl:htm          discovery with
                 -inurl:html                                 document type
                                                             scoping.

  Cross-engine   site:target.com filetype:env OR             Bing-specific
  credential     site:target.com inbody:\"DB_PASSWORD\" OR   credential sweep.
  sweep (Bing)   site:target.com inbody:\"api_key\"          Run separately ---
                                                             Bing\'s inbody:
                                                             replaces Google\'s
                                                             intext:, inurl: not
                                                             supported.

  Paste site     (site:pastebin.com OR site:pastie.org OR    Credential and API
  credential     site:hastebin.com) \"target.com\"           key exposure on
  sweep          (\"password\" OR \"api_key\" OR \"secret\"  paste sites.
                 OR \"token\")                               High-frequency
                                                             finding in pentest
                                                             pre-engagement.

  Code           (site:github.com OR site:gitlab.com)        Source code
  repository     \"target.com\" (\"api_key\" OR              repositories
  secret sweep   \"secret_key\" OR \"password\" OR           containing hardcoded
                 \"access_token\") language:python OR        credentials
                 language:javascript                         referencing the
                                                             target domain.

  Subdomain      site:target.com -site:www.target.com        Documents hosted on
  document       filetype:pdf                                non-www subdomains
  discovery                                                  only. Surfaces
                                                             content on dev,
                                                             staging, api,
                                                             intranet, and
                                                             partner portal
                                                             subdomains.

  Wayback        site:web.archive.org/web/\*/target.com/\*   Google-indexed
  historical     filetype:pdf                                Wayback Machine
  sweep                                                      snapshots of target
                                                             domain PDFs.
                                                             Recovers documents
                                                             removed from the
                                                             live site.

  Mining /       site:.gov.au OR site:asic.gov.au            Australian mining
  regulatory AU  filetype:pdf \"company name\"               exploration
                 (intext:\"tenement\" OR                     regulatory documents
                 intext:\"exploration licence\" OR           naming a specific
                 intext:\"mining lease\") after:2023-01-01   company. Covers
                                                             state and federal
                                                             portals.
  -------------------------------------------------------------------------------

> Source notes: Templates derived from: GHDB categories
> (exploit-db.com/google-hacking-database); Seek Your Data layered
> methodology guide 2026; Recosint Guide 2026; StationX cheat sheet
> 2026; CybelAngel 2026; DorkFinder blog 2026. Australian government
> tender and mining templates derived from Atlas Pillar 1 geoscience
> repository protocol and GSQ/NSW MinView access patterns.

**Document Information**

Prepared by: Atlas Strategic Consultants --- Gary Stewart, Lead
Consultant

Date: March 2026 \| Status: Active --- Version 1.2 \| Classification:
Internal Use Only

Next Review: April 2026 (post-ATT&CK v19 release) \| Classification:
Internal Use Only

Key events since v1.1: Section 10 --- Web Document Access Full Parameter
Reference added (v1.2): complete filetype/ext parameter table (22
formats), URL/path structure patterns, content filter parameters,
scope/domain patterns, date/temporal parameters including Wayback CDX
API, Boolean combination reference, specialised discovery mechanisms
(Publicwww, SearchCode, FOFA, ZoomEye, crt.sh, Perplexity AI operators),
and 14 production-ready compound query templates.
