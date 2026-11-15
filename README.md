# Project 9: L'Oréal Routine Builder
L’Oréal is expanding what’s possible with AI, and now your chatbot is getting smarter. This week, you’ll upgrade it into a product-aware routine builder. 

Users will be able to browse real L’Oréal brand products, select the ones they want, and generate a personalized routine using AI. They can also ask follow-up questions about their routine—just like chatting with a real advisor.
## Run the routine builder

Serve the repository over HTTP (for example, `python3 -m http.server 8000`) or open the GitHub Pages site. Search by product name, brand, or ingredient alongside the category dropdown. Product details expand independently of selection. Picks are saved in the current browser. The RTL layout button mirrors the interface, and chat messages automatically follow the direction of their text.

## Cloudflare Worker and live web search

The frontend currently uses the existing beauty advisor Worker. It serves routine generation and follow-up chat with GPT-4.1. The web-search implementation in `worker/index.mjs` is ready to deploy separately so the previous project can keep its existing Worker. It uses the OpenAI Responses API with `web_search` and returns clickable citation annotations in the same response envelope the frontend expects.

Deploy the module Worker through Cloudflare with an `OPENAI_API_KEY` secret and an `ALLOWED_ORIGINS` variable containing the Pages origin (`https://mohammad-comp.github.io`). You can set `OPENAI_MODEL` to another web-search-enabled Responses model. Apply rate limiting at Cloudflare for a publicly available, metered endpoint. Replace `workerUrl` in `script.js` with the deployed URL, then check that a current product question returns clickable citations. Until this deployment is connected, the published site uses the existing advisor without live search.
