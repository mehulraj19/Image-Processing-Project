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
<br/><u>About Dataset:</u>
<br/> The dataset contains around 7600 images out of which around 3700 are with masks and 3800 are without masks.
<br/>The Dataset is not balanced, this actually works for better results since this will help to extract only certain differnces and train itself accordingly.
<h1> Dataset Used</h1>
For model developmen, I have used the dataset having 2 main domains: with-mask and without mask.
<br/> You can find dataset <a href="https://www.kaggle.com/omkargurav/face-mask-dataset">here</a>
<h1>Model Used</h1>
I am part of the Group: Face-Mask Detection, Here all three of my group members have implemeted the same working model via three different models. I have implemented via 
RandomForest. 
<br/><u>Why Random Forest?</u>
<br/> Random Forest is an ensemble algorthim. Here for the development of model, forest of Descision Trees is used. Therfore, this model works effectively for the classification.
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
    <h1> Model Training </h1>
  Now after Image Pre-Processing and Feature Selection, all we are left with actual model training. For this I have used 300 Descsion trees and criterion: entropy (since this 
  crtiterion works well for information gain.).
  </li>
</ol>
<h1>Results</h1>
I have compared the the training accuracy before and after feature selection. 
<ul>
  <li> Without Feature Selection: 85.84% </li>
  <li>With Feature Selection: 86.24%</li>
<ul>
