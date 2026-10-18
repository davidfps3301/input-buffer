# dynamicv3
What is it?
Input Buffering is a mod for Geometry Dash that expands the time window in which the player can successfully hit a click. Its purpose is to eliminate deaths caused by frame imprecision in extreme levels, where a single frame of difference decides whether you survive or die.

In simple terms: it makes difficult clicks easier to hit without requiring the player to execute them with perfect precision.

What does it do exactly?
The mod implements an intelligent input buffer. When the player presses or releases the jump button, the mod does not execute the action immediately. Instead:

It holds the player's intent (the click or the release).

It simulates the next physics ticks to determine which one would be safe for the input.

It applies the input on the correct tick, not on the tick when the player clicked.

The result is that the player can click several ticks early, and the mod automatically shifts it to the exact tick where the action is valid. This turns a 1-frame timing (nearly impossible to execute consistently) into a 2, 4, or 8-frame margin, depending on the configured stage.

How is it controlled?
F6 key: cycles through the mod's stages.

Off: vanilla behavior, no assistance.

Stage 1 (2 ticks): 2-frame margin.

Stage 2 (4 ticks): 4-frame margin.

Stage 3 (8 ticks): 8-frame margin.

On-screen overlay: shows the current stage and how many ticks were "saved" on the last applied input.

Which game modes does it work in?
Cube: allows clicking in the air, and the jump executes upon landing, extending the native hold-to-jump beyond what the game allows.

Wave: the most critical case. It buffers both press (hold) and release, eliminating deaths from releasing a frame early or holding a frame too long.

Ship, UFO, Ball, Robot, Spider: buffers inputs the same way, with mode-specific calibration.

Why is it controversial?
The mod makes the game significantly easier in levels where everything is decided by frames. A player using it with 2 ticks can already pass clicks that in vanilla would require perfect precision. With 8 ticks, the game becomes "ridiculously easy" in the words of the video's creator.

That's why:

It goes against the competitive integrity of the Demon List and the extreme levels community.

It is practically undetectable with 1 or 2 ticks, because the delay is minimal and the result looks like a perfectly executed click.

Its existence is a warning: it shows that the community needs better cheat detection methods, especially as levels become increasingly difficult.

How does it work technically?
The mod hooks into the game's physics functions, specifically PlayerObject::update and the input handlers. On each tick:

It checks if there is a pending input (buffered click or release).

It simulates the next physics step with that input applied.

It checks whether the player would survive (no lethal collision).

If they survive, it applies the input; if not, it waits for the next tick (until the N-tick window is exhausted).

This process repeats until a safe tick is found or the window expires. It is the same technique used by Click Between Frames (CBF) for sub-frame precision, but applied specifically to input buffering

<img src="logo.png" width="150" alt="the mod's logo" />

*Update logo.png to change your mod's icon (please)*

## Getting started
We recommend heading over to [the getting started section on our docs](https://docs.geode-sdk.org/getting-started/) for useful info on what to do next.

## Build instructions
For more info, see [our docs](https://docs.geode-sdk.org/getting-started/create-mod#build)
```sh
# Assuming you have the Geode CLI set up already
geode build
```

# Resources
* [Geode SDK Documentation](https://docs.geode-sdk.org/)
* [Geode SDK Source Code](https://github.com/geode-sdk/geode/)
* [Geode CLI](https://github.com/geode-sdk/cli)
* [Bindings](https://github.com/geode-sdk/bindings/)
* [Dev Tools](https://github.com/geode-sdk/DevTools)
