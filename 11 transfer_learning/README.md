![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/c014f7e1-021c-4ca3-b503-d8eebc3c70bb)# Transfer Learning Qna
## q1) Difference between Transfer Learning vs Multitask Learning vs lifelong learning

### Transfer Learning

Transfer learning involves leveraging knowledge from one or multiple source tasks/domains to improve learning on a target task/domain. In transfer learning, the goal is to enhance performance on the target task by transferring relevant knowledge from the source task(s). This approach assumes that there are labeled training data for the source task(s) and limited labeled data (or even none) for the target task, but there is an abundance of unlabeled data available for the target task. The focus is solely on improving performance on the target task, and learning from the source task(s) is not considered relevant beyond transferring knowledge.

### Multitask Learning

Multitask learning, on the other hand, involves simultaneously learning multiple tasks. Rather than treating each task independently, multitask learning aims to optimize performance across all tasks by leveraging shared knowledge. In this approach, the learner co-learns all tasks simultaneously, utilizing commonalities between tasks to improve overall performance. Multitask learning can be conducted in batch mode, where all tasks are learned together, or in online mode, where tasks are learned sequentially over time, which is more akin to lifelong learning.

### Lifelong Learning

Lifelong learning extends beyond transfer learning and multitask learning by considering a sequential learning process. In lifelong learning, the learner accumulates knowledge from a series of tasks and applies this knowledge to facilitate learning on subsequent tasks. When faced with a new task, the learner utilizes relevant knowledge gained from past tasks to aid in learning without directly observing data from the new task. This can involve generating prior knowledge from past tasks to assist in learning without access to future task data. **Lifelong learning differs from both transfer learning and multitask learning in that it emphasizes leveraging past knowledge for future tasks without jointly optimizing learning across all tasks or relying on labeled data from the target task.**


## q2) Application areas of transfer learning?
  Resource constraint environment
  Source task and target task need not to be solved simultaneously.
  Privacy concerns associated with the source training data-set.

## Q3) Fine tuning vs transfer learning ? Describe fine-tuning choices.

While transfer learning freezes all the pre-trained layers and only trains the new layers, fine-tuning goes a step further by allowing the pre-trained layers to be updated. Both techniques have their advantages and are suitable for different scenarios.

**Some Design Choices are:
**
1) Fine-tune with a smaller learning rate
2) Smaller lr for earlier layers
3) Freeze earlier layers, gradually unfreeze
4) Reinitialise Last layer
5) Search over hyperparameters via cross-val
6) Architecture choice Matter

Below is an example of the Impact of freeze and training Different layers in a neural network:
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/46ca9459-dfbc-4d5d-ac91-a28b5266d315)




## Q5) Differentiate Meta-learning, transfer learning and multi-task learning ?

![Screenshot from 2024-05-12 03-13-34](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/f576ac32-d82e-4e0a-961a-aa1f85ae5919)

