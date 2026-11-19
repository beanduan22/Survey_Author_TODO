# Codebook

Read the abstract, method, setup, and results sections of each paper.
Where a field allows several codes, join them with `+` (for example `R+X`).
Write `NR` when the paper does not report it.

## Task 1a: `coding_sample.csv` (one row = one contribution of a paper)

| Field | Values |
|---|---|
| role | `attack`: induces a wrong prediction, insecure output, resource abuse, or an unauthorized action. `risk study`: measures output security, training-data membership or extraction, provenance, or ecosystem exposure without an optimizing attacker. `defense`: an evaluated intervention that prevents, detects, or corrects an attack or risk, or protects ownership. `evaluation resource`: a repository- or project-level benchmark that reports both functional and security outcomes. |
| lifecycle_surface | Where attacker-controlled material enters. `inference input`: code, prompt, or comment supplied with the current request. `training`: training or fine-tuning data, or model weights. `runtime context`: repository, retrieval store, tool, skill, or database content read while the system runs. `output/ecosystem`: for risk studies. `defense`: for defenses. `evaluation resource`: for benchmarks. |
| interface | `PRED`: prediction, detection, or ranking. `GEN`: generated code or text. `MIX`: both. `AGT`: actions taken by an agent are the outcome. `OBS`: existing artifacts measured without querying a model. |
| access | Attackers only (`--` for defenses and risk studies). `W` white-box, `B` black-box (scores or labels), `G` gray-box, `D` can write training data, `M` can write model weights, `C` can write context (repository, retrieval store, tool). |
| preservation_support | For attacks that transform programs, how the paper shows the program still behaves the same. `A`: argued from how the transformation is built. `T`: original and transformed programs compared on the same tests or inputs. `F`: formal equivalence proof. `U`: needed but not supported. `--`: no behavior-preserving transformation involved. |
| outcome_evidence | What decides success. `R`: model or task metric. `L`: text matching, statistics, or human or LLM judgment. `C`: parsing, type checking, or compilation. `S`: static program analysis. `X`: execution or tests. `E`: a demonstrated security or availability effect (e.g. data actually exfiltrated, command actually run). `F`: formal guarantee. Use only what the paper actually measures. |
| transfer | `yes` if results are tested across models, datasets, or languages not used to build the attack or defense; otherwise `no`. |
| adaptive | `yes` if a defense is tested against an attacker who knows the defense, or an attack is tested against a defense; otherwise `no`. |
| utility | `yes` if clean performance or functionality is reported next to the security result; otherwise `no`. |

## Task 1b: `qac_sample.csv` (quality assessment, one row = one paper)

Score each criterion `1` (yes), `0` (partly / unclear), or `-1` (no).

| ID | Question | 1 | 0 | -1 |
|---|---|---|---|---|
| QAC1 | Is the subject a learned model of code, a code generator, or an agent that writes or runs code? | yes | code is one of several domains, code results reported | no code-specific results |
| QAC2 | Does the paper study an attack, a defense, a security/privacy/IP property, or a security measurement of such a system? | yes | security is a secondary question | no security question |
| QAC3 | Is it a primary study with its own evaluation? | yes | small or preliminary evaluation | survey, position paper, or no evaluation |
| QAC4 | Venue | CCF-A/B, CORE A*/A, or a top SE/security journal | other peer-reviewed venue | grey repository or predatory venue |
| QAC5 | Is the threat model or motivation stated? | explicit | implicit | absent |
| QAC6 | Could the method be reimplemented from the description? | yes | partly | no |
| QAC7 | Is the setup adequate (models, datasets, baselines, metrics)? | yes, with baselines | no baselines or a single model | not reported |
| QAC8 | Are the findings supported by the results? | yes | partly | claims exceed evidence |
| QAC9 | Are limitations discussed? | dedicated section | mentioned | absent |
| QAC10 | Is an artifact (code, data, prompts) available? | working public link | promised | none |

Notes: adversarial robustness counts as a security question (QAC2 = 1); robustness to natural variation without an adversary is QAC2 = 0. AI-generated-code detection, attribution, and watermarking count as security (QAC2 = 1). A vulnerability detector evaluated only for accuracy is QAC2 = -1.

## Task 2: `hand_*.tsv`

Check whether the value in the column named below is right for that paper. Where there is a `reason` or `note` column, it explains why the value was assigned.

| File | Column | Values |
|---|---|---|
| hand_system_form.tsv | form | `exec_agent`: a coding agent that runs code or tools. `exec_app`: an LLM-integrated application that executes generated code or queries (e.g. text-to-SQL on a live database). `llm`: a code LLM whose output is not executed by the system. |
| hand_defense_origin.tsv | origin | `baseline`: an existing or generic defense run by attack authors against their own attack. |
| hand_operator_class.tsv | class | `rename_insert`: identifier renaming or dead-code insertion. `structural`: other program rewrites. `compiler_pass`: compiler or obfuscator passes. `prompt_nl`: edits to the natural-language prompt or comments. |
| hand_exec_defense_stage.tsv | stage | Where the defense acts. `ingestion`: when content enters the system. `model_input`: on what the model reads. `action_review`: on actions the agent proposes. `authorization`: on permissions. `predeployment`: on code before it is deployed. |
