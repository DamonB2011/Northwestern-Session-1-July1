# Rocket & Rocket Nozzle Design — SolidWorks

## Overview

I designed a rocket and rocket nozzle in SolidWorks, then ran both through SolidWorks Flow Simulation under subsonic and supersonic conditions to see how they actually performed instead of just trusting the CAD geometry. I looked at vortex formation, pressure distribution, and how nozzle orientation affects thrust and lift generation. Both stayed CAD and simulation only, no physical print.

## Rocket Body

### Design Goal
I wanted a nose cone shape that minimized drag across both subsonic and supersonic regimes, since the rocket has to transition through both during a real flight.

### Initial Version → Modified Version
My first version ran into two problems at once. Aerodynamically, the nose tip was too blunt, so the supersonic simulation showed a detached shock wave sitting further out from the surface than it should, which spiked drag way higher than expected. Structurally, the wall thickness I'd set near the tip was too thin for the geometry, and the part flagged stress concentration right at the tip junction when I checked it, a weak point that would have failed under real load even though it looked fine in the CAD model.

I went back into SolidWorks and built a **Modified** version of the part. I sharpened the nose profile to move the shock wave closer to the surface and cut supersonic drag, and I thickened the wall section right at the tip junction to remove the stress concentration without changing the outer aerodynamic profile. Re-running Flow Simulation on the modified part showed the shock sitting tighter against the nose like I wanted, and the stress check came back clean.

That back and forth, sim it, find what breaks, go fix the actual part, was the real work. The first version looking right in CAD didn't mean it worked.

### Subsonic Testing
At subsonic speeds, I saw smooth, attached airflow along most of the body with a small pressure buildup right at the nose tip. Drag stayed low, and the flow didn't separate significantly anywhere along the body.

### Supersonic Testing
At supersonic speeds, I picked up a shock wave forming just ahead of the nose tip, with a sharp pressure spike concentrated right at the leading point. Vortices started forming further back along the body where the shock interacted with the boundary layer.

### Optimal Nose Tip
A sharper, more pointed tip performed better at supersonic speeds by pushing the shock wave closer to the surface and reducing wave drag, but it traded off some structural strength and slightly worse subsonic performance compared to a more rounded tip. I landed on a moderately pointed profile that balanced both regimes instead of maximizing either one.

## Rocket Nozzle

### Design Goal
I wanted a nozzle orientation and shape that converted internal pressure into thrust as efficiently as possible while contributing usable lift during ascent.

### Subsonic Testing
At subsonic exit speeds, the flow through the nozzle stayed smooth and attached, with pressure dropping steadily as expected through the converging section.

### Supersonic Testing
At supersonic exit speeds, I saw the expected expansion in the diverging section, with vortices forming near the nozzle exit where the expanding flow met the surrounding lower pressure air. The pressure gradient there was the strongest indicator of how much thrust the nozzle was actually generating.

### Optimal Orientation
Angling the nozzle slightly relative to the rocket's centerline redirected some of the exhaust thrust into a small lift component, without losing so much axial thrust that it hurt overall performance. Straight axial orientation gave the most raw thrust, but the slight angle gave a better combined thrust-and-lift outcome for the flight profile I was targeting.

## Key Findings

- Vortex formation showed up consistently at the transition points, right where the shock wave met the boundary layer on the rocket body, and right at the nozzle exit where expanding gas met ambient air.
- Pressure spiked hardest at the nose tip under supersonic conditions, which is why tip geometry mattered more for drag than anything else on the body.
- Nozzle orientation was a tradeoff between raw thrust and usable lift, not a single optimal answer independent of flight goals.

## Tools Used

- SolidWorks (CAD design)
- SolidWorks Flow Simulation (subsonic and supersonic airflow analysis, vortex visualization, pressure mapping)
