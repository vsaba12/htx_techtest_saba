# htx_techtest_saba

# Tutor Assignment Optimisation (HTX Technical Assessment)

## Overview

This project implements an optimisation-based framework for assigning students to tutors under operational constraints.

The objective is to allocate new students to tutors while respecting:

- Skill compatibility (students requiring extensive tutoring are assigned to tutors who have extensive skills)
- Tutor capacity limits (respecting tutors' maximum capacities while noting their existing students)
- Tutor centre preferences (assigning to tutors' first or second choices as best as possible)

The model is implemented using **Mixed-Integer Programming (MIP)** with IBM CPLEX via the `docplex` Python library.

---

## Model Design

Each scenario shares the same feasibility constraints:

- Every student is assigned to exactly one tutor.
- Extensive tutoring requests are assigned only to tutors with extensive capability.
- A tutor’s total workload (existing + new students) does not exceed their maximum capacity.

The scenarios differ in their objective priorities.

---

## Scenarios

### Scenario (a): Minimises the number of tutors activated.

Objective:
- Prioritises reducing tutor count.
- Maximises tutor preference alignment as a secondary objective.

---

### Scenario (b): Minimises workload spread across tutors.

Objective:
- Reduces the difference between the most and least loaded tutors.
- Preference alignment remains secondary.

---

### Scenario (c): Combined objective that balances both efficiency and fairness.

Objective:
- Minimises tutors used.
- Minimises workload spread.
- Maximises preference satisfaction.

This produces a compromise solution reflecting mixed strategic priorities.

---

## Key Metrics

The following metrics are evaluated for each scenario:

- Tutors used
- Workload range (after assignment)
- Workload spread
- Preference satisfaction rate

---

## Output

The final results are exported to:

`HTX_Tutor_Assignment_Results.xlsx`

Containing six sheets:

- (a)_student_assignments
- (a)_tutors
- (b)_student_assignments
- (b)_tutors
- (c)_student_assignments
- (c)_tutors

---

## Technologies Used

- Python 3.x
- pandas
- docplex (IBM CPLEX)
- openpyxl (Excel export)

---

## Installation

Install dependencies using:

```bash
pip install -r requirements.txt
