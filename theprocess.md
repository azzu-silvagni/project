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

==The result was TRUE==, confirming the presence of the individual in the KG.
We then performed a **second SELECT query** to retrieve her unique IRI:

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap;">
PREFIX arco: &lt;https://w3id.org/arco/ontology/arco/&gt;<br>
PREFIX rdfs: &lt;http://www.w3.org/2000/01/rdf-schema#&gt;<br><br>
SELECT ?s<br>
WHERE {<br>
  ?s rdfs:label "Caterina Sforza" .<br>
}
</div>

The result consisted in the retrieval of the following **agent entity**: https://w3id.org/arco/resource/Agent/cf402e9bbd5dd8372a35022c85259530

![Agent Caterina Sforza](agent_caterina_arco)

## Depiction of Caterina Sforza

Although Caterina Sforza exists in the ArCo knowledge graph as an Agent, she is not directly associated with any visual depiction.
To address this gap, we executed a **SPARQL SELECT query** to search for visual properties that could be linked to her, such as portraits:

<div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 10px; margin: 1em 0; font-family: monospace; white-space: pre-wrap;">
PREFIX arco: &lt;https://w3id.org/arco/ontology/arco/&gt;<br>
PREFIX a-cd: &lt;https://w3id.org/arco/ontology/context-description/&gt;<br>
PREFIX agent: &lt;https://w3id.org/arco/resource/Agent/&gt;<br>
PREFIX rdfs: &lt;http://www.w3.org/2000/01/rdf-schema#&gt;<br><br>
SELECT DISTINCT ?cp<br>
WHERE {<br>
&nbsp;&nbsp;?cp a arco:HistoricOrArtisticProperty ;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;rdfs:label ?l .<br>
&nbsp;&nbsp;FILTER(REGEX(?l, "Ritratto di Caterina Sforza", "i"))<br>
}
</div>

The query returned the following **cultural properties**: 

https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900231485

https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900644122

https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900281635-21

https://w3id.org/arco/resource/HistoricOrArtisticProperty/0900479412

Among these four properties, we chose the third one as it was the only coloured painting.
