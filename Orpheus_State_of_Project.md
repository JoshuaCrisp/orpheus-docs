# ORPHEUS: State of the Project
## Last Updated: April 4, 2026 (Co-Creative Director Session — SDK Review, Creative Direction)

---

## How To Use This Document

**This document is the single source of truth for the Orpheus project.** It lives in the Claude Project knowledge base and is automatically available to every conversation in the project. It is the asynchronous communication channel between conversations.

Update this document at the end of every work session. Any conversation in the project can update it.

---

## 1. Project Vision

Orpheus is a substitutional reality experience built for Meta Quest 3. The player begins in the real world (passthrough), transitions seamlessly into a fully virtual underworld, and must retrieve a lost soul (Eurydice) without looking back. The experience uses physical props, stagecraft, and gradual immersion to create a novel sense of presence.

### Core Design Principles
1. **Gradual spatial transition** — Passthrough to MR to full VR. No hard cut.
2. **Body stays real** — Passthrough occlusion keeps the player's body visible. No controllers. No disembodiment.
3. **Tactile honesty** — Every surface and object within arm's reach has a physical stand-in. Virtual scenery extends freely beyond the haptic zone.
4. **Narrative stakes drive physical interaction** — The virtual world provides danger and meaning. Real objects provide bodily confirmation.
5. **Darkness is an asset** — The underworld limits what needs to be rendered and physically built. The torch controls the player's attention radius.
6. **Portable staging** — Set pieces are placed in any available space, marked with trackable anchors, and the virtual world generates a path connecting them.
7. **Stagecraft logic** — Physical stand-ins need to pass a tactile test, not a visual one.

### Story Summary
Based on Orpheus and Eurydice. The player is Orpheus. They enter the underworld, receive a physical torch, cross a physical bridge over a virtual chasm, find Eurydice (potentially a real actress holding a prop hand), and must return without turning around. Success: real person waiting at exit. Failure: holding only a severed hand.

### Underworld Tone
Dark wet stone. Water is the dominant ambient sound — dripping, flowing, echoing off cavern walls. Mythological architecture emerging from darkness. An active sense of threat — not just emptiness but something that watches, whispers, pressures. The underworld doesn't want you here and it tells you so.

### Actor System
- Actor speaks live via wireless microphone
- Voice is spatialized in the virtual world using Meta XR Audio SDK — HRTF, source directivity, room acoustics
- Actor monitors via Quest 3 cast to phone while optionally walking alongside player physically
- System supports both single-actor and two-actor configurations
- Actor serves as dynamic difficulty adjustment (more help for nervous players, less for confident ones)
- Actor's character role is an OPEN QUESTION (see Section 11)

---

## 2. Project Structure and Roles

### Team Model
This project uses multiple Claude conversations within a single Claude Project as a team. Each conversation has a specialized role. The Project Knowledge Base is the shared drive. The State of Project document is the asynchronous communication channel between all conversations.

Joshua Crisp is the facilitator. He opens each conversation, ensures messages are delivered, provides input, and makes final decisions when the team disagrees. He is not a translator between team members — he is the one who opens the door so each conversation can read the others' mail.

### Roles
| Role | Status | Responsibilities |
|------|--------|-----------------|
| Co-Creative Director (Technical Authority) | ACTIVE — new conversation opened April 4, 2026 | Holds full picture: vision, story, staging, design philosophy, technical architecture, project status, timeline. Makes creative and architectural decisions. Also serves as Project Manager — tracks deadlines and prioritizes work. |
| Developer | ACTIVE — conversation created April 5, 2026 | Pure implementation: scripts, components, configuration, bug fixes. Takes direction from State of Project and Co-Creative Director decisions. |
| Researcher | ACTIVE — conversation created April 5, 2026 | Deep-dives into SDK documentation, technical feasibility, experimental features. Reports findings via Inter-Team Messages. May be short-lived per investigation rather than one persistent conversation. |
| Business roles (future) | NOT YET CREATED — defer until working prototype exists | Marketing, funding, distribution |

### Workflow
1. Joshua opens the Co-Creative Director conversation first at the start of each session — even briefly — to set direction and priorities
2. Joshua then opens Developer or Researcher conversations as the work requires
3. Each conversation checks its Inter-Team Messages before starting work
4. Each conversation writes messages for other roles when it discovers something relevant
5. At the end of each work session, Joshua updates the State of Project document with changes from that conversation

### Dispute Resolution Framework

1. **Creative/design disputes**: Both positions stated, discussed, documented. Co-Creative Director can say "no" on design grounds, but must make the case. User can override with reasoning.
2. **Technical feasibility claims**: The statement "this isn't technically possible" is NEVER the final word. It must always be qualified with "based on what I currently know, which may be incomplete." Resolution process:
   - Claude states belief and reasoning
   - User asks "have you read the current documentation for this specific feature?"
   - If no: stop and read documentation before deciding
   - If yes and still disagree: user's experiential intuition about human presence gets benefit of the doubt
   - Prototype the disputed approach. The headset is the tiebreaker.
3. **Unresolved disagreements**: Documented in "Open Questions" section with both positions and reasoning. Resolved through prototyping.

### Timeline
| Milestone | Target Date | Status |
|-----------|------------|--------|
| **PROTOTYPE DELIVERY** | **July 11, 2026** | **HARD DEADLINE** |
| Development pipeline (Claude Code + MCP) | April 4, 2026 | IN PROGRESS — Developer working on it now |
| Body occlusion working | ASAP — blocks all other work | NOT STARTED — approach confirmed, awaiting pipeline |
| Passthrough-to-VR transition | TBD | NOT STARTED |
| Spatial audio foundation | TBD | NOT STARTED — promoted to prototype milestone |
| Torch tracking | TBD | NOT STARTED — pending documentation review |
| Set piece tracking | TBD | NOT STARTED — pending documentation review |
| Full walkthrough prototype | Before July 11 | NOT STARTED |

**Weeks remaining as of April 4, 2026: approximately 14 weeks.**

---

## 3. Technical Stack

### Engine and Platform
| Component | Version | Notes |
|-----------|---------|-------|
| Unity | 6000.4.0f1 (Unity 6) | Meta Quest build target |
| Target Device | Meta Quest 3 | Developer Mode enabled |
| Development Machine | Mac (Apple Silicon, macOS Sequoia 15.x) | |
| Build Pipeline | USB-C for initial deploy, then wireless via app library | App appears under "Unknown Sources" |

### SDK Versions (Locked as of April 5, 2026)
| Package | Version | Source |
|---------|---------|--------|
| Meta XR Core SDK | 85.0.0 | Unity Asset Store / UPM |
| Meta XR All-in-One SDK | 85.0.0 | Unity Asset Store / UPM |
| Meta XR Movement SDK | 83.0.0 | GitHub: oculus-samples/Unity-Movement (latest available) |
| Unity OpenXR Meta | 2.2.0 | UPM |
| OpenXR Plugin | 1.16.1 | UPM |
| AR Foundation | 6.4.1 | UPM |
| Meta MR Utility Kit | 85.0.0 | Unity Asset Store / UPM |
| Meta XR Interaction SDK | 85.0.0 | Unity Asset Store / UPM |
| Meta XR Interaction SDK Essentials | 85.0.0 | Unity Asset Store / UPM |
| Meta XR Platform SDK | 85.0.0 | Unity Asset Store / UPM |
| Meta XR Audio SDK | 85.0.0 | Unity Asset Store / UPM |
| Meta XR Haptics SDK | 85.0.0 | Unity Asset Store / UPM |

### ADB Path (for log checking)
```
/Applications/Unity/Hub/Editor/6000.4.0f1/PlaybackEngines/AndroidPlayer/SDK/platform-tools/adb
```

### Key Unity Project Settings
- **XR Plug-in Management**: OpenXR enabled with Meta XR feature group
- **Oculus Touch Controller Profile**: Added under OpenXR Interaction Profiles
- **Hand Interaction Poses**: Enabled in OpenXR Feature Groups
- **Meta Quest Support**: Enabled in OpenXR Feature Groups
- **Foveated Rendering**: Enabled in OpenXR Feature Groups

---

## 4. Current Scene: Underworld

### Scene Hierarchy
```
OVRCameraRig (Position: 0,0,0)
├── TrackingSpace
│   ├── CenterEyeAnchor (Camera: Solid Color, Black, Alpha=0)
│   ├── LeftHandAnchor
│   │   └── OVRHandPrefab (Hand Type: Hand Left, Material: HandOcclusionMaterial)
│   ├── RightHandAnchor
│   │   └── OVRHandPrefab (Hand Type: Hand Right, Material: HandOcclusionMaterial)
│   └── [other anchors]
├── OVR Body (Script) — Provided Skeleton Type: Full Body
├── BodyTrackingDebug (Script)
├── RequestBodyTracking (Script)
└── RequestSpatialPermission (Script)

PassthroughLayer (GameObject at scene root)
├── OVR Passthrough Layer (Placement: Underlay)
└── Color Control: Color Adjustment (Brightness/Contrast/Saturation adjustable)

DepthManager (GameObject at scene root)
└── Environment Depth Manager — DISABLED (caused whole room to show through)

CaveWalls (Inverted Sphere, Scale: 15,8,15, Material: CaveMaterial)
├── InvertMesh (Script)

Floor (Cube, Position: 0,-0.05,0, Scale: 12,0.1,12)

Pillar 1 (Position: -1.5,1.5,2, Scale: 0.6,3,0.6)
Pillar 2 (Position: 1.8,1.3,1.5, Scale: 0.5,2.6,0.5)
Boulder 1 (Position: 0.5,0.4,4.5, Scale: 1.8,0.8,1.2)
Pillar 3 (Position: -3,1.8,5, Scale: 0.7,3.6,0.7)
Boulder 2 (Position: 2,0.5,7, Scale: 2,1,1.5)
Pillar 4 (Position: -1,2,8, Scale: 0.8,4,0.8)

UnderworldParticles (Position: 0,1.2,0)

Point Light (Position: 0,2,0)
```

### OVR Manager Settings (on OVRCameraRig)
- Tracking Origin Type: **Floor Level**
- Passthrough Support: **Required**
- Enable Passthrough: **Checked**
- Hand Tracking Support: **Controllers and Hands**
- Body Tracking Support: **Supported**
- Body Tracking Fidelity: **High**
- Body Tracking Joint Set: **Full Body**

### Materials
| Name | Shader | Color | Notes |
|------|--------|-------|-------|
| CaveMaterial | URP/Lit | ~(30,25,25) near-black | Smoothness 0.1 |
| FloorMaterial | URP/Lit | ~(50,45,40) dark warm | Smoothness 0.05 |
| TestMaterial | URP/Lit | (150,150,150) gray | For debugging visibility |
| HandOcclusionMaterial | Custom/DepthOnlyHand | N/A (invisible) | Writes depth only, renders no color |

### Custom Scripts
| Script | Location | Purpose |
|--------|----------|---------|
| InvertMesh.cs | Assets/Scripts | Flips sphere normals so cave renders inside-out |
| DepthOnlyHand (Shader) | Assets/Scripts | ZWrite On, ColorMask 0 — invisible depth writer |
| RequestSpatialPermission.cs | Assets/Scripts | Requests com.oculus.permission.USE_SCENE on startup |
| RequestBodyTracking.cs | Assets/Scripts | Requests com.oculus.permission.BODY_TRACKING on startup |
| BodyTrackingDebug.cs | Assets/Scripts | Logs body tracking status to console (debug only) |
| PassthroughStyling.cs | Assets/Scripts | REMOVED from scene — replaced by Inspector Color Adjustment sliders |

### Fog Settings
- Enabled via Window → Rendering → Lighting → Environment
- Color: near-black (10,8,8)
- Mode: Linear
- Start: 0.5
- End: 5

---

## 5. What Works

- **Passthrough**: Real world visible through headset as underlay
- **Hand tracking**: Both hands tracked, finger positions accurate
- **Hand occlusion**: Real hands visible in VR cave via depth-only shader on OVRHandPrefab meshes
- **Passthrough color adjustment**: Brightness, contrast, saturation controllable — hands can be darkened to match cave
- **Cave environment**: Inverted sphere with dark material, fog, pillars, boulders, floor, ambient particles
- **Fog**: Linear fog working correctly, objects fade at distance
- **Floor tracking**: Floor level is correct (Tracking Origin: Floor Level)
- **Body tracking data**: OVR Body running with FullBody skeleton at ~36fps (confirmed via adb logcat)
- **Build pipeline**: USB build and run to Quest 3 works reliably

---

## 6. What Doesn't Work Yet

### Body Occlusion (CRITICAL — Blocks Progress)
- Body tracking DATA is flowing (confirmed via logs)
- No visible body mesh exists to use as occlusion mask
- **Approach confirmed (April 4/5):** Movement SDK Character Retargeter + depth-only shader. Capsule-person (primitives parented to skeleton joints) is the first-pass approach. See Resolved Messages for full Researcher findings.
- The Depth API (EnvironmentDepthManager) must remain DISABLED — it occludes everything in the room, not just the body.
- AI Building Blocks do NOT solve this problem — no image segmentation exists in v85.
- Developer has been given implementation instructions.

### Hand Occlusion Border/Halo
- Thin border of real world visible around hand edges
- Scaling hand prefabs to 1.05-1.08 helps but doesn't eliminate
- Proper fix deferred to polish phase

### Headset Sleep/Resume
- App sometimes goes to black screen when headset is removed and put back on
- Workaround: tip headset up like a visor instead of fully removing
- Reset Tracker On Load: enabled

---

## 7. Technical Challenges To Solve

### Tier 1: Must Solve for Prototype
1. **Full body occlusion** — See player's real body in VR cave without showing the room. Approach confirmed; implementation pending.
2. **Torch tracking** — Track a physical prop while player carries it
3. **Passthrough-to-VR transition** — Gradual blend from real world into underworld. Selective Passthrough shader is a strong candidate (see Section 18). Narrative justification for the transition is an open question.

### Tier 2: Important for Prototype Quality
4. **Spatial audio foundation** — PROMOTED from Tier 3. Stone/water acoustics, spatialized actor voice, ambient soundscape. The Meta XR Audio SDK supports all of this natively. Sound is what makes the cave real.
5. **Set piece tracking via QR codes or other trackables** — Place set pieces anywhere, world adapts. QR tracking confirmed available in MRUK v85 with 6DOF pose and payload data.
6. **"Don't look back" detection** — Head rotation threshold detection
7. **Bridge wobble tracking** — Arduino accelerometer on physical beam, data to Unity via BLE

### Tier 3: Polish Phase
8. **Passthrough color linked to torch proximity**
9. **Hand/body occlusion edge refinement**
10. **Environment visual polish**
11. **Advanced sound design** (environmental variation, dynamic acoustics per location)

### IMPORTANT NOTE ON FEASIBILITY
Multiple technical challenges were initially assessed as difficult or impossible based on web research of older SDK versions. The v85 SDK documentation has now been reviewed by the Co-Creative Director. All key capabilities have been confirmed against the actual documentation in the project knowledge base. See Section 18 for the SDK capability summary.

---

## 8. Research Areas — Documentation Required

The following areas require reading the official Meta v85 documentation before making technical decisions. PDFs have been uploaded to the project knowledge base.

### Priority 1 — REVIEWED by Co-Creative Director (April 4, 2026)
The Co-Creative Director has read all uploaded SDK documentation at a high level. Detailed implementation review is the Developer's responsibility before writing code. Key documentation reviewed includes: Spatial Audio (spatialization, room acoustics, ambisonics, ray tracing), Passthrough (compositing, masking, occlusions, selective passthrough shader), MRUK (trackables, QR codes, scene data, EffectMesh, destructible mesh), Voice SDK, Microgestures, Eye Tracking, Hand/Body Tracking, Interaction SDK, AI Building Blocks (agents, STT, TTS, LLM, object detection), and performance optimization guides.

### Still Needs Detailed Developer Review Before Implementation
| Topic | Notes |
|-------|-------|
| Movement SDK Character Retargeter | Exact setup steps for capsule-person body occlusion |
| Meta XR Audio SDK setup in Unity | Spatializer plugin, mixer configuration, room acoustics component |
| Selective Passthrough shader | Exact material/shader path in Core SDK, integration with custom geometry |
| QR Code Tracking in MRUK | Tracker configuration, event subscription, payload handling |

---

## 9. User Profile

- **Name**: Joshua Scott Crisp
- **Background**: Theatre (BFA), HCI (MS from Georgia Tech, Augmented Environments Lab)
- **Technical level**: Can download/install software, navigate Unity with guidance, cannot write code independently
- **Physical capabilities**: Owns Einscan Rigel 3D scanner, has Arduino basics, can build physical set pieces and props
- **Location**: Athens, Georgia
- **Hardware**: Mac (Apple Silicon), Meta Quest 3, Einscan Rigel scanner, basic Arduino supplies

---

## 10. Key Design Decisions Made

| Decision | Rationale | Date |
|----------|-----------|------|
| Unity 6 over 2022.3 LTS | Newer features, Meta Quest build target, user preference | April 5 |
| OpenXR over Oculus XR Plugin | Meta recommends for v74+, future-proof | April 5 |
| No controllers ever | Core design principle — all interaction via hands and physical props | April 5 |
| Passthrough as Underlay (not Overlay) | Cave renders on top, passthrough shows through body occlusion holes | April 5 |
| Depth-only shader for occlusion | Invisible mesh blocks virtual cave, revealing passthrough behind it | April 5 |
| Full Body tracking (not Upper Body) | Player needs to see feet on bridge | April 5 |
| Color Adjustment for passthrough styling | Darkens/desaturates hands to match cave lighting | April 5 |
| Claude Project structure = team model | Multiple conversations with specialized roles sharing knowledge base | April 5 |
| Co-Creative Director role for main conversation | Holds full picture, makes design/architecture decisions | April 5 |
| Depth API disabled for Orpheus | Occludes entire room, not just body. Confirmed by Researcher. | April 5 |
| AI Building Blocks not used for body occlusion | No image segmentation in v85; inference engine lacks hardware acceleration on Quest | April 5 |
| Body occlusion via Movement SDK + depth shader | Capsule-person first pass, Character Retargeter for refinement | April 4-5 |
| Spatial audio promoted to prototype milestone | Sound is what makes the cave real; SDK supports it natively | April 4 |
| Underworld tone: wet stone, water as dominant sound | Aligned with narrative and atmospheric goals | April 4 |
| Player is Orpheus (POV) | The experience is told from Orpheus's perspective, not Eurydice's | April 4 |

---

## 11. Open Questions

| Question | Current Thinking | Status |
|----------|-----------------|--------|
| Narrative justification for the transition into the underworld | Must be narratively motivated, not just a door. Could involve a ritual act (drinking, lying down, a death-transition). The Selective Passthrough shader can support many shapes/geometries for the transition. The experience starts when the headset goes on, not at the portal. | OPEN — needs creative discussion |
| Who is the guide character? | Charon (the ferryman) is a strong candidate. Could also be a character who has been in the underworld before and has a personal stake. Actor chooses character based on player personality, or plays multiple roles. The guide must function like Jill in Ghost in the Room — demonstrate possibility, modulate difficulty, give the player confidence to act. | OPEN — needs creative discussion |
| Torch tracking method | Wrist tracking + Arduino IMU vs. SDK object tracking. QR code tracking confirmed available but updates at lower frequency (not frame-perfect). May be suitable for a stationary torch holder but not a hand-carried torch. | OPEN — needs documentation review and prototyping |
| What does the player find at the end? | Real actress holding a prop hand (original concept). Success/failure determined by whether they look back on the return. Details of the encounter need development. | OPEN — needs creative discussion |
| How does the return journey differ from the descent? | The "don't look back" rule must have sensory weight. The actor's spatialized voice behind the player, source directivity causing voice to muffle as player faces forward — these create a felt rule. The return should feel different from the descent. | OPEN — needs creative discussion |

---

## 12. Rules for Future Sessions

### Before Starting Work
1. Read the State of Project document (automatically available via project knowledge base)
2. State what you want to work on
3. If any SDK versions have changed, update this document immediately

### Before Giving Instructions
1. Reference the SDK documentation PDFs in the knowledge base for the specific feature
2. If documentation is not available, say so — do not guess
3. Specify exact Unity paths: which object → which component → which field → what value

### After Completing Work
1. Update this document with any changes
2. Note any new scripts, materials, or objects created
3. Update "What Works" and "What Doesn't Work Yet" sections

### When Adding New SDKs or Packages
1. Record exact version number in Section 3
2. Save and upload documentation PDF to project knowledge base
3. Note any known incompatibilities or setup requirements

### Dispute Resolution
1. Creative disputes: discuss, document, Co-Creative Director can say no but must make the case
2. Technical feasibility: never final without documentation review
3. Unresolved: document both positions, prototype, headset is tiebreaker

---

## 13. Project File Structure
```
Assets/
├── Scenes/
│   ├── SampleScene (original passthrough test — not active)
│   └── Underworld (active scene)
├── Scripts/
│   ├── InvertMesh.cs
│   ├── DepthOnlyHand.shader (Custom/DepthOnlyHand)
│   ├── RequestSpatialPermission.cs
│   ├── RequestBodyTracking.cs
│   ├── BodyTrackingDebug.cs
│   └── PassthroughStyling.cs (REMOVED from scene, file may still exist)
├── Materials/
│   ├── CaveMaterial
│   ├── FloorMaterial
│   ├── TestMaterial
│   └── HandOcclusionMaterial
```

---

## 14. Next Session Plan

### Currently In Progress (April 4, 2026)
Developer is working on:
1. Restructuring the Unity project into an enclosing folder
2. Installing Claude Code + MCP Unity bridge
3. Body occlusion — capsule person first pass

### After Pipeline Is Working
4. Build and test body occlusion — confirm body visibility in cave
5. Begin spatial audio setup — Meta XR Audio spatializer plugin, room acoustics component
6. Prototype portal transition using Selective Passthrough shader

---

## 15. Infrastructure TODO
- [x] Upload State of Project document to Claude Project knowledge base
- [x] Paste Project Instructions v2 into Claude Project settings
- [x] Save and upload Priority 1 SDK documentation PDFs
- [x] Save and upload Priority 2 SDK documentation PDFs
- [x] Save and upload additional SDK documentation PDFs (Joshua uploaded extensive collection)
- [x] Create Developer conversation
- [x] Create Researcher conversation
- [x] Open new Co-Creative Director conversation (opened April 4, 2026)
- [ ] Install Node.js if needed (nodejs.org) — Developer working on this
- [ ] Install Claude Code on Mac — Developer working on this
- [ ] Set up MCP Unity bridge in Unity project — Developer working on this
- [ ] Set up wireless ADB for cable-free Quest deployment
- [ ] Restructure Unity project into enclosing folder — Developer working on this

---

## 16. Inter-Team Messages

### For: Co-Creative Director
(No new messages)

### For: Developer
(No new messages — Developer has already received implementation instructions for body occlusion via the Researcher message from April 5, and a detailed session prompt from the Co-Creative Director on April 4)

### For: Researcher
(No new messages)

### For: All
- (no new messages)

---

## 17. Resolved Messages

(Messages moved here after being read and addressed by the recipient)

- [FROM Co-Creative Director, April 5] Priority research needed: Can the Depth API be configured to occlude ONLY the player's body without showing the rest of the room? → **RESOLVED by Researcher April 5. Answer: No. Depth API disabled for Orpheus. Read and acknowledged by Co-Creative Director April 4.**
- [FROM Co-Creative Director, April 5] Secondary research: What do the AI Building Blocks (Object Detection, Image Segmentation) actually do? → **RESOLVED by Researcher April 5. No image segmentation in v85. AI Building Blocks not used for body occlusion. Read and acknowledged by Co-Creative Director April 4.**
- [FROM Researcher, April 5] RE: Depth API body-only occlusion — **Read and acknowledged by Co-Creative Director April 4. Decision: Depth API stays disabled. Body occlusion proceeds via Movement SDK + depth-only shader.**
- [FROM Researcher, April 5] RE: AI Building Blocks capabilities — **Read and acknowledged by Co-Creative Director April 4. Decision: AI Building Blocks reserved for future use (voice commands, object detection for set pieces). Not used for body occlusion.**
- [FROM Researcher, April 5] Body occlusion approach confirmed for Developer — **Read by Developer (pending confirmation). Implementation instructions delivered.**

---

## 18. SDK Capabilities Summary (Co-Creative Director Review, April 4, 2026)

The Co-Creative Director reviewed all uploaded Meta SDK documentation. This section captures the capabilities most relevant to Orpheus's design goals.

### Spatial Audio (Meta XR Audio SDK)
- HRTF-based spatialization for point-source audio (actor voice, environmental sounds)
- **Source directivity**: voices sound muffled when speaker faces away, clear when facing toward listener. Directly relevant to the "don't look back" rule — Eurydice's voice changes character as player turns away.
- **Room acoustics**: Shoebox model (lightweight, manual control) and Acoustic Ray Tracing (automated, more natural). Room properties (dimensions, materials) can be updated at runtime using invisible colliders as triggers — different acoustics in different parts of the underworld.
- **Material library**: Built-in reflection coefficients for stone, marble, water, soil, mud, gravel, concrete, wood, glass, metal, and more. Directly applicable to cave surfaces.
- **Ambisonics**: Pre-rendered 3D sound fields for environmental beds (dripping water, subterranean rumble). Computationally cheap. Meta provides an Ambisonics Starter Pack with ambient WAV files.
- **Volumetric sources**: Sound sources can be given a radius, spreading as they envelop the listener. Useful for large environmental sounds (river, chasm).
- **Near-field rendering**: Automatic approximation of acoustic diffraction for sources within 1 meter. Relevant for the torch, held objects, Eurydice's hand.

### Passthrough Compositing and Masking
- **Selective Passthrough shader**: Built-in material in Core SDK that makes any mesh transparent to reveal real-world camera feed. Can be applied to EffectMesh or custom geometry. Strong candidate for portal transition.
- **Passthrough Windows**: Create windows through which passthrough is visible within a VR environment.
- **EffectMesh**: Can cut holes in scene geometry by semantic label (doors, windows, ceilings). Tutorial exists for ceiling-reveal animation pattern — adaptable for portal transitions.
- **Destructible Global Mesh**: MRUK can spawn breakable versions of scene geometry at runtime. Fragments independently destroyable. Potential for dramatic visual effects.

### Tracking and Scene Understanding
- **QR Code Tracking**: 6DOF pose with string payload via MRUK. Supports detection, event-driven subscription, and position updates. Not frame-perfect (lower frequency), suitable for stationary set pieces. Requires spatial data permission and Scene/Anchor support.
- **Scene API / MRUK**: Room scanning, semantic labels (walls, floor, ceiling, furniture), spatial queries, world locking for drift correction.
- **Body Tracking**: Full body at ~36fps, already working. Movement SDK provides Character Retargeter for driving humanoid meshes.

### Voice and AI
- **Voice SDK**: Full NLU via Wit.ai, custom intent/entity training. Could enable voice-triggered events in the underworld.
- **AI Building Blocks**: STT → LLM → TTS agent chain. Object Detection (YOLO, bounding boxes). No image segmentation.
- **Microgestures**: Thumb swipes (4 directions), taps, index pinches per hand. Subtle input without controllers.

### Performance
- **Fixed Foveated Rendering**: Available, reduces GPU load at periphery.
- **Forward+ Rendering**: Recommended for Quest with few dynamic lights (our scenario).
- **Phase Sync**: Adaptive frame timing, complements late-latching.
- **Dynamic Resolution**: Adjusts render scale based on GPU load.

---

## 19. Narrative and Creative Reference

### Source Material
The project draws on the myth of Orpheus and Eurydice. The player is Orpheus. All narrative decisions are made from his perspective.

### Creative Influences (Not Source Material — For Inspiration Only)
- **Sarah Ruhl's *Eurydice*** (2003): Read by the Co-Creative Director. The play's wet-stone underworld, its use of ambient voices as environmental pressure (the Stones), and its treatment of water as the sensory through-line all align with Orpheus's design direction. We are NOT adapting or following this play. We are building an original experience. Any resonance is atmospheric, not narrative.
- **Joshua's childhood nightmare**: Conscious fog that lives in a closet. Informed the original "active threat" tone — something that hunts, not just empty darkness.
- **Joshua's thesis (*The Ghost in the Room*)**: Proved that a guide character (Jill) is essential for participant confidence in interactive theatre. The actor in Orpheus serves this function. Also demonstrated that games with clear rules, opponents, and stakes (the Ouija board) produce the highest engagement.
- **Joshua's HCI paper**: Demonstrated that presence measurement works across VR/AR modalities and that perceptual substitution is robust — users don't detect the swap when coherence is maintained. This is the theoretical license for substitutional reality.
