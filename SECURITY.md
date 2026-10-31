# security policy

## reporting vulnerabilities

the mit-museum-brain project and its web application (`letters-mit-museum-brain.web.app`) prioritize client confidentiality, data integrity, and responsible engineering.

if you discover a potential vulnerability, security flaw, or bug that could be used maliciously, please report it responsibly:

- **contact**: Erick Oduniyi (`eeoduniyi@gmail.com`)
- **subject**: `[security] mit-museum-brain vulnerability report`

please provide:
1. a clear description of the vulnerability and its potential impact.
2. step-by-step instructions or proof-of-concept to reproduce the behavior.
3. any proposed remediation or patch if available.

we will investigate, verify, and resolve confirmed vulnerabilities promptly before public disclosure.

---

## client-side threat model & protections

1. **content security policy (csp)**:
   strict http headers enforce origin boundaries on scripts, styles, media, and connections, preventing cross-site scripting (xss) and data exfiltration.

2. **subresource integrity (sri)**:
   all external runtime dependencies (`p5.js`, `onnxruntime-web`) are pinned using sha-384 cryptographic checksums, guaranteeing that tampered or compromised cdn assets are rejected by browsers.

3. **clickjacking protection**:
   `X-Frame-Options: DENY` and `frame-ancestors 'none'` prevent the web application from being hosted within unauthorized iframes or deceptive overlays.

4. **permissions policy**:
   hardware features such as cameras, microphones, payments, and geolocation are explicitly blocked at the http header level (`camera=(), microphone=(), geolocation=(), payment=()`).

5. **offline zero-taint ingestion**:
   museum photographs and feature vectors are bundled via base64 data uris inheriting local document contexts, preventing canvas-taint vulnerabilities and cross-origin tracking.

