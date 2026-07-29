---
tags: config
---

1. `miniflux_host` → Settings → API Keys → Create a new API key → `fluent-reader` → Copy the Token
2. Fluent Reader → Setting → Select a service Service → Miniflux:
	 ```
	 Endpoint: http://127.0.0.1:8070
	 Type: API Key
	 Password: <token>
	 ```