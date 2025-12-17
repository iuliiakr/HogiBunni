# HogiBunni

<a href="https://www.loom.com/share/2952c30088ee4fc2885be3a799167dd0">
  <img src="hogibunni.png" width="300" alt="Demo Video" align="right" padding="15 0">
</a>
**HogiBunni** is an optimistic, AI-powered travel itinerary builder that creates personalized, day-by-day travel plans. It combines the reasoning power of Large Language Models with the accuracy of Google Maps to ensure every suggestion is a real, verified place.

<p></p>

The name is derived from the Kannada phrase **"Hogi Banni"** (ಹೋಗಿ ಬನ್ನಿ), which literally translates to "Go and return" - a heartwarming way to say goodbye to a traveler, ensuring they return safely.

## Demo

**[36-second silent demo](https://www.loom.com/share/2952c30088ee4fc2885be3a799167dd0)** showing the V1 flow: input -> orchestration -> structured output.

This repository documents a V1 prototype.  
If you’re interested in trying the live version or sharing feedback, feel free to reach out.

## Key Features

*   **Verified Intelligence**: Uses a hybrid approach of Generative AI for planning and **Google Maps Grounding** for verification. Zero hallucinations - every place suggested exists in the real world.
*   **Context Aware**: Checks **Live Weather** and **Public Holidays** for your specific dates. (e.g., Suggests indoor museums during rain).
*   **Interactive Refinement**: Don't like a suggestion? Mark it as "Remove" and the AI will surgically replace just that slot while keeping the rest of your plan intact.
*   **Eco-Friendly Clustering**: Automatically groups daily activities by neighborhood to minimize transit time and carbon footprint.
*   **Local Persistence**: Saves traveler profiles and recent searches directly to your browser.
*   **Shareable Plans**: Generate professional PDFs or copy formatted text summaries to share with friends.

## Architecture Overview (V1)

This project is a deliberately scoped V1 prototype that explores how an LLM can be integrated into a user-facing workflow for travel planning, with an emphasis on clarity, reliability, and architectural restraint.

*   **Frontend**: React 19 + TypeScript + Vite.
*   **Styling**: Tailwind CSS with a custom "Warm & Optimistic" design system.
*   **AI Engine**: Google Gemini API ('gemini-2.5-flash') via the '@google/genai' SDK.
*   **Data Sources**:
    *   **Google Maps Tool**: Used for verifying place existence, getting addresses, and ratings.
    *   **Google Search Tool**: Used for live weather forecasting and finding public images/pricing.

### Data Flow
1.  **User Input**: Location, Dates, Traveler Profile.
2.  **LLM Reasoning**: Gemini generates a logical flow (Morning -> Night).
3.  **Grounding**: The model queries Google Maps to verify every venue.
4.  **Rendering**: The UI renders a timeline view with interactive feedback buttons.
5.  **Refinement Loop**: User feedback is sent back to the LLM to regenerate specific time slots.

## Future Roadmap

*   **Multi-City Trips**: Logic to handle "Road Trip" style itineraries spanning multiple locations.
*   **User Accounts**: Move from 'localStorage' to a backend (Supabase/Firebase) to sync itineraries across devices.
*   **Budget Calculator**: Real-time summation of estimated ticket costs.
*   **Booking Integration**: Deep links to Reserve with Google for restaurants.
