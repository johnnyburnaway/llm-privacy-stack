# Privacy-preserving LLM tools 


 Last updated: 31 Dec 2025

This is a human-curated collection aimed at privacy-conscious users and builders. Leverage LLMs with no or minimized tracking, profiling and surveillance risks. Solutions listed are not constrained to fully local setups. Enterprise and experimental tools might feature, but are not prioritized. 


## Private LLM use strategies

When interacting with cloud LLM providers, your data, queries, inputs, and outputs become tied to your real identity. Due to this connection, data from your activities can be mined, synthesized, sold, weaponized, subpoenaed and generally used in ways that won't benefit you.   

You have the following choices when considering this issue, in order of privacy protection level:

| Strategy | Tools | Tradeoffs | Complexity | Examples | 
| :--- | :--- | :--- | :--- | :--- | 
| #1 Local-only setup | Open source/open weight models <br>Local inference  | Resource intensive <br> Open source model performance gap vs. frontier LLMs | High | LMStudio + DeepSeek V3.2 
| #2 Use verifiable cloud inference | Local apps <br>  Open source/open weight models in cloud, run in TEE | Not free compared to Local-only <br> Payment information shared <br>  Open source (OS) model performance gap vs. frontier LLMs | Medium |OpenWebUI + Tinfoil.sh  
| #3 LLM proxy/router  | Local apps <br> LLM router to increase degree of separation, <br>  Local & Proxy routing mix |Trust shifts to router <br> Memory and persistent context harder to manage | Medium |AnythingLLM + OpenRouter with ZDR
| #4 Web services | Privacy-first open source model inference and frontier LLM proxy packaged as subscription service | Trust need shifts to service provider<br>Open source model performance gap vs. frontier LLMs<br>Unfavorable pricing schemes |Low | Kagi Assistant, Brave Leo
| #5 Direct SOTA| Frontier lab service use via Web or API | Personal details shared = Provider owns data with PII attached |Low| Chatgpt.com, Gemini app

If you are reading this, you are likely not comfortable with the Direct route (Option 5). You shouldn't be. Leading providers like Anthropic, OpenAI and Google might promise to not train models on your data, but that does not stop them from changing their policies or reusing collected information in other ways (see [the Big Rug](https://x.com/goodalexander/status/1955578905706033651) theory).

Where you end up between Options 1-4 depends on your workflows, needs and privacy expectations. Options can be mixed to mitigate some drawbacks per choice, which in turn increases complexity of your setup.



## Tools 


### Local Apps [#1, #2, #3] 

Tools that help you download and run models locally and/or connect to APIs. Open source unless noted. Ordered from most straightforward to most complex. 
 

| Tool | Notes|
| :--- | :--- |
| **[Jan.ai](https://www.jan.ai/)** | Desktop focused. Local inference + API plug-in options.  |
| **[AnythingLLM](https://anythingllm.com/)** | Desktop/mobile. Document chat.| 
| **[Msty](https://msty.ai/)** | Closed source. Desktop only. Unique multi-chat UI. Local context building with PII scrubbing.|
| **[LMstudio](https://lmstudio.ai)** | For running local models. Basic chat functions. |
| **[OpenWebUI](https://github.com/open-webui/open-webui)** | Desktop/mobile. Speech to text support. Local context building. Web search, web browsing. ImageGen support.|


## Services


   
### Inference providers [#2] 

You can run open source models in the cloud inside Trusted Execution Environments (TEEs) with end-to-end encrypted inference with pay-per-token pricing. Your data is processed inside secure hardware enclaves that cryptographically prove they can't be accessed, even by the provider. Your payment and account details reveal you as a customer, but with TEE your actual queries cannot be tied to your identity (metadata on usage can be).

On-demand cloud services below are built for developers and enterprise use, but you can get set up in minutes: add payment details, grab an API key and plug it into your local tools.

| Provider | Notes| Payment methods| Endpoint 
| :--- | :--- | :--- | :--- |
| **[Tinfoil](https://tinfoil.sh)** | Open source model inference with verifiable privacy guarantees through secure hardware enclaves and cryptographically-verifiable runtime attestation. Vision/audio models. Model list [here](https://docs.tinfoil.sh/models/catalog).|CC| https://inference.tinfoil.sh/v1/|
| **[Phala Network](https://phala.network/)** |  OpenAI-compatible API for running AI models in TEE on GPU hardware. Model list [here](https://docs.phala.com/phala-cloud/confidential-ai/confidential-model/confidential-ai-api#phala-provider). API through their RedPill service.| CC, Crypto (CoinBase commerce) |  https://api.redpill.ai/v1/|
| **[Near AI](https://docs.near.ai)** | Open source models run in secure Trusted Execution Environments (TEEs). Model list [here](https://docs.near.ai/cloud/models/overview). | CC |https://cloud-api.near.ai/v1|







### LLM Routers/Proxies [#3] 

Routers separate your payment identity from your queries. Plug the API key to a local app and access open source and frontier models with pay-per-token pricing. Inference providers will see aggregated traffic from the router, not your individual usage patterns.

There are many routing services, most are built for developers and enterprise use and have unfavorable privacy and retention policies. Listings below fit end-user privacy-first strategies. 

Using anon-friendly payment options and a VPN to mask your IP is good practice with this method. 

> ⚠️ Important: Listing here is not a blind endorsement. With this method you shift trust from model providers to the router operator. These services may still log, profile, or retain your queries despite their promises.  Tools are listed in order of recommendation by author.


| Router | Notes| Payment methods| Endpoint
| :--- | :--- | :--- | :--- 
| **[Nano-GPT](https://nano-gpt.com//)** | Web chat and API. No mandatory sign up. Image/Video/Audio generation models. | CC, Apple/Google Pay, Monero / Bitcoin / crypto direct. Subscription option foropen-sourcemodels.| https://nano-gpt.com/api/v1|
| **[OpenRouter](https://openrouter.ai/)** | Web chat and API. [Zero data retention](https://openrouter.ai/docs/guides/features/zdr) filter available.   | CC, Crypto (CoinBase commerce)| https://openrouter.ai/api/v1/|
| **[Redpill AI](https://www.redpill.ai)** | Web chat and API routing for frontier models. Uses TEE. Same operator as Phala Network.  | CC, Crypto (CoinBase commerce)|  https://api.redpill.ai/v1/|
| **[PPQ.AI](https://ppq.ai/)** | Web chat and API. | CC, Monero / Bitcoin / crypto direct | https://api.ppq.ai|

#### Get started with routers

1. Sign up and top up account or add billing info
2. Create and copy API key
3. Gather third-party app compatible API endpoint URL (latest known in table above)
4. Add both in your Local App at model provider setup 
5. Fetch and select models to use

### Web services [#4] 

These services offer a balance of ease-of-use and privacy protections. No local tools required. Web services can be acceptable recommendations for family, friends, or non-technical users who need immediate access without complex setup. Typically available on desktop and mobile via apps, no API support.

Frontier models (latest GPT/Claude releases) often lag behind official launches on these platforms.

> ⚠️ Note: Listing here is not an endorsement. Counterparty risk remains. You are trusting these providers to stay true to their privacy promises. Avoid using Credit Cards and opt for anon payment methods (Monero, Cash, Privacy Pass) if possible.




| Service | Notes| Price | Payment methods|
| :--- | :--- | :--- | :--- |
| **[Kagi Assistant](https://help.kagi.com/kagi/ai/assistant.html)** | Frontier model proxy, File uploads, Kagi search tie-in | $25 /mo for flagship models (bundle)| CC, Paypal, Bitcoin + [Privacy Pass](https://privacypass.github.io)|
| **[Brave Leo](https://brave.com/leo/)** | Open source  models + frontier models (latest not available), In Brave Browser, File uploads|$14.99 /mo, free tier| CC |
| **[Duck AI](http://duck.ai/)** | Open source + frontier models (latest not available), PII removal | $9.99 /mo in a bundle | CC, Paypal, App store
| **[Maple.AI](https://trymaple.ai)** | Open source models in TEE| From $20 /mo| CC, Bitcoin|
| **[Proton Lumo](https://lumo.proton.me/guest)** | Open source Models e.g. Mistral Nemo, OpenHands 32B, Files support | $12.99 /mo, free tier| CC, Paypal, Cash, Apple/Google Pay|



     
   
## Glossary

- **OS** - Open Source (includes Open Weight in this context)

- **TEE** - Trusted Execution Environment

- **PII** - Personally Identifiable Information

- **Frontier labs** - Leading LLM providers

- **SOTA** - State of the art models from frontier labs    
   
## Planned next

- [ ] Improved threat modeling explanations
- [ ] Expand on local inference guides, links, options
- [ ] Add explainer on TEE verfication 
- [ ] Add trust verification criteria explainer (e.g. routers section ranking)
- [ ] Add mobile apps
- [ ] Add local-first agent tools
- [ ] Add local-first coding tools

## Contribute

Suggestions and corrections are welcome. Open a PR, create an Issue or email me polite.artist38@mailx.net at mailx.net. 
   
