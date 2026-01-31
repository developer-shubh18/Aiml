# Email Spam Detection System

A complete machine learning system for detecting spam emails using various classification algorithms.

## 🚀 Features

- **Multiple ML Models**: Naive Bayes, Logistic Regression, Random Forest, and SVM
- **Text Preprocessing**: Advanced text cleaning, tokenization, and stemming
- **Feature Extraction**: TF-IDF vectorization for optimal feature representation
- **Model Evaluation**: Comprehensive performance metrics and visualizations
- **Interactive Prediction**: Test the model with custom messages
- **Web Interface**: Simple web app for real-time spam detection
- **Model Persistence**: Save and load trained models

## 📋 Requirements

- Python 3.7+
- Required packages (install via `pip install -r requirements.txt`):
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - scikit-learn
  - nltk
  - wordcloud
  - flask (for web interface)
  - jupyter (for notebook)

## 🛠️ Installation

1. **Clone or download the project files**

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Download NLTK data** (will be done automatically on first run):
   ```python
   import nltk
   nltk.download('punkt')
   nltk.download('stopwords')
   ```

## 📊 Dataset

The system expects a CSV file named `combined_data.csv` with the following structure:
- `label`: 0 for ham (legitimate), 1 for spam
- `text`: The email message content

If the dataset file is not found, the system will create sample data for demonstration.

### Dataset Format Example:
```csv
label,text
0,"Hi, how are you doing today?"
1,"Congratulations! You've won $1000!"
```

## 🎯 Usage

### Option 1: Jupyter Notebook (Recommended)

1. **Open the complete notebook**:
   ```bash
   jupyter notebook Complete_Email_Spam_Detection.ipynb
   ```

2. **Run all cells** to:
   - Load and explore the data
   - Visualize data distributions
   - Train multiple models
   - Compare model performance
   - Test predictions interactively

### Option 2: Python Script

1. **Run the complete script**:
   ```bash
   python complete_spam_detection.py
   ```

2. **Follow the interactive prompts** to test predictions

### Option 3: Web Interface

1. **First, train a model** using either the notebook or script

2. **Start the web server**:
   ```bash
   python web_interface.py
   ```

3. **Open your browser** and go to: `http://localhost:5000`

4. **Enter email messages** to get real-time spam/ham predictions

## 📈 Model Performance

The system trains and compares four different models:

1. **Naive Bayes**: Fast and effective for text classification
2. **Logistic Regression**: Linear model with good interpretability
3. **Random Forest**: Ensemble method with feature importance
4. **SVM**: Support Vector Machine with linear kernel

Each model is evaluated using:
- Accuracy
- Precision
- Recall
- F1-Score
- Cross-validation scores

## 🔍 Key Components

### Text Preprocessing
- Convert to lowercase
- Remove special characters and digits
- Remove stopwords
- Apply stemming
- Tokenization

### Feature Extraction
- TF-IDF (Term Frequency-Inverse Document Frequency)
- Maximum 5000 features
- English stopwords removal

### Model Training
- 80/20 train-test split
- Stratified sampling to maintain class balance
- 5-fold cross-validation
- Hyperparameter optimization

## 📁 File Structure

```
Spam email detection/
├── Complete_Email_Spam_Detection.ipynb  # Main Jupyter notebook
├── complete_spam_detection.py           # Complete Python script
├── web_interface.py                     # Flask web interface
├── requirements.txt                     # Python dependencies
├── README.md                           # This file
├── models/                             # Saved models directory
│   ├── best_spam_detector_*.pkl        # Best performing model
│   ├── spam_detector_*.pkl             # All trained models
│   └── preprocessing_info.txt          # Preprocessing instructions
└── combined_data.csv                   # Dataset (if available)
```

## 🎮 Interactive Features

### Notebook Interactive Prediction
```python
# In the notebook, use:
message = "Your message here"
result, confidence, probabilities = predict_message(message)
print(f"Prediction: {result} (Confidence: {confidence:.4f})")
```

### Command Line Interface
The Python script includes an interactive mode where you can enter messages and get immediate predictions.

### Web Interface
A user-friendly web interface that allows anyone to test the spam detection system through their browser.

## 📊 Visualizations

The system generates several informative visualizations:

1. **Distribution Charts**: Spam vs Ham message distribution
2. **Length Analysis**: Message and word count distributions
3. **Word Clouds**: Most common words in spam and ham messages
4. **Model Comparison**: Performance metrics across all models
5. **Confusion Matrix**: Detailed classification results
6. **Feature Importance**: Most important words for classification

## 🔧 Customization

### Adding New Models
To add a new model, modify the `models` dictionary in the training code:

```python
models['New Model'] = Pipeline([
    ('tfidf', TfidfVectorizer(max_features=5000, stop_words='english')),
    ('classifier', YourClassifier())
])
```

### Adjusting Preprocessing
Modify the `preprocess_text` function to change text preprocessing steps.

### Changing Features
Adjust TfidfVectorizer parameters:
- `max_features`: Maximum number of features
- `ngram_range`: N-gram range (e.g., (1,2) for unigrams and bigrams)
- `min_df`: Minimum document frequency
- `max_df`: Maximum document frequency

## 🚀 Deployment

### Local Deployment
Use the included Flask web interface for local testing.

### Production Deployment
For production deployment, consider:
- Using a production WSGI server (e.g., Gunicorn)
- Adding authentication and rate limiting
- Implementing model monitoring and retraining
- Using a more robust database for logging

## 📝 Example Usage

```python
from complete_spam_detection import SpamDetector

# Initialize detector
detector = SpamDetector()

# Load and train on your data
df = detector.load_and_explore_data("your_data.csv")
X_train, X_test, y_train, y_test = detector.prepare_data(df)
models, cv_scores = detector.train_models(X_train, y_train)

# Make predictions
result, confidence = detector.predict_message("Your message here")
print(f"Prediction: {result} (Confidence: {confidence:.4f})")
```

## 🤝 Contributing

Feel free to contribute by:
- Adding new machine learning models
- Improving text preprocessing
- Enhancing the web interface
- Adding more evaluation metrics
- Improving documentation

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- Scikit-learn for machine learning algorithms
- NLTK for natural language processing
- Flask for web interface
- The open-source community for various tools and libraries

---

**Happy Spam Detection! 🛡️**