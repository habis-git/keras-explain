# Keras Explain

This package includes the majority of explanation tools for explaining 
Keras models predictions. Currently, only models with images on input are 
supported.
It supports following approaches:

Gradient methods:

- GradCam
- Guided GradCam
- Guided back-propagation
- Integrated gradients
- Saliency
- Layer-wise relevance propagation [BETA]

Model-independent methods:
- Prediction difference
- Basic graying out
- LIME

All approaches are easy to apply to your model in two lines of code. 
If you have any suggestion for new approaches to be included in the package
please do not hesitate to suggest. Also all improvements suggestions, bug reports and bug fixes are welcome. 

Right now we are in the process of implementing the following approaches:

- Meaningful perturbation by Fong et al.
- Layer-wise relevance propagation - we are adding layers that are not supported
yet. 

## Usage

### Gradient methods

#### GradCam

    from keras_explain.grad_cam import GradCam
    
    explainer = GradCam(model, layer=None)
    exp = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class
- `layer` - (optional) The index (index in model.layers) of the layer which 
prediction is explained. 
If not specified the last layer prediction is explained automatically.

Output:

- `exp` - explanation. GradCam mark only features which contribute to the 
classification in a `target class`. 

#### Guided GradCam

    from keras_explain.grad_cam import GuidedGradCam

    explainer = GuidedGradCam(model, lyer=None)
    exp = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class
- `layer` - (optional) The index (index in model.layers) of the layer which 
prediction is explained. 
If not specified the last layer prediction is explained automatically.

Output:

- `exp` - explanation. GuidedGradCam mark only features which contribute to the 
classification in a `target class`. 

#### Guided back-propagation

    from keras_explain.guided_bp import GuidedBP

    explainer = GuidedBP(model)
    exp = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class

Output:

- `exp` - explanation. Guided back-propagation mark only features which 
contribute to the classification in a `target class`. 

#### Integrated gradients

    from keras_explain.integrated_gradients import IntegratedGradients
    
    explainer = IntegratedGradients(model)
    exp = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class

Output:

- `exp` - explanation. Integrated gradients mark only features which contribute 
to the classification in a `target class`. 

#### Saliency

    from keras_explain.saliency import Saliency

    explainer = Saliency(model, layer=None)
    exp = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class
- `layer` - (optional) The index (index in model.layers) of the layer which 
prediction is explained. 
If not specified the last layer prediction is explained automatically.

Output:

- `exp` - explanation. Saliency mark only features which contribute 
to the classification in a `target class`. 

#### Layer-wise relevance propagation [BETA]

This approach does not support all layers yet. We are currently implementing
missing layers. If you wish you can implement any layer support yourself
and submit it as a pull request. Since implementation is very custom any
suggestion for improvement is welcome.

    from keras_explain.lrp import LRP

    explainer = LRP(model)
    exp = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class

Output:

- `exp` - explanation. LRP mark only features which contribute 
to the classification in a `target class`. 

###Model independent approaches

#### Prediction difference

    from keras_explain.prediction_diff import PredictionDiff

    explainer = PredictionDiff(model)
    exp_pos, exp_neg = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class

Output:

- `exp_pos` - explanation with marked features which contribute 
to the classification in a `target class`. 
- `exp_neg` - explanation with marked features which contribute 
against the classification in a `target class`.

#### Basic graying out

    from keras_explain.graying_out import GrayingOut

    explainer = GrayingOut(model)
    exp_pos, exp_neg = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class

Output:

- `exp_pos` - explanation with marked features which contribute 
to the classification in a `target class`. 
- `exp_neg` - explanation with marked features which contribute 
against the classification in a `target class`. 

#### LIME

    from keras_explain.lime_ribeiro import Lime

    explainer = Lime(model)
    exp_pos, exp_neg = explainer.explain(image, target_class)
    
Parameters:

- `model` - Keras model which is explained
- `image` - input which prediction is explained
- `target_class` - approach explains prediction for a target class

Output:

- `exp_pos` - explanation with marked features which contribute 
to the classification in a `target class`. 
- `exp_neg` - explanation with marked features which contribute 
against the classification in a `target class`.
