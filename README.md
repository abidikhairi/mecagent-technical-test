### Everything is explained in the good_luck.ipynb file.

#### Dataset Observations
The CAD code contains excessive floating-point precision, which is problematic for LLMs, known to struggle with numeric precision and generalization ([llms struggle with math](https://arxiv.org/html/2411.03766v1)).

#### Preprocessing Suggestions
- Placeholder Substitution: Replace floating-point numbers with abstract tokens (e.g., <FLOAT_1>, <FLOAT_2>) to reduce vocabulary noise and focus learning on structure.
- Float Truncation (alternative): Truncate floating-point numbers to a fixed precision (e.g., 5 digits) to reduce variability while preserving semantic meaning.
- Code Transformation: Refactor CAD code to initialize numeric values as variables, then reference those variables in the instructions. This makes patterns easier to learn and improves generalization.

#### My Approach
- The task is a direct image-to-code generation with limited instruction complexity.

- I used a small Vision Transformer (ViT) encoder to extract features from the CAD image efficiently.

- For the decoder, I chose RoFormer, a transformer decoder capable of handling long sequences with relative positioning.

- The model was trained from scratch due to the domain mismatch with pretrained LLMs. Zero-shot performance confirmed poor generalization without fine-tuning (`results/smolvlm_zero_shot.json`).
