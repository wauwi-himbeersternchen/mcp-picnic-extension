# Listing All MCP Interfaces

The following two methods can be used to list all MCP interfaces.

---

## 1. stdio

Communicate with `mcp-picnic` (or `.start.sh`) via standard input/output:

```bash
printf '%s\n' \
'{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2025-06-18","capabilities":{},"clientInfo":{"name":"cli","version":"1.0"}}}' \
| mcp-picnic
```

> **Note:** `mcp-picnic` can be replaced with `.start.sh`.

---

## 2. HTTP + curl

Communicate with a local service via HTTP request:

```bash
curl -i http://localhost:3000/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{
    "jsonrpc":"2.0",
    "id":1,
    "method":"initialize",
    "params":{
      "protocolVersion":"2025-06-18",
      "capabilities":{},
      "clientInfo":{
        "name":"curl",
        "version":"1.0"
      }
    }
  }'
```

> **Note:** The service must be running at `http://localhost:3000`.
