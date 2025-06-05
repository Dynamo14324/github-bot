# How to Use the GitHub Contribution Bot

This guide explains how to use the script in the `Dynamo14324/github-bot` repository to populate your own GitHub contribution graph with past-dated commits.

**Disclaimer:** This script modifies your repository's commit history significantly. Use it with caution and preferably on a dedicated repository.

## Prerequisites

1.  **Git:** Ensure Git is installed on your system. ([Download Git](https://git-scm.com/downloads))
2.  **Node.js:** Ensure Node.js (which includes npm) is installed. ([Download Node.js](https://nodejs.org/))
3.  **GitHub Account:** You need a GitHub account.
4.  **Verified Email:** You must know an email address that is registered and verified with your GitHub account. Contributions are only counted if the commit email matches a verified email on your account.
5.  **GitHub Personal Access Token (PAT):** It's recommended to create a PAT with the `repo` scope (for full control of private repositories) to authenticate Git operations securely, especially for pushing. ([Create a PAT](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic))

## Steps

1.  **Clone the Repository:**
    Open your terminal or command prompt and clone the repository:
    ```bash
    git clone https://github.com/Dynamo14324/github-bot.git
    cd github-bot
    ```

2.  **Install Dependencies:**
    Install the necessary Node.js packages:
    ```bash
    npm install
    ```

3.  **Configure Your Email:**
    *   Open the `index.js` file in a text editor.
    *   Find the line that configures the Git user email (around line 16):
        ```javascript
        await git.raw(["config", "user.email", "'yogeshjadhavfyjc@gmail.com'"]); 
        ```
    *   **IMPORTANT:** Replace `'yogeshjadhavfyjc@gmail.com'` with **your own verified GitHub email address**, keeping the single quotes around it.
    *   You can also update the `user.name` on the line above if desired.

4.  **Configure Authentication (Recommended: PAT):**
    *   The script currently includes a token directly in the push URL (line 58). **This is not secure.**
    *   **Recommended:** Remove the token from the URL in `index.js`:
        ```javascript
        // Change this:
        const remote = `https://REMOVED_TOKEN@github.com/Dynamo14324/github-bot.git`;
        // To this (replace USERNAME with your GitHub username):
        const remote = `https://github.com/USERNAME/github-bot.git`; 
        ```
    *   Then, configure Git to use your PAT for authentication when pushing. You can do this globally or use credential helpers. Alternatively, when Git prompts for username/password during the push, use your GitHub username and your PAT as the password.

5.  **Run the Script:**
    Execute the script from the `github-bot` directory:
    ```bash
    node index.js
    ```
    *   The script will start generating ~365 commits with random dates from the past year.
    *   It will configure the local Git user, make commits locally, and then attempt to push them all to the `main` branch of the repository specified in the script (currently `Dynamo14324/github-bot`).
    *   **Note:** If you want to push to *your own fork* or a different repository, you'll need to update the remote URL in the `index.js` script (line 58 or as modified in step 4) and potentially the repository path (`repoPath` variable on line 8).

6.  **Verify:**
    *   Wait for the script to finish (it will print "All commits pushed successfully.").
    *   Check your GitHub profile page. It might take a few minutes for the contribution graph to update.

By following these steps and ensuring you use your verified email, the generated commits should appear on your contribution graph.
