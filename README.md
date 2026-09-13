# Claw Cryptics --- Streamlit

A browser-based maze and word-hunt game built with **Streamlit,
HTML/CSS, and JavaScript**.

Play as a green dog, explore the maze, collect treasure chests
containing scrambled letters, avoid the dinosaur, and solve the hidden
answer.

Answers may be in **Slovak or English** and can be a **word, phrase,
name, place, or brand**.

## Main features

-   Random word / phrase selection
-   Treasure chests with scrambled letters
-   Dinosaur chase
-   Multiple maze orientations
-   IN / OUT portals with different shapes
-   Keyboard and mobile controls
-   Pause / resume
-   Hints
-   Win fireworks
-   Player selection
-   Shared Supabase scoreboard
-   Tracks games, wins, and different solved words
-   Optional **New words only** mode
-   Responsive layout:
    -   desktop: scoreboard beside the playground
    -   mobile: scoreboard below the playground

## Files

-   `app.py` --- main Streamlit app and browser game
-   `ClawCryptics.jpg` --- welcome-screen image; keep it beside `app.py`
-   `requirements.txt` --- Python dependencies
-   `.streamlit/secrets.toml` --- local Supabase configuration (**do not
    upload this file to GitHub**)

## Local run

Install the requirements:

``` bash
pip install -r requirements.txt
```

Then start the app:

``` bash
streamlit run app.py
```

## Supabase setup

Claw Cryptics uses Supabase to store the shared player scoreboard.

The player table stores:

-   player name
-   games played
-   wins
-   different correctly solved words

The app reads the Supabase connection details from Streamlit Secrets.

For local testing, create:

``` text
.streamlit/secrets.toml
```

and add:

``` toml
SUPABASE_URL = "YOUR_SUPABASE_PROJECT_URL"
SUPABASE_ANON_KEY = "YOUR_SUPABASE_PUBLISHABLE_KEY"
```

Use only the **public / publishable key** in the game.

**Never put a Supabase secret or service-role key in the browser game or
GitHub repository.**

## Streamlit Community Cloud

1.  Push the project files to GitHub.
2.  Create a Streamlit Community Cloud app from the repository.
3.  Set the main file path to `app.py`.
4.  Open the app's **Settings → Secrets**.
5.  Add:

``` toml
SUPABASE_URL = "YOUR_SUPABASE_PROJECT_URL"
SUPABASE_ANON_KEY = "YOUR_SUPABASE_PUBLISHABLE_KEY"
```

6.  Save the secrets and reboot the app if Streamlit requests it.

## Welcome image

Keep the image named exactly:

``` text
ClawCryptics.jpg
```

in the same repository folder as `app.py`.

The app converts the image to a data URI so it can also be displayed
inside the Streamlit game component.

## Controls

**PC**

-   Arrow Keys / WASD --- move
-   SPACE --- pause / resume
-   ENTER --- start a new game after the end screen

**Mobile**

-   Use the on-screen directional controls.

## Game goal

1.  Choose an existing player or create a new one.
2.  Move through the maze as the green dog.
3.  Collect every treasure chest before the dinosaur catches you.
4.  Each chest reveals one scrambled character.
5.  Use the collected characters and optional hint to solve the hidden
    answer.
6.  Correct answers increase the player's wins and solved-word count in
    Supabase.

## Important

Do not commit real Streamlit secrets to GitHub.

A `.gitignore` should include:

``` gitignore
.streamlit/secrets.toml
```

The Supabase **publishable key** is designed for client-side use, but
database access should still be controlled with appropriate Supabase Row
Level Security (RLS) policies.
