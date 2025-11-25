UC_Berkeley_AI_Module_11
Practical Application II: What Drives the Price of a Car?

Overview
In this application, a dataset of 426K used cars was analyzed to understand what factors make a car more or less expensive. The goal of the
#analysis is to provide clear recommendations to the used car dealership as to what consumers value in a used car.

Executive Summary and Conclusion
The extensive data cleaning and feature engineering phase was highly successful, but all tested Linear Models (Linear, Ridge, Lasso, and Polynomial Regression)
failed to explain the market dynamics. The best predictive model achieved a low R^2 of only ~30% and an average prediction error of over $7,500.
Conclusion: The problem is not data quality but High Bias (Underfitting)—the linear form of the model is mathematically too simple to capture the complex,
non-linear relationships and feature interactions that drive pricing.
 
Recommendation: Do not use the current model for pricing. Immediate action is required to switch to a non-linear ensemble method (like Random Forest or XGBoost) to achieve the necessary R^2 stability (expected 80-95%) and deliver reliable, actionable insights.

While the overall model failed, diagnostic tools like Permutation Importance revealed the market's true priorities.
These insights should guide your inventory strategy immediately:
1. Mileage x Age (mean importance = 20.22%) is the strongest driver. The market heavily punishes cars with high mileage relative to their age. Inventory must prioritize cars with low usage for their model year (e.g., a 5-year-old car with 20k miles).
2. State mean price (5.7%) - The average price in your specific State/Region is the second most important factor. All pricing must be anchored to local market values.
3. Mileage x Mileage (~5%) - The market applies a highly non-linear discount to mileage, meaning the value drop is steeper for very high mileage cars than it is for low-to-mid mileage cars.
4. State mean price x Age (~5%) - The rate at which a car depreciates depends on the local market. Older cars in a high-value state may retain value longer.


Please note that these findings exclude extreme outliers in the data (price > $90k, odometer > 300k miles, cars older than 1970). Records missing information on fuel, odometer, and transmission were dropped. High cardinality features were consolidated (manufacturer mapped to country of origin, type of vehicle was grouped into categories). The target variable was transformed (log of price) to stabilize the model's variance, and year was converted to Age.

Next steps/recommendation
To move past this roadblock and deliver the promised product, we must update the modeling tool:Action: Proceed to Phase 2 by using the fully prepared and cleaned feature set with a tree-based ensemble method. The new model will be able to interpret the crucial Mileage x Age interaction and deliver R^2 scores high enough for reliable pricing and inventory decisions.
