<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>IE × Hydrogeology Research Roadmap</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --gold:        #b5953a;
      --gold-light:  rgba(181, 149, 58, 0.11);
      --gold-border: rgba(181, 149, 58, 0.24);
      --text-1:      #1a2530;
      --text-2:      #4a5568;
      --text-3:      #718096;
      --text-4:      #9aabb8;
      --card:        rgba(255, 255, 255, 0.70);
      --card-hover:  rgba(255, 255, 255, 0.92);
      --card-border: rgba(255, 255, 255, 0.88);
    }

    body {
      font-family: 'Inter', sans-serif;
      font-weight: 400;
      background: linear-gradient(155deg, #edf1f7 0%, #e3eaf3 100%);
      color: var(--text-1);
      min-height: 100vh;
      padding: 64px 24px 96px;
    }

    .wrap { max-width: 1000px; margin: 0 auto; }

    /* HEADER */
    .header { text-align: center; margin-bottom: 50px; animation: rise 0.7s ease both; }
    .eyebrow { font-size: 10px; font-weight: 600; letter-spacing: 0.22em; text-transform: uppercase; color: var(--text-4); margin-bottom: 16px; }
    .header h1 { font-family: 'Cinzel', serif; font-size: 24px; font-weight: 600; color: var(--text-1); letter-spacing: 0.07em; line-height: 1.4; text-transform: uppercase; margin-bottom: 18px; }
    .gold-rule { width: 44px; height: 1px; background: var(--gold); margin: 0 auto 18px; }
    .header p { font-size: 13px; font-weight: 300; color: var(--text-3); max-width: 570px; margin: 0 auto; line-height: 1.8; }

    /* BRIDGE */
    .bridge { display: flex; align-items: center; justify-content: center; margin-bottom: 50px; animation: rise 0.7s ease 0.1s both; }
    .bridge-cell { padding: 18px 28px; border-radius: 10px; flex: 1; max-width: 272px; }
    .bridge-cell.left  { background: rgba(255,255,255,0.52); border: 1px solid rgba(0,0,0,0.06); text-align: right; }
    .bridge-cell.right { background: var(--gold-light); border: 1px solid var(--gold-border); text-align: left; }
    .b-label { font-size: 9px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.14em; color: var(--text-4); margin-bottom: 5px; }
    .b-val { font-family: 'Cinzel', serif; font-size: 11.5px; font-weight: 600; letter-spacing: 0.04em; line-height: 1.5; }
    .b-val.l { color: var(--text-3); }
    .b-val.r { color: var(--text-1); }
    .bridge-mid { display: flex; flex-direction: column; align-items: center; gap: 4px; padding: 0 20px; }
    .bridge-tag { font-size: 8.5px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.12em; color: var(--gold); white-space: nowrap; }

    /* PHASE HEADERS */
    .phase-headers { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; margin-bottom: 8px; animation: rise 0.7s ease 0.18s both; }
    .ph { display: flex; align-items: center; gap: 9px; }
    .ph-dot { width: 7px; height: 7px; border-radius: 50%; background: var(--gold); flex-shrink: 0; }
    .ph-title { font-family: 'Cinzel', serif; font-size: 10.5px; font-weight: 700; letter-spacing: 0.13em; text-transform: uppercase; color: var(--text-1); white-space: nowrap; }
    .ph-rule { flex: 1; height: 1px; background: rgba(0,0,0,0.09); }

    /* ROADMAP */
    .roadmap { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; margin-bottom: 52px; }

    /* TRACK */
    .track { position: relative; display: flex; flex-direction: column; gap: 18px; }
    .track::before { content: ''; position: absolute; left: 12px; top: 32px; bottom: 32px; width: 1px; border-left: 1px dashed rgba(181,149,58,0.28); }

    /* NODE */
    .node { position: relative; padding-left: 36px; }
    .node:nth-child(1) { animation: rise 0.6s ease 0.26s both; }
    .node:nth-child(2) { animation: rise 0.6s ease 0.40s both; }

    .pin { position: absolute; left: 4px; top: 19px; width: 18px; height: 18px; border-radius: 50%; background: var(--gold); display: flex; align-items: center; justify-content: center; font-size: 9px; font-weight: 700; color: #fff; z-index: 2; }

    /* CARD */
    .card { background: var(--card); backdrop-filter: blur(16px); -webkit-backdrop-filter: blur(16px); border: 1px solid var(--card-border); border-radius: 14px; overflow: hidden; transition: background 0.28s, box-shadow 0.28s; }
    .card:hover { background: var(--card-hover); box-shadow: 0 6px 24px rgba(100,120,150,0.13); }
    .card.open  { background: var(--card-hover); box-shadow: 0 10px 32px rgba(100,120,150,0.16); }

    .card-head { padding: 20px 22px 18px; user-select: none; }
    .card-row { display: flex; justify-content: space-between; align-items: flex-start; gap: 10px; }
    .card-title { font-family: 'Cinzel', serif; font-size: 13.5px; font-weight: 600; color: var(--text-1); line-height: 1.45; letter-spacing: 0.01em; }
    .chevron { color: var(--text-4); font-size: 15px; transition: transform 0.3s ease, color 0.2s; flex-shrink: 0; padding-top: 2px; line-height: 1; }
    .card.open .chevron { transform: rotate(180deg); color: var(--gold); }

    /* CARD BODY */
    .card-body { max-height: 0; overflow: hidden; transition: max-height 0.42s cubic-bezier(0.25, 0.8, 0.25, 1); }
    .body-inner { border-top: 1px solid rgba(0,0,0,0.05); padding: 18px 22px 20px; }
    .blk { margin-bottom: 14px; }
    .blk:last-of-type { margin-bottom: 0; }
    .bl { font-size: 8.5px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.12em; color: var(--text-1); margin-bottom: 5px; }
    .bt { font-size: 12.5px; line-height: 1.68; font-weight: 400; color: var(--text-2); }

    .chips { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 8px; margin-top: 16px; }
    .chip { background: var(--gold-light); border: 1px solid var(--gold-border); border-radius: 8px; padding: 9px 12px; }
    .chip a { font-size: 10.5px; font-weight: 500; color: var(--gold); text-decoration: none; line-height: 1.45; display: block; margin-top: 2px; }
    .chip a:hover { text-decoration: underline; }
    .cl { font-size: 8px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.1em; color: var(--text-4); margin-bottom: 3px; }
    .cv { font-size: 11px; font-weight: 600; color: var(--text-1); line-height: 1.3; }

    /* PILLARS */
    .pillars-wrap { animation: rise 0.7s ease 0.52s both; }
    .sec-rule { display: flex; align-items: center; gap: 14px; margin-bottom: 26px; }
    .sec-rule span { height: 1px; flex: 1; background: rgba(0,0,0,0.08); }
    .sec-rule h2 { font-family: 'Cinzel', serif; font-size: 11px; font-weight: 700; letter-spacing: 0.18em; text-transform: uppercase; color: var(--text-1); white-space: nowrap; }
    .pillars { display: grid; grid-template-columns: repeat(3,1fr); gap: 16px; }
    .pillar { background: rgba(255,255,255,0.60); border: 1px solid rgba(255,255,255,0.90); border-radius: 14px; padding: 24px 20px; text-align: center; transition: background 0.24s, transform 0.24s, box-shadow 0.24s; }
    .pillar:hover { background: rgba(255,255,255,0.88); transform: translateY(-2px); box-shadow: 0 6px 20px rgba(100,120,150,0.12); }
    .p-glyph { font-size: 19px; color: var(--gold); margin-bottom: 11px; }
    .p-from  { font-size: 10.5px; color: var(--text-4); text-decoration: line-through; margin-bottom: 5px; }
    .p-arr   { font-size: 14px; color: var(--gold); margin-bottom: 5px; }
    .p-to    { font-family: 'Cinzel', serif; font-size: 11.5px; font-weight: 600; color: var(--text-1); letter-spacing: 0.04em; margin-bottom: 10px; }
    .p-desc  { font-size: 11.5px; font-weight: 300; color: var(--text-3); line-height: 1.65; }

    /* FOOTER */
    .footer { text-align: center; margin-top: 52px; animation: rise 0.7s ease 0.62s both; }
    .foot-rule { width: 44px; height: 1px; background: var(--gold); opacity: .45; margin: 0 auto 14px; }
    .footer p { font-size: 10.5px; font-weight: 300; letter-spacing: 0.05em; color: var(--text-4); }
    .footer strong { font-family: 'Cinzel', serif; font-weight: 600; font-size: 10.5px; color: var(--text-3); }

    @keyframes rise { from { opacity: 0; transform: translateY(14px); } to { opacity: 1; transform: translateY(0); } }

    @media (max-width: 660px) {
      .roadmap, .phase-headers, .pillars { grid-template-columns: 1fr; }
      .bridge { flex-direction: column; align-items: center; gap: 8px; }
      .bridge-cell { text-align: center; max-width: 100%; }
      .bridge-mid { flex-direction: row; }
    }
  </style>
</head>
<body>
<div class="wrap">

  <!-- HEADER -->
  <header class="header">
    <div class="eyebrow">Dr. Mohd Yawar Ali Khan &nbsp;·&nbsp; Hydrogeological Research Collaboration</div>
    <h1>Unlocking the Full Potential<br>of a Pioneering Research Program</h1>
    <div class="gold-rule"></div>
    <p>Dr. Khan's landmark contributions to hydrogeological science have established a rich body of high-caliber datasets and frameworks. This roadmap identifies where the application of Industrial Engineering methodologies can illuminate the deeper quantitative power already embedded in that work.</p>
  </header>

  <!-- BRIDGE -->
  <div class="bridge">
    <div class="bridge-cell left">
      <div class="b-label">Established Foundation</div>
      <div class="b-val l">Dr. Khan's Frameworks &amp; Datasets</div>
    </div>
    <div class="bridge-mid">
      <div class="bridge-tag">IE Amplification</div>
      <svg width="88" height="20" viewBox="0 0 88 20" fill="none">
        <line x1="4" y1="10" x2="72" y2="10" stroke="#b5953a" stroke-width="1.5" stroke-dasharray="4 3"/>
        <path d="M68 5L76 10L68 15" stroke="#b5953a" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>
    <div class="bridge-cell right">
      <div class="b-label">Revealed Potential</div>
      <div class="b-val r">Full Scientific Depth Activated</div>
    </div>
  </div>

  <!-- PHASE HEADERS -->
  <div class="phase-headers">
    <div class="ph"><div class="ph-dot"></div><span class="ph-title">Phase I — Computational Layer</span><div class="ph-rule"></div></div>
    <div class="ph"><div class="ph-dot"></div><span class="ph-title">Phase II — Structural Layer</span><div class="ph-rule"></div></div>
  </div>

  <!-- ROADMAP -->
  <div class="roadmap">

    <!-- PHASE I -->
    <div class="track">

      <div class="node">
        <div class="pin">1</div>
        <div class="card" id="c11">
          <div class="card-head" onclick="toggle('c11')" style="cursor:pointer">
            <div class="card-row">
              <h3 class="card-title">Revealing the Statistical Depth of Dr. Khan's Groundwater Network Data</h3>
              <span class="chevron">&#9662;</span>
            </div>
          </div>
          <div class="card-body">
            <div class="body-inner">
              <div class="blk">
                <div class="bl">Dr. Khan's Established Framework</div>
                <div class="bt">Comprehensive geochemical characterisation of arid aquifer networks through rigorously applied PCA and HCA — producing authoritative spatial maps of groundwater quality distributions across multi-well systems.</div>
              </div>
              <div class="blk">
                <div class="bl">What Dr. Bader's Toolkit Reveals</div>
                <div class="bt">Dr. Khan's datasets carry a level of statistical richness that extends well beyond static mapping. By layering Hotelling T² control boundaries and Mahalanobis distance metrics, the full multivariate signal embedded in his data can be activated — revealing dynamic anomaly patterns and network drift signatures his original framework had already captured.</div>
              </div>
              <div class="blk">
                <div class="bl">Potential Elevated</div>
                <div class="bt">Dr. Khan's characterisation work proves substantial enough to sustain a live regional monitoring architecture — elevating his published record from landmark geological survey to an operational early-warning resource for water security policy.</div>
              </div>
              <div class="chips">
                <div class="chip"><div class="cl">Approach</div><div class="cv">Purely Computational</div></div>
                <div class="chip"><div class="cl">Timeline</div><div class="cv">Days to Activate</div></div>
                <div class="chip"><div class="cl">Source Paper</div><a href="https://www.sciencedirect.com/science/article/pii/S1470160X23004296" target="_blank">Wadi Itwad Aquifer, Saudi Arabia (2023) ↗</a></div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="node">
        <div class="pin">2</div>
        <div class="card" id="c12">
          <div class="card-head" onclick="toggle('c12')" style="cursor:pointer">
            <div class="card-row">
              <h3 class="card-title">Mathematically Validating Dr. Khan's Machine Learning Architecture</h3>
              <span class="chevron">&#9662;</span>
            </div>
          </div>
          <div class="card-body">
            <div class="body-inner">
              <div class="blk">
                <div class="bl">Dr. Khan's Established Framework</div>
                <div class="bt">Sophisticated application of ANN feedforward-backpropagation architectures to predict volatile river discharge rates and sediment curves — among the most advanced ML deployments in regional hydrogeological research.</div>
              </div>
              <div class="blk">
                <div class="bl">What Dr. Bader's Toolkit Reveals</div>
                <div class="bt">By treating Dr. Khan's ML architecture as an experimental system and mapping its parameters into a Box-Behnken design, a formal response surface can be constructed over the exact parameter space his models operate in — producing a mathematical proof that his design choices are not only effective, but optimal.</div>
              </div>
              <div class="blk">
                <div class="bl">Potential Elevated</div>
                <div class="bt">Dr. Khan's ML framework transitions from high-performing predictive model to a formally verified geoscientific instrument — strengthening its standing for publication, citation, and operational adoption.</div>
              </div>
              <div class="chips">
                <div class="chip"><div class="cl">Approach</div><div class="cv">HPC Simulation</div></div>
                <div class="chip"><div class="cl">Timeline</div><div class="cv">1 – 2 Weeks</div></div>
                <div class="chip"><div class="cl">Source Papers</div><a href="https://link.springer.com/article/10.1007/s40899-020-00396-6" target="_blank">Bhagirathi River ANN (2020) ↗</a><a href="https://link.springer.com/article/10.1007/s40899-018-0288-7" target="_blank">Ramganga Sediment Load (2019) ↗</a></div>
              </div>
            </div>
          </div>
        </div>
      </div>

    </div>

    <!-- PHASE II -->
    <div class="track">

      <div class="node">
        <div class="pin">1</div>
        <div class="card" id="c21">
          <div class="card-head" onclick="toggle('c21')" style="cursor:pointer">
            <div class="card-row">
              <h3 class="card-title">Demonstrating the Spatial Precision in Dr. Khan's Recharge Zone Methodology</h3>
              <span class="chevron">&#9662;</span>
            </div>
          </div>
          <div class="card-body">
            <div class="body-inner">
              <div class="blk">
                <div class="bl">Dr. Khan's Established Framework</div>
                <div class="bt">Highly regarded GIS-integrated Aquifer Recharge Potential Zone delineation — employing multi-layer data fusion and AHP weighting to produce regional recharge maps relied upon for groundwater resource planning.</div>
              </div>
              <div class="blk">
                <div class="bl">What Dr. Bader's Toolkit Reveals</div>
                <div class="bt">By applying spatial D-Optimal design principles to Dr. Khan's site topology, the informational value already captured by his field campaign can be formally quantified — while identifying precisely where a targeted next-phase campaign would yield the greatest marginal scientific return, building directly on his established methodology.</div>
              </div>
              <div class="blk">
                <div class="bl">Potential Elevated</div>
                <div class="bt">Dr. Khan's ARPZ framework is positioned as the foundational layer for the most statistically defensible aquifer monitoring system achievable in the region — with a clear, evidence-based path for each future field expansion.</div>
              </div>
              <div class="chips">
                <div class="chip"><div class="cl">Approach</div><div class="cv">Field + Analytical</div></div>
                <div class="chip"><div class="cl">Timeline</div><div class="cv">Planned Field Seasons</div></div>
                <div class="chip"><div class="cl">Source Papers</div><a href="https://www.mdpi.com/2072-4292/15/10/2567" target="_blank">ARPZ Saudi Arabia (2023) ↗</a><a href="https://www.mdpi.com/2073-4441/14/7/1041" target="_blank">Eastern Desert Egypt (2022) ↗</a></div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="node">
        <div class="pin">2</div>
        <div class="card" id="c22">
          <div class="card-head" onclick="toggle('c22')" style="cursor:pointer">
            <div class="card-row">
              <h3 class="card-title">Extending Dr. Khan's Sustainability Criteria into a Living Control Architecture</h3>
              <span class="chevron">&#9662;</span>
            </div>
          </div>
          <div class="card-body">
            <div class="body-inner">
              <div class="blk">
                <div class="bl">Dr. Khan's Established Framework</div>
                <div class="bt">Authoritative multi-criteria AHP-based sustainability evaluation of dry-land water reserves — providing the criteria structure that now informs regional water resource management and guides policy decisions.</div>
              </div>
              <div class="blk">
                <div class="bl">What Dr. Bader's Toolkit Reveals</div>
                <div class="bt">Dr. Khan's carefully constructed sustainability criteria serve as the ideal seed for a fully adaptive stochastic optimisation engine. His weighting structure is brought to life as a dynamic Pareto-optimal system that updates continuously with real-time sensor telemetry — fulfilling the operational intent of his original criteria at scale.</div>
              </div>
              <div class="blk">
                <div class="bl">Potential Elevated</div>
                <div class="bt">Dr. Khan's sustainability framework grows from landmark research into a living water management architecture — extending its reach from published assessment into real-time operational control of the very reserves it originally described.</div>
              </div>
              <div class="chips">
                <div class="chip"><div class="cl">Approach</div><div class="cv">SCADA + IoT Network</div></div>
                <div class="chip"><div class="cl">Timeline</div><div class="cv">Multi-Month Build</div></div>
                <div class="chip"><div class="cl">Source Papers</div><a href="https://www.sciencedirect.com/science/article/pii/S1470160X23004296" target="_blank">Wadi Itwad Aquifer (2023) ↗</a><a href="https://www.mdpi.com/2073-4441/15/19/3464" target="_blank">Wadi Bani Malik Basin (2023) ↗</a></div>
              </div>
            </div>
          </div>
        </div>
      </div>

    </div>

  </div>

  <!-- PILLARS -->
  <div class="pillars-wrap">
    <div class="sec-rule"><span></span><h2>Core Transformation Pillars</h2><span></span></div>
    <div class="pillars">
      <div class="pillar">
        <div class="p-glyph">&#11041;</div>
        <div class="p-from">Static Snapshots</div>
        <div class="p-arr">&#8595;</div>
        <div class="p-to">Process-Oriented</div>
        <div class="p-desc">Dr. Khan's geological datasets are rich enough to sustain dynamic, continuous monitoring — not merely periodic surveys</div>
      </div>
      <div class="pillar">
        <div class="p-glyph">&#11041;</div>
        <div class="p-from">Expert Estimation</div>
        <div class="p-arr">&#8595;</div>
        <div class="p-to">Algorithmic Rigor</div>
        <div class="p-desc">The science already present in his frameworks is elevated by replacing subjective weighting with mathematically defensible optimisation</div>
      </div>
      <div class="pillar">
        <div class="p-glyph">&#11041;</div>
        <div class="p-from">Published Assessment</div>
        <div class="p-arr">&#8595;</div>
        <div class="p-to">Operational Impact</div>
        <div class="p-desc">Dr. Khan's research carries enough depth to transition from scholarly contribution to real-time policy and management tools</div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="foot-rule"></div>
    <p><strong>IE &times; Hydrogeology Collaboration</strong> &nbsp;&middot;&nbsp; 4 Research Pathways &nbsp;&middot;&nbsp; 2 Phases &nbsp;&middot;&nbsp; 3 Transformation Pillars</p>
  </div>

</div>

<script>
  function toggle(id) {
    var card = document.getElementById(id);
    var body = card.querySelector('.card-body');
    var wasOpen = card.classList.contains('open');
    document.querySelectorAll('.card').forEach(function(c) {
      c.classList.remove('open');
      c.querySelector('.card-body').style.maxHeight = null;
    });
    if (!wasOpen) {
      card.classList.add('open');
      body.style.maxHeight = body.scrollHeight + 'px';
    }
  }
</script>
</body>
</html>
