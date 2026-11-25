# program
プログラム技術の授業で作ったリポジトリ

## index.html のソースコード

```html
<!doctype html>
<html lang="ja">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#f2e7c7">
  <meta name="description" content="鎌ケ谷市をイメージした、学習用の市民向けホームページです。くらしの情報とデジタル市民リテラシーを紹介します。">
  <title>鎌ケ谷市｜梨のあるまち、鎌ケ谷の日々</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Shippori+Mincho:wght@500;600;700&family=Zen+Kaku+Gothic+New:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    :root {
      color-scheme: light;
      --paper: #f4f7f0;
      --ink: #172a25;
      --muted: #62726c;
      --green: #164d3e;
      --mint: #d6efdf;
      --blue: #dcecf4;
      --orange: #e8794e;
      --pear: #f0cf69;
      --pear-paper: #f2e7c7;
      --line: #d9e1d8;
      --serif: "Shippori Mincho", "Yu Mincho", serif;
      --sans: "Zen Kaku Gothic New", "Yu Gothic", sans-serif;
      --mono: "DM Mono", monospace;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; scroll-padding-top: 98px; }
    body {
      margin: 0;
      color: var(--ink);
      background-color: var(--paper);
      background-image: radial-gradient(#bdcbbf 0.6px, transparent 0.6px);
      background-size: 15px 15px;
      font-family: var(--sans);
      font-size: 16px;
      line-height: 1.8;
    }
    body.large-text { font-size: 19px; }
    a { color: inherit; }
    button, input { font: inherit; }
    button, a { -webkit-tap-highlight-color: transparent; }
    a:focus-visible, button:focus-visible, input:focus-visible {
      outline: 3px solid var(--orange);
      outline-offset: 4px;
    }
    .skip-link {
      position: fixed;
      z-index: 20;
      top: 10px;
      left: 10px;
      padding: 8px 14px;
      color: white;
      background: var(--green);
      transform: translateY(-160%);
    }
    .skip-link:focus { transform: translateY(0); }
    .shell { width: min(1200px, calc(100% - 64px)); margin-inline: auto; }

    .site-header {
      position: sticky;
      z-index: 10;
      top: 0;
      border-bottom: 1px solid rgba(23, 42, 37, .1);
      background: rgba(244, 247, 240, .94);
      backdrop-filter: blur(14px);
    }
    .header-inner {
      min-height: 80px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
    }
    .brand { display: flex; align-items: center; gap: 11px; text-decoration: none; flex-shrink: 0; }
    .brand-mark {
      position: relative;
      display: grid;
      width: 41px;
      aspect-ratio: 1;
      place-items: center;
      border-radius: 48% 48% 52% 52% / 43% 43% 57% 57%;
      color: var(--green);
      background: var(--pear);
      font-family: var(--serif);
      font-size: 22px;
    }
    .brand-mark::before { position: absolute; top: -3px; right: 7px; width: 11px; height: 7px; border-radius: 100% 0 100% 0; background: var(--green); content: ""; transform: rotate(-24deg); }
    .brand-name { display: block; font-size: 17px; font-weight: 800; line-height: 1.35; }
    .brand-caption { display: block; color: var(--muted); font-family: var(--mono); font-size: 10px; letter-spacing: 0; }
    .main-nav { display: flex; align-items: center; gap: clamp(13px, 2.2vw, 29px); }
    .main-nav a { font-size: 13px; font-weight: 700; text-decoration: none; white-space: nowrap; }
    .main-nav a:hover { color: var(--green); text-decoration: underline; text-underline-offset: 5px; }
    .header-actions { display: flex; align-items: center; gap: 8px; flex-shrink: 0; }
    .utility-button {
      min-height: 39px;
      padding: 5px 11px;
      border: 1px solid var(--line);
      border-radius: 3px;
      color: var(--ink);
      background: transparent;
      cursor: pointer;
      font-size: 12px;
      font-weight: 700;
    }
    .utility-button:hover { border-color: var(--green); background: white; }
    .menu-button { display: none; }

    .prototype-note {
      padding: 7px 16px;
      color: #fff;
      background: var(--green);
      text-align: center;
      font-size: 12px;
    }
    .prototype-note strong { color: #b7efcc; }
    .hero {
      position: relative;
      min-height: 500px;
      display: flex;
      align-items: center;
      margin-top: 24px;
      overflow: hidden;
      color: white;
      background: #35533c;
      isolation: isolate;
    }
    .hero::before {
      position: absolute;
      z-index: -2;
      inset: 0;
      background: url("https://thumb.wikimedia.org/wikipedia/commons/thumb/c/cd/Kamagaya-daibutsu03.jpg/1920px-Kamagaya-daibutsu03.jpg") center 24% / cover;
      content: "";
      animation: arrive 1s ease-out both;
    }
    .hero::after {
      position: absolute;
      z-index: -1;
      inset: 0;
      background: linear-gradient(90deg, rgba(14, 42, 33, .88) 0%, rgba(14, 42, 33, .73) 43%, rgba(14, 42, 33, .12) 100%), linear-gradient(0deg, rgba(14, 42, 33, .2), transparent 40%);
      content: "";
    }
    .hero-content { width: min(670px, 75%); padding: 65px 0 70px 7%; animation: rise .75s .1s both; }
    .eyebrow { display: flex; align-items: center; gap: 12px; margin: 0 0 16px; font-family: var(--mono); font-size: 11px; letter-spacing: 0; }
    .eyebrow::before { width: 28px; height: 1px; background: #a4d5b2; content: ""; }
    .hero h1 { margin: 0; font-family: var(--serif); font-size: clamp(38px, 5.2vw, 65px); font-weight: 600; line-height: 1.46; }
    .hero h1 span { color: var(--pear); }
    .hero-copy { max-width: 470px; margin: 17px 0 26px; color: rgba(255,255,255,.9); font-size: 15px; }
    .hero-actions { display: flex; flex-wrap: wrap; align-items: center; gap: 10px; }
    .hero-link {
      display: inline-flex;
      align-items: center;
      gap: 20px;
      min-height: 49px;
      padding: 0 17px;
      color: var(--ink);
      background: #fff;
      font-size: 13px;
      font-weight: 800;
      text-decoration: none;
    }
    .hero-link-secondary { display: inline-flex; min-height: 49px; align-items: center; gap: 10px; padding: 0 15px; border: 1px solid rgba(255,255,255,.6); color: white; font-size: 13px; font-weight: 700; text-decoration: none; transition: background .2s ease; }
    .hero-link-secondary:hover { background: rgba(255,255,255,.14); }
    .hero-link span { color: var(--green); font-size: 20px; transition: transform .2s ease; }
    .hero-link:hover span { transform: translateX(4px); }
    .hero-link-secondary span { font-size: 17px; transition: transform .2s ease; }
    .hero-link-secondary:hover span { transform: translateX(3px); }
    .hero-caption { position: absolute; right: 19px; bottom: 12px; color: rgba(255,255,255,.88); font-family: var(--mono); font-size: 10px; text-decoration: none; text-underline-offset: 3px; }
    .hero-caption:hover { text-decoration: underline; }
    .local-story { background: var(--pear-paper); }
    .local-story-inner { display: grid; grid-template-columns: .8fr 1fr 1.1fr; align-items: center; gap: 30px; padding-block: 25px; }
    .local-story-kicker { margin: 0 0 5px; color: var(--green); font-family: var(--mono); font-size: 10px; }
    .local-story h2 { margin: 0; font-family: var(--serif); font-size: 22px; font-weight: 600; line-height: 1.55; }
    .local-story-copy { margin: 0; color: #43584e; font-size: 12px; }
    .local-highlights { display: flex; flex-wrap: wrap; gap: 8px 16px; margin: 0; padding: 0; list-style: none; }
    .local-highlights li { display: flex; align-items: center; gap: 7px; font-size: 11px; font-weight: 700; }
    .local-highlights li::before { width: 7px; height: 7px; border-radius: 50%; background: var(--orange); content: ""; }

    .search-section {
      display: grid;
      grid-template-columns: 1fr minmax(280px, 500px);
      align-items: center;
      gap: 25px;
      padding-block: 27px;
      border-bottom: 1px solid var(--line);
    }
    .search-title { margin: 0; font-family: var(--serif); font-size: 20px; }
    .search-hint { display: block; color: var(--muted); font-size: 11px; }
    .search-form { display: flex; min-height: 48px; border: 1px solid #b9c9bd; background: #fff; }
    .search-form input { width: 100%; min-width: 0; padding: 0 15px; border: 0; color: var(--ink); background: transparent; font-size: 14px; }
    .search-form button { width: 51px; flex-shrink: 0; border: 0; color: white; background: var(--green); cursor: pointer; font-size: 21px; }
    .search-shortcuts { grid-column: 1 / -1; display: flex; flex-wrap: wrap; align-items: center; gap: 8px; margin-top: -13px; }
    .search-shortcut-label { margin-right: 3px; color: var(--muted); font-size: 11px; font-weight: 700; }
    .search-shortcuts a { padding: 5px 11px; border: 1px solid var(--line); border-radius: 999px; background: rgba(255,255,255,.65); font-size: 11px; text-decoration: none; transition: border-color .2s ease, background .2s ease; }
    .search-shortcuts a:hover { border-color: var(--green); background: white; }
    .search-results { grid-column: 1 / -1; margin: 0; color: var(--green); font-size: 13px; }
    [hidden] { display: none !important; }

    .section { padding-block: 65px; }
    .section-heading { display: flex; align-items: end; justify-content: space-between; gap: 20px; margin-bottom: 27px; }
    .section-kicker { margin: 0 0 6px; color: var(--green); font-family: var(--mono); font-size: 11px; letter-spacing: 0; }
    .section-title { margin: 0; font-family: var(--serif); font-size: clamp(25px, 3vw, 34px); font-weight: 600; line-height: 1.5; }
    .section-description { max-width: 480px; margin: 0; color: var(--muted); font-size: 13px; }
    .service-grid { display: grid; grid-template-columns: repeat(4, 1fr); border-top: 1px solid var(--line); border-left: 1px solid var(--line); }
    .service-card {
      position: relative;
      min-height: 174px;
      padding: 22px 20px;
      border-right: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
      background: rgba(255,255,255,.65);
      text-decoration: none;
      transition: background .2s ease, transform .2s ease;
    }
    .service-card:hover { z-index: 1; background: white; transform: translateY(-3px); }
    .service-number { color: var(--green); font-family: var(--mono); font-size: 11px; }
    .service-card[data-external] .service-arrow { font-family: var(--sans); font-size: 10px; font-weight: 700; }
    .service-icon { position: absolute; top: 20px; right: 19px; display: grid; width: 39px; aspect-ratio: 1; place-items: center; border-radius: 50%; background: var(--mint); font-size: 18px; }
    .service-card:nth-child(even) .service-icon { background: #fbe4d9; }
    .service-card h3 { margin: 26px 0 5px; font-family: var(--serif); font-size: 17px; }
    .service-card p { margin: 0; color: var(--muted); font-size: 12px; }
    .service-arrow { position: absolute; right: 19px; bottom: 14px; color: var(--green); font-size: 18px; }

    .digital-section { padding-block: 63px; color: white; background: var(--green); }
    .digital-layout { display: grid; grid-template-columns: .87fr 1.13fr; gap: 7%; align-items: center; }
    .digital-kicker { margin: 0 0 11px; color: #b7efcc; font-family: var(--mono); font-size: 11px; }
    .digital-section h2 { margin: 0; font-family: var(--serif); font-size: clamp(27px, 3.4vw, 41px); font-weight: 500; line-height: 1.55; }
    .digital-intro { max-width: 410px; margin: 17px 0 0; color: rgba(255,255,255,.78); font-size: 13px; }
    .digital-steps { display: grid; grid-template-columns: repeat(3, 1fr); gap: 11px; }
    .digital-step { min-height: 170px; padding: 18px 15px; border-top: 2px solid #a4d5b2; background: rgba(255,255,255,.08); }
    .digital-step:nth-child(2) { border-color: #f1aa78; }
    .digital-step:nth-child(3) { border-color: #9dc5df; }
    .step-number { color: #b7efcc; font-family: var(--mono); font-size: 11px; }
    .digital-step h3 { margin: 15px 0 7px; font-family: var(--serif); font-size: 16px; }
    .digital-step p { margin: 0; color: rgba(255,255,255,.78); font-size: 11px; line-height: 1.8; }
    .digital-reminder { margin: 17px 0 0; color: #d7ecdf; font-size: 11px; }

    .news-section { padding-block: 63px 75px; }
    .news-heading { display: flex; align-items: center; gap: 12px; }
    .news-count { display: inline-flex; min-width: 35px; min-height: 25px; align-items: center; justify-content: center; margin-left: 9px; padding: 0 8px; border: 1px solid var(--line); border-radius: 999px; color: var(--muted); font-family: var(--mono); font-size: 10px; vertical-align: middle; }
    .news-description { display: flex; align-items: center; gap: 10px; padding: 11px 14px; border: 1px solid var(--line); background: rgba(255,255,255,.65); }
    .news-demo { flex-shrink: 0; padding: 3px 7px; color: white; background: var(--green); font-family: var(--mono); font-size: 9px; }
    .news-list { display: grid; gap: 11px; }
    .news-item { display: grid; grid-template-columns: 58px 84px minmax(0, 1fr) auto; align-items: center; gap: 17px; min-height: 91px; padding: 14px 19px; border: 1px solid var(--line); border-left: 3px solid var(--green); background: rgba(255,255,255,.72); text-decoration: none; transition: background .2s ease, border-color .2s ease, transform .2s ease; }
    .news-item:hover { border-color: #b7c9bc; border-left-color: var(--orange); background: white; transform: translateX(3px); }
    .news-date { display: grid; width: 52px; aspect-ratio: 1; align-content: center; justify-items: center; border-radius: 50%; color: var(--green); background: var(--mint); font-family: var(--mono); font-size: 11px; font-weight: 500; }
    .news-date-mark { color: var(--muted); font-size: 7px; letter-spacing: .04em; }
    .news-label { width: max-content; padding: 3px 9px; color: var(--green); background: var(--mint); font-size: 10px; font-weight: 700; }
    .news-item:nth-child(2) .news-label { color: #8d4b28; background: #fbe4d9; }
    .news-item:nth-child(3) .news-label { color: #315d78; background: var(--blue); }
    .news-copy { min-width: 0; }
    .news-title { margin: 0; font-size: 14px; font-weight: 700; }
    .news-summary { margin: 3px 0 0; color: var(--muted); font-size: 11px; }
    .news-action { display: flex; align-items: center; gap: 9px; color: var(--green); font-size: 11px; font-weight: 700; white-space: nowrap; }
    .news-action span { display: grid; width: 27px; aspect-ratio: 1; place-items: center; border: 1px solid var(--line); border-radius: 50%; font-size: 16px; transition: color .2s ease, background .2s ease; }
    .news-item:hover .news-action span { color: white; background: var(--green); }
    .detail-dialog { width: min(520px, calc(100% - 32px)); max-height: min(80vh, 620px); padding: 28px; border: 1px solid var(--line); color: var(--ink); background: var(--paper); }
    .detail-dialog::backdrop { background: rgba(14, 35, 29, .62); backdrop-filter: blur(3px); }
    .dialog-topline { display: flex; align-items: center; justify-content: space-between; gap: 12px; }
    .dialog-kicker { margin: 0; color: var(--green); font-family: var(--mono); font-size: 10px; }
    .dialog-close { min-width: 44px; min-height: 44px; border: 1px solid var(--line); color: var(--ink); background: white; cursor: pointer; font-size: 13px; }
    .dialog-close:hover { border-color: var(--green); }
    .detail-dialog h2 { margin: 18px 0 8px; font-family: var(--serif); font-size: 25px; line-height: 1.5; }
    .dialog-content { margin: 0; color: #43584e; font-size: 14px; }
    .dialog-note { margin: 22px 0 0; padding-top: 13px; border-top: 1px solid var(--line); color: var(--muted); font-size: 11px; }

    .site-footer { padding-block: 28px; color: white; background: #122f28; }
    .footer-inner { display: flex; align-items: center; justify-content: space-between; gap: 20px; }
    .footer-brand { font-family: var(--serif); font-size: 16px; font-weight: 600; }
    .footer-note { margin: 3px 0 0; color: rgba(255,255,255,.66); font-size: 11px; }
    .footer-links { display: flex; gap: 18px; font-size: 11px; }
    .footer-links a { color: white; text-underline-offset: 4px; }
    .page-pagination { display: flex; align-items: center; justify-content: center; gap: 8px; padding-block: 4px 38px; }
    .page-number, .page-next { display: inline-flex; min-height: 40px; align-items: center; justify-content: center; border: 1px solid var(--line); background: rgba(255,255,255,.75); font-size: 12px; font-weight: 700; text-decoration: none; }
    .page-number { min-width: 40px; }
    .page-number[aria-current="page"] { border-color: var(--green); color: white; background: var(--green); }
    .page-next { gap: 8px; padding-inline: 13px; }
    .page-number[href]:hover, .page-next:hover { border-color: var(--green); background: white; }
    .page-number[aria-current="page"]:hover { color: white; background: var(--green); }

    @keyframes rise { from { opacity: 0; transform: translateY(12px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes arrive { from { opacity: .6; transform: scale(1.035); } to { opacity: 1; transform: scale(1); } }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { scroll-behavior: auto !important; animation-duration: .01ms !important; animation-iteration-count: 1 !important; transition-duration: .01ms !important; }
    }
    @media (max-width: 920px) {
      .shell { width: min(100% - 40px, 720px); }
      .header-inner { min-height: 72px; }
      .main-nav { display: none; position: absolute; top: 71px; left: 0; right: 0; padding: 12px 20px 20px; border-bottom: 1px solid var(--line); background: var(--paper); }
      .main-nav.is-open { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0; }
      .main-nav a { padding: 12px 4px; border-bottom: 1px solid var(--line); }
      .menu-button { display: inline-flex; align-items: center; gap: 5px; }
      .hero { min-height: 410px; }
      .hero-content { width: 83%; padding-left: 6%; }
      .local-story-inner { grid-template-columns: 1fr 1.2fr; gap: 12px 24px; }
      .local-highlights { grid-column: 1 / -1; }
      .service-grid { grid-template-columns: repeat(2, 1fr); }
      .digital-layout { grid-template-columns: 1fr; gap: 29px; }
      .digital-intro { max-width: 600px; }
    }
    @media (max-width: 560px) {
      html { scroll-padding-top: 78px; }
      .shell { width: calc(100% - 32px); }
      .brand-name { font-size: 15px; }
      .brand-caption { font-size: 9px; }
      .brand-mark { width: 36px; font-size: 19px; }
      .header-actions { gap: 5px; }
      .utility-button { min-height: 36px; padding: 4px 8px; font-size: 11px; }
      .prototype-note { font-size: 10px; }
      .hero { min-height: 435px; margin-top: 14px; }
      .hero::after { background: linear-gradient(90deg, rgba(14,44,35,.88), rgba(14,44,35,.58)); }
      .hero-content { width: 100%; padding: 40px 22px 55px; }
      .hero h1 { font-size: 40px; }
      .hero-copy { font-size: 13px; }
      .hero-caption { right: 10px; font-size: 9px; }
      .local-story-inner { grid-template-columns: 1fr; gap: 9px; padding-block: 20px; }
      .local-story h2 { font-size: 20px; }
      .local-highlights { grid-column: auto; gap: 7px 14px; }
      .search-section { grid-template-columns: 1fr; gap: 12px; padding-block: 21px; }
      .search-title { font-size: 18px; }
      .search-shortcuts { gap: 7px; margin-top: 0; }
      .search-shortcut-label { flex-basis: 100%; }
      .search-results { margin-top: 0; }
      .section { padding-block: 46px; }
      .section-heading { display: block; margin-bottom: 20px; }
      .section-description { margin-top: 8px; }
      .service-card { min-height: 160px; padding: 17px 13px; }
      .service-card h3 { max-width: 125px; margin-top: 27px; font-size: 15px; }
      .service-card p { max-width: 145px; font-size: 11px; }
      .service-icon { top: 14px; right: 12px; width: 34px; }
      .digital-section { padding-block: 45px; }
      .digital-steps { grid-template-columns: 1fr; gap: 8px; }
      .digital-step { min-height: 0; padding: 14px; }
      .digital-step h3 { margin: 5px 0; }
      .news-section { padding-block: 45px 52px; }
      .news-heading { gap: 7px; }
      .news-description { align-items: flex-start; font-size: 11px; }
      .news-item { grid-template-columns: auto minmax(0, 1fr) auto; gap: 7px 9px; padding: 12px; }
      .news-date { grid-column: 1; grid-row: 1; width: auto; min-height: 22px; aspect-ratio: auto; padding: 0 8px; border-radius: 999px; font-size: 9px; }
      .news-date-mark { display: none; }
      .news-label { grid-column: 2; grid-row: 1; }
      .news-copy { grid-column: 1 / 3; grid-row: 2; }
      .news-title { font-size: 12px; }
      .news-summary { font-size: 10px; }
      .news-action { grid-column: 3; grid-row: 1 / 3; gap: 0; font-size: 0; }
      .news-action span { width: 25px; }
      .detail-dialog { padding: 21px; }
      .detail-dialog h2 { font-size: 22px; }
      .footer-inner { align-items: flex-start; flex-direction: column; }
      .footer-links { flex-wrap: wrap; gap: 9px 16px; }
    }
  </style>
</head>
<body>
  <a class="skip-link" href="#main">本文へ移動</a>
  <header class="site-header">
    <div class="shell header-inner">
      <a class="brand" href="#top" aria-label="鎌ケ谷市トップ">
        <span class="brand-mark" aria-hidden="true">か</span>
        <span><span class="brand-name">鎌ケ谷市</span><span class="brand-caption">CHIBA / PEAR TOWN</span></span>
      </a>
      <nav class="main-nav" id="main-nav" aria-label="メインメニュー">
        <a href="#local-story">鎌ケ谷の魅力</a>
        <a href="spots.html">おすすめスポット</a>
        <a href="#services">くらしの手続き</a>
        <a href="#safety">安全・安心</a>
        <a href="#digital">デジタルとのつきあい方</a>
        <a href="#news">お知らせ</a>
      </nav>
      <div class="header-actions">
        <button class="utility-button" id="text-size" type="button" aria-pressed="false" aria-label="文字を大きくする">文字サイズ A+</button>
        <button class="utility-button menu-button" id="menu-toggle" type="button" aria-expanded="false" aria-controls="main-nav">メニュー</button>
      </div>
    </div>
  </header>

  <div class="prototype-note"><strong>学習用プロトタイプ</strong>｜このページは授業課題の見本です。実際の市の公式情報・発表ではありません。</div>

  <main id="main">
    <section class="shell hero" id="top" aria-labelledby="hero-title">
      <div class="hero-content">
        <p class="eyebrow">CHIBA / KAMAGAYA</p>
        <h1 id="hero-title">梨のあるまち、<br><span>鎌ケ谷。</span></h1>
        <p class="hero-copy">大仏さまのそばに、梨畑がひろがるまち。季節の魅力も、毎日の暮らしの情報も、ここから。</p>
        <div class="hero-actions">
          <a class="hero-link" href="#services">くらしの情報を探す <span aria-hidden="true">→</span></a>
          <a class="hero-link-secondary" href="#news">お知らせを見る <span aria-hidden="true">↘</span></a>
        </div>
      </div>
      <a class="hero-caption" href="https://commons.wikimedia.org/wiki/File:Kamagaya-daibutsu03.jpg" target="_blank" rel="noreferrer">鎌ケ谷大仏 / Wikimedia Commons / CC0</a>
    </section>

    <section class="local-story" id="local-story" aria-labelledby="local-story-title">
      <div class="shell local-story-inner">
        <div>
          <p class="local-story-kicker">A LITTLE CLOSER TO KAMAGAYA</p>
          <h2 id="local-story-title">梨の季節、まちの風景。</h2>
        </div>
        <p class="local-story-copy">畑の実りや鎌ケ谷大仏のたたずまい。身近な風景の魅力と、まちで暮らす人に役立つ情報をお届けします。</p>
        <ul class="local-highlights" aria-label="鎌ケ谷の見どころ">
          <li>梨の実り</li>
          <li>鎌ケ谷大仏</li>
          <li>まちの四季</li>
        </ul>
      </div>
    </section>

    <section class="shell search-section" aria-labelledby="search-title">
      <div>
        <h2 class="search-title" id="search-title">知りたいことから探す</h2>
        <span class="search-hint">例：ごみ、防災、子育て、情報の確認</span>
      </div>
      <form class="search-form" id="site-search" role="search">
        <input id="search-input" type="search" placeholder="キーワードを入力" aria-label="サイト内を検索">
        <button type="submit" aria-label="検索する">⌕</button>
      </form>
      <nav class="search-shortcuts" aria-label="よく見られる情報">
        <span class="search-shortcut-label">よく見られる情報</span>
        <a href="#services">手続き・申請</a>
        <a href="#services">子育て・教育</a>
        <a href="#safety">防災・安全</a>
        <a href="spots.html">おすすめスポット</a>
        <a href="#digital">デジタル生活</a>
      </nav>
      <p class="search-results" id="search-results" role="status" aria-live="polite" hidden></p>
    </section>

    <section class="shell section" id="services" aria-labelledby="services-title">
      <div class="section-heading">
        <div>
          <p class="section-kicker">LIFE &amp; CITY</p>
          <h2 class="section-title" id="services-title">くらしの情報</h2>
        </div>
        <p class="section-description">必要な情報に、迷わずたどり着けるように。目的に合わせた入口をまとめました。</p>
      </div>
      <div class="service-grid">
        <a class="service-card" href="https://www.city.kamagaya.chiba.jp/kurashi-tetsuzuki/todokede/kakushushoumei.html" target="_blank" rel="noopener noreferrer" data-external data-search="届け出 手続き 引っ越し 住民票">
          <span class="service-number">01 / PROCEDURES</span><span class="service-icon" aria-hidden="true">▤</span>
          <h3>届け出・手続き</h3><p>引っ越しや証明書など</p><span class="service-arrow" aria-hidden="true">公式サイト ↗</span>
        </a>
        <a class="service-card" href="https://www.city.kamagaya.chiba.jp/kurashi/kosodate_kyoiku.html" target="_blank" rel="noopener noreferrer" data-external data-search="子育て 教育 子ども 学校">
          <span class="service-number">02 / FAMILY</span><span class="service-icon" aria-hidden="true">♡</span>
          <h3>子育て・教育</h3><p>子どもと家庭のくらし</p><span class="service-arrow" aria-hidden="true">公式サイト ↗</span>
        </a>
        <a class="service-card" href="https://www.city.kamagaya.chiba.jp/anzen_anshin/bousai/index.html" target="_blank" rel="noopener noreferrer" data-external data-search="防災 安全 安心 災害 避難">
          <span class="service-number">03 / SAFETY</span><span class="service-icon" aria-hidden="true">＋</span>
          <h3>安全・安心</h3><p>防災の備えと情報の確認</p><span class="service-arrow" aria-hidden="true">公式サイト ↗</span>
        </a>
        <a class="service-card" href="https://www.soumu.go.jp/use_the_internet_wisely/" target="_blank" rel="noopener noreferrer" data-external data-search="デジタル ネット SNS 情報 確認 個人情報">
          <span class="service-number">04 / DIGITAL LIFE</span><span class="service-icon" aria-hidden="true">◎</span>
          <h3>デジタルとのつきあい方</h3><p>安心して使うためのヒント</p><span class="service-arrow" aria-hidden="true">総務省 ↗</span>
        </a>
      </div>
    </section>

    <section class="digital-section" id="digital" aria-labelledby="digital-title">
      <div class="shell digital-layout">
        <div>
          <p class="digital-kicker">DIGITAL CITIZENSHIP</p>
          <h2 id="digital-title">画面の向こうにも、<br>ひとりの人がいる。</h2>
          <p class="digital-intro">ネットを使う力は、自分と誰かを大切にする力。情報を受け取るときも、発信するときも、ちょっと立ち止まる習慣を。</p>
        </div>
        <div>
          <div class="digital-steps">
            <article class="digital-step" data-search="情報 ニュース 災害 確認 出典">
              <span class="step-number">01 / CHECK</span><h3>出典を確かめる</h3><p>見出しだけで決めず、発信元・日付・公式情報を確認する。</p>
            </article>
            <article class="digital-step" data-search="個人情報 写真 位置情報 プライバシー">
              <span class="step-number">02 / PROTECT</span><h3>個人情報を守る</h3><p>写真や投稿に住所、顔、位置情報が写っていないか見直す。</p>
            </article>
            <article class="digital-step" data-search="思いやり SNS コメント 誹謗中傷 対話">
              <span class="step-number">03 / RESPECT</span><h3>相手を思いやる</h3><p>送る前に読み返す。困ったときは一人で抱えず相談する。</p>
            </article>
          </div>
          <p class="digital-reminder">災害や緊急時は、うわさを広げる前に自治体などの公式発表を確認しましょう。</p>
        </div>
      </div>
    </section>

    <section class="shell section" id="safety" aria-labelledby="safety-title">
      <div class="section-heading">
        <div>
          <p class="section-kicker">SAFETY &amp; INFORMATION</p>
          <h2 class="section-title" id="safety-title">大切な情報こそ、確かめて。</h2>
        </div>
        <p class="section-description">災害や安全に関する情報を見かけたら、発信元と更新日時をチェック。未確認の情報は、そのまま転送しないことも大切です。</p>
      </div>
      <div class="service-grid">
        <a class="service-card" href="https://www.city.kamagaya.chiba.jp/anzen_anshin/bousai/index.html" target="_blank" rel="noopener noreferrer" data-external data-search="災害 防災 避難 情報 公式 確認">
          <span class="service-number">BEFORE SHARING</span><span class="service-icon" aria-hidden="true">⌕</span>
          <h3>発信元はどこ？</h3><p>公式サイトなど一次情報を確認</p><span class="service-arrow" aria-hidden="true">鎌ケ谷市 ↗</span>
        </a>
        <a class="service-card" href="https://www.bousai.pref.chiba.lg.jp/" target="_blank" rel="noopener noreferrer" data-external data-search="日時 更新 日付 情報 古い">
          <span class="service-number">CHECK THE DATE</span><span class="service-icon" aria-hidden="true">◷</span>
          <h3>いつの情報？</h3><p>日付や更新時刻を確かめる</p><span class="service-arrow" aria-hidden="true">千葉県 ↗</span>
        </a>
        <a class="service-card" href="https://www.soumu.go.jp/use_the_internet_wisely/" target="_blank" rel="noopener noreferrer" data-external data-search="拡散 うわさ SNS 転送 災害">
          <span class="service-number">PAUSE &amp; THINK</span><span class="service-icon" aria-hidden="true">Ⅱ</span>
          <h3>広げる前にひと呼吸</h3><p>確かでない情報は転送しない</p><span class="service-arrow" aria-hidden="true">総務省 ↗</span>
        </a>
        <a class="service-card" href="https://www.moj.go.jp/JINKEN/jinken113.html" target="_blank" rel="noopener noreferrer" data-external data-search="相談 困った 誹謗中傷 相談窓口">
          <span class="service-number">ASK FOR HELP</span><span class="service-icon" aria-hidden="true">✳</span>
          <h3>困ったら相談</h3><p>信頼できる人に話してみる</p><span class="service-arrow" aria-hidden="true">法務省 ↗</span>
        </a>
      </div>
    </section>

    <section class="shell news-section" id="news" aria-labelledby="news-title">
      <div class="section-heading">
        <div>
          <p class="section-kicker">NOTICE BOARD</p>
          <h2 class="section-title news-heading" id="news-title">お知らせ<span class="news-count">03</span></h2>
        </div>
        <p class="section-description news-description"><span class="news-demo">SAMPLE</span>実際の市政情報ではなく、ページ構成を示す掲載例です。</p>
      </div>
      <div class="news-list">
        <a class="news-item" href="#news" data-search="手続き 見本 申請" data-detail="市からのお知らせを掲載する欄の見本です。実際のお知らせではありません。">
          <span class="news-date">見本<span class="news-date-mark">SAMPLE</span></span><span class="news-label">手続き</span><div class="news-copy"><h3 class="news-title">手続き案内の掲載イメージ</h3><p class="news-summary">申請や届出など、くらしの手続き情報を案内します。</p></div><span class="news-action">詳しく見る<span aria-hidden="true">›</span></span>
        </a>
        <a class="news-item" href="#news" data-search="防災 見本 公式情報 確認" data-detail="防災情報を案内する欄の見本です。緊急時は自治体などの公式発表を確認してください。">
          <span class="news-date">見本<span class="news-date-mark">SAMPLE</span></span><span class="news-label">防災</span><div class="news-copy"><h3 class="news-title">防災情報への案内掲載イメージ</h3><p class="news-summary">日ごろの備えや、公式情報の確認先を紹介します。</p></div><span class="news-action">詳しく見る<span aria-hidden="true">›</span></span>
        </a>
        <a class="news-item" href="#news" data-search="デジタル 情報 確認 SNS 見本" data-detail="情報の確認方法を紹介するお知らせの見本です。共有する前に発信元や日付を確かめることが大切です。">
          <span class="news-date">見本<span class="news-date-mark">SAMPLE</span></span><span class="news-label">デジタル</span><div class="news-copy"><h3 class="news-title">ネット上の情報を確かめるヒント</h3><p class="news-summary">共有する前に、発信元や日付をチェック。</p></div><span class="news-action">詳しく見る<span aria-hidden="true">›</span></span>
        </a>
      </div>
    </section>
    <nav class="page-pagination shell" aria-label="ページ送り">
      <span class="page-number" aria-current="page" aria-label="1ページ目、現在のページ">1</span>
      <a class="page-number" href="spots.html" aria-label="2ページ目、おすすめスポット">2</a>
      <a class="page-next" href="spots.html">次のページ <span aria-hidden="true">→</span></a>
    </nav>
  </main>

  <footer class="site-footer">
    <div class="shell footer-inner">
      <div><div class="footer-brand">鎌ケ谷市｜まちの情報と、たしかなつながり</div><p class="footer-note">学校の授業課題として作成した学習用プロトタイプです。掲載内容は実際の市政情報ではありません。</p></div>
      <nav class="footer-links" aria-label="フッターメニュー"><a href="#top">ページの先頭へ ↑</a><a href="spots.html">おすすめスポット</a><a href="#digital">デジタル市民リテラシー</a><a href="#services">くらしの情報</a></nav>
    </div>
  </footer>

  <dialog class="detail-dialog" id="detail-dialog" aria-labelledby="dialog-title">
    <div class="dialog-topline">
      <p class="dialog-kicker">KAMAGAYA / INFORMATION</p>
      <button class="dialog-close" id="dialog-close" type="button" aria-label="詳細を閉じる">閉じる</button>
    </div>
    <h2 id="dialog-title"></h2>
    <p class="dialog-content" id="dialog-content"></p>
    <p class="dialog-note">学習用プロトタイプの掲載例です。実際の制度・窓口・緊急情報ではありません。</p>
  </dialog>

  <script>
    const textSizeButton = document.querySelector("#text-size");
    textSizeButton.addEventListener("click", () => {
      const enlarged = document.body.classList.toggle("large-text");
      textSizeButton.setAttribute("aria-pressed", String(enlarged));
      textSizeButton.setAttribute("aria-label", enlarged ? "標準の文字サイズにする" : "文字を大きくする");
    });

    const menuButton = document.querySelector("#menu-toggle");
    const mainNav = document.querySelector("#main-nav");
    menuButton.addEventListener("click", () => {
      const expanded = menuButton.getAttribute("aria-expanded") !== "true";
      menuButton.setAttribute("aria-expanded", String(expanded));
      menuButton.textContent = expanded ? "閉じる" : "メニュー";
      mainNav.classList.toggle("is-open", expanded);
    });
    mainNav.addEventListener("click", (event) => {
      if (event.target.closest("a")) {
        mainNav.classList.remove("is-open");
        menuButton.setAttribute("aria-expanded", "false");
        menuButton.textContent = "メニュー";
      }
    });

    const detailDialog = document.querySelector("#detail-dialog");
    const dialogTitle = document.querySelector("#dialog-title");
    const dialogContent = document.querySelector("#dialog-content");
    document.querySelectorAll(".service-card:not([data-external]), .news-item").forEach((link) => {
      link.addEventListener("click", (event) => {
        event.preventDefault();
        dialogTitle.textContent = link.querySelector("h3").textContent;
        dialogContent.textContent = link.dataset.detail;
        detailDialog.showModal();
      });
    });
    document.querySelector("#dialog-close").addEventListener("click", () => detailDialog.close());
    detailDialog.addEventListener("click", (event) => {
      if (event.target === detailDialog) detailDialog.close();
    });

    const searchableItems = [...document.querySelectorAll("[data-search]")];
    const searchForm = document.querySelector("#site-search");
    const searchInput = document.querySelector("#search-input");
    const searchResults = document.querySelector("#search-results");
    searchForm.addEventListener("submit", (event) => {
      event.preventDefault();
      const query = searchInput.value.trim().toLocaleLowerCase("ja");
      searchableItems.forEach((item) => {
        item.hidden = Boolean(query) && !`${item.textContent} ${item.dataset.search}`.toLocaleLowerCase("ja").includes(query);
      });
      if (!query) {
        searchResults.textContent = "キーワードを入力してください。";
      } else {
        const count = searchableItems.filter((item) => !item.hidden).length;
        searchResults.textContent = count ? `「${searchInput.value.trim()}」に関連する項目を ${count} 件表示しています。` : `「${searchInput.value.trim()}」に一致する項目はありません。別のキーワードをお試しください。`;
      }
      searchResults.hidden = false;
    });
    searchInput.addEventListener("input", () => {
      if (!searchInput.value.trim()) {
        searchableItems.forEach((item) => { item.hidden = false; });
        searchResults.hidden = true;
      }
    });
  </script>
</body>
</html>
```
