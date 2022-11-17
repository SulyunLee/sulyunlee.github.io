---
title: "Dynamic Healthcare Embeddings for Improving Patient Care"
collection: publications
date: 2022-11-16
venue: 'IEEE/ACM Advances in Social Networks Analysis and Mining (ASONAM)'
permalink: /publication/ASONAM_2022_publication
---
Hankyu Jang, **Sulyun Lee**, D. M. Hasibul Hasan, Philip M. Polgreen, Sriram V. Pemmaraju and Bijaya Adhikari

**Abstract**:<br>
As hospitals move towards automating and integrating their computing systems, more fine-grained hospital operations data are becoming available.
These data include hospital architectural drawings, logs of interactions between patients and healthcare professionals, prescription data, procedures data, and data on patient admission, discharge, and transfers.
This has opened up many fascinating avenues for healthcare-related prediction tasks for improving patient care. 
However, in order to leverage off-the-shelf machine learning software for these tasks, one needs to learn structured representations of entities involved from heterogeneous, dynamic data streams.
Here, we propose DECENT, an auto-encoding heterogeneous co-evolving dynamic neural network, for learning heterogeneous dynamic embeddings of patients, doctors, rooms, and medications from diverse data streams.
These embeddings capture similarities among doctors, rooms, patients, and medications based on static attributes and dynamic interactions.

DECENT enables several applications in healthcare prediction, such as predicting mortality risk and case severity of patients, adverse events (e.g., transfer back into an intensive care unit), and future healthcare-associated infections.
The results of using the learned patient embeddings in predictive modeling show that DECENT has a gain of up to 48.1% on the mortality risk prediction task,
12.6% on the case severity prediction task,
6.4% on the medical intensive care unit transfer task, 
and 3.8% on the Clostridioides difficile (C.diff) Infection (CDI) prediction task
over the state-of-the-art baselines.
In addition, case studies on the learned doctor, medication, and room embeddings show that our approach learns meaningful and interpretable embeddings.


**Paper link**: [PDF]([http://sulyunlee.github.io/files/no_copyright_ASONAM22_dynamic_healthcare_embeddings_for_improving_patient_care.pdf])

**Recommended citation**: <br>
Hankyu Jang, Sulyun Lee, D. M. Hasibul Hasan, Philip M. Polgreen, Sriram V. Pemmaraju and Bijaya Adhikari. Dynamic Healthcare Embeddings for Improving Patient Care. In Proceedings of the 2022 IEEE/ACM International Conference on Advances in Social Networks Analysis and Mining (ASONAM 2022).
