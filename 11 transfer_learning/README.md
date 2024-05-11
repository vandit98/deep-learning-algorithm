# Transfer learning Qna
### q1) difference between transfer learning vs multitask learning ?
| Aspect                  | Lifelong Learning                                   | Transfer Learning                                     | Multitask Learning                                      |
|-------------------------|-----------------------------------------------------|-------------------------------------------------------|--------------------------------------------------------|
| Learning Paradigm       | Learns a sequence of tasks incrementally,           | Focuses on transferring knowledge from a              | Simultaneously learns multiple tasks, optimizing      |
|                         | leveraging knowledge from past tasks to aid         | source domain/task to a target domain/task.          | performance across all tasks through shared knowledge.|
|                         | learning for future tasks.                          |                                                       |                                                        |
| Objective               | Aims to learn well on future tasks without          | Aims to improve learning for the target task by      | Aims to improve learning/performance across all tasks. |
|                         | observing their data so far.                        | leveraging knowledge from related tasks.            |                                                        |
| Relationship among      | Sequences tasks and uses knowledge gained           | Typically involves a single source domain/task      | Co-learns multiple tasks concurrently, optimizing    |
| Tasks                   | from past tasks to assist learning for future       | and a target domain/task.                           | across all tasks.                                     |
|                         | tasks.                                              |                                                       |                                                        |
| Knowledge Transfer      | Utilizes knowledge gained from past tasks to        | Transfers knowledge from source to target            | Shares knowledge among tasks during learning process. |
|                         | facilitate learning for future tasks.               | domain/task.                                          |                                                        |
| Approach                | Adapts to new tasks by leveraging past             | Adapts pre-trained models or features to new tasks   | Jointly learns tasks, exploiting commonalities among |
|                         | knowledge without directly observing future         | with limited data.                                   | tasks to enhance learning efficiency.                 |
|                         | task data.                                          |                                                       |                                                        |
| Data Requirements       | Learns incrementally from task data and prior       | Requires labeled data in source domain/task,         | Requires labeled data for all tasks,                  |
|                         | knowledge.                                          | possibly unlabeled data in target domain/task.       | potentially with shared unlabeled data.               |
| Goal                    | Aims to learn well on future tasks without          | Enhances performance on target task only by          | Enhances performance across all tasks.               |
|                         | observing their data so far.                        | leveraging knowledge from related tasks.            |                                                        |
|                         |                                                     | Learning for source task(s) is irrelevant.          |                                                        |
