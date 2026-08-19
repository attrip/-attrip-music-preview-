# ATTRIP Jazz — Faust/WASM Engine Experiment

## Goal

Replace only the sound engine first, without breaking the current instrument UI.

Current UI remains:

- A S D F G H J = jazz chords
- visible keyboard = exact sounding notes
- hold/release = instrument-like interaction
- Space = backing band

## Why Faust/WASM

Faust can compile DSP instruments to WebAssembly and run them as WebAudio nodes. A precompiled DSP module can be shipped without embedding the full Faust compiler, which is the route we want for a light GitHub Pages instrument.

## v0.9 experiment

1. Build a small polyphonic electric-piano DSP in Faust.
2. Compile it ahead of time to WebAssembly.
3. Load the precompiled WASM from the existing ATTRIP Jazz page.
4. Feed the existing rootless voicing MIDI notes into the Faust polyphonic node.
5. A/B test it against the current Web Audio FM engine.
6. Keep the current engine as fallback until the WASM version clearly wins on sound and CPU.

## Sound target

Not an acoustic grand piano. The first target is a light, expressive electric piano suitable for acid-jazz/funk:

- fast hammer/tine attack
- velocity-dependent bark
- controlled metallic tine component
- natural decay/release
- low CPU at 4–8 simultaneous voices
- rootless 7th/9th/13th voicings

## Architecture

```text
keyboard / chord pads
        ↓
ATTRIP chord + voice-leading engine
        ↓ MIDI note / velocity / gate
Faust polyphonic DSP (precompiled WASM)
        ↓
WebAudio node
        ↓
master / backing band
```

## Deployment rule

Do not compile Faust DSP in the visitor's browser for the production version. Precompile the DSP and publish only the runtime WASM + metadata needed by the page. This keeps load time and runtime overhead lower.

## Next implementation step

Create `electric-piano.dsp`, compile it with `faust2wasm ... -poly`, then add an A/B `ENGINE: WEB AUDIO / FAUST WASM` switch to the current preview.
