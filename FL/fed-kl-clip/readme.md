# Federated Learning : Dynamic KL Clipping
## Overview
This architecture is inspired by the concept of Federated Learning with Dynamic Kullback-Leibler (KL) divergence Weight (FedDkw). The key idea is to utilize the data heterogeneity information to enhance system performance. Additionally, we introduce a clipping mechanism to further stabilize the training process.

### Key Components
1. **Dynamic KL-Divergence Weighting:**
   - Each client, while uploading its model to the server, also provides the distribution of its training data.
   - The server maintains a global distribution, which is updated after receiving the distributions from all clients in each round.
   - The weight assigned to each client is proportional to \( \frac{1}{KL(i)} \), where \( KL(i) \) is the KL divergence between the client’s distribution and the global distribution. This ensures that clients with distributions closer to the global one are given higher weights.

2. **Clipping Mechanism:**
   - To ensure stability and robustness, gradient clipping is applied to the updates from each client. This prevents any single client with a significantly different data distribution from dominating the model update.

3. **Data Distribution Inference (FedDkw++):**
   - To mitigate potential security risks associated with clients uploading their data distributions, the server infers each client’s distribution using the uploaded model and its local data. This inferred distribution is then used to calculate the KL divergence.

## Architecture


