---
title: auto-code-rover
date: 2024-04-12T12:15:40+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1711166827048-d7e103af0869?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTI4OTUyOTN8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1711166827048-d7e103af0869?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTI4OTUyOTN8&ixlib=rb-4.0.3
---

# [nus-apr/auto-code-rover](https://github.com/nus-apr/auto-code-rover)

# AutoCodeRover: Autonomous Program Improvement

![overall-workflow](https://github.com/nus-apr/auto-code-rover/assets/48704330/0b8da9ad-588c-4f7d-9c99-53f33d723d35)

<p align="center">
  <a href="https://arxiv.org/abs/2404.05427"><strong>ArXiv Paper</strong></a>
</p>

## 👋 Overview

AutoCodeRover is a fully automated approach for resolving GitHub issues (bug fixing and feature addition) where LLMs are combined with analysis and debugging capabilities to prioritize patch locations ultimately leading to a patch.

On [SWE-bench lite](https://www.swebench.com/lite.html), which consists of 300 real-world GitHub issues, AutoCodeRover resolves ~**22%** of issues, improving over the current state-of-the-art efficacy of AI software engineers.

<p align="center">
<img src=https://github.com/nus-apr/auto-code-rover/assets/48704330/28e26111-5f15-4ee4-acd1-fa6e2e6e0593 width=330/>
</p>

AutoCodeRover works in two stages:

- 🔎 Context retrieval: The LLM is provided with code search APIs to navigate the codebase and collect relevant context.
- 💊 Patch generation: The LLM tries to write a patch, based on retrieved context.

### ✨ Highlights

AutoCodeRover has two unique features:

- Code search APIs are *Program Structure Aware*. Instead of searching over files by plain string matching, AutoCodeRover searches for relevant code context (methods/classes) in the abstract syntax tree.
- When a test suite is available, AutoCodeRover can take advantage of test cases to achieve an even higher repair rate, by performing *statistical fault localization*.

## 🗎 arXiv Paper
### AutoCodeRover: Autonomous Program Improvement [[arXiv 2404.05427]](https://arxiv.org/abs/2404.05427)

<p align="center">
  <a href="https://arxiv.org/abs/2404.05427">
    <img src="https://github.com/nus-apr/auto-code-rover/assets/48704330/3d42a873-dd9f-41f3-ae09-eba477db2420" alt="First page of arXiv paper" width="570">
  </a>
</p>

For referring to our work, please cite and mention:
```
@misc{zhang2024autocoderover,
      title={AutoCodeRover: Autonomous Program Improvement},
      author={Yuntong Zhang and Haifeng Ruan and Zhiyu Fan and Abhik Roychoudhury},
      year={2024},
      eprint={2404.05427},
      archivePrefix={arXiv},
      primaryClass={cs.SE}
}
```

## ✔️ Example: Django Issue #32347

As an example, AutoCodeRover successfully fixed issue [#32347](https://code.djangoproject.com/ticket/32347) of Django. See the demo video for the full process:

https://github.com/nus-apr/auto-code-rover/assets/48704330/719c7a56-40b8-4f3d-a90e-0069e37baad3

### Enhancement: leveraging test cases

AutoCodeRover can resolve even more issues, if test cases are available. See an example in the video:

https://github.com/nus-apr/auto-code-rover/assets/48704330/26c9d5d4-04e0-4b98-be55-61c1d10a36e5

## 🚀 Setup & Running

We recommend running AutoCodeRover in a Docker container.
First of all, build and start the docker image:

```
docker build -f Dockerfile -t acr .
docker run -it acr
```

In the docker container, set the `OPENAI_KEY` env var to your [OpenAI key](https://help.openai.com/en/articles/4936850-where-do-i-find-my-openai-api-key):

```
export OPENAI_KEY=xx-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Set up one or more tasks in SWE-bench

In the docker container, we need to first set up the tasks to run in SWE-bench (e.g., `django__django-11133`). The list of all tasks can be found in [`conf/swe_lite_tasks.txt`](conf/swe_lite_tasks.txt).

The tasks need to be put in a file, one per line:

```
cd /opt/SWE-bench
echo django__django-11133 > tasks.txt
```

Then, set up these tasks by running:

```
cd /opt/SWE-bench
conda activate swe-bench
python harness/run_setup.py --log_dir logs --testbed testbed --result_dir setup_result --subset_file tasks.txt
```

Once the setup for this task is completed, the following two lines will be printed:

```
setup_map is saved to setup_result/setup_map.json
tasks_map is saved to setup_result/tasks_map.json
```

The `testbed` directory will now contain the cloned source code of the target project.
A conda environment will also be created for this task instance.

_If you want to set up multiple tasks together, put their ids in `tasks.txt` and follow the same steps._

### Run a single task

Before running the task (`django__django-11133` here), make sure it has been set up as mentioned [above](#set-up-one-or-more-tasks-in-swe-bench).

```
cd /opt/auto-code-rover
conda activate auto-code-rover
PYTHONPATH=. python app/main.py --enable-layered --model gpt-4-0125-preview --setup-map ../SWE-bench/setup_result/setup_map.json --tasks-map ../SWE-bench/setup_result/tasks_map.json --output-dir output --task django__django-11133
```

The output of the run can then be found in `output/`. For example, the patch generated for `django__django-11133` can be found at a location like this: `output/applicable_patch/django__django-11133_yyyy-MM-dd_HH-mm-ss/extracted_patch_1.diff` (the date-time field in the directory name will be different depending on when the experiment was run).

### Run multiple tasks

First, put the id's of all tasks to run in a file, one per line. Suppose this file is `tasks.txt`, the tasks can be run with

```
PYTHONPATH=. python app/main.py --enable-layered --model gpt-4-0125-preview --setup-map ../SWE-bench/setup_result/setup_map.json --tasks-map ../SWE-bench/setup_result/tasks_map.json --output-dir output --task-list-file tasks.txt
```

**NOTE**: make sure that the tasks in `tasks.txt` have all been set up in SWE-bench. See the steps [above](#set-up-one-or-more-tasks-in-swe-bench).

#### Using a config file

Alternatively, a config file can be used to specify all parameters and tasks to run. See `conf/vanilla-lite.conf` for an example.
Also see [EXPERIMENT.md](EXPERIMENT.md) for the details of the items in a conf file.
A config file can be used by:

```
python scripts/run.py conf/vanilla-lite.conf
```

## Experiment Replication

Please refer to [EXPERIMENT.md](EXPERIMENT.md) for information on experiment replication.

## ✉️ Contacts

For any queries, you are welcome to open an issue.

Alternatively, contact us at: {yuntong,hruan,zhiyufan}@comp.nus.edu.sg.

## Acknowledgements

This work was partially supported by a Singapore Ministry of Education (MoE) Tier 3 grant "Automated Program Repair", MOE-MOET32021-0001.
