# Relnote Extractor
[![PyPI version](https://badge.fury.io/py/relnote-extractor.svg)](https://badge.fury.io/py/relnote-extractor)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Downloads](https://static.pepy.tech/badge/relnote-extractor)](https://pepy.tech/project/relnote-extractor)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue)](https://www.linkedin.com/in/eugene-evstafev-716669181/)


Extract and structure release notes from software update announcements

[![GitHub](https://img.shields.io/github/v/tag/chigwell/relnote-extractor)](https://github.com/chigwell/relnote-extractor)
[![PyPI](https://img.shields.io/pypi/v/relnote-extractor)](https://pypi.org/project/relnote-extractor/)

## Overview

This package is designed to extract and structure release notes from software update announcements. It takes raw text containing software release information as input and processes it to identify and format key details such as version numbers, release dates, new features, bug fixes, and other relevant updates.

## Features

* Extracts and structures release notes from software update announcements
* Supports multiple language models via `langchain` library
* Can use default `ChatLLM7` from `langchain_llm7` library or user-provided LLM instance
* Allows users to pass their own API key for higher rate limits (LLM7 free tier sufficient for most use cases)
* Easy to use and integrate into existing workflows

## Installation

```bash
pip install relnote_extractor
```

## Example Usage

```python
from relnote_extractor import relnote_extractor

user_input = """
Release Notes:

* Fixed issue with XYZ
* Added feature ABC
* Updated to version 1.2.3
"""

response = relnote_extractor(user_input)
print(response)
```

## Input Parameters

* `user_input`: str - the user input text to process
* `llm`: Optional[BaseChatModel] - the langchain LLM instance to use (default: `ChatLLM7` from `langchain_llm7`)
* `api_key`: Optional[str] - the API key for LLM7 (default: `None`)

## Using a Different LLM

You can safely pass your own LLM instance based on https://docs.langchain.com/llm.html if you want to use another LLM. For example, to use the OpenAI LLM:

```python
from langchain_openai import ChatOpenAI
from relnote_extractor import relnote_extractor

llm = ChatOpenAI()
response = relnote_extractor(user_input, llm=llm)
```

Similarly, you can use the Anthropic or Google Generative AI LLMs:

```python
from langchain_anthropic import ChatAnthropic
from relnote_extractor import relnote_extractor

llm = ChatAnthropic()
response = relnote_extractor(user_input, llm=llm)
```

```python
from langchain_google_genai import ChatGoogleGenerativeAI
from relnote_extractor import relnote_extractor

llm = ChatGoogleGenerativeAI()
response = relnote_extractor(user_input, llm=llm)
```

## Rate Limits

The default rate limits for LLM7 free tier are sufficient for most use cases of this package. If you need higher rate limits, you can pass your own `api_key` via environment variable `LLM7_API_KEY` or via passing it directly like `relnote_extractor(user_input, api_key="your_api_key")`. You can get a free API key by registering at https://token.llm7.io/

## GitHub Issues

https://github.com/chigwell/relnote-extractor/issues

## Author

Eugene Evstafev (<hi@eugene.plus>)