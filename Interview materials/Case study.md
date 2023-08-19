# Examples

- Forecasting product sales @ Amazon
- ==Meaningful== segmentation of Apple's customers (see elaboration below $\downarrow$)
# [Response Framework](https://www.youtube.com/watch?v=DqgiUo44X-k)

1. Clarify
	- "What is the business objective of the segmentation? Is it for product research or marketing?" $\rightarrow$ What kind of segmentation is ==meaningful==?
	- "Should I focus on all Apple domain or just one (e.g. Apple Music)?"
2. Constrain
	- Stating the defined goal after clarification
	- "Focusing on segmenting users based on subscriptions to Apple Music. The goal is find customer profiles for the marketing team."
3. Plan
4. Method
	- Preparing data:
		- user profiles
		- user behaviour
		- marketing ==engagement data==
	- ==Feature engineering to extract signals==:
		- \# of active minutes or sessions in Apple Music in the past 10 days
	- Model:
		- K-Mean clustering
		- [Elbow method](https://www.geeksforgeeks.org/elbow-method-for-optimal-value-of-k-in-kmeans/) for optimization
		- The clusters can be ==interpreted using descriptive statistics== to create user profiles
5. Conclude
	- low frequency active session in one cluster $\rightarrow$ targeted email to encourage engagement
# [Measure driver satisfaction @ Lyft](https://www.youtube.com/watch?v=DqgiUo44X-k)

- Business purpose of measuring driver satisfaction?
- What does satisfaction mean?
- Are there labels?
- It's up to the interviewee to decide what satisfaction measurement means and how to use it. No labels.
- The goal is the keep the churn-rate down
- Labeling:
	- Survey for the users
	- Proxy variable: churn
- Model:
	- Logistic regression
	- The output is the probability of churn
	- Inputs: driver profile, engagement, geo, etc.
- The marketing team could target the group with high churn probability
# ToDo - possible use case points

- Trigger for executing the model
- Model testing
- Data pipeline
# [Finding influencers on Instagram](https://www.youtube.com/watch?v=XOJk0AKIqv8)

- Definition:
	- \# of followers
	- \# of overall views of their posts
	- paid ads
- Goal: Promote potential influencers for advertisers
- How to model:
	- Unsupervised:
		- Cluster -> influencers, potential influencers, others
	- Supervised:
		- ==Getting labels for training data==: IG knows the paid posts
- Segmenting influencers
	- Potential categories: fashion, politics, etc.
	- It can be used as signal for what kind of readers they attract
	- Features: content of post (NLP, LSTM, Naive Bayes), their followers (their interest can be estimated)
	- Model: k-means clustering
	- Evaluation: human raters against estimated clusters