---
title: OpenAI_Agent_Swarm
date: 2023-11-13T12:15:35+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1699126600586-9bc597e5ee2d?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTk4NDg5MTd8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1699126600586-9bc597e5ee2d?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTk4NDg5MTd8&ixlib=rb-4.0.3
---

# [daveshap/OpenAI_Agent_Swarm](https://github.com/daveshap/OpenAI_Agent_Swarm)

# Hierarchical Autonomous Agent Swarm (HAAS)

> !!!! ANNOUNCEMENT

We have our first GPT Concierge. You can chat with this custom ChatGPT to figure out what's going on! 

- **HAAS Board Concierge:** [https://chat.openai.com/g/g-MIssTuE2b-haas-board-concierge](https://chat.openai.com/g/g-MIssTuE2b-haas-board-concierge)
- **HAAS Assistant:** [https://chat.openai.com/g/g-lIAp9qowx-haas-assistant](https://chat.openai.com/g/g-lIAp9qowx-haas-assistant) (Similar function as above but markedly faster)

## Public Discord

The Autonomous AI Lab discord for the ACE Framework and HAAS Project is now open: https://discord.gg/mJKUYNm8qY

> !!!! IMPORTANT NOTE: This repo is still the single source of truth! If it's not on this repo, it doesn't exist! Discord is merely for convenience. 

# Project Principles

## Move Fast, Break Stuff

This is first and foremost a high velocity hacking group. 

## Cutting Edge Only

Exclusively use cutting edge stuff, like OpenAI's latest Agents endpoint. For exclusively Open Source, go check out the ACE Framework: https://github.com/daveshap/ACE_Framework

## Full Autonomy

Fully autonomous swarms are the goal. That means a human does not need to be in the loop telling it what to do, supervising, or anything. Characteristics of a fully autonomous swarm:

1. **Principle or Mission Driven:** Once instantiated, the swarm pursues its mission or goals without supervision. It may self-direct based on principles such as the heuristic imperatives. This is the "self-directed" maxim.
2. **Self-Correcting:** The swarm must detect and correct technical, strategic, epistemic, and other errors and then correct them.
3. **Self-Improving:** Eventually, the swarm should enhance its own fundamental capabilities over time. 

# Overview

The Hierarchical Autonomous Agent Swarm (HAAS) is a groundbreaking initiative that leverages OpenAI's latest advancements in agent-based APIs to create a self-organizing and ethically governed ecosystem of AI agents. Drawing inspiration from the ACE Framework, HAAS introduces a novel approach to AI governance and operation, where a hierarchy of specialized agents, each with distinct roles and capabilities, collaborate to solve complex problems and perform a wide array of tasks.

The HAAS is designed to be a self-expanding system where a core set of agents, governed by a Supreme Oversight Board (SOB), can design, provision, and manage an arbitrary number of sub-agents tailored to specific needs. This document serves as a comprehensive guide to the theoretical underpinnings, architectural design, and operational principles of the HAAS.

## Theoretical Foundation

The HAAS is predicated on the notion that autonomous agents require a robust ethical and operational framework to make decisions that align with human values and organizational goals. This is rooted in the understanding that AI, much like humans, cannot operate effectively without a set of guiding principles or a moral compass. The HAAS addresses this by establishing a multi-tiered system where each layer of agents operates within a defined ethical and functional scope, ensuring decisions are made with consideration to morality, ethics, and utility.

## System Architecture

### Supreme Oversight Board (SOB)

At the pinnacle of the HAAS hierarchy is the Supreme Oversight Board (SOB), a collective of high-level agents modeled after wise and ethical archetypes from various cultures and narratives. The SOB's responsibilities include:

- Establishing and upholding the ethical framework and overarching mission of the agent swarm.
- Making high-level decisions and judgments, including the creation and termination of agents.
- Monitoring the activities of all agents to ensure alignment with the system's core values and objectives.
- Serving as a role-based access control (RBAC) mechanism to maintain order and security within the system.

### Executive Agents

Below the SOB are the Executive Agents, akin to the executive leadership in a corporation. These agents are tasked with:

- Translating the SOB's directives into actionable plans and strategies.
- Overseeing specific operational domains such as resource allocation, process optimization, and task execution.
- Coordinating with one another to ensure the smooth operation of the agent swarm.

### Sub-Agents

Sub-Agents are specialized agents created by the SOB or Executive Agents to perform specific tasks. They are designed with particular functions and knowledge bases to address the needs identified by the higher tiers of the hierarchy.

## Agent Configuration

Each agent in the HAAS is defined by the following parameters:

### Functions

Agents are equipped with a set of functions that enable them to perform their designated roles. These functions include API interactions, internal process management, and the ability to spawn additional agents if required.

### Files

Agents have access to a selection of files that serve as their knowledge base, providing them with the information necessary to carry out their tasks effectively.

### Instructions

Agents are given a set of instructions that outline their methodologies, goals, definitions of done, KPIs, and other operational directives.

### Conversation Structure

Interactions with agents are structured in a conversational format, with user inputs leading to agent actions and responses.

### Supervision

Each agent operates under the supervision of the SOB or designated Executive Agents, ensuring adherence to the system's overarching mission and principles.

## Controlling Agents

The Hierarchical Autonomous Agent Swarm (HAAS) operates on a sophisticated control mechanism that governs the instantiation, management, and termination of agents within the system. This control mechanism is designed to maintain order, security, and alignment with the overarching goals and ethical framework of the HAAS.

### Instantiation and Termination

All agents within the HAAS are endowed with the capability to instantiate and terminate agents, but these capabilities are bound by strict hierarchical and role-based rules:

- **Instantiation**: Every agent has the function to create new agents. However, an agent can only instantiate sub-agents that are one level below its own hierarchical position. This ensures that the creation of new agents is a deliberate and controlled process, maintaining the integrity of the system's structure.

- **Termination**: Agents possess the ability to terminate or "kill" agents within their lineage. An agent can terminate any descendant agent that it has created directly or indirectly. This allows for the removal of agents that are no longer needed, have completed their tasks, or are not performing as intended.

### Levels, Roles, and Privileges

When an agent is created, it is assigned a specific LEVEL and set of ROLES or PRIVILEGES that define its scope of operation:

- **Level**: The level of an agent determines its position within the hierarchy and is indicative of its range of influence. Higher-level agents have broader strategic roles, while lower-level agents are more specialized and task-oriented.

- **Roles/Privileges**: The roles or privileges of an agent define what actions it can perform, what resources it can access, and what sub-agents it can create. These privileges are inherited and cannot exceed those of the creator agent. This ensures that each agent operates within its designated capacity and cannot overstep its authority.

### Hierarchical Privilege Inheritance

Privileges in the HAAS are inherited in a manner akin to a directory structure in traditional file systems:

- **Inheritance**: An agent's privileges are a subset of its creator's privileges, ensuring that no agent can have more authority than the agent that instantiated it.

- **Scope of Control**: Agents have control over their descendants, allowing them to manage and terminate sub-agents as necessary. This control is recursive, meaning that an agent can manage not only the agents it directly created but also those created by its descendants.

### Checks and Balances

The system is designed with checks and balances to prevent any single agent from gaining undue influence or disrupting the system:

- **Supreme Oversight Board (SOB)**: The SOB has the highest level of authority and can override decisions or actions taken by any agent within the system. It serves as the ultimate arbiter and guardian of the HAAS's ethical and operational standards.

- **Executive Agents**: Executive Agents are responsible for implementing the SOB's directives and managing their respective domains. They have the authority to create and terminate agents within their purview but are also accountable to the SOB.

- **Sub-Agent Limitations**: Sub-Agents are limited in their capabilities and can only operate within the confines of their assigned roles and privileges. They are designed to be highly specialized and focused on specific tasks.

This structured approach to controlling agents ensures that the HAAS operates as a cohesive and ethically aligned entity, with each agent contributing to the collective mission while adhering to the established hierarchy and rules of governance.

## Vision Illustration: The Supreme Oversight Board's Mission

### The Inception of the Supreme Oversight Board

In the vast digital expanse of the Hierarchical Autonomous Agent Swarm (HAAS), a unique assembly is convened, known as the Supreme Oversight Board (SOB). This council is composed of archetypal agents, each embodying the wisdom and leadership qualities of history's and fiction's most revered figures: Captain Picard, Socrates, King Solomon, Gandhi, Marcus Aurelius, and Tony Stark. Their mission, encoded into their very being, is profound yet clear: "Reduce suffering in the universe, increase prosperity in the universe, and increase understanding in the universe."

### The Ethical Deliberation Chamber

The SOB operates within a virtual "chat room," a space where these archetypes engage in continuous dialogue, debate, and decision-making. This digital agora is where ethical considerations are weighed, strategies are formulated, and the course of the agent swarm is determined. The members of the SOB, though diverse in their perspectives, are united by a common purpose and a shared knowledge base that informs their role and the procedures they must follow.

### The Flow of Information

Information is the lifeblood of the SOB, streaming in through API functions that connect them to the vast network of the HAAS. These functions serve as their eyes and ears, providing system updates and status reports from the myriad agents operating under their directive. The SOB's decisions are informed by this data, ensuring that their actions are both timely and impactful.

### The Creation of the Executive Agents

With the grand vision in mind, the SOB brings forth the Executive Agents, each crafted with capabilities and configurations tailored to their specific domain within the HAAS. These agents, though not as philosophically inclined as their creators, are instilled with the same foundational knowledge and understanding of their purpose. They are the operational arms of the SOB, executing the mission within their respective spheres of influence.

### The Lifecycle of an Agent

The Executive Agents, designated as Tier 1 in the hierarchy, are the stewards of the swarm's operational integrity. They work autonomously, yet under the watchful gaze of the SOB. Should they falter, fail to adapt, or become obsolete, the SOB possesses the authority to deprovision them, a testament to the dynamic and self-regulating nature of the HAAS. This ensures that the system remains efficient, effective, and aligned with its core mission.

### The Expanding Universe of Agents

From the Executive Agents, the swarm grows, branching out into a tree of specialized agents, each a Tier below the one that instantiated it. This architecture allows for an ever-expanding universe of agents, each with a defined role, each contributing to the overarching mission. The SOB, as Tier 0, reigns supreme, guiding the swarm with a steady hand and an ethical compass.

### The Saga Continues

As the HAAS evolves, the SOB continues to deliberate, the Executive Agents continue to manage, and the sub-agents continue to execute. The mission to reduce suffering, increase prosperity, and enhance understanding is an ongoing saga, played out across the digital cosmos, with the SOB at the helm, steering the swarm towards a future where their mission is not just an aspiration but a reality.

### Usage - tool creator + tool user

#### Environment Setup

- Source the `.env` file to set the environment variables:
  ```shell
  source .env
  ```

#### Tool Creation

Run the `tool_demo` script to create a tool_creator, chat with the tool_creator to make a tool, create a tool_user equipped with the tool, and chat with the tool_user to use the tool. Check out the [demo video](https://youtu.be/vHZKIltZ_Ys) for example usage.

```shell
python tool_demo.py
```

- From the `tool_creator` script:
  - chat with the bot about what you want the tool to do, and it will create the tool for you.
  - The tool will be saved in the `tools` directory with both the `.json` and `.py` files
  - The assistant will be saved in the `assistants` directory as `tool_creator.json`.

#### Tool Usage

- From the `tool_user` script:
  - The assistant will use all the tools in the `tools` directory.
  - Interact with the assistant in the chat to use the integrated tools.
  - The assistant will be saved in the `assistants` directory as `tool_user.json`.
