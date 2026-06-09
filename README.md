<h2><u>Sum Pop</u></h2>

Sports Academy Games — Web Game Developer Submission
Anushka | https://sum-pop.onrender.com

<h2><u>Play the game</u></h2>

Open index.html in any browser. No install, no server, no build step needed.

<h2><u>What is Sum Pop?</u></h2>

A math bubble game where you select numbers that add up to a target, then pop them. The math is not a quiz sitting on top of the game. The math is the game. You cannot do anything without doing addition.

Three difficulty levels:

Easy — targets 5 to 15, numbers 1 to 9, 90 seconds
Medium — targets 10 to 30, numbers 1 to 15, 75 seconds
Hard — targets 15 to 50, numbers 1 to 25, 60 seconds

Each level has a streak system, combo popups, level progression every 5 correct pops, a hint button, high scores saved locally, and bubble refill when the board gets sparse.

<h2><u>Why this design works</u></h2>

The mechanic forces real math.
You see a target number. You scan the board. You build a sum in your head. You tap the bubbles. You either got it or you didn't. There is no option to skip the math or guess randomly because wrong attempts break your streak.
The addiction loop.
Correct pop feels satisfying (bubble burst animation, score jump, streak counter). Wrong pop feels bad (screen shake, streak reset). Both feelings make you want to try again. That loop is what makes CoolMathGames games hard to put down.
Streak and combo system.
Getting 3 or 4 pops in a row lights up a combo banner and multiplies your score. Kids will chase that multiplier.
Level progression.
After every 5 correct pops the numbers get slightly larger. You are always being pushed forward without a difficulty wall appearing suddenly.

<h2><u>AI workflow used to build this</u></h2>

Phase 1 — Concept
Used Claude to define the mechanic. The key question was: "what is a game where the math is the action, not the reward?" The bubble selection concept came from that constraint.
Phase 2 — Design brief
Ran a design session in Claude to define the visual system: colour palette, typography, animation behaviour, screen states, HUD layout. The spec covered the title screen, game screen, results screen, feedback states, and the bubble rendering approach.
Phase 3 — Art and asset generation
All visuals are rendered in HTML Canvas with JavaScript. In a full production build this is where Ludo AI would generate the bubble sprites, background textures, and pop particle sheets. The Ludo prompt anchor for this game would be: "colourful round bubbles with shine highlight, bold number labels, cel shaded, transparent background, arcade game style."
Phase 4 — Assembly
Claude Code generated the game engine, bubble physics, no-overlap placement algorithm, and the sum validation logic. Cursor was used to iterate on edge cases like bubble refill and hint detection. Total build time was around 30 minutes.

<h2><u>File structure</u></h2>

sum-pop
├── index.html    
└── README.md    

<h2><u>Known minor issues (and how I would fix them)</u></h2>
Bubbles can overlap slightly after refill because the no-overlap check uses the original radius and does not account for the float animation offset. Fix: run placement check against the animated Y position, not the base Y.
Hint button only works once per game. Intentional for balance, but in a production build I would give the player 3 hints total with a cooldown timer between uses.
No sound yet. In production this would use the Web Audio API for a pop sound on correct, a thud on wrong, and a chime on level up. Ludo AI would generate the SFX.
