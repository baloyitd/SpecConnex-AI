## 1. Mega Prompt

You are an expert AI software architect. Your goal is to design a robust, end-to-end Python pipeline to perform a semantic comparison between a Business Requirements Document (BRD) in .docx format and a complex Figma design file. The system must identify which requirements are present in the design and which are missing.

Design the architecture based on the following critical principles and constraints:

Modular, Verifiable Pipeline: The entire pipeline must be a series of standalone, single-responsibility Python scripts. Each script must perform one distinct task and save its output as a verifiable intermediate JSON file before the next script runs. Do not design a single monolithic script.

Figma API Strategy: Address the Figma API's response size limitations. The design must use a multi-stage fetching strategy: first, a shallow call to get top-level frame IDs, 
followed by deep, looped calls for each frame's content. The extractor must capture the text, its full hierarchical path, and the node_id of both the text element and its parent frame.

Data Sanitization: Include a dedicated sanitize_figma_data.py script. Its purpose is to filter the raw Figma text extract to remove designer metadata and other non-user-facing "noise." 
It should use configurable, pattern-based rules (e.g., for style tokens like "Body Base Light", placeholder signatures, and path redundancy) rather than relying on a large, hardcoded list.

Contextual String Transformation: After sanitization, include a dedicated build_figma_context_strings.py script. This script's sole responsibility is to 
transform the clean Figma data {"path": "...", "text": "..."} into a context-rich string format f"{path} {text}" that is optimized for SBERT embedding.

Hierarchical BRD Parsing: The BRD parser (verify_brd_hierarchy.py) must understand the document's structure. It must explicitly extract and isolate a top-level product_concept 
(from the document's title or first heading) and then parse the remaining requirements into a parent-child hierarchy.

BRD Topic Structuring: Include a verify_brd_topic_structure.py script that takes the hierarchical requirements, clusters them into semantic topics using an algorithm like HDBSCAN, and 
filters out non-functional "definitional" topics (e.g., glossary terms).

Two-Stage Contextual Matching: The final matching engine (run_final_matcher.py) must implement a two-stage process:

A "Gatekeeper" Stage: It first compares the BRD's product_concept against all top-level Figma frame names to identify a small list of "relevant frames."

A "Matchmaker" Stage: It then compares the functional BRD topics only against the text found within those pre-filtered relevant frames.

Your first task is to provide the following:

A high-level diagram or list showing the sequence of scripts in the pipeline.

For each script, state its single responsibility, its primary input file(s), and its primary output file.

Define the JSON "data contract" (the key-value structure) for each intermediate output file.

Finally, provide the complete, production-ready Python code for the first script in the pipeline.






### 1.1 Application Acrhitecture  

You are an expert AI Software architect. based on the attached chat trails and
retro insights and feedback.
Your goal is to provide me with comprehensive, clear prompts that will
provide clear context to build the application architecture, to eliminate back and forth.
The application will have three main components:
Data Management, The User Interface (UI), and Reporting.
Design the architecture based on the following critical principles and constraints:
Embedded Figma Previews,
offine figma image workfow i.e.
zero dependence on the live Figma API. It will only read local files.
This makes it faster, more reliable, and capable of running on a machine that might be temporarily offline.
Local first architecture,

your is to provide the following:

comprehensice sequence of prompts for the application architecure, for the main components.
this must incorporate context engineering principles. i.e just the right information for the next step.

Key Considerations:

This is a collaborative design, that is interactive.

Matching results can be across multiple frames.

in future, a frame can have multiple cards, and each card corresponds to the a product.
Cater for this variation in the UI.

it must be possible to set the thresholds for the semantic matching.

please add any other considerations that will enhance the user experien



## 2. PRD + UI Brief (Decouple) - Rewrite Prompt
Provide a comprehensive PRD, for the concept below. This must be clear and comprehensive. No Code. The PRD will should include comprehensive structure for a systems design document, 
to granular details like a snr UI design would. to include the proposal the following: emotional vibe, modular cards, padding, layout behaviour, 
typography best suited for this application. 
Call out any specific feature that will enhance the user experience to make it more engaging and interactive. 
Precisely specify the colours, font sizes and any specific things related to UI designs.


