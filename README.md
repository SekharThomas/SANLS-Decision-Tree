SANLS CODE DOCUMENTATION & EXECUTION GUIDE

Overview of the Code
	The provided code implements the Soft Adaptive Node-Level Stabilization (SANLS) Decision Tree. This model extends classical decision trees by incorporating adaptive bootstrapping to stabilize splits and monitor node-level stability across multiple bootstrapped trees.
	The code has the following major parts:
Library imports
•	SANLSTree class: The core model with stability tracking.
•	Stability metric function: Calculates median, mean, and max stability.
•	Dataset loading functions: Load Iris or Digits datasets.
•	Experiment function: Trains, tests, and evaluates the SANLS model.
•	Benchmark function: Compares splitting criteria (gini vs entropy).
•	Statistical tests: Performs Wilcoxon Signed-Rank and Friedman tests.

Functional Workflow Description
Step 1: Model Initialization
SANLS is initialized by specifying:
Splitting criterion (entropy or gini).
Maximum depth
Number of bootstrap iterations (default 80).
Step 2: Model Training (fit)
The training data is repeatedly resampled using bootstrapping.
A Decision Tree is trained on each resampled dataset.
Stability (number of nodes) is computed for every tree.
The first trained tree is saved for future predictions.
Step 3: Prediction (predict)
The first trained tree is used to predict test data.
Step 4: Stability Computation
Calculates median, mean, and maximum number of nodes across bootstraps, representing split stability.
Step 5: Evaluation (run_experiment)
Dataset is split into train-test sets.
The SANLS model is trained and evaluated.
Accuracy, training time, and stability measures are recorded.
Step 6: Benchmarking (benchmark_criteria)
Runs SANLS using both entropy and gini splitting criteria for comparison.
Step 7: Statistical Testing (statistical_tests)
Performs Wilcoxon Signed-Rank test to compare models pairwise.
	Performs Friedman test to compare multiple models simultaneously.

How to Run the Code (Step-by-Step Execution)
Step 1: Install Required Libraries
Before running the code, ensure that you have installed the following Python libraries:
bash
Copy
Edit
pip install numpy pandas scikit-learn scipy
Step 2: Load Dataset
By default, the provided code loads the Iris dataset. You may also switch to the Digits dataset inside the load_sample_dataset() function.
No external datasets are required for basic execution.
Step 3: Execute the Benchmark Experiment
Simply execute:
The load_sample_dataset() function to load the dataset.
The benchmark_criteria() function to evaluate gini and entropy criteria.
The output will be a table showing accuracy, training time, and stability scores.
Step 4: Execute Statistical Comparison
Run:
The statistical testing section.
This will compute pairwise Wilcoxon tests and the Friedman test to check significance between models.
Step 5: Modify Hyperparameters
Number of bootstrap iterations (n_bootstrap).
Maximum tree depth (max_depth).
Splitting criterion (criterion).
These parameters can be adjusted inside the run_experiment() function to study their influence.

Expected Outputs
Model accuracy for test data.
Stability statistics: median, mean, and max node counts.
Runtime for training.
Wilcoxon test p-values.
Friedman test results.

