# 5-Day-Kaggle-GenAI

- Core of the LLM:
  - What they are made of
  - How do they evolve
  - How they actually learn
- The foundation of most modern llms is the Transformer architecture.
- It came from the Google Project focused on language translation in 2017.
  - The original transformer has an encoder and decoder.
  - Take a sentence in one language and turn it into another language.
  - The encoder will take the input like sentence in one language -> create its representation of it like summary of the meaning -> then decoder uses that representation to generate the output -> translated piece by piece called as token
  - Magic happens inside each layer of this Transformer
    - First Input text need to preepped for the model -> Turn text into tokens based on specific vocabulary the model uses.
    - Each of these tokens gets turned into a dense vector called an Embedding.
      - That captures the meaning of that token.
    - The transformer processes all the tokens at the same time.
      - So we need to add in some information about the order in which they appeared in the sentences - This is called Positional encoding.
      - There are different types of Positional Encoding, like **Sinodal** and **Learned** encodings.
      - The choice can affect how well the model understands longer sentences or longer text sequences.
        - Positioning is imp - Otherwise it is like throwing all the words in a bag we loose all the structure.
      - Then we think for the **Multi-Head attention**  - Brain of transformer.
        - Famous Ex - Thirsty Tiger a classic so the sentence is "The tiger jumped out of the tree to get a drink because it was thirsty."
      - Self-Attention Mechanism
        - It does this by creating the key value pair vector query for every single word.
        - The **key** is like a **label attached to each word** - what it represents.
        - The **Value** represents the actual information the word carries.
        - The model calculates the score of how well each query matches up with all other keys.
        - Then it normalizes these scores, and they become **Attention weights**.
        - These weights tell us how much each word should pay attention to others.
        - Then it uses those weights to create a weighted sum of all the value vectors.
        - We get the Rich representation for each words which takes into accounts its relationship to every other word in the sentence.
      - All this comparison and calculation happen in parallel using these metrics for the query **Key k and Values v** of all the tokens.
      - This ability to process all these relationships simultaneously is a huge reason why Transformers are so good at capturing these subtle meanings in language that previous models like **SEQUENTIAL** struggled with, especially across longer distances within the sentences. 
      - Multi-Edges doing the self-attention thing serveral times at the same time but with different sets of those query key and value matrices.
      - Each of these parallel self-attention/head processes learns to focus on different types of relationships
        - One head might look for grammatical stuff,
        - Another one might focus on the meaning connection between words and by combining all those different views/prespective the model gets this much deeper understanding of what's going on in the text.
          - Like second opinion, third or fourth.
  - Layer Normalization & Residual Connection :
    - Layer Normalization: 
      - These are important for keeping the training on track when we have deep networks.
      - It also helps to keep the activity level of each layer/activation at a steady level that makes the training go much faster.
        - Also gives the better result in the end. 
    - Residual connection acts like a shortcut within the network, letting the original input layer bypass everything and get added directly to the output.
      - It is a way for the network to remember what it learned earlier, even if it's gone through many, many layers.
      - Important in case of Deep Models.
      - It prevents the **Vanishing Radiance Problem** where the signal gets weaker and weaker as it goes deeper.
   - After that, we have the **Feed Forward Layer**:
     - Applied to each token;s representation seperately after we have done all the attention things.
     - It usually has two linear transformations with non-linear activation functions in between, like **relu or gelu**.
     - This gives the model even more power to represent information and helps it learn these complex functions of the input.
  - We have seen the encoders and decoder in the original transformer design But Newer LLMs they're going with the decoder only architecture.
    - When we focus on generating texts like writing or having conversation, **we don't always need the encoder part**.
    - **Encoder main job is to create the representation of the whole input sequence upfront.**
    - Decoder models skip that step and directly generate the output token by token.
    - They use a special type of **Self-Attention** called **Masked Self-Attention**.
      - It is a way to make sure that when the model is predicting the next token, it can only see the token that came before.
      - Just like when we write or speak.
    - SIMPLE DESIGN FOR GENERATING TEXT.
  - MOE - Mixture of Experts
    - Clear way to make these models even bigger but without making them super slow.
  - HOW WE MAKE THESE MASSIVE MODELS MORE EFFICIENT
    - MOE is the key part of that.
    - In MOE, we have these specialized submodels - experts, and they all live within one big model.
    - There is a gatting network that decides which experts are the best ones to use for the each input.
    - We might have the model with billions of parameters, but for any given input, only a small fraction of those parameters/experts are actually active.    























