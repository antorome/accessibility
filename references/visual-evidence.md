# Visual evidence: conditions, functional needs, and population estimates

**Reviewed: 2026-11-23.** This educational reference supports accessibility decisions for monitors, phones, browsers, and applications. It is not a diagnostic instrument, treatment guide, or exhaustive disease catalogue. Use [visual-needs.md](visual-needs.md) for practical adjustments and [GUIDE.md](../GUIDE.md) for technical criteria.

## Read the evidence correctly

**Prevalence** describes existing cases in a defined population and period; **incidence** describes new cases over time. The numbers below are prevalence estimates or counts of existing cases. A publication or review date is not necessarily the year represented by its data.

A diagnosis, a symptom, measured visual impairment, disability in a particular environment, and a presentation preference are different observations. Corrected presbyopia does not establish residual difficulty reading a screen. Discomfort during computer work does not establish permanent vision loss. Conversely, normal visual acuity does not rule out difficulties with color, contrast, light, or binocular coordination. [G1][color] [G3][refractive] [G8][binocular] [A1][visual]

**Rows overlap and must not be added or ranked as clinical severity.** For example, one person can have presbyopia, cataract, and dry eye. Different age distributions, correction status, definitions, and measurement methods prevent direct comparisons. None of these figures estimates the proportion of application users who need a dark theme, borders, larger text, or any other preset.

## Conditions and functional implications

The final column contains **design hypotheses to verify**, informed by functional guidance rather than clinical trials proving that a particular interface treats a condition. “No generalizable estimate” means this reference supplies no defensible population-wide percentage for that functional need; it does not mean the difficulty is rare or unimportant.

| Condition or trait | Population evidence and limits | Possible screen difficulty and design implication |
| --- | --- | --- |
| **Color vision deficiency** | MedlinePlus reports red–green deficiency in about **1 in 12 men (8.3%) and 1 in 200 women (0.5%) of Northern European ancestry**. This is a compiled reference estimate, not a single dated survey or a universal rate. Acquired deficiencies also occur. [G1][color] | Hue-coded errors, charts, and selection can become ambiguous even with sharp vision. Add labels, symbols, or patterns; check meaningful color pairs. A generic “color-blind palette” cannot cover every deficiency. |
| **Near vision and presbyopia** | A global model estimated **1.8 billion people, 25% of the all-age population (95% CI 23–27%), in 2015**. This includes corrected presbyopia; **826 million** had near impairment from absent or inadequate correction. Published 2018. [E1][presbyopia-study] | Small near text may be difficult, with needs varying by viewing distance and correction. Support enlargement and reflow on both phone and monitor; do not assign a theme from age or diagnosis. |
| **Other refractive needs** | Myopia, hyperopia, and astigmatism affect focus differently. No combined worldwide percentage is supplied here: diagnosis prevalence and impairment remaining with usual correction are different measures. [G3][refractive] | Blur or unclear characters can affect labels, code, and detail. Offer usable scaling and readable type; verify with the person's ordinary setup. CSS cannot supply optical correction. |
| **Distance impairment, low vision, and blindness** | For **2020, all ages globally**, VLEG/GBD estimated **43.3 million blind** (95% uncertainty interval 37.6–48.4m), **295 million with moderate/severe distance impairment** (267–325m), and **258 million with mild impairment** (233–285m). These are modeled presenting-vision categories, not counts of screen users or necessarily irreversible loss. [E2][vleg] | Needs can include magnification, stronger contrast, orientation support, speech, or Braille. Preserve semantics, keyboard access, and assistive-technology compatibility; visual personalization alone cannot serve all users. |
| **Cataract, glare, and fading detail** | Clinical guidance describes blur, faded colors, light sensitivity, and halos; early cataract may have no noticeable symptoms. No population percentage is used because disease presence, surgery history, and current functional impairment differ. [G5][cataract] | Low-contrast text and glare can interfere with reading. Test contrast, surface brightness, polarity, and environmental reflections separately. A brighter display is not automatically more legible. |
| **Age-related macular degeneration (AMD)** | AMD can affect central detailed vision; early disease may be asymptomatic. No all-stage diagnosis percentage is presented as the prevalence of central reading disability. [G6][amd] | Reading and recognizing small icons may be difficult. Support enlargement, reflow, meaningful labels, and alternatives to visual detail. Preserve context when only part of the interface is visible. |
| **Glaucoma and visual field loss** | Glaucoma can develop without early symptoms and later affect peripheral vision. Field loss also has other causes. **No generalizable percentage for field-related interface needs** is supplied. [G7][glaucoma] [G4][lowvision] | Distant notifications or controls may be missed. Keep feedback associated with its action, maintain predictable navigation, and provide programmatically available status. Greater magnification can reduce visible context further. |
| **Binocular coordination and diplopia** | Convergence insufficiency can cause near blur, double vision, or losing one's place, including during computer or phone use. Good acuity does not exclude it. **No generalizable prevalence estimate** is supplied; strabismus prevalence is not diplopia prevalence. [G8][binocular] | Sustained reading may be difficult. Test spacing, stable layouts, and reading support against the actual task. Do not infer a binocular disorder or offer corrective exercises through an accessibility setting. |
| **Dry eye disease** | The **2017 TFOS DEWS II** review reported approximately **5–50% across studies**, with different countries, ages, and definitions. This is a heterogeneous study range, **not a pooled world rate**. Symptoms and clinical signs do not give interchangeable estimates. [E3][dryeye] | Discomfort and fluctuating clarity can affect sustained reading. Evaluate reported comfort as well as task performance. Interface adjustments are not evidence that ocular surface disease has been treated. |
| **Digital eye strain** | **TFOS Lifestyle 2023** identifies major definition and questionnaire limitations, including difficulty separating digital from non-digital task symptoms. No universal percentage is adopted. It can overlap with dry eye, refractive needs, and binocular difficulties. [E4][strain] | Tiredness, blur, or discomfort can build during work. Assess ordinary task duration, size, glare, layout, and viewing setup. A brief theme preview cannot establish sustained benefit or medical efficacy. |
| **Migraine and light sensitivity** | A **2022 review of 357 non-clinical population publications through 2020**, predominantly from high-income countries, estimated **active migraine prevalence at 14.0% (95% CI 12.9–15.2%)**. Ages and methods varied. This is **not the prevalence of screen-triggered migraine or photophobia**. [E5][migraine-study] | Light sensitivity can accompany migraine, but symptoms and triggers vary. Offer controllable brightness/polarity and motion; avoid promising that dark mode prevents attacks. [G9][migraine] |
| **Motion and flashing sensitivity** | There is no single transferable percentage for intolerance of animation, vestibular symptoms, migraine triggers, and photosensitive seizures. These are distinct concerns. WAI explains motion-related reactions; WCAG separately addresses flashing and animation. [A2][motion] [N1][wcag] | Reduce nonessential movement and support user control. Assess flashing against the applicable criterion; a reduced-motion setting does not by itself establish flash safety. Do not test tolerance by exposing someone to suspected hazardous effects. |

**Definitions matter:** VLEG's presenting-vision estimates describe vision with available correction, if any, and include potentially correctable impairment. NEI uses *low vision* for difficulty that standard correction or treatment cannot fix. These populations are not interchangeable. Blindness classifications also do not necessarily mean complete absence of light perception. [E2][vleg] [G4][lowvision]

## Apply this without diagnosing users

Start with a task: reading a passage, finding focus, interpreting an error, or following a change across windows. Ask about functional preferences when needed, such as “Which sample is easier to read?” Do not require a diagnosis or medical history to unlock adjustments.

Keep text size, foreground/background polarity, contrast, surface brightness, control boundaries, transparency, and motion separable. A border can help someone locate a field without implying a particular disease. A dark background is not a treatment, and a contrast ratio does not measure display luminance or comfort. Individual preferences and environmental conditions can differ. [A3][needs]

Evaluate the same task with representative users and their usual devices, viewing distances, lighting, and assistive technology. Record completion, errors, orientation, effort, and voluntarily reported comfort separately from technical conformance. Judge a barrier by its consequences in that task, not by the condition's population frequency. Keep preferences reversible and the adjustment controls accessible.

## Source register and evidence classes

**E — Empirical synthesis and modeling.** These are the original publications for the estimates summarized here, although they synthesize earlier studies rather than constitute single population surveys. Confidence or uncertainty intervals describe the respective statistical analysis; they do not eliminate measurement or selection limitations.

- **E1:** Fricke et al. (2018), [Global Prevalence of Presbyopia and Vision Impairment from Uncorrected Presbyopia][presbyopia-study]. Systematic review, meta-analysis, and modeling; estimates for 2015.
- **E2:** GBD 2019 Blindness and Vision Impairment Collaborators / VLEG (2021; online 2020), [Trends in prevalence of blindness and distance and near vision impairment over 30 years][vleg]. Population surveys from 1980–2018, modeled to 2020.
- **E3:** Stapleton et al. (2017), [TFOS DEWS II Epidemiology Report][dryeye]. Review of heterogeneous epidemiological studies.
- **E4:** Wolffsohn et al. (2023), [TFOS Lifestyle: Impact of the digital environment on the ocular surface][strain]. Evidence review and consensus report, including measurement limitations.
- **E5:** Stovner et al. (2022), [The global prevalence of headache][migraine-study]. Narrative review and methodological analysis of population prevalence publications through 2020.

**G — Medical explanatory guidance.** These sources describe conditions and possible manifestations. They do not validate interface presets or supply a common epidemiological denominator. Pages were checked on the review date; their update dates are not observation years.

- **G1:** MedlinePlus Genetics, [Color vision deficiency][color] (updated 2026-10-21).
- **G2–G8:** National Eye Institute: [Presbyopia][presbyopia], [Refractive errors][refractive], [Low vision][lowvision], [Cataracts][cataract], [AMD][amd], [Glaucoma][glaucoma], and [Convergence insufficiency][binocular], respectively.
- **G9:** NIH, [Migraine][migraine].

**N — Normative requirements; A — informative accessibility guidance.** [N1: WCAG 2.2][wcag] supplies testable conformance requirements, not prevalence statistics or proof of medical benefit. [A1: WAI visual barriers][visual] and [A2: Understanding Animation from Interactions][motion] are informative. [A3: Accessibility Requirements for People with Low Vision][needs] is a **Working Draft**, not a normative standard. Apply the exact criteria, levels, and exceptions in the main guide.

[presbyopia-study]: https://pubmed.ncbi.nlm.nih.gov/29753495/
[vleg]: https://pmc.ncbi.nlm.nih.gov/articles/PMC7820390/
[dryeye]: https://pubmed.ncbi.nlm.nih.gov/28736337/
[strain]: https://pubmed.ncbi.nlm.nih.gov/37062428/
[migraine-study]: https://pubmed.ncbi.nlm.nih.gov/35410119/
[color]: https://medlineplus.gov/genetics/condition/color-vision-deficiency/
[presbyopia]: https://www.nei.nih.gov/eye-health-information/eye-conditions-and-diseases/presbyopia
[refractive]: https://www.nei.nih.gov/eye-health-information/eye-conditions-and-diseases/refractive-errors
[lowvision]: https://www.nei.nih.gov/eye-health-information/eye-conditions-and-diseases/low-vision
[cataract]: https://www.nei.nih.gov/eye-health-information/eye-conditions-and-diseases/cataracts
[amd]: https://www.nei.nih.gov/eye-health-information/eye-conditions-and-diseases/age-related-macular-degeneration
[glaucoma]: https://www.nei.nih.gov/eye-health-information/eye-conditions-and-diseases/glaucoma
[binocular]: https://www.nei.nih.gov/eye-health-information/eye-conditions-and-diseases/convergence-insufficiency
[migraine]: https://health.nih.gov/health-topics-a-z/migraine
[wcag]: https://www.w3.org/TR/WCAG22/
[visual]: https://www.w3.org/WAI/people-use-web/abilities-barriers/visual/
[motion]: https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions.html
[needs]: https://www.w3.org/TR/low-vision-needs/
