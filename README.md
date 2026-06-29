<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Supply & Demand Scenario Watchlist</title>

  <style>
    :root {
      --bg:#0f172a;
      --panel:#111827;
      --panel2:#1f2937;
      --text:#e5e7eb;
      --muted:#9ca3af;
      --line:#374151;
      --bull:#16a34a;
      --bear:#dc2626;
      --gold:#f59e0b;
      --blue:#38bdf8;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin:0;
      font-family: Arial, Helvetica, sans-serif;
      background:var(--bg);
      color:var(--text);
    }

    .wrap {
      max-width:1180px;
      margin:0 auto;
      padding:28px;
    }

    h1 {
      margin:0 0 6px 0;
      font-size:32px;
    }

    h2 {
      margin:32px 0 16px;
      border-bottom:1px solid var(--line);
      padding-bottom:8px;
    }

    .sub {
      color:var(--muted);
      line-height:1.5;
    }

    .stats {
      display:grid;
      grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
      gap:12px;
      margin:22px 0;
    }

    .stat {
      background:var(--panel);
      border:1px solid var(--line);
      border-radius:14px;
      padding:16px;
    }

    .stat .label {
      color:var(--muted);
      font-size:13px;
    }

    .stat .value {
      font-size:24px;
      font-weight:700;
      margin-top:6px;
    }

    table {
      width:100%;
      border-collapse:collapse;
      background:var(--panel);
      border-radius:14px;
      overflow:hidden;
      margin-bottom:22px;
    }

    th, td {
      padding:11px 12px;
      border-bottom:1px solid var(--line);
      text-align:left;
      font-size:14px;
      vertical-align:top;
    }

    th {
      color:var(--muted);
      background:var(--panel2);
      font-weight:600;
    }

    tr:last-child td {
      border-bottom:none;
    }

    .cards {
      display:grid;
      grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
      gap:16px;
    }

    .card {
      background:var(--panel);
      border:1px solid var(--line);
      border-left:6px solid var(--blue);
      border-radius:16px;
      padding:18px;
      box-shadow: 0 8px 20px rgba(0,0,0,.18);
    }

    .card.bullish {
      border-left-color:var(--bull);
    }

    .card.bearish {
      border-left-color:var(--bear);
    }

    .card h3 {
      margin:0 0 8px;
      font-size:20px;
    }

    .badges {
      display:flex;
      flex-wrap:wrap;
      gap:8px;
      margin:10px 0 14px;
    }

    .badge {
      display:inline-block;
      padding:4px 9px;
      border-radius:999px;
      background:var(--panel2);
      color:var(--text);
      font-size:12px;
      border:1px solid var(--line);
    }

    .badge.grade-aplus,
    .badge.grade-a {
      background:rgba(245,158,11,.18);
      border-color:rgba(245,158,11,.5);
      color:#fde68a;
    }

    .badge.bullish {
      background:rgba(22,163,74,.16);
      border-color:rgba(22,163,74,.5);
      color:#bbf7d0;
    }

    .badge.bearish {
      background:rgba(220,38,38,.16);
      border-color:rgba(220,38,38,.5);
      color:#fecaca;
    }

    .grid {
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap:10px 16px;
      margin:12px 0;
    }

    .item .k {
      color:var(--muted);
      font-size:12px;
      margin-bottom:2px;
    }

    .item .v {
      font-weight:600;
    }

    .plan {
      color:#d1d5db;
      background:rgba(255,255,255,.04);
      border:1px solid var(--line);
      border-radius:12px;
      padding:12px;
      line-height:1.5;
      margin-top:14px;
    }

    .small {
      color:var(--muted);
      font-size:12px;
    }

    .rr-legend {
      display:flex;
      flex-wrap:wrap;
      gap:8px;
      margin:16px 0 22px;
    }

    .rr-pill {
      font-size:12px;
      border-radius:999px;
      padding:5px 10px;
      border:1px solid var(--line);
      background:var(--panel);
    }

    .rr-excellent {
      color:#bbf7d0;
      border-color:rgba(22,163,74,.65);
      background:rgba(22,163,74,.14);
    }

    .rr-strong {
      color:#d9f99d;
      border-color:rgba(132,204,22,.65);
      background:rgba(132,204,22,.14);
    }

    .rr-acceptable {
      color:#fde68a;
      border-color:rgba(245,158,11,.65);
      background:rgba(245,158,11,.14);
    }

    .rr-watch {
      color:#fed7aa;
      border-color:rgba(249,115,22,.65);
      background:rgba(249,115,22,.14);
    }

    .rr-poor,
    .rr-none {
      color:#fecaca;
      border-color:rgba(220,38,38,.65);
      background:rgba(220,38,38,.12);
    }

    .target-ladder {
      display:grid;
      gap:8px;
      margin-top:8px;
    }

    .target-row {
      padding:8px 10px;
      border-radius:10px;
      border:1px solid var(--line);
      display:grid;
      grid-template-columns: 34px 1fr auto;
      gap:8px;
      align-items:center;
    }

    .target-row em {
      display:block;
      font-style:normal;
      font-size:11px;
      color:var(--muted);
    }

    .target-row small {
      grid-column:2 / span 2;
      color:var(--muted);
      font-size:11px;
    }

    .checklist {
      margin:8px 0 0;
      padding-left:18px;
      line-height:1.55;
    }

    .checklist li {
      margin:2px 0;
    }

    a {
      color:#93c5fd;
    }

    @media (max-width: 720px) {
      .wrap {
        padding:18px;
      }

      .grid {
        grid-template-columns:1fr;
      }

      table {
        display:block;
        overflow-x:auto;
        white-space:nowrap;
      }
    }
  </style>
</head>

<body>
  <main class="wrap">
    <h1>Supply &amp; Demand Scenario Watchlist</h1>

    <p class="sub">
      Generated: 2026-06-28 10:06 PM EDT America/New_York<br>
      Price source: latest delayed OHLCV close<br>
      Final report filter: setup grades A and above, minimum T1 R:R 1:2.50<br>
      Entry-confirmation score is intentionally reserved for backtesting/trade review, not watchlist inclusion.<br>
      Latest OHLCV bar seen: 2026-06-26T15:55:00-04:00, 5M regular-session source
    </p>

    <section class="stats">
      <div class="stat">
        <div class="label">Final setups</div>
        <div class="value">17</div>
      </div>

      <div class="stat">
        <div class="label">All candidates</div>
        <div class="value">299</div>
      </div>

      <div class="stat">
        <div class="label">Bullish / bearish</div>
        <div class="value">7 / 10</div>
      </div>

      <div class="stat">
        <div class="label">Avg. distance</div>
        <div class="value">1.54%</div>
      </div>
    </section>

    <div class="rr-legend">
      <span class="rr-pill rr-excellent">Excellent: 1:4+</span>
      <span class="rr-pill rr-strong">Strong: 1:2.5–1:3.99</span>
      <span class="rr-pill rr-acceptable">Acceptable: 1:2.0–1:2.49</span>
      <span class="rr-pill rr-watch">Watch only: 1:1.5–1:1.99</span>
      <span class="rr-pill rr-poor">Poor: &lt;1:1.5</span>
    </div>

    <h2>Quick View</h2>

    <table>
      <thead>
        <tr>
          <th>Section</th>
          <th>Symbol</th>
          <th>Contract</th>
          <th>Scenario</th>
          <th>Setup Grade</th>
          <th>Zone</th>
          <th>Distance</th>
          <th>T1 R:R Tier</th>
          <th>R:R Range</th>
        </tr>
      </thead>

      <tbody>
        <tr>
          <td>Immediate</td>
          <td><strong>SMCI</strong></td>
          <td>Puts</td>
          <td>Demand Breakdown / Continuation — Puts</td>
          <td>A+</td>
          <td>4H/3H/2H/90m/1H demand $29.94–$30.66</td>
          <td>0.00%</td>
          <td class="rr-strong">1:3.32<br><small>Strong</small></td>
          <td>T1 1:3.32; range 1:3.32–1:5.18</td>
        </tr>

        <tr>
          <td>Immediate</td>
          <td><strong>PLTR</strong></td>
          <td>Puts</td>
          <td>Supply Rejection — Puts</td>
          <td>A+</td>
          <td>4H/3H/2H/90m/1H supply $112.86–$114.35</td>
          <td>0.06%</td>
          <td class="rr-strong">1:2.79<br><small>Strong</small></td>
          <td>T1 1:2.79; range 1:2.79–1:2.79</td>
        </tr>

        <tr>
          <td>Immediate</td>
          <td><strong>SHOP</strong></td>
          <td>Calls</td>
          <td>Supply Breakout / Continuation — Calls</td>
          <td>A</td>
          <td>1D/4H/3H/2H/90m/1H supply $115.88–$118.26</td>
          <td>0.00%</td>
          <td class="rr-strong">1:2.67<br><small>Strong</small></td>
          <td>T1 1:2.67; range 1:2.67–1:6.36</td>
        </tr>

        <tr>
          <td>Immediate</td>
          <td><strong>AMZN</strong></td>
          <td>Calls</td>
          <td>Supply Breakout / Continuation — Calls</td>
          <td>A</td>
          <td>4H/1H supply $229.04–$231.15</td>
          <td>0.00%</td>
          <td class="rr-excellent">1:5.91<br><small>Excellent</small></td>
          <td>T1 1:5.91; range 1:5.91–1:10.63</td>
        </tr>
      </tbody>
    </table>

    <h2>Setup Cards</h2>

    <section class="cards">
      <article class="card bearish">
        <h3>SMCI — Puts</h3>

        <div class="badges">
          <span class="badge bearish">Bearish</span>
          <span class="badge grade-aplus">A+</span>
          <span class="badge">Immediate</span>
        </div>

        <div class="grid">
          <div class="item">
            <div class="k">Scenario</div>
            <div class="v">Demand Breakdown / Continuation</div>
          </div>

          <div class="item">
            <div class="k">Zone</div>
            <div class="v">$29.94–$30.66</div>
          </div>

          <div class="item">
            <div class="k">Distance</div>
            <div class="v">0.00%</div>
          </div>

          <div class="item">
            <div class="k">T1 R:R</div>
            <div class="v">1:3.32</div>
          </div>
        </div>

        <div class="plan">
          Watch for continuation below demand. Prefer confirmation from regular-session 5M structure before entry.
        </div>
      </article>

      <article class="card bearish">
        <h3>PLTR — Puts</h3>

        <div class="badges">
          <span class="badge bearish">Bearish</span>
          <span class="badge grade-aplus">A+</span>
          <span class="badge">Immediate</span>
        </div>

        <div class="grid">
          <div class="item">
            <div class="k">Scenario</div>
            <div class="v">Supply Rejection</div>
          </div>

          <div class="item">
            <div class="k">Zone</div>
            <div class="v">$112.86–$114.35</div>
          </div>

          <div class="item">
            <div class="k">Distance</div>
            <div class="v">0.06%</div>
          </div>

          <div class="item">
            <div class="k">T1 R:R</div>
            <div class="v">1:2.79</div>
          </div>
        </div>

        <div class="plan">
          Watch for failed acceptance above supply and a clean 5M rejection candle.
        </div>
      </article>

      <article class="card bullish">
        <h3>SHOP — Calls</h3>

        <div class="badges">
          <span class="badge bullish">Bullish</span>
          <span class="badge grade-a">A</span>
          <span class="badge">Immediate</span>
        </div>

        <div class="grid">
          <div class="item">
            <div class="k">Scenario</div>
            <div class="v">Supply Breakout / Continuation</div>
          </div>

          <div class="item">
            <div class="k">Zone</div>
            <div class="v">$115.88–$118.26</div>
          </div>

          <div class="item">
            <div class="k">Distance</div>
            <div class="v">0.00%</div>
          </div>

          <div class="item">
            <div class="k">T1 R:R</div>
            <div class="v">1:2.67</div>
          </div>
        </div>

        <div class="plan">
          Watch for continuation through supply with clean acceptance, not just a wick through the level.
        </div>
      </article>

      <article class="card bullish">
        <h3>AMZN — Calls</h3>

        <div class="badges">
          <span class="badge bullish">Bullish</span>
          <span class="badge grade-a">A</span>
          <span class="badge">Immediate</span>
        </div>

        <div class="grid">
          <div class="item">
            <div class="k">Scenario</div>
            <div class="v">Supply Breakout / Continuation</div>
          </div>

          <div class="item">
            <div class="k">Zone</div>
            <div class="v">$229.04–$231.15</div>
          </div>

          <div class="item">
            <div class="k">Distance</div>
            <div class="v">0.00%</div>
          </div>

          <div class="item">
            <div class="k">T1 R:R</div>
            <div class="v">1:5.91</div>
          </div>
        </div>

        <div class="plan">
          Strong R:R setup. Watch for breakout acceptance and avoid chasing if price gaps beyond the zone.
        </div>
      </article>
    </section>

    <p class="small">
      This report is generated from regular-session candles only. Premarket and after-hours data are excluded.
    </p>
  </main>
</body>
</html>
