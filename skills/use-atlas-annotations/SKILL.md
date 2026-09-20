---
name: use-atlas-annotations
description: Create native dimensions, tags, notes and basic detail content in standalone Revit drawing views, using Atlas Core for work ownership and inspection.
---

# Atlas Annotations

If Atlas tools cannot connect, follow the installed Atlas Core skill's agent-assisted installation reference. When setup is authorized, the agent runs Core's packaged helper; do not ask the user to configure tokens or install another Annotations engine. If Core is absent, install it through the selected marketplace first.

Follow the requested change intent. An ordinary edit does not require or automatically create a formal drawing revision, revision cloud, issue date or revision-table entry. Preserve existing issue history while making authorized edits. A formal revision includes only the requested change documentation and issue metadata; discover supported native revision/cloud actions before promising them, and report missing capability explicitly. Do not substitute static notes for native revision history. Tool `expected_revision` and model/presentation counters are concurrency controls, not drawing issue numbers.

For existing-sheet edits, start with Core `drawing_context` for the selected sheet; it returns placed views, titleblock instances and a bounded annotation page. `atlas_work.open` takes an RVT `path`; `create` takes an RTE `template_path`. New semantic keys and delivery basenames are lowercase letters/digits/underscores starting with a letter, at most 64 characters. Human-readable names remain separate. Adopt only objects you intend to edit.

Compile final requirements and bindings before saving, capturing and reviewing. `workflow_id` identifies the whole delivery; each new continuation is a different immutable request. Omit top-level `operation_id` on a new continuation. Reusing it retrieves only that original request's historical outcome, or rejects changed inputs; it does not refresh old checks. Checkpoint before reading `drawing_preservation`. It compares current saved elements with the signed pre-authoring starting copy and verifies original file bytes separately; initial Revit load/save normalization is outside its scope. Historical work without that snapshot remains incomplete. Model revision zero is not preservation proof.


Use `spatial_tag_number` for a requested room/space number without prescribed label formatting. It verifies the live native target's number and its presence in tag text; bind the intended host target or linked target explicitly. It does not prove every family label field's dependency. Use strict `tag_text` when exact displayed text is required. Do not guess label concatenation before inspection. Requirement `patch` changes selected criteria while preserving the rest; `amend` replaces the full list. Neither silently erases scope changes to the original engineering brief.

For edits, inspect `drawing_dependencies` and adopt existing annotations explicitly. Replacement needs the expected native identity; invalid references or removal of unrelated dependents roll back. Semantic keys persist through supported replacements. Field discovery returns exact parameter identities and current values: use guarded edits, not matching names alone.

This candidate requires Atlas Core and a matching admitted native engine. It can use existing project views without Atlas Sheets. Family is only needed when creating new annotation families, not using existing ones.

Start from the engineering brief and inspect available views, annotation types and targets through Core. Prefer compatible project styles. Discover `RoomTagType` and `SpaceTagType` explicitly; they are not ordinary `FamilySymbol` types. If suitable content is absent, inspect Core `drawing_standards` for installation-local architectural/MEP content, then use `load_standard` with the selected family name and template hash. Supplied RFAs use `load` with provenance. No Autodesk content is redistributed by Atlas. Discover the exact action contract through `atlas_catalog`; unsupported combinations are not an invitation to use scripts or rewrite records.

For native linear/chained dimensions and spot elevations, use `atlas_annotations_dimensions.references` to discover actual geometric references in the intended view. Select the intended faces/edges explicitly. Reference candidates include geometry kind and host-coordinate positions where available; ambiguous geometry needs inspection, not nearest-face guessing. Native dimension readback supplies actual values and references. Dimensions are unlocked by default. Text saying a distance is not an associative dimension.

For linked elements, identify the exact local link instance and linked element unique identity. Loaded first-level RVT links are read-only. Reacquire references after link changes. Linked space tags are explicitly unsupported by this candidate; do not substitute unrelated host tags.

`atlas_annotations_tags` uses existing compatible native types for element, room and space tags. Element tags require a supported 2D or locked orthographic 3D view. Inspect rendered text and orphan status after changes. Bind `tag_text` requirements to the actual annotation; for a linked target use `tag_reference` with the host link semantic key and the linked element unique identity. Correct-looking text cannot prove the correct target. Preserve target identity when repositioning a tag.

`atlas_annotations_notes` handles text, detail curves, view-based symbols and filled/masking regions, plus provenance-checked family loading. Loading does not silently replace an existing family. Native geometry, visibility and view compatibility still constrain detail placement.

`atlas_annotations_layout` moves selected annotation content in paper millimetres and reports projected bounding-box overlaps. It must not move model elements. A clean overlap report is only a screening result: review the drawing at issue scale for hidden leaders, cramped text and unclear targets.

Use expected revisions and stable semantic keys. Recover the same operation after response loss; do not duplicate annotations. Leave failed or missing references incomplete. Core owns evidence and delivery; do not claim that tag creation, parameter presence or an exported file establishes whole-brief acceptance.

Notes, detail curves and compatible view-based symbols may be placed directly on a sheet; their explicit millimetre coordinates then refer to paper. Model dimensions and element tags require an appropriate drawing view. Inspect inherited annotation and titleblock sizes at issue scale.
