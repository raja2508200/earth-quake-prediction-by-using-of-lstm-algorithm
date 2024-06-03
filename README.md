

#### Data Loading and Preprocessing
1. **Data Loading**: Reads earthquake data from the USGS website into a pandas DataFrame.
2. **Cleaning and Preparation**:
   - Sorts data by time and extracts the date.
   - Extracts relevant columns and cleans the 'place' column.
   - Calculates average coordinates for each place.

3. **Feature Engineering**:
   - Computes rolling averages for depth and magnitude over different windows (7, 15, 22 days).
   - Creates a target column 'mag_outcome' indicating whether the magnitude exceeds 2.5 within 25 days.

4. **Filtering**: Removes rows with NaN values in the engineered features and target column.

#### Model Training
1. **Data Splitting**: Splits data into training and testing sets.
2. **Scaling**: Scales the features to a range between 0 and 1.
3. **Reshaping**: Reshapes the data for LSTM input (samples, time steps, features).
4. **Model Definition**: Builds a Sequential LSTM model with one LSTM layer and a Dense output layer.
5. **Training**: Trains the model using the training data.

#### Prediction and Flask Web Application
1. **Prediction**: Applies the trained model to live data to generate predictions.
2. **Formatting**: Adjusts prediction dates to account for the 25-day prediction horizon.

3. **Utility Functions**: Defines functions to extract and format predictions based on user queries by date or place.

4. **Flask Web Application**:
   - Defines routes for the main page and select page.
   - Handles user requests to display earthquake predictions.

5. **Execution**: Runs the Flask web application on port 200.

