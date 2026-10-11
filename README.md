# RTS Navigation Lab 3D — Heavy-safe paths

Open `index.html` directly in Chrome or Safari on Mac. No Terminal or local server is needed. A network connection is needed to load the pinned Three.js library.

## Heavy vehicle navigation

- Large units now reserve their 29-pixel simulation footprint **plus an 8-pixel safety buffer** when spawning, planning, path shortcutting, choosing goals, steering, braking and integrating their position.
- Exact continuous swept circle-versus-circle and circle-versus-axis-aligned-box tests guard actual motion; an unsafe move is rejected.
- A* retries at an 8-pixel grid when the 16-pixel grid misses a viable narrow corridor. For RRT, a full-clearance A* rescue is indicated in the event log when RRT cannot find a route within its iteration budget.
- Random environments containing heavy units retry up to 160 times to select a map with a demonstrably available central heavy route, without deleting the required 20, 30 or 100 obstacles.
- Group destinations are individually collision-checked and heavy units receive reachable slots. Vehicles nearer the front of a convoy get forward goal slots, reducing head-on congestion.
- If a safe route does not exist, the unit stays put and reports the failure rather than touching obstacles.

## Caveats

The collision safety guarantee applies to the simulator's conservative 2D circular model hulls and obstacle footprints; an animation whose moving weapon or decorative appendages extend beyond that physical hull is not a full 3D rigid-body collision simulation. Groups can still deadlock around other units on very congested maps; they never become intangible to resolve this. Potential-fields-only movement can reach local minima by design. The viewer requires live Three.js on a connected browser for 3D rendering.

The original shift-click manual checkpoints, all environment layouts, camera controls and 3D model assets are preserved.


Potential-field improvements: higher-contrast field overlay; denser 3D force arrows; group-mode local-minimum bypass waypoint insertion around blocking obstacles; blocked status if escape attempts fail.
