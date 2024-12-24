# Static Workflow Engine for Multi-Agent AI Systems

## **Synopsis**
The Static Workflow Engine is a simplified version of a dynamic workflow system for coordinating tasks among multiple agents in a multi-agent AI system. This engine manages workflows with predefined task sequences and statically assigned agents. By limiting the scope to static workflows, the project focuses on implementing core event-driven functionality, making it accessible to undergraduate students.

This system uses preconfigured workflows defined in JSON files to handle task execution and state tracking. Agents execute tasks based on a fixed sequence, while an event-driven mechanism facilitates communication and task progress tracking.

---

## **Architecture**

### **Components**
1. **Workflow Manager**:
   - Reads predefined workflows from JSON files.
   - Initializes tasks and assigns agents based on static definitions.

2. **Event Manager**:
   - Manages task-related events (e.g., `task_started`, `task_completed`).
   - Tracks the state of tasks and triggers subsequent tasks based on the workflow.

3. **Task Tracker**:
   - Maintains the state of each task (e.g., Pending, In Progress, Completed).
   - Ensures workflows progress according to the predefined sequence.

4. **Agents**:
   - Perform specific tasks as defined in the workflow.
   - Communicate task status updates to the Event Manager.

---

## **JSON Schema**
Below is the JSON schema for defining workflows:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "workflowId": {
      "type": "string",
      "description": "Unique identifier for the workflow"
    },
    "workflowName": {
      "type": "string",
      "description": "Human-readable name of the workflow"
    },
    "tasks": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "taskId": {
            "type": "string",
            "description": "Unique identifier for the task"
          },
          "taskName": {
            "type": "string",
            "description": "Human-readable name of the task"
          },
          "assignedAgent": {
            "type": "string",
            "description": "Identifier of the agent assigned to this task"
          },
          "dependencies": {
            "type": "array",
            "items": {
              "type": "string",
              "description": "Task IDs that must be completed before this task"
            },
            "description": "List of task dependencies"
          }
        },
        "required": ["taskId", "taskName", "assignedAgent"]
      }
    }
  },
  "required": ["workflowId", "workflowName", "tasks"]
}
```

---

## **Example Workflows**

### Workflow 1: Document Summarization
```json
{
  "workflowId": "wf-001",
  "workflowName": "Document Summarization Workflow",
  "tasks": [
    {
      "taskId": "task-001",
      "taskName": "Extract Text from PDF",
      "assignedAgent": "agent-ocr",
      "dependencies": []
    },
    {
      "taskId": "task-002",
      "taskName": "Summarize Text",
      "assignedAgent": "agent-llm",
      "dependencies": ["task-001"]
    },
    {
      "taskId": "task-003",
      "taskName": "Generate Summary Report",
      "assignedAgent": "agent-report",
      "dependencies": ["task-002"]
    }
  ]
}
```

### Workflow 2: Customer Feedback Analysis
```json
{
  "workflowId": "wf-002",
  "workflowName": "Customer Feedback Analysis",
  "tasks": [
    {
      "taskId": "task-101",
      "taskName": "Fetch Customer Feedback",
      "assignedAgent": "agent-fetch",
      "dependencies": []
    },
    {
      "taskId": "task-102",
      "taskName": "Analyze Sentiment",
      "assignedAgent": "agent-llm",
      "dependencies": ["task-101"]
    },
    {
      "taskId": "task-103",
      "taskName": "Generate Insights Report",
      "assignedAgent": "agent-report",
      "dependencies": ["task-102"]
    }
  ]
}
```

---

## **Guidelines for Students**
1. **Understand the JSON Schema**:
   - Familiarize yourself with the structure of the workflow definition.
   - Experiment with creating simple workflows using the schema.

2. **Implement the Components**:
   - Start by building a basic Event Manager to handle task state changes.
   - Develop the Workflow Manager to read and execute workflows from JSON.

3. **Test with Example Workflows**:
   - Use the provided examples to validate your implementation.
   - Debug and refine your system based on task execution logs.

4. **Extend and Enhance**:
   - Once the static engine is functional, consider extending it with optional features like monitoring or basic error handling.

---

This document provides the foundation for building a Static Workflow Engine. By following the architecture and using the examples, students can create a functional system while gradually exploring more advanced concepts.
