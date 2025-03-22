# CODECRAFT_GA_03
# Trains a Markov model based on the data in training_data_file
def train_markov_model():
    for line in open(training_data_file):
        tokens = remove_punctuation(line.rstrip().lower()).split()
        tokens_length = len(tokens)
        for i in range(tokens_length):
            token = tokens[i]
            if i == 0:
                initial_word[token] = initial_word.get(token, 0) + 1
            else:
                prev_token = tokens[i - 1]
                if i == tokens_length - 1:
                    add2dict(transitions, (prev_token, token), 'END')
                if i == 1:
                    add2dict(second_word, prev_token, token)
                else:
                    prev_prev_token = tokens[i - 2]
                    add2dict(transitions, (prev_prev_token, prev_token), token)
# Normalize the distributions
    initial_word_total = sum(initial_word.values())
    for key, value in initial_word.items():
        initial_word[key] = value / initial_word_total
        
    for prev_word, next_word_list in second_word.items():
        second_word[prev_word] = list2probabilitydict(next_word_list)
        
    for word_pair, next_word_list in transitions.items():
        transitions[word_pair] = list2probabilitydict(next_word_list)
    
    print('Training successful.')


    generate()
full of sweet dreams and health and quiet breathing
its loveliness increases it will never
till i heard chapman speak out loud and bold
with streams that deepen freshly into bowers
about old forests while the willow trails
hum about globes of clover and sweet peas
there let its trumpet blow and quickly dress
the passion poesy glories infinite
a fullborn beauty new and exquisite
hide in deep herbage and ere yet the bees
