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

![Agent Caterina Sforza](agent_caterina_arco)

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

![Portrait Caterina Sforza](portrait_caterina_arco)

## Triple n.1

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
<img src="/project/assets/img/triple1.jpg" alt="First Triple" style="max-width: 100%; height: auto; margin-bottom: 1em;">

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
