# One-Hot-Encoding-for-Nominal-Data
This repository demonstrates the implementation of One-Hot Encoding techniques for handling nominal categorical data in machine learning projects. The notebook covers multiple approaches to convert categorical variables into a numerical format suitable for ML algorithms.
One-Hot Encoding for Nominal Data
This repository demonstrates the implementation of One-Hot Encoding techniques for handling nominal categorical data in machine learning projects. The notebook covers multiple approaches to convert categorical variables into a numerical format suitable for ML algorithms.

# 📁 Project Structure
ONE_HOT_ENCODING.ipynb: Jupyter notebook containing a comprehensive implementation of one-hot encoding methods

cars.csv: Dataset used for demonstrating the encoding techniques

# 🎯 Key Concepts Covered
1. One-Hot Encoding Basics
Used for nominal data where categories have no intrinsic ordering

For n categories, use (n-1) columns to avoid multicollinearity

Handling large numbers of categories by grouping infrequent values

2. Implementation Methods
A. Using Pandas
python
pd.get_dummies(df, columns=['fuel','owner'], drop_first=True, dtype=np.int64)
Quick and easy implementation

Not recommended for production ML pipelines due to inconsistent behavior

B. Using Scikit-Learn
python
from sklearn.preprocessing import OneHotEncoder
ohe = OneHotEncoder(drop='first', sparse_output=False)
x_train_new = ohe.fit_transform(x_train[['fuel','owner']])
Preferred for ML projects

Consistent behavior and integration with sklearn pipelines

Proper train-test separation

C. Handling High Cardinality Features
Grouping infrequent categories (count ≤ threshold) into 'uncommon' category

Reduces dimensionality while preserving information

🔧 Technical Implementation
Data Overview
The dataset contains car features:

brand: Car manufacturer (32 unique values)

km_driven: Kilometers driven

fuel: Fuel type (Diesel, Petrol, CNG, LPG)

owner: Ownership history

selling_price: Target variable

Key Techniques Demonstrated
Train-Test Split before encoding to prevent data leakage

Drop First Category to avoid dummy variable trap

Combining Encoded Features with original numerical features

Threshold-based Category Grouping for high cardinality features

 # 🚀 Usage
python
# For sklearn implementation
from sklearn.preprocessing import OneHotEncoder
from sklearn.model_selection import train_test_split

# Split data first
x_train, x_test, y_train, y_test = train_test_split(
    df.iloc[:,0:4], df.iloc[:,-1], test_size=0.2, random_state=2
)

# Encode categorical features
ohe = OneHotEncoder(drop='first', sparse_output=False)
x_train_encoded = ohe.fit_transform(x_train[['fuel','owner']])
x_test_encoded = ohe.transform(x_test[['fuel','owner']])
⚠️ Important Considerations
Always split data before encoding to prevent test set information leakage

Use sklearn's OneHotEncoder for production ML pipelines

Handle high cardinality features by grouping rare categories

Be mindful of multicollinearity when using one-hot encoding

# 📊 Results
The notebook demonstrates how to effectively transform categorical variables into machine-readable format while maintaining data integrity and model performance.

This project serves as a practical guide for data preprocessing in machine learning workflows, specifically focusing on handling categorical data through one-hot encoding techniques.

