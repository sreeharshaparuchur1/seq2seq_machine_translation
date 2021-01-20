# seq2seq_machine_translation

## Architecture
The Attention based architecture performs better on longer sequences than the classical,
end-to-end encoder-decoder based Seq2Seq network. The translation is done from the English corpus to the Hindi corpus.

## Data Cleaning
When dealing with data, the most important thing to do is to "standardise" it. 
Essentially, data has to be preprocessed so that there are no anomalities present (which could lead to poor testing results).

We follow the following steps to "clean" our data:
- converting our english data into lower case.
- replace english contractions with the help of a dictionary
- Remove extra spaces and non-printable symbols / numbers.

SpaCy tokenising was used and the words were embedded into a 300-dimensional embedding.

## Procedure and Observations
- Batch size = 32
- Adam optimizer
- CrossEntropyLoss as the loss function

The models were trained for a certain number of epochs (note that a single epoch took longer in the attention model as there are more learnable parameters)
and were only saved when the validation loss decreased. This is done to prevent overfitting the model to the test data.

While the translations obtained aren't exact, the mis-translated words still hold onto the context of the sentence.
The Encoder-Decoder architecutre didn't perform too poorly owing to the multi-layered approach taken. The Attention model uses a single-layered decoder.

The models aren't perfect but can be improved by using [beam search](https://medium.com/@dhartidhami/beam-search-in-seq2seq-model-7606d55b21a5) instead of greedy decoding.
