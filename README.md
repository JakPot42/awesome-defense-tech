# Awesome Defense Tech [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Curated resources for building national security and defense-adjacent software: public APIs, open standards, policy documents, and worked examples.

Defense-tech software draws on an unusually scattered set of data sources and frameworks — spread across government portals, academic preprint servers, treaty documents, and obscure federal registries. This list collects them in one place.

Everything here is **free or free-tier accessible**. Nothing requires security clearance. Every API can be called from a laptop. The worked examples at the bottom show these resources assembled into real tools.

---

## Contents

- [Public APIs and Data Sources](#public-apis-and-data-sources)
  - [Cybersecurity and Vulnerability Intelligence](#cybersecurity-and-vulnerability-intelligence)
  - [Space and Orbital Mechanics](#space-and-orbital-mechanics)
  - [Energy and Grid Infrastructure](#energy-and-grid-infrastructure)
  - [Water and Environmental](#water-and-environmental)
  - [Biodefense and Public Health](#biodefense-and-public-health)
  - [Geospatial and Remote Sensing](#geospatial-and-remote-sensing)
  - [Materials Science and Chemistry](#materials-science-and-chemistry)
  - [Government Procurement and Spending](#government-procurement-and-spending)
  - [Policy, Regulatory, and Legal](#policy-regulatory-and-legal)
  - [Intelligence and Open Source](#intelligence-and-open-source)
  - [Financial, Corporate, and Trade](#financial-corporate-and-trade)
  - [Patents, Research, and Innovation](#patents-research-and-innovation)
  - [Critical Infrastructure](#critical-infrastructure)
- [Open Standards and Frameworks](#open-standards-and-frameworks)
  - [Cybersecurity and Threat Intelligence](#cybersecurity-and-threat-intelligence)
  - [AI and Autonomous Systems](#ai-and-autonomous-systems)
  - [Intelligence Community Standards](#intelligence-community-standards)
  - [Defense Acquisition and Compliance](#defense-acquisition-and-compliance)
  - [Critical Infrastructure Protection](#critical-infrastructure-protection)
  - [Formal Methods and Verification](#formal-methods-and-verification)
  - [Privacy and Cryptography](#privacy-and-cryptography)
- [Regulatory and Policy Documents](#regulatory-and-policy-documents)
  - [Foreign Investment and Trade Controls](#foreign-investment-and-trade-controls)
  - [Personnel Security and Clearances](#personnel-security-and-clearances)
  - [Defense Acquisition Regulations](#defense-acquisition-regulations)
  - [Cybersecurity Policy](#cybersecurity-policy)
  - [AI and Emerging Technology Policy](#ai-and-emerging-technology-policy)
- [Worked Examples](#worked-examples)
  - [Threat Intelligence and Influence Operations](#threat-intelligence-and-influence-operations)
  - [Cybersecurity and Vulnerability Management](#cybersecurity-and-vulnerability-management)
  - [Defense Acquisition and Contracting](#defense-acquisition-and-contracting)
  - [OSINT and Strategic Intelligence](#osint-and-strategic-intelligence)
  - [Space and Orbital Security](#space-and-orbital-security)
  - [Critical Infrastructure and Energy Security](#critical-infrastructure-and-energy-security)
  - [Biodefense and Health Security](#biodefense-and-health-security)
  - [AI Safety Ethics and Compliance](#ai-safety-ethics-and-compliance)
  - [Formal Verification and Zero Trust](#formal-verification-and-zero-trust)
  - [Supply Chain and Foreign Investment Risk](#supply-chain-and-foreign-investment-risk)
  - [Policy and Regulatory Analytics](#policy-and-regulatory-analytics)
  - [Materials Science and Emerging Technology](#materials-science-and-emerging-technology)
- [Contributing](#contributing)

---

## Public APIs and Data Sources

### Cybersecurity and Vulnerability Intelligence

- [CISA Known Exploited Vulnerabilities (KEV)](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) — CISA's authoritative catalog of CVEs actively exploited in the wild. JSON feed, no key. Binding Operational Directive 22-01 requires federal agencies to patch KEV entries on a mandatory timeline — this is the canonical "which CVEs actually matter" list.
- [EPSS (Exploit Prediction Scoring System)](https://www.first.org/epss/) — FIRST.org model that scores each CVE by probability of exploitation in the next 30 days. REST API, no key. Pair with KEV for genuine triage: high-EPSS + not-yet-KEV entries are your early warning.
- [NVD CVE API](https://nvd.nist.gov/developers/vulnerabilities) — NIST National Vulnerability Database. Full CVE metadata, CVSS v3 scores, CWE mappings, CPE affected products. Free key (email registration). The authoritative source that KEV and EPSS both reference.
- [CISA ICS-CERT Advisories](https://www.cisa.gov/ics-advisories) — Advisories for industrial control system vulnerabilities (ICSA-* format). JSON/RSS, no key. Separate from KEV — covers Purdue Model Layer 0–3 OT/ICS products that NVD often lacks.
- [Shodan Internet-of-Things API](https://developer.shodan.io/) — Internet-facing device discovery. Free tier; full API is paid. Useful for enumerating exposed industrial protocols (Modbus, DNP3, BACnet) in critical infrastructure research.
- [MITRE ATT&CK STIX](https://attack.mitre.org/resources/attack-data-and-tools/) — Structured JSON/STIX2 export of the entire ATT&CK knowledge base (Enterprise, ICS, Mobile). No key. The standard vocabulary for describing adversary TTPs programmatically.
- [VirusTotal API](https://developers.virustotal.com/) — Multi-engine malware scanning and file/URL/IP reputation. Free tier (4 lookups/min). Useful for IOC enrichment in OSINT and threat intelligence pipelines.

### Space and Orbital Mechanics

- [Space-Track.org](https://www.space-track.org/) — US Space Force 18th Space Defense Squadron's authoritative catalog of all tracked Earth-orbiting objects (TLEs, orbital elements, maneuver histories). Free account required. This is the ground truth for satellite tracking — all other tracking sites derive from it.
- [CelesTrak](https://celestrak.org/SOCRATES/) — Dr. T.S. Kelso's cleaned and redistributed TLE feeds plus conjunction data. No key for most feeds. More developer-friendly than Space-Track for quick prototyping.
- [NASA Horizons System](https://ssd.jpl.nasa.gov/horizons/) — JPL ephemeris server for solar system bodies, spacecraft, and asteroids. REST API, no key. Generates precise position/velocity vectors for any body over any time range.
- [NASA Small-Body Database (SBDB)](https://ssd.jpl.nasa.gov/sbdb.cgi) — Complete catalog of asteroids and comets with orbital elements, close-approach data, and physical parameters. REST API, no key. The NHATS endpoint identifies NEOs potentially accessible by human spaceflight.
- [NASA Astronomy Picture of the Day (APOD)](https://api.nasa.gov/) — The NASA open APIs portal also covers DONKI (space weather), Earth imagery, Mars rover photos, and more. Free key registration at api.nasa.gov.
- [ESA Space Debris API](https://discosweb.esoc.esa.int/) — ESA's Database and Information System Characterizing Objects in Space. Track resident space objects, fragmentation events, and conjunction assessments.

### Energy and Grid Infrastructure

- [EIA API v2](https://www.eia.gov/opendata/) — US Energy Information Administration. Electricity demand and generation by fuel type, region, and hour. Pipeline flows. Petroleum storage. Free key. The `electricity/rto/region-data/data/` endpoint gives real-time regional demand and generation mix — essential for grid stress modeling.
- [PJM Data Miner](https://dataminer2.pjm.com/) — PJM Interconnection's data platform for the largest US grid region (13 states). Load forecasts, actual generation, ancillary service prices. No key for public feeds.
- [CAISO OASIS](http://oasis.caiso.com/) — California ISO real-time market data: LMPs, generation, demand, curtailment. XML/JSON, no key. Useful for modeling renewable intermittency and demand response.
- [NOAA API](https://www.ncdc.noaa.gov/cdo-web/webservices/v2) — Hourly weather observations, climate norms, extreme event data. Free key. Temperature forecasts drive electricity demand; precipitation drives hydroelectric generation — both feed grid stress models.
- [NREL PVWatts API](https://developer.nrel.gov/docs/solar/pvwatts/) — National Renewable Energy Lab solar generation estimates by location. Free key. Useful for estimating solar contribution to grid mix.

### Water and Environmental

- [USGS Water Services API](https://waterservices.usgs.gov/) — Real-time and historical streamflow, groundwater levels, water quality data for thousands of USGS gauges across the US. No key. The `instantaneous values` endpoint returns current streamflow percentile relative to historical norms — the key metric for water stress modeling.
- [US Drought Monitor (USDM)](https://droughtmonitor.unl.edu/DmData/DataDownload.aspx) — Weekly drought severity (D0–D4) by county, state, or watershed. JSON/CSV, no key. Maintained jointly by NOAA, USDA, and the National Drought Mitigation Center. CISA designates water systems as critical infrastructure (NCF-39/40).
- [EPA Water Quality Portal](https://www.waterqualitydata.us/) — Harmonized water quality data from USGS, EPA, and state agencies. REST, no key. Covers chemical, physical, and biological parameters.
- [USDA Cropland Data Layer](https://nassgeodata.gmu.edu/CropScape/) — Satellite-derived crop type maps for the entire US at 30m resolution. REST API. Useful for combining with water stress data for agricultural security modeling.

### Biodefense and Public Health

- [WHO Disease Outbreak News (DON)](https://www.who.int/emergencies/disease-outbreak-news) — WHO's primary channel for novel pathogen events, unusual clusters, and formal outbreak declarations. JSON feed, no key. The canonical early-warning data source for biosurveillance.
- [CDC Open Data](https://data.cdc.gov/) — Socrata API access to CDC surveillance datasets: mortality, hospitalization, immunization coverage, foodborne illness. Free key for higher rate limits.
- [ProMED Mail](https://promedmail.org/) — Program for Monitoring Emerging Diseases. RSS/API access to epidemiologist-moderated outbreak reports dating to 1994. Historically predates WHO DON alerts.
- [NCBI Entrez APIs](https://www.ncbi.nlm.nih.gov/home/develop/api/) — PubMed, GenBank, SRA, and other NCBI databases. Free key. Essential for linking pathogen sequences to published literature in biosurveillance pipelines.
- [Synthea](https://github.com/synthetichealth/synthea) — Open-source synthetic patient record generator. FHIR-compliant output. Useful for testing biosurveillance and clinical decision-support tools without real patient data.

### Geospatial and Remote Sensing

- [Copernicus Open Access Hub](https://scihub.copernicus.eu/) — EU free satellite imagery: Sentinel-1 (SAR), Sentinel-2 (multispectral), Sentinel-5P (atmospheric). Free account. Sentinel-2 Level-2A provides 10m surface reflectance — enough to detect crop stress, deforestation, or infrastructure changes.
- [GDELT Project](https://www.gdeltproject.org/) — Global event database derived from global news, updated every 15 minutes. BigQuery public dataset, CSV downloads, no key. CAMEO event codes allow filtering for conflict events, protests, or diplomatic contacts by country/actor/date.
- [Maxar SecureWatch](https://www.maxar.com/products/securewatch) — Commercial high-resolution satellite imagery. Paid. Mentioned here because it is the primary commercial imagery source for defense and intelligence applications.
- [Planet Labs API](https://developers.planet.com/) — Daily global satellite imagery at 3–5m resolution. Paid; free education tier. Useful for change detection at specific coordinates.
- [OpenStreetMap Overpass API](https://overpass-api.de/) — Query the full OSM database by geometry, tag, or relation. No key. Useful for extracting infrastructure features (pipelines, substations, ports) for modeling.

### Materials Science and Chemistry

- [Computation-Ready Experimental (CoRE) MOF Database](https://github.com/gregchung/gregchung.github.io/tree/master/CoRE-MOFs) — 8,636 experimentally synthesized Metal-Organic Frameworks with precomputed geometric properties. CSV/JSON, no key. MOFs are of defense interest for chemical agent capture, gas storage, and filtration.
- [Materials Project API](https://materialsproject.org/api) — DFT-computed properties for ~150,000 inorganic materials. Free key. Crystal structures, band gaps, elastic constants — foundational for materials screening.
- [PubChem REST API](https://pubchemdocs.ncbi.nlm.nih.gov/pug-rest) — Chemical structure, property, and bioactivity data for ~115 million compounds. No key. Essential for CBRN agent lookup, chemical similarity search, and toxicity screening.
- [RCSB Protein Data Bank](https://www.rcsb.org/docs/programmatic-access/web-services-overview) — 200,000+ experimentally determined protein structures. REST, no key. Relevant for biodefense: pathogen receptor structures, antibody engineering, vaccine target identification.

### Government Procurement and Spending

- [SAM.gov API](https://open.gsa.gov/api/sam/) — System for Award Management. Active solicitations, contract opportunities, entity registrations, exclusions (debarred parties), CAGE codes. Free key. The primary federal acquisition portal — integrates with FPDS for award history.
- [USASpending.gov API](https://api.usaspending.gov/) — Federal contract and grant award data aggregated by agency, program, recipient, and fiscal year. No key. The `spending_over_time` endpoint lets you track DoD investment in any keyword-matched technology area year by year.
- [FPDS-NG API](https://www.fpds.gov/fpdsng_cms/index.php/en/worksite.html) — Federal Procurement Data System. Individual contract actions with full metadata: contractor, place of performance, product/service code (PSC), NAICS, obligated amount. Feeds USASpending.
- [SBIR.gov API](https://www.sbir.gov/api) — Small Business Innovation Research and STTR award database. Searches SBIR/STTR contracts by agency, technology, phase, and year. Useful for tracking emerging technology investment patterns.
- [congress.gov API](https://api.congress.gov/) — Bill text, summaries, committee actions, member votes, and amendments. Free key (registration). Essential for tracking NDAA (National Defense Authorization Act) provisions — the annual legislation that shapes DoD funding and policy.

### Policy, Regulatory, and Legal

- [Federal Register API](https://www.federalregister.gov/developers/api/v1) — Full text of every proposed and final rule published in the Federal Register, plus executive orders and presidential documents. No key. The `documents` endpoint lets you search by agency, date, CFR part, or keyword.
- [Regulations.gov API](https://open.gsa.gov/api/regulationsgov/) — Public comments on proposed rules. Free key. The `comments` endpoint retrieves all public submissions for a given docket — essential for tracking industry and public response to defense-relevant rules (CMMC, ITAR, BIS export controls).
- [CourtListener API](https://www.courtlistener.com/api/) — Federal and state court opinions, dockets, and oral arguments. Free key. PACER alternative for citation analysis, litigation network mapping, and precedent tracking.
- [Oyez API](https://api.oyez.org/) — Supreme Court case transcripts, oral argument audio, and opinion text. No key. Structured JSON makes it programmatically useful for SCOTUS-specific analytics.
- [OFAC SDN API](https://sanctionssearch.ofac.treas.gov/Details.aspx?id=22683) — Office of Foreign Assets Control sanctions lists (SDN, Consolidated). XML/CSV, no key. Any contractor, supplier, or investment target should be checked against this list.
- [SEC EDGAR Full-Text Search](https://efts.sec.gov/LATEST/search-index?q=%22beneficial+ownership%22&dateRange=custom&startdt=2024-01-01&enddt=2024-12-31&forms=10-K) — Full-text search across all SEC filings. No key. The `company_search` and `submissions` endpoints let you pull beneficial ownership disclosures, CFIUS-relevant foreign investment disclosures, and technology licensing terms from 10-Ks.

### Intelligence and Open Source

- [GDELT Project](https://www.gdeltproject.org/) — See [Geospatial and Remote Sensing](#geospatial-and-remote-sensing). Also useful for: tracking state-media narratives, mapping influence campaigns, detecting protest/conflict escalation.
- [Internet Archive API](https://archive.org/developers/) — Wayback Machine and digital library. No key. Useful for recovering deleted propaganda content, archiving web evidence, and historical baseline comparisons.
- [Recorded Future Free Feeds](https://www.recordedfuture.com/threat-intelligence-feeds) — Free OSINT indicators of compromise (IOCs) in STIX format. Limited scope vs. paid tier, but useful for baseline threat enrichment.
- [AbuseIPDB API](https://www.abuseipdb.com/api.html) — Community-reported malicious IPs. Free key (1,000 lookups/day). Useful for rapid IOC screening in network log analysis.

### Financial, Corporate, and Trade

- [SEC EDGAR API](https://data.sec.gov/api/xbrl/companyfacts/) — Structured financial data for all public US companies. No key. The `company_facts` endpoint returns XBRL-tagged financials — revenue, debt, R&D spend — back to ~2009 for any filer.
- [Census Bureau Trade API](https://www.census.gov/data/developers/data-sets/international-trade.html) — US import/export data by commodity (HTS code), country, and month. Free key. Useful for supply chain dependency analysis and tracking export-controlled commodity flows.
- [BIS Export Enforcement Actions](https://efts.commerce.gov/complete?q=&dateRange=custom&startDate=2020-01-01&endDate=2024-12-31&sources=EARActions) — Bureau of Industry and Security enforcement actions (denial orders, civil penalties). Useful for building an export-controls compliance screening dataset.
- [USPTO PatentsView API](https://patentsview.org/apis/api-endpoints/patents) — US patent metadata: inventors, assignees, CPC/USPC classification, citations, geographic data. No key. Useful for mapping emerging technology development by company, country, or research institution.
- [OpenCorporates API](https://api.opencorporates.com/) — Corporate registration data for 200+ jurisdictions. Free tier. Useful for beneficial ownership tracing and foreign corporate structure analysis.
- [OpenSanctions API](https://www.opensanctions.org/api/) — Aggregated sanctions, PEP (Politically Exposed Persons), and adverse media data from 100+ sources. Free for non-commercial use. Covers OFAC, EU, UN, OFSI, and more in one normalized feed.

### Patents, Research, and Innovation

- [arXiv API](https://arxiv.org/help/api/) — 2M+ preprints in physics, math, CS, and engineering. No key. The `search_query` endpoint lets you track emerging research by subject, institution, or keyword — useful for monitoring dual-use technology development.
- [USPTO PatentsView API](https://patentsview.org/apis/api-endpoints/patents) — See [Financial, Corporate, and Trade](#financial-corporate-and-trade).
- [CrossRef API](https://api.crossref.org/) — 150M+ scholarly metadata records. No key. Useful for citation network analysis, tracking technology transfer between academia and industry.
- [Semantic Scholar API](https://api.semanticscholar.org/) — 200M+ academic papers with citation graphs and AI-generated paper summaries. Free key. More developer-friendly than CrossRef for influence network analysis.
- [Google Patents Public Data](https://console.cloud.google.com/marketplace/product/google_patents_public_data) — BigQuery public dataset with 100M+ patent documents from 17 patent offices. Free query tier.

### Critical Infrastructure

- [TeleGeography Submarine Cable Map](https://www.submarinecablemap.com/) — Interactive and downloadable data on all commercial submarine cable systems: landing stations, capacity, owners, build year. Free data download. The 400+ cables in this dataset carry ~97% of international internet traffic.
- [HIFLD Critical Infrastructure Data](https://hifld-geoplatform.opendata.arcgis.com/) — Homeland Infrastructure Foundation-Level Data. Geospatial datasets for power plants, substations, pipelines, ports, hospitals, and more. Public layers are free; some layers require account.
- [EIA-860 Power Plant Database](https://www.eia.gov/electricity/data/eia860/) — Annual survey of all US electricity generating facilities: capacity, technology type, fuel, ownership, interconnection. CSV, no key. The authoritative source for US generation asset data.
- [PHMSA Pipeline Safety Data](https://www.phmsa.dot.gov/data-and-statistics/pipeline/distribution-transmission-gathering-lng-and-liquid-pipeline-annual-data) — Pipeline and Hazardous Materials Safety Administration incident reports, inspection data, and operator filings. Useful for pipeline vulnerability modeling.

---

## Open Standards and Frameworks

### Cybersecurity and Threat Intelligence

- [MITRE ATT&CK](https://attack.mitre.org/) — Adversary tactics, techniques, and procedures (TTPs) organized by attack lifecycle phase. Three matrices: Enterprise (Windows/Linux/Cloud), ICS (industrial control systems), and Mobile. The standard vocabulary for threat intelligence products and red team reporting.
- [MITRE ATT&CK for ICS](https://attack.mitre.org/matrices/ics/) — Dedicated OT/ICS coverage across the Purdue Model. Technique IDs prefixed with `T0` (e.g., T0886 Remote Services). Aligns with CISA ICS-CERT advisories.
- [DISARM Framework](https://www.disarm.foundation/) — Disinformation Analysis and Risk Management framework. Modeled on ATT&CK but for influence operations: tactics (Plan Strategy, Create Assets, Publish Content), techniques (Fabricate Quotes, Use Coordinated Inauthentic Accounts), and countermeasures. Maintained by DISARM Foundation.
- [STIX 2.1 / TAXII 2.1](https://oasis-open.github.io/cti-documentation/) — Structured Threat Information Expression (STIX) is the standard format for cyber threat intelligence objects. TAXII is the transport protocol for sharing them. Most commercial and government CTI platforms ingest and emit STIX.
- [CVSS v3.1](https://www.first.org/cvss/specification-document) — Common Vulnerability Scoring System. Base, Temporal, and Environmental scores. Base score is deterministic from attack vector, complexity, privileges required, user interaction, and impact dimensions. Required by DoD and federal agencies for vulnerability severity reporting.
- [CWE (Common Weakness Enumeration)](https://cwe.mitre.org/) — MITRE's catalog of software and hardware security weaknesses. Distinct from CVE (specific vulnerabilities) — CWE classifies the class of flaw. Used in SAST tools and secure code review.
- [C2PA (Coalition for Content Provenance and Authenticity)](https://c2pa.org/) — Open standard for cryptographically signing and verifying the origin and edit history of digital content. Relevant for detecting AI-generated media in influence operations.

### AI and Autonomous Systems

- [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/system/files/documents/2023/01/26/AI%20RMF%201.0.pdf) — NIST's framework for managing AI risk across the AI lifecycle. Four core functions: Govern, Map, Measure, Manage. Increasingly cited in DoD AI program documentation and Congressional oversight.
- [DoD AI Ethical Principles](https://www.ai.mil/docs/Ethical_Principles_for_Artificial_Intelligence.pdf) — The five principles DoD adopted in 2020: Responsible, Equitable, Traceable, Reliable, Governable. Operationalized in the DoD Responsible AI Strategy and Implementation Pathway (RAISE 2.0).
- [DoD Responsible AI Strategy and Implementation Pathway (RAISE 2.0)](https://www.ai.mil/docs/RAI_Strategy_Implementation_Pathway.pdf) — Operationalizes the AI Ethical Principles with implementation milestones, responsible AI champions, and lifecycle checkpoints for AI-enabled systems.
- [NATO Principles of Responsible Use of AI in Defence](https://www.nato.int/cps/en/natohq/official_texts_187617.htm) — Six principles adopted by NATO allies in 2021. Includes lawfulness, responsibility, explicability, accuracy, reliability, and governability. NATO's version of the DoD ethical AI principles.
- [IEEE 7000 Series](https://standards.ieee.org/industry-connections/ec/autonomous-systems/) — IEEE standards for ethically aligned autonomous systems design. IEEE 7010 covers wellbeing metrics; IEEE 7001 covers transparency.
- [CNSA 2.0 (Commercial National Security Algorithm Suite)](https://media.defense.gov/2022/Sep/07/2003071836/-1/-1/0/CSA_CNSA_2.0_ALGORITHMS_.PDF) — NSA's recommended post-quantum cryptography algorithms for national security systems. Specifies transition timelines to CRYSTALS-Kyber (ML-KEM), CRYSTALS-Dilithium (ML-DSA), and SPHINCS+ (SLH-DSA). Published September 2022.
- [NIST PQC Standards (FIPS 203/204/205)](https://csrc.nist.gov/projects/post-quantum-cryptography/post-quantum-cryptography-standardization/finalized-standards) — NIST's finalized post-quantum cryptography standards: FIPS 203 (ML-KEM, key encapsulation), FIPS 204 (ML-DSA, digital signatures), FIPS 205 (SLH-DSA, stateless hash-based signatures). Published August 2024. Mandatory transition for federal systems per NSA/CISA guidance.

### Intelligence Community Standards

- [ICD 203 (Analytic Standards)](https://www.dni.gov/files/documents/ICD/ICD%20203%20Analytic%20Standards.pdf) — Intelligence Community Directive 203. Defines the analytic standards for all IC products: sourcing, uncertainty, alternative analysis, and the precise language of analytic confidence levels ("high confidence," "moderate confidence," "low confidence"). Any software that produces intelligence-flavored outputs should use this vocabulary.
- [ICD 206 (Sourcing Requirements for Finished Intelligence)](https://www.dni.gov/files/documents/ICD/ICD%20206.pdf) — How intelligence analysts must source and cite claims. Influences how OSINT tools should structure evidence citations.
- [Admiralty Scale (NATO STANAG 2511)](https://www.nato.int/cps/en/natolive/official_texts_139229.htm) — The 6x6 reliability/credibility scale for grading intelligence sources (A–F) and the quality of individual reports (1–6). The standard source-grading framework across NATO intelligence organizations.
- [PMESII-PT Framework](https://irp.fas.org/doddir/army/fm3-0.pdf) — Political, Military, Economic, Social, Information, Infrastructure, Physical Environment, Time. The joint military framework for structured environment analysis. Used in operational planning and intelligence products.

### Defense Acquisition and Compliance

- [Cybersecurity Maturity Model Certification (CMMC 2.0)](https://www.acq.osd.mil/cmmc/) — DoD's framework for protecting Controlled Unclassified Information (CUI) in the defense industrial base. Three levels: Foundational (17 practices), Advanced (110 NIST 800-171 practices), Expert (110 + NIST 800-172). Level 2 and 3 require third-party assessment.
- [NIST SP 800-53 Rev. 5](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final) — Security and Privacy Controls for Information Systems and Organizations. 1,000+ controls organized into 20 control families. The baseline for federal ATO (Authorization to Operate) packages under RMF.
- [NIST Risk Management Framework (RMF)](https://csrc.nist.gov/projects/risk-management) — The six-step process (Categorize → Select → Implement → Assess → Authorize → Monitor) for authorizing federal information systems. Required for all DoD IT systems.
- [FIPS 199](https://csrc.nist.gov/publications/detail/fips/199/final) — Federal Information Processing Standard for categorizing information systems by impact level (Low/Moderate/High) across Confidentiality, Integrity, and Availability. Determines which NIST 800-53 baseline applies.
- [ITAR (International Traffic in Arms Regulations)](https://www.pmddtc.state.gov/ddtc_public?id=ddtc_public_portal_itar_landing) — US Munitions List (USML) and export licensing for defense articles and services. Administered by State Department DDTC. Key constraint for any software that touches controlled defense technology.
- [EAR (Export Administration Regulations)](https://www.bis.doc.gov/index.php/regulations/export-administration-regulations-ear) — Controls on dual-use items on the Commerce Control List (CCL). More broadly scoped than ITAR; includes most advanced semiconductor and AI technology.

### Critical Infrastructure Protection

- [Purdue Model (ISA-99 / IEC 62443)](https://www.isa.org/standards-and-publications/isa-standards/isa-standards-committees/isa99) — The reference architecture for industrial control system (ICS) network segmentation. Levels 0–4: field devices, basic control, supervisory, manufacturing operations, enterprise. The lingua franca for OT/IT security discussions.
- [CISA National Critical Functions (NCF)](https://www.cisa.gov/topics/critical-infrastructure-security-and-resilience/critical-infrastructure-sectors/national-critical-functions) — 55 functions so vital to national security, economic security, or public health that their disruption would have a debilitating effect. Organized by sector. More granular than the 16 critical infrastructure sectors — each function maps to specific assets and interdependencies.
- [NIST SP 800-82 Rev. 3](https://csrc.nist.gov/publications/detail/sp/800-82/rev-3/final) — Guide to Operational Technology (OT) Security. The OT-specific companion to NIST 800-53. Covers ICS security architectures, network segmentation, remote access controls, and incident response for OT environments.
- [ICS-CERT CISA Top 10 ICS Vulnerabilities](https://www.cisa.gov/sites/default/files/2022-09/CISA_ICS-CERT_Advisory_9_2022.pdf) — CISA's annually updated most-common-attack-paths against ICS. Useful for prioritizing OT hardening efforts.

### Formal Methods and Verification

- [Z3 Theorem Prover](https://github.com/Z3Prover/z3) — Microsoft Research's SMT (Satisfiability Modulo Theories) solver. Widely used for formal verification of software, contracts, and policy logic. Python API (`pip install z3-solver`). Can encode behavioral rules as logical constraints and automatically find counterexamples.
- [TLA+](https://lamport.azurewebsites.net/tla/tla.html) — Leslie Lamport's specification language for concurrent and distributed systems. Used by AWS, Microsoft, and others to formally verify system properties before implementation.
- [Isabelle/HOL](https://isabelle.in.tum.de/) — Interactive theorem prover for higher-order logic. Used in DO-178C avionics certification and formal verification of safety-critical systems.
- [SPIN Model Checker](https://spinroot.com/) — Model checker for concurrent software verification. Used in aerospace and defense for verifying protocol correctness.

### Privacy and Cryptography

- [Differential Privacy (ε,δ)](https://programming-dp.com/) — Mathematical framework for releasing statistical results about a dataset while bounding information leakage about any individual. The formal guarantee: outputs differ by at most e^ε with probability 1-δ when any single record changes. Used in US Census 2020, Apple, Google.
- [NIST PQC Standards (FIPS 203/204/205)](https://csrc.nist.gov/projects/post-quantum-cryptography) — See [AI and Autonomous Systems](#ai-and-autonomous-systems).
- [CNSA 2.0](https://media.defense.gov/2022/Sep/07/2003071836/-1/-1/0/CSA_CNSA_2.0_ALGORITHMS_.PDF) — See [AI and Autonomous Systems](#ai-and-autonomous-systems).

---

## Regulatory and Policy Documents

### Foreign Investment and Trade Controls

- [31 CFR Part 800 (CFIUS Regulations)](https://www.ecfr.gov/current/title-31/subtitle-B/chapter-VIII/part-800) — The implementing regulations for CFIUS (Committee on Foreign Investment in the United States). Defines covered transactions, mandatory filing thresholds, and TID US businesses (technology, infrastructure, data). Essential reading for any tool analyzing foreign investment in defense suppliers.
- [FIRRMA (Foreign Investment Risk Review Modernization Act)](https://home.treasury.gov/system/files/206/FIRRMA2018.pdf) — The 2018 law that expanded CFIUS authority to cover non-controlling investments in TID US businesses. Introduced mandatory filings for certain transactions involving critical technology, critical infrastructure, and sensitive personal data.
- [Export Administration Regulations (EAR) — CCL](https://www.bis.doc.gov/index.php/documents/regulations-docs/2232-ccl0-to-ccl9/file) — The Commerce Control List (CCL) organizing dual-use items into 10 categories by Export Control Classification Number (ECCN). Category 3 (Electronics), 4 (Computers), and 5 (Telecommunications/IT Security) are most relevant to defense-tech software.
- [OFAC Sanctions Lists](https://ofac.treasury.gov/sanctions-list-service) — SDN (Specially Designated Nationals), Consolidated Sanctions List, CAPTA List, and others. XML/CSV download and REST API. Any transaction or investment tool should screen against these.

### Personnel Security and Clearances

- [Security Executive Agent Directive (SEAD) 3](https://www.dni.gov/files/NCSC/documents/Regulations/SEAD-3-Reportable-Foreign-Contacts-508.pdf) — Reporting requirements for cleared personnel: foreign contacts, travel, financial changes, adverse information. SEAD 3 defines what must be reported, by whom, and within what timeframe. The policy basis for DISS-integrated compliance tools.
- [SEAD 4 (National Security Adjudicative Guidelines)](https://www.dni.gov/files/NCSC/documents/Regulations/SEAD-4-Adjudicative-Guidelines-U.pdf) — The 13 adjudicative criteria used to evaluate clearance eligibility: allegiance, foreign influence, foreign preference, sexual behavior, personal conduct, financial considerations, alcohol, drugs, psychological conditions, criminal conduct, handling protected information, outside activities, use of IT systems.
- [Adjudicative Desk Reference (ADR)](https://www.dhra.mil/Portals/52/Documents/ADR.pdf) — DHRA's comprehensive guide to applying the 13 adjudicative criteria. Covers whole-person analysis, mitigating and aggravating factors, case examples. The operational reference manual for security clearance adjudicators.
- [DISS (Defense Information System for Security)](https://www.dcsa.mil/is/diss/) — The DoD system of record for personnel security investigations and adjudications. CSV export formats used in SEAD 3 compliance reporting tools.

### Defense Acquisition Regulations

- [FAR (Federal Acquisition Regulation)](https://www.acquisition.gov/far/) — The primary regulation governing all federal government procurement. 53 parts covering contract types, clauses, small business rules, and ethics. FAR Part 52 contains standard contract clauses — the boilerplate every federal contractor must accept.
- [DFARS (Defense Federal Acquisition Regulation Supplement)](https://www.acquisition.gov/dfars/) — DoD-specific additions to FAR. DFARS 252.204-7012 (Safeguarding Covered Defense Information) is the clause that operationalizes CMMC requirements in contracts. DFARS 252.239-7010 covers cloud computing.
- [NDAA Annual Authorization](https://armedservices.house.gov/) — National Defense Authorization Act. Enacted annually; authorizes DoD programs and sets policy. Key for tracking: which programs get funded, what acquisition authorities change, and what new oversight requirements are imposed. NDAA FY2024 was P.L. 118-31; FY2025 was P.L. 118-159.
- [DoD 5000 Series (Defense Acquisition Policy)](https://www.dau.edu/tools-and-resources/dag/) — DoD instruction series governing the acquisition lifecycle: DODI 5000.02 (Operation of the Defense Acquisition System), DODI 5000.80 (Middle Tier Acquisition). Defines Milestone A/B/C decision points that determine program funding and transition from RDT&E to procurement.

### Cybersecurity Policy

- [NIST SP 800-171 Rev. 3](https://csrc.nist.gov/publications/detail/sp/800-171/rev-3/final) — Protecting Controlled Unclassified Information in Nonfederal Systems. 110 security requirements, derived from NIST 800-53 and organized into 17 families. The basis for CMMC Level 2. Required for all contractors handling CUI.
- [CISA Zero Trust Maturity Model](https://www.cisa.gov/zero-trust-maturity-model) — CISA's five-pillar model for federal Zero Trust adoption: Identity, Devices, Networks, Applications/Workloads, Data. NDAA FY2024 mandated DoD achieve Zero Trust by 2027.
- [NSA/CISA Cybersecurity Advisories](https://www.cisa.gov/news-events/cybersecurity-advisories) — Joint advisories on nation-state threat actor TTPs, vulnerabilities, and mitigations. The Volt Typhoon, Salt Typhoon, and Midnight Blizzard advisories are particularly relevant to critical infrastructure defense.
- [Binding Operational Directive (BOD) 22-01](https://www.cisa.gov/binding-operational-directive-22-01) — Requires all federal civilian agencies to patch CISA KEV entries within defined timelines. Federal contractors must comply as a contractual requirement.

### AI and Emerging Technology Policy

- [Executive Order 14110 (Safe, Secure, and Trustworthy AI)](https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/) — The October 2023 EO directing federal agencies on AI safety and security. Required NIST to develop AI safety guidelines, directed DoD and IC to develop AI guidance, and established the AI Safety Institute at NIST.
- [DoD AI Strategy (2023)](https://www.ai.mil/docs/2023_DoD_Data_Analytics_AI_Adoption_Strategy.pdf) — Updates DoD's approach to AI adoption, establishing CDAO (Chief Digital and AI Office) as the enterprise coordinator and laying out a path from experimentation to production for AI-enabled capabilities.
- [NSA AI Security Center Guidance](https://media.defense.gov/2024/Mar/28/2003409696/-1/-1/0/CSI-DEPLOYING-AI-SYSTEMS-SECURELY.PDF) — NSA guidance on deploying AI systems securely. Covers model hardening, adversarial ML defenses, and supply chain security for AI components.

---

## Worked Examples

All 49 projects below are part of a single portfolio built between June 9–25, 2026. Each is a standalone tool — no shared infrastructure. Most are CLI-first; 25 are deployed as web apps on Render's free tier.

### Threat Intelligence and Influence Operations

- [SENTINEL](https://sentinel-io-engine.onrender.com) — Ingests adversary RSS/news feeds, clusters posts by DISARM TTP using cosine similarity, and generates an analyst-style intelligence assessment. Uses the DISARM Framework and ICD 203 analytic confidence vocabulary.
- [Dragonbridge/Spamouflage Behavioral Fingerprint Analyzer](https://github.com/JakPot42/dragonbridge-analyzer) — Scores content samples against 12 documented Dragonbridge/Spamouflage behavioral indicators from public Meta ATR, Google/Mandiant, and Stanford Internet Observatory takedown reports. Deterministic scoring. Enforces non-attribution framing throughout. 230 tests.
- [IP Theft Pattern Database](https://github.com/JakPot42/ip-theft-db) — Pattern database of documented intellectual property theft operations by method, sector, and actor type. Scores a given scenario against 443 tests. Built from public DoJ indictments and NCSC/FBI advisories.
- [OSINT Brief Generator](https://github.com/JakPot42/osint-brief) — Compiles an intelligence brief for a named entity by querying open sources (web, news, regulatory filings). Claude synthesizes the raw hits into an ICD 203-formatted product with source citations and confidence levels.
- [FL OSINT Triage](https://github.com/JakPot42/osint-triage) — Foreign-language OSINT triage tool. Detects language, scores relevance, and queues items for analyst review. Designed for document volumes too large to manually translate.
- [Red Team Evaluation](https://github.com/JakPot42/redteam-eval) — Adversarial evaluation framework for AI systems. Runs structured red-team scenarios and scores model responses against safety criteria.

### Cybersecurity and Vulnerability Management

- [CVE Prioritizer](https://cve-prioritizer.onrender.com) — Combines CISA KEV and EPSS scores to produce a prioritized remediation queue. Surfaces high-EPSS CVEs not yet in KEV as early warnings. Zero false-positive philosophy: only ranks what is in the authoritative feeds.
- [ICS/SCADA Vulnerability Exposure Assessor](https://github.com/JakPot42/ics-assessor) — Maps CISA ICS-CERT advisories to Purdue Model layers and scores OT exposure. Flags Volt Typhoon attack vectors for internet-exposed Level 3.5 (DMZ) assets. Three demo environments: water treatment, oil refinery, auto assembly. 225 tests.
- [Volt Typhoon Exposure Assessor](https://github.com/JakPot42/volt-typhoon) — Scores a given OT/IT environment against documented Volt Typhoon TTPs (living-off-the-land binaries, SOHO router pivoting, KV-botnet infrastructure). Built from CISA/NSA/FBI Joint Advisory (February 2024).
- [ATO Accelerator](https://ato-accelerator.onrender.com) — FIPS 199 impact categorization plus NIST 800-53 control baseline selection. Generates a System Security Plan (SSP) narrative draft. Implements the full RMF categorization step deterministically.
- [Fault Injector](https://github.com/JakPot42/fault-injector) — Byzantine fault simulator for distributed systems. Injects partition, delay, crash, and Byzantine faults and observes system behavior. Useful for testing resilience of distributed control systems.
- [Differential Privacy Demo](https://github.com/JakPot42/dp-demo) — Demonstrates the Laplace and Gaussian mechanisms for differential privacy on tabular data. Computes ε-budget consumption across multiple queries. Educational tool for privacy engineering in defense data pipelines.

### Defense Acquisition and Contracting

- [SAM Acquisition Agent](https://sam-acquisition-agent.onrender.com) — Monitors SAM.gov for new contract opportunities, classifies them by NAICS and PSC code, scores fit against a capability profile, and generates a bid/no-bid recommendation. Uses SAM.gov API.
- [Defense Budget & Appropriations Tracker](https://github.com/JakPot42/defense-budget-tracker) — Tracks DoD funding for AI/ML, Hypersonics, Space, and Cyber across FY2022–2026. RDT&E vs. Procurement vs. O&M breakdowns. CAGR and year-over-year trend classification. NDAA provisions seeded from public DoD budget documents and CRS reports. Uses USASpending.gov and congress.gov APIs. 204 tests.
- [Pre-Acquisition Intelligence Brief](https://github.com/JakPot42/acquisition-brief) — Generates a pre-deal intelligence brief for a target company by querying USPTO, CourtListener, SEC EDGAR, and SAM.gov. Deterministic scoring engine (IP strength, litigation risk, regulatory exposure, contract dependency). Demo: Parsons Corporation. 221 tests.
- [CFIUS Screener](https://cfius-screener.onrender.com) — Scores a proposed investment transaction against the Part 800 CFIUS decision tree. Produces a TVC risk scorecard (Technology, Infrastructure, Data) and flags mandatory filing triggers under FIRRMA. Deterministic — Claude never makes a legal determination.
- [FriendShore](https://friendshore-supply-chain.onrender.com) — BOM (Bill of Materials) → Tier 1-3 supply chain graph with SPF (Single Point of Failure) detection. OFAC SDN screening of all nodes. Flags entities with Chinese parent ownership and potential ITAR/EAR entanglements.
- [Security Clearance Advisor](https://clearance-advisor.onrender.com) — Evaluates clearance eligibility scenarios against all 13 SEAD 4 adjudicative criteria. Deterministic whole-person analysis with mitigating/aggravating factors. Based on the Adjudicative Desk Reference.

### OSINT and Strategic Intelligence

- [GhostTrace](https://ghosttrace-aose.onrender.com) — EDGAR beneficial ownership extraction with entity resolution (rapidfuzz), ChromaDB semantic search, and OFAC SDN screening. Agentic loop (5 tool calls max) for deep tracing of corporate structures.
- [Portfolio RAG](https://github.com/JakPot42/portfolio-rag) — Retrieval-augmented generation over a portfolio of intelligence documents. Demonstrates how to build a document-grounded analyst assistant without hallucination.
- [ContextSlim](https://github.com/JakPot42/contextslim) — LLM context compression tool. Trims irrelevant content from long documents before API calls using semantic similarity scoring. Reduces token costs for pipelines that process large intelligence reports.
- [SEAD 3 Auditor](https://sead3-auditor.onrender.com) — Personnel security compliance tool. Processes DISS CSV exports and flags personnel overdue for SEAD 3 reportable events. Generates a ReportLab PDF compliance report for security officers.
- [Carta](https://github.com/JakPot42/carta) — Geopolitical analysis tool using structured analytical techniques. Implements ACH (Analysis of Competing Hypotheses) and other IC structured analytic methodologies.

### Space and Orbital Security

- [Orbital Sentinel](https://orbital-sentinel-65cj.onrender.com) — Real-time satellite conjunction monitoring. Pulls TLE data from Space-Track.org and CelesTrak, computes orbital mechanics, and alerts on close approaches between tracked objects. The only tool in this portfolio that runs in live mode by default (no DEMO_MODE flag).
- [Race Condition](https://github.com/JakPot42/race-condition) — Multi-agent strategic simulator for technology capability races and escalation dynamics. Models arms-race-style competition using game-theoretic payoff matrices.

### Critical Infrastructure and Energy Security

- [GridPulse](https://github.com/JakPot42/gridpulse) — Regional electricity grid stress index. Fuses EIA API v2 demand and generation mix data with NOAA weather forecasts. Six US EIA regions. Stress score: `(net_load / firm_capacity - 0.6) / 0.4 * 100`. Four named scenarios: wind drop, solar drop, demand surge, polar vortex. CISA NCF framing. 221 tests.
- [Water Security Stress Monitor](https://github.com/JakPot42/water-monitor) — USGS streamflow percentile + USDM drought severity → regional water stress score. Eight US watersheds. CISA NCF-39/40 framing. Demo: Colorado River Basin at CRITICAL (82.8/100). 391 tests.
- [Cable Resilience Analyzer](https://cable-resilience-analyzer.onrender.com) — Analyzes submarine cable redundancy and failure scenarios using TeleGeography data. Models traffic re-routing under single and multi-cable failure. Identifies choke points where cable cuts would isolate nations or regions.
- [DIB Monitor](https://dib-monitor.onrender.com) — Defense Industrial Base financial health monitor. Tracks revenue, margins, and R&D spend for major prime contractors. Flags financial distress signals that could indicate supply chain risk.
- [Critical Mineral Monitor](https://critical-mineral-monitor.onrender.com) — Tracks supply chain exposure for DoD-critical minerals (rare earths, cobalt, lithium, etc.). Maps production concentration and US import dependency by mineral.

### Biodefense and Health Security

- [BioMon](https://biomon.onrender.com) — Biosurveillance tool that ingests WHO DON outbreak news, classifies pathogen types (bacterial, viral, unknown), scores severity, and generates a Z-score alert for unusual clustering patterns. The same anomaly-detection architecture as GridPulse and Regulatory Velocity, applied to disease events.
- [scRNA Explorer](https://scrna-explorer-pbmc.onrender.com) — Single-cell RNA sequencing data explorer. Visualizes cell-type clusters from PBMC datasets. Relevant to biodefense for understanding immune response characterization workflows.
- [Harvest Horizon](https://harvest-horizon-lulp.onrender.com) — Agricultural biosecurity and crop resilience tracker. Fuses NOAA weather data and USDA crop reports to assess food security stress scenarios.

### AI Safety, Ethics, and Compliance

- [RAI Compliance](https://rai-compliance.onrender.com) — DoD AI Ethical Principles compliance assessor. Scores an AI system description against all five principles (Responsible, Equitable, Traceable, Reliable, Governable) using a 20-criteria checklist. Claude extracts evidence; deterministic rules produce the score. Claude never makes compliance determinations.
- [NCF TTX Generator](https://ncf-ttx-generator.onrender.com) — Generates tabletop exercise (TTX) scenarios for any of CISA's 55 National Critical Functions. Scenario structure follows HSEEP (Homeland Security Exercise and Evaluation Program) conventions.
- [Emerging Tech Scanner](https://github.com/JakPot42/tech-scanner) — Monitors arXiv and patent databases for emerging technology developments in configurable domains (hypersonics, directed energy, autonomous systems, biotechnology). Scoring based on publication velocity and citation growth.

### Formal Verification and Zero Trust

- [Z3 Contract Checker](https://github.com/JakPot42/z3-contract) — Uses Microsoft's Z3 SMT solver to verify logical consistency in legal contract clauses. Can detect contradictions, ambiguous obligations, and clauses that are always-true or always-false. Demo: lease and licensing agreements.
- [Guarden-FV](https://github.com/JakPot42/guarden-fv) — Formal verification of UAV behavioral rules using Z3. Encodes autonomous system decision policies as logical constraints and checks for consistency. Framing: rule-consistency checker, not a flight dynamics simulator — analogous to how a linter checks code, not how a debugger runs it.
- [Distributed Inference](https://github.com/JakPot42/distributed-inference) — Distributed LLM inference framework. Splits model layers across multiple nodes with network partition handling. Relevant to Zero Trust architectures that require air-gapped AI inference.

### Supply Chain and Foreign Investment Risk

- [FriendShore](https://friendshore-supply-chain.onrender.com) — See [Defense Acquisition and Contracting](#defense-acquisition-and-contracting).
- [CFIUS Screener](https://cfius-screener.onrender.com) — See [Defense Acquisition and Contracting](#defense-acquisition-and-contracting).
- [Gene Drive Ecosystem Sim](https://github.com/JakPot42/gene-drive-sim) — Agent-based simulation of gene drive spread in an ecosystem. Relevant to biosecurity policy: models containment strategies, reversal scenarios, and ecological risk under different drive architectures.
- [MOF Discovery](https://mof-discovery.onrender.com) — Screens the CoRE MOF database for Metal-Organic Frameworks matching target gas capture properties. Demo: CWA (chemical warfare agent) simulant capture for filtration material R&D.

### Policy and Regulatory Analytics

- [Regulatory Velocity Tracker](https://github.com/JakPot42/regulatory-velocity) — Tracks the rate of rulemaking activity per agency using the Federal Register API. Z-score anomaly detection flags agencies with unusually high or low rule publication velocity. Coverage: DFARS, CMMC, ITAR, BIS export controls, SEAD directives. 98 tests.
- [Federal Rulemaking Comment Analyzer](https://github.com/JakPot42/comment-analyzer) — Downloads all public comments from a Regulations.gov docket, classifies them by position (support/oppose/mixed) and stakeholder type using Claude Haiku, and produces a government decision memo. Demo: CMMC 2.0 docket DoD-2023-OS-0063. 131 tests.
- [SCOTUS Analyzer](https://scotus-analyzer.onrender.com) — Analyzes Supreme Court opinion text from Oyez for legal doctrine evolution. Tracks doctrine drift over time for national security and administrative law cases.
- [Litigation Network](https://litigation-network.onrender.com) — Maps litigation relationships between defense industry entities using CourtListener. Identifies repeat litigants, co-defendants, and influential precedents in defense contracting disputes.
- [Citation Checker](https://citation-checker-9d3a.onrender.com) — Verifies that legal citations in a document exist, are accurate, and support the claimed propositions. Uses CourtListener for case retrieval and Claude for proposition matching.
- [Civic RAG](https://civic-rag.onrender.com) — Retrieval-augmented generation over government documents (federal regulations, agency guidance, congressional reports). Answers policy questions with citations to source documents.
- [Lease Translator](https://lease-translator.onrender.com) — Plain-language explanation of government lease and facility agreement terms. Flags non-standard clauses and uses Z3 to check clause consistency before synthesis.
- [Agora](https://agora-oaje.onrender.com) — Public deliberation analytics tool. Aggregates and analyzes public comment patterns across regulatory proceedings.

### Materials Science and Emerging Technology

- [MOF Discovery](https://mof-discovery.onrender.com) — See [Supply Chain and Foreign Investment Risk](#supply-chain-and-foreign-investment-risk).
- [Gene Drive Ecosystem Sim](https://github.com/JakPot42/gene-drive-sim) — See [Supply Chain and Foreign Investment Risk](#supply-chain-and-foreign-investment-risk).
- [Emerging Tech Scanner](https://github.com/JakPot42/tech-scanner) — See [AI Safety, Ethics, and Compliance](#ai-safety-ethics-and-compliance).

---

## Contributing

Additions welcome. Please keep entries:

1. **Free or free-tier accessible** — paid resources are noted but not the focus.
2. **Programmatically accessible** — APIs, structured data downloads, or machine-readable formats. Not just websites.
3. **Defense or national security relevant** — broadly construed to include dual-use technology, critical infrastructure, intelligence, and foreign investment.

For new worked examples, link to a public GitHub repo or live demo. Include the primary API(s) used and one sentence on what makes the implementation interesting.

To suggest additions: open an issue or submit a pull request.

---

*This list is maintained by [@JakPot42](https://github.com/JakPot42). Last updated: June 2026.*

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
