# HogiBunni

## Demo

[Demo video (Loom)](https://www.loom.com/share/2952c30088ee4fc2885be3a799167dd0)

36-second silent demo showing the V1 flow: input -> orchestration -> structured output.



## Architecture Overview (V1)

This project is a deliberately scoped V1 prototype that explores how an LLM can be integrated into a user-facing workflow for travel planning, with an emphasis on clarity, reliability, and architectural restraint.

The system follows a simple three-layer design:

### 1. Frontend (Web UI)
The frontend collects user input (destination, dates, and a free-form description of the travel party), displays progress, and renders structured itinerary output. It also provides lightweight share and print views, implemented without user accounts or persistent user state.

### 2. Backend / Orchestration Layer
The backend acts as a thin orchestration layer responsible for:

- validating and normalizing user input
- constructing prompts
- invoking the LLM
- post-processing the response into a predictable, structured format

This layer intentionally contains the application logic, keeping the frontend simple and the LLM isolated behind a clear interface.

### 3. LLM Integration

The LLM is used as a reasoning and generation component, not as an application controller. Prompt design and output constraints are used to reduce hallucinations and ensure consistently structured results suitable for direct user consumption.


## Design Trade-offs (Intentional for V1)

Stateless by design: no user accounts, long-term storage, or personalization

Optimized for clarity and iteration speed rather than scale

Share/print implemented as shallow features to support usability without introducing identity or data-retention complexity

If evolved beyond V1, the system could be extended with persistence, personalization, and scaling strategies, but those concerns are intentionally deferred to keep the prototype focused and inspectable.
