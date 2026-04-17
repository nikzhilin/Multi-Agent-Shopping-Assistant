# AI Shopping Agents

This project shows a simple shopping assistant built in a notebook. It grows in three steps:

- a tool-calling agent
- an agent with memory
- a multi-agent system for recommendations

The code is in [submission.ipynb](submission.ipynb).

## What it can do

- search products by category, brand, price, and sorting
- add products to a cart
- remember chat context
- save user preferences in a JSON profile
- split a recommendation task between several agents

## Files

- [submission.ipynb](submission.ipynb) - main notebook
- [example.env](example.env) - env template
- [pyproject.toml](pyproject.toml) - project dependencies
- [LICENSE](LICENSE) - MIT license

## Parts of the project

### Tool-calling agent

Uses these tools:

- `search_products`
- `add_to_cart`

Main function:

- `run_shopping_agent(...)`

### Agent with memory

Adds saved user preferences.

Main functions:

- `load_profile(...)`
- `save_profile(...)`
- `update_profile(...)`
- `run_memory_agent(...)`

### Multi-agent system

Uses several small roles:

- one agent finds products
- one writes pros
- one writes cons
- one picks the best option

## Stack

- Python 3.11+
- Jupyter Notebook
- LangChain Core
- `langchain-openai`
- `python-dotenv`

## How to run

Install dependencies:

```bash
pip install -e .
```

or

```bash
pip install langchain-openai langchain-core python-dotenv jupyter
```

Create a local env file:

```bash
cp example.env .env
```

Fill it with your values:

```env
YANDEX_CLOUD_FOLDER=your_folder_id
YANDEX_CLOUD_API_KEY=your_api_key
```

Start the notebook:

```bash
jupyter notebook submission.ipynb
```

## Example prompts

- `Find a coffee machine under 180 dollars with good reviews`
- `I like Logitech and my budget is 90 dollars. Remember that for later`
- `Pick the best gaming mouse under 120 dollars and add it to cart`

## Example MAS response

Prompt:

```text
Pick the best gaming mouse under 120 dollars and add it to cart
```

Example answer:

```text
I checked several gaming mice under 120 dollars.

Best option: Logitech G502 X

Why this one:
- strong sensor and tracking
- comfortable shape for long use
- good feature set for the price

Possible downside:
- heavier than some lightweight esports models

I added Logitech G502 X to your cart.
```

## Notes

- local JSON data is ignored by Git
- `example.env` stays in the repo, but real `.env` files do not
