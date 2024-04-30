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

# Prompt the user to input text
input_text = input("Enter the Malayalam text to transliterate: ")

# Preprocess the input text
input_sequence = source_tokenizer.texts_to_sequences([input_text])
input_sequence_padded = pad_sequences(input_sequence, maxlen=max_seq_length, padding='post')

# Generate predictions
predicted_sequence = model.predict(input_sequence_padded)

# Decode the predicted sequence
predicted_text = "".join(target_tokenizer.index_word[i] for i in np.argmax(predicted_sequence, axis=-1)[0] if i != 0)

print("Input Text:", input_text)
print("Predicted Transliteration:", predicted_text)
