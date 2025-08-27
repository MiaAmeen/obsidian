1. A Physically-Based Model for Urban Fire Spread
	- The study develops a physically-based model for simulating urban fire spread, treating urban fire as a collection of individual building fires
	- The model consists of two sub-models: a building fire model to predict fire behavior under external heating, and a thermal environment model to predict the thermal conditions caused by building fires
- 1.2 Risk and Behavior of Fire Spread in a Densely-built Urban Area
	- The study uses a physics-based model to simulate fire spread4. This model treats urban fires as a collection of individual building fires that evolve under the thermal influence of surrounding building fires
- 1.3 Development and validation of a physics-based urban fire spread model
	- 2 major sub-models: building and building-to-building fire model.
	- As for the building-to-building fire spread, three mechanisms are considered as contributing factors of fire spread, i.e., (I) thermal radiation from fire-involved buildings; (II) temperature rise due to wind-blown fire plumes; and (III) firebrand spotting. As for the model verification, fire spread simulations were carried out in a hypothetical urban area, where 2500 buildings of identical configuration were aligned at constant separations

1. Development of a fire prediction model at the urban planning stage
	- This document presents a study that develops fire prediction models for use in urban planning, using land use area data and fire damage data from South Korea
	- The model results suggest that residential areas are a significant factor in the number of fires because the proportion of fires and the area of residential areas are high

2. Urban fire situation forecasting
	1. The core problem is forecasting urban fire situations, which is crucial for urban security and firefighting
	2. Spatio-temporal dynamics are critical but challenging to model. Fires are influenced by spatial factors (e.g., different districts with different fire risks) and temporal factors (e.g., time of day, seasons)
	3. The authors propose a novel deep sequence learning model called FSFN (Fire Situation Forecasting Network) to address the challenges of urban fire forecasting. Also uses seq2seq somehow ?

Related to wildfires...

2. CAUSAL GRAPH NEURAL NETWORKS FOR WILDFIRE
DANGER PREDICTION
	- "The study integrates causality with Graph Neural Networks (GNNs) to model the causal mechanisms among complex variables using graph learning"
	- Uses GNNs to do wildfire forecasting
	- The causal GNN model demonstrates superior performance in forecasting wildfire patterns compared to other methods1.
	- The model shows physically consistent dependencies between variables

3. Explainable Global Wildfire Prediction Models using Graph Neural Networks
	- The study proposes a GNN-based model that combines a Graph Convolutional Network (GCN) with a Long Short-Term Memory (LSTM) network to address the limitations of CNNs
	- The GCN-LSTM model outperforms the baseline models (LSTM, CAE-LSTM, and Conv-LSTM) in terms of predictive accuracy, with lower Mean Square Error (MSE) and Relative Root Mean Squared Error (RRMSE), and higher Structural Similarity Index Measure (SSIM) and Peak Signal-to-Noise Ratio (PSNR)
	- Our findings not only advance the methodological domain of wildfire prediction but also underscore the importance of model transparency through explainability

Im lazy. Summary:
By combining the strengths of GNNs, physics-informed learning, and other advancements, it's possible to develop more accurate, interpretable, and efficient models for urban fire spread prediction.