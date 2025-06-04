# 🤖 GitHub Contribution Graph Enhancer (goGreen Fork)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](/LICENSE) [![Node.js CI](https://github.com/Dynamo14324/github-bot/actions/workflows/node.js.yml/badge.svg)](https://github.com/Dynamo14324/github-bot/actions/workflows/node.js.yml) <!-- Placeholder CI Badge -->

Ever wished your GitHub contribution graph looked a bit more... active? Or maybe you want to create some pixel art on your profile? This script, originally inspired by **goGreen**, lets you make commits dated in the past (or future!), effectively painting your contribution graph green.

**Disclaimer:** This tool is intended for creative expression and personal use (e.g., filling in legitimate gaps from offline work, creating profile art). Using it to misrepresent your activity level is discouraged.

## ✨ Features

*   **Backdate Commits:** Create commits for any date to fill your GitHub contribution graph.
*   **Simple Setup:** Easy to configure and run with Node.js.
*   **Customizable:** Modify the script to control commit frequency and patterns.
*   **Creative Potential:** Design patterns or artwork on your contribution graph.

## 🚀 Getting Started

Follow these steps to get started:

1.  **Clone this Repository:**
    ```bash
    git clone https://github.com/Dynamo14324/github-bot.git
    cd github-bot
    ```

2.  **Install Dependencies:**
    Make sure you have Node.js installed. Then run:
    ```bash
    npm install
    ```
    This installs the necessary packages (`moment`, `simple-git`, `jsonfile`, `random`).

3.  **Configure Your Repository:**
    *   This script makes commits *within the cloned repository itself* (`github-bot`).
    *   Ensure you have set your Git user name and email globally or locally for this repository:
        ```bash
        git config user.name "Your Name"
        git config user.email "your.email@example.com"
        ```
    *   **Important:** The script modifies the `data.json` file with each commit. You need to push these changes to *this* repository (`Dynamo14324/github-bot`) for the contributions to appear on your profile graph associated with this repo.

4.  **Run the Script:**
    Execute the script to start making backdated commits:
    ```bash
    node index.js
    ```
    The script will output the dates for which it is creating commits.

5.  **Push Your Changes:**
    After the script finishes (or periodically), push the changes made to `data.json` back to GitHub:
    ```bash
    git add data.json
    git commit -m "feat: Update contribution data" # Or any commit message
    git push origin main # Or your default branch
    ```
    Allow some time for GitHub to update your contribution graph.

## ⚙️ How It Works

Here's a simplified view of the script's workflow:

![Workflow Diagram](./workflow_diagram.png)

The `index.js` script uses:
*   `moment` to handle date calculations.
*   `jsonfile` to read/write commit timestamps to `data.json`.
*   `simple-git` to execute Git commands programmatically (commit).
*   `random` to generate random dates within a specified range (typically the past year).

For each generated date, it modifies the `data.json` file and creates a commit with that specific date using Git environment variables (`GIT_COMMITTER_DATE` and `GIT_AUTHOR_DATE`).

## 🎨 Customization & Ideas

*   **Commit Frequency:** Modify the loop in `index.js` (e.g., the `ITERATION` constant) to control how many commits are generated.
*   **Date Range:** Adjust the `DATE` calculation using `moment` to target specific periods.
*   **Pattern Generation:** Instead of random dates, implement logic to generate dates corresponding to specific patterns or images on the contribution graph.
*   **Target Different Repos:** Adapt the script to make commits in a *different* repository if desired (requires careful path management and Git initialization in the target repo).

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

## 🙏 Acknowledgements

*   Original concept inspired by Akshay Saini's video tutorial.
*   Libraries: `moment`, `simple-git`, `jsonfile`, `random`.

