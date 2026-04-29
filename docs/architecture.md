# Architecture

码元引擎围绕具身智能任务构建四层模块结构：Semantic Layer、Interaction Layer、Adapter Layer 和 Workflow Layer。该结构的目标是把多模态输入、任务表达、设备适配和执行反馈组织成可调用、可复用、可沉淀的能力体系。

## 1. Semantic Layer

Semantic Layer 负责将图像、点云、传感器状态、自然语言指令和机器人运行状态转化为统一的结构化表达。

Typical inputs:

- RGB / RGB-D image
- Point cloud
- Robot state
- Natural-language task instruction
- Scene metadata

Typical outputs:

- Scene object list
- Spatial relations
- Task context
- SceneCode representation

## 2. Interaction Layer

Interaction Layer 将具体能力抽象为可调用动作，使上层任务流程可以通过统一接口组合不同能力。

Example verbs:

- detect
- query
- match
- plan
- grasp
- place
- verify

## 3. Adapter Layer

Adapter Layer 面向不同机器人、传感器和边缘设备进行适配，重点解决坐标、单位、时间、状态和执行接口不一致的问题。

Key functions:

- Coordinate alignment
- Unit normalization
- Time synchronization
- Device-state mapping
- Execution-status tracking

## 4. Workflow Layer

Workflow Layer 记录任务执行过程，并将成功轨迹、失败样本和异常状态沉淀为可复用数据。

Long-term value:

- Successful workflows can become reusable skill packages.
- Failure cases can become valuable optimization samples.
- Deployed devices can continuously contribute task data.
- The system becomes stronger as more scenarios are used.

## Data Loop

The long-term loop is:

1. Deploy module to real device.
2. Execute task in real scenario.
3. Record scene, action, result, and failure information.
4. Return valuable data to the central system.
5. Optimize modules and skill templates.
6. Reuse improved skills in future deployments.