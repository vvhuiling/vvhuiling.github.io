---
layout: post
title: "Multiversal Studios Interactive Kiosk Prototype"
author: "Huiling Huang"
categories: project
tags: [project]
image: multiversal-hero.png    # <- 封面图，请替换为你的实际文件
---

This project is a **front-end interactive prototype** of a theme‑park planning kiosk designed for *Multiversal Studios*.  
It translates my TEL2 HCI design work into a working, responsive interface so that visitors can plan their day in the park directly on a large touchscreen kiosk.

The prototype focuses on:

- Turning a slide-based concept into a **clickable, high‑fidelity experience**
- Exploring **information architecture** for a dense catalog of attractions
- Supporting **decision‑making** under constraints like time, distance and wait time

The build is done entirely with **HTML + TailwindCSS (CDN) + Vanilla JavaScript**, and runs 100% on the client side.

---

This project is a **front-end interactive prototype** of a theme-park trip-planning kiosk designed for *Multiversal Studios*.  
It is based on my TEL2 HCI design slides and transforms the original static wireframes into a functional interface using **HTML + TailwindCSS + Vanilla JavaScript**.


 

---

## Overview

The kiosk allows visitors to explore rides, eateries, and shows; open detailed information panels; apply filters; search by keyword; build a trip itinerary; and receive automated suggestions when wait times change.  
The goal was to preserve the user flow and information hierarchy from the original design materials while implementing a smooth, responsive interaction model in the browser.

This prototype focuses on:

- Clear navigation between attraction categories  
- Consistent modal interactions across all detail views  
- Lightweight state handling (filters, search, trip additions)  
- Schedule visualization that reflects wait/play/walk segments  
- Contextual recommendations that respond to changing conditions  

---

## Core Interaction Flow

The user first enters the **Explore** view, where all attractions are presented as cards.  
They can refine the content through **Filters** (wait time, rider height, attraction type) or through **Search**, which includes proper empty-state feedback for unmatched queries.

Selecting any attraction opens a **detail modal** describing the experience, requirements, and wait times.  
From here, the user may **add the attraction to their trip**, triggering a short confirmation and updating relevant UI elements.

Once several activities are selected, the user can enter the **Schedule Planner**, where the system visualizes the timeline for the day.  
If conflicts occur, warnings appear to prompt the user to adjust.

---

## Adaptive Recommendation Logic

A key interaction is the **smart recommendation** feature:  
If the wait time for a chosen activity increases significantly, the interface suggests an alternative attraction with a shorter expected queue.  
This simulates how real theme-park systems could assist visitors in managing crowds more efficiently.

This component demonstrates simple condition-based decision logic implemented purely with JavaScript, without any backend systems.

<div align="center">
  <img src="/assets/img/recommendation.png" width="80%" alt="Recommendation Screenshot">
</div>

---

## “Welcome Back” & Trip Summary

To mimic a physical kiosk used by returning visitors, the prototype includes a **Welcome Back** flow.  
Upon return, the user is shown an updated trip summary with revised wait times and the option to modify their plan or continue exploring.

The intention was to create a believable end-to-end loop representing a real park-planning system:  
**Explore → Detail → Add to Trip → Schedule → Recommendation → Summary → Return**.

---

## Implementation Details

**Tech Stack**

- HTML5  
- TailwindCSS (CDN)  
- Vanilla JavaScript  
- Fully client-side; no frameworks or backend required  

**Technical Focus**

- DOM-based modal system  
- Category filtering & keyword search  
- Basic state tracking for selected activities  
- Simple timestamp-based schedule composition  
- Conditional rendering of recommendations  

The entire prototype is intentionally lightweight to ensure clarity and easy reproducibility while faithfully representing the logic described in the original design slides.

---

## Reflection

This project strengthened my ability to:

- Translate HCI wireframes and PPT flows into fully interactive UI  
- Implement clean, dependency-free front-end systems  
- Communicate UX logic through consistent interactions  
- Build end-to-end prototypes that feel cohesive and realistic  

It also demonstrates how minimal code structures can still express meaningful UX behavior when paired with thoughtful interface design.

---


You can find the source code in [the repository](https://github.com/vvhuiling/multiversal-studios).