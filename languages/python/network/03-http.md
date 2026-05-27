# 51 - HTTP Client API (PRO)

Definition: Fetching data from the web.

## 1. Modern Path (3.12+ / Idiomatic)
Using `httpx` or `aiohttp` (Note: External but standard for Modern devs).

```python
# httpx.get("https://google.com")
```

## 2. Systems Path (Internals / C-Interop)
Using `urllib.request` (The low-level stdlib way).

```python
import urllib.request
with urllib.request.urlopen('http://python.org') as response:
   html = response.read()
```

## 3. Portable Path (Zero-Dependency)
Basic request handling.

```python
import http.client
conn = http.client.HTTPSConnection("www.python.org")
```

## 4. Strict Path (Type-Hinted)
Typed HTTP responses.

```python
from http.client import HTTPResponse
def fetch() -> HTTPResponse: pass
```

# The Logic Bridge
// Logic: Most high-level Python HTTP clients are wrappers around the C `libcurl` or the Python `http.client` stdlib. They handle DNS resolution, TLS handshakes, and connection pooling automatically.
