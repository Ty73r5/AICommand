# Primary Injection Field Lab, Rev 2

A self-contained HTML educational application for a shorted primary-injection output loop and a movable monitoring CT. No build process, external JavaScript, analytics, or network connection is required to run the downloaded page in a browser that executes local HTML.

## Open the working webpage

Latest revision:

https://raw.githack.com/Ty73r5/AICommand/main/primary-injection-ct-guide/index.html

Pinned Rev 2 application:

https://rawcdn.githack.com/Ty73r5/AICommand/e1edeacc2fc982786d2c9d2d91e6a88aa0b1d69a/primary-injection-ct-guide/index.html

These are runnable Raw Githack webpages, not GitHub source views. No GitHub Pages configuration is needed. Raw Githack is an independent third-party proxy and may show a destination confirmation before opening HTML. The branch URL can cache changes briefly; the commit URL is fixed to this revision. For iPad, open the web URL in Safari or Chrome rather than relying on a Files/Quick Look preview to execute local JavaScript.

## What changed

- Replaced decorative circular field rings with vectors and numerically integrated streamlines from the same closed-loop Biot-Savart solution.
- Uses the analytic field of each finite straight filament segment. Rounded bends use short segments. The assumed internal return is visible and completes the modeled current loop.
- Removed unsupported placement scores, steel/heat/leakage severity multipliers and aggregate uncertainty ranges. Smaller arbitrary coefficients would not constitute validation.
- Separates assigned primary current, ideal CT indication, an assumed linear CT equivalent-circuit example, a shunt example, and user-entered real measurements.
- The ideal CT indication remains independent of location while it encloses the same single current path. Field nonuniformity is not converted into a claimed CT percentage error.
- Includes secondary burden resistance/reactance, lead-loop resistance, winding resistance, magnetizing inductance, core-loss resistance, frequency, core area and an entered knee voltage. These are explicit example parameters, not a calibrated monitor model.
- Shows shunt voltage, dissipation, entered temperature-coefficient effects and lumped residual inductance. A series shunt is not automatically an error-free reference.
- Adds a prominent 0.4x to 8x zoom control, CT focus, front/top views, reset, two-pointer pinch/pan, mouse pan, keyboard controls and synchronized CT-position controls.
- Adds slow AC-phase playback and half-cycle reversal while keeping RMS readings distinct from instantaneous current.
- Adds measured CT/reference pairs with local browser storage, per-record deletion and CSV export. Records are not uploaded. CSV includes simulation settings and instrument/condition notes.
- Includes variable definitions, equations, source links, safe comparison guidance and explicit limitations.

## Controls

One finger or left mouse drag rotates the schematic. Drag the CT to move it on the straight cable run. Two fingers pinch and pan. Mouse wheel zooms; right-drag or Shift-drag pans. Arrow keys rotate when the scene has focus; plus/minus zoom. The position and radial-offset sliders provide alternatives to direct manipulation.

The Center CT at midspan button does not change the joint-closure checkbox or imply that a real joint has been closed.

## Scientific scope

The field solution is a quasistatic free-space filament-current approximation, evaluated outside the conductor radius. The housing is visual context, not a steel boundary. The CT core's magnetic reaction, steel permeability/eddy currents, actual transformer leakage, skin/proximity current distribution, harmonics, switching transients, DC offset, remanence and nonlinear saturation are not solved.

The external-field control applies an assumed uniform in-phase AC field. It is not a prediction of transformer leakage. The displayed magnetic field at the sampling ring is an unperturbed air field, not working CT core flux density.

The upper/lower output arrangement is representative. It is not a dimensionally verified CB-8160 model, and the equivalent conductor is not an ampacity recommendation.

The linear CT circuit assumes a current-output CT and one primary turn. It must not be directly substituted for a voltage-output current monitor with an internal burden, a Rogowski probe, or a Hall sensor. At or above the entered knee-voltage screening value, the linear indication is withheld. A value below the knee does not establish accuracy.

Midspan is a repeatable starting location, not a mathematically or experimentally proven optimum for a real test set. Determine actual position dependence using the monitor's instructions and repeatable simultaneous comparisons against a suitable calibrated reference. Never select a location solely because one reading happens to agree.

## Tests performed

The standalone HTML runs eight numerical self-checks on load: finite-wire magnitude; right-hand-rule direction; centered and off-center closed-contour Ampere checks; cancellation of an added uniform field around the contour; zero-current field; zero-burden ideal CT ratio; and nominal shunt Ohm's law.

Browser checks performed in Chromium with desktop, tablet and phone viewport/touch emulation:

- No JavaScript page errors or horizontal page overflow in the tested layouts.
- All eight built-in numerical self-checks passed.
- CT dragging, CT position buttons, zoom slider, focus and reset worked.
- A two-touch separation doubling produced a 2.0x model-zoom change in tablet and phone emulation without rotating the view.
- Zero current, open-joint handling, knee-limit withholding, entered shunt temperature coefficient and measured-pair CSV export passed.
- The Ampere contour was checked across 96 geometry/position/offset combinations. Maximum absolute residual at 6000 A was approximately 1.37e-11 A, reflecting numerical consistency of the assumed model, not instrument accuracy.

These tests were not performed on physical iPad or Android hardware. A WebKit executable was unavailable in the test environment, so native Safari execution is not claimed.

## Safety and metrology

Stop injection and de-energize before moving a CT or touching output connections. Never open a current-output CT secondary while primary current flows. Follow equipment ratings, duty cycle and the applicable safe work procedure. The app is not an equipment operating manual, certified calibration program, finite-element validation, uncertainty budget or safety assessment.

Source links and model equations are included inside `index.html`. Previous revisions remain in Git history.
