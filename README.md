### Everything is explained in the good_luck.ipynb file.

#### Dataset Observations
The CAD code contains excessive floating-point precision, which is problematic for LLMs, known to struggle with numeric precision and generalization ([llms struggle with math](https://arxiv.org/html/2411.03766v1)).

#### Preprocessing Suggestions
- Placeholder Substitution: Replace floating-point numbers with abstract tokens (e.g., <FLOAT_1>, <FLOAT_2>) to reduce vocabulary noise and focus learning on structure.
- Float Truncation (alternative): Truncate floating-point numbers to a fixed precision (e.g., 5 digits) to reduce variability while preserving semantic meaning.
- Code Transformation: Refactor CAD code to initialize numeric values as variables, then reference those variables in the instructions. This makes patterns easier to learn and improves generalization.

#### My Approach
The task is fundamentally image-to-code generation with limited instruction complexity.

I selected RoFormer (Transformer decoder) for its ability to handle long contexts efficiently and its manageable model size.

The model was trained from scratch, as the target code format is out-of-distribution for existing LLMs. Pretrained models performed poorly (see zero-shot results in directory `results`).
