# Sentiment in text

- Removing Stopwords
```ruby
def remove_stopwords(sentence):
    # List of stopwords
    stopwords = ["a", "about", "above", "after", "again", "against", "all", "am", "an", "and", "any", "are", "as", "at", "be", "because", "been", "before", "being", "below", "between", "both", "but", "by", "could", "did", "do", "does", "doing", "down", "during", "each", "few", "for", "from", "further", "had", "has", "have", "having", "he", "he'd", "he'll", "he's", "her", "here", "here's", "hers", "herself", "him", "himself", "his", "how", "how's", "i", "i'd", "i'll", "i'm", "i've", "if", "in", "into", "is", "it", "it's", "its", "itself", "let's", "me", "more", "most", "my", "myself", "nor", "of", "on", "once", "only", "or", "other", "ought", "our", "ours", "ourselves", "out", "over", "own", "same", "she", "she'd", "she'll", "she's", "should", "so", "some", "such", "than", "that", "that's", "the", "their", "theirs", "them", "themselves", "then", "there", "there's", "these", "they", "they'd", "they'll", "they're", "they've", "this", "those", "through", "to", "too", "under", "until", "up", "very", "was", "we", "we'd", "we'll", "we're", "we've", "were", "what", "what's", "when", "when's", "where", "where's", "which", "while", "who", "who's", "whom", "why", "why's", "with", "would", "you", "you'd", "you'll", "you're", "you've", "your", "yours", "yourself", "yourselves" ]
    
    # Sentence converted to lowercase-only
    sentence = sentence.lower()
    
    ### START CODE HERE
    sentence = sentence.split()
    sentence = [w for w in sentence if not w in stopwords]
    sentence = ' '.join(sentence)
    ### END CODE HERE
    return sentence
```
- Reading the raw data
- Using the Tokenizer
```ruby
def fit_tokenizer(sentences):
    ### START CODE HERE
    # Instantiate the Tokenizer class by passing in the oov_token argument
    tokenizer = Tokenizer(oov_token="<OOV>")
    # Fit on the sentences
    tokenizer.fit_on_texts(sentences)
    ### END CODE HERE
    return tokenizer
    
def get_padded_sequences(tokenizer, sentences):
    
    ### START CODE HERE
    # Convert sentences to sequences
    sequences = tokenizer.texts_to_sequences(sentences)
    
    # Pad the sequences using the post padding strategy
    padded_sequences = pad_sequences(sequences, padding='post')
    ### END CODE HERE
    
    return padded_sequences
```
