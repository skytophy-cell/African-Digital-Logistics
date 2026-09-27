# EcoDash – African Logistics Simulation
 `EcoDash-African-Logistics`

## Project description
EcoDash is an interactive 2D logistics simulation based on the challenge of moving essential medical supplies to an underserved rural clinic. The player controls a solar-assisted delivery drone across an African-inspired landscape while managing battery energy, weather, wind, load-shedding, obstacles, collisions, time and delivery objectives.

The simulation intentionally models constraints rather than presenting a conventional arcade game. The player must plan movement, protect battery capacity and use solar microgrid zones when the grid is available.

## Features implemented
- HTML5 Canvas rendering and animation loop.
- Vanilla JavaScript ES6 classes: `Vector2`, `Particle`, `Player`, `Obstacle`, `SolarZone`, `DeliveryPoint`, `World`.
- Smooth acceleration, velocity and drag.
- `Math.sin()`, `Math.cos()` and `Math.atan2()` for directional physics.
- Vector-based wind modifier.
- Dynamic battery drain, boost drain and solar recharge.
- Load-shedding periods that disable solar charging.
- African-inspired savanna, rural huts, acacia trees, roads and geometric decorative motifs.
- Potholes, river, trees, wildlife and construction-zone hazards.
- AABB rectangle collision detection.
- Weather states: clear, wind, rain and dust.
- Generated sound effects using the browser Web Audio API; no external sound library.
- HUD showing battery, score, time, weather and grid status.
- Start, playing, pause, win and game-over states.
- LocalStorage high-score persistence.
- Restart without refreshing the page.
- Responsive page layout.
- Original-feature candidate: contextual dust/boost particle behaviour and dynamic weather. **Before submission, the student must verify/adapt the feature independently if the brief requires a strictly AI-free feature.**

## Controls
| Action | Key |
|---|---|
| Move | WASD / Arrow Keys |
| Boost | Shift |
| Pause/Resume | P |
| Sound On/Off | M |
| Restart after mission | R |

## How to run
1. Download or clone the project.
2. Open `index.html` in a modern browser, or serve the folder through a simple local web server.
3. Click the canvas to start.
4. Deliver the package to the **RURAL CLINIC** marker.
5. Use solar microgrid circles to recharge while load-shedding is not active.

No npm installation, build process, external framework or external game engine is required.

## Project structure
```text
EcoDash-African-Logistics/
├── index.html
├── README.md
├── .gitignore
├── docs/
│   ├── African_Context_Report.md
│   ├── AI_Reflection_Log.md
│   ├── Wireframe_Notes.md
│   ├── GitHub_Commit_Plan.md
│   ├── Presentation_Code_Defence.md
│   ├── Testing_Checklist.md
│   └── References.md
├── screenshots/
│   ├── start-screen.png
│   ├── gameplay.png
│   └── mission-result.png
├── assets/
│   └── README.md
└── src/
    ├── game.js
    └── styles.css
```

## Architecture
The project follows an object-oriented design. `World` owns the simulation state and coordinates updates. `Player` owns movement and battery behaviour. `Vector2` provides reusable vector operations. `Obstacle` provides common environmental hazard behaviour. Rendering functions are kept separate from the simulation update methods so that the animation loop remains easy to explain during code defence.

### Physics model
The player direction is represented by an angle:

`angle = Math.atan2(inputY, inputX)`

The directional thrust vector is then calculated with:

`thrustX = Math.cos(angle) * thrust`

`thrustY = Math.sin(angle) * thrust`

Velocity is accumulated, capped at a maximum speed, modified by environmental wind, multiplied by drag, and then applied to position. Battery consumption is linked to movement speed and boost use.

### Collision model
The simulation uses axis-aligned bounding-box (AABB) collision. The player's rectangular bounds are compared with each obstacle rectangle. On collision, the drone is pushed back, velocity is reduced/reversed, battery is reduced, and score is penalised.

## AI usage disclosure
Generative AI was used as a learning and development support tool for planning, code structure, explanations and documentation. AI-generated suggestions were reviewed and modified rather than treated as authoritative. The final submission must only claim understanding of code the student can explain.

The assignment also requires one original feature to be developed **without Generative AI**. The supplied project contains a candidate implementation, but the student should independently redesign or modify that feature and document the manual implementation process before claiming it as their AI-free original feature.

See `docs/AI_Reflection_Log.md` for the prompt, response summary, problems found and modifications.

## GitHub requirement
The assessment requires at least **8 meaningful commits on different days**. This ZIP cannot truthfully create historical development days for the student. Use `docs/GitHub_Commit_Plan.md` to make real commits as development continues. Do not backdate or fabricate commits.

Suggested sequence:
1. Initial Canvas project structure.
2. Base canvas and responsive layout.
3. Player class and keyboard movement.
4. Vector/trigonometric physics and battery.
5. Obstacles and collision detection.
6. Weather/load-shedding/solar zones.
7. HUD, scoring, game states and localStorage.
8. Final polish, documentation and testing.

## Academic references
The report includes academic sources relevant to drone logistics and African transport/e-mobility. Because the assignment specifically requires **two references from the Stadio Library**, the student must verify that the selected academic articles/books are accessible through the Stadio Library portal and retain evidence of that search. Do not falsely state library availability without checking.

## Academic integrity
This project is supplied as a working learning scaffold. The student must understand and be able to explain every submitted line, complete their own GitHub history, independently implement the required AI-free feature, and replace any placeholders with their own identity details.
