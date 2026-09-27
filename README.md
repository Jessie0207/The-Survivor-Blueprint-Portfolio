# The Survivor — Technical Blueprint Portfolio

**Unreal Engine 5.7 · VR experience with desktop input support**

The Survivor is an immersive experience exploring how individuals become a crowd. Inspired by Elias Canetti’s *Crowds and Power*, five encounters translate collective impulses into spatial conditions, narrative cues and player actions. The Shop connects these encounters through tarot cards that disappear as progress is made.

This repository presents the project’s custom Blueprint systems. Following the structure of my first project, each module includes a short overview, BlueprintUE links and the roles of its main Blueprint elements.

**Contribution:** I extended the VR template’s pawn with keyboard and mouse input and built the project-specific targeting, interactions, progression and narrative sequences. Epic Games’ VR template provides the underlying tracking, controller and baseline movement/grab systems.

**VR demonstration:** Link to be added.

**Desktop demonstration:** Link to be added.

*BlueprintUE links are being added. This is a technical showcase, not a standalone Unreal Engine project.*

---

## Module 1: XR Pawn Extension and Desktop Input

Keyboard and mouse controls extend the pawn used for the VR experience, allowing the same project to be demonstrated on desktop.

**Blueprint location:** XR Pawn — custom input logic in the Event Graph.

<!-- 编辑提示：模块 1，XRPawn：键鼠输入与 VR 交互接入。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Desktop input:** Link to be added.

**BlueprintUE — VR interaction routing:** Link to be added.

### System Overview

- Desktop movement, viewing and interaction were added within the VR pawn.
- Controller input connects to the project-specific interactions; desktop and VR actions are documented according to their actual implementation.

### Core Blueprint Elements and Roles

- **Input events:** Receive keyboard, mouse and controller actions.
- **TryInteract:** Connects an interaction request to the targeting system.

---

## Module 2: Tarot Targeting and Focus Feedback

The targeting system identifies the card under the player’s aim and provides visual feedback for the current selection.

**Blueprint location:** XR Pawn → UpdateTarotFocus; card focus-response logic.

<!-- 编辑提示：模块 2，卡牌射线定位与高亮。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — UpdateTarotFocus:** Link to be added.

**BlueprintUE — Card focus feedback:** Link to be added.

### System Overview

- The targeting trace identifies the card and updates the current reference.
- Focus feedback changes when the player switches cards or looks away.

### Core Blueprint Elements and Roles

- **UpdateTarotFocus / Line Trace By Channel:** Update the target from the player’s aim.
- **FocusedTarotCard:** Stores the current card reference.
- **Card focus response:** Applies and removes the visual feedback.

---

## Module 3: Interaction Dispatch and Door Fallback

A routing function connects the player’s input to a tarot card or, when no valid card is selected, to the door interaction.

**Blueprint location:** XR Pawn → TryInteract and TryOpenFocusedDoor.

<!-- 编辑提示：模块 3，交互分发与门交互。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — TryInteract:** [View Blueprint](https://blueprintue.com/blueprint/2sl29jkw/)

**BlueprintUE — TryOpenFocusedDoor:** Link to be added.

### System Overview

- TryInteract checks whether FocusedTarotCard is valid.
- A valid card receives ActivateTarotCard; the alternative branch calls TryOpenFocusedDoor.

### Core Blueprint Elements and Roles

- **Is Valid:** Checks the selected card before use.
- **ActivateTarotCard:** Calls the card’s activation response.
- **TryOpenFocusedDoor:** Handles the door interaction fallback.

---

## Module 4: Tarot Activation and Level Entry

Activating a tarot card produces a visible response before loading its associated crowd scene.

**Blueprint location:** BP_TarotCard → ActivateTarotCard and the connected transition sequence.

<!-- 编辑提示：模块 4，卡牌激活与进入关卡。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Card activation and level entry:** Link to be added.

### System Overview

- The activation sequence controls the card’s lift, rotation and floating response.
- Selection information is recorded before the visual transition and map change.

### Core Blueprint Elements and Roles

- **ActivateTarotCard / IsActivated:** Start the response and check activation state.
- **Card timelines:** Drive the card’s movement.
- **ActiveCardIndex / ReturnFadeColor / Open Level:** Record selection information and enter the associated scene.

---

## Module 5: Encounter Completion and Shop State Restoration

Returning to The Shop removes the completed encounter’s card, making absence a visible record of progress.

**Blueprint location:** Encounter return logic; project GameInstance; BP_TarotCard BeginPlay; The Shop completion check.

<!-- 编辑提示：模块 5，完成记录、卡牌消失与终章条件。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Completion and return:** Link to be added.

**BlueprintUE — Card state restoration:** Link to be added.

**BlueprintUE — Ending condition:** Link to be added.

### System Overview

- Completion data passes between maps during the current running session.
- The returning Shop restores card states and checks whether the ending should begin.

### Core Blueprint Elements and Roles

- **GameInstance:** Retains session data across map loads.
- **CompletedCardCount / ActiveCardIndex / CardIndex:** Participate in the recorded progress and card checks.
- **Card BeginPlay and ending check:** Restore visible card states and evaluate the ending condition.

---

## Module 6: Spatial Narrative Cues and Audio Timing

Floating text and narration introduce each crowd’s condition and describe the consequence of the player’s action.

**Blueprint location:** Narrative trigger; the object receiving ShowNow; associated text and audio logic.

<!-- 编辑提示：模块 6，浮动文字、触发与旁白。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Narrative trigger:** Link to be added.

**BlueprintUE — Text display and audio timing:** Link to be added.

### System Overview

- Cues are placed along the player’s route and within interaction responses.
- Text display and audio timing structure the transition from observation to action.

### Core Blueprint Elements and Roles

- **Narrative trigger:** Starts the appropriate cue.
- **ShowNow:** Requests the text presentation.
- **Text and audio controls:** Coordinate the cue’s display and narration.

---

## Module 7: Baiting — Bell Interaction and Target Confirmation

Ringing the bell turns the player from an observer into a participant in the collective accusation.

**Blueprint location:** Bell interaction actor and the Baiting scene response.

<!-- 编辑提示：模块 7，第一关：敲铃与指认。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Bell interaction and scene response:** Link to be added.

### System Overview

- The bell action triggers sound and the consequence narration.
- The encounter then records completion and returns the player to The Shop.

### Core Blueprint Elements and Roles

- **Bell interaction event:** Receives the player’s action.
- **Sound and narrative calls:** Present the response to the accusation.
- **Completion and return logic:** Connect the encounter to the shared progression system.

---

## Module 8: Flight — Door Reveal and Passage

A door appears as the player approaches the blue slit. Crossing it places the player at the front of the escape.

**Blueprint location:** Flight proximity trigger, exit-door actor and passage detection.

<!-- 编辑提示：模块 8，第二关：门显现、打开与通过。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Door reveal, opening and passage:** Link to be added.

### System Overview

- Approaching the opening reveals the door.
- Door interaction and passage detection connect the player’s crossing to the encounter’s conclusion.

### Core Blueprint Elements and Roles

- **Reveal trigger:** Makes the door visible on approach.
- **Door response:** Receives the interaction routed from TryOpenFocusedDoor.
- **Passage detection:** Advances narration, completion and return.

---

## Module 9: Prohibition — Automatic Travel and Staged Stillness

Automatic travel establishes shared motion before the environment gradually becomes still.

**Blueprint location:** Spider/player travel controller and the Prohibition scene sequence.

<!-- 编辑提示：模块 9，第三关：蜘蛛行进与分阶段停止。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Automatic travel:** Link to be added.

**BlueprintUE — Staged stillness:** Link to be added.

### System Overview

- The spider carries the player along the scene’s route.
- Birds, water, background music and finally player/spider movement stop in sequence, while residual ambience remains.

### Core Blueprint Elements and Roles

- **Travel controller:** Starts, updates and stops the route.
- **Environment and audio references:** Identify the systems controlled by the scene.
- **Staged stop sequence:** Orders their changes over time.

---

## Module 10: Reversal — Hourglass Rotation and Crown Transfer

Turning the hourglass exchanges ruler and subject positions while the scene’s tiered hierarchy remains.

**Blueprint location:** Interactable hourglass and the Reversal scene response.

<!-- 编辑提示：模块 10，第四关：沙漏翻转与王冠响应。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Hourglass interaction:** Link to be added.

**BlueprintUE — Rotation and crown response:** Link to be added.

### System Overview

- The player’s hourglass interaction activates the reversal.
- Rotation, crown response and narration communicate the change in position and power.

### Core Blueprint Elements and Roles

- **Hourglass interaction entry:** Receives the request to turn the hourglass.
- **Rotation driver:** Updates the scene transformation.
- **Crown and narrative response:** Connect the transformation to its consequence.

---

## Module 11: Feast — Dish Placement and Diner Activation

Placing the final dish activates the twelve waiting diners and begins the next stage of the feast.

**Blueprint location:** Feast offering trigger or Level Blueprint; FinalDish and diner animation calls.

<!-- 编辑提示：模块 11，第五关：献菜与食客活动。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Dish placement and diner activation:** Link to be added.

### System Overview

- The offering sequence moves FinalDish into its scene position.
- The diner animations and following cues respond to the player’s contribution.

### Core Blueprint Elements and Roles

- **Offering trigger:** Recognises arrival at the offering point.
- **FinalDish placement:** Moves the dish into position.
- **Diner animation calls:** Activate the twelve seated figures.

---

## Module 12: Feast — Knife Handling and Stab Detection

The knife interaction converts the player’s action into the event that advances the feast.

**Blueprint location:** Knife/Pawn handling logic and the Blueprint owning the stab target.

<!-- 编辑提示：模块 12，第五关：持刀与刺入检测。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Knife handling:** Link to be added.

**BlueprintUE — Stab detection:** Link to be added.

### System Overview

- The knife’s hand relationship supports the VR action, with a desktop input path for the same encounter.
- The stab target recognises an accepted action and sends a response event to the scene.

### Core Blueprint Elements and Roles

- **Knife and hand references:** Define the held object’s relationship to the player.
- **Stab target detection:** Recognises the accepted knife action.
- **Stab event:** Notifies the scene response.

---

## Module 13: Feast — Stab Response and Narrative Timing

The accepted stab coordinates the dish response, consequence narration and the later chandelier fall.

**Blueprint location:** Feast scene graph → On Dish Stabbed (TRG_StabDish) and TL_DishHit.

<!-- 编辑提示：模块 13，第五关：刺菜反馈与叙事时序。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Stab response and narrative timing:** Link to be added.

### System Overview

- On Dish Stabbed starts the visual and narrative responses.
- The timing was revised to give narration, the player’s action and the chandelier’s fall distinct moments.

### Core Blueprint Elements and Roles

- **On Dish Stabbed / Sequence:** Receive the event and dispatch its responses in order.
- **TL_DishHit / SetWorldLocation:** Drive the dish’s visible response.
- **ShowNow and audio/timing calls:** Present the consequence and cue the next stage.

---

## Module 14: Feast — Chandelier Fall

The chandelier’s fall gives the feast’s final action a large spatial consequence.

**Blueprint location:** The graph containing TL_ChandelierFall and the BP_FeastChandelier reference.

<!-- 编辑提示：模块 14，第五关：吊灯坠落。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Chandelier fall:** Link to be added.

### System Overview

- A timeline drives the chandelier between its starting and target positions.
- The movement’s completion connects to the remaining scene response and return sequence.

### Core Blueprint Elements and Roles

- **TL_ChandelierFall:** Supplies the interpolation value over time.
- **Lerp (Vector):** Interpolates between the position values.
- **SetActorLocation:** Applies the result to BP_FeastChandelier.

---

## Module 15: The Shop Ending — Survivor Reveal and Fire Progression

After the five encounters, the sixth card appears and the familiar Shop becomes the setting of the ending.

**Blueprint location:** The Shop ending controller or Level Blueprint.

<!-- 编辑提示：模块 15，终章：第六张牌与商店燃烧。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Survivor reveal and staged fire:** Link to be added.

### System Overview

- The completion condition starts the Survivor card reveal.
- Fire, lighting and narration transform the room from an unburned space into a full blaze.

### Core Blueprint Elements and Roles

- **Ending entry condition:** Connects progression to the final sequence.
- **Survivor card response:** Reveals the sixth card.
- **Fire, light and narrative controls:** Coordinate the room’s transformation.

---

## Module 16: Ending — Blink Transition and Final Title

Alternating darkness and visibility closes the Shop sequence before The Survivor appears on a black screen.

**Blueprint location:** Ending blackout controller and final title widget.

<!-- 编辑提示：模块 16，终章：眨眼黑屏与最终标题。只需把下面的 Link to be added. 换成你的 Markdown 链接。 -->

**BlueprintUE — Blink sequence:** Link to be added.

**BlueprintUE — Final title:** Link to be added.

### System Overview

- The ending alternates blackout and visibility alongside its remaining narration.
- The final title closes the experience in darkness.

### Core Blueprint Elements and Roles

- **Blackout/fade control:** Changes visibility during the blink sequence.
- **Timing sequence:** Orders the transitions.
- **Final title widget:** Presents the closing title.

---

## Credits and Scope

- **Engine and foundation:** Unreal Engine 5.7 and Epic Games’ VR template.
- **Conceptual reference:** Elias Canetti, *Crowds and Power* (1960).
- **Project work:** Concept and narrative development, custom Blueprint interactions, scene assembly, asset development/refinement, and sound editing. AI-assisted model assets were refined and assembled with Blender and Unreal Engine.
- **External assets:** Environment resources, effects and music recordings used in the experience belong to their respective creators. This repository documents their integration; it does not redistribute those resource packs or recordings.

BlueprintUE links show selected node graphs. Variables, components, timeline curves, map references and project dependencies may need additional context. Progress described here is retained during the running session; this repository does not claim a save-to-disk system.
