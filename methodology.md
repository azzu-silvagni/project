---
layout: default
title: Methodology
---

<div style="text-align: center; margin-bottom: 20px;">
  <a href="index.html">Home</a> |
  <a href="theproject">The Project</a> |
  <a href="theprocess.html">The Process</a> |
  <a href="conclusions.html">Conclusions</a>
</div>

# METHODOLOGY

This section outlines the approach and steps taken to investigate the **architectural heritage** of [**Romagna**](https://en.wikipedia.org/wiki/Romagna), focusing on **two fortresses** historically linked to [**Caterina Sforza**](https://en.wikipedia.org/wiki/Caterina_Sforza).

The project was carried out through a series of structured phases, combining **semantic technologies** and **historical research**.
Click on the highlighted sections below to explore each stage of the process in detail.

- [**ArCo**](#step-1-arco)

- [**SPARQL**](#step-2-sparql)

- [**Large Language Models**](#step-3-large-language-models)

- [**RDF Triples**](#step-4-rdf-triples)

- [**GitHub**](#step-5-github)

***

# Step 1: ArCo

## What is the ArCo Ontology?

The **ArCo Ontology** is a set of semantic vocabularies developed to describe and structure data related to Italian cultural heritage.
It is part of the broader **[ArCo](http://wit.istc.cnr.it/arco/) (Architecture of Knowledge)** project, promoted by the [Italian Ministry of Culture](https://cultura.gov.it/).

[ArCo](http://wit.istc.cnr.it/arco/) provides a formal model for representing cultural heritage objects, people, places, events, and their relationships — enabling **interoperability**, **linked open data**, and **semantic reasoning** within knowledge graphs.

## What is the ArCo SPARQL Editor?

The **[ArCo](http://wit.istc.cnr.it/arco/) [SPARQL Query Editor](https://dati.cultura.gov.it/sparql)** is an online tool that allows users to interact with the **[ArCo](http://wit.istc.cnr.it/arco/) Knowledge Graph**.
Through this editor, it is possible to write and run SPARQL queries to access, explore, and retrieve structured data from the dataset.

This querying process also enables the discovery of **semantic relationships** between different cultural heritage entities, as defined by the **[ArCo](http://wit.istc.cnr.it/arco/) ontologies**.

***

# Step 2: SPARQL

## What is SPARQL?

**SPARQL (SPARQL Protocol and RDF Query Language)** is a query language used to access and manipulate data stored in the **RDF (Resource Description Framework)** format.
It allows users to retrieve, filter, and explore structured data from knowledge graphs by writing specific query patterns.

<details>
  <summary><strong>SPARQL queries syntax:</strong> ⬇️</summary>

A typical SPARQL query can include the following components:

<ol>
    <li><strong>FILTER</strong>: Applies conditions to narrow down the results based on specific criteria.</li>
    <li><strong>LIMIT</strong>: Sets a maximum number of results to be returned.</li>
    <li><strong>OPTIONAL</strong>: Retrieves additional data if available, without excluding results when that data is missing.</li>
    <li><strong>ORDER BY</strong>: Arranges the results according to one or more selected variables.</li>
    <li><strong>PREFIX</strong>: Declares abbreviations for long URIs, making the query more readable and concise.</li>
    <li><strong>REGEX</strong>: Uses regular expressions to filter results based on pattern matching.</li>
    <li><strong>SELECT</strong>: Identifies the variables that should be included in the output.</li>
    <li><strong>UNION</strong>: Allows for the combination of multiple patterns, treating them as valid alternatives.</li>
    <li><strong>WHERE</strong>: Specifies the triple patterns to be matched against the RDF dataset.</li>
  </ol>

</details>

***

# Step 3: Large Language Models

Large Language Models (LLMs) are a type of [artificial intelligence](https://en.wikipedia.org/wiki/Artificial_intelligence) system built to process, generate, and understand human language. They are typically developed using **[deep learning](https://en.wikipedia.org/wiki/Deep_learning) methods** and trained on extensive [**text datasets**](https://en.wikipedia.org/wiki/Data_set).

As part of our project, the following large language models were used: 

| ChatGPT    | Gemini |
| ----------- | ----------- |
| [ChatGPT](https://chatgpt.com/) is an AI-powered conversational model created by [OpenAI](https://openai.com/), built on the GPT (Generative Pretrained Transformer) architecture. It’s designed to **interpret and produce human-like text**. Trained on a wide range of textual data, it can **engage in dialogue**, **create content**, and **support a variety of tasks**.      | [Gemini](https://gemini.google.com/?hl=en) is a collection of AI models developed by [Google DeepMind](https://deepmind.google/), aimed at combining the strengths of large language models with **advanced reasoning** and **problem-solving skills**. It leverages state-of-the-art techniques to improve the model's capacity to **generate nuanced, context-aware responses** across a wide range of topics.       |
| ![Logo ChatGPT](logo_chat1.png) | ![Logo Gemini](logo_gemini1.png) |

## Prompting Techniques

Prompting techniques are strategies used to steer AI models—especially language models—toward generating **specific and relevant outputs**. These methods play a key role in ensuring that the AI responds accurately and appropriately to given inputs.

<details>
  <summary><strong>Prompting techniques include:</strong> ⬇️</summary>

<ol>
    <li><strong>Zero-shot Prompting</strong>: Instructing the model to complete a task without providing any examples. This approach depends entirely on the model’s general training and prior knowledge.</li>
    <li><strong>Few-shot Prompting</strong>: Supplying a handful of examples or contextual cues to help the model understand the desired response style or structure.</li>
    <li><strong>Chain-of-thought Prompting</strong>: Encouraging the model to generate intermediate reasoning steps before producing a final answer.</li>
  </ol>

</details>

***

# Step 4: RDF Triples

## What is RDF?

**RDF (Resource Description Framework)** is a standard model for representing structured data on the Web.
It is used to describe resources — such as people, places, artworks, or historical events — and the relationships between them, in a way that is **machine-readable and semantically meaningful**.

RDF expresses data in the form of **triples**, which are the basic building blocks of a knowledge graph.

<details>
  <summary><strong>Structure of an RDF triple</strong> ⬇️</summary>

<p>Each RDF triple consists of three parts:</p>

<ol>
    <li><strong>Subject</strong>: the entity being described</li>
    <li><strong>Predicate</strong>: the property or relationship that connects the subject to something else.</li>
    <li><strong>Object</strong>: The value or target of the relationship. This can be either a literal (like a string or a date) or another resource.</li>
</ol>

</details>

***

# Step 5: GitHub

[GitHub](https://github.com/) is an online platform that enables **code management and collaboration** using the **[Git](https://git-scm.com/) version control system**. Developers can host their projects in repositories, manage changes over time, and collaborate through branching. Core features include pull requests for reviewing and merging code, issue tracking for handling tasks and bugs, and **GitHub Actions** for automating workflows like testing and deployment. The platform supports both public and private repositories.

![Logo GitHub](logo_github1.png)
