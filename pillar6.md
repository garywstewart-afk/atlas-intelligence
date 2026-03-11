**ATLAS STRATEGIC CONSULTANTS**

**INTELLIGENCE BRIEF**

**Pillar 6: Geospatial Intelligence and Global Monitoring**

Version 1.0 (Draft for Review) \| March 2026 \| Classification: Internal Use Only

**1. Scope and Rationale**

This pillar covers the aggregation, rendering, and analysis of real-time open-source geospatial intelligence (GEOINT) feeds for situational awareness across Atlas research programmes. Unlike Pillar 3 (Penetration Testing and OSINT), which operates at the target enumeration and vulnerability assessment layer, Pillar 6 operates at the geospatial event monitoring layer: tracking the movement of aircraft, ships, satellites, and conflict events on a unified map interface to provide persistent global awareness.

The rationale for a separate pillar is threefold. First, a new category of open-source aggregation dashboards (ShadowBroker, WorldMonitor, Pharos AI) emerged in late 2025 and early 2026, consolidating what previously required bouncing between a dozen separate platforms. Second, Atlas has active programmes with direct geospatial monitoring requirements: the West Africa Intelligence Programme (Sierra Leone, Liberia, Cote d'Ivoire) needs conflict event tracking, and the Mining Exploration programme benefits from infrastructure and natural hazard monitoring. Third, the underlying data feeds (ADS-B, AIS, GDELT, ACLED, USGS, satellite TLE) are all freely available but rarely consumed systematically within consulting engagements. This pillar formalises that consumption.

> ***Source notes:** ShadowBroker (GitHub: BigBodyCobain/Shadowbroker, March 2026). WorldMonitor (GitHub: koala73/worldmonitor, 2024-2026). Pillar 3 brief v1.2 for OSINT tool boundary. Atlas West Africa programme scope from project instructions v3.3.*

**2. Core Data Feeds Taxonomy**

The feeds that underpin this pillar fall into six domains. Each domain has established open-source providers with well-documented APIs or WebSocket streams. The table below catalogues the primary feeds, their providers, update frequencies, and Atlas relevance.

  -------------------------- ------------------------------------------------------- --------------------------------------------- ------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------
  **Domain**                 **Primary Feed**                                        **Provider**                                  **Update Freq**                 **Atlas Relevance**

  Aviation (ADS-B)           Commercial and military transponder positions           OpenSky Network, ADS-B Exchange               5-10 sec                        Carrier/military movement indicators. West Africa airspace monitoring. Private jet tracking for corporate intelligence.

  Maritime (AIS)             Vessel positions, type, heading, cargo class            AIS WebSocket (25K+ vessels), MarineTraffic   Real-time                       Gulf of Guinea piracy corridor. Bulk carrier movements for mining commodity logistics. EEZ monitoring.

  Satellite (TLE)            Orbital elements for intelligence-relevant satellites   N2YO, CelesTrak                               15 min                          Overhead pass awareness for sensitive operations. ISR satellite tracking.

  Conflict Events            Political violence, protests, military actions          GDELT, ACLED, UCDP                            15 min (GDELT), daily (ACLED)   West Africa conflict monitoring (ACLED Conflict Index covers Sierra Leone, Liberia, Cote d'Ivoire). Mining jurisdiction risk assessment.

  Seismic / Natural Hazard   Earthquakes, volcanic activity, wildfire hotspots       USGS, GDACS, NASA FIRMS/EONET                 Minutes                         Mining tenement natural hazard overlay. Infrastructure risk for operational sites.

  GPS Interference           GPS jamming and spoofing detection                      GPSJam.org                                    Daily                           Indicator of military activity or electronic warfare. Relevant to geopolitical event monitoring.
  -------------------------- ------------------------------------------------------- --------------------------------------------- ------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------

> ***Source notes:** Feed providers and update frequencies verified from ShadowBroker README and WorldMonitor DATA_SOURCES.md (March 2026). GDELT updates every 15 minutes per gdeltproject.org. ACLED provides near-real-time event data with 30-day rolling window via tokenised API. OpenSky Network provides free ADS-B data with 5-10 second resolution.*

**3. Open-Source Aggregation Platforms (2025-2026)**

Three open-source platforms have emerged that aggregate multiple GEOINT feeds into unified dashboard interfaces. These represent a new category distinct from single-domain trackers like Flightradar24 or MarineTraffic.

**3.1 ShadowBroker**

ShadowBroker is a real-time multi-domain OSINT dashboard released in March 2026 by developer BigBodyCobain on GitHub. It aggregates ADS-B (commercial and military aircraft via OpenSky), AIS maritime data (25,000+ vessels via WebSocket), N2YO satellite telemetry, GDELT conflict events, USGS seismic data, GPS jamming feeds, and publicly crawled CCTV camera databases onto a single MapLibre GL map interface. The stack is Next.js (frontend), FastAPI/Python (backend), with Docker Compose for self-hosting. It includes a carrier strike group tracker that estimates positions of all 11 active US Navy aircraft carriers using automated GDELT news scraping. The developer explicitly notes that carrier positions are estimates based on public reporting, not classified data. The project received significant attention on Hacker News in March 2026.

> ***Source notes:** GitHub: BigBodyCobain/Shadowbroker. Hacker News: Show HN thread (March 11, 2026). Stack: Next.js, MapLibre GL, FastAPI, Python, Docker.*

**3.2 WorldMonitor**

WorldMonitor is a more mature and architecturally sophisticated platform developed by Elie Habib (2024-2026), licensed under AGPL-3.0. It aggregates 31 tracked data sources including OpenSky, GDELT, ACLED, UCDP, HAPI, USGS, GDACS, NASA EONET, NASA FIRMS, Polymarket prediction markets, Cloudflare Radar, WorldPop population data, OREF (Israel Home Front Command alerts), GPSJam GPS interference, and 26 Telegram OSINT channels via MTProto. The platform features a Composite Intelligence Index (CII) that scores geopolitical instability using regime-aware weighting: democratic countries use logarithmic scaling for protests while authoritarian states use linear scaling. It provides AI-powered summarisation through Groq and OpenRouter LLM integrations with local Ollama support. The tech stack includes vanilla TypeScript (no framework), 60+ Vercel Edge Functions, Tauri for native desktop builds (macOS/Windows/Linux), Protocol Buffers for 22 typed service domains, and 3-tier caching (in-memory, Redis, upstream). It supports 21 languages and 435+ RSS feeds.

> ***Source notes:** GitHub: koala73/worldmonitor. DATA_SOURCES.md for feed inventory. AGPL-3.0 license. Tauri desktop builds confirmed for Apple Silicon.*

**3.3 Pharos AI**

Pharos AI is a more narrowly scoped open-source intelligence dashboard focused on conflict tracking with interactive geospatial visualisation, multi-source RSS monitoring, and actor dossiers. It appears in the jivoi/awesome-osint curated list. It is less feature-rich than ShadowBroker or WorldMonitor but provides a lighter-weight option for conflict-specific monitoring.

> ***Source notes:** GitHub: listed in jivoi/awesome-osint. Scope: conflict tracking with geospatial visualisation.*

**4. Commercial and Institutional Platforms**

The open-source dashboards exist alongside established commercial platforms that offer curated, verified intelligence at higher price points. ACLED itself provides a Conflict Alert System (CAST) that forecasts political violence events up to six months ahead for every country. GDELT Cloud launched a commercial tier with an MCP server integration that works directly with Claude Desktop, providing 12 tools for querying event data programmatically. OS-Surveillance offers an AI-powered OSINT platform with satellite imagery comparison across 8 providers, face recognition, and territory analysis with automated AI reporting. Windward provides Maritime AI that fuses AIS data with behavioural analytics to detect dark vessel activity, EEZ violations, and suspicious loitering patterns near sensitive sites.

The global geospatial analytics market is projected to grow from USD \$95.84 billion in 2025 to USD \$174.44 billion by 2030 at a CAGR of 12.7%, reflecting the mainstreaming of GEOINT capabilities beyond traditional defence and intelligence consumers.

> ***Source notes:** ACLED CAST: acleddata.com/conflict-data. GDELT Cloud MCP: gdeltcloud.com (MCP server for Claude Desktop integration). Windward Maritime AI: windward.ai. Market projection: Mordor Intelligence geospatial analytics forecast 2025-2030.*

**5. Atlas Programme Application Mapping**

  -------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Atlas Programme**        **GEOINT Application**                                                                                                                                         **Priority Feeds**

  West Africa Intelligence   Conflict event monitoring across Sierra Leone, Liberia, and Cote d'Ivoire. Protest tracking. Military movement indicators. Gulf of Guinea maritime security.   ACLED (conflict events, actor attribution, fatality counts), GDELT (news event volume and sentiment), AIS (Gulf of Guinea vessel tracking), GPS jamming (military activity indicator).

  Mining Exploration (AU)    Natural hazard overlay for tenement assessment. Seismic activity near exploration corridors. Infrastructure monitoring. Commodity shipping logistics.          USGS (seismic), NASA FIRMS (wildfire hotspots), AIS (bulk carrier movements for Mt Isa corridor commodity exports).

  Pillar 2 (Quant Trading)   Geopolitical event correlation with market movements. Polymarket prediction market integration. Supply chain disruption indicators.                            GDELT (event volume spikes), Polymarket (geopolitical contract probabilities), AIS (chokepoint congestion at Suez, Hormuz, Malacca).

  Pillar 3 (Pentest/OSINT)   Complementary layer: geospatial situational awareness during engagement planning. Physical security assessment context.                                        All feeds as background context. ShadowBroker/WorldMonitor as pre-engagement situational awareness dashboard.
  -------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

> ***Source notes:** Application mapping derived from Atlas programme scope in project instructions v3.3 and pillar briefs v1.0-v1.2.*

**6. Technical Deployment Considerations**

Both ShadowBroker and WorldMonitor are Docker-composable and can run on Apple Silicon (the Atlas development platform). ShadowBroker is the lighter deployment (Next.js + FastAPI, minimal dependencies) while WorldMonitor is more complex (Vercel Edge Functions, Railway for WebSocket relay, Redis for caching, Tauri for desktop builds) but offers significantly richer intelligence processing including CII scoring and AI summarisation.

For Atlas purposes, the recommended deployment path is to self-host ShadowBroker as a quick-start dashboard for visual situational awareness, and evaluate WorldMonitor for deeper integration where the CII scoring and ACLED regime-aware protest weighting add analytical value. Both projects are under active development. API keys are required for certain feeds (ACLED tokenised API, OpenSky authenticated access for higher rate limits, Groq/OpenRouter for AI features in WorldMonitor). All API keys are stored server-side and never exposed to the browser in either platform.

A critical operational note from the OSINT community: these dashboards surface signals, not verified intelligence. An AI-generated threat classification is a hypothesis that requires investigation. The dashboard finds the signal; the human determines what it means. This discipline aligns with the Atlas per-pillar reliability framework documented in Pillar 5.

> ***Source notes:** ShadowBroker Docker deployment: compose.sh auto-detects Docker/Podman. WorldMonitor Tauri builds: confirmed macOS Apple Silicon. Operational discipline: Nico Dekens, ShadowDragon 2026 OSINT Guide; Philippe Borremans, RiskComms 2025. Pillar 5 reliability framework cross-reference.*

**7. GDELT Cloud MCP Integration Opportunity**

GDELT Cloud now offers an MCP server that integrates directly with Claude Desktop and any MCP-compatible AI agent framework. The server provides system prompts, 12 tools, and schema resources for querying GDELT event data. This means GDELT conflict and protest data can be queried inline during Atlas research sessions in the same way that PubMed, Scholar Gateway, and S&P Global are currently used via MCP connectors. The MCP endpoint is gdelt-cloud-mcp.fastmcp.app/mcp and requires a GDELT API key (available on Analyst or Professional plans). This would bring Pillar 6 feeds into the Rule 1 framework (MCP connectors as first-pass tools) and is the highest-priority integration action for this pillar.

> ***Source notes:** GDELT Cloud MCP: gdeltcloud.com. Configuration: mcp_servers entry with bearer auth and GDELT_API_KEY. Plans: free tier (Research Agent, Media Events feed), Analyst and Professional tiers for API keys and MCP access.*

**8. Update Protocol**

**8.1 Update Triggers**

This pillar brief is updated when any of the following events occur. New aggregation platform releases or major version updates to ShadowBroker or WorldMonitor. New GEOINT-relevant MCP connectors becoming available (particularly GDELT Cloud, ACLED). Significant changes to feed availability or API terms (OpenSky rate limit changes, ACLED access tier modifications). New Atlas programme with geospatial monitoring requirements. ACLED Conflict Watchlist annual release (covers West Africa programme countries). Emergence of new conflict data sources or prediction market integrations.

**8.2 Pillar Boundary with Pillar 3**

Pillar 3 covers target-specific OSINT (enumeration, reconnaissance, vulnerability assessment) using tools like Maltego, SpiderFoot, Sherlock, and Shodan. Pillar 6 covers persistent, wide-area geospatial monitoring using event feeds, vessel/aircraft tracking, and conflict data. The boundary is operational scope: Pillar 3 is narrow and deep (a specific target), Pillar 6 is broad and continuous (the operating environment). ShadowBroker and WorldMonitor sit in Pillar 6. DNSDumpster and Nuclei sit in Pillar 3. Some tools and feeds may appear in both contexts.

**Document Information**

Prepared by: Atlas Strategic Consultants --- Gary Stewart, Lead Consultant

Date: March 2026 \| Status: Draft for Review --- Version 1.0 \| Classification: Internal Use Only

Next Review: On any update trigger listed in Section 8.1 --- minimum quarterly.

Triggering event: ShadowBroker OSINT dashboard identification (March 11, 2026), subsequent landscape review of open-source GEOINT aggregation platforms. Scope: real-time geospatial intelligence feeds, open-source and commercial aggregation platforms, Atlas programme application mapping, GDELT MCP integration opportunity, technical deployment considerations, pillar boundary definition with Pillar 3.
