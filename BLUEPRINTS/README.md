# Native Blueprint Archive

**Current status: no native source assets have been supplied in this package.**

Add the current project-specific `.uasset` files below `Content/`, preserving each asset’s original path relative to the source project’s Content directory. Do not flatten or rename assets to match the documentation module titles.

For example, an asset whose actual package path is `/Game/Interaction/BP_TarotCard` would be archived as `Content/Interaction/BP_TarotCard.uasset`. This is an example of the path rule, not a claim about this project’s actual folder names.

One asset may serve several documentation modules. Store the native asset once and reference it from those modules.

Actor assets alone do not include the Level Blueprints for the five maps and The Shop. Those graphs must also be exported, and their map context recorded. If maps are included, preserve their native `.umap` files and any associated dependencies needed for the intended use.

This folder is a source inspection archive. Copying selected binaries into it does not make a runnable project. For reuse in another Unreal project, use Unreal’s Migrate workflow with the necessary dependencies and matching engine/plugin configuration.

Record native paths in [NATIVE_ASSET_REGISTER.csv](../DOCS/NATIVE_ASSET_REGISTER.csv), and follow the [Chinese export guide](../DOCS/EXPORT_GUIDE_ZH.md).
