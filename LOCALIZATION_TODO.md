# Localization TODO — `inputs/` corpus (FR → EN-US)

> The **code, README and notebooks are already localized** to English (Willow Creek).
> What remains is the **RAG knowledge corpus** under [`inputs/`](inputs/): 30 files
> (17 PDF · 8 DOCX · 2 CSV · 1 WAV · 1 PNG · 1 WEBP), all written around the fictional
> French town **Trifouillis-sur-Loire**. They must be re-created in **English (US)** for the
> fictional town **Willow Creek**, staying consistent with the rest of the repo.
>
> This file is a guide to drive that localization (e.g. with ChatGPT). Keep it until the
> corpus is done, then delete it.

---

## 0. How to use this file (FR)

Tu vas régénérer les fichiers `inputs/` avec ChatGPT. Pour chaque fichier :
1. Donne à ChatGPT le **glossaire** (§2) + les **ancres de cohérence** (§3) — c'est ce qui garantit
   que le corpus colle au code et aux notebooks déjà traduits.
2. Demande-lui de **traduire/adapter le contenu** en anglais US (pas du mot-à-mot : adaptation
   culturelle vers une petite ville américaine).
3. **Renomme** le fichier selon le mapping (§1) et garde la **même arborescence de dossiers**
   (les noms de dossiers servent de `category` dans le RAG — voir [utils/data_loader.py](utils/data_loader.py)).
4. Un **prompt prêt à coller** est fourni en §5.

⚠️ **Sécurité** : le repo source OpenClassrooms contenait une clé API Mistral en clair
(`StthE16bt5…`). Elle a été retirée de ce repo. Si elle t'appartient, **révoque-la** sur
console.mistral.ai.

---

## 1. File & folder renaming map

Keep the structure; rename folders to English too (the folder name becomes the RAG `category`).
Filenames marked 🔗 are **referenced by `notebooks/P1C3_text_extraction.ipynb`** — use these exact names.

| # | Source (FR) | Target (EN) |
|---|-------------|-------------|
| | **`budget/`** | **`budget/`** |
| 1 | `budget_2024.csv` | `budget_2024.csv` *(translate headers + values inside)* |
| | **`communication/`** | **`communication/`** |
| 2 | `Acceuil_affichage_Mairie de Triffouillis sur Loire.pdf` | 🔗 `Welcome_notice_Willow_Creek_City_Hall.pdf` |
| 3 | `logo_triffouillis.webp` | `logo_willow_creek.webp` *(redo image/logo text)* |
| 4 | `voeux2025_trifouillis.wav` | 🔗 `willow_creek_greetings_2025.wav` *(re-record/synthesize EN audio)* |
| | **`demandes citoyennes/`** | **`citizen_requests/`** |
| 5 | `Demande d'information sur l'entretien de la voirie.docx` | `Request_for_information_on_road_maintenance.docx` |
| 6 | `Demande de participation à la réunion municipale sur la revitalisation du centre-ville.docx` | `Request_to_attend_the_town_meeting_on_downtown_revitalization.docx` |
| 7 | `Signalement et demande d'intervention pour un éclairage public défectueux.docx` | `Report_and_request_to_fix_faulty_street_lighting.docx` |
| | **`evenements/`** | **`events/`** |
| 8 | `Festival des Rires et des Blagues.docx` | `Festival_of_Laughs_and_Jokes.docx` |
| 9 | `Fête des Saveurs Insolites.docx` | `Festival_of_Unusual_Flavors.docx` |
| 10 | `Journée de l'Insolence Créative.docx` | `Day_of_Creative_Insolence.docx` |
| 11 | `Le Carnaval des Objets Oubliés.docx` | `The_Carnival_of_Forgotten_Objects.docx` |
| 12 | `Nuit des Arts Urbains.docx` | `Urban_Arts_Night.docx` |
| 13 | `marche_noel_trifouillis_2023.png` | 🔗 `willow_creek_christmas_market_2023.png` *(redo poster image)* |
| | **`intances/`** *(sic — misspelled in source)* | **`instances/`** |
| 14 | `Bulletin Municipal – Intervention Technique et Sécurité Routière.pdf` | `Municipal_Bulletin_-_Technical_Intervention_and_Road_Safety.pdf` |
| 15 | `Bulletin Municipal – Marché de Noël 2023.pdf` | `Municipal_Bulletin_-_Christmas_Market_2023.pdf` |
| 16 | `Bulletin Municipal – Réunion Publique.pdf` | `Municipal_Bulletin_-_Public_Meeting.pdf` |
| 17 | `PV_05102023.pdf` | `Minutes_2023-10-05.pdf` *(PV = procès-verbal = council minutes)* |
| 18 | `PV_15112023.pdf` | `Minutes_2023-11-15.pdf` |
| 19 | `PV_20122023.pdf` | `Minutes_2023-12-20.pdf` |
| 20 | `RÈGLEMENT MUNICIPAL.pdf` | `CITY_REGULATIONS.pdf` |
| | **`projets/`** | **`projects/`** |
| 21 | `Développement de nouvelles pistes cyclables et zones piétonnes (2026).pdf` | `Development_of_new_bike_lanes_and_pedestrian_zones_(2026).pdf` |
| 22 | `Installation d'un système de surveillance urbaine.pdf` | `Installation_of_an_urban_surveillance_system.pdf` |
| 23 | `Installation de panneaux photovoltaïques sur les bâtiments municipaux.pdf` | `Installation_of_solar_panels_on_municipal_buildings.pdf` |
| 24 | `Projet d'Amélioration des Espaces Verts.pdf` | `Green_Spaces_Improvement_Project.pdf` |
| 25 | `Projet de Création du Centre Culturel Innovant.pdf` | `Innovative_Cultural_Center_Creation_Project.pdf` |
| 26 | `Projet de Modernisation de l eclairage public.pdf` | `Public_Lighting_Modernization_Project.pdf` |
| 27 | `Projet de Rénovation de la Voirie Centrale.pdf` | `Central_Road_Renovation_Project.pdf` |
| 28 | `Réaménagement de la place du Marché.pdf` | `Market_Square_Redevelopment.pdf` |
| 29 | `Suivi du projet de Centre Culturel Innovant.pdf` | `Innovative_Cultural_Center_Project_Follow-up.pdf` |
| 30 | `projets_2024.csv` | `projects_2024.csv` *(translate headers + values inside)* |

---

## 2. Glossary (FR → EN-US)

| French | English (US) |
|--------|--------------|
| Trifouillis-sur-Loire | **Willow Creek** |
| Mairie / Hôtel de ville | **City Hall** (the institution: *Willow Creek City Hall*) |
| Commune / municipalité | town / municipality |
| Maire : **Madame Pétillante Rigolade** | Mayor: **Mrs. Sparkle Merriweather** *(see §3 — keep consistent)* |
| Conseil municipal | City Council |
| Procès-verbal (PV) | Minutes |
| Règlement municipal | City Regulations / Municipal Code |
| Voirie | roads / public works |
| État civil | Vital Records |
| Démarches administratives | administrative procedures |
| Place du Grand Chêne | **Grand Oak Square** |
| Déchetterie / ramassage des ordures | recycling center / waste collection |
| Pistes cyclables | bike lanes |
| Devise **€** | convert to **$** (keep the same numbers, 1:1) |
| Téléphone `01 23 45 67 89` | a US format placeholder, e.g. **(555) 123-4567** |
| Site web `trifouillis-mairie.fr` | **willowcreek.gov** |
| Dates `JJ/MM/AAAA` | US format `MM/DD/YYYY` (or ISO `YYYY-MM-DD`) |

**Tone:** the source is deliberately whimsical/satirical (silly event names, a jovial mayor).
Preserve that playful tone in English — don't flatten it.

---

## 3. Consistency anchors (MUST match the already-localized code & notebooks)

These facts are **already hard-set in the repo** (notebooks / prompts). The corpus you generate
must use the **same** values — or, if you change a value, update it in BOTH the corpus and the file noted.

- **Town / institution:** Willow Creek · Willow Creek City Hall · website `willowcreek.gov`
- **Mayor:** **Mrs. Sparkle Merriweather** — used in [`notebooks/P2C4_RAGASS.ipynb`](notebooks/P2C4_RAGASS.ipynb).
  *(If you prefer another name, change it there too.)*
- **City Hall hours (canonical):** Monday–Friday, **8:30 AM – 12:00 PM**; closed Sat/Sun
  — used in P2C4. *(Note: the P1C4 embedding demo uses an illustrative "8:30 AM–5:00 PM"; that
  one is just a similarity example, not corpus ground truth.)*
- **Christmas Market 2023:** Dec **16–17, 2023**, at **Grand Oak Square**, **10 AM – 8 PM**.
- **2026 mobility plan:** ~**2.5 km** of new secure bike lanes.
- **2023 projects & budgets** (reproduce these in the `projects/` PDFs + `projects_2024.csv`,
  amounts in **$**, dates `YYYY-MM-DD`):

  | Project | Start | Budget |
  |---------|-------|--------|
  | Central road renovation | 2023-09-01 | $750,000 |
  | Public lighting modernization (LED) | 2023-10-15 | $300,000 |
  | Green spaces improvement | 2023-11-10 | $450,000 |
  | Elementary school renovation | 2023-08-20 | $650,000 |
  | Municipal Sports Center creation | 2023-07-15 | $950,000 |
  | Market Square redevelopment | 2023-10-05 | $500,000 |
  | Urban surveillance system | 2023-12-01 | $400,000 |
  | Bike lanes development | 2023-09-15 | $350,000 |
  | Advanced selective sorting system | 2023-11-20 | $300,000 |

- **Mayor's 2025 New Year address** (the `.wav`): the narrative mentions closing the town's
  **train station** and switching to a modern **electric bus** fleet, plus ecology/sustainability
  commitments — keep this storyline when re-recording in English.

---

## 4. Per-format tips

- **PDF / DOCX:** translate + culturally adapt the body; recreate the file (e.g. Google Docs →
  export PDF/DOCX). Keep tables (hours, budgets) intact.
- **CSV (`budget_2024.csv`, `projects_2024.csv`):** translate column headers AND row values;
  convert € → $; keep the delimiter consistent (the loader tries `,` then `;`).
- **PNG (market poster) / WEBP (logo):** recreate the image with English text (any image tool).
- **WAV (mayor's address):** re-synthesize or re-record an English voiceover of the translated script.

After regenerating everything:
```bash
python indexer.py          # rebuilds vector_db/ (faiss_index.idx + document_chunks.pkl)
```
and the SQLite `database/interactions.db` repopulates as the app is used.

---

## 5. Ready-to-paste prompt for ChatGPT

```
You are localizing a French RAG course corpus into US English.
Town: "Trifouillis-sur-Loire" -> "Willow Creek". Institution -> "Willow Creek City Hall".
Mayor "Madame Pétillante Rigolade" -> "Mrs. Sparkle Merriweather".
Currency € -> $ (keep the same numbers). Website -> willowcreek.gov.
Phone -> US format like (555) 123-4567. Dates -> MM/DD/YYYY or YYYY-MM-DD.
Keep the playful, satirical tone (silly event names, jovial mayor).
Stay consistent with these fixed facts: City Hall hours Mon–Fri 8:30 AM–12:00 PM;
Christmas Market Dec 16–17 2023 at Grand Oak Square 10 AM–8 PM; 2026 plan ~2.5 km of new
secure bike lanes; and the 2023 projects/budgets table I will paste.

I will paste one document at a time. For each: translate and culturally adapt it to a small
US town, preserve structure (headings, tables, amounts), and return the full English version.
Here is the first document:
<paste content>
```
