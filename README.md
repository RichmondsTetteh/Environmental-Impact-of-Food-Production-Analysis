# Environmental-Impact-of-Food-Production-Analysis
Not only has demand for all three increased, but they are also strongly interlinked: food production requires water and energy; traditional energy production demands water resources; agriculture provides a potential energy source. This data focuses on the environmental impacts of food.

Data Loading and Initial Assessment
This section focuses on loading the dataset into a pandas DataFrame and performing an initial assessment to understand its structure, data types, and identify any potential issues like missing values or duplicates.

This code block imports necessary libraries for data manipulation, analysis, and visualization: pandas for data handling, numpy for numerical operations, and matplotlib and seaborn for plotting. The %matplotlib inline command ensures that plots are displayed directly within the notebook.

The cell prompts to upload the CSV file containing the food production data. The uploaded file will be saved in the Colab environment.

The code reads the uploaded CSV file into a pandas DataFrame named food_production. This DataFrame will be used for all subsequent data cleaning, analysis, and visualization tasks.

The markdown cell serves as a header to indicate the start of the data assessment process, where the structure and quality of the loaded data will be examined.

The head() method is used to display the first 5 rows of the food_production DataFrame. This provides a quick preview of the data and its format.

The shape attribute returns a tuple representing the dimensions of the DataFrame (number of rows, number of columns). This gives an overview of the dataset's size.

The markdown cell summarizes the dimensions of the dataset as obtained from the shape attribute, stating that it has 43 rows and 23 columns.

The dtypes attribute displays the data type of each column in the DataFrame. Understanding data types is crucial for appropriate data manipulation and analysis.

The markdown cell lists the columns that were identified as having null (missing) values based on the output of the info() method or isnull().sum().

The code checks for duplicate rows in the food_production DataFrame using the duplicated() method and sums the boolean results to get the total count of duplicate rows.

The cell performs two checks for missing data: isnull().sum() counts the number of null values in each column, and (food_production == '').sum() checks for columns containing empty strings.

Data Cleaning
This section focuses on cleaning the dataset to handle missing values and improve the usability of column names.

Based on the assessment of the food_production dataset, the most crucial data cleaning steps are addressing missing values and improving column names for better readability and ease of use in analysis and visualization.

For handling the missing data, I used median imputation because:

The code creates a copy of the original food_production DataFrame named cleaned_data. This is a good practice to preserve the original data while performing cleaning operations on a separate copy.

The code identifies the numerical columns in the cleaned_data DataFrame that contain missing values. It selects columns with numerical data types (include=np.number) and then filters these columns to find those where any value is null (isnull().any()). The names of these columns are then printed.

The code iterates through the numerical_cols_with_missing list and fills the missing values (NaN) in each of these columns in the cleaned_data DataFrame with the median value of the respective column. This is the median imputation step.

The markdown cell serves as a header to indicate that the following code will test whether the missing values have been successfully handled after the imputation step.

The code verifies that missing values have been handled in the cleaned_data DataFrame after median imputation. It prints the sum of null values for each column, and ideally, the numerical columns that previously had missing values should now show a count of 0.

The markdown cell indicates the start of the process to clean up and standardize the column names for better readability and ease of use in coding.

The code block renames the columns in the cleaned_data DataFrame. It iterates through the existing column names, converts them to lowercase, replaces spaces and hyphens with underscores, and shortens some of the longer, more descriptive names to more concise abbreviations while retaining their meaning. A dictionary new_column_names is created to map the old names to the new ones, and the rename() method is used to apply the changes to the DataFrame in place.

The markdown cell serves as a header to indicate that the following code will test whether the column names have been successfully renamed.

The code displays the first two rows of the cleaned_data DataFrame after renaming the columns. This allows for a quick visual verification that the column names have been updated as intended.

The code displays the data types of each column in the cleaned_data DataFrame after the column renaming. This is to confirm that the data types have remained consistent after the renaming process.

Group by 'Category' and analyze
Group the dataframe by the new 'category' column and calculate the total and mean of the numerical columns to analyze the total and the average environmental impact metrics for each food category.

Group the farm products into logical categories based on their type and use.
Grouped Farm Products Grains and Cereals

Wheat & Rye (Bread) Maize (Meal) Barley (Beer) Oatmeal Rice

Root and Tuber Crops

Potatoes Cassava Root Vegetables

Legumes and Pulses

Other Pulses Peas Groundnuts

Nuts

Nuts

Oil Crops and Oils

Soybean Oil Palm Oil Sunflower Oil Rapeseed Oil Olive Oil

Vegetables

Tomatoes Onions & Leeks Brassicas Other Vegetables

Fruits

Citrus Fruit Bananas Apples Berries & Grapes Other Fruit

Sugar Crops

Cane Sugar Beet Sugar

Animal Products

Beef (beef herd) Beef (dairy herd) Lamb & Mutton Pig Meat Poultry Meat Milk Cheese Eggs Fish (farmed) Shrimps (farmed)

Soy Products

Soymilk Tofu

Beverages and Specialty Crops

Coffee Wine Dark Chocolate

Create a mapping dictionary
Define a dictionary to map each food product to its corresponding category based on the provided groupings.

Create a new 'category' column
Add a new column 'category' to the dataframe by mapping 'food_product' using the food_category_mapping dictionary and then display the first few rows to verify.

Group the DataFrame by the 'category' column and calculate the mean of all numerical columns for each category.

Visualizations
The code creates a copy of the cleaned_data DataFrame for visualization purposes, named graph. This is done to ensure that any modifications or filtering for visualizations do not affect the cleaned data used for analysis.

The code block generates a bar plot showing the count of each unique food product in the dataset. This helps to understand the distribution of different food items in the data.

Visualize Grouped Data
Generate bar plots using the category_means dataframe to visualize and compare the average total emissions, land use, and water withdrawal metrics for each food category.

The code block generates a bar plot to visualize the total environmental impact per food category, broken down by different impact types (land use change, animal feed, farm, processing, transport, packaging, and retail). The categories are ordered by their total impact in descending order. This plot helps to identify which food categories have the highest overall environmental burden and which stages contribute most to that impact within each category.

The code block generates a bar plot to visualize the total emissions for each food category. The categories are sorted in descending order based on their total emissions. This plot clearly highlights which food categories contribute the most to overall emissions. Data labels are added to show the exact total emission values for each category.

The code block generates a bar plot to visualize the average total emissions per food category. The categories are sorted in descending order based on their average total emissions. This plot helps to understand the typical emission intensity of food products within each category. Data labels are added to show the exact average total emission values.

The code filters the cleaned_data DataFrame to include only the rows where the 'category' is 'Animal Products'. This creates a new DataFrame animal_products that can be used for further analysis or visualization specifically for animal products.

The code block generates a bar plot to visualize the total emissions for each individual animal product within the 'Animal Products' category. The animal products are sorted in descending order based on their total emissions. This plot allows for a direct comparison of the emission impact of different animal products. Data labels are added to show the exact total emission values.

The code block generates a bar plot to visualize the total land use (in m² per kilogram) for each food category. The categories are sorted in descending order based on their total land use. This plot helps to identify which food categories require the most land. Data labels are added to show the exact total land use values.

The code block generates a bar plot to visualize the average land use (in m² per kilogram) per food category. The categories are sorted in descending order based on their average land use. This plot helps to understand the typical land use intensity of food products within each category. Data labels are added to show the exact average land use values.

The code block generates a bar plot to visualize the total land use (in m² per kilogram) for each individual animal product within the 'Animal Products' category. The animal products are sorted in descending order based on their total land use. This plot allows for a direct comparison of the land use impact of different animal products. Data labels are added to show the exact total land use values.

The code block generates a bar plot to visualize the total freshwater withdrawals (in liters per kilogram) for each food category. The categories are sorted in descending order based on their total freshwater withdrawals. This plot helps to identify which food categories require the most freshwater. Data labels are added to show the exact total freshwater withdrawal values.

The code block generates a bar plot to visualize the average freshwater withdrawals (in liters per kilogram) per food category. The categories are sorted in descending order based on their average freshwater withdrawals. This plot helps to understand the typical freshwater withdrawal intensity of food products within each category. Data labels are added to show the exact average freshwater withdrawal values.

The code block generates a bar plot to visualize the total freshwater withdrawals (in liters per kilogram) for each individual animal product within the 'Animal Products' category. The animal products are sorted in descending order based on their total freshwater withdrawals. This plot allows for a direct comparison of the freshwater withdrawal impact of different animal products. Data labels are added to show the exact total freshwater withdrawal values.

The code block generates a bar plot to visualize the total scarcity-weighted water use (in liters per kilogram) for each food category. The categories are sorted in descending order based on their total scarcity-weighted water use. This plot helps to identify which food categories have the highest water scarcity impact. Data labels are added to show the exact total scarcity-weighted water use values.

The code block generates a bar plot to visualize the average scarcity-weighted water use (in liters per kilogram) per food category. The categories are sorted in descending order based on their average scarcity-weighted water use. This plot helps to understand the typical water scarcity impact intensity of food products within each category. Data labels are added to show the exact average scarcity-weighted water use values.

The code block generates a bar plot to visualize the total scarcity-weighted water use (in liters per kilogram) for each individual animal product within the 'Animal Products' category. The animal products are sorted in descending order based on their total scarcity-weighted water use. This plot allows for a direct comparison of the water scarcity impact of different animal products. Data labels are added to show the exact total scarcity-weighted water use values.

This code block filters the cleaned_data DataFrame to include only the rows where the 'category' is 'Beverages and Specialty Crops'. This creates a new DataFrame beverages_specialty_crops that can be used for further analysis or visualization specifically for beverages and specialty crops.
