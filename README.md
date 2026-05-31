
# 🚀 Nenvi — Node Runner GitHub Action  
Run a Node.js application inside GitHub Actions with a specified **entry file** and **port**.

Nenvi is a lightweight composite action designed for workflows that need a running Node server — perfect for integration tests, API checks, webhooks, and CI pipelines that depend on a live backend.

---

## ✨ Features

- 🔧 **Simple configuration** — just provide `entry_file` and `port`
- 🚀 **Starts your Node app automatically** in the background
- 🌐 **Exposes the port** for the rest of the workflow
- 🧹 **Graceful, automatic backgrounding** using `nohup`
- 🖥️ **Works on all runners**: Linux, macOS, Windows
- 📦 **Framework‑agnostic** — Express, Fastify, Koa, custom HTTP servers, anything

---

## 📥 Inputs

| Name | Description | Required | Default |
|------|-------------|----------|---------|
| `entry_file` | Path to the Node.js entry file. | **Yes** | `index.js` |
| `port` | Port to run the server on. | **Yes** | `3000` |

---

## 🚀 Usage Example

```yaml
name: Run Node App

on:
  workflow_dispatch:

jobs:
  node-server:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v4

    - name: Set up Node
      uses: actions/setup-node@v4
      with:
        node-version: 20

    - name: Start Node Server
      uses: bytedeveloping/Nenvi@v1
      with:
        entry_file: "server.js"
        port: 3000

    - name: Test server
      run: curl http://localhost:3000/health
```

---

## 🧪 Example `server.js`

```js
import express from "express";
const app = express();

app.get("/health", (req, res) => res.json({ ok: true }));

app.listen(process.env.PORT || 3000, () =>
  console.log("Server running")
);
```

---

## 🛠️ What This Action Does

When executed, Nenvi:

1. Validates that your entry file exists  
2. Starts your Node.js server in the background  
3. Exposes the specified port  
4. Waits briefly for the server to boot  
5. Leaves the server running for the remainder of the workflow  

This makes it ideal for:

- API integration tests  
- Webhook simulations  
- UI test runners  
- Microservice‑dependent CI pipelines  

---

## 📄 License

MIT License — free for personal and commercial use.
<badges>
<p align="center">

  <!-- Stars -->
  <a href="https://github.com/bytedeveloping/Test_Node/stargazers">
    <img src="https://img.shields.io/github/stars/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Forks -->
  <a href="https://github.com/bytedeveloping/Test_Node/network/members">
    <img src="https://img.shields.io/github/forks/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Watchers -->
  <a href="https://github.com/bytedeveloping/Test_Node/watchers">
    <img src="https://img.shields.io/github/watchers/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Issues -->
  <a href="https://github.com/bytedeveloping/Test_Node/issues">
    <img src="https://img.shields.io/github/issues/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Pull Requests -->
  <a href="https://github.com/bytedeveloping/Test_Node/pulls">
    <img src="https://img.shields.io/github/issues-pr/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- License -->
  <a href="https://github.com/bytedeveloping/Test_Node/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Last Commit -->
  <a href="https://github.com/bytedeveloping/Test_Node/commits/main">
    <img src="https://img.shields.io/github/last-commit/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Repo Size -->
  <a href="https://github.com/bytedeveloping/Test_Node">
    <img src="https://img.shields.io/github/repo-size/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Commit Activity -->
  <a href="https://github.com/bytedeveloping/Test_Node/commits">
    <img src="https://img.shields.io/github/commit-activity/y/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

  <!-- Contributors -->
  <a href="https://github.com/bytedeveloping/Test_Node/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/bytedeveloping/Test_Node?style=for-the-badge" />
  </a>

</p>
</badges>
