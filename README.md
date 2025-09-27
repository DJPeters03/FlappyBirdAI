# Flappy Bird --- Q-Learning Simulation

This project is a browser-based **Flappy Bird clone powered by
Q-Learning**. Instead of a single player bird, multiple agents learn
over generations to improve survival and pipe-passing scores.

The implementation is entirely self-contained in a single HTML file with
embedded JavaScript and CSS --- no external dependencies are required.

------------------------------------------------------------------------

## 🎮 Features

-   **Q-Learning Agents**
    -   20 birds train together using a shared Q-table.\
    -   Discretized states: horizontal distance to next pipe, vertical
        offset from gap, and velocity.\
    -   Actions: *flap* or *do nothing*.
-   **Customizable Training Parameters (left panel)**
    -   **Exploration ε (epsilon):** chance of random action
        (exploration).\
    -   **Learning Rate α (alpha):** weight given to new experience.\
    -   **Discount γ (gamma):** how far ahead rewards are considered.\
    -   **Pace:** number of simulation steps per animation frame.
-   **Reward System (fully adjustable)**
    -   **Pass Pipe Reward:** bonus for successfully passing a pipe.\
    -   **Alive Step Reward:** small reward/penalty each frame
        survived.\
    -   **Crash Penalty:** negative reward when colliding with ground,
        ceiling, or pipe.
-   **Game World**
    -   Fit-to-view single canvas shows the entire world.\
    -   Pipes have **fixed openings of 200px**, always within playable
        bounds.\
    -   Unique pipe IDs ensure accurate pass counting.
-   **Controls & Options**
    -   Start, Pause, Reset buttons.\
    -   Toggle rendering (for faster training).\
    -   Human control option: press **Space** to flap manually.
-   **Live Stats (right panel)**
    -   Current generation.\
    -   Best score ever achieved.\
    -   Rolling average score over the last 100 runs.\
    -   Number of Q-states explored.\
    -   Alive vs total agents.\
    -   Leader's score in the current generation.

------------------------------------------------------------------------

## 🚀 How to Run

1.  Download or clone the project.\
2.  Open `FlappyBird.html` in any modern browser (Chrome, Firefox,
    Safari, Edge).
    -   No installation or build steps are required.

------------------------------------------------------------------------

## 🧠 How It Works

-   Each frame, every agent chooses an action (`flap` or `do nothing`)
    based on its **policy**:
    -   With probability ε (epsilon), it explores randomly.\
    -   Otherwise, it exploits the best known action from the Q-table.\
-   After stepping the environment, rewards are assigned:
    -   Passing a pipe, staying alive, or crashing.\
-   The Q-table updates using the standard Q-learning rule:

\[ Q(s,a) `\leftarrow `{=tex}Q(s,a) +
`\alpha `{=tex}`\Big[r + \gamma \max_{a'}Q(s',a') - Q(s,a)\Big]`{=tex}\]

-   When all agents die, a **new generation** begins and learning
    continues with accumulated experience.

------------------------------------------------------------------------

## 📊 Tips for Experimentation

-   **Faster Training:** Increase *pace* or disable rendering.\
-   **Exploration vs Exploitation:** Start with higher ε (0.2--0.3),
    then lower it over time.\
-   **Rewards Tuning:**
    -   Too harsh a crash penalty can discourage risk-taking.\
    -   Too small pass rewards make survival unmotivated.\
-   **Observe Generations:** Watch how the best score improves as
    generations pass.

------------------------------------------------------------------------

## 📂 File Structure

-   `FlappyBird.html` --- contains:
    -   Embedded CSS (UI & layout).\
    -   Left control panel & right game canvas.\
    -   JavaScript engine for environment, Q-learning loop, and
        rendering.

------------------------------------------------------------------------

## 📜 License

This project is open for personal, educational, and research use.\
Feel free to experiment, modify, and extend it.
