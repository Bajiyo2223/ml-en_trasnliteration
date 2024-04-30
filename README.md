# Malayalam to English Transliteration

## Overview

This repository contains code for a Malayalam to English transliteration model. The model is trained to transliterate Malayalam words into English.

## Dataset

The training and testing data are located in the `datasets` folder. Before training the model, it's recommended to clean the dataset. The code for cleaning the dataset is provided in the uploaded code.

## Training

To train the model, follow these steps:

1. Ensure the dataset is cleaned.
2. Run the training script, which includes tokenization and model training.
3. After training, the tokenizers and model can be saved into a particular folder. You can change the path as per your need.

## Usage

Once the model is trained and saved, you can load the saved files to run the code. Here's how to use the trained model:

1. Load the saved tokenizers and model from the specified folder.
2. Use the loaded tokenizers to preprocess the input data.
3. Feed the preprocessed data into the loaded model for transliteration.

## Example Code

```python
# Load tokenizers and model
source_tokenizer = Tokenizer.from_file("path/to/source_tokenizer_config.json")
target_tokenizer = Tokenizer.from_file("path/to/target_tokenizer_config.json")
model = load_model("path/to/saved_model")

# Preprocess input data
input_data = preprocess_data(input_text, source_tokenizer)

# Transliterate using the model
output_data = model.transliterate(input_data)

# Display results
print("Input:", input_text)
print("Output:", output_data)
