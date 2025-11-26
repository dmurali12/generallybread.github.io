---
title: Endocrine System Overview
tags: [InProgess, Endocrine]
---

# Overview

- How organs and tissues communicate with each other
- Allows organisms to respond to changes in internal and external stimuli to maintain homeostasis
- Relies on hormonal communication
- Influenced by and influences the [[Nervous System|nervous system]]


```mermaid
graph TD
%% ===== HYPOTHALAMUS =====
H[Hypothalamus]

%% ===== PITUITARY =====
AP[Anterior Pituitary]
PP[Posterior Pituitary]

%% ===== TARGET GLANDS =====
T[Thyroid Gland]
A[Adrenal Cortex]
O[Ovaries]
L[Leydig Cells]
S[Sertoli Cells]
LIV[Liver]
M[Mammary Glands]
AC[Adrenal Cortex]

%% ==== AP HORMONES ====
FSH([FSH])
LH([LH])
ACTH([ACTH])
TSH([TSH])
Pr([Prolactin])
En([Endorphins])
GH([GH])


%% ===== PERIPHERAL HORMONES =====
T3((T₃))
T4((T₄))
CORT((Cortisol))
E((Estrogen))
P((Progesterone))
TST((Testosterone))
GH((GH))
IGF((IGF-1))
PRL((Prolactin))
OX((Oxytocin))
ADH((ADH))
GC((Glucocorticoids))
En((Endorphins))
GH((Growth Hormones))
Som((Somatostatin))


%% ==== PROCESSES ====
OO[/Oogenesis/]
Sp[/Spermatogenesis/]

Ov([Ovulation])


%% ==== HPG Axis ====
H -->|GnRH|AP

AP-->FSH-->S
S -->Sp
AP -->LH-->L
L -->TST

AP -->FSH-->O
AP -->LH-->Ov
O --> E
O --> P

%% ==== HPA Axis ====
H -->|CRF|AP
AP -->|ACTH|AC
AC --> GC

AP -->En
GC -.-xEn

%% ==== HPT Axis ====
H --> |TRH| AP
AP --> |TSH| T
T --> T3
T --> T4
T4 --> T3

%% ==== Prolactin ====
H -->|PIF|AP
AP -->|Prolactin| M

%% ==== Growth Hormone ====
H -->|GHRH|AP
AP -->GH

H -->Som-.-x GH

```

# Graph

```dot
digraph Endocrine {
  rankdir=TD;           // left→right flow (feels like Mermaid graph LR)
  splines=true;         // smooth-ish edges
  nodesep=0.5;
  ranksep=0.7;
  bgcolor="transparent"

  fontname="Helvetica"; // or "Inter", "SF Pro" etc if your system has it
  node [fontname="Helvetica"];
  edge [fontname="Helvetica"];

  node [
    shape=box,
    style="rounded,filled",
    fillcolor="#f8fafc",
    color="#cbd5e1",
    penwidth=1.4
  ];

  edge [
    color="#94a3b8",
    arrowsize=0.8,
    penwidth=1.4
  ];

  /* ======= Default node look ======= */
  node [style=rounded, fontsize=11];

  /* --- Organs (rectangles) --- */
  node [shape=box, fillcolor="#e3f2fd", style="filled,rounded", color="#1565c0"];
  H  [label="Hypothalamus"];
  AP [label="Anterior Pituitary"];
  T  [label="Thyroid"];
  A  [label="Adrenal Cortex"];
  O  [label="Ovaries"];
  L  [label="Leydig Cells"];
  LIV[label="Liver"];
  M  [label="Mammary Glands"];

  /* --- Hormones (ellipses) --- */
  node [shape=ellipse, fillcolor="#fff3cd", style="filled", color="#f9a825"];
  T3  [label="T₃"];
  T4  [label="T₄"];
  CORT[label="Cortisol"];
  E   [label="Estrogen"];
  P   [label="Progesterone"];
  TST [label="Testosterone"];
  IGF [label="IGF-1"];
  PRL [label="Prolactin"];
  GH  [label="GH"];

  /* ====== HPT Axis (blue) ====== */
  edge [color="#1565c0", penwidth=2];
  H  -> AP [label="TRH"];
  AP -> T  [label="TSH"];
  T  -> T4 [label="T₄"];
  T  -> T3 [label="T₃"];
  T4 -> T3 [label="Conversion"];
  T3 -> H  [label="– feedback", style=dashed, arrowhead=tee];

  /* ====== HPA Axis (orange) ====== */
  edge [color="#ef6c00", penwidth=2];
  H  -> AP [label="CRH"];
  AP -> A  [label="ACTH"];
  A  -> CORT;
  CORT -> H  [label="– feedback", style=dashed, arrowhead=tee];
  CORT -> AP [label="– feedback", style=dashed, arrowhead=tee];

  /* ====== HPG Axis (pink) ====== */
  edge [color="#c2185b", penwidth=2];
  H  -> AP [label="GnRH"];
  AP -> O  [label="FSH/LH"];
  AP -> L  [label="LH"];
  O  -> E;
  O  -> P;
  L  -> TST;
  E  -> H  [label="– feedback", style=dashed, arrowhead=tee];
  TST-> H  [label="– feedback", style=dashed, arrowhead=tee];

  /* ====== GH Axis (green) ====== */
  edge [color="#2e7d32", penwidth=2];
  H  -> AP [label="GHRH"];
  AP -> LIV [label="GH"];
  LIV-> IGF;
  IGF-> H [label="– feedback", style=dashed, arrowhead=tee];

  /* ====== Prolactin Axis (purple) ====== */
  edge [color="#6a1b9a", penwidth=2];
  H  -> AP [label="PIF (DA)"];
  AP -> M  [label="Prolactin"];
}
```

# Other Stuff

The endocrine system is one way that organs **communicate** with each other. "Endo" means *inside* and "crine" comes from the Greek root "kreinin", which in this case, means "to secrete".

- This system deals with **hormones** which are *secreted* into the **bloodstream**

## General Definitions

- **Gland**: an organ that *secretes* hormones
- **Hormone**: a *chemical* messenger that is secreted into the bloodstream

## [[Hormones]]

Hormones are the *messengers* of the endocrine system. Hormones are classified based on

1. Their makeup

- [[Peptide Hormones]]
- [[Amino Acid-Derived Hormones]]
- [[Steroid Hormones]]

2. Their intended action

- **[[Tropic Hormones]]** act on a *gland* to secrete a hormone
- **[[Direct Hormones]]** act on the *target tissue*

## The big players: hypothalamus and pituitary

Many endocrine axes start at the **[[hypothalamus]]**, which secretes [[Endocrine System/Peptide Hormones|peptide hormones]] that act on the [[anterior pituitary]].

- These are [[tropic hormones]]

The hypothalamus also [[Action Potentials|electrically stimulates]] the [[posterior pituitary]].

## [[Endocrine System/Pituitary Gland|Pituitary Gland]]

The pituitary gland has two lobes: the ***anterior** pituitary* and the ***posterior** pituitary*. How the hypothalamus sends the signal depends on which lobe the axis utilizes.

### [[Endocrine System/Anterior Pituitary|Anterior Pituitary]]

The [[Endocrine System/Anterior Pituitary|anterior pituitary]] (AP) is made of [[Gland|glandular]] tissue that can both synthesize and secrete [[Endocrine System/Peptide Hormones|peptide hormones]]. The hypothalamus releases ***releasing*** and ***inhibiting*** factors into the ***[[Hypophyses|hypophyseal]] [[Portal System|portal system]]***.  

- Hypothalamus sends ==[[Gland#Types of Glands|endocrine]] hormones to anterior pituitary==

#### Axes Involving Anterior Pituitary

##### Tropic Hormones

- [[Endocrine System/Reproductive Axis|HPG Axis]]
  - AP hormones: **[[Follicle Stimulating Hormone (FSH)]]** and **[[Lutenizing Hormone (LH)]]**
  - [[Gonadotropin Releasing Hormone (GnRH)]] --> FSH + LH --> [[Androgens]]
- [[Endocrine System/HPA Axis|HPA Axis]]
  - [[Corticotropin Releasing Factor (Hormone)]] --> [[Adrenocorticotropic Releasing Hormone (ACTH)]] --> [[Glucocorticoids]]
- [[Endocrine System/Thyroid Axis|HPT Axis]]
  - TRH --> TSH --> T3 + T4

##### Direct Hormones

- [[Prolactin]]
  - PIF (Dopamine) --| Prolactin
- [[Endorphins]]
  - CRH --> Endorphins
  - Glucocorticoids --| Endorphins
- [[Growth Hormone]]
  - GHRH --> GH
  - Somatostatin --| GH

| Hypothalamic Hormone | AP Hormone | Target Tissue          | Effect          |
| -------------------- | ---------- | ---------------------- | --------------- |
| GnRH                 | FSH        | Ovaries, Sertoli cells |                 |
|                      | LH         |                        |                 |
| CRF                  | ACTH       | Adrenal cortex         | glucocorticoids |
| TRH                  | TSH        |                        |                 |

### [[Endocrine System/Posterior Pituitary|Posterior Pituitary]]

The [[Endocrine System/Posterior Pituitary|posterior pituitary]] only *stores* hormones that the *hypothalamus produces*. The hypothalamus sends axons down into the posterior pituitary. When depolarized, the posterior pituitary releases the hormones (known as **neurohormones**) from the [[Neuron Structure|axon terminals]].

[[Anti-Diuretic Hormone (ADH)]]
[[Oxytocin]]

## Target Tissues

### [[Adrenal Gland]]

### [[Renal Hormones]]

### [[Pancreatic Hormones]]

[[Endocrine System/Renin-Angiotenisin-Aldosterone System|Renin-Angiotensin-Aldosterone System]]
[[Catecholamines]]

[[Parathyroid Gland]]

Appetite hormones
[[ghrelin]]
[[leptin]]
[[somatostatin]]

[[pineal gland]]
[[thymus]]

[[anp]]

[[Digestion]]
[[Gastrin]]
[[Cholecystekinin]]

whether the axis uses the [[Public/Endocrine System/Anterior Pituitary|anterior pituitary]] or the [[Public/Endocrine System/Posterior Pituitary|posterior pituitary]].
