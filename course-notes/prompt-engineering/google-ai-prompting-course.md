# Google AI Prompting Course

## Module 1: Start Writing Prompts like a Pro

### 5 Step Framework

- Framework Overview:
  - Task
  - Context
  - References
  - Evaluate
  - Iterate
- Tasks
  - Persona
    - "Act as an security expert to suggest..."
  - Output format
    - "...and organize that data into a table."
- Context
  - The more context you can provide, the better the output will be.
  - Context should allow for targeted output (i.e. if prompting for help
    with generating gift ideas, include the age of the recipient and a few
    details about their tastes).

- References
  - Providing examples of what you want can clarify ambiguity for models.
  - In the gift-giving example, this would be the inclusion of past gifts
    that the recipient really liked.

- Evaluate & Iterate
  - Examine the output you received; if it's not exactly what you're looking
    for, add additional details for persona, context, and references, and
    continually iterate.
  - Prompting should be iterative, it is rarely a one and done shot.

### Iteration Methods

- Revisit the prompting framework.
- Separate your prompt into shorter sentences (long-running sentences can
  muddle clarity for the model).
- Try different phrasing or switch to an analogous task.
- Introduce constraints.

### Issues & Mitigations RE: Model Usage

- Hallucination is when a tool provides outputs that are inconsistent,
  incorrect, or even nonsensical.
- AI systems trained on human-generated content often inadvertently inherit
  the biases prsent in that content, including those related to gender,
  race, etc.
- It is the responsibility of the end user to ensure that what the LLM
  produces is accurate. Some considerations to keep in mind:
  - Evaluate suitability: ensure AI fits the task and does not reinforce
    harmful biases.
  - Get approval: obtain company consent before using AI on projects.
  - Protect privacy: use secure tools and avoid exposing sensitive data.
  - Validate outputs: review all AI-generated content before sharing.
  - Be transparent: disclose AI use to teams and clients.

### Additional Notes

- ABI: "Always be iterating"
- TCREI: "Thoughtfully create really excellent inputs" to remember 5 step
  framework above.
- Interact with different modalities (input & output):
  - Pictures
  - Audio
  - Video
  - Code

## Module 2: Design Prompts for Everyday Work Tasks

### Module 2 Notes

- A classic use case of generative AI is the production of content for work
  tasks:
  - Documentation
  - Emails
  - Essays
  - etc.
- Clear directions for the task are very important.
  - Bad direction: "Write a casual summary."
  - Good direction: "Write a summary in a friendly, easy to understand tone
    like explaining to a curious friend."

## Module 3: Speed up Data Analysis and Presentation Building

### Module 3 Notes

- Be very careful about what data you share with a generative AI model (be
  mindful of employer privacy policies, PII, and things of that nature).
- Excel (and Google) Sheets can be uploaded as context for the LLM to guide
  the creation of new columns and formulas; the model can also perform trend
  analysis (e.g. analyzing correlation).

## Module 4: Use AI as a Creative or Expert Partner

## Advanced Prompting Techniques

- Prompt Chaining: Prompt chaining guides generative AI tools through a
  series of interconnected prompts, adding new layers of complexity along
  the way.
  - The idea is to use the output of the previous prompt as added context
    for the task in the next prompt.
    - This technique can allow you to slowly build out project plans.
- Chain of Thought Prompting: Ask the AI model to explain its reasoning as
  a step by step process.
  - This is basically like when a math teacher instructs you to show your
    work when solving a problem.
  - You can achieve this by adding the following to the end of your prompt:
    "Explain your thought process."
- Tree of Thought Prompting: Ask the AI model to produce distinct and varied
  threads of processing to solve the problem.
  - This technique allows you to explore multiple reasoning paths (like
    branches of a tree) simultaneously.
    - This is best for particularly complex or abstract problem-solving
      (e.g. outlines or drafting sections of a long document).
    - A good example would be the following: "Imagine three different
      designers are pitching their design to me. All designers will write
      down one step of their thinking, then share it with the group. Then
      all experts will go on to the next step. If any expert realizes
      they're wrong at any point, then they will leave. The task is this:
      Generate an image that's visually energetic and features images of
      engineers and computers. Show me three suggestions in very different
      styles from simple to detailed & complex."

## AI Agents

- AI Agent: an AI agent is like an expert designed to help with tasks and
  answer questions (e.g. coding agent, marketing agent, learning agent, or
  a friend).
- 2 Examples of Agent Types:
  - Simulation Agents (e.g. Agent Sim) can simulate scenarios with you,
    conduct interviews, or participate in role playing.
    - When using Simulation Agents, you want to focus primarily on persona
      and context.
  - Expert Feedback Agents (e.g. Agent X) is able to give you feedback
    about any topic of your choosing, sort of like a personal tutor or
    consultant.
    - Give as much context and detail as possible as far as the task and
      context.
- Guidelines for creating an AI Agent (using an LLM):
  - Step 1: Assign a Persona (e.g. "Act like a successful personal fitness
    trainer and talented nutritionist.")
  - Step 2: Give as much context and detail as possible about the scenario
    and the conversation (e.g. "I'm looking to improve my overall fitness
    and adopt a healthier lifestyle.")
  - Step 3: Specify the type of conversations or interactions you want to
    have with the AI agent (e.g. "Ask me about my workout routines and meal
    planning, and give feedback.")
  - Step 4: Provide a Stop Phrase to stop the conversation when you are
    done (e.g. "When I want to end the conversation, I'll say 'No pain, no
    gain.'")
  - Step 5: Ask the tool to provide feedback or areas of improvement when
    the conversation ends (e.g. "At the end of our conversation, provide
    a summary of the advice you provided.")

## Pro Tips

- A couple Pro-tips
  - You can combine chain of thought and tree of throught prompting by
    asking the AI to explain its reasoning at each iteration so you can
    provide feedback.
  - Meta-Prompting: using generative AI models to generate prompts for use
    with generative AI models
    - Models often create excellent prompts, and you can use them to
      accelerate your prompting significantly.
