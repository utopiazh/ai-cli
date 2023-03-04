

# AI Tools for chatGPT

This CLI tool allows you to easily use chatGPT in the command line. You can chat with it, ask it questions, and even have it translate text. Plus, 
it supports Markdown rendering in the terminal. 

[中文](README.zh.md) | [English](README.md) | [日本語](README.ja.md)

## Quick Start (No Installation Required)

```bash
curl https://raw.githubusercontent.com/yufeikang/ai-cli/main/ai.py -L -s | python - ask "Hello"
```

## Installation

```bash
curl https://raw.githubusercontent.com/yufeikang/ai-cli/main/ai.py -L -s> /usr/local/bin/ai && chmod +x /usr/local/bin/ai && pip install -U rich 
openai
```

## Usage

Ask a Question

```bash
ai ask "Hello"
# no stream mode
ai --no-stream ask "Hello"
# help
ai ask --help
```

![](./_/video/ask.gif)

Translation

```bash
ai translate "Hello"
ai translate "Hello" -t japanese
ai translate -t english -f "file.txt"
echo "Hello" | ai translate -t english
cat "file.txt" | ai translate -t english
```

![](./_/video/translate.gif)

Chatting

```bash
ai chat
```

![](./_/video/chat.gif)

## Dependencies

```bash
pip install rich openai
```

* Proxy Support

Support for environment variables `HTTP_PROXY` and `HTTPS_PROXY` or `ALL_PROXY`. You can also specify a proxy using the `--proxy` parameter.

For example:

```bash
export HTTP_PROXY=http://x.x.x.x:xxxx
# or
export HTTPS_PROXY=https://x.x.x.x:xxxx
```

SOCKS5 proxies are also supported, for example:

```bash
export ALL_PROXY=socks5://x.x.x.x:xxxx
```

SOCKS5 proxies require the installation of `pip install pysocks`.

* OPENAI_API_BASE (Optional)
If you cannot access `https://api.openai.com` due to the GFW, you can specify another API address through the `OPENAI_API_BASE` environment 
variable. It is recommended to use this method instead of using a proxy. It is more stable than using a proxy.
You can refer to this article on how to use Cloudflare workers to build a proxy for the OpenAI API: [Using Cloudflare Workers to Build OpenAI API 
Proxies](https://github.com/noobnooc/noobnooc/discussions/9).

* OPENAI_API_KEY
You can set the environment variable `OPENAI_API_KEY`, or specify it through the `--api-key` parameter.