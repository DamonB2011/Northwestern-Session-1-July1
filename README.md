# Rocket & Rocket Nozzle Design - SolidWorks

<p float="left">
  <img src="Rocket Nozzle 2.jpeg" width="45%" />
  <img src="Dynamic Fluid Rocket Model 4.jpeg" width="45%" />
</p>
<p float="left">
  <img src="Rocket Model 2.jpeg" width="45%" />
  <img src="Dynamic Fluid Rocket Model 6.jpeg" width="45%" />
</p>

## Overview

I designed a rocket and a rocket nozzle in SolidWorks, then ran both through SolidWorks Flow Simulation under subsonic and supersonic conditions to see how they actually held up instead of just trusting what the CAD geometry looked like. I looked at vortex formation, pressure distribution, and how nozzle orientation affects thrust and lift. Both stayed CAD and simulation only, no physical print.

I focused on the atmospheric phase of flight on purpose, not deep space. Once a rocket clears the atmosphere, the physics gets a lot easier, there's no air resistance to fight anymore, so momentum basically carries it the rest of the way. The genuinely hard aerodynamic engineering happens while it's still pushing through air: managing shock waves, drag, and structural loads at subsonic and supersonic speeds. That's the part actually worth optimizing, so that's where I put the effort.

## Rocket Body

### Design Goal

I wanted a nose cone shape that minimized drag across both subsonic and supersonic regimes, since the rocket has to pass through both on its way up through the atmosphere.

### Initial Version / Modified Version

My first version had two problems at once. Aerodynamically, the nose tip was too blunt, so the supersonic simulation showed a detached shock wave sitting further off the surface than it should, and that alone spiked drag way higher than I expected. Structurally, the wall thickness I'd set near the tip was too thin for the geometry, and when I checked it, the part flagged a stress concentration right at the tip junction, a weak point that would've failed under real load even though it looked totally fine in CAD. So I went back in and built a Modified version.

I sharpened the nose profile to pull the shock wave in closer to the surface and cut supersonic drag, and thickened the wall section at the tip junction to kill the stress concentration without touching the outer aerodynamic shape.

Re-running Flow Simulation on the modified part showed the shock sitting tight against the nose like I wanted, and the stress check came back clean. That back and forth, sim it, find what breaks, fix the actual part, was the real work here. The first version looking right in CAD didn't mean it actually worked.

### Subsonic Testing

At subsonic speeds, airflow stayed smooth and attached along most of the body, with a small pressure buildup right at the nose tip. Drag stayed low and the flow didn't really separate anywhere along the body.

### Supersonic Testing

At supersonic speeds, a shock wave formed just ahead of the nose tip, with a sharp pressure spike right at the leading point.

Vortices started showing up further back along the body, right where the shock interacted with the boundary layer.

### Optimal Nose Tip

A sharper, more pointed tip did better at supersonic speeds, it pushed the shock wave in closer and cut wave drag, but it cost some structural strength and slightly hurt subsonic performance compared to a rounder tip. I landed on a moderately pointed profile that balanced both regimes instead of maxing out either one.

## Rocket Nozzle

### Design Goal

I wanted a nozzle orientation and shape that turned internal pressure into thrust as efficiently as possible, while also contributing a bit of usable lift during ascent through the atmosphere.

### Subsonic Testing

At subsonic exit speeds, flow through the nozzle stayed smooth and attached, with pressure dropping off steadily through the converging section like you'd expect.

### Supersonic Testing

At supersonic exit speeds, I saw the expected expansion in the diverging section, with vortices forming near the nozzle exit where the expanding flow met the lower-pressure air around it.

That pressure gradient was the clearest signal for how much thrust the nozzle was actually putting out.

### Optimal Orientation

Angling the nozzle slightly off the rocket's centerline redirected a bit of the exhaust thrust into lift, without losing so much axial thrust that it hurt overall performance. Straight axial gave the most raw thrust, but the slight angle gave a better combined thrust-and-lift outcome for what I was actually targeting.

## Key Findings

- Vortex formation showed up consistently at the transition points, where the shock wave met the boundary layer on the body, and right at the nozzle exit where expanding gas met ambient air.
- Pressure spiked hardest at the nose tip under supersonic conditions, which is why tip geometry mattered more for drag than anything else on the body.
- Nozzle orientation was a tradeoff between raw thrust and usable lift, not one clean answer independent of what the flight was actually for.
- Sticking to the atmospheric phase instead of the post-atmosphere coast meant every decision here had to fight real physical constraints instead of idealized ones.

## Tools Used

- SolidWorks (CAD design)
- SolidWorks Flow Simulation (subsonic and supersonic airflow analysis, vortex visualization, pressure mapping)

## Files in This Repo

- `rocket123.SLDPRT`, `rocket (improved).SLDPRT` - rocket body iterations
- `rocket nozzle.SLDPRT` - nozzle part file
- `Rocket Model 1-2.jpeg` - rendered rocket body views
- `Rocket Nozzle 1-3.jpeg` - nozzle design and simulation views
- `Dynamic Fluid Rocket Model 1.MOV`, `Dynamic Fluid Rocket Model 2-7.jpeg` - Flow Simulation results, fluid dynamics visualization
- `Low-Poly Rocket Model 1 2.jpeg` - low-poly reference/render
- `Stress Rocket 1.jpeg`, `Stress Rocket 2-3.MOV` - stress test results on the nose tip junction
