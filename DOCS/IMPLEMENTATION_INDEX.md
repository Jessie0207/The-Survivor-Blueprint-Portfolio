# Implementation Index

## Evidence Boundaries

This package was prepared from the project’s development discussion and reviewed portfolio graph excerpts. The current Unreal project and native assets have not been inspected directly. The descriptions separate documented behaviour from names or wiring that still require export.

## Names Supported by Reviewed Graph Excerpts

| Location | Identifiers | What is documented |
| --- | --- | --- |
| XR Pawn | UpdateTarotFocus; TryInteract; TryOpenFocusedDoor; FocusedTarotCard | Targeting and the card-first interaction dispatcher |
| Tarot card | BP_TarotCard; ActivateTarotCard; IsActivated | Activation event and state check |
| Card transition | ActiveCardIndex; ReturnFadeColor; Open Level | Selection/transition values and map entry |
| Card restoration | Event BeginPlay; CompletedCardCount; ActiveCardIndex; CardIndex | Progress checks; exact full predicate still needs the source |
| Narrative sequence | ShowNow | Display call; owning class must be recorded |
| Feast scene | On Dish Stabbed (TRG_StabDish); Sequence; FinalDish; TL_DishHit; SetWorldLocation | Accepted action and dish feedback |
| Chandelier movement | TL_ChandelierFall; Lerp (Vector); SetActorLocation; BP_FeastChandelier | Timeline-driven positional fall |

Node titles may display spaces while the asset or variable identifier does not. Keep the exact spelling from the exported graph when filling the manifest.

## Historical Locators to Verify

These help locate the current logic but are not asserted to be the final asset names:

- BP_ExitDoor, OpenDoor, TL_OpenDoor.
- TarotFocusOn and the hover overlay material.
- KnifeTip, StabZone and the class owning the stab trigger.
- The specific project GameInstance class and any completed-card collection.
- The Survivor card/shrine class and the actual ending controller/widget names.

## Behaviour Supported by the Current Project Discussion

- Desktop input was added inside the VR-based pawn.
- Five encounters return to The Shop and their corresponding cards disappear.
- Flight uses a blue opening, a door that appears on approach, and the player going first.
- Prohibition stages the stopping of environment, music and travel.
- Reversal exchanges positions without removing the hierarchy’s spatial structure.
- Feast includes offering, diner activation, the knife action and chandelier fall.
- The Feast narration/action timing was revised; no numerical test outcome is inferred.
- The ending includes the sixth card, fire and blackout/title presentation.

## Points Requiring the Current Source

| Point | Evidence to collect |
| --- | --- |
| Encounter order | Actual card-availability and completion predicates; do not infer arbitrary ordering from a count |
| Completion persistence | Both the write path and the Shop/card read path |
| Stab timing fix | The present enabling/sequencing logic; do not substitute an older proposed collision gate |
| VR versus desktop inputs | Actual input bindings and receiver calls, including per-level Pawn overrides |
| Movement, highlight and widget details | Current functions, material calls, component settings and curve values |
| Ending trigger | The true all-complete condition, not an assumed final card index |

## Dependencies That Node Copy Alone Does Not Document

Record relevant variables and their types/defaults, component hierarchies, collision settings, input assets, timeline curves, widget layouts/animations, Blueprint interfaces, structures/enums, actor references, map context and custom trace channels.

The source register is a collection list, not proof that these assets have already been delivered. One native asset may implement several modules; it should be stored once and referenced many times.
