# Datasets & Benchmarks

This document provides detailed information on datasets available for training and evaluating medical world models.

---

## Surgical Video

### SurgToolLoc-2022

| Attribute | Information |
|-----------|-------------|
| **Description** | da Vinci surgical robot training videos showing standard activities like tissue dissection and suturing |
| **Size** | 24,695 video clips, 30 seconds each |
| **Resolution** | 1280 x 720, 60fps |
| **Annotations** | Presence labels for 14 surgical tools |
| **Availability** | 🔓 Public |
| **Link** | [Grand Challenge](https://surgtoolloc.grand-challenge.org/) |
| **Related Papers** | Surgical Vision World Model |

**Usage Tips:**
- Suitable for training action-controllable surgical video generation models
- 16-frame sampling @1fps is a common setting
- Center crop to 900x600 to remove black borders

---

## Chest Imaging

### MIMIC-CXR

| Attribute | Information |
|-----------|-------------|
| **Description** | Large-scale chest X-ray dataset with radiology reports |
| **Size** | 377,110 images, 227,827 reports |
| **Availability** | 🔐 Requires PhysioNet credentialing |
| **Link** | [PhysioNet](https://physionet.org/content/mimic-cxr/2.0.0/) |
| **Related Papers** | CheXWorld, X-WIN |

**Usage Tips:**
- Application process takes approximately 1-2 weeks
- Commonly used for pre-training and evaluation
- Includes frontal and lateral views

### NLST (National Lung Screening Trial)

| Attribute | Information |
|-----------|-------------|
| **Description** | Lung cancer screening CT dataset |
| **Size** | 32,371 CT scans |
| **Availability** | 🔐 Requires application |
| **Link** | [CDAS](https://cdas.cancer.gov/nlst/) |
| **Related Papers** | X-WIN |

**Usage Tips:**
- Can be used to generate simulated X-ray projections
- Provides 3D volumetric information

---

## Brain MRI

### MU-Glioma-Post

| Attribute | Information |
|-----------|-------------|
| **Description** | University of Missouri post-operative glioma dataset |
| **Size** | 203 patients, 654 MRI follow-ups |
| **Annotations** | Treatment records, genomic annotations, survival data |
| **Availability** | 🔓 Public |
| **Link** | [TCIA](https://www.cancerimagingarchive.net/) |
| **Related Papers** | CLARITY |

**Usage Tips:**
- Contains rich longitudinal data
- Suitable for disease progression modeling
- 4:1 patient-level split to avoid temporal leakage

### UCSF-ALPTDG

| Attribute | Information |
|-----------|-------------|
| **Description** | UCSF Adult Longitudinal Post-Treatment Diffuse Glioma dataset |
| **Size** | 298 patients |
| **Annotations** | Longitudinal MRI sequences, survival outcomes |
| **Availability** | 🔓 Public |
| **Link** | [TCIA](https://www.cancerimagingarchive.net/) |
| **Related Papers** | CLARITY |

**Usage Tips:**
- Can be used for external validation
- Complementary to MU-Glioma-Post

---

## Disease Diagnosis

### VinDr-CXR

| Attribute | Information |
|-----------|-------------|
| **Description** | Vietnamese chest X-ray dataset |
| **Size** | 18,000 images |
| **Annotations** | Radiologist-annotated lesions |
| **Availability** | 🔓 Public |
| **Link** | [VinDr](https://vindr.ai/) |
| **Related Papers** | X-WIN |

### CheXpert

| Attribute | Information |
|-----------|-------------|
| **Description** | Stanford chest X-ray dataset |
| **Size** | 224,316 images |
| **Annotations** | 14 pathology labels (with uncertainty) |
| **Availability** | 🔓 Public |
| **Link** | [CheXpert](https://stanfordmlgroup.github.io/competitions/chexpert/) |

### NIH Chest X-ray

| Attribute | Information |
|-----------|-------------|
| **Description** | NIH Clinical Center chest X-ray dataset |
| **Size** | 112,120 images |
| **Annotations** | 14 disease labels |
| **Availability** | 🔓 Public |
| **Link** | [NIH](https://nihcc.app.box.com/v/ChestXray-NIHCC) |

---

## Ultrasound

### Cardiac Ultrasound Datasets

(Dataset information used by EchoWorld and Cardiac Copilot to be added)

---

## Electronic Health Records (EHR)

### Epic Cosmos

| Attribute | Information |
|-----------|-------------|
| **Description** | Large-scale EHR data from Epic systems |
| **Size** | Billions of medical events |
| **Availability** | 🔒 Requires partnership agreement |
| **Related Papers** | CoMET |

**Note:** This dataset is typically not publicly available; access only through Epic partnerships.

---

## Breast Cancer

### I-SPY2

| Attribute | Information |
|-----------|-------------|
| **Description** | Multi-center neoadjuvant chemotherapy trial data |
| **Content** | Clinical variables, treatment protocols, pCR outcomes |
| **Availability** | 🔐 Requires application |
| **Link** | [I-SPY](https://www.ispytrials.org/) |
| **Related Papers** | CLARITY |

---

## Data Access Recommendations

### Priority (Public & Easy Access)

1. **SurgToolLoc-2022** - Surgical video, direct download
2. **MU-Glioma-Post** - Brain MRI, TCIA download
3. **CheXpert** - Chest X-ray, registration required
4. **NIH Chest X-ray** - Chest X-ray, direct download

### Requires Credentialing

1. **MIMIC-CXR** - Requires PhysioNet training completion (~2-3 hours)
2. **NLST** - Requires research proposal submission

### Institutional Partnership

1. **Epic Cosmos** - Requires partnership with Epic

---

## Data Preprocessing Tips

### Medical Imaging

```python
# Common preprocessing pipeline
1. Normalize to [0, 1] or [-1, 1]
2. Resize (common: 224x224, 512x512)
3. Remove black borders and overlays
4. Histogram equalization (optional)
```

### Temporal Data

```python
# Longitudinal data processing
1. Group by patient ID
2. Sort by time
3. Calculate time intervals (delta_t)
4. Handle missing values
5. Patient-level split (avoid data leakage)
```

---

[← Back to Home](../README.md)
