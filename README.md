# LangChain-code

## Purpose

The repository is a learning/code-along project. Each file focuses on one concept so that the relationship between LangChain components can be understood clearly.

```text
langchain-code-along/
├── README.md                     # what this repo is, how to run it
├── requirements.txt
├── .env.example                  # HuggingFace or OPENAI_API_KEY=...
├── data/
│   ├── sample.pdf
├── 01_chain_types/
│   ├── 01_simple_chain.py
│   ├── 02_sequential_chain.py
│   ├── 03_parallel_chain.py
│   ├── 04_router_chain.py
│   ├── 05_transform_chain.py
├── 02_loaders_and_splitters/
│   └── pipeline.py
├── 03_retrieval_chain/
│   ├── ingest.py
│   └── rag.py
├── 04_memory/
│   ├── message_history.py
│   ├── conversational_rag.py
│   └── trimming_and_summary.py
├── 05_langchain_vs_raw/
│   ├── raw_openai.py
│   └── langchain_version.py
```

## Running Examples

Run the examples individually, for example:

```bash
python chains/01_basic_chain.py
```

The retrieval example requires the document-processing and vector-store setup first.

## Types of Chains:
## Simple chain (prompt → model → parser)

### What it is

The atomic unit. A prompt template feeds a model, whose output is parsed to a string.

### When to use

Any single-step task: rewriting, classification, Q&A, translation.

## Sequential chain (output of one step feeds the next)

### What it is

Multiple LLM calls in a row where each depends on the previous result.

### When to use

Multi-stage tasks: draft then critique then rewrite; summarise then translate; extract then format.

## Parallel chain (fan-out, then merge)

### What it is

Run several independent chains on the same input simultaneously and collect the results in a dict.

### When to use

Independent sub-tasks: pros and cons at once, multiple analyses of one document, or retrieving context and passing the question through

## Router / branching chain (conditional chain)

### What it is

A chain that first classifies the input, then sends it to a different sub-chain.

### When to use

Support triage, "math question vs. code question vs. general chat", choosing a specialised prompt per topic.

## Transform Chain

You can use RunnableLambda to transform the input

RunnableLambda: It lets you put your own Python function inside a LangChain pipeline.

## Some other chain types:

#### Structured-output (extraction) chain

#### What it is

A chain whose result is a typed Python object rather than free text, validated by a Pydantic schema.

#### When to use

Information extraction, form-filling, anything feeding a database or API.

#### Summarization chain (stuff, map-reduce, refine)

Long texts exceed the context window, so there are three classic strategies:
i. Stuff
ii. Map-Reduce
iii. Refine

### Overall Langchain concepts covered in the repo are:
- Code-along covering at least 5 chain types
- Connect a document loader and text splitter in a pipeline
- A retrieval chain built using LangChain and a vector store
- LangChain memory used to maintain conversation context
- Know when to use LangChain vs writing raw API calls

