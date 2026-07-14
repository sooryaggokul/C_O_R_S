# 🌞~CORSair

A browser-based **CORS misconfiguration** testing tool.

<img width="1355" height="630" alt="image" src="https://github.com/user-attachments/assets/9d28866c-46c7-4abe-80f3-e4825aee21df" />



## About
CORSair is a web tool that checks whether a target endpoint leaks data across origins due to a misconfigured CORS policy. Paste a URL, hit test, and it tells you whether the browser could read the response cross-origin, and how serious that is.

CORSair runs three checks against your target URL and compares the results:
Reachability probe — a no-cors request to confirm the endpoint is actually reachable (so network/DNS/TLS failures aren't mistaken for CORS decisions).
Uncredentialed read — a cors request with credentials: omit.
Credentialed read — a cors request with credentials: include (cookies attached).

🔴 HIGH :
Authenticated data is readable cross-origin - the server allows a specific origin with credentials. Private, cookie-authed data could be read by another origin.
🟡 INFO : 
Readable without credentials only - typically Access-Control-Allow-Origin: * on a public endpoint. Usually intentional and safe.
🟢 BLOCKED :
The Same-Origin Policy blocked the read. Working as intended for this origin.
⚪ UNREACHABLE :
Even a no-cors probe failed - a network, DNS, TLS, or mixed-content issue, not a CORS conclusion.

How it works (and its limits) :
Browsers don't let JavaScript set the Origin header, so CORSair tests whether this page's own origin can read the target , it can't spoof arbitrary origins. This makes it a fast, honest first pass, but it cannot test crafted-origin bypasses like null, suffix matching, or reflected-origin misconfigurations. Those require a server-side tool. CORSair is upfront about this in its own output.

## Usage
1. Open the tool: https://sooryaggokul.github.io/CORSair/
2. Enter the target URL.
3. Click **Test CORS Policy** to see the result.

## ⚠️ Disclaimer
Only test endpoints you own or are explicitly authorized to assess. Unauthorized security testing may be illegal. This tool is for educational and authorized security-assessment purposes only.

---
Built by **SooryaGokul** 🌞
