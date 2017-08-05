# Adding predictions to AFL

<pre>
                   american fuzzy lop 2.49b (magic_fuzzer)

┌─ process timing ─────────────────────────────────────┬─ overall results ─────┐
│        run time : 0 days, 0 hrs, 2 min, 29 sec       │  cycles done : 0      │
│   last new path : 0 days, 0 hrs, 0 min, 0 sec        │current paths : 533    │
│ prediction info : 297 / 32 / 197k                    │  1 min paths : 652    │
│ last uniq crash : none seen yet                      │  total paths : 1911   │
│  last uniq hang : none seen yet                      │  correctness : 2e-03  │
│ uniq crash/hang : 0 / 0                              │   difficulty : 5e-02  │
</pre>

* **current paths**: shows the current number of paths discovered.
* **1 min paths**: shows the number of paths discovered in the future (1min, 10min, 1hour, 10hrs, and 1d). However, the prediction does not anticipate sudden increases in the number of paths discovered. It expects the path discovery to decelerate at the same speed (approaching an asymptote). The prediction quickly adjusts once the sudden increase has happened.
* **total paths**: shows the number of *asymptotic* total number of paths discovered. In the beginning when many paths are discovered the estimates are positively biased (over-estimate). Later, when an asymptote is discernable the estimate becomes slightly negatively biased. However, the magnitude of the bias reduces the longer the fuzzing campaign.
* **prediction info**: shows the number of paths exercised exactly once / exactly twice / #inputs. All estimates and predictions are computed from these numbers.
* **correctness**: shows an upper bound on the probability to expose a unique crash if no crashes have been found. The number is fairly representative of fuzzing campaigns of similar length, assuming AFL is started with the same seeds, parameters, and test driver. Pythia provides *statistical correctness guarantees* for fuzzing campaigns!.
* **difficulty**: shows how "difficult" it is to discover new paths in that program. Difficulty is a program property where programs with difficulty 0 are extremely difficult to fuzz while programs with difficulty 1 are extremely easy to fuzz.

If there is enough interest, I'll put up a technical report explaining the research behind this.
Cheers - Marcel
