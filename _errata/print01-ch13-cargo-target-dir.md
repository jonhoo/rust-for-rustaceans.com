---
chapter: 13
page: 229
kind: code
reporter: wezm
date: 2022-02-05
# fixed: 2021-01-01
---
The paragraph on Cargo disk usage suggests setting `[build] target` in your `~/.cargo/config.toml` to use a shared artefacts directory but it should be `[build] target-dir`.
