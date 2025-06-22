---
layout: default
title: The Process
---

<div style="text-align: center; margin-bottom: 20px;">
  <a href="index.html">Home</a> |
  <a href="theproject">The Project</a> |
  <a href="methodology.html">Methodology</a> |
  <a href="theprocess.html">The Process</a> |
  <a href="conclusions.html">Conclusions</a>
</div>

# THE PROCESS

This section outlines all the specific steps taken to investigate the **architectural heritage** of **Romagna**, focusing on the **Rocca di Ravaldino** and the **Rocca di Imola**, historically linked to **Caterina Sforza**.

Click on the highlighted sections below to explore each step of the process in detail.

- [**Identifying the Topic**](#identifying-the-topic)

- [**Depiction of Caterina Sforza**](#depiction-of-caterina-sforza)

- [**Exploring the Fortresses**](#exploring-the-fortresses)

- [**Ordering the Fortresses**](#ordering-the-fortresses)

- [**Checking for Links to Caterina Sforza**](#checking-for-links-to-caterina-sforza)

- [**Checking for other Missing Information**](#checking-for-other-missing-information)

- [**Use of LLMs**](#use-of-llms)

## Identifying the Topic

The project began by verifying the existence of Caterina Sforza within the ArCo knowledge graph. To do this, we executed a **first SPARQL ASK** query to check whether the resource was present:

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap;">
PREFIX arco: &lt;https://w3id.org/arco/ontology/arco/&gt;
PREFIX rdfs: &lt;http://www.w3.org/2000/01/rdf-schema#&gt;

ASK
WHERE {
  ?person rdfs:label "Caterina Sforza".
}
</div>

<mark>The result was TRUE</mark>, confirming the presence of the individual in the KG.
We then performed a **second SELECT query** to retrieve her unique IRI:

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap;">
PREFIX arco: &lt;https://w3id.org/arco/ontology/arco/&gt;
PREFIX rdfs: &lt;http://www.w3.org/2000/01/rdf-schema#&gt;<br>
SELECT ?s
WHERE {
  ?s rdfs:label "Caterina Sforza" .
}
</div>

The result consisted in the retrieval of the following **agent entity**: <https://w3id.org/arco/resource/Agent/cf402e9bbd5dd8372a35022c85259530>

![Agent Caterina Sforza](agent_caterina.png)

## Depiction of Caterina Sforza

Although Caterina Sforza exists in the ArCo knowledge graph as an Agent, she is not directly associated with any visual depiction.
To address this gap, we executed a **SPARQL SELECT query** to search for visual properties that could be linked to her, such as portraits:

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap;">
PREFIX arco: &lt;https://w3id.org/arco/ontology/arco/&gt;
PREFIX a-cd: &lt;https://w3id.org/arco/ontology/context-description/&gt;
PREFIX agent: &lt;https://w3id.org/arco/resource/Agent/&gt;
PREFIX rdfs: &lt;http://www.w3.org/2000/01/rdf-schema#&gt;<br>
SELECT DISTINCT ?cp
WHERE {
&nbsp;&nbsp;?cp a arco:HistoricOrArtisticProperty ;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;rdfs:label ?l .
&nbsp;&nbsp;FILTER(REGEX(?l, "Ritratto di Caterina Sforza", "i"))
}
</div>

The query returned the following **cultural properties**: 

- <https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900231485> 

- <https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900644122>

- <https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900281635-21>

- <https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900479412>

Among the four properties, we selected <mark>the third one</mark>, as it was the only one featuring a colour painting.

![Portrait Caterina Sforza](ritratto_caterina.png)

## First Triple

From this, an image was identified and associated with Caterina using a **CONSTRUCT query**, which allows the creation of new RDF triples to enrich the graph.

<!-- QUERY BOX - con wrapping migliorato -->
<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
PREFIX foaf: &lt;http://xmlns.com/foaf/0.1/&gt;

CONSTRUCT {
  &lt;https://w3id.org/arco/resource/Agent/cf402e9bbd5dd8372a35022c85259530&gt;
  foaf:depiction
  &lt;https://www.sigecweb.beniculturali.it/images/fullsize/ICCD50007125/ICCD5194406_16411.jpg&gt; .
}
WHERE {
  FILTER(REGEX("Caterina Sforza", "Caterina Sforza", "i"))
}
</div>

<!-- Immagine -->
<img src="first_triple.png" alt="First Triple" style="max-width: 100%; height: auto; margin-bottom: 1em;">

<!-- Tabella con colonne strette e avvolgimento testo -->
<table style="table-layout: fixed; width: 100%; word-wrap: break-word;">
  <thead>
    <tr>
      <th>Subject</th>
      <th>Predicate</th>
      <th>Object</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Caterina Sforza</td>
      <td>foaf:depiction</td>
      <td>Ritratto di Caterina Sforza</td>
    </tr>
    <tr>
      <td><code>&lt;https://w3id.org/arco/resource/Agent/cf402e9bbd5dd8372a35022c85259530&gt;</code></td>
      <td><code>&lt;http://xmlns.com/foaf/0.1/&gt;</code></td>
      <td><code>&lt;https://www.sigecweb.beniculturali.it/images/fullsize/ICCD50007125/ICCD5194406_16411.jpg&gt;</code></td>
    </tr>
  </tbody>
</table>

## Exploring the Fortresses

To identify the types of architectural heritage present in the ArCo Knowledge Graph, we first executed a **SPARQL query** aimed at listing all distinct **types of architectural assets**.

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
SELECT DISTINCT ?type  
WHERE {  
  ?cp a arco:ArchitecturalOrLandscapeHeritage ;  
      dc:type ?type .  
}
</div>

We then refined our search by listing only the resources of this type containing the word **"rocca"** in their label:

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?s ?label
WHERE {
  ?s rdfs:label ?label .
  FILTER(REGEX(?label, "rocca", "i"))
</div>

This helped us identify two resources relevant to our topic:

**Rocca di Imola** ⤵️ <https://w3id.org/arco/resource/ArchitecturalOrLandscapeHeritage/0800242914>

**Rocca di Ravaldino** ⤵️ <http://dati.beniculturali.it/iccd/schede/resource/CulturalInstituteOrSite/S006699_Rocca_di_Ravaldino>

We selected these as our core case studies, due to their **historical connection** to Caterina Sforza.

## Ordering the Fortresses 

To ensure a more structured presentation of the selected heritage sites, we applied the **ORDER BY clause** to **alphabetically** sort the two fortresses by their label.
This improves the clarity of the results and demonstrates our ability to control not only what we query from the knowledge graph, but also how we present it.

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?rocca ?label
WHERE {
  VALUES ?rocca {
    <https://w3id.org/arco/resource/ArchitecturalOrLandscapeHeritage/0800242914>
    <http://dati.beniculturali.it/iccd/schede/resource/CulturalInstituteOrSite/S006699_Rocca_di_Ravaldino>
  }
  ?rocca rdfs:label ?label .
}
ORDER BY ?label
</div>

ORDER BY allows us to alphabetically sort the fortresses — useful for future scaling (e.g., if we add more sites), and for implementing clean navigation on the GitHub website.

## Checking for Links to Caterina Sforza

To verify whether Caterina Sforza was already linked to the two fortresses in the ArCo Knowledge Graph, we used an **ASK query**.

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
PREFIX arco: <https://w3id.org/arco/ontology/arco/>

ASK {
  {
    <https://w3id.org/arco/resource/Agent/cf402e9bbd5dd8372a35022c85259530> arco:isConnectedTo <https://w3id.org/arco/resource/ArchitecturalOrLandscapeHeritage/0800242914>
  }
  UNION
  {
    <https://w3id.org/arco/resource/Agent/cf402e9bbd5dd8372a35022c85259530> arco:isConnectedTo <http://dati.beniculturali.it/iccd/schede/resource/CulturalInstituteOrSite/S006699_Rocca_di_Ravaldino>
  }
}
</div>

The result was false. This result justifies the **creation of new RDF triples**, using both **LLM-generated content** and **SPARQL CONSTRUCT** to enrich the knowledge graph with new semantic relations.

## Checking for other Missing Information

We ran a series of **SPARQL ASK queries** to verify whether the two fortresses were already associated with certain semantic properties in the ArCo Knowledge Graph.
This helped us detect gaps in the data and justify the use of LLMs and new RDF triples to enrich the graph.

- **Temporal designation**

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
PREFIX arco: <https://w3id.org/arco/ontology/arco/>

ASK {
  {
    <https://w3id.org/arco/resource/ArchitecturalOrLandscapeHeritage/0800242914>
    arco:hasDesignationInTime ?date .
  }
  UNION
  {
    <http://dati.beniculturali.it/iccd/schede/resource/CulturalInstituteOrSite/S006699_Rocca_di_Ravaldino>
    arco:hasDesignationInTime ?date .
  }
</div>

- **Committent**

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>

ASK {
  {
    <https://w3id.org/arco/resource/ArchitecturalOrLandscapeHeritage/0800242914> 
    a-cd:hasCommittent ?committent .
  }
  UNION
  {
    <http://dati.beniculturali.it/iccd/schede/resource/CulturalInstituteOrSite/S006699_Rocca_di_Ravaldino> 
    a-cd:hasCommittent ?committent .
  }
</div>

- **Cultural Events**

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap; overflow-wrap: anywhere;">
PREFIX arco: <https://w3id.org/arco/ontology/arco/>

ASK {
  {
    <https://w3id.org/arco/resource/ArchitecturalOrLandscapeHeritage/0800242914> 
    arco:hasCulturalEvent|arco:hasSituationInTime ?event .
  }
  UNION
  {
    <http://dati.beniculturali.it/iccd/schede/resource/CulturalInstituteOrSite/S006699_Rocca_di_Ravaldino> 
    arco:hasCulturalEvent|arco:hasSituationInTime ?event .
  }
}
</div>

As already stated before, all the results were <mark>false</mark>.

## Use of LLMs

### Designation in time

As concerns the designation in time, we submitted the following prompts to both Gemini and ChatGPT, the two LLMs selected for our project. 

> When was the Fortress of Ravaldino built?

> When was the Fortress of Imola built?

With the aim of obtaining the most accurate and reliable information possible, we cross-checked the construction dates of the two fortresses using the following **online sources**:

**Rocca di Ravaldino** ➡️ <https://turismoforlivese.it/it/arte-cultura/rocca-di-ravaldino/> 

**Rocca di Imola** ➡️ <https://imolamusei.it/rocca-sforzesca/> 

After consulting these sources, we found that Gemini was accurate regarding the Fortress of Ravaldino, whereas ChatGPT provided incorrect information. In the case of the Fortress of Imola, Gemini was again correct, while ChatGPT, although not entirely inaccurate, offered a less precise response.
