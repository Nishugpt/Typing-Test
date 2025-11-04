# Type-Tech
# 🏆 Type-Tech: The Tech Typing Challenge

Type-Tech is a web-based typing application designed specifically for developers, students, and tech enthusiasts. It helps you improve your typing speed and accuracy by practicing with tech-related facts, common code snippets, and programming symbols.

This project is built with HTML, vanilla JavaScript, and Tailwind CSS, using Chart.js for data visualization. All progress is saved locally using `localStorage`.

![Screenshot of Type-Tech interface](<#Link to a screenshot of your app>)
*(**Action required:** Take a screenshot of your app and upload it to your repo, then replace this text with the link.)*

## ✨ Key Features

* **Multiple Game Modes:**
    * **Snippets:** Practice short tech facts and code lines.
    * **Tech Rush:** A 30-second timed challenge with longer paragraph-style tech facts.
    * **Symbol Sprint:** A 30-second timed challenge focused on common programming symbols (`()`, `{}`, `=>`, `!==`).
    * **Workout:** A custom-generated test that targets your most common mistakes.
* **Performance Analytics:**
    * **Core Metrics:** WPM, Accuracy, Consistency, and a final "Tech Score."
    * **Live WPM Chart:** See your speed fluctuate in real-time during a test.
    * **Progress History:** Your past 20 games are saved and visualized in a historical performance chart.
    * **Error Analysis:** Highlights your most common character mistakes after each round.
    * **Keystroke Analysis:** Shows your fastest and slowest typed key pairs (digraphs).
* **Persistent Tracking:**
    * **Activity Streak:** Tracks your consecutive practice days.
    * **Achievements:** Unlock trophies for milestones like high WPM, perfect accuracy, and maintaining a streak.
    * **Local Storage:** All history and achievements are saved in your browser.
* **Custom Practice:**
    * A modal allows you to paste in your own text or code to practice.
* **Modern UI:**
    * Built with Tailwind CSS.
    * Includes a dark mode that respects your system preferences.

## 💻 Tech Stack

* **HTML5**
* **Tailwind CSS** (via CDN)
* **Vanilla JavaScript (ES6+)**
* **Chart.js** (via CDN)
* **`localStorage`** for data persistence

---

## ⚠️ Brutally Honest Critique & Actionable Plan

This project's weakness is its structure. All HTML, CSS, and JavaScript live in a **single `index.html` file.** This is not maintainable, scalable, or professional. The feature logic is good, but the architecture is nonexistent.

Here is your immediate refactoring plan to turn this from a "single-file demo" into a "real portfolio project."

### Your 4-Step Refactoring Plan:

1.  **Separate Concerns (The 5-Minute Fix)**
    * Create a `script.js` file. Cut ALL the JavaScript (the `<script>` block) and paste it there.
    * Create a `style.css` file. Cut ALL the CSS (the `<style>` block) and paste it there.
    * In your `index.html`, link them properly in the `<head>`:
        ```html
        <link rel="stylesheet" href="style.css">
        <script src="script.js" defer></script>
        ```

2.  **Separate Your Data**
    * Your `snippets`, `paragraphSnippets`, and `symbolSnippets` arrays are hard-coded in your main script.
    * Create a new file called `data.js`. Move all three arrays into it.
    * In your `index.html`, load this file *before* your main script:
        ```html
        <script src="data.js"></script>
        <script src="script.js" defer></script>
        ```
    * **Better:** Learn to use the `fetch` API to load this data from a separate `snippets.json` file.

3.  **Break Up Your Monolithic Script**
    * Your `script.js` file is one giant, 1000-line script. This is unmanageable.
    * Your logic is already grouped by features. Use that to your advantage.
    * Create a `modules` folder and break your code into ES6 Modules.
        * `game.js`: Logic for starting, running, and ending the game (`handleTyping`, `endGame`, `timer`).
        * `ui.js`: Logic for updating the DOM (`updateStats`, `renderHistory`, `displayErrorAnalysis`).
        * `charts.js`: All `Chart.js` configuration and update functions (`renderHistoryChart`, `renderLiveWpmChart`).
        * `achievements.js`: Logic for achievements (`checkAchievements`, `renderAchievements`).
        * `main.js`: Your main file that imports from the others and adds the event listeners.

4.  **Manage Your Dependencies (The "Pro" Step)**
    * You're using CDNs for Tailwind and Chart.js. This is for hobbyists.
    * Initialize `npm` in your project (`npm init -y`).
    * Install your dependencies properly:
        ```bash
        npm install tailwindcss chart.js
        ```
    * Set up Tailwind to scan your HTML/JS files for classes and build a minimal CSS file. This is the standard, professional way to use Tailwind.
