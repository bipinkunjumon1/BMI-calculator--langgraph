```markdown
# BMI Calculator using LangGraph

A Python-based Body Mass Index (BMI) calculator built using LangGraph. This project demonstrates how to structure a simple computational workflow as a stateful graph, transitioning from data input to calculation and classification.

## Project Overview

This project utilizes langgraph to create a directed graph that:

1. Initializes State: Accepts weight (kg) and height (m).

2. Calculates BMI: Executes a node to compute the BMI value.

3. Categorizes Result: Passes the state to a second node to determine the health category (Underweight, Normal, Overweight, or Obese).

4. Visualizes Workflow: Generates a Mermaid diagram of the internal logic.

## Features

* State Management: Uses TypedDict to maintain a consistent state across nodes.

* Modular Logic: Separate nodes for calculation and labeling.

* Graph Visualization: Includes code to render the graph structure using Mermaid.

## Technical Stack

* Language: Python

* Orchestration: LangGraph

* Data Handling: typing.TypedDict

## Installation

1. Clone the repository:

   ```
   git clone https://github.com/your-username/bmi-langgraph.git
   cd bmi-langgraph
   ```

2. Install dependencies:

   ```
   pip install langgraph
   ```

## How It Works

### The State

The BMIstate keeps track of the weight, height, BMI, and the final category:

```python
class BMIstate(TypedDict, total=False):
    weight_kg: float
    height_m: float
    bmi: float
    category: str
```

### The Graph Logic

The workflow follows a linear path:

* START → calculate_bmi → bmi_label → END

## Usage

Run the script to see the output for a sample input:

```python
initial_state = {'weight_kg': 80, 'height_m': 1.75}
final_state = workflow.invoke(initial_state)
print(final_state)
# Output: {'weight_kg': 80, 'height_m': 1.75, 'bmi': 26.12, 'category': 'overweight'}
```

## Visualization

The project includes a utility to display the graph structure:

```python
from IPython.display import Image
Image(workflow.get_graph().draw_mermaid_png())
```
```
