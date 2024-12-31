</head>
<body>
    <h1>Loan Default Prediction Project</h1>

   <h2>Table of Contents</h2>
    <ol>
        <li><a href="#dataset-information">Dataset Information</a></li>
        <li><a href="#null-value-imputation">Null Value Imputation</a></li>
        <li><a href="#encoding">Encoding</a></li>
        <li><a href="#handling-imbalance-data-smote">Handling Imbalance Data (SMOTE)</a></li>
        <li><a href="#model-selection">Model Selection</a></li>
        <li><a href="#why-i-chose-xgboost">Why I Chose XGBoost</a></li>
        <li><a href="#hyperparameter-tuning-and-building-model-on-best-parameters">Hyperparameter Tuning and Building Model on Best Parameters</a></li>
        <li><a href="#author">Author</a></li>
    </ol>
    <h2 id="dataset-information">Dataset Information</h2>
    <p>The dataset used in this project contains data related to loan defaults, with various features including demographic, financial, and behavioral attributes. Below is a quick summary of the dataset:</p>
    <ul>
        <li>Total Rows: 150,000</li>
        <li>Total Columns: 22</li>     
        </li>
        <li>Target Variable: <code>status</code> (0 for non-default, 1 for default)</li>
    </ul>
    <h2 id="null-value-imputation">Null Value Imputation</h2>
<p>Several columns had missing values, including:</p>
<ul>
    <li><strong>Debt-to-Income Ratio (<code>dtir1</code>)</strong>:
        <ul>
            <li>Imputed missing values using median grouped by <code>Income</code>.</li>
        </ul>
    </li>
    <li><strong>Property Value (<code>property_value</code>), Income (<code>income</code>), Loan-to-Value Ratio (<code>LTV</code>)</strong>:
        <ul>
            <li>Imputed missing values using the mean.</li>
        </ul>
    </li>
    <li><strong>Term (<code>term</code>), Age (<code>age</code>)</strong>:
        <ul>
            <li>Filled missing values with the most frequent value.</li>
        </ul>
    </li>
</ul>
    <h2 id="encoding">Encoding</h2>
    <p>Categorical columns were encoded to numerical values using the following strategies:</p>
    <ul>
        <li>Used label encoding for ordinal columns.</li>
        <li>Converted age ranges (<code>&lt;25</code>, <code>45-54</code>, etc.) into their respective midpoints for better numerical representation.</li>
    </ul>
    <h2 id="handling-imbalance-data-smote">Handling Imbalance Data (SMOTE)</h2>
    <p>The target variable (<code>status</code>) was highly imbalanced:</p>
    <ul>
        <li><strong>Majority Class (0)</strong>: 112,031 instances</li>
        <li><strong>Minority Class (1)</strong>: 36,591 instances</li>
    </ul>
    <p>To address this imbalance, the <strong>SMOTE</strong> (Synthetic Minority Oversampling Technique) was applied with a <code>sampling_strategy=0.7</code>. This ensured the minority class was augmented proportionally without overwhelming the dataset size.</p>
    <h2 id="model-selection">Model Selection</h2>
    <p>Various models were evaluated, including::</p>
    <ul>
        <li>XGBoost Classifier</li>
        <li>RandomForesr Classifier</li>
        <li>GradientBoosting Classifier</li>
    </ul>

   <h2 id="why-i-chose-xgboost">Why I Chose XGBoost</h2>
    <p>XGBoost outperformed other models in terms of accuracy, precision, recall, and F1-score. Key metrics:</p>
    <ul>
        <li><strong>Accuracy</strong>: 91.32%</li>
        <li><strong>Precision</strong>: 81.5%</li>
        <li><strong>Recall</strong>: 96.7%</li>
        <li><strong>F1-Score</strong>: 88.4%</li>
        <li><strong>AUC-ROC</strong>: 92.1%</li>
    </ul>
    <p>These metrics demonstrate the ability of XGBoost to effectively classify loan defaults.</p>

  <h2 id="hyperparameter-tuning-and-building-model-on-best-parameters">Hyperparameter Tuning and Building Model on Best Parameters</h2>
    <p>Hyperparameter tuning was conducted using <code>RandomizedSearchCV</code> with the following parameter grid:</p>
    <h3>Final Model Performance</h3>
    <p>The tuned XGBoost model achieved:</p>
    <ul>
        <li><strong>Accuracy</strong>: 91.2%</li>
        <li><strong>Precision</strong>: 80.6%</li>
        <li><strong>Recall</strong>: 96.6%</li>
        <li><strong>F1-Score</strong>: 88.05%</li>
        <li><strong>AUC-ROC</strong>: 92.3%</li>
    </ul>

  <h2 id="author">Author</h2>
    <p><strong>Tark Patel</strong></p>
    <ul>
        <li><strong>LinkedIn</strong>: <a href="https://www.linkedin.com/in/tark-patel/" target="_blank">https://www.linkedin.com/in/tark-patel/</a></li>
        <li><strong>Kaggle</strong>: <a href="https://www.kaggle.com/tark01" target="_blank">https://www.kaggle.com/tark01</a></li>
    </ul>
</body>
</html>

