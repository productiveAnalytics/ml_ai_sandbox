# Creating a Clustering Model with Azure ML Designer

## Introduction
In this hands-on lab, you are working as a data scientist for The Greenery, a gardening store. After an unfortunate accident where the summer intern (we'll call him Steve) spilled all the seeds on the floor, you’ve been asked to come up with a model that can be used to group together the seeds based on their features. Steve wants to make sure the seeds are sorted before the boss returns and finds the mess! You’ll use Azure Machine Learning studio and Azure Machine Learning designer to create a clustering model that will group together similar seeds.

## Solution
Log in to the Azure portal using the credentials provided on the lab page. Be sure to use an incognito or private browser window to ensure you're using the lab account rather than your own.

### Open the Azure ML Studio and Create a New Dataset
1. From the list of resources, click the lab-provided machine learning workspace (its type will be Machine learning).

2. On the machine learning workspace page, click Launch studio. This will open it in a new browser tab.

3. In the left-hand menu, click the Data icon, which looks like two rectangles with a magnifying glass at the bottom.

4. On the Data page, click +Create.

5. On the Create data asset pane, fill in the following fields:
- Name: Enter Seeds
- Type: Select Tabular (under Azure ML v1 APIs)
6. Click Next.

7. On the Choose a source for your data asset page, choose From web files.

8. Click Next.

9. On the Enter a web URL page, paste in https://raw.githubusercontent.com/MicrosoftDocs/ml-basics/master/data/seeds.csv.

10. Click Next.

11. On the Settings page, leave the default settings and click Next.

12. On the Schema page, leave the default settings and click Next.

13. On the Review page, click Create.

### Review the Dataset
1. In the left-hand menu, click the Designer icon, which looks like a tiny flow chart.

2. Click the big plus sign on the left under New pipeline, which represents the blank canvas option.

Note: If necessary, close out of any pop-ups that appear.

3. In the upper right-hand corner, click Settings and set the following fields:
- Select compute type: Select Compute cluster.
- Select Azure ML compute cluster: Select the automatically lab-created cluster, which should be the only option.

4. Click the Close icon in the top right (the icon looks like an arrow inside a box) to close out of the Settings pane.

5. From the left-hand menu, drag the Seeds dataset onto the canvas.

6. Right-click Seeds and select Preview data.

7. Review the data in the pane on the right.

8. Click the Close icon in the top right to close out of the data preview.

### Design a Pipeline to Group Together Similar Seeds

#### Add _Normalize Data_ Module
1. In the left-hand menu, click the Component tab.

2. In the search bar above the module list, search for normalize.

3. Select and drag the Normalize Data module onto the canvas, below Seeds.

4. Click the circle at the bottom of the Seeds module and link it to the circle at the top of the Normalize Data module.

5. Double-click the Normalize Data module to open it in a pane on the right.

6. In the Normalize Data pane, click the Edit column link next to Columns to transform.

7. In the Columns to transform popup, in the Column names dropdown, select All columns instead.

8. Then select the + on the right.

9. In the Include dropdown, select Exclude.

10. In the All columns dropdown, select Column names.

11. Click into the Enter column name field, and select species from the dropdown.

Note: If the dropdown menu doesn't appear, type species and hit the Tab key to select it.

12. Click Save to save and exit the popup.

13. Click the Close icon in the top right of the pane to close out of the Normalize Data module.

#### Add _Split Data_ Module
1. In the search bar above the module list, search for split.

2. Select and drag the Split Data module onto the canvas, below Normalize Data.

3. Double-click the Split Data module to open it.

4. In the Split Data pane, in the Fraction of rows in the first output dataset field, enter 0.7.

5. Click the Close icon to close out of the Split Data module.

6. Click the circle at the bottom left of the Normalize Data module and link it to the circle at the top of the Split Data module.

#### Add _K-Means Clustering_ Module
1. In the search bar above the module list, search for k means.

2. Select and drag the K-Means Clustering module onto the canvas, to the left of the Split Data module.

#### Add _Train Clustering Model_ Module
1. In the search bar above the module list, search for train cluster.

2. Select and drag the Train Clustering Model module onto the canvas, below K-Means Clustering.

3. Click the circle at the bottom of the K-Means Clustering module and link it to the top left circle of the Train Clustering Model module.

4. Click the circle at the bottom left of the Split Data module and link it to the top right circle of the Train Clustering Model module.

5. Double-click the Train Clustering Model module to open it.

6. In the Train Clustering Model pane, click the Edit column link next to Column set.

7. In the Column set popup, click into the Column names dropdown and select All columns instead.

8. Click Save to close the popup.

9. Click the Close icon to close out of the Train Clustering Model module.

#### Add _Assign Data to Clusters_ Module
1. In the search bar above the module list, search for assign.

2. Select and drag the Assign Data to Clusters module onto the canvas, below Train Clustering Model.

3. Click the circle at the bottom left of the Train Clustering Model module and link it to the top left circle of the Assign Data to Clusters module.

4. Click the circle at the bottom right of the Split Data module and link it to the top right circle of the Assign Data to Clusters module.

#### Add _Evaluate Model_ Module
1. In the search bar above the module list, search for evaluate.

2. Select and drag the Evaluate Model module onto the canvas, below Assign Data to Clusters.

3. Click the circle at the bottom of the Assign Data to Clusters module and link it to the top left circle of the Evaluate Model module.

You now have a completed pipeline, which will normalize the seeds' features, split the data, and then build the clustering model for you.

### Run Pipeline
. 1Click Submit in the top menu bar.

2. In the Set up pipeline job window, select Create new.

3. For New experiment name, enter seedsclustering.

4. Click Submit.

5. In the Submitted jobs pane on the left, click the Job detail link to keep an eye on its progress in a new tab.

Note: It will take a few minutes to run.

6. Once it's done (each step in the flow chart will have a green checkmark), right-click the Evaluate Model module.

7. Select Preview data > Evaluation results.

8. Review the results.
