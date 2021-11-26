# Custom-Transformer-for-Encoding-Categorical-Data
A Custom Transformer built to automatically one-hot or label encode categorical data. <br />
It adds a level of automation to the process of encoding categorical variables during data preprocessing as well as simultaneously expanding the functionality of Scikit-Learn's built-in One-Hot and Label encoders by being able to perform encoding transformations while there are missing values present, and preserve their state afterwards.

The custom transformer, arbitrarily named `EncoderbyCol`, accepts a dictionary (as a parameter), that has encoding methods - "`onehot`" or "`label`" (representing One-Hot, or Label encoding respectively), as its keys, and the column names of the features to be encoded by these methods, respectively, as the values. 
The encoding method performed on each column is specified in the dictionary's keys; the DataFrame is transformed by the encoders.

For example: <br />
 `col = {'label': ['Sex'], 'onehot': ['Embarked','Pclass']}` <br />
The feature 'Sex' will be transformed by a `LabelEnconder`, while the features 'Embarked', and 'Pclass' will be transformed by OneHotEncoder.

It has the functionality to perform Label encoding and One-hot encoding.

Its functionality is unaffected by the presence of missing data. All missing values that were present prior to the transformation will remain so after the transformation. Missing data points are excluded from the encoding process, i.e, encoding is performed on only the non-missing values. 
All missing values in the DataFrame are first replaced by the string 'NaN' to prevent the encoder from raising an error, the encoding operation is performed, and then the transformed DataFrame is returned with the missing values intact, having been converted to `np.nan`.

The transformer will return the full DataFrame passsed into it, but with the pre-selected features transformed/encoded as required. The other features will remain unchanged.
