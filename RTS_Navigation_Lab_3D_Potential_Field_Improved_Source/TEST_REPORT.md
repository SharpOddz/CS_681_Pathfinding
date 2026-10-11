# Focused automated regression report

Chromium was used with the original navigation core run in the application's DOM and no Three.js module. Rendering of native animated GLBs was not exercised here.

1. Single heavy-vehicle controller traversed the **H, office, 20/30/100 circles, and 20/30/100 rectangles** in one 8-environment set. All eight reached their assigned target. A safety check ran after every simulated timestep: **zero breaches of the 8-pixel protected clearance**.
2. A five-heavy-unit hybrid movement test planned all five routes in the H, office, 30/100 circle and 30/100 rectangular environments, without protected obstacle-margin breaches. In one sampled batch, all five reached the office target. Some heavy groups stalled due to congestion in dense environments; this is not claimed as a universal arrival guarantee.
3. A 20-unit mixed deployment spawned all 20, including 10 heavy, in office, H, 100-circle and 100-rectangle environments with **zero initial protected-footprint obstacle overlaps**.
4. An RRT heavy route test on H, office, 100-circle and 100-rectangle environments produced continuous clearance-validated routes. When sampling failed, an explicitly labeled A* safety fallback was used.
5. A heavy unit followed three queued user checkpoints around the H geometry with **zero protected-margin incursions** and completed the sequence.
6. JavaScript syntax verification completed with Node 22 (`node --check`).

Sampled tests cannot prove the absence of every possible deadlock or model-art/obstacle contact in a live 3D browser. If there is no feasible path for the footprint, the simulator reports a blocked route.


Additional checks added for potential-field visualization readability and group-mode obstacle bypass around circular obstacles.
