⚽ World Cup Database

🧑🏽‍💻 A simple PostgreSQL + Bash project I built while learning databases through freeCodeCamp.

🌍 About the Project

This project was part of my SQL learning journey.
I built a PostgreSQL database that stores information about the FIFA World Cup finals (2014 & 2018) — including the teams, match results, and stats.

It helped me understand:

How relational databases work

How to use foreign keys, joins, and aggregate functions

How to automate data imports using Bash scripts

🧱 Database Design

The project has two main tables: teams and games.

🥇 teams
Column	Type	Description
team_id	SERIAL	Primary key
name	VARCHAR(50)	Team name (unique)
⚽ games
Column	Type	Description
game_id	SERIAL	Primary key
year	INT	Year of the match
round	VARCHAR(50)	Tournament round (Final, Quarter-Final, etc.)
winner_id	INT	FK → teams(team_id)
opponent_id	INT	FK → teams(team_id)
winner_goals	INT	Goals scored by winner
opponent_goals	INT	Goals scored by opponent
🧠 What It Can Do

✅ Store data about all World Cup matches from 2014 & 2018
✅ List the champions by year
✅ Show teams that played in a given round
✅ Calculate averages, totals, and other fun stats

⚙️ How to Run It
1️⃣ Create and connect to the database
psql --username=freecodecamp --dbname=postgres


Then inside PostgreSQL:

CREATE DATABASE worldcup;
\c worldcup

2️⃣ Insert the data

Make the script executable:

chmod +x insert_data.sh


Run it:

./insert_data.sh


✅ This will:

Add all 24 unique teams

Insert all 32 games

Reset IDs each time to avoid duplicates

🔍 Sample Queries and Results

Run your queries:

chmod +x queries.sh
./queries.sh


Here are some examples 👇

🏆 Champions by Year
2014|Germany
2018|France

⚽ Average Goals per Game
2.8125000000000000

🇳🇬 Teams in 2014 Eighth-Final
Algeria
Argentina
Belgium
Brazil
Chile
Colombia
Costa Rica
France
Germany
Greece
Mexico
Netherlands
Nigeria
Switzerland
United States
Uruguay

📂 File Structure
.
├── games.csv         # CSV data file
├── insert_data.sh    # Script to populate the database
├── queries.sh        # Script with example queries
├── worldcup.sql      # SQL dump for backup
└── README.md         # You're here!

💾 Backup & Restore

To back up your database:

pg_dump -cC --inserts -U freecodecamp worldcup > worldcup.sql


To restore it later:

psql -U postgres < worldcup.sql

🧩 What I Learned

Setting up and connecting to PostgreSQL databases

Creating relations between tables with foreign keys

Reading and parsing CSV files using Bash

Avoiding duplicate data with TRUNCATE + RESTART IDENTITY

Running aggregate queries to calculate totals and averages

🚀 Future Ideas

Add data for more World Cups (2010, 2022, etc.)

Build a small web dashboard with charts for goals and wins

Connect the database to a Python or Node.js backend

💬 Final Thoughts

This project taught me a lot about SQL logic and data management.
It was a great mix of scripting, database design, and problem-solving — all while exploring something fun like football ⚽.
