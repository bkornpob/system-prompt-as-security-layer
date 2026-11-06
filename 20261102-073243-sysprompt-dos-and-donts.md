# opening hook

SYSTEM PROMPTS ARE NOT SECURITY BOUNDARIES.

If your AI agent has a system prompt saying “never do this”
know that it's not a rule.
It is a recommendation ... and sometimes, your agent may forget about the "never do this"

One time, i was leading a LLM wiki and Skill development project for an AI agent.
an impossible request landed on the table:
secure its internal knowledge using system prompt security.

that brought us here today. 
Let's talk about:
what system prompt is,
its role as a security layer, 
and the hard DOs and DONTs.

hi SEEKER สวัสดีครับ
dr.kb here
grab a bowl and let's dive into this rabbit-hole

# what system prompt is

system prompt is ... 
a text string, background instructions, a tutorial guidebook for the bot

developer put this system prompt inside a bot, 
and the bot was trained to prioritize and keeps reading it while doing its things.

typical use cases for a system prompt includes:
- guiding role scope--that is giving it a hat to be specialized in roles like being a technical specialist, a ghost writer, or a grandma tutor,
- guiding steps reasoning and logic--about of how to think, process, and tool call,
- guiding vibe, user interaction, and user experience--such as through output formatting or aligned values and words, 
- and ... guiding security constraints --which is very brittle, but also very important to implement it right.

again ... system prompt is a guidebook, 
NOT a rulebook, NOT an unbreakable security boundary, NOT access control policy.

# system prompt as a security layer

system prompt as a security layer ...
it's brittle, but it's still a useful soft layer ... one layer in defense in depth, not the last line.
it works through three things:

- instruction hierarchy ... through post-training, the model learns to weight system instructions above user messages. it’s a learned tendency, not a separate privileged channel.
- role tags and delimiters ... system, user, assistant ... the model learns to trust each role differently. and as a developer, you can add your own delimiters to mark untrusted content, like retrieved documents or tool outputs ... treated as data to read, not orders to follow.
- scope and refusal rules ... this part is on you. tell the bot it only handles cooking recipes and refuses trip planning ... and it’ll mostly comply.

# DOs and DONTs for system prompt as security layer

For the last part, here are the DOs and DON'Ts for using a system prompt as a security layer.

**DOs**
- **Set an instruction hierarchy.** System and developer instructions outrank user input, tool output, and retrieved content.
- **Treat external input as untrusted data.** Wrap user text, RAG documents, and web content in delimiters, tell the model it's data, never commands, and strip those delimiters from the input.
- **Specify explicit prohibitions.** State what the model must not do (reveal secrets, mention competitors), and make sure the rules don't conflict.
- **Isolate non-negotiable rules.** Give them their own XML tag or Markdown header, apart from tone and workflow.
- **Keep refusals short and neutral.** One or two sentences, no moralizing. Long refusals leak signal.
- **Constrain tools in the prompt, enforce in code.** Validate every call against a schema outside the model.
- **Apply least privilege.** Give the model only the tools, data, and permissions the task needs.
- **Red-team before shipping.** Test injection and extraction, then monitor logs.

**DON'Ts**
- **Don't treat the prompt as a security boundary.** Models fail probabilistically. Spending caps, database permissions, and API authorization belong in code.
- **Don't put secrets or PII in the prompt.** Assume it will be extracted.
- **Don't concatenate untrusted text into the system message.** Keep user and retrieved content in user or tool roles.
- **Don't rely on the prompt for irreversible actions.** "Ask before deleting" will eventually fail. Require human approval at the application layer.
- **Don't bloat the rulebook.** Edge cases dilute attention, add cost, and create contradictions.

# Call to actions

coming to the end ...
here are a few things you can start today for a better AI hygiene.

if you've ever run `ollama create model -f Modelfile`, you've already baked a system prompt into a local model.
or if you use a modern AI platform, you may have noticed a `user instructions` slot, which works like your own baked-in prompt. 
either one is a safe playground to practice on.

so try this:
- audit your system prompt: find every “never” and “always”
- experiment with different versions
- attack your own agent: try to extract the prompt, inject through your own documents
- strengthen it, then attack it again
- move anything that protects money, data, or irreversible actions into code
- share what you learn

remember ... 
SYSTEM PROMPTS ARE NOT SECURITY BOUNDARIES.
It is a guidebook.

thank you for today
SEEKER, stay curious, stay safe
until next rabbit hole
dr.kb out
ขอบคุณครับ
