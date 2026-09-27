# The Survivor — Technical Blueprint Portfolio

**Unreal Engine 5.7 · VR experience with desktop input support**

The Survivor is an immersive experience exploring how individuals become a crowd. Inspired by five crowd types in Elias Canetti’s *Crowds and Power*, it translates collective impulses into spatial conditions, narrative cues and player actions. The player repeatedly returns to The Shop, where disappearing tarot cards record completed encounters. A sixth card introduces the ending.

This repository documents the project-specific Blueprint work: desktop input added within the VR pawn, card targeting and activation, spatial narrative, five encounter systems, session progress and the final Shop sequence.

> **Archive status:** the documentation and export structure are prepared. Native Blueprint assets, node-text exports, screenshots, demo URLs and BlueprintUE links have not yet been added to this package. It is not a runnable Unreal project or a complete source release.

## Project Foundation and Contribution

The project starts from Epic Games’ VR template. I extended the XR Pawn with desktop input and custom interaction logic, then connected the five encounters through The Shop, narrative events and completion records. Inherited tracking, baseline grabbing and locomotion are credited to the template. The modules below focus on additions and modifications made for this project.

The module numbers are a reading order for the technical archive. They do not specify the order in which encounters can be selected in the current build.

## Demonstrations

| Version | Link |
| --- | --- |
| VR demonstration | URL to be added from the final portfolio video |
| Desktop demonstration | URL to be added from the final portfolio video |

## Experience and Technical Responsibilities

| Part | Player experience | Technical responsibility |
| --- | --- | --- |
| The Shop | Select a tarot card; return after an encounter | Targeting, activation, map entry and card state restoration |
| 01 Baiting | Ring the bell around a shared target | Bell interaction, narrative response and completion |
| 02 Flight | Approach the blue slit and cross the revealed door | Door reveal, targeting, opening and passage detection |
| 03 Prohibition | Travel with the scene, then experience staged stillness | Travel control and sequential environment/audio changes |
| 04 Reversal | Turn the hourglass and exchange positions | Interaction, rotation and the crown/scene response |
| 05 Feast | Offer the dish, join the feast and pierce the food | Placement, diners, knife detection, narration and chandelier fall |
| Ending | Return to the burning Shop and encounter The Survivor | Completion check, sixth-card reveal, fire, blackout and title |

## Repository Guide

| Location | Contents |
| --- | --- |
| [BLUEPRINTS](BLUEPRINTS/README.md) | Native assets, with original Content-relative paths preserved when added |
| [GRAPHS](GRAPHS/README.md) | One folder per module for node-text exports and BlueprintUE links |
| [IMAGES](IMAGES/README.md) | Blueprint screenshots, timeline curves, settings and in-game results when added |
| [Technical index](DOCS/IMPLEMENTATION_INDEX.md) | Evidence boundaries, known names and export dependencies |
| [Graph export checklist](DOCS/GRAPH_EXPORT_CHECKLIST.csv) | One record per requested graph export |
| [Chinese export guide](DOCS/EXPORT_GUIDE_ZH.md) | Step-by-step collection and GitHub publishing instructions |
| [Credits](DOCS/CREDITS.md) | Template, tools and third-party asset attribution |

## Module Index

| Module | System | Graph archive |
| --- | --- | --- |
| 01 | XR Pawn Extension and Desktop Input | [Export guide](GRAPHS/01-shared-xr-pawn/README.md) |
| 02 | Tarot Targeting and Focus Feedback | [Export guide](GRAPHS/02-tarot-focus/README.md) |
| 03 | Interaction Dispatch and Door Fallback | [Export guide](GRAPHS/03-interaction-dispatch/README.md) |
| 04 | Tarot Activation and Level Entry | [Export guide](GRAPHS/04-card-activation/README.md) |
| 05 | Encounter Completion and Shop State Restoration | [Export guide](GRAPHS/05-progress-and-return/README.md) |
| 06 | Spatial Narrative Cues and Audio Timing | [Export guide](GRAPHS/06-narrative-system/README.md) |
| 07 | Baiting — Bell Interaction and Target Confirmation | [Export guide](GRAPHS/07-baiting-bell/README.md) |
| 08 | Flight — Door Reveal and Passage | [Export guide](GRAPHS/08-flight-door/README.md) |
| 09 | Prohibition — Automatic Travel and Staged Stillness | [Export guide](GRAPHS/09-prohibition-freeze/README.md) |
| 10 | Reversal — Hourglass Rotation and Crown Transfer | [Export guide](GRAPHS/10-reversal-hourglass/README.md) |
| 11 | Feast — Dish Placement and Diner Activation | [Export guide](GRAPHS/11-feast-offering/README.md) |
| 12 | Feast — Knife Handling and Stab Detection | [Export guide](GRAPHS/12-feast-knife/README.md) |
| 13 | Feast — Stab Response and Narrative Timing | [Export guide](GRAPHS/13-feast-narrative-response/README.md) |
| 14 | Feast — Chandelier Fall | [Export guide](GRAPHS/14-feast-chandelier/README.md) |
| 15 | The Shop Ending — Survivor Reveal and Fire Progression | [Export guide](GRAPHS/15-shop-ending-fire/README.md) |
| 16 | Ending — Blink Transition and Final Title | [Export guide](GRAPHS/16-blink-and-title/README.md) |

---

## Module 1: XR Pawn Extension and Desktop Input

Desktop controls were added within the pawn used for the VR experience. This lets the project be demonstrated with a headset or with keyboard and mouse while retaining its VR foundation.

**Blueprint location:** The project XR Pawn; exact asset path to be recorded during export.

**Graph evidence:** [Module export guide](GRAPHS/01-shared-xr-pawn/README.md). **BlueprintUE:** pending source export.

### System Overview

- The custom work concerns desktop movement and viewing, project interaction entry points, and the connection between input and scene actions.
- The VR template provides the starting pawn, tracked camera, motion controllers and baseline grab/locomotion behaviour. These inherited systems are distinguished from the project-specific additions.
- Both input modes participate in the same experience, but their actions do not have to map one-to-one. The exported input graphs should show the actual paths used by each mode.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| XR Pawn Event Graph | Hosts the project-specific desktop input additions and their connections to interaction logic. |
| TryInteract | Project interaction entry point used by the targeting system. |
| Input actions and mapping contexts | Record the actual assets and bindings used in the current build; bindings are not reconstructed from older notes. |

---

## Module 2: Tarot Targeting and Focus Feedback

The targeting system identifies the card under the player’s aim and stores it as the current interaction target.

**Blueprint location:** XR Pawn / UpdateTarotFocus, together with the card focus response.

**Graph evidence:** [Module export guide](GRAPHS/02-tarot-focus/README.md). **BlueprintUE:** pending source export.

### System Overview

- UpdateTarotFocus contains the targeting logic. The relevant export covers trace origin selection, the trace itself, hit interpretation and the update of FocusedTarotCard.
- The card supplies visual focus feedback so that the player can distinguish the selected card from the surrounding shrines.
- Focus loss and switching to a different card belong in the same evidence set. The final material or overlay calls must be taken from the current project.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| UpdateTarotFocus | Updates the interaction target from the current aim. |
| Line Trace By Channel | Queries what the targeting ray hits. |
| FocusedTarotCard | Variable holding the focused card reference; it is not a separate function. |
| Card focus response | Applies and removes the selected-card feedback; exact event/material names await export. |

---

## Module 3: Interaction Dispatch and Door Fallback

A short routing function connects the current target to the appropriate response: activate a focused tarot card, or try the door interaction when no valid card is available.

**Blueprint location:** XR Pawn / TryInteract and TryOpenFocusedDoor.

**Graph evidence:** [Module export guide](GRAPHS/03-interaction-dispatch/README.md). **BlueprintUE:** [View Blueprint — TryInteract](https://blueprintue.com/blueprint/2sl29jkw/)    
### System Overview

- TryInteract checks the FocusedTarotCard reference with Is Valid.
- A valid card receives ActivateTarotCard. The alternative path calls TryOpenFocusedDoor.
- The dispatcher is documented separately from the receiving actors so that the relationship between player input and object response remains readable.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| TryInteract | Dispatches the player interaction request. |
| Is Valid | Checks the current card reference before use. |
| ActivateTarotCard | Calls the selected card’s response. |
| TryOpenFocusedDoor | Handles the door interaction fallback. |

---

## Module 4: Tarot Activation and Level Entry

Activating a card turns a selection into a visible response before the associated crowd scene is loaded.

**Blueprint location:** BP_TarotCard / ActivateTarotCard and its connected response logic.

**Graph evidence:** [Module export guide](GRAPHS/04-card-activation/README.md). **BlueprintUE:** pending source export.

### System Overview

- The activation branch checks activation state and drives the card’s lift, rotation and floating response.
- The transition branch records the active card and return colour in the project’s GameInstance before the map change.
- The graph coordinates the visual transition with Open Level. This is documented as a map change, without claiming seamless streaming or multithreaded Blueprint execution.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| ActivateTarotCard / IsActivated | Entry event and activation-state check. |
| Card response timelines | Drive the lift, rotation and float response; export the actual curve tracks. |
| ActiveCardIndex / ReturnFadeColor | Recorded selection and transition information visible in the reviewed implementation. |
| Delay, camera fade and Open Level | Coordinate the transition into the associated scene. |

---

## Module 5: Encounter Completion and Shop State Restoration

Returning to The Shop removes the card associated with a completed encounter, making absence the visible record of progress.

**Blueprint location:** Project GameInstance, encounter return logic, BP_TarotCard BeginPlay and The Shop completion check.

**Graph evidence:** [Module export guide](GRAPHS/05-progress-and-return/README.md). **BlueprintUE:** pending source export.

### System Overview

- Completion and selection information is held across map loads during the running session. The Shop reads that information when it is loaded again.
- The reviewed card graph includes CompletedCardCount, ActiveCardIndex, CardIndex and the burn/already-burned response. The write side must be archived alongside the read side.
- The exact completion predicate must be preserved from the current source. A count alone should not be described as a verified per-card completion set, nor as proof that arbitrary encounter order is supported.
- GameInstance persistence refers to the current running session. No save-to-disk system is claimed here.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Project GameInstance | Retains session data across map loads. |
| CompletedCardCount / ActiveCardIndex / CardIndex | Fields visible in the progress/card checks; their exact types and write sites belong in the export. |
| BP_TarotCard BeginPlay | Reads progress and restores the card’s visible state. |
| Burn and already-burned response | Removes completed cards without replaying the wrong response on return. |
| All-encounters completion check | Determines when The Shop can begin the ending. |

---

## Module 6: Spatial Narrative Cues and Audio Timing

Spatial text and narration introduce each crowd’s condition, cue the player’s action and describe its consequence.

**Blueprint location:** Current narrative trigger, floating-text actor/widget and their audio calls.

**Graph evidence:** [Module export guide](GRAPHS/06-narrative-system/README.md). **BlueprintUE:** pending source export.

### System Overview

- Narrative cues are placed along the route and within scene response sequences. Their order is part of the encounter design.
- The reviewed implementation uses ShowNow calls to display narrative elements. The trigger, receiving object and associated sound should be archived together.
- The export should include the actual text presentation and timing settings. Camera-facing text, fading or automatic duration calculations are only documented as implemented if they exist in that export.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Narrative trigger | Introduces a cue at the relevant point in the encounter. |
| ShowNow | Display call visible in the reviewed narrative sequence. |
| Floating-text actor / widget | Presents the text in the scene; record the actual asset name. |
| Audio calls and timing | Relate narration to text and interaction; record the current sound references and timing method. |

---

## Module 7: Baiting — Bell Interaction and Target Confirmation

Ringing the bell gives the player an active role in the accusation around the suspended body.

**Blueprint location:** The current bell interaction actor and/or Baiting Level Blueprint.

**Graph evidence:** [Module export guide](GRAPHS/07-baiting-bell/README.md). **BlueprintUE:** pending source export.

### System Overview

- The encounter presents a shared target through spatial narrative cues and the central suspended figure.
- The bell interaction connects the player’s action to sound and the next narrative response. It should be shown with the scene-level receiver if that response is implemented outside the bell actor.
- The completion and return call belongs in the evidence so that the interaction can be traced back to the disappearing card in The Shop.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Bell interaction entry | Accepts the player action; exact event/function name awaits export. |
| Bell sound / scene response | Provides immediate feedback and advances the encounter. |
| Narrative consequence | Connects the bell action to collective accusation. |
| Completion and return | Hands the completed encounter back to the shared progress system. |

---

## Module 8: Flight — Door Reveal and Passage

The blue slit gives the crowd a destination. A door appears on approach, and the player’s passage makes them the first to cross.

**Blueprint location:** The Flight reveal trigger and exit-door blueprint; BP_ExitDoor is a historical locator to verify.

**Graph evidence:** [Module export guide](GRAPHS/08-flight-door/README.md). **BlueprintUE:** pending source export.

### System Overview

- The reveal logic changes the door’s availability as the player approaches the opening.
- Door targeting and interaction connect to the pawn’s TryOpenFocusedDoor path. The export should show how the current VR and desktop inputs reach the door.
- The door’s response, crossing condition and return sequence should remain distinct in the documentation; approaching, opening and crossing are different events.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Proximity / reveal condition | Makes the hidden door available on approach. |
| TryOpenFocusedDoor | Routes the player’s interaction to the door. |
| OpenDoor / opening timeline | Historical graph names for the door response; verify against the current asset. |
| Passage trigger | Detects the relevant crossing and advances completion. |

---

## Module 9: Prohibition — Automatic Travel and Staged Stillness

The player is carried through a moving environment before successive systems stop, turning shared motion into collective refusal.

**Blueprint location:** The spider travel controller and the Prohibition scene sequence.

**Graph evidence:** [Module export guide](GRAPHS/09-prohibition-freeze/README.md). **BlueprintUE:** pending source export.

### System Overview

- The encounter first establishes automatic travel and movement in the surrounding environment.
- The staged response stops birds, water, background music, then the player/spider movement. Remaining ambience separates stillness from a total loss of sound.
- Archive each affected system’s actual control call. A staged freeze should not be described as a verified global pause unless the source really uses one.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Travel controller | Drives the spider/player route; exact motion method awaits export. |
| Freeze sequence | Orders the changes to environmental movement and sound. |
| Bird, water and audio references | Identify which scene systems receive the stop commands. |
| Player/spider movement control | Applies the final movement restriction within the encounter. |

---

## Module 10: Reversal — Hourglass Rotation and Crown Transfer

Turning the hourglass exchanges the ruler and subject positions while leaving the tiered hierarchy of the scene intact.

**Blueprint location:** The interactable hourglass and the Reversal scene response.

**Graph evidence:** [Module export guide](GRAPHS/10-reversal-hourglass/README.md). **BlueprintUE:** pending source export.

### System Overview

- The interaction begins at the hourglass. Its response drives the visible reversal rather than simply playing an unrelated animation.
- The scene’s crowned and mirrored figures communicate the transfer of position and power. The crown transfer and relevant narration should be linked to their actual events.
- The exported timelines or rotation logic should show the pivot and space in which rotation occurs. Exact timing and transforms must come from the source.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Hourglass interaction entry | Receives the request to turn the hourglass. |
| Rotation driver | Controls the turn; record the actual timeline/function and transform nodes. |
| Crown / figure response | Connects the turn to the change in position. |
| Narrative and completion calls | Coordinate the scene consequence and return. |

---

## Module 11: Feast — Dish Placement and Diner Activation

The player brings the final dish into the scene. Its placement activates the waiting diners and begins the next stage of the feast.

**Blueprint location:** The Feast offering trigger/Level Blueprint, FinalDish and the diner animation calls.

**Graph evidence:** [Module export guide](GRAPHS/11-feast-offering/README.md). **BlueprintUE:** pending source export.

### System Overview

- The offering is detected at the appropriate place in the route and the dish is moved to its scene position.
- The response activates the twelve seated figures, connecting the player’s contribution to the crowd’s movement.
- The following narrative and lighting changes should be exported with their real order. This stage is separate from the later knife action.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Offering trigger | Detects arrival of the player/dish at the required location. |
| FinalDish placement | Moves the offering to its target position using the current placement driver. |
| Diner animation calls | Start the seated figures’ response. |
| Next-stage cue | Prepares the narrative and scene for the knife interaction. |

---

## Module 12: Feast — Knife Handling and Stab Detection

The knife interaction converts the player’s physical motion into the event that advances the feast.

**Blueprint location:** Current knife/hand setup and the receiving stab target or trigger.

**Graph evidence:** [Module export guide](GRAPHS/12-feast-knife/README.md). **BlueprintUE:** pending source export.

### System Overview

- The knife’s relation to the tracked hand is part of the VR interaction. The desktop path should be documented separately wherever its input differs.
- The receiving target determines when the knife action counts as a stab and sends the event to the scene response.
- The source export must include the actual collision/validity conditions and repeat-trigger protection, if present. None of these checks are inferred merely from the visual result.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Knife / hand relationship | Defines how the action is performed in the VR build. |
| Stab target detection | Recognises the accepted knife action; exact component names await export. |
| Accepted-stab event | Signals the Feast sequence when the action is accepted. |
| Availability and repeat checks | Document the actual conditions present in the current graph. |

---

## Module 13: Feast — Stab Response and Narrative Timing

The accepted stab coordinates the dish response, narration and the later chandelier fall.

**Blueprint location:** Feast scene graph receiving On Dish Stabbed (TRG_StabDish).

**Graph evidence:** [Module export guide](GRAPHS/13-feast-narrative-response/README.md). **BlueprintUE:** pending source export.

### System Overview

- The reviewed scene graph receives On Dish Stabbed from TRG_StabDish and dispatches the following responses.
- TL_DishHit drives the dish feedback, while sound and ShowNow calls deliver the consequence narration.
- A timing revision separated narration, the player’s stab and the chandelier’s fall after an earlier sequence allowed their responses to overlap. The revision is recorded as a development change, without inventing test statistics.
- Export the present timing mechanism as implemented; a particular gate, timer or collision-toggle solution is not assumed.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| On Dish Stabbed (TRG_StabDish) | Scene-level entry for the accepted action. |
| Sequence | Dispatches execution outputs in order; it is not a multithreading mechanism. |
| TL_DishHit / FinalDish / SetWorldLocation | Drive the visible dish response in the reviewed graph. |
| Sound playback / ShowNow / timing calls | Present the consequence and schedule the following stage. |

---

## Module 14: Feast — Chandelier Fall

The chandelier fall gives the final action of the feast a large spatial consequence.

**Blueprint location:** The graph driving BP_FeastChandelier with TL_ChandelierFall.

**Graph evidence:** [Module export guide](GRAPHS/14-feast-chandelier/README.md). **BlueprintUE:** pending source export.

### System Overview

- The reviewed fall is driven by TL_ChandelierFall and position interpolation.
- Lerp (Vector) uses the starting and target positions, and SetActorLocation applies the result to the chandelier.
- The start call, curve and completion output are archived together so that the movement can be related to narration and the return sequence.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| TL_ChandelierFall | Outputs the fall interpolation value over time. |
| Lerp (Vector) | Interpolates between the two position values. |
| SetActorLocation | Applies the position to the chandelier actor. |
| BP_FeastChandelier reference | Identifies the actor receiving the movement. |

---

## Module 15: The Shop Ending — Survivor Reveal and Fire Progression

After the five encounters, the recurring hub becomes the setting of the ending. The sixth card appears as the familiar room is transformed by fire.

**Blueprint location:** The Shop ending controller/Level Blueprint and the referenced survivor card, lights and fire systems.

**Graph evidence:** [Module export guide](GRAPHS/15-shop-ending-fire/README.md). **BlueprintUE:** pending source export.

### System Overview

- The completed-encounters condition starts the final Shop sequence. The exact condition belongs to the exported source, not a guessed final-level index.
- The sixth card and its associated scene response are revealed. The fire progresses from the unburned room to initial flames and a full blaze.
- The project-specific contribution is the timing and integration of narration, light and fire into the ending. Externally sourced fire assets should be attributed separately.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Ending entry condition | Receives the completion result from the progression system. |
| Survivor card / shrine reveal | Changes visibility and any implemented presentation response. |
| Fire activation sequence | Controls the staged introduction of fire in the room. |
| Lighting and narrative calls | Coordinate the transformation of the recurring hub. |

---

## Module 16: Ending — Blink Transition and Final Title

Alternating darkness and visibility closes the burning Shop sequence, followed by the title The Survivor on a black screen.

**Blueprint location:** Current ending screen/fade controller and the final title widget.

**Graph evidence:** [Module export guide](GRAPHS/16-blink-and-title/README.md). **BlueprintUE:** pending source export.

### System Overview

- The ending coordinates the repeated blackout with the remaining narration and audio.
- The final state presents the project title in darkness. The archive should include both the triggering graph and the widget/camera-fade implementation actually used.
- The screenshots and footage serve as the visual result; exact delays, opacity curves and input restrictions are documented only from the current build.

### Core Blueprint Elements and Roles

| Element | Role |
| --- | --- |
| Blink / fade driver | Alternates the visible scene and darkness using the current implementation. |
| Timing sequence | Relates each blackout to the ending’s narration and sound. |
| Final title widget | Presents the final title and its animation, if any. |
| Terminal state | Records how the experience ends after the title is shown. |

---

## Reading and Reuse

The module descriptions are based on the documented project behaviour and reviewed graph excerpts. They do not substitute for the original source graphs. Names described as historical or awaiting export must be checked against the current project before this archive is presented as complete.

Blueprint node text is useful for reading and sharing graph excerpts, but it does not provide a standalone project with all variables, components, curves, widgets and references. Native assets also require their project context and dependencies. Level Blueprint logic must be collected from the relevant map as well as from reusable actors.

Session progress is not described as a disk save. No multiplayer, performance benchmark or user-test result is claimed in this archive.

## References

- [Project 1 repository used as the documentation reference](https://github.com/Jessie0207/Project1-Blueprint-Portfolio)
- [Epic Games: VR Template](https://dev.epicgames.com/documentation/en-us/unreal-engine/vr-template-in-unreal-engine)
- [Epic Games: Gameplay Framework](https://dev.epicgames.com/documentation/en-us/unreal-engine/gameplay-framework-in-unreal-engine)
- [Epic Games: Level Blueprint](https://dev.epicgames.com/documentation/en-us/unreal-engine/level-blueprint-in-unreal-engine)
- [Epic Games: Migrating Assets](https://dev.epicgames.com/documentation/unreal-engine/migrating-assets-in-unreal-engine)
- [GitHub: Adding a File to a Repository](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)
