# 🍽️ ElevateMyDish

Website: https://marcrulo.github.io/MonthlyProjects/food-pairing

ElevateMyDish is a small research project on food pairing. It asks a simple question: given a few starting ingredients, can a graph of food relationships surface sensible additions? The work is inspired by the FlavorGraph dataset and the ideas in the accompanying blog post.

## 🧭 Storyline
FlavorGraph combines recipe co-occurrence with molecular composition to build a heterogeneous network of ingredients and molecules. This project narrows that down to ingredients only and then explores two complementary lenses:

- **Graph structure** for explicit connectivity (shortest paths and minimal connecting subgraphs).
- **Embedding space** for soft similarity (vector averages and cosine ranking).

The main example in the blog uses `tomato`, `pasta`, and `chicken`. The take-away is that graph methods produce interpretable connectors, while embeddings often drift for multi-ingredient mixes. That tension is the red thread of this repo.

## 🧩 What This Repo Does
- Builds an ingredient-only graph from FlavorGraph and cleans edges/nodes.
- Compares weighted vs unweighted connections to expose unintuitive links.
- Uses Steiner trees to connect a set of ingredients with minimal structure.
- Experiments with embedding averaging to propose candidate additions.
- Visualizes the results with Bokeh and optional T-SNE projections.

## 🖼️ Examples From The Blog
These figures show why graph-based pairing can feel interpretable while still being tricky:

![Steiner tree example](https://marcrulo.github.io/MonthlyProjects/assets/images/food_pairing/steiner.png)

The weighted Steiner tree connects `tomato`, `pasta`, and `chicken` by minimizing total similarity cost. The red edges highlight the minimum structure, but the path can look unintuitive because “similarity” weights do not always align with culinary intuition.

![Unweighted stock cube example](https://marcrulo.github.io/MonthlyProjects/assets/images/food_pairing/stock_cube.png)

When weights are ignored, the shortest unweighted connection finds a simple bridge ingredient (`stock cube`). This tends to be more interpretable, but it can oversimplify and ignore how weak or strong the underlying relationships are.

![Cucumber link example](https://marcrulo.github.io/MonthlyProjects/assets/images/food_pairing/cucumber.png)

Adding an unusual ingredient like `kefir` still yields a one-hop bridge (`cucumber`) in the unweighted case, which can make sense via shared dish contexts (e.g., tzatziki or salad dressing). This illustrates how graphs can surface plausible links even when the pairing is not obvious.

## 🗂️ Data Sources
- FlavorGraph dataset: https://github.com/lamypark/FlavorGraph
- FlavorDB reference: https://cosylab.iiitd.edu.in/flavordb/

## ▶️ Run
This repo is research-first. If you want to run the notebook:
1. Create a Python environment (3.13+).
2. Install dependencies from [pyproject.toml](pyproject.toml).
3. Open [src/main.ipynb](src/main.ipynb) in Jupyter or VS Code.
