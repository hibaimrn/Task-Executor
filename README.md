# Dash

An AI-powered project planning agent that converts your goal into a structured, milestone-based plan with prioritized tasks, timelines, and progress tracking.

## Overview

Dash is a task planning assistant that generates detailed, actionable project plans. Input your goal, timeframe, and daily availability, and Dash creates a plan with:

- Multiple **milestones** (major phases)
- Prioritized **tasks** within each milestone
- **Daily assignments** and time estimates
- **Progress tracking** with visual progress bar
- **Quick reference** sections for next moves
- **Exportable plans** as Markdown or plain text

Perfect for:
- **Project kickoffs**: Break down big goals into phases
- **Personal goals**: Structure fitness, learning, or life changes
- **Team planning**: Share via Markdown with your team
- **Accountability**: Track what's done, what's next

## Features

- **Smart Task Generation**: Breaks down goals into realistic milestones and actionable tasks
- **Prioritization**: Tasks marked as High, Medium, Low priority
- **Timeline Assignment**: "Day 1", "Week 2", etc. for scheduling
- **Contextual Notes**: "Why" notes explain the reasoning behind tasks
- **Progress Tracking**: Check off tasks, see real-time progress bar
- **Multiple Exports**:
  - Copy as plain text
  - Download as Markdown
  - Share with teams
- **No External Dependencies**: Runs entirely in-browser, no backend needed

## Getting Started

### Requirements

- Modern web browser
- OpenAI API key (for plan generation)
- 2-3 minutes of your time

### Usage

1. **Load Dash** in your browser
2. **Paste your OpenAI API key** (not stored, cleared on refresh)
3. **Define your project**:
   - **Goal**: What are you trying to achieve? (e.g., "Launch a new AI product")
   - **Timeframe**: How long? (e.g., "12 weeks", "3 months", "6 months")
   - **Time per day**: How much time can you dedicate? (e.g., "2 hours", "full-time")
   - **Model**: Choose gpt-4o (recommended) or gpt-4o-mini (faster, cheaper)
4. **Click "Create plan"**
5. **Review the generated plan**:
   - Summary of the approach
   - Next 3 moves to start with
   - Detailed milestones and tasks
6. **Track progress**: Click tasks to mark complete
7. **Export**: Download as Markdown or copy for sharing

## Plan Structure

```
GOAL: Launch AI content moderation SaaS MVP
12 weeks · Full-time · 5 milestones · 47 tasks

SUMMARY:
Build a moderation model, develop web API, create 
basic dashboard, get first customers, gather feedback.

NEXT 3 MOVES:
1. Set up dev environment and review moderation libraries
2. Train initial classification model on labeled data
3. Design API spec and write endpoint scaffolding

MILESTONE 1: Research & Prototyping (Weeks 1-2)
Focus: Evaluate models, prove concept

Tasks:
- [x] Research existing ML moderation approaches
- [ ] Test OpenAI Moderation API vs local models (High priority)
- [ ] Gather sample data for fine-tuning
... (tasks with priorities, days assigned, and rationale)

MILESTONE 2: Core API Development (Weeks 3-5)
... and so on
```

## Configuration

| Option | Purpose | Examples |
|--------|---------|----------|
| Goal | What you're building | Launch product, complete course, build habit |
| Timeframe | Duration | 4 weeks, 3 months, 6 months |
| Time per day | Daily commitment | "2 hours", "40 hours/week", "full-time" |
| Model | LLM for planning | gpt-4o, gpt-4o-mini |

## Understanding Task Fields

Each task contains:

- **Task text**: What to do (e.g., "Set up CI/CD pipeline")
- **Priority**: High, Medium, or Low (helps with scheduling)
- **Day/Week**: When to do it (e.g., "Day 3", "Week 2")
- **Why note**: Reasoning or context (e.g., "Needed before API testing")
- **Checkbox**: Click to mark complete

Example:
```
[x] Deploy MVP to production (High priority, Week 6)
    — Required for customer feedback, gates final QA
```

## Progress Tracking

The progress bar shows:
- **Percentage complete**: Visual representation
- **Task count**: "22 / 47 done"
- **Completion state**: Automatically updates as you check tasks

## Export & Sharing

### Markdown Export
Download as `.md` file with:
- Formatted headings and sections
- Checkbox syntax for task lists
- Ready for GitHub, Notion, or tools

```markdown
# Launch AI SaaS MVP

**Timeframe:** 12 weeks | **Time per day:** Full-time | **Progress:** 5/47 tasks

> Build a moderation model, develop web API...

## Start here — your next 3 moves

1. Set up dev environment and review libraries
2. Train initial classification model on labeled data
...
```

### Plain Text Export
Copy to clipboard:
- Simple, readable format
- No Markdown syntax
- Paste into email, docs, messaging

## Best Practices

### Strong Goal Definitions

✅ **Good**:
- "Build and ship a personal finance iOS app with budgeting and goals"
- "Go from zero to Python intermediate level"
- "Create a sustainable morning routine and 25-lb weight loss"

❌ **Vague**:
- "Do a project"
- "Learn stuff"
- "Get fit"

### Realistic Timeframes

| Goal Complexity | Realistic Duration |
|---|---|
| Small feature | 1–2 weeks |
| MVP / Prototype | 2–6 weeks |
| Product launch | 6–12 weeks |
| Career pivot | 3–6 months |
| Major life change | 6–12 months |

### Time Commitment Clarity

- **"2 hours/day"**: Part-time side project
- **"5-6 hours/day"**: Full focus, flexible schedule
- **"Full-time"**: 40+ hours per week, dedicated
- **"Weekends only"**: Slow-moving, long timeframe

## Cost

Plan generation typically costs:
- **Simple goal** (gpt-4o-mini): ~$0.05–0.15
- **Complex goal** (gpt-4o): ~$0.20–0.50

*Usually a one-time cost; regenerating plans is cheap.*

## Architecture

**Frontend**: Single-page app, pure HTML/CSS/JavaScript

**No Backend**: Everything runs client-side

**Data Storage**: 
- Plans stored in browser memory only
- Export if you want to save

**Integrations**:
- OpenAI Chat API for plan generation

## API Usage

Behind the scenes, Dash uses:

```javascript
// Sends your goal, timeframe, and availability
const response = await openai.createChatCompletion({
  model: "gpt-4o",
  messages: [
    { role: "system", content: "You are a project planning expert..." },
    { role: "user", content: "Goal: ..., Timeframe: ..., Hours/day: ..." }
  ]
});
```

The model returns structured JSON with milestones and tasks.

## Example Plans

### Example 1: Ship an AI Product
```
Goal: Launch an AI writing assistant SaaS
Timeframe: 12 weeks
Time per day: Full-time

Output:
- Milestone 1: Research & model selection (Week 1-2)
- Milestone 2: API & backend (Week 3-5)
- Milestone 3: Dashboard frontend (Week 6-8)
- Milestone 4: Beta testing & iteration (Week 9-10)
- Milestone 5: Launch & marketing (Week 11-12)
Total: 52 tasks across 5 milestones
```

### Example 2: Personal Learning Goal
```
Goal: Learn React and build 3 projects
Timeframe: 8 weeks
Time per day: 2 hours (20 hours/week)

Output:
- Milestone 1: Fundamentals (Week 1-2)
- Milestone 2: Project 1 - Todo app (Week 2-3)
- Milestone 3: Project 2 - Dashboard (Week 4-6)
- Milestone 4: Project 3 - Real app (Week 6-8)
Total: 35 tasks
```

### Example 3: Business Launch
```
Goal: Launch podcast and reach 1000 listeners
Timeframe: 6 months
Time per day: 3 hours (part-time)

Output:
- Milestone 1: Equipment & setup (Weeks 1-2)
- Milestone 2: First 10 episodes (Weeks 3-6)
- Milestone 3: Distribution & growth (Weeks 7-16)
- Milestone 4: Community building (Weeks 17-26)
Total: 64 tasks
```

## Limitations

- Plans are AI-generated; you know your project best
- Adjust timelines and priorities based on your actual pace
- Some tasks may not be relevant to your situation (delete or modify)
- No real-time collaboration (plans are client-side only)
- No integration with external tools (Jira, Asana, etc.) yet

## Tips for Success

1. **Review first**: Don't blindly execute. Read the plan, adjust as needed.
2. **Track weekly**: Update progress weekly to stay honest
3. **Flex the timeline**: If tasks take longer, adjust milestones
4. **Add context**: Use "why" notes to remember your reasoning
5. **Celebrate wins**: Mark tasks complete as you go, don't wait till the end
6. **Regenerate as needed**: Project changed? Generate a new plan.

## Privacy

- **API keys**: Sent only to OpenAI, never stored or logged
- **Plan data**: Stored in browser memory only, cleared on refresh
- **No backend**: Nothing sent to external servers
- **HTTPS recommended**: Ensure secure connection

## Future Features

- [ ] Plan templates for common goals
- [ ] Dependency mapping between tasks
- [ ] Estimated time per task
- [ ] Team collaboration and task assignment
- [ ] Calendar integration for scheduling
- [ ] Slack/Discord notifications for milestones
- [ ] Progress analytics and burndown charts
- [ ] AI check-ins for plan adjustments

## Use Cases in the Wild

**Startups**: Use Dash to plan MVP launches
**Learning**: Break down courses into daily tasks
**Fitness**: Create realistic workout progression plans
**Writing**: Outline book or content projects
**Career**: Plan skill development and job transition
**Home**: Structure home renovation or organization projects

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Plan doesn't load | Check API key, refresh page |
| Tasks unclear | Regenerate with more specific goal |
| Timeline unrealistic | Adjust "time per day" or extend timeframe |
| Too many tasks | Start with MVP goal, add phases later |
| Can't find a task | Use browser find (Ctrl+F) to search |

## License

MIT

## Questions or Feedback?

Open an issue or PR. Dash improves with your input.
