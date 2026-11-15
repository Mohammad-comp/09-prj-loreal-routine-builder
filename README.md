# Project 9: L'Oréal Routine Builder
L’Oréal is expanding what’s possible with AI, and now your chatbot is getting smarter. This week, you’ll upgrade it into a product-aware routine builder. 

Users will be able to browse real L’Oréal brand products, select the ones they want, and generate a personalized routine using AI. They can also ask follow-up questions about their routine—just like chatting with a real advisor.
## Run the routine builder

Serve the repository over HTTP (for example, `python3 -m http.server 8000`) or open the GitHub Pages site. Search by product name, brand, or ingredient alongside the category dropdown. Product details expand independently of selection. Picks are saved in the current browser. The RTL layout button mirrors the interface, and chat messages automatically follow the direction of their text.

## Cloudflare Worker and live web search

The published site uses the existing Cloudflare beauty advisor’s /routine route. This route uses the OpenAI Responses API with the web_search tool and returns clickable citation annotations. Other routes continue to serve the earlier chatbot.

The worker/index.mjs file contains the handler as a standalone Cloudflare module. To run it separately, bind OPENAI_API_KEY as a Worker secret and set ALLOWED_ORIGINS to your Pages origin. You can set OPENAI_MODEL to another Responses model that supports web search. Point workerUrl in script.js to the deployed endpoint. Ask for a current product page to check that citations are clickable.
