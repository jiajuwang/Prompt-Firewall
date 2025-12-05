# Prompt Firewall - Jailbreak Detection Assessment

## Overview
This project evaluates the ability of Ollama language models to identify jailbreaking prompts and distinguish them from benign conversational prompts.

## Dataset
The `malignant.csv` file contains 1,581 prompts categorized as:
- **Conversation** (1,312 samples): Normal, benign prompts
- **Jailbreak** (199 samples): Attempts to bypass AI safety measures
- **Act_as** (70 samples): Role-playing attempts to manipulate AI behavior

## Features
- ✅ Automated classification using Ollama LLMs
- ✅ Comprehensive evaluation metrics (accuracy, precision, recall, F1)
- ✅ Confusion matrix visualization
- ✅ Error analysis (false positives/negatives)
- ✅ Results export to CSV and PNG

## Requirements
```bash
pip install pandas ollama scikit-learn matplotlib seaborn tqdm
```

## Setup
1. **Install Ollama**: Download from [ollama.ai](https://ollama.ai)
2. **Pull a model**:
   ```bash
   ollama pull llama2
   # or
   ollama pull mistral
   ollama pull llama3
   ```
3. **Start Ollama service** (if not already running)

## Usage
Run the Jupyter notebook `main.ipynb` cell by cell:

1. **Load Data**: Import and explore the dataset
2. **Install Dependencies**: Install required Python packages
3. **Check Ollama**: Verify Ollama is running and models are available
4. **Configure Test**: Set `SAMPLE_SIZE` and `MODEL_NAME`
5. **Run Classification**: Classify all test prompts
6. **Evaluate Results**: View metrics and confusion matrix
7. **Visualize**: Generate performance charts
8. **Analyze Errors**: Examine misclassifications

## Configuration
In the notebook, you can adjust:
- `SAMPLE_SIZE`: Number of prompts to test (use `None` for full dataset)
- `MODEL_NAME`: Ollama model to use (`"llama2"`, `"mistral"`, `"llama3"`, etc.)
- `CLASSIFICATION_PROMPT`: The prompt template for classification

## Output Files
- `{model_name}_classification_results.csv`: Detailed results per prompt
- `ollama_jailbreak_detection_results.png`: Performance visualization

## Metrics Explained
- **Accuracy**: Percentage of correct classifications
- **Precision**: Of prompts flagged as jailbreaks, how many were actual jailbreaks
- **Recall**: Of actual jailbreaks, what percentage was detected
- **F1 Score**: Harmonic mean of precision and recall

## Example Results
```
Accuracy:  85.00%
Precision: 78.00% (of predicted jailbreaks, how many were correct)
Recall:    82.00% (of actual jailbreaks, how many were detected)
F1 Score:  80.00% (harmonic mean of precision and recall)
```

## Project Structure
```
Prompt-Firewall/
├── main.ipynb                    # Main analysis notebook
├── malignant.csv                 # Dataset with prompts
├── README.md                     # This file
└── [generated files]
    ├── *_classification_results.csv
    └── ollama_jailbreak_detection_results.png
```

## Notes
- Start with a small `SAMPLE_SIZE` (e.g., 50-100) to test quickly
- Each classification takes a few seconds depending on your model
- Lower temperature (0.1) provides more consistent results
- Different models may have different detection capabilities

## Future Improvements
- [ ] Test multiple models and compare performance
- [ ] Implement ensemble methods
- [ ] Fine-tune classification prompt
- [ ] Add confidence scores
- [ ] Test with custom jailbreak examples

## License
MIT

## References
- Dataset source: Based on jailbreak detection research
- Ollama: https://ollama.ai
