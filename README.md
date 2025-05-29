# PersonalPokemonShowdownBot
This project builds a machine learning model that plays Pokémon Showdown battles by mimicking your personal playstyle. The model is trained on your battle logs and predicts actions (e.g., "move Thunderbolt", "switch Tyranitar") based on the current state of the game.
## Features

- Parses battle logs from Pokémon Showdown format
- Extracts turn-by-turn state and corresponding player actions
- Trains a text-sequence model to predict moves based on historical context
- Reaches over 70% accuracy on test data
- Designed for eventual deployment on a personal website or game simulation

## Project Structure

- data/ — Folder containing raw battle logs
- models/ — Trained model weights and saved tokenizers
- scripts/ — Python scripts for parsing, training, and inference
- notebook/ — Optional Jupyter notebooks for prototyping and EDA

## Getting Started

### 1. Clone the repository

git clone https://github.com/yourusername/PersonalPokemonShowdownBot.git
cd PersonalPokemonShowdownBot

### 2. Install dependencies
Create a virtual environment and install required packages:

Copy
Edit
pip install -r requirements.txt

### 3. Parse battle logs
bash
Copy
Edit
python scripts/parse_logs.py --log_dir data/DoubleBattleLogs --output parsed_data.pkl

### 4. Train the model
bash
Copy
Edit
python scripts/train_model.py --data parsed_data.pkl

### 5. Make predictions (optional)
bash
Copy
Edit
python scripts/predict_move.py --input "Turn 5 opponent move Draco Meteor switch Garchomp"

## Model Architecture
The model uses a Transformer-based encoder architecture to classify battle contexts into user-like actions:

- **Tokenizer:** Keras Tokenizer on raw battle logs to convert states into integer sequences.
- **Sequence encoder:** Embedding layer followed by Transformer encoder blocks.
- **Output layer:** Softmax over the set of unique actions (e.g., moves and switches taken during battles).

This allows the model to attend to the entire battle history and capture complex dependencies between actions.

## Future Work
Train a reinforcement learning opponent to counter the imitation model

Integrate with a front-end web interface for interactive battles

Improve state representation with additional game mechanics (HP, boosts, weather)
