---
title: UEA Discussion
summary: Discussing "Do Appraiser and Borrower Race Affect Valuation?"
authors: [Florian Oswald]
tags: []
categories: []
date: "2019-02-05T00:00:00Z"
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: simple
  # Choose a code highlighting style (if highlighting enabled in `params.toml`)
  #   Light style: github. Dark style: dracula (default).
  highlight_style: dracula
---

## Do Appraiser and Borrower Race Affect Valuation?

<br>

- **Authors**: Brent W. Ambrose, James N. Conklin, N. Edward Coulson, Moussa Diop, and Luis A. Lopez
- **Discussant**: Florian Oswald

---

### Intro

* Property appraisers are trained to asses property value estimates.
* Large body of evidence going back to the 60s of discriminatory practices in mortgage markets - HMDA.
* *Extremely* relevant setting: In remortgageing setting, appraiser *proclaims* the value of property (not the market).
* **This Paper**: Is there racial bias in remortgageing appraisals?


---

### Approach

1. Use property level data on remortgage appraisals, where owner's race is observed.
2. Infer the appraiser's race from first and last name.
3. Compare appraisal to output of an industry model (Automatic Valuation Model, AVM).
4. Assess and interpret differences.

---

### Contribution

* Novel dataset and insights in a contentious area of debate.
* First paper to be able to assess impact of appraiser's race.
* Found effect does *not* disappear with race of appraiser.

---

### Comment 1: The AVM Model

* It would be good to know more about this *black box* model.
* We should know what variables it uses, at which geographic scale.
* How well does it perform?
* 🤔 Why do lenders send appraisers instead of relying on the model?
* Outcome $Y_i$ is difference between appraiser and some estimate we don't know much about. (We know it's a *moving target*.)

---

### Comment: Quality

$$Y_i = \delta_1 A_i + \delta_2 B_i + \delta_3 H_i + X_i \beta + \xi_i +\lambda_i +\omega_i + \epsilon_i$$

{{< fragment >}}
* $X$: property type, investment properties, multi-unit properties, condominiums, and PUDs
* *Unobserved House Quality* is the elephant in the room. 
* Omitted variable bias could be severe. Notice that the appraiser FE does not deal with this.
* If avg unobserved quality of group $g$ is relatively high, we will *underestimate* discrimination, and vice versa.
* Here are a few candidates:
{{< /fragment >}}

---

### Potentially Omitted Variables

1. Age of property. It may be that certain groups can afford only buildings of older vintage, which could be assessed a lower value. 
2. Investments in structure, maintainance and upkeep: Less affluent groups may find it harder to make timely investments (roof, heating, insulation...), which in turn impact the appraisal.
3. Investments in home improvement: Less affluent groups may find it harder to install winter garden or swimming pools, with the same effect on valuations.

---

### Potential Solutions

* A building-level fixed effect. [Vladimir Avetian](http://jmp-consider-the-slavs.tilda.ws/) can use one in documenting (overt) discrimination in Moscow's housing market. *Probably hard here - unless you have a bunch of properties in a single unit?*
* Get more data on the property to increase $X$? With current data seemingly impossible. What about ZTRAX, which has tons of characteristics (and First and Last name of Buyer and Seller), or something similar?
* The upside could be that one obtains more credible identification, downside that one probably uses the race (indeed, the name) of the appraiser.
