<div align="center">

# ERICC 2 — ENSIT Vision Edition

### 5-DOF Articulated Robotic Arm | SOLIDWORKS CAD & Technical Drawing

![SOLIDWORKS](https://img.shields.io/badge/CAD-SOLIDWORKS-red?style=for-the-badge)
![DOF](https://img.shields.io/badge/Kinematics-5--DOF%20(RRR--RR)-blue?style=for-the-badge)
![Units](https://img.shields.io/badge/Units-MMGS-informational?style=for-the-badge)
![Interference](https://img.shields.io/badge/Interference-Zero%20Overlaps-brightgreen?style=for-the-badge)

*A custom SOLIDWORKS mechanical redesign of the classic **5-DOF ERICC 2** robotic manipulator, styled after the **ENSIT** robotics lab hardware and adapted with a 2-axis articulated optical camera wrist for computer vision.*

<br>

![ERICC 2 ENSIT Vision Hero Render](images/ericc2_hero.png)

</div>

---

## Overview

This repository contains the complete native **SOLIDWORKS** part models, articulated 5-DOF assembly, and ISO A3 **Dessin d'ensemble** for the **ERICC 2 (ENSIT Vision Edition)**. Built to nominal ERICC 2 link lengths and joint envelopes, the original mechanical gripper is replaced by a compact, balanced vision wrist (`J4` pitch + `J5` roll) carrying an optical camera module.

| Parameter | Specification |
| :--- | :--- |
| **Designer** | Ghassen Ben Rhouma — École Nationale Supérieure d'Ingénieurs de Tunis (**ENSIT**) |
| **Credential Applied** | SOLIDWORKS Design Associate (**CSWA**) |
| **Units & System** | `MMGS` (millimeter, gram, second) |
| **Kinematic Chain** | 5-DOF Serial Manipulator (`RRR-RR`) |
| **Max Nominal Reach** | $752.50\text{ mm}$ from $O_2$ ($a_2 + a_3 + d_{\text{tool}}$) |
| **CAD Model Mass** | $147.75\text{ kg}$ (solid-body structural estimate) |
| **Assembly Validation** | Verified zero interferences (*Aucune interférence*) |

---

## Visual Showcase

| Side Elevation (*Vue de face*) | 2-Axis Vision Wrist Close-Up |
| :---: | :---: |
| ![ERICC 2 Side Profile](images/ericc2_side_profile.png) | ![Camera Wrist Close-Up](images/camera_wrist_closeup.png) |

### ISO A3 Technical Drawing (*Dessin d'ensemble*)

Includes the front elevation, connected vertical section view (`COUPE A-A`) with alternating hatching, shaded isometric reference, official ERICC 2 kinematic dimensions, aligned underlined repères (`1`–`6`), and full French *Nomenclature* (BOM).

![ERICC 2 ENSIT Vision Dessin d'ensemble](images/ericc2_ensit_vision.JPG)

> **Printable Vector PDF:** [Download `ericc2_ensit_vision.pdf`](exports/ericc2_ensit_vision.pdf)

---

## Joint Hierarchy & Angular Limits

`00_base_socle` is fixed (`f`) at the assembly origin. All 5 revolute joints use unlocked **Concentric** mates paired with flush **Coincident** (or centered **Width**) mates so the full manipulator articulates smoothly.

The table below documents the official **ERICC 2 mechanical angular limits** for each axis (in both degrees and radians for CAD limit mates and downstream kinematics):

| Joint | Variable | Parent $\rightarrow$ Child | Axis Ref | Min Angle | Max Angle | Total Stroke | Limits (Radians) | Motion Type |
| :---: | :---: | :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **J1** | $\theta_1$ | `00_base_socle` $\rightarrow$ `01_chaise_turret` | `Axis_J1` | $-135^\circ$ | $+135^\circ$ | $270^\circ$ | $[-2.356,\ +2.356]\text{ rad}$ | Base Pan |
| **J2** | $\theta_2$ | `01_chaise_turret` $\rightarrow$ `02_bras_upper_arm` | `Axis_J2` | $-90^\circ$ | $+43^\circ$ | $133^\circ$ | $[-1.571,\ +0.750]\text{ rad}$ | Shoulder Pitch |
| **J3** | $\theta_3$ | `02_bras_upper_arm` $\rightarrow$ `03_avant_bras_forearm` | `Axis_J3` | $-90^\circ$ | $+45^\circ$ | $135^\circ$ | $[-1.571,\ +0.785]\text{ rad}$ | Elbow Pitch |
| **J4** | $\theta_4$ | `03_avant_bras_forearm` $\rightarrow$ `04_wrist_pitch` | `Axis_J4` | $-90^\circ$ | $+90^\circ$ | $180^\circ$ | $[-1.571,\ +1.571]\text{ rad}$ | Wrist Pitch |
| **J5** | $\theta_5$ | `04_wrist_pitch` $\rightarrow$ `05_camera_mount_roll` | `Axis_J5` | $-180^\circ$ | $+180^\circ$ | $360^\circ$ | $[-3.142,\ +3.142]\text{ rad}$ | Camera Roll |

<details>
<summary><b>SOLIDWORKS Tip: Applying Limit Angle Mates</b></summary>

Rotation is left unlocked by default so the assembly exports cleanly to robotics simulators. To enforce mechanical stops while dragging the arm in SOLIDWORKS:
1. Open **Mate** $\rightarrow$ **Advanced Mates** $\rightarrow$ **Limit Angle**.
2. Select the reference planes of the parent and child links for the target joint.
3. Enter the **Min Angle** and **Max Angle** values from the table above.

</details>

---

## Bill of Materials & Kinematic Dimensions

| Repère | File Name | Désignation | Material | Key Dimensions & Features |
| :---: | :--- | :--- | :--- | :--- |
| **6** | `00_base_socle.SLDPRT` | Socle de base | Acier AISI 1020 | Trapezoidal base plate ($15\text{ mm}$) + $\varnothing 220\text{ mm}$ pedestal; $160.00\text{ mm}$ height to $O_1$; ENSIT Blue (`RGB 15, 95, 165`) |
| **5** | `01_chaise_turret.SLDPRT` | Tourelle rotative - Chaise | Alliage d'aluminium 1060 | $\varnothing 220\text{ mm}$ drum + vertical column rising $352.00\text{ mm}$ to $O_2$; rear belt guard & drive motor |
| **1** | `02_bras_upper_arm.SLDPRT` | Bras supérieur | Alliage d'aluminium 1060 | Tapered boxy arm; $280.00\text{ mm}$ link length ($O_2 \to O_3$); side stepper motor, stainless cover plate & embossed `ensit` sign |
| **4** | `03_avant_bras_forearm.SLDPRT` | Avant-bras à chape | Alliage d'aluminium 1060 | Tapered forearm; $317.50\text{ mm}$ link length ($O_3 \to O_4$); $52.00\text{ mm}$ open clevis fork & stainless `ensit` top plate |
| **3** | `04_wrist_pitch.SLDPRT` | Poignet de tangage | Acier AISI 1020 | $50.00\text{ mm}$ pitch yoke ($1\text{ mm}$ clearance/side inside clevis); $65.00\text{ mm}$ offset to $\varnothing 48\text{ mm}$ roll boss |
| **2** | `05_camera_mount_roll.SLDPRT` | Module caméra vision | Alliage d'aluminium 1060 | $\varnothing 48\text{ mm}$ roll flange, universal adapter plate, $40\text{ mm}$ camera body & $\varnothing 34\text{ mm}$ lens ($90.00\text{ mm}$ length; $155.00\text{ mm}$ total reach from $O_4$) |

---

## Repository Structure

```text
ericc2-ensit-vision/
├── 00_base_socle.SLDPRT
├── 01_chaise_turret.SLDPRT
├── 02_bras_upper_arm.SLDPRT
├── 03_avant_bras_forearm.SLDPRT
├── 04_wrist_pitch.SLDPRT
├── 05_camera_mount_roll.SLDPRT
├── ericc2_ensit_vision.SLDASM      # Full 5-DOF articulated assembly
├── ericc2_ensit_vision.SLDDRW      # ISO A3 Dessin d'ensemble
├── exports/
│   └── ericc2_ensit_vision.pdf     # Printable high-resolution A3 drawing
├── images/
│   ├── ericc2_hero.png
│   ├── ericc2_side_profile.png
│   ├── camera_wrist_closeup.png
│   └── ericc2_ensit_vision.JPG
├── .gitignore
└── README.md
```

---

## CAD Verification Checklist

- [x] All 6 part files built in `MMGS` units as single merged solid bodies (`Solid Bodies(1)`).
- [x] Explicit reference axes (`Axis_J1`–`Axis_J5`) and reference frames (`base_frame`, `camera_link`) included.
- [x] **Evaluate** $\rightarrow$ **Interference Detection** confirmed **Aucune interférence** (zero interferences).
- [x] ISO A3 technical drawing exported with connected section view (`COUPE A-A`), BOM, and ENSIT title block.

---

## Author

**Ghassen Ben Rhouma**  
Master Professionnel Industrie 4.0 — **ENSIT** (Tunis, Tunisia)  
GitHub: [@ghassenbrh](https://github.com/ghassenbrh)