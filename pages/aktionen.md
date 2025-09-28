---
layout: default
transition: slide-down
---

<Timeline
  v-motion
  :initial="{ x: -430 }"
  :enter="{ x: -430 }"
  :click-1="{ x: -1380 }"
  title="Oktober 2025"
  heading="Spendenlauf"
  description="Die gesammelten Spenden gehen an eine gemeinnützige Organisation eurer Wahl."
/>

<Timeline
  v-click
  v-motion
  :initial="{ x: 950 }"
  :enter="{ x: -430 }"
  :click-2="{ x: -1380 }"
  title="Dezember 2025"
  heading="Weihnachtspäckchenaktion"
  description="Wir sammeln und verpacken Geschenke für Bedürftige zu Weihnachten."
/>

<Timeline
  v-click
  v-motion
  :initial="{ x: 950 }"
  :enter="{ x: -430 }"
  :click-3="{ x: -1380 }"
  title="06. Dezember 2025"
  heading="Nikolausaktion"
  description="Schokolade und kleine Überraschungen für die Unterstufe."
/>

<Timeline
  v-click
  v-motion
  :initial="{ x: 950 }"
  :enter="{ x: -430 }"
  :click-4="{ x: -1380 }"
  title="Februar 2026"
  heading="Fasching"
  description="Faschingsfeier, organisiert mit den Patenklassen."
/>

<Timeline
  v-click
  v-motion
  :initial="{ x: 950 }"
  :enter="{ x: -430 }"
  :click-5="{ x: -1380 }"
  title="14. Februar 2026"
  heading="Valentinstag"
  description="Rosenverkauf am Pausenhof."
/>

<Timeline
  v-click
  v-motion
  :initial="{ x: 950 }"
  :enter="{ x: -430 }"
  :click-6="{ x: -1380 }"
  title="Mai 2026"
  heading="Bunsencup"
  description="Fußballturnier mit anderen Heidelberger Schulen."
/>
