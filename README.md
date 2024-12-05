# Kolmogorov-Smirnov Test - Non Parametric Test

This repository contains code to perform the Kolmogorov-Smirnov (KS) Test, a non-parametric test used to compare a sample with a reference probability distribution or to compare two samples. The KS test is used to determine whether two datasets are significantly different or if a dataset follows a given distribution.

## File Overview
The main file is the `KS Test - Non Parametric Test.ipynb`, which demonstrates the application of the KS test on a credit card fraud dataset to test if fraudulent and non-fraudulent transactions have significantly different distributions, and to assess if a sample follows a normal distribution.

## Libraries Used
- **pandas**: Data manipulation and analysis.
- **numpy**: Numerical computations.
- **scipy.stats**: Statistical tests, including KS test.
- **matplotlib**: Plotting histograms and cumulative distribution functions (CDFs).

## Steps in the Code

### 1. **Data Loading**
The dataset `creditcard.csv` is loaded into a pandas DataFrame, which contains transaction data with features like `Amount`, and a `Class` column indicating whether a transaction is fraudulent (`1`) or non-fraudulent (`0`).
- Dataset Link : - https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

```python
df = pd.read_csv('creditcard.csv')
```

### 2. **Data Split**
The dataset is split into two subsets:
- Fraudulent transactions (`Class = 1`)
- Non-fraudulent transactions (`Class = 0`)

### 3. **Kolmogorov-Smirnov Test on Amount Feature**
The KS test compares the distribution of the `Amount` feature between fraudulent and non-fraudulent transactions. The hypothesis tested is:
- **Null Hypothesis (H0)**: The distributions of the two samples are the same.
- **Alternative Hypothesis (H1)**: The distributions are different.

The KS test is performed with the following line of code:

```python
ks_stat, p_value = kstest(fraudulent['Amount'], non_fraudulent['Amount'])
```

The result of the test indicates whether there is a significant difference between the two distributions.

### 4. **Plotting Distributions and CDF**
Histograms and cumulative distribution functions (CDFs) for both fraudulent and non-fraudulent transactions are plotted for visual inspection.

### 5. **Kolmogorov-Smirnov Test for Normality**
A normality check is performed by comparing the `Amount` feature to a normal distribution with the mean and standard deviation of the data. The KS statistic is calculated and compared with a critical value for a significance level of α = 0.05.

### 6. **Interpretation of Results**
- If the p-value is less than 0.05, we reject the null hypothesis (H0), indicating that the distributions are significantly different.
- If the p-value is greater than 0.05, we accept the null hypothesis (H0), indicating that the distributions follow the same pattern.

### 7. **KS Test Function for Custom Data**
A custom implementation of the Kolmogorov-Smirnov test (`kolmogorov_smirnov_test`) compares observed and expected frequencies, calculates cumulative and relative cumulative frequencies, and computes the KS statistic.

```python
kolmogorov_smirnov_test(observed, expected, ks_critical_value, test_scores)
```

## Example Output
The KS test results for normality (using the Iris dataset) might look like this:

```
KS Statistic (Dn): 0.0895
P-Value: 0.1706
KS Critical Value: 0.1110
Conclusion: Accept H0: The distribution follows the normal distribution.
```

### Visualizations
The histograms and CDF plots generated provide visual representation of the data distributions, highlighting the difference (if any) between fraudulent and non-fraudulent transactions.

## Requirements
To run the code, you will need the following Python libraries:
- pandas
- numpy
- scipy
- matplotlib

You can install them using pip:
```bash
pip install pandas numpy scipy matplotlib
```

## Conclusion
This code demonstrates the use of the Kolmogorov-Smirnov test to assess the distributions of transaction amounts and the normality of the data. It can be extended to analyze other datasets or perform similar tests for distribution comparisons.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

This `README.md` provides an overview of the steps and outputs of your Kolmogorov-Smirnov test implementation, making it clear for anyone who wants to understand or replicate your work.
