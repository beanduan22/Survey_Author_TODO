# Author TODO

Please do the three tasks below. Each row gives the paper title and a link. The meaning of every code is in [CODEBOOK.md](CODEBOOK.md).

## 1. Code a sample of papers (`1_recode_sample/`)

Read each paper and fill in the empty columns.

- `coding_sample.csv`: 70 rows. Fill in role, lifecycle_surface, interface, access, preservation_support, outcome_evidence, transfer, adaptive, utility.
- `qac_sample.csv`: 159 rows. Fill in QAC1–QAC10.

## 2. Check coded values (`2_full_checks/`)

Open each paper and check the values already filled in. In the last columns, write `ok` or `fix`, the correct value if wrong, your name, and the date.

- `critical_contributions_check.csv`: 60 rows. `locator` tells you where to look in the paper.
- `hand_system_form.tsv`, `hand_defense_origin.tsv`, `hand_operator_class.tsv`, `hand_exec_defense_stage.tsv`: 180 rows in total.

## 3. Check numbers (`3_number_checks/`)

- `numbers_to_verify.csv`: 60 claims. For each row, check that the numbers in `claim` match the linked paper. Write `ok` or `fix`, the correction if wrong, and where you found it (page, table, or section). A claim that cites several papers has one row per paper.

## What to send back

The same 8 files, filled in, with the same names:

- `coding_sample.csv`
- `qac_sample.csv`
- `critical_contributions_check.csv`
- `hand_system_form.tsv`
- `hand_defense_origin.tsv`
- `hand_operator_class.tsv`
- `hand_exec_defense_stage.tsv`
- `numbers_to_verify.csv`
