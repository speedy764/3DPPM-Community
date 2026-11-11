# 3DPPM – Frequently asked questions (FAQ)

[Deutsch](FAQ_DE.md)

Answers about setup, updates and daily work with 3DPPM. The notes below the answers identify the relevant sections of the offline manual.

- [Installation, database and updates](#faq-installation)
- [Back up and preserve data](#faq-data)
- [Profiles, experiments and parameters](#faq-profiles)
- [3MF, evaluation and support](#faq-workflow)

<a id="faq-installation"></a>

## Installation, database and updates

<a id="faq-mysql"></a>

### Does 3DPPM support external databases such as MySQL?

Yes. In addition to a local SQLite file, 3DPPM supports an external MySQL database. Select Settings → Database → External (MySQL). Your server administrator must provide a dedicated empty database; 3DPPM does not create a server database or transfer your SQLite data automatically. Enter and test the connection, then restart after setup. When using several computers, the associated files also require a shared, accessible Data directory.

**Detailed instructions in the offline manual** — Settings → Set up a central MySQL database.

<a id="faq-inplace-update"></a>

### How do I update 3DPPM in its existing application folder (in-place update)?

Open Settings → General → Updates. Check for updates or select a complete downloaded ZIP. Close other instances and MySQL clients. Review the version and schema, then confirm Back up and install update. The wizard backs up the application, active database and settings before replacing files; personal data, images and configuration are retained. Replacing only the EXE is insufficient. If your previous version has no wizard, follow the instructions for manually transferring the complete application folder.

**Detailed instructions in the offline manual** — Settings → Updating 3DPPM.

<a id="faq-master-data-update"></a>

### How do I update the master data package?

Back up the database first. Select Settings → Updates → Master data package and open the JSON file. Compare Before and After in the preview, then confirm the displayed changes. The package adds or updates records using stable IDs and does not delete existing records or relationships. Therefore also review changes to your own entries sharing an ID. Entries with the same name but a different ID are not merged automatically; conflicts abort the import. Check the affected master data afterwards. A master data package does not update the application.

**Detailed instructions in the offline manual** — Master data – shared foundations → Transfer a master-data pack to a second installation.

<a id="faq-permission-denied"></a>

### Why does startup under Program Files report “Access denied” (WinError 5)?

The portable application needs a writable application folder for its local files and settings. A protected folder such as C:\Program Files can prevent writes. Extract the complete package into a folder where your Windows user can write. For an existing installation, back up data and settings first and check the configured paths afterwards.

**Detailed instructions in the offline manual** — Getting started and preparation → 1. Unpack and launch the application.

<a id="faq-data"></a>

## Back up and preserve data

<a id="faq-backup"></a>

### What should I back up: the database, files or settings?

Each of the three areas has its own purpose. The database contains structured application data; profile, image and experiment files are stored separately. The configuration contains settings and paths. Use the available backup types under Settings → Backup and keep corresponding snapshots together. A database backup does not replace a backup of associated files, including when using MySQL.

**Detailed instructions in the offline manual** — Settings → Three separate backup types.

<a id="faq-move-database"></a>

### How do I keep using my existing database after changing folders?

Create a database backup first and close 3DPPM. Transfer the backed-up database into a dedicated data folder using the documented procedure. Then select the target folder under Settings → Database and choose to use the existing database. Selecting an empty folder does not move your previous database. After restarting, check familiar profiles and experiments and configure the separate file storage accordingly.

**Detailed instructions in the offline manual** — Settings → Use an existing database in another directory.

<a id="faq-profiles"></a>

## Profiles, experiments and parameters

<a id="faq-profile-experiment"></a>

### What is the difference between a profile, an experiment and a parameter definition?

A parameter definition in master data describes a setting with its data type, range and slicer mapping. A profile combines the printing environment with concrete parameter values and rating criteria. An experiment documents an individual test with its own parameter snapshot, results and measurements. New experiments capture the profile state; later profile changes do not alter existing experiment snapshots.

**Detailed instructions in the offline manual** — Profile data – the foundation of your experiments → Distinguish profile, parameter definition and experiment.

<a id="faq-missing-parameters"></a>

### Why is a parameter missing from the selection for my profile?

Check that its definition is active and mapped to the selected slicer, and check the chosen profile kind: printer, process or filament. Parameters already used or selected on the right are hidden on the left. Also review the search, Source filter and selected base profile. A missing base value alone does not exclude an applicable active slicer definition: it can appear with source Slicer and its master-data default value.

**Detailed instructions in the offline manual** — Profile data – the foundation of your experiments → Parameter sources and technical names.

<a id="faq-parameter-source"></a>

### What does the parameter source “Base profile” or “Slicer” mean?

Base profile means that the effective value comes from the selected base profile, including inheritance. Slicer identifies additional applicable definitions from profile-parameter master data for which no valid base value is available. Their initial value comes from the master-data default and is not read from the running slicer application. The Source filter offers All, Base profile and Slicer.

**Detailed instructions in the offline manual** — Profile data – the foundation of your experiments → Parameter sources and technical names.

<a id="faq-technical-name"></a>

### How do I find a parameter by its technical name?

Enter the technical name in the available-parameter search, for example initial_layer_acceleration. The search includes this column even when it is hidden. You can also show Technical name using the column selector.

**Detailed instructions in the offline manual** — Profile data – the foundation of your experiments → Parameter sources and technical names.

<a id="faq-percent-values"></a>

### Can I enter absolute values or percentages for parameters?

Parameters that support both formats allow absolute or relative values, for example 6000 or 15%. The percent sign remains part of the value; no unsolicited conversion takes place. The definition’s data type and range still apply. For scalar base values supplied as a list, the first entry provides the initial value; actual list parameters remain lists.

**Detailed instructions in the offline manual** — Profile data – the foundation of your experiments → Base values, lists and percentages.

<a id="faq-workflow"></a>

## 3MF, evaluation and support

<a id="faq-3mf-mapping"></a>

### Why are printer, nozzle or filament missing after importing a 3MF?

A file value may be missing or may not have an unambiguous master-data mapping. Review unresolved entries in the comparison and the rules under Master data → 3MF master data mappings. Correct the applicable rule and read the same file again to check the result.

**Detailed instructions in the offline manual** — Master data – shared foundations → Check and correct 3MF master-data mappings.

<a id="faq-object-assignment"></a>

### How do I assign an object on a specific build plate to an experiment?

Open object assignment for the experiment, select the appropriate build plate and then the object. After saving, check the assignment on the experiment. The same procedure lets you change or remove an existing assignment. The walkthrough demonstrates this using a 3MF with two build plates.

**Detailed instructions in the offline manual** — Prepare and document experiments → Assign objects and build plates.

<a id="faq-3mf-export"></a>

### Can I export several experiments together as a 3MF?

Yes, when the experiments are compatible for a shared export. A 3MF has one common printer state; different printer values or conflicting base states can prevent the export. Review the messages and export references. You can also export a single experiment, then inspect the generated file’s build plates, objects and settings in the 3MF analyzer.

**Detailed instructions in the offline manual** — Profile data – the foundation of your experiments → Export an experiment or an entire project as 3MF.

<a id="faq-blocked-action"></a>

### Why is an action or status transition blocked?

Workflow rules can make a transition depend on prerequisites, such as complete information or a rating. Read the message for the blocked action and supply the required data. Rules are configured in settings; the status transition is performed on the profile or experiment.

**Detailed instructions in the offline manual** — Settings → Workflow rules.

<a id="faq-rating"></a>

### Why does changing criterion weights affect the overall score?

The overall score uses the individual criterion ratings with their respective weights. A more heavily weighted criterion has a larger influence on the result. Review criteria, weights and individual ratings together and use the preview before comparing results.

**Detailed instructions in the offline manual** — Ranking and criterion weighting → Read the weighted overall score.

<a id="faq-help-zoom"></a>

### Can I use and zoom the help independently of the application?

The help window can be operated independently. Use Ctrl and the mouse wheel to change help text size; the application keeps its own scaling. Use Contents, Search or Index to move to a topic. The help chapter explains the controls and image viewer in detail.

**Detailed instructions in the offline manual** — Using Help and zooming independently → Navigate the manual.

<a id="faq-report-error"></a>

### How do I report an error, and which files should I include?

If needed, enable debug logging under Settings → General and restart 3DPPM. Reproduce the error and note the version, time, initial state, steps, expected result and actual result. Include a readable screenshot and copies of 3DPPM.log, 3DPPM-debug.log and 3DPPM-crash.log from logs. The detailed guide explains missing or empty files and links to the public Community issue; check attachments for confidential content before uploading.

**Detailed instructions in the offline manual** — Report errors and use debug logging → Report template.
