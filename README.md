<h1 align="center">A Precision Livestock Health Framework for Herd Health Monitoring from Cloud-Integrated Wearable Sensor Data</h1>


<h3 align="center">Asad Prodhan<sup>*</sup></h3>


<div align="center"><b> School of Veterinary Medicine, Murdoch University </b></div>


<div align="center"><b> 90 South St, Murdoch WA 6150, Australia. <sup>*</sup>Correspondence: Asad.Prodhan@murdoch.edu.au </b></div>


<br />


<p align="center">
  <a href="https://github.com/asadprodhan/plh-behavioral-earlywarning-demo/tree/main#GPL-3.0-1-ov-file"><img src="https://img.shields.io/badge/License-GPL%203.0-yellow.svg" alt="License GPL 3.0" style="display: inline-block;"></a>
  <a href="https://orcid.org/0000-0002-1320-3486"><img src="https://img.shields.io/badge/ORCID-green?style=flat-square&logo=ORCID&logoColor=white" alt="ORCID" style="display: inline-block;"></a>
</p>


<br />


## **Introduction**

Modern dairy systems increasingly rely on commercial sensor platforms such as DeLaval, Lely, Afimilk, and CeresTag to provide real-time dashboards for rumination, activity, milk yield, SCC, and health alerts. These vendor interfaces are effective for day-to-day monitoring and operational decision support.

However, these systems are inherently vendor-defined: users typically interact with pre-built visualisations and fixed alert logic, with limited ability to extract cloud-hosted data for custom, question-driven analysis. When new biological, clinical, or research questions arise — for example “What behavioural changes precede mastitis across cows?” or “How should baselines be adjusted for parity or environment?” — the standard dashboards are often insufficient.

This repository demonstrates a vendor-agnostic Precision Livestock Health (PLH) analytics concept: starting from cloud-accessible sensor data, independent of the originating platform, and enabling flexible downstream analysis defined by the researcher or clinician, not the dashboard. Using synthetic dairy sensor data, the demo shows how rumination, activity, SCC, and milk production signals can be normalised at the individual-cow level and explored through interpretable visualisations rather than fixed vendor views.

**The emphasis is on:**

- Working directly with data retrieved from vendor clouds (once access is granted)

- Applying cow-specific baselines instead of one-size-fits-all thresholds

- Enabling ad-hoc, hypothesis-driven analysis beyond predefined web interfaces

This workflow is not a replacement for commercial platforms. Instead, it represents a complementary analytics layer that becomes possible once data access is available — supporting research, teaching, and services.

All data in this repository are synthetic, making it safe to share. 

> This repo is a **pilot demo** showing how common dairy sensor signals (rumination, activity, SCC, milk yield) can be transformed into **interpretable early-warning visualisations**.

---

## **Example 1 — Herd-Level Rumination Heatmap (Early-Warning Overview)**

**Objective**

- To provide a single, herd-level view of rumination behaviour
- To enable rapid identification of individual cows deviating from their own normal patterns
- To use individual cow-level threshold, rather than relying on fixed herd-wide thresholds or one-cow-at-a-time dashboards


<br /> <p align="center"> <img src="https://github.com/asadprodhan/plh-behavioral-earlywarning-demo/blob/main/Rumination_HeatMap.png" width="100%" > </p> <p> <strong>Figure 1. Herd-level rumination heatmap showing cow-specific deviations from healthy behavioural baselines.</strong> Heatmap representation of daily rumination behaviour across the herd over the study period. Rows correspond to individual cows and columns correspond to consecutive days. Cell colours encode the magnitude and direction of deviation of each cow’s rumination time from its own healthy baseline, rather than absolute rumination minutes. For each cow, a baseline rumination profile was derived from that cow’s historical data using the median daily rumination time, and a healthy range was defined as the median ± one standard deviation. Values falling within this cow-specific healthy range are shown in grey. Values below the healthy range are shown in red, with increasing colour intensity indicating progressively larger negative deviations from baseline. Values above the healthy range are shown in blue, with increasing intensity indicating stronger positive deviations. This representation enables rapid visual identification of individual cows exhibiting transient or sustained departures from their normal rumination behaviour, supporting herd-level early-warning assessment while accounting for inter-animal variability. </p> <br />



**What the graph shows**

- Rows represent individual cows

- Columns represent days

- Each cell shows how much that cow’s rumination deviates from its own healthy baseline

**Colour meaning**

- Grey → rumination within that cow’s healthy (normal) range

- Red → rumination below the healthy range; darker red = larger drop from normal

- Blue → rumination above the healthy range; darker blue = stronger positive deviation

**Importantly**

- “Healthy” is defined per cow, based on that cow’s own historical behaviour

- The heatmap shows relative change, not absolute rumination minutes

**This makes patterns immediately visible, such as:**

- Single-day dips versus multi-day sustained reductions

- Cows that repeatedly show instability

- Whether changes are isolated to individuals or appear herd-wide

**What this means for farmers**

- Farmers can scan the entire herd in seconds, instead of clicking through individual cow dashboards.

- Cows needing attention stand out visually, without interpreting numbers or thresholds.

- Sustained red patterns highlight cows that should be:

  - checked

  - monitored more closely

  - prioritised for intervention

**Equally important:**

- Large grey regions provide reassurance that most cows are behaving normally, reducing unnecessary checks.

- One-day red events can be distinguished from persistent problems, helping avoid over-reaction.


**In practical terms, this supports everyday questions like:**

> “Which cows should I look at today?”
>“Is this a temporary change, or something that’s persisting?”

---

## **Example 2 — Single-Cow Rumination Trend (Cow 13)**

**Objective**

- To show how rumination for a single cow evolves over time relative to that cow’s own healthy baseline, allowing differentiation between normal day-to-day variability and meaningful behavioural change

- This view complements the herd-level heatmap by enabling focused inspection of individual animals flagged for attention


<br /> <p align="center"> <img src="https://github.com/asadprodhan/plh-behavioral-earlywarning-demo/blob/main/Rumination_Trend_CowNo13.png" width="100%" > </p> <p> <strong>Figure 2. Single-cow rumination time-series showing deviations from an individual healthy behavioural baseline (Cow 13).</strong> Line plot showing daily rumination time (minutes per day) for Cow 13 across the study period. The solid line represents observed daily rumination values. Dashed horizontal lines indicate the cow-specific healthy rumination range derived from this cow’s historical behaviour, defined as the median daily rumination ± one standard deviation. Triangular markers denote days on which rumination values fall outside the healthy range, highlighting both negative deviations (below-range values) and strong positive deviations (above-range values). This representation enables visual differentiation between normal day-to-day variability and transient or sustained departures from baseline rumination behaviour, supporting individual-animal monitoring and early-warning assessment. </p> <br />


**What the graph shows**

- The blue line represents daily rumination time (minutes/day) for Cow 13

- The dashed horizontal lines define Cow 13’s healthy rumination range, calculated from its own historical behaviour

**Triangle markers highlight days that fall:**

- Below the healthy range (flagged low rumination)

- Above the healthy range (strong positive deviation)

**Key patterns visible in this plot:**

- Short, isolated dips followed by rapid recovery

- Periods of stable rumination within the healthy range

- Occasional deeper drops that cross the lower threshold

**This allows visual distinction between:**

- Transient noise (one-day deviations)

- Persistent or repeated deviations that may warrant closer attention

**What this means for farmers**

**Farmers can quickly answer:**

> “Is this cow just having a bad day, or is something changing?”

One-day drops that recover immediately can be safely deprioritised.

**Repeated or sustained drops below the healthy range suggest:**

- digestive stress

- early illness

- environmental or management issues

**This helps farmers:**

- Avoid unnecessary checks for normal variation

- Focus attention on cows showing patterns, not just alerts

- Make better-timed decisions such as monitoring, checking, or intervening

**In practice, this supports decisions like:**

> “I’ll keep an eye on this cow today.”

> “This drop has happened several times — I should check her.”

---

## **Example 3 — Rumination vs Activity Behaviour**

**Objective**

- To place rumination in behavioural context by combining it with activity, allowing identification of distinct behavioural states rather than interpreting a single metric in isolation

- To illustrate how mastitis-associated days occupy different regions of behaviour space compared to normal, healthy days


<br /> <p align="center"> <img src="https://github.com/asadprodhan/plh-behavioral-earlywarning-demo/blob/main/Rumination_VS_Activity.png" width="100%" > </p> <p> <strong>Figure 3. Behaviour-space representation of daily cow states based on rumination and activity.</strong> Scatter plot showing the joint distribution of rumination time (minutes per day) and activity level across all cows and days. Each point represents a single cow on a single day. The horizontal axis corresponds to daily rumination time and the vertical axis corresponds to activity level. The dense central cluster reflects the predominant healthy behavioural state of the herd, while points located outside this core region indicate days on which cows exhibited altered behavioural patterns. This representation highlights how combining multiple behavioural signals provides contextual information beyond single-metric views, enabling interpretation of distinct behavioural states such as normal digestion and movement, reduced rumination with reduced activity (high-risk or sickness-associated behaviour), reduced rumination with elevated activity (stress or discomfort-associated behaviour), and high rumination with low activity (calm, resting behaviour). This behaviour-space view supports intuitive assessment of behavioural shifts and complements time-series and herd-level summaries in early-warning analysis. </p> <br />


**What the graph shows**

- Each point represents a single cow on a single day

- The x-axis shows rumination time (minutes/day)

- The y-axis shows activity level

- The dense central cloud represents normal, healthy behavioural states


**This plot highlights:**

- Behavioural states rather than absolute thresholds

- How multiple signals together provide clearer insight than either signal alone

- Why the same rumination value can mean different things depending on activity level

**Key behavioural interpretations visible in this space:**

- Normal digestion with normal movement (healthy baseline)

- Reduced rumination with reduced activity (high-risk state)

- Reduced rumination with elevated activity (stress or discomfort)

- High rumination with low activity (calm, resting, healthy state)

**What this means for farmers**

- Farmers can move from alerts to understanding

- Instead of seeing "rumination low”, they can see "rumination dropped and activity changed — this is not normal behaviour for this cow.”

**This helps farmers:**

- Understand why a cow was flagged, not just that it was flagged

- Distinguish between sickness, behaviour stress, discomfort, normal resting behaviour

- Build confidence in data-driven alerts by seeing the behavioural context

**In practical terms, this supports decisions like:**

> “This cow is quiet and not chewing properly — I should check her.”

> “This looks like temporary stress, not illness.”

## **Conclusion**

This pilot study demonstrates how vendor-agnostic access to dairy sensor data can enable interpretable, animal-centric early-warning insights that extend beyond predefined commercial dashboard views. By integrating herd-level visual summaries, individual cow time-series trends, and multi-signal behavioural space representations, the workflow supports earlier detection of deviations from normal behaviour and more informed decision-making. Although based on synthetic data, the examples illustrate how cloud-hosted sensor streams can be repurposed into a flexible analytical framework suitable for hypothesis-driven investigation, teaching, and collaborative research once real data access is available.
