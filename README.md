# Bigg Ontology

The BIGG Ontology is an open-source initiative that establishes a standardised schema
for describing, characterising, and analysing buildings and urban areas. This ontology supports urban planning, building
management, and sustainable development by creating a shared vocabulary for researchers and practitioners. This common
language facilitates the sharing and integrating information within the urban development domain. The ontology also
includes a framework for defining measurements and key performance indicators (KPIs) to enable precise evaluation and
benchmarking of building and urban area performance. This repository documents the ongoing development of the ontology
and provides essential resources for its application.

## Key Components

The BIGG ontology is divided into 5 main components:

- **Systems**: Describe and analyze the various systems, sensors, devices, and weather stations within buildings and
  urban areas, including their functions, interconnections, and performance. This ensures efficient operation,
  maintenance, and integration of systems, leading to enhanced overall building performance and reliability.

- **Geospatial**: Capture and analyze spatial characteristics and geographic information of buildings and urban areas.
  This supports urban planning, optimal land use, site selection, and environmental impact assessments, thereby
  facilitating informed decision-making and efficient spatial management.

- **Measurements**: Catalogue and standardize the various devices and sensors used in buildings and urban areas for data
  collection and control. This includes meters, thermostats, smart appliances, and sensors measuring temperature,
  humidity, occupancy, and energy consumption. Standardizing these devices and sensors ensures accurate and consistent
  data capture across different environments, facilitating reliable monitoring, data collection, analysis, and informed
  decision-making.

- **Agents**: Identify and categorize the various stakeholders and entities involved in the lifecycle of buildings and
  urban areas. This promotes effective coordination, compliance with regulations, and collaboration among stakeholders,
  leading to more efficient and cohesive management of urban environments.

- **Temporal**: Address the timing of events, lifecycle phases of systems and components, and historical data related to
  buildings and urban areas. This enables time-based analysis and planning, prediction of future needs, scheduling of
  maintenance activities, and evaluation of long-term trends, ensuring proactive management and sustainability of urban
  assets.

![Ontology](resources/ontology.png)

This ontology is designed to represent the domain of buildings energy measurements. It provides a formal structure to
describe buildings, consumptions, weather, KPIs, and their relationships.

### Purpose and Objectives

- **Purpose**: Facilitate the organization and tracking of projects through a structured and formalized representation.
- **Objectives**: Establish a formal framework for describing and categorizing different aspects of buildings and urban
  areas. This will enhance our comprehension and management of urban elements, streamline building management, promote
  interoperability between systems, and lay the groundwork for creating data-driven analysis and visualization tools.
  Ultimately, this will simplify the analysis process and support the design of policies and strategies for sustainable
  urban development.

### Motivations

- **Complexity of Urban Environments**: The intricate nature of urban areas necessitates a comprehensive framework to
  manage
  and analyze various elements effectively.
- **Data Integration**: The need to integrate disparate data sources and systems to provide a cohesive understanding of
  urban environments.
- **Sustainability Goals**: The growing emphasis on sustainable development requires precise tools for planning and
  managing
  urban growth.
- **Technological Advancements**: Leveraging new technologies to improve data collection, analysis, and visualization.
- **Policy Development**: The demand for robust data-driven insights to inform urban policy and decision-making.

## Repository Structure

The repository is organized as follows:

- `ontology/`
    - `ontology.ttl`: Main ontology file in Turtle format.
- `extensions/`
    - `tariff.ttl`: Bigg ontology extension for Tariff in Turtle format.
    - `bigg4kpi.ttl`: Bigg ontology extension for energy kpi in Turtle format.
- `schema/`
    - `BiggOntology.drawio`: UML schema of the ontology.
- `resources/`: Contains images and additional files.
- `use_cases/`
    - `barcelona_use_case/`: Use case of the Bigg ontology with the city of Barcelona.
    - `montreal_use_case/`: Use case of the Bigg ontology with the city of Montreal.

## Edit/View

- Editing and viewing tools [Protegé](https://protege.stanford.edu/) & [Webvowl](https://service.tib.eu/webvowl/)
- Editing and viewing library [Owlready](https://owlready2.readthedocs.io/en/latest/)

## Use Cases

### Barcelona use case

A comprehensive initiative is underway in [Barcelona](use_cases/barcelona_use_case/README.md) to characterise the city's
Vulnerability Index. This index is
predicated on factors such as adaptation, exposure, and other critical elements determining the city's susceptibility to
various risks. Relevant datasets have been identified and harmonised according to a specific ontology to facilitate
this.

Key Performance Indicators (KPIs) are integral to characterising the Vulnerability Index. These KPIs are employed to
evaluate vulnerability at the building level under specific conditions. Nevertheless, there is a need to estimate these
KPIs in instances where actual or simulated values are unavailable. To address this, advanced data modelling techniques
are being utilised, leveraging the previously harmonised model as input. This approach allows the storage of KPIs for
the entire city following the ontology and their subsequent analysis and prediction.

The objective is to harmonize all building-level data according to the established ontology, enabling the accurate
computation of the Vulnerability Index. This approach aims to ensure a coherent and comprehensive assessment of
vulnerability, thereby enhancing Barcelona’s ability to manage and mitigate risks effectively.

### Montreal use case

In [Montreal](use_cases/montreal_use_case/README.md), a solution is being developed to predict consumption at the
Regional Territorial Area (RTA) level by
creating a datalake that integrates tabular time series (TS) data with cadastral vector data. This datalake harmonizes
consumption data and building characteristics according to the defined ontology, ensuring effective data linkage.

The primary challenge is the current need for more linkage between time series data and cadastral data, which limits
predictive accuracy. The proposed solution involves harmonizing these data types based on the established ontology,
facilitating their integration and correlation. This approach will enable more accurate predictive modelling and enhance
resource management in Montreal.

Our ultimate goal is to establish a coherent and accessible database that significantly improves Montreal's ability to
manage and forecast resource consumption based on specific territorial characteristics.

## Instalation

### Installation Steps

1. Clone this repository:
   ```bash
   git clone https://github.com/BeeGroup-cimne/biggontology.git

