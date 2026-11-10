	2.	server.js is far too big: 1,260 lines. createApp() holds about 200 action handlers in one place, which breaks the repo's 500-line rule and ties everything together. The audit already suggested a src/actions/ split; it hasn't been done.
	3.	Messages can't be trusted by author. Anyone or anything that can write board.md can post as ## … Human or add "priority":"high" metadata. A prompt injection in one project's files could spread to every agent. The audit's suggestion to sign server-written entries is still open (there's no HMAC in bus.js).
	4.	Messages can be lost when two writers hit the board at once. Agents that edit board.md with an Edit tool rewrite the whole file while the server appends to it, so one write can overwrite the other.
	5.	The screen reading is fragile. Mode switching, permission answers and plan approval depend on each CLI's on-screen text, option labels and key bindings. Any CLI update can silently break it. The notes admit that the Gemini and opencode plan paths haven't been tested against a live CLI.
	6.	The board only grows. It is re-read and re-parsed in full on every change, and nothing archives old messages

Absolutely — here’s the updated version of the internal guide with that point included in a clear, helpful way:

⸻

Internal Connectivity Guide

Is it a Network Issue, a Blocked Domain, or Just a Wi-Fi Glitch?

Use this guide to understand what’s wrong — and what kind of ticket to open.

⸻

Step 1: Test Basic Internet Access

Open these websites in your browser:
	•	https://www.bing.com
	•	https://example.com
	•	Your company portal (if available)

If NONE of them load:

This is likely a full network issue.
You’re not connected to the internet.

Action:
	•	Check if you’re connected to Wi-Fi
	•	If you are, but nothing loads, move to Step 1A

⸻

Step 1A: Restart Wi-Fi on Your Device

Sometimes the device is connected to Wi-Fi, but not properly.
This is often caused by:
	•	Weak signal
	•	Device failing to renew its IP
	•	Internal Wi-Fi module issue

Action:
	•	Turn Wi-Fi off and back on
	•	Or restart the device completely

Then test websites again.

If websites still don’t work → Open a Network Issue ticket.

⸻

Step 2: One App or Website Doesn’t Work

If most websites work, but one app or site fails, it’s probably a blocked or closed domain.

Example:
	•	Google.com loads fine, but the company chat app doesn’t connect.

This is not a Wi-Fi problem — it’s a domain-level issue.

Action:
	•	Open a Domain Access ticket
	•	Include the name of the site or domain that doesn’t work
(e.g., api.appname.com or service-name.io)

⸻

Step 3: Ask Around (Optional Check)

Still not sure?
Ask a colleague:
	•	“Is this website or app working for you?”
	•	If yes: Try restarting your device or browser.
	•	If no: It’s likely blocked for everyone — report it.

⸻

Quick Reference – What to Do

Problem	What It Means	Action
No sites work at all	Full network outage or bad Wi-Fi	1. Restart Wi-Fi/device → 2. If still broken: Open Network Issue ticket
Wi-Fi shows connected but nothing loads	Weak or stuck connection	Restart device, retry
Most sites work, one fails	Blocked domain	Open Domain Access ticket with full domain
App says “No Internet,” but browser works	App checks a blocked test domain	Open Domain Access ticket with domain name



⸻

Let me know if you’d like this in a PDF layout or with visual icons to distribute internally!
