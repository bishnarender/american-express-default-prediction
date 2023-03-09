# american-express-default-prediction
## 10th place score achieved.
![amex_submission](https://user-images.githubusercontent.com/49610834/224013039-21f119fe-fa9c-4769-8480-540791432254.png)

-----

### Start 
For better understanding of project, read the files in the following order:
1. eda.ipynb
2. amex.ipynb 
3. lgb_pre.ipynb
4. amex_2.ipynb
5. lgb_main.ipynb
6. nn_main.ipynb
7. inference.ipynb

-----

### amex.ipynb
Feature engineering part is performed in this file.<br />
Those who have memory restriction can use 'amex_pola_rs.ipynb' insted of this.<br />
'amex_pola_rs.ipynb' uses polars library for feature creation.

![feat_engg_1](https://user-images.githubusercontent.com/49610834/224014110-650d3665-17a3-47d8-bc81-a3b0e897b220.jpg)

![feat_engg_2](https://user-images.githubusercontent.com/49610834/224014128-23a3b1b2-5dc1-47f2-bbfa-1e6a04ad2759.jpg)

![feat_engg_3](https://user-images.githubusercontent.com/49610834/224014182-2125af15-e582-466f-a4a0-de8d6b035322.jpg)

-----

### lgb_pre.ipynb
LightGBM was trained initially on raw data to create "target features" on series data. Here, "series" is used to represent the repetition of "customer_Id" in raw data. 

![feat_engg_4](https://user-images.githubusercontent.com/49610834/224014200-636deb30-7fa8-4191-ba61-28ac0f06a044.jpg)

-----

### amex_2.ipynb
All features are concatenated in this file.

-----

### lgb_main.ipynb
LightGBM was finally trained on "manual features" + "target features". Single model was trained on two types of data.<br />
One type have only "manual features".<br />
Second type have both "manual features + target features".

-----

### nn_main.ipynb
A neural network was also trained on "modified raw data","manual features" and "target features". Single model was trained on two types of data.<br />
One type have only "modified raw data".<br />
Second type have all "modified raw data + manual features + target features".<br />
Modified raw data is a histogram formulation on raw data.<br />

Model architecture.
![model](https://user-images.githubusercontent.com/49610834/224018286-b40fbc28-0f70-4b68-8f97-e4924601347f.jpg)

-----

### metric
![metric_1](https://user-images.githubusercontent.com/49610834/224019520-afcb6af9-959f-4ac2-a0d7-23b677f11a6a.jpg)
![metric_2](https://user-images.githubusercontent.com/49610834/224019539-f90f3f8e-2143-46df-8855-a65a9dfb65e8.jpg)

-----

### inference.ipynb
Ensemble of models on a "hit and trial" basis. First pickup 2 models of LGM for modification. Freeze the scores of the other two NN models. Tuning process:
1. In the 1st step, increase the gap between scores of both models. Monitor the score.
2. In the 2nd step, decrease the gap between scores of both models. Monitor the score.
3. In the 3rd step, increase scores of both models. Monitor the score.
4. In the final step, decrease scores of both models. Monitor the score.

Repeat the same tuning process with 2 models of NN, keeping scores of 2 models of LGM freezed.

-----

### Future scope
1. use some developed and approved method on too many missing feature values.<br />

**Note:**  all images used here are present in images folder.
