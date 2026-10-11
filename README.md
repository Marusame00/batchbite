# 🍔 BatchBite

**A per-meal batch budget calculator.** Find out what each serving of a home-cooked batch really costs.

**▶ Live demo:** https://marusame00.github.io/batchbite/

When you shop, one "anchor" item usually sets the batch size, like a 6-pack of burger patties. BatchBite takes every other ingredient (buns, cheese, sauce, toppings), splits its cost across that batch, and gives you an accurate **cost per serving** and **total batch cost**. It also tracks the value of the leftovers that go back into your pantry.

## ✨ Features

- **Batch anchor:** set a batch name, the number of servings, and the anchor item's name and cost. The anchor's full cost goes to the batch.
- **Add-on ingredients:** add as many items as you need. Each one has two ways to count its cost:
  - **Whole Package:** the batch takes 100% of the package cost.
  - **Partial Use:** the batch takes only the share it uses (for example, 6 of 12 cheese slices = 50% of the cost).
- **Live KPI dashboard:**
  - Cost Per Serving
  - Total Batch Cost
  - Pantry Surplus Value (money spent on groceries that weren't used up in this batch)
- **Cost breakdown bar:** a color-coded stacked bar that shows each ingredient's share of the total.
- **Auto-save:** your current batch is saved in your browser's `localStorage`.
- **Quick actions:** a one-click **Load Burger Example** preset and a **Reset** button.
- **Dark mode UI:** slate palette with emerald accents. Works on desktop and mobile.

## 🚀 Getting Started

There's nothing to install or build. It's one HTML file.

```bash
git clone https://github.com/Marusame00/batchbite.git
cd batchbite
open index.html   # or just double-click it
```

## 🧮 How the Math Works

| Value | Formula |
|---|---|
| Attributed cost (Whole Package) | `package price` |
| Attributed cost (Partial Use) | `package price × (units used ÷ units in package)` |
| Total Batch Cost | `anchor cost + Σ attributed costs` |
| Cost Per Serving | `Total Batch Cost ÷ servings` |
| Pantry Surplus Value | `Σ (package price − attributed cost)` |

## 🛠️ Tech Stack

- HTML5 + vanilla JavaScript
- [Tailwind CSS](https://tailwindcss.com/) (CDN)
- [Lucide Icons](https://lucide.dev/) (CDN)
- Google Fonts: Inter & JetBrains Mono

## 📄 License

[MIT](LICENSE). Use it, fork it, and cook on a budget.
