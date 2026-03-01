# Get Started with ADK - Comic

## Overview
- **Lab**: Get Started with Google Agent Development Kit (ADK)
- **Art Style**: Tech
- **Pages**: 3 (Cover + 2 pages)
- **Generated on**: 2026-03-01

## Comic Pages

### Cover
![Cover](00-cover.png)

### Page 1 - Installation & First Steps
![Page 1](01-page.png)

**Content**: Dev meets ADK-Bot who guides them through installing ADK with `pip install google-adk`, understanding the project structure (agent.py, __init__.py), and equipping an agent with the google_search tool.

### Page 2 - Dev UI & Testing
![Page 2](02-page.png)

**Content**: Launching the ADK Dev UI with `adk web`, testing grounded search results, using structured output with Pydantic schemas, running agents via CLI with `adk run`, and previewing multi-agent systems with SequentialAgent.

## Core Knowledge Points
1. **ADK Installation & Project Structure** - Every agent lives in a folder with `agent.py` and `__init__.py`
2. **Tool Integration** - Adding `google_search` gives agents real-time web search capabilities
3. **Three Ways to Run Agents** - Dev UI (`adk web`), programmatic (`InMemoryRunner`), and CLI (`adk run`)
4. **Structured Output** - Use Pydantic `BaseModel` as `output_schema` for clean JSON responses
5. **Multi-Agent Preview** - SequentialAgent chains agents like `critic_agent` -> `reviser_agent`

## Characters
- **ADK-Bot** - Friendly robot mentor with Google colors
- **Dev** - Young developer learning ADK
- **Search-Sprite** - Golden orb representing the google_search tool
