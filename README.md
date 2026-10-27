# SE/CprE 4210: Learning Sprint #3 — Problem 5

## Complexity & Side Channels — Interactive Security Lab

A browser-based educational visualization for **SE/CprE 4210: Learning Sprint #3 — Problem 5**, based on Module 5 (*Algorithmic Complexity & Side Channel Attacks*, Ahmed Tamrawi, Iowa State University).

## Run the app

Open `index.html` in a modern browser (Chrome, Firefox, or Edge). No installation, build, dependencies, account, API keys, or network connection are required.

Alternatively, serve the directory with `python -m http.server 8000` and open `http://localhost:8000/`.

## Lessons and interactions

1. **Hash-collision DoS:** Use the key-count slider and input-pattern dropdown to compare distributed keys with adversarial collisions in a resizing linked-list model (load factor at most 0.75). The visualization updates buckets, comparison counts, longest chains, and modeled comparison growth. Based on Module 5 slides 9–16.
2. **ReDoS:** Change the number of `a` characters and whether the input ends with an unexpected `!`. Compare possible exponential group partitions against linear input length for a pattern similar to `^(a+)+$`. Based on Module 5 slides 27–36.
3. **Timing side channel:** Switch between early-return and equalized login pathways; adjust the maximum added network delay and simulate 20 timing samples per category. Compare known-user and unknown-user means. Based on Module 5 slides 50–60 and 68–70.

Every lesson also includes a short concept question with immediate feedback.

## Educational scope and safety

- All values are **illustrative simulations**, not measured performance from real services.
- The regex demonstration uses arithmetic only: it **never executes** a catastrophic-backtracking regex.
- No real authentication attempts, packet collection, requests to remote servers, or exploit payloads occur.
- Input values are intentionally bounded; the site works offline and uses no external packages or trackers.
- The spread case deliberately uses distinct buckets; the collision case forces all distinct keys into one bucket. We count key equality comparisons, not wall-clock time. Hash-table behavior depends on runtime implementation. Modern Java hash maps can treeify long collision chains under specified conditions; this demo illustrates the older/simple linked-list approach explained in class.
- The partition count `2^(n-1)` is the number of ways to split `n` repeated characters into nonempty contiguous groups. It is **not an exact regex-engine instruction count** and does not imply that successful matches explore all possible partitions.
- Timing samples add a nonnegative delay between zero and the selected maximum to the modeled processing time. All 20 sample pairs are displayed; changing settings clears previous results. Repeating the same settings reproduces the same samples.
- The deterministic timing simulation is a simplified model and **not a guarantee** of constant-time behavior in production.

## Project structure

```text
complexity-security-lab/
├── index.html     # Complete HTML, CSS, and JavaScript app
├── README.md      # Setup, explanation, limitations
└── reflection.md  # One-page reflection draft to review and personalize
```

## Testing checklist

- Open `index.html` without internet access.
- Switch among all three lesson tabs.
- Move both sliders to their minimum and maximum values.
- Verify that hash comparison counts increase sharply in collision mode.
- Verify that ReDoS partition counts double each time `n` increases by one.
- Run timing samples in both modes at 0 and 45 ms maximum added delay; verify that all times are nonnegative and all 20 sample pairs appear.
- Change timing settings after a run and confirm that old results clear. Check that Reset restores the initial settings.
- Test each quiz answer and confirm immediate feedback.
- Check usability on a narrow/mobile browser window.

## AI-assisted workflow

Used ChatGPT to plan educational interactions, draft a standalone app and documentation, and reason about safe mathematical simulations. The student should review the implementation, manually test it in the browser, revise the reflection to match actual experience, and commit the final files.

## Course source

Ahmed Tamrawi, *CprE/SE 4210 — Module 5: Algorithmic Complexity & Side Channel Attacks*, class lecture slides supplied for the assignment.
