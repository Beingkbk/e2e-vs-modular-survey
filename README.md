# e2e-vs-modular-survey
## [Autonomous Driving Architecture Selection Framework](https://beingkbk.github.io/e2e-vs-modular-survey)

![Flowchart](framework_flowchart.png "framework flow")

The selection of an appropriate architecture for an autonomous driving system is rarely straightforward. A system designed for highway cruise control operates under fundamentally different constraints than an urban robotaxi, yet both are autonomous driving systems. To address this complexity, this paper introduces a Four-Dimensional Architecture Selection Framework (Figure 7), which provides a structured, repeatable method for selecting between Modular, End-to-End Imitation Learning, Reinforcement Learning, and Hybrid architectures based on the specific requirements of a given application.


The framework organises twelve decision criteria across four dimensions, each targeting a distinct aspect of system requirements. For each criterion, a practitioner answers a binary question yes or no and each answer generates a signal favouring one or more architecture paradigms. The architecture accumulating the highest signal count across all twelve criteria is recommended as the most suitable choice.


- Dimension 1: Safety and Regulatory Compliance is evaluated first because safety requirements are the hardest constraint in any real-world deployment. It asks three questions: whether full decision traceability is legally required (e.g., under ISO 26262 or UNECE WP.29), whether engineers must be able to isolate a failure to a specific component, and whether formal safety integrity certification such as ASIL-C or ASIL-D is mandated. If any of these apply, the framework signals strongly toward Modular or Hybrid architectures, since end-to-end systems by mapping inputs to outputs through a single opaque neural network cannot natively provide the module-level accountability that certification bodies require.


- Dimension 2: Operating Environment examines the nature of the deployment scenario. It asks whether the driving domain is highly structured (such as a motorway or a geofenced campus), whether rare or unexpected situations arise frequently, and how dense and unpredictable the surrounding traffic and pedestrian activity is. Structured, predictable environments suit Modular architectures because rule-based planning excels when the world behaves as expected. Unstructured, high-density environments where edge cases are common and agent behaviour is erratic favour End-to-End or Hybrid systems, which learn flexible representations from data rather than relying on pre-programmed rules.


- Dimension 3: Data and Computational Resources addresses the practical constraints on training and running the system. Three factors are assessed: whether a large, labelled training dataset exists for the target domain, whether a high-fidelity driving simulator is available for training, and how much onboard computing power is available at inference time. End-to-end imitation learning demands large-labelled datasets; reinforcement learning requires a capable simulator. Both approaches are computationally expensive at inference. If any of these resources are scarce, the framework signals toward Modular architectures, which can leverage pre-trained components and run efficiently on embedded hardware.


- Dimension 4: Deployment and Operational Context considers the lifecycle and team context of the project. It evaluates whether the system is a certified production deployment or a research prototype, whether individual components will need to be updated independently over time, and whether the engineering team has cross-functional expertise in both classical control and deep learning. Production systems with strict update processes benefit from modularity, since a single perception model can be swapped without revalidating the full pipeline. Hybrid architectures require expertise in both paradigms and are therefore better suited to teams that span both disciplines.


By working through these four dimensions sequentially, a practitioner arrives at a recommendation that reflects the real constraints of their application rather than a general preference for one paradigm. Importantly, no single architecture dominates across all criteria: Modular systems excel in safety-critical, resource-constrained deployments; End-to-End systems shine in data-rich, unstructured environments; Reinforcement Learning suits simulation-heavy research settings; and Hybrid systems offer the best balance when moderate interpretability and adaptability are both required. architecture choice has always been driven by application context rather than algorithmic superiority alone

