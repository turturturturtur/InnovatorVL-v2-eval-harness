# InnovatorVL-v2 — Eval Harness

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Base framework](https://img.shields.io/badge/base-LMMs--Eval%200.7.2-blue)](https://github.com/EvolvingLMMs-Lab/lmms-eval)
[![Release](https://img.shields.io/badge/release-v2.0.0-green)](../../releases)

**This repository is the evaluation harness behind every InnovatorVL-v2 benchmark
number.** It is published so the results below can be inspected, re-run and audited
end to end. Model weights and the model card live at
[`InnovatorLab/InnovatorVL-v2`](https://huggingface.co/InnovatorLab/InnovatorVL-v2)
on Hugging Face.

▶ **[Watch the 28-second promo video](https://huggingface.co/InnovatorLab/InnovatorVL-v2/resolve/main/InnovatorVL-v2-Main-Promo-v7-28s.mp4)** (hosted on Hugging Face)

**InnovatorVL-v2 is a dense 9B-parameter multimodal model that delivers
state-of-the-art scientific visual understanding at its scale, without giving up
general multimodal ability.** Built on Qwen3.5-9B-Base, it is trained through a
pipeline centred on systematic data governance — recursive self-improvement for
data scoring and filtering, rank-based mixture optimisation, failure-guided data
synthesis, and Visual Evidence-Calibrated Reinforcement Learning (VEC-RL).

Evaluated on 22 benchmarks with thinking disabled for every compared model,
InnovatorVL-v2 attains **the highest average in all three categories**:

| Category | **InnovatorVL-v2 (Ours)** | Margin over strongest baseline |
| --- | :---: | :---: |
| General (12 benchmarks) | **80.18** | +3.32 |
| Science (8 benchmarks) | **59.71** | **+12.46** |
| Spatial (2 benchmarks) | **61.56** | +1.17 |

Headline results:

- **First on 18 of the 22 benchmarks** among the models displayed, and
  **beats Qwen3.5-9B on 21 of the 22** — the single exception is SimpleVQA.
- **Scientific understanding is the standout gain**: +17.70 points over
  Qwen3.5-9B on the Science average.
- **MolParse 75.40** and **OpenRxn 56.50** — ahead of the best compared baseline
  by **+56.35** and **+40.85** points respectively. Molecular structure parsing
  and reaction understanding are near-solved relative to the field.
- **Best general score on 11 of the 12 general benchmarks**, including
  DocVQA 96.76, V\*Bench 90.58, ChartQA 89.24, AI2D 88.34,
  OCRBench 88.20 and InfographicVQA 87.69.
- **Highest Spatial average**, with EmbSpatial-Bench 77.36 and ERQA 45.75.

## Performance

![Performance overview across 22 benchmarks](https://huggingface.co/InnovatorLab/InnovatorVL-v2/resolve/main/main_result.png)

**Performance overview across 22 benchmarks.** Blue bars indicate our model; the
remaining bars show the compared models available in each panel. Our model ranks
first on 18 of the 22 benchmarks among the models displayed and outperforms
Qwen3.5-9B on 21 of the 22. The signed value in the upper-right corner of each
panel is the score-point difference against Qwen3.5-9B. All results use our
local evaluation setting with thinking disabled. Higher scores are better;
vertical scales vary across panels.

![Category-level performance](https://huggingface.co/InnovatorLab/InnovatorVL-v2/resolve/main/general_ability.png)

**Category-level performance with thinking disabled.** Panels (a), (b) and (c)
report unweighted averages over 12 general, eight scientific and two spatial
benchmarks respectively. All seven models have complete coverage. Blue bars
denote InnovatorVL-v2 (Ours); the remaining bars are the six baselines, including
Qwen3.5-9B-Base. Models appear in the same order across panels, sorted by their
General scores. All panels use the same 0–100 scale.

### Full results

Local non-thinking evaluation across all 22 benchmarks. Bold marks the best score
in each row, including ties.

| Benchmark | **InnovatorVL-v2 (Ours)** | Qwen3-VL-8B | Gemma4-12B-IT | InternVL3.5-8B | Step3-VL-10B | Qwen3.5-9B | Qwen3.5-9B-Base |
| --- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| *General* | | | | | | | |
| AI2D | **88.34** | 83.74 | 77.49 | 82.22 | 83.55 | 85.46 | 63.28 |
| ChartQA | **89.24** | 85.24 | 52.12 | 87.20 | 59.68 | 85.28 | 61.04 |
| InfographicVQA (val) | **87.69** | 83.72 | 53.86 | 74.23 | 71.27 | 83.34 | 76.70 |
| DocVQA (val) | **96.76** | 93.66 | 83.10 | 92.37 | 92.33 | 94.98 | 92.60 |
| MMBench (EN dev) | **87.97** | 83.67 | 81.62 | 83.51 | 85.47 | 85.48 | 86.34 |
| MME-RealWorld | **71.33** | 63.29 | 35.02 | 62.66 | 30.32 | 60.08 | 46.79 |
| MMStar | **73.15** | 59.94 | 67.11 | 66.38 | 63.24 | 70.52 | 71.92 |
| OCRBench | **88.20** | 87.00 | 77.80 | 83.20 | 85.30 | 83.10 | 86.30 |
| RealWorldQA | **76.73** | 68.76 | 65.23 | 63.53 | 63.66 | 74.51 | 72.81 |
| SEED-Bench-2-Plus | **72.38** | 71.28 | 68.25 | 70.58 | 69.35 | 70.84 | 64.08 |
| V\*Bench | **90.58** | 84.82 | 52.36 | 70.68 | 67.02 | 84.29 | 82.20 |
| SimpleVQA | 39.80 | 39.31 | 40.27 | 35.47 | **46.24** | 44.40 | 45.73 |
| *Science* | | | | | | | |
| EMVista | **49.62** | 44.27 | 39.30 | 46.81 | 43.03 | 43.35 | 37.84 |
| ScienceQA | 93.89 | 91.91 | 89.39 | **95.94** | 85.76 | 93.35 | 89.53 |
| MolParse | **75.40** | 4.35 | 4.95 | 19.05 | 4.25 | 7.00 | 5.20 |
| OpenRxn | **56.50** | 9.25 | 12.60 | 14.05 | 12.70 | 14.40 | 15.65 |
| RxnBench (EN) | **89.05** | 82.75 | 85.31 | 80.46 | 73.70 | 88.52 | 87.67 |
| SmolInstruct_v2 | 27.08 | 20.15 | 24.18 | **40.27** | 6.87 | 14.38 | 27.44 |
| ProteinLMBench | 61.97 | 59.32 | 56.67 | 61.76 | 56.25 | 54.77 | **65.89** |
| SFE (EN) | 24.13 | **28.98** | 22.41 | 19.63 | 14.44 | 20.24 | 20.12 |
| *Spatial* | | | | | | | |
| EmbSpatial-Bench | **77.36** | 74.90 | 73.54 | 73.24 | 68.10 | 75.77 | 75.00 |
| ERQA | **45.75** | 38.80 | 42.25 | 41.25 | 24.00 | 45.00 | **45.75** |

## Usage

This section is about running **the harness**. For loading the model itself, see
[Model inference](#model-inference) below.

### 1. Install

```bash
git clone https://github.com/turturturturtur/InnovatorVL-v2-eval-harness.git
cd InnovatorVL-v2-eval-harness
python3 -m pip install -e '.[all]'
```

Extras are declared in `pyproject.toml` (`core`, `server`, `tui`, `video`, `audio`,
`metrics`, ...). The web console needs `.[tui]`, which `all` already includes.
Upstream installation options, including `uv`, are in
[`README.upstream.md`](README.upstream.md).

### 2. Configure

Three JSON files drive everything; templates live in `run_scripts/`:

| File | Purpose |
| --- | --- |
| `config_eval.json` | model path/HF id, tensor parallelism, tasks, generation kwargs, output path, `limit` |
| `config_judge.json` | judge backend (`api` or `vllm`), judge model, parallelism |
| `config_dlc.json` | cluster submission only: workers, GPU/CPU/memory, image, mounts, DLC ids |

Keys are read with `jq`; every placeholder listed in
[Placeholders you must fill in](#placeholders-you-must-fill-in) has to be replaced
with your own values before a cluster submission will pass validation.
`run_scripts/QUICKSTART.md` (Chinese) walks through each field.

### 3. Run on a single node

```bash
# MODEL TASKS OUTPUT [LIMIT] [THINKING]
bash run_scripts/qwen35_local_eval.sh \
  Qwen/Qwen3-VL-8B-Instruct \
  ai2d,chartqa,ocrbench \
  /path/to/eval_result \
  -1 off
```

`THINKING` is `on` or `off` and defaults to `off` — **every number in the tables
above was produced with thinking disabled**, for our model and for all baselines.
`LIMIT` must stay `-1` for reported results; anything smaller is a debug setting
and is not comparable to the paper.

Or call the framework directly:

```bash
python3 -m lmms_eval --tasks list          # discover task ids
python3 -m lmms_eval --model vllm \
  --model_args pretrained=Qwen/Qwen3-VL-8B-Instruct,tensor_parallel_size=1 \
  --tasks ai2d,chartqa --limit -1 --output_path /path/to/eval_result
```

### 4. Run on a cluster (Alibaba Cloud PAI-DLC)

```bash
DRY_RUN=1 bash run_scripts/qwen35_submit.sh \
  run_scripts/config_dlc.json run_scripts/config_eval.json run_scripts/config_judge.json
```

`DRY_RUN=1` prints the exact submission command without sending it. Dropping
`DRY_RUN` submits for real. Both submitters run
`lmms_eval/storage_policy.py` first, which rejects runs pointing at the wrong
mounts or caches, and `lmms_eval/runtime_preflight.py` verifies the interpreter,
vLLM/PyTorch/CUDA/Transformers versions and the model files before the job is
accepted. `run_scripts/qwen3_vl_submit.sh` is the Qwen3-VL variant.

### 5. Judge

Generation and judging are separate stages; the judge is constructed only after
evaluation finishes.

```bash
bash run_judge.sh config_judge.json
```

`backend: vllm` starts a local judge (see `tools/start_vllm_judge.sh`);
`backend: api` uses any OpenAI-compatible endpoint. Credentials come from
`JUDGE_API_KEY` / `JUDGE_BASE_URL` (or `OPENAI_API_KEY` / `OPENAI_API_BASE`) —
never from a committed file. `task_judge_table.md` lists which tasks need a judge.

### 6. Web console

```bash
uv run uvicorn lmms_eval.tui.server:app --host 0.0.0.0 --port 8000
```

Submit runs, stream worker logs, filter saved samples, pick metrics, browse
historical results and author task YAML/`utils.py` from the browser. See
`lmms_eval/tui/README.md`.

### 7. Task ids for the reported benchmarks

| Benchmark | task id | Benchmark | task id |
| --- | --- | --- | --- |
| AI2D | `ai2d` | EMVista | `EMVista` |
| ChartQA | `chartqa` | ScienceQA | `scienceqa` |
| InfographicVQA (val) | `infovqa_val` | MolParse | `MolParse` |
| DocVQA (val) | `docvqa_val` | OpenRxn | `OpenRxn` |
| MMBench (EN dev) | `mmbench_en_dev` | RxnBench (EN) | not in this snapshot — see note |
| MME-RealWorld | `mmerealworld` | SmolInstruct_v2 | `SmolInstruct_v2` (task group) |
| MMStar | `mmstar` | ProteinLMBench | `ProteinLMBench` |
| OCRBench | `ocrbench` | SFE (EN) | `sfe-en` |
| RealWorldQA | `realworldqa` | EmbSpatial-Bench | `embspatial` |
| SEED-Bench-2-Plus | `seedbench_2_plus` | ERQA | `erqa` |
| V\*Bench | `vstar_bench` | SimpleVQA | `simplevqa` (needs judge) |

> **Note on RxnBench (EN).** The score is reported above, but this public snapshot
> contains no `RxnBench` task configuration — only `OpenRxn`. The remaining 21
> benchmarks are fully reproducible from this repository.

A one-command reproduction of all 21:

```bash
TASKS=ai2d,chartqa,infovqa_val,docvqa_val,mmbench_en_dev,mmerealworld,mmstar,ocrbench,realworldqa,seedbench_2_plus,vstar_bench,simplevqa,EMVista,scienceqa,MolParse,OpenRxn,SmolInstruct_v2,ProteinLMBench,sfe-en,embspatial,erqa
bash run_scripts/qwen35_local_eval.sh InnovatorLab/InnovatorVL-v2 "$TASKS" /path/to/eval_result -1 off
bash run_judge.sh config_judge.json      # simplevqa needs the judge stage
```

### Model inference

Verified with `transformers` 5.3.0. All 760 tensors in `model.safetensors` map
cleanly onto the model (no missing or unexpected keys).

```python
import torch
from transformers import AutoModelForImageTextToText, AutoProcessor

path = "InnovatorLab/InnovatorVL-v2"
processor = AutoProcessor.from_pretrained(path)          # Qwen3VLProcessor
model = AutoModelForImageTextToText.from_pretrained(     # Qwen3_5ForConditionalGeneration
    path, dtype=torch.bfloat16, device_map="auto"
)
```

The text stack uses hybrid attention with `linear_attention` layers. Without
[`flash-linear-attention`](https://github.com/fla-org/flash-linear-attention) and
[`causal-conv1d`](https://github.com/Dao-AILab/causal-conv1d) installed,
`transformers` logs *"The fast path is not available"* and falls back to a slower
pure-PyTorch implementation. Results are unaffected, but throughput is lower —
install both for production inference.

## What this harness adds on top of LMMs-Eval

This is a fork of [LMMs-Eval](https://github.com/EvolvingLMMs-Lab/lmms-eval)
(MIT). The upstream framework is kept intact; on top of it:

- **LLM-as-a-judge pipeline** — `lmms_eval/llm_judge/` (23 files): pluggable judge
  providers (OpenAI-compatible API, local vLLM, Bedrock), retry/backoff hardening,
  and deferred judge construction so judging starts only after generation completes.
- **Web console** — `lmms_eval/tui/` and `lmms_eval/tasks/tui/` (46 files): FastAPI
  backend plus a React front end for submission, log streaming, sample filtering,
  metric selection, history browsing and in-browser task authoring.
- **Cluster submission** — `run_scripts/` (17 files): single-node and PAI-DLC entry
  points, matching worker scripts, shared `eval_common.sh`, and `dlc_create_job.py`
  which submits through the native DLC `CreateJob` API.
- **Storage and runtime contract** — `lmms_eval/storage_policy.py`,
  `lmms_eval/runtime_preflight.py`: reject runs pointing at wrong mounts or caches and
  verify the runtime before a cluster job is accepted.
- **Operations tooling** — `tools/` (15 files): batch watchdog, runtime snapshot
  creator, worker resource monitor, sample re-aggregation, video-decode backend
  benchmarking, task input capture.
- **Correctness fixes** in the evaluation path: per-request sampling parameters
  preserved for the vLLM, OpenAI-chat and SGLang backends (previously built once per
  batch); task-native stop policy respected instead of a global default; OCRBench
  full-width/ASCII normalization; owner-aligned MicroVQA protocol; saved-sample
  scoring corrected and invalid aggregations made to fail loudly; benchmark cache
  handling on shared network storage.
- **Regression tests** — `test/` (128 files) covering judge retry, runtime preflight,
  storage policy, WebUI flows and submitter argument templates.

Additional benchmark task configurations (science, code, video and safety suites) come
from upstream LMMs-Eval mainline and from the fork this harness is derived from; they
are not claimed as our work.

## Placeholders you must fill in

Internal infrastructure identifiers and absolute mount paths were replaced with
shell-safe placeholders so this repository can be public. Evaluation logic is
unchanged.

| Placeholder | Meaning |
| --- | --- |
| `evaluser` | OS/cluster user name appearing in mount paths |
| `/mnt/clusterfsA`, `/mnt/clusterfsB`, `/mnt/clusterfs` | primary / secondary / legacy parallel-FS mount roots |
| `/mnt/sharednasA`, `/mnt/sharednasB` | primary / secondary NAS mount roots |
| `innovator` | internal project directory name in example paths |
| `000000` | PAI-DLC workspace id |
| `quota0000000000000` | PAI-DLC resource (quota) id |
| `cpfs-placeholder`, `cpfs-placeholder-vpc-suffix`, `ap-placeholder0000` | parallel-FS instance, mount target, access point |
| `nas-placeholder.cn-wulanchabu.nas.aliyuncs.com` | NAS mount target |
| `vpc-placeholder000000000`, `vsw-placeholder000000000`, `sg-placeholder0000000000` | VPC, vSwitch, security group |
| `192.0.2.0/24`, `198.51.100.0/24`, `203.0.113.0/24`, `192.0.2.128/25`, `198.51.100.128/25` | extended CIDRs (RFC 5737 documentation ranges) |
| `registry.example.com` | container image registry |
| `judge.internal.example.com`, `127.0.0.1:8000` | judge / API serving endpoints |
| `0000000000000000`, `evaluser-role` | cloud account id and RAM role in the DLC role ARN |
| `example-served-model` | default served-model name for API-mode evaluation |

The internal run manifests and per-job audit evidence (`local/`) are deliberately not
part of this public release. Credentials were never committed: judge and API keys are
read from `OPENAI_API_KEY` / `JUDGE_API_KEY` / `JUDGE_BASE_URL` or injected at
submission time.

Note that `storage_policy.py` *enforces* the mount roots and the quota/workspace ids
above. Replace the placeholders consistently — the policy, the submitter scripts, the
JSON templates and the tests all read the same literals, so a partial replacement will
fail validation by design.

## Tests

```bash
pytest test -m "not gpu and not api and not slow"
```

Expected on a fresh clone: **1007 passed, 6 failed, 8 skipped**. The six failures are
pre-existing in our internal tree as well and are unrelated to the harness changes above:

- `test/eval/test_judge_import_contract.py::test_generation_task_import_does_not_construct_judge_clients`
- `test/eval/test_new_benchmarks_tasks.py::TestNewBenchmarkTaskConfigSources::test_fullset_dataset_paths` (countix dataset path)
- `test/eval/test_scivqr_official.py::TestSciVQROfficialAdapters::test_openai_provider_omits_officially_unspecified_fields`
- `test/llm_judge/test_integration.py::TestEndToEnd::test_judge_file_with_mock_task`
- `test/llm_judge/test_integration.py::TestCLIIntegration::test_cli_with_mock_files`
- `test/tui/test_webui_auth.py::test_defaults_match_qwen35_feishu_benchmarks_exactly` (task ordering)

`test/tools/test_qwen35_local_eval_shell.py` additionally requires a prepared
`.venv/bin/python` inside the checkout. `test/eval/qwen2_5_vl/` and
`test/eval/test_ocrbench_v2.py` need GPU fixtures and the `jieba` package.

## Provenance

The full development history is included, so the harness can be dated and audited:

```bash
git log --format='%h %ad %an %s' --date=short   # 1923 commits, 2023-12-24 → 2026-11-12
```

History was rewritten for this public release, in every commit rather than only at the
tip: the internal `local/` run manifests were dropped and the identifiers listed above
were replaced. Commit SHAs therefore differ from our internal tree; commit content and
dates do not. One portability fix is included so the submitter works in a checkout that
is not named `lmms-eval` (`run_scripts/qwen3_vl_submit.sh` now derives its root from its
own location, matching `qwen35_submit.sh`).

At the point where this snapshot was cut (2026-11-11, compared against upstream
`main` at `c26b6b2`), the harness was based on LMMs-Eval `0.7.2`-era mainline, 152
commits behind upstream `main`, and carried 103 commits that have not been sent
upstream.

## Citation

```bibtex
@misc{innovatorvl2-eval-harness,
  title        = {InnovatorVL-v2 Eval Harness},
  author       = {{InnovatorVL-v2 Team}},
  year         = {2026},
  howpublished = {\url{https://github.com/turturturturtur/InnovatorVL-v2-eval-harness}},
  note         = {Version v2.0.0. Evaluation harness for the InnovatorVL-v2 report,
                  derived from LMMs-Eval (MIT License)}
}
```

<!-- TODO(paper): add the arXiv id / DOI of the InnovatorVL-v2 report here and in CITATION.cff. -->

LMMs-Eval itself should be cited as described in [`CITATION.cff`](CITATION.cff) and
[`README.upstream.md`](README.upstream.md).

## License

MIT. Copyright for the upstream framework belongs to LMMs-Lab and the
lm-evaluation-harness authors; see [`LICENSE`](LICENSE). Our additions are released
under the same license. The license of the **model weights** is stated separately on
the [Hugging Face model card](https://huggingface.co/InnovatorLab/InnovatorVL-v2).
