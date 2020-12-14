# Image-Processing-Project

This is part of Image Processing Project. This is actually a part of the project of my team: Face-Mask Detection.
</br>The project overall development is divided into 3 parts:-
<ul>
  <li>Image Processing</li>
  <li>Feature Selection</li>
  <li>Model Training (Classification model used: RandomForest Classification)
</ul>
</br>
<h1>Motivation</h1>
The sole purpose is to help our frontline warriors in anyway possible This model can be used to detect whether a particular person is actually wearing mask or not. Before actual 
starting working in the project, we have divided our part into three groups: Data Augmentation, Face Detection, Face-Mask Detection. The whole working can be checked in 
<a href="https://fierce-forest-62094.herokuapp.com/">here</a>.
<h1> Dataset Used</h1>
For model development, I have used the dataset having 2 main domains: with-mask and without mask.
<br/><ins>About Dataset:</ins>
<br/> The dataset contains around 7600 images out of which around 3700 are with masks and 3800 are without masks.
<br/>The Dataset is not balanced, this actually works for better results since this will help to extract only certain differnces and train itself accordingly.
<br/> You can find dataset <a href="https://www.kaggle.com/omkargurav/face-mask-dataset">here</a>.
<h1>Model Used</h1>
I am part of the Group: Face-Mask Detection, Here all three of us have implemeted the same working model via three different models. I have implemented via 
RandomForest. 
<br/><ins>Why Random Forest?</ins>
<br/> Random Forest is an ensemble algorthim. Here for the development of model, forest of Descision Trees is used. Therfore, this model works effectively for the classification.

<h1>Different Feature Selection techniques with their Working </h1>
<ul>
  <li>
    <h3>sklearn.feature_selection.SelectFromModel</h3>
        Here, the feature selection is done via comparison of weights with the threshold value we provide and accordingly prune those having weights less than threshold and 
        keeping all others. 
        </br>First we need to provide the estimator or the classification algorithm on which we are actually developing the model. In our case, we are using RandomForest, 
              therefore, this will be the estimator. Now when we are talking about weights of features, these are usually less for images-type dataset. So, we have given the 
              threshold as: 0.0001
         </br> <b>How this weighting features actually happens</b>
         </br>The RandomForest that we have taken for training uses the concepts of 'Embedded Methods' that include 2 things:
  <ul>
    <li><ins>Filter:</ins> This uses the correlation to find importance of features</li>
    <li><ins>Wrapper:</ins> This uses the concept of usefulness after actual training happens. After training, the model assigns weights and importance of the features.</li>
  </ul>
  So, the selectionFromModel uses the weights we get from RandomForest and compare it with threshold value we set and prune all those having less than the threshold.
  </li>
  
  <li>
  <h3>sklearn.feature_selection.RFE</h3>
      This feature elimination used greedy search to find the best performing feature dataset. The goal is to select features by recursively considering smaller and smaller 
      datasets. Here, we first need to give estimator, RandomForest, in our case, then, the selection is done either by taking coef_ into consideration or feature_importances_.
      Here, we have the flexibility to determine the number of features to prune after each step as well as number of features at the end of the process (If not given,               selection will reduce to half the size).
  </li>
  <li>
    <h3>sklearn.feature_selection.RFECV</h3>
    Here, we rank features based on recursive feature elimination and cross-validated selection of the best number of features. Here, we have cv as an extra feature in RFE,        where it takes 5 as default and we can give n-Strategicfolds.<br/>
  <b><ins>Cross-validation estimator:</b></ins> This estimator built-on cross-validation capabilties to automatically select the best hyper-parameters.The advantage of using   this estimator that we can use pre-computed results in the previous steps of the cross-validation process. This generally leads to speed improvements. 
  </li>
</ul>
<h1>Implementation</h1>
I have divided woking model into three parts as I have mentioned before.
<ol>
  <li> <h3>Image Pre-Processing</h3>
        <ul>
          <li>For Image Pre-Processing, I have first scaled my Image from RGB into Gray-scale. Reason behind this is that for the model that I am trying to build, colors do not 
          play much significiant role. 
          <li>
          Image size has been changed to reduce the overall computation.
        </ul>
  </li>
  <li>
    <h3>Feature Selection</h3>
        Feature Selection in literal terms means to select only those features that are actually required for overall model development and extractiong all other that are not. Now
        this actually helps us to reduce the computational cost of model training, also sometimes, by doing this, the features that are actually important, leads to even better 
        accuracy.
        <br/>How this is achieved?
        <br/> For implementing this, I have used python inbuilt library for feature Selection. For threshold, I have set it to: 0.0001. Now doing this, all featured values 
        lesser than this threshold will be dicarded and others having greater than threshold are stored. 
  </li>
  <li>
    <h3> Model Training </h3>
  Now after Image Pre-Processing and Feature Selection, all we are left with actual model training. For this I have used 300 Descsion trees and criterion: entropy (since this 
  crtiterion works well for information gain.).
  </li>
</ol>
<h1>Further Improvement</h1>
<p>
  For this, I have developed Web-App which one can use to classify same. Visit <a href="https://github.com/mehulraj19/Image-Processing-Project-WebApp">here</a> to get the code.
</p>
<h1>Results</h1>
I have compared the the training accuracy before and after feature selection. 
<ul>
  <li> Without Feature Selection: 85.84% </li>
  <li>With Feature Selection (using SelectionFromModel): 86.24%</li>
<ul>
<br>

