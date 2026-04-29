# API Preview

This document describes the planned API style for CodeElement Engine. The production API is not publicly available yet. The examples below are interface previews for trial planning and developer communication.

## Base Concept

The trial API is designed to receive scene input and task information, then return structured scene expression, decision code, or task-planning results.

## Planned Endpoints

### 1. Scene Understanding

```http
POST /v1/scene/understand
```

Purpose:

- Accept image, point cloud, or structured task metadata.
- Return SceneCode and object-level scene information.

Possible input:

```json
{
  "scene_id": "demo_lab_arm_001",
  "input_type": "rgbd",
  "task": "pick the red block and place it on the tray"
}
```

Possible output:

```json
{
  "scene_id": "demo_lab_arm_001",
  "scene_code": "Scene(objects=[Object(id='red_block', type='cube')], goal='place_on_tray')",
  "confidence": 0.91
}
```

### 2. Decision Generation

```http
POST /v1/decision/generate
```

Purpose:

- Convert SceneCode and task goal into a task-level decision plan.
- Return ordered actions and execution constraints.

Possible output:

```json
{
  "plan_id": "plan_001",
  "actions": [
    {"step": 1, "verb": "detect", "target": "red_block"},
    {"step": 2, "verb": "grasp", "target": "red_block"},
    {"step": 3, "verb": "place", "target": "tray"}
  ],
  "status": "preview"
}
```

### 3. Workflow Feedback

```http
POST /v1/workflow/feedback
```

Purpose:

- Record task execution result.
- Mark success, failure, abnormal states, and reusable trajectory information.

Possible feedback:

```json
{
  "plan_id": "plan_001",
  "device_id": "arm_demo_01",
  "result": "success",
  "reusable_skill_candidate": true
}
```

## Current Status

- API trial entrance: planning
- Developer documentation: preparing
- Core service: pending release
- Public SDK: pending release

## Notes

This preview is intended for communication and early trial planning. Endpoint names, payload fields, and response formats may change before public release.