<!--Copyright 2021 The HuggingFace Team. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with
the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.
-->

# BigBird

## Overview

The BigBird model was proposed in [Big Bird: Transformers for Longer Sequences](https://arxiv.org/abs/2007.14062) by
Zaheer, Manzil and Guruganesh, Guru and Dubey, Kumar Avinava and Ainslie, Joshua and Alberti, Chris and Ontanon,
Santiago and Pham, Philip and Ravula, Anirudh and Wang, Qifan and Yang, Li and others. BigBird, is a sparse-attention
based transformer which extends Transformer based models, such as BERT to much longer sequences. In addition to sparse
attention, BigBird also applies global attention as well as random attention to the input sequence. Theoretically, it
has been shown that applying sparse, global, and random attention approximates full attention, while being
computationally much more efficient for longer sequences. As a consequence of the capability to handle longer context,
BigBird has shown improved performance on various long document NLP tasks, such as question answering and
summarization, compared to BERT or RoBERTa.

The abstract from the paper is the following:

*Transformers-based models, such as BERT, have been one of the most successful deep learning models for NLP.
Unfortunately, one of their core limitations is the quadratic dependency (mainly in terms of memory) on the sequence
length due to their full attention mechanism. To remedy this, we propose, BigBird, a sparse attention mechanism that
reduces this quadratic dependency to linear. We show that BigBird is a universal approximator of sequence functions and
is Turing complete, thereby preserving these properties of the quadratic, full attention model. Along the way, our
theoretical analysis reveals some of the benefits of having O(1) global tokens (such as CLS), that attend to the entire
sequence as part of the sparse attention mechanism. The proposed sparse attention can handle sequences of length up to
8x of what was previously possible using similar hardware. As a consequence of the capability to handle longer context,
BigBird drastically improves performance on various NLP tasks such as question answering and summarization. We also
propose novel applications to genomics data.*

Tips:

- For an in-detail explanation on how BigBird's attention works, see [this blog post](https://huggingface.co/blog/big-bird).
- BigBird comes with 2 implementations: **original_full** & **block_sparse**. For the sequence length < 1024, using
  **original_full** is advised as there is no benefit in using **block_sparse** attention.
- The code currently uses window size of 3 blocks and 2 global blocks.
- Sequence length must be divisible by block size.
- Current implementation supports only **ITC**.
- Current implementation doesn't support **num_random_blocks = 0**
- BigBird is a model with absolute position embeddings so it's usually advised to pad the inputs on the right rather than
  the left.

This model was contributed by [vasudevgupta](https://huggingface.co/vasudevgupta). The original code can be found
[here](https://github.com/google-research/bigbird).

## Documentation resources

- [Text classification task guide](../tasks/sequence_classification)
- [Token classification task guide](../tasks/token_classification)
- [Question answering task guide](../tasks/question_answering)
- [Causal language modeling task guide](../tasks/language_modeling)
- [Masked language modeling task guide](../tasks/masked_language_modeling)
- [Multiple choice task guide](../tasks/multiple_choice)

## BigBirdConfig

[[autodoc]] BigBirdConfig

## BigBirdTokenizer

[[autodoc]] BigBirdTokenizer
    - build_inputs_with_special_tokens
    - get_special_tokens_mask
    - create_token_type_ids_from_sequences
    - save_vocabulary

## BigBirdTokenizerFast

[[autodoc]] BigBirdTokenizerFast

## BigBird specific outputs

[[autodoc]] models.big_bird.modeling_big_bird.BigBirdForPreTrainingOutput

## BigBirdModel

[[autodoc]] BigBirdModel
    - forward

## BigBirdForPreTraining

[[autodoc]] BigBirdForPreTraining
    - forward

## BigBirdForCausalLM

[[autodoc]] BigBirdForCausalLM
    - forward

## BigBirdForMaskedLM

[[autodoc]] BigBirdForMaskedLM
    - forward

## BigBirdForSequenceClassification

[[autodoc]] BigBirdForSequenceClassification
    - forward

## BigBirdForMultipleChoice

[[autodoc]] BigBirdForMultipleChoice
    - forward

## BigBirdForTokenClassification

[[autodoc]] BigBirdForTokenClassification
    - forward

## BigBirdForQuestionAnswering

[[autodoc]] BigBirdForQuestionAnswering
    - forward

## FlaxBigBirdModel

[[autodoc]] FlaxBigBirdModel
    - __call__

## FlaxBigBirdForPreTraining

[[autodoc]] FlaxBigBirdForPreTraining
    - __call__

## FlaxBigBirdForCausalLM

[[autodoc]] FlaxBigBirdForCausalLM
    - __call__

## FlaxBigBirdForMaskedLM

[[autodoc]] FlaxBigBirdForMaskedLM
    - __call__

## FlaxBigBirdForSequenceClassification

[[autodoc]] FlaxBigBirdForSequenceClassification
    - __call__

## FlaxBigBirdForMultipleChoice

[[autodoc]] FlaxBigBirdForMultipleChoice
    - __call__

## FlaxBigBirdForTokenClassification

[[autodoc]] FlaxBigBirdForTokenClassification
    - __call__

## FlaxBigBirdForQuestionAnswering

[[autodoc]] FlaxBigBirdForQuestionAnswering
    - __call__