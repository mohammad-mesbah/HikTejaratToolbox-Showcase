# HikTejarat Toolbox

A web-based engineering platform for CCTV system design, network planning, power budgeting, and technical analysis — built to replace scattered spreadsheets and manual calculations with a single, structured workflow for system designers and integrators.

This is a public portfolio showcase. The source code and internal technical documentation live in a private repository; this page describes the product, its architecture, and current development status.

**Status: Public Beta** · Live at [toolbox.hiktejarat.com](https://toolbox.hiktejarat.com)

## Overview

Designing a CCTV or structured cabling deployment involves a lot of manual, error-prone arithmetic: camera counts and placement, cable run lengths, switch port budgets, PoE power draw, storage sizing for retention periods, and voltage drop across long runs. Most of this work still happens across disconnected spreadsheets, vendor datasheets, and rule-of-thumb estimates.

HikTejarat Toolbox consolidates these calculations into one platform, so an engineer can move from a site's requirements to a verified, documented design without re-deriving the same formulas project after project.

## Engineering problems addressed

- **Power budgeting** — PoE load calculation across switches and injectors, with headroom and derating considerations.
- **Network planning** — port counts, VLAN segmentation groundwork, and bandwidth estimation for camera streams.
- **Cable and voltage-drop analysis** — maximum run lengths and conductor sizing for a given load and distance.
- **Storage sizing** — retention-period storage requirements based on resolution, frame rate, compression, and camera count.
- **Documentation consistency** — every calculation is tied to a project record, so a design can be revisited, audited, or handed off without reconstructing the reasoning behind it.

V1 focuses on getting these calculations right and keeping them auditable, rather than on automated design generation.

## Technology stack

| Area | Technology |
|---|---|
| Back end | Laravel (PHP) |
| Front end | React, TypeScript |
| Database | MySQL |
| Hosting | toolbox.hiktejarat.com |

## Architecture (high level)

- **Laravel back end** exposes the calculation engines and project/record persistence behind an API consumed by the React front end.
- **React + TypeScript front end** provides the calculator workflows, project dashboards, and (planned) visual design tools, built with type safety across the calculation and data-entry layers.
- **MySQL** stores project records, calculation inputs/outputs, and user accounts, with each engineering tool's data modeled around a project so results stay traceable over time.
- Calculation modules (power, network, cabling, storage) are built as independent tools sharing a common project/record layer, so new engineering calculators can be added without reworking the core data model.

This repository does not include the application source code, internal architecture documents, infrastructure configuration, or credentials — only the information needed to understand what the platform does and how it is built.

## Main engineering tools

**Implemented and available in the current Public Beta:**

- PoE power budget calculator
- Network/switch port planning calculator
- Cable run and voltage-drop calculator
- Video storage sizing calculator
- Project-based record keeping for saved calculations

**Planned / in development:**

- Visual Floor Plan Designer — drag-and-drop camera placement on uploaded floor plans, with automatic cable-run and coverage estimation derived from the layout
- Expanded reporting and export options for client-facing documentation
- Additional engineering modules beyond CCTV/networking/power (scope to be defined as the platform grows)

Nothing above marked as planned is implemented yet; this list is kept up to date as features ship.

## Roadmap

1. **Public Beta (current)** — core calculators live, stabilizing based on real project usage.
2. **Floor Plan Designer** — visual, floor-plan-based design workflow layered on top of the existing calculators.
3. **Reporting** — polished, exportable project reports for client delivery.
4. **Platform expansion** — broader engineering tool coverage based on demand from real deployments.

## Links

- Live platform: [toolbox.hiktejarat.com](https://toolbox.hiktejarat.com)

## Author

Mohammad Mesbah — Technical Manager, electronics procurement and systems engineering background. Dubai.
