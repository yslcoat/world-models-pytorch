World models are a type of models which aims to understand the environment around them. They do this by
intepreting the environment around them through some sensor input, like images, then processing these using 
some neural network to process these images, everything from CNNs to VAEs, and then some model to model
time-dependencies, like how the environment changes over time. The goal of a world model is to model the 
environmnet its acting in. 

* World models are categorised as model-based reinforcement learning.
* The generative aspect of world models allows it to generate possible scenarios, also known as "dreaming", which allows it to simulate possible actions and determine the best action.

World models are composed of
* A visual sensory component that interprets the environment the model is acting in. Usually compressess the sensor data into embedding space for example by using VAEs.
* A memory component which makes predictions about future states based on historical information.
* A decision-making component that decides what actions to take based on the information provided by the sensory component and memory component.

World models are trained by predicting the next state of the environment its acting in based on the previous state it has seen, combined
with the previous action it took. 

Complete training loop:
1. Collect new experiences by acting in environment using current policy
2. Train VAE to reconstruct states
3. Train transition model
4. Train actor-critic using dreaming
5. Repeat

Different world models architectures, MDN-RNN (mixed density network - RNN), RSSM (recurrent state-space model) etc

MDN-RNN:
    * Instead of outputting a deterministic scalar or vector used as a prediction, the hidden state is used to
    parametereize a mixture of K densities via the MDN. I'm gonna guess this is what enables the "dreaming", as
    the output does not collapse into a singular observation, but rather we can sample different observations.