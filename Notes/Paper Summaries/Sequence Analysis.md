
### ABSTRACT
- Most existing methods cluster similar learning trajectories  and very few oﬀer metrics to characterize the learners’ temporal learning behavior.
- This study introduces sequence-based metrics: **sequence length, diversity, and complexity** to characterize students' temporal behavior dynamics
Key findings include:
1. The metrics effectively characterize individual students' learning dynamics.
2. Students who interacted with the LAD exhibited **more complex behavior** but did not show significant differences in final grades.
3. **Consistent engagement** (measured as regular activity) may be a stronger predictor of success than specific learning strategies.

### Introduction
- current SA methods often focus on general behaviors and transition frequencies, neglecting the temporal dynamics of learning, which are crucial for understanding how learning evolves over time.
- There is still a lack of measures that reflect changes in study behavior, which are essential for characterizing students' temporal dynamics.
- The paper aims to contribute to this gap by applying SA methods to analyze the impact of an intervention in a Blended Learning (BL) course. The intervention involves introducing a Learning Analytics Dashboard (LAD) to support Self-Regulated Learning (SRL). The study uses sequence indicators proposed by Ritschard to characterize students' temporal behavior and employs Inverse Probability Weighting (IPW) to assess causal relationships between dashboard adoption, student behavior, and final grades. The analysis controls for factors such as self-reported SRL proficiency, prior academic achievement (GPA), and pre-intervention behavior.
**The main aim of this study is to understand how sequential indicators can inform students’ behavior along the course, and to assess the impact of the intervention.**
##### Characterizing Nature of Sequences
- SA sequences: consecutive states (TREXetc)
	- "spells": succession of different states
		- For example, AAABCC is represented in spells as A/3-B/1-C/2, where A/3 indicates a spell of length 2 in A.
- Metrics to measure individual nature of sequences:
	- Basic indicators (counts of states/spells/transitions)
	- Diversity (the heterogeneity/distribution of visited states/spells in a sequence). For example, normalized entropy can be used to compare the diversity of sequences across different contexts.
	- Complexity (unpredictability of state/spell arrangement). 
- These are **state-agnostic**, focusing on the sequence’s dynamics rather than the specific actions involved. Consequently, sequences like ABAB and CDCD would yield the same indicators, despite having no states in common.
- Conceptual framework for analysis:
	- Passage of Time: Focuses on continuous streams of events, measured by metrics like position, duration, frequency, and rate.
	- Order in Time: Focuses on the temporal organization of events, requiring advanced techniques to analyze aspects like consistency, recurrent/non-recurrent change, and irregular change.
##### Sequence Analysis in Education
SA challenge: how to transform raw log data into meaningful sequences that capture learning behaviors?
1. **Defining Learning Actions**: Mapping interactions with a Learning Management System (LMS) to specific learning actions.
2. **Higher-Level Mapping**: Linking interactions to metacognitive actions associated with Self-Regulated Learning (SRL) strategies, such as planning, reviewing, or practicing.
3. **Multi-Step Approaches**: Creating session-based clusters and combining them to form comprehensive course-level sequences.
- SA methods have focused on **clustering similar behaviors** across learners using techniques like **Optimal Matching**, which measures the number of insertions, deletions, and substitutions needed to transform one sequence into another. While effective for grouping similar behaviors, this approach can obscure the **nuanced individual characteristics** of sequences, acting as a "black box" that hides the chronological richness of students' actions.

This study aims to contribute by:
1. Using **sequence indicators** (basic, diversity, and complexity) to profile learners based on **personal characteristics** like SRL proficiency and prior achievements.
2. Assessing the **effectiveness of an intervention** (a Learning Analytics Dashboard) aimed at supporting SRL strategies and influencing students' behavioral dynamics.
The study addresses two research questions:
- **RQ1**: How do sequence indicators complement existing approaches to profile learners based on personal characteristics?
- **RQ2**: How can sequence indicators inform the effectiveness of an intervention aimed at supporting SRL strategies?

### Methodology

#### Context
15 wk course DB management structured into three 5 wk periods:
- 1: Flipped classroom, students completed self evaluations
- 2: more independent/individual work; in class problem solving and at home exercises/instructional videos. Note: in this period, teacher introduced the NoteMyProgress (NMP) tool, a Learning Analytics Dashboard (LAD) to support student SRL 
- 3: hands-on group project
#### Data Sources
- (1) self-reported measures about students’ SRL proficiency - with MSLQ questionnaire
- (2) trace data generated from students’ interactions with the course: Moodle log files
- (3) metadata associated with the course: provided by teacher
#### Analytical Process
- Data preprocessing
	- 1st step: defining learning actions from trace data. 
	- Defining Learning Actions: defined from trace data, took advantage of weekly nature of course.
	- Clustering Weekly Behavior: Used a MHMM model...
- Indicators
	- Basic
		- no of non missing states in the sequences
		- proportion of transitions
	- Diversity





