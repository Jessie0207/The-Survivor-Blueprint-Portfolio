# Blueprint Graph Exports

Each numbered folder contains a collection guide for one documentation module. The module folder names are documentation categories, not Unreal asset names.

**Current status: module guides are present; no original graph-text exports have been supplied.**

For each graph, add:

1. The node text copied from the current Unreal graph, saved as UTF-8 `.txt`.
2. A readable screenshot in `IMAGES/`, including the event/function entry and the result.
3. The BlueprintUE URL after publishing that same node text.
4. The source asset/package path and graph name in the checklist.

Do not place prose or pseudocode in a `.txt` file and label it as an Unreal export. Separate functions, macros and event chains into separate files. Keep screenshots of timeline curves, widget layout and required settings alongside the node evidence.

The per-module guide supplies the expected text filenames. The repository does not create empty source files or fake BlueprintUE links.
