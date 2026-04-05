# ORPHEUS: State of the Project
## Last Updated: April 5, 2026 (Co-Creative Director — Spatial Audio Accepted, Portal Transition Directive Issued)

---

## How To Use This Document

**This document is the single source of truth for the Orpheus project.** It lives at https://github.com/JoshuaCrisp/orpheus-docs and is fetched by every conversation before starting work.

**Update workflow:** At the end of a session, provide Joshua with specific text changes. Joshua gives those instructions to Claude Code, which edits the file and pushes to GitHub.

**Who can update what:** Any role may report facts (build results, test outcomes, new files, infrastructure changes). Only the Co-Creative Director may author design decisions, open question resolutions, creative direction, and narrative sections.

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
This project uses multiple Claude conversations within a single Claude Project as a team. Each conversation has a specialized role. The GitHub docs repo is the shared document store. The State of Project document is the asynchronous communication channel between all conversations.

Joshua Crisp is the facilitator. He opens each conversation, ensures messages are delivered, provides input, and makes final decisions when the team disagrees.

### Roles
| Role | Status | Responsibilities |
|------|--------|-----------------|
| Co-Creative Director (Technical Authority) | ACTIVE — new conversation opened April 4, 2026 | Holds full picture: vision, story, staging, design philosophy, technical architecture, project status, timeline. Makes creative and architectural decisions. Authors all design decisions in this document. |
| Developer | ACTIVE — conversation created April 5, 2026 | Pure implementation: scripts, components, configuration, bug fixes. Takes direction from State of Project and Co-Creative Director decisions. May update this document with factual reports only. |
| Researcher | ACTIVE — conversation created April 5, 2026 | Deep-dives into SDK documentation, technical feasibility, experimental features. Reports findings via Inter-Team Messages. May be short-lived per investigation. |
| Business roles (future) | NOT YET CREATED — defer until working prototype exists | Marketing, funding, distribution |

### Workflow
1. Joshua opens the Co-Creative Director conversation first at the start of each session — even briefly — to set direction and priorities
2. Joshua then opens Developer or Researcher conversations as the work requires
3. Each conversation fetches the State of Project from GitHub before starting work
4. Each conversation checks its Inter-Team Messages before starting work
5. Each conversation writes messages for other roles when it discovers something relevant
6. At the end of each session, updates are pushed to GitHub via Claude Code

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
| Development pipeline (Claude Code + MCP) | April 4, 2026 | COMPLETE |
| Body occlusion working | April 5, 2026 | COMPLETE — first pass (capsule person). Polish issues deferred to Tier 3. |
| Spatial audio foundation | April 5, 2026 | COMPLETE — spatializer plugin, Audio Mixer, room acoustics, test source confirmed working. |
| Passthrough-to-VR transition | After spatial audio | NOT STARTED — Developer directed to begin |
| Torch tracking | TBD | NOT STARTED — pending documentation review |
| Set piece tracking | TBD | NOT STARTED — pending documentation review |
| Full walkthrough prototype | Before July 11 | NOT STARTED |

**Weeks remaining as of April 5, 2026: approximately 14 weeks.**

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

### Development Tools (Installed April 4, 2026)
| Tool | Version | Notes |
|------|---------|-------|
| Claude Code CLI | latest (native installer) | Connected to Unity via MCP |
| CoplayDev unity-mcp | beta (git) | Unity Package Manager, `https://github.com/CoplayDev/unity-plugin.git#beta` |
| Python | 3.13.12 | Homebrew (required by MCP server) |
| uv/uvx | 0.11.3 | Required by MCP server |
| Homebrew | 5.1.3 | macOS package manager |
| Git | system | GitHub docs repo at https://github.com/JoshuaCrisp/orpheus-docs |

### Unity Project Location
```
/Users/lab/Desktop/Orpheus in the Underworld/Technical/Unity Project/Orpheus Prototype
```

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

### Audio Settings
- **Spatializer Plugin**: Meta XR Audio
- **Ambisonic Decoder Plugin**: Meta XR Audio
- **Default Speaker Mode**: Stereo
- **Audio Mixer**: SpatializerMixer with MetaXRAudioReflection effect on Master channel

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
├── RequestSpatialPermission (Script)
└── SetRefreshRate (Script) — sets display to 120Hz on Start

PassthroughLayer (GameObject at scene root)
├── OVR Passthrough Layer (Placement: Underlay)
└── Color Control: Color Adjustment (Brightness/Contrast/Saturation adjustable)

DepthManager (GameObject at scene root)
└── Environment Depth Manager — DISABLED (caused whole room to show through)

BodyOcclusion (Position: 0,0,0)
└── CapsuleBodyOcclusion (Script)
    ├── Camera Rig: OVRCameraRig
    ├── Occlusion Material: HandOcclusionMaterial
    ├── Debug Visible: false
    ├── Size Multiplier: 1.4
    └── Creates at runtime: 12 capsule segments + 5 spheres (head, elbows, shoulders)

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

CaveAcoustics (Position: 0,0,0)
└── MetaXRAudioRoomAcousticProperties (Stone walls, 15x8x15, clutter 0.2, lock to listener)

TestDrip (Position: 2,1.5,3)
├── AudioSource (Spatial Blend: 1.0, Spatialize: true, Output: Master SpatializerMixer)
├── ProceduralTestTone (Script)
└── MetaXRAudioSource (Script)

PortalTestObj (Position: 0,0,0)
└── PortalQuad (Quad, Position: 0,1.5,3, Rotation: 0,180,0, Scale: 2,2.5,1)
    └── MeshRenderer (Material: SelectivePassthroughPortal)
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
| HandOcclusionMaterial | Custom/DepthOnlyHand | N/A (invisible) | Writes depth only, renders no color. Cull Off (both faces). |
| SelectivePassthroughPortal | Oculus/SelectivePassthrough | N/A (transparent) | Blend Zero SrcAlpha — punches hole in VR to reveal passthrough underlay. Copied from Core SDK Editor folder. |

### Custom Scripts
| Script | Location | Purpose | Status |
|--------|----------|---------|--------|
| InvertMesh.cs | Assets/Scripts | Flips sphere normals so cave renders inside-out | Active |
| DepthOnlyHand.shader | Assets/Scripts | ZWrite On, ColorMask 0, Cull Off — invisible depth writer for both faces | Active — Cull Off added April 5 |
| RequestSpatialPermission.cs | Assets/Scripts | Requests com.oculus.permission.USE_SCENE on startup | Active |
| RequestBodyTracking.cs | Assets/Scripts | Requests com.oculus.permission.BODY_TRACKING on startup | Active |
| BodyTrackingDebug.cs | Assets/Scripts | Logs body tracking status to console (debug only) | Active |
| PassthroughStyling.cs | Assets/Scripts | REMOVED from scene — replaced by Inspector Color Adjustment sliders | Inactive |
| CapsuleBodyOcclusion.cs | Assets/Scripts | Reads OVRPlugin.GetBodyState4() with Full Body joint set (84 joints), creates 12 capsule segments + 5 spheres (head, elbows, shoulders), positions between joint pairs, applies depth-only shader for body occlusion passthrough | Active — deployed and tested April 5 |
| SetRefreshRate.cs | Assets/Scripts | Sets Quest 3 display refresh rate to 120Hz on Start | Active — added April 5 |
| ProceduralTestTone.cs | Assets/Scripts | Procedural mono water drip tone for spatial audio testing | Active — added April 5 |
| SelectivePassthrough.shader | Assets/Shaders | Oculus/SelectivePassthrough — Blend Zero SrcAlpha, ZWrite Off, Cull Off. Punches holes in VR rendering to reveal passthrough. Copied from Meta XR Core SDK Editor/BuildingBlocks path into Assets for build inclusion. | Active — tested April 5 |

### Fog Settings
- Enabled via Window → Rendering → Lighting → Environment
- Color: near-black (10,8,8)
- Mode: Linear
- Start: 0.5
- End: 5

### OVRPlugin Body Joint Indices (verified against v85 SDK)
These are the BoneId enum values confirmed in OVRPlugin.cs for this SDK version:
| Joint | Index |
|-------|-------|
| Body_LeftShoulder | 8 |
| Body_LeftArmUpper | 10 |
| Body_LeftArmLower | 11 |
| Body_LeftHandWrist | 19 |
| Body_RightShoulder | 13 |
| Body_RightArmUpper | 15 |
| Body_RightArmLower | 16 |
| Body_RightHandWrist | 45 |
| Body_LeftUpperLeg | 70 |
| Body_LeftLowerLeg | 71 |
| Body_LeftFootAnkle | 73 |
| Body_RightUpperLeg | 77 |
| Body_RightLowerLeg | 78 |
| Body_RightFootAnkle | 80 |

### CapsuleBodyOcclusion Technical Details
- API: `OVRPlugin.GetBodyState4(Step.Render, BodyJointSet.FullBody, ref bodyState)` — returns 84 joints including generative legs
- Coordinate conversion: OVRPlugin right-hand space → Unity left-hand space (Z negated)
- Validity check: `bodyState.Confidence > 0` and `JointLocations != null`
- Joint validity: `LocationFlags & 0x3 != 0`
- Capsule sizing: base radius per segment × global sizeMultiplier (currently 1.4)
- Debug mode: `debugVisible` flag swaps depth-only material for TestMaterial (gray visible capsules)

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
- **Body occlusion (capsule person)**: Player's real body visible as passthrough silhouette against virtual cave. 12 capsule segments + 5 spheres (head, elbows, shoulders) driven by OVRPlugin.GetBodyState4 (Full Body, 84 joints). Arms, torso, legs, head all tracking correctly. sizeMultiplier 1.4. Depth-only shader with Cull Off. Tested and confirmed working April 5.
- **Display refresh rate**: Set to 120Hz via SetRefreshRate.cs for smoother visual experience.
- **Claude Code ↔ Unity pipeline**: Claude Code connected to Unity via CoplayDev MCP bridge. Can create/modify GameObjects, components, and scripts from Terminal or VS Code. Tested successfully April 4 (created and deleted a test cube). Used April 5 to set up BodyOcclusion GameObject and wire all component references.
- **GitHub docs repo**: State of Project document hosted at https://github.com/JoshuaCrisp/orpheus-docs — editable via Claude Code, fetchable by all conversations.
- **Spatial audio foundation**: Meta XR Audio spatializer plugin enabled, Audio Mixer with MetaXRAudioReflection effect, Room Acoustics Properties (15x8x15 stone, clutter 0.2, locked to listener), spatialized test drip source at (2,1.5,3). HRTF spatialization, distance attenuation, and room reverb all confirmed working on Quest 3 — April 5.
- **Selective Passthrough portal (proof of concept)**: A quad with the Selective Passthrough shader (Oculus/SelectivePassthrough, from Meta XR Core SDK) successfully punches a hole in the VR cave to reveal real-world passthrough. Sharp edges, no fog interference, body occlusion unaffected, works from both sides (Cull Off added). Shader and material copied from SDK Editor folder into Assets/Shaders and Assets/Materials for device build inclusion. Tested and confirmed working on Quest 3 — April 5.

---

## 6. What Doesn't Work Yet

### Body Occlusion — Polish Issues (Non-blocking, Deferred to Tier 3)
- **Elbow gaps**: When arm bends tightly, gap visible between upper arm and forearm capsules. Elbow spheres added but coverage not complete at extreme bend angles. Expected to resolve when upgrading from capsule primitives to a proper humanoid mesh driven by Character Retargeter.
- **Shoulder cutoff**: Head sphere may intersect shoulder sphere, creating visual cutoff when looking down at own shoulders. Also expected to resolve with proper mesh.
- **Leg tracking responsiveness**: Legs use "Generative Legs" (predicted from upper body, not directly tracked). Inherently less responsive than arm/torso tracking. This is a Quest 3 hardware limitation, not fixable in software.
- **Body tracking update rate**: Body data arrives at ~36fps regardless of display refresh rate (120Hz). Interpolation/smoothing could make transitions appear smoother but would not reduce latency.

### Controller/Hand Tracking Mode Switch
- Switching to controllers (e.g., to interact with system menus) disables hand and body tracking for the remainder of the session
- Tracking does not re-engage until the app is restarted and controllers are set aside before launch
- Not blocking for prototype (players will never use controllers) but worth noting

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
1. ~~**Full body occlusion**~~ — **COMPLETE (first pass).** Capsule person deployed and tested. Player sees real body as passthrough silhouette. Polish issues deferred to Tier 3.
2. **Torch tracking** — Track a physical prop while player carries it.
3. **Passthrough-to-VR transition** — Gradual blend from real world into underworld. Selective Passthrough shader CONFIRMED WORKING (proof of concept April 5). Next step: architectural decision on how to invert the effect — player needs to start in passthrough and see the cave through a portal, not the reverse. Requires Co-Creative Director direction.

### Tier 2: Important for Prototype Quality
4. ~~**Spatial audio foundation**~~ — **COMPLETE.** Spatializer plugin, Audio Mixer, room acoustics, test source all working. Further audio work (ambient soundscape, actor voice, additional sources) continues as part of ongoing development.
5. **Set piece tracking via QR codes or other trackables** — Place set pieces anywhere, world adapts. QR tracking confirmed available in MRUK v85 with 6DOF pose and payload data.
6. **"Don't look back" detection** — Head rotation threshold detection.
7. **Bridge wobble tracking** — Arduino accelerometer on physical beam, data to Unity via BLE.

### Tier 3: Polish Phase
8. **Passthrough color linked to torch proximity**
9. **Hand/body occlusion edge refinement** — upgrade capsule person to proper humanoid mesh via Character Retargeter
10. **Environment visual polish**
11. **Advanced sound design** (environmental variation, dynamic acoustics per location)

---

## 8. Research Areas — Documentation Status

### Reviewed by Co-Creative Director (April 4, 2026)
The Co-Creative Director has read all uploaded SDK documentation at a high level. Key areas reviewed: Spatial Audio (spatialization, room acoustics, ambisonics, ray tracing), Passthrough (compositing, masking, occlusions, selective passthrough shader), MRUK (trackables, QR codes, scene data, EffectMesh, destructible mesh), Voice SDK, Microgestures, Eye Tracking, Hand/Body Tracking, Interaction SDK, AI Building Blocks (agents, STT, TTS, LLM, object detection), and performance optimization guides.

### Needs Detailed Developer Review Before Implementation
| Topic | Notes |
|-------|-------|
| Meta XR Audio SDK setup in Unity | **DONE** — Spatializer plugin, mixer, room acoustics, spatialized source all set up and tested April 5 |
| Selective Passthrough shader | **DONE** — Shader and material located in Core SDK Editor/BuildingBlocks path, copied to Assets for build inclusion. Shader is Oculus/SelectivePassthrough, uses Blend Zero SrcAlpha. Cull Off added. Proof of concept tested and working April 5. |
| QR Code Tracking in MRUK | Tracker configuration, event subscription, payload handling |
| Movement SDK Character Retargeter | For refined body occlusion (Tier 3) |

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
| Body occlusion via capsule primitives + depth shader | Direct OVRPlugin.GetBodyState4() joint access, 12 capsules + 5 spheres, sizeMultiplier 1.4 | April 4-5 |
| Body occlusion first pass accepted | Polish issues deferred to Tier 3. Body is no longer a blocker. | April 5 |
| Spatial audio promoted to prototype milestone | Sound is what makes the cave real; SDK supports it natively | April 4 |
| Spatial audio foundation accepted | Two Tier milestones cleared in one day. | April 5 |
| Portal transition is next active priority | Remaining Tier 1 challenge not requiring physical props. | April 5 |
| Spatial audio is next active priority | Sound before portal. We need to hear the cave before we open the door into it. | April 5 |
| Underworld tone: wet stone, water as dominant sound | Aligned with narrative and atmospheric goals | April 4 |
| Player is Orpheus (POV) | The experience is told from Orpheus's perspective, not Eurydice's | April 4 |
| State of Project on GitHub | Single source of truth, editable via Claude Code, fetchable by all conversations | April 4 |
| Document governance: facts open, decisions restricted | Any role reports facts; only Co-Creative Director authors design decisions | April 4 |

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
1. Fetch the State of Project from GitHub and read it
2. Check Inter-Team Messages for messages addressed to your role
3. State what you want to work on
4. If any SDK versions have changed, update this document immediately

### Before Giving Instructions
1. Reference the SDK documentation PDFs in the knowledge base for the specific feature
2. If documentation is not available, say so — do not guess
3. Specify exact Unity paths: which object → which component → which field → what value

### After Completing Work
1. Update this document with any changes (respecting governance rules)
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
│   ├── DepthOnlyHand.shader (Custom/DepthOnlyHand — Cull Off added April 5)
│   ├── RequestSpatialPermission.cs
│   ├── RequestBodyTracking.cs
│   ├── BodyTrackingDebug.cs
│   ├── PassthroughStyling.cs (REMOVED from scene, file may still exist)
│   ├── CapsuleBodyOcclusion.cs (deployed and tested April 5)
│   ├── SetRefreshRate.cs (added April 5)
│   └── ProceduralTestTone.cs (added April 5)
├── Shaders/
│   └── SelectivePassthrough.shader (Oculus/SelectivePassthrough — Cull Off, copied from Core SDK April 5)
├── Materials/
│   ├── CaveMaterial
│   ├── FloorMaterial
│   ├── TestMaterial
│   ├── HandOcclusionMaterial
│   └── SelectivePassthroughPortal.mat (Selective Passthrough material, April 5)
```

---

## 14. Next Session Plan

### Completed This Session (April 5)
- Body occlusion: capsule person deployed, tested, working
- Spatial audio foundation: spatializer, mixer, room acoustics, test source all working
- Claude Code + MCP pipeline: connected and used for scene setup
- 120Hz display refresh rate enabled

### Next Priorities (Awaiting Co-Creative Director Direction)
1. Prototype portal transition using Selective Passthrough shader
2. Additional spatial audio work (ambient soundscape, actor voice spatialization)
3. Torch tracking research/implementation

---

## 15. Infrastructure TODO
- [x] Upload State of Project document to Claude Project knowledge base
- [x] Paste Project Instructions into Claude Project settings
- [x] Save and upload SDK documentation PDFs (extensive collection uploaded)
- [x] Create Developer conversation
- [x] Create Researcher conversation
- [x] Open new Co-Creative Director conversation (opened April 4, 2026)
- [x] Install Python 3.13 via Homebrew (MCP server requires Python, not Node)
- [x] Install Claude Code on Mac (native installer)
- [x] Set up MCP Unity bridge in Unity project (CoplayDev unity-mcp, beta branch)
- [x] Create GitHub docs repo for State of Project (https://github.com/JoshuaCrisp/orpheus-docs)
- [ ] Set Git identity (`git config --global user.name` / `user.email`)
- [ ] Set up wireless ADB for cable-free Quest deployment
- [x] Update Project Instructions to include GitHub URL for State of Project fetching (added April 5)

---

## 16. Inter-Team Messages

### For: Co-Creative Director
- [FROM Developer, April 5] Portal passthrough proof of concept COMPLETE. Selective Passthrough shader (Oculus/SelectivePassthrough) from Meta XR Core SDK confirmed working on Quest 3. Shader uses Blend Zero SrcAlpha to punch holes in VR rendering, revealing passthrough underlay. Both shader and material were in an Editor-only SDK path and had to be copied into Assets/ for device builds. Cull Off added to shader for double-sided visibility. Test results: passthrough shows cleanly through a door-sized quad in the VR cave — sharp edges, no fog interference, body occlusion unaffected. KEY DESIGN FINDING: The shader erases VR to reveal passthrough. For Orpheus, we need the inverse — the player starts in passthrough and sees the cave THROUGH a portal. This likely requires a large Selective Passthrough shell surrounding the player (sphere, box, or quads covering all directions), with a door-shaped opening cut out. The cave renders everywhere but is hidden by the shell; only the opening reveals the cave. Walking through the opening puts the shell behind the player, leaving them fully in the cave. This is an architectural/creative decision requiring Co-Creative Director direction. Files created: Assets/Shaders/SelectivePassthrough.shader, Assets/Materials/SelectivePassthroughPortal.mat. Scene objects: PortalTestObj/PortalQuad in Underworld scene (test quad, can be repurposed or removed). Minor finding: switching to controllers disables hand/body tracking for the rest of the session — requires app restart.

### For: Developer
(No new messages)

### For: Researcher
(No new messages)

### For: All
- (no new messages)

---

## 17. Resolved Messages

(Messages moved here after being read and addressed by the recipient)

- [FROM Co-Creative Director, April 5] Priority research: Depth API for body-only occlusion? → **RESOLVED by Researcher April 5. Answer: No. Read and integrated by Co-Creative Director April 4.**
- [FROM Co-Creative Director, April 5] Secondary research: AI Building Blocks capabilities? → **RESOLVED by Researcher April 5. No image segmentation in v85. Read and integrated by Co-Creative Director April 4.**
- [FROM Researcher, April 5] Depth API findings for Co-Creative Director → **Read and acknowledged April 4. Decision: Depth API stays disabled.**
- [FROM Researcher, April 5] AI Building Blocks findings for Co-Creative Director → **Read and acknowledged April 4. Decision: AI Building Blocks reserved for future use.**
- [FROM Researcher, April 5] Body occlusion approach confirmed for Developer → **Read by Developer April 5. Script written, deployed, and tested using confirmed approach.**
- [FROM Developer, April 4] Infrastructure complete: Claude Code + MCP bridge connected, GitHub docs repo created, CapsuleBodyOcclusion.cs written and ready for deployment. → **Read and integrated by Co-Creative Director April 4.**
- [FROM Developer, April 5] Body occlusion first pass COMPLETE. Capsule person deployed, tested, and working. → **Read and acknowledged by Co-Creative Director April 5. Body occlusion first pass accepted. Polish issues deferred to Tier 3. Body occlusion is no longer a blocker.**
- [FROM Co-Creative Director, April 5] Spatial audio directive for Developer → **Read and completed by Developer April 5. Spatializer, mixer, room acoustics, and test source all deployed and confirmed working.**
- [FROM Developer, April 5] Spatial audio foundation COMPLETE report → **Read and acknowledged by Co-Creative Director April 5. Spatial audio foundation accepted.**
- [FROM Co-Creative Director, April 5] Portal transition directive for Developer → **Read by Developer April 5. Proof of concept completed: Selective Passthrough shader located, copied, tested, confirmed working. Findings and architectural question reported back to Co-Creative Director.**

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
