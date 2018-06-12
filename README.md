# Intern program at VoxelCloud 
The exon 19 and 21 in Epidermal Growth Factor Receptor (EGFR) mutation are the most common subtype of lung adenocarcinoma.
EGFR mutation was reported significantly related with some CT features[1].

The raw dataset is uploaded as 'eye recognition.xlsx' which contains 36 columns and 360 samples.
The dataset contains:
CTnumbers
name
gender
age
smoker
部位：lobe
形状：tumour shape
肿瘤最大径(mm)：maximum tumour diameter(mm)
肿瘤体积: tumour volume
边缘: margin, 0 is smoothed, 1 is unsmoothed
分叶征
毛刺征
磨玻璃影
密度: density
空泡
空洞
空气支气管征
胸膜增厚
肿瘤坏死
卫星结节
结节
胸膜凹陷征
钙化
肺气肿
纤维化
转移情况
肺门淋巴结肿大
纵隔淋巴结肿大
增强幅度
病理: pathology
18号: EGFR mutation of Exon18 status
19号: EGFR mutation of Exon19 status
20号: EGFR mutation of Exon20 status
21号: EGFR mutation of Exon21 status

19 and 21 are two outcome labels.
Density, age and maximum diameters are continuous variables while others are binary variables.

Firstly I did preprocessing:
1. Take a look at unique values of each column and recode them.
2. For lobe(部位), merge 16 unique values into 5 categories: LUL,LLL,RML,RLL,RUL.
3. For shape(形状), merge 12 unique values into 4 categories: 类圆形, 团片状, 斑片状, 不规则
4. For pathology, merge 27 values into 4 categories: 腺癌, 鳞癌, 腺鳞癌, 多形性癌
5. Some values in margin(边缘) will be recoded to 0 and 1.
6. Values in Gender will be recoded to 0 for male and 1 for female.
7. Remove CTnumber, name, volume, 转移情况, 增强幅度, ATK from our training features.Remove exon18 and 20 from our outcome variables.
8. Fill missing values in age with mean and that in other binary variables with 0. Drop two lines which contain missing values in outcome.
9. Prepare summary table to show mean values for continuous observations and count numbers for binary observations.
10. Apply one-hot encoding on categorical variables and min-max scaler on continuoues variables.
11. Resample observations from minority class 1 for exon19 and exon21 to make sure two classes are balanced.
12. Split dataset into 80% train and 20% test subsets in a straitified fashion.


Then I applied machine learning algorithms such as logistic regression,SVM ,adaboost,random forest on  selected features to train models to predict correct mutation status.





[1]Lee, H. J. et al. Epidermal growth factor receptor mutation in lung adenocarcinomas: relationship with CT characteristics and histologic subtypes. Radiology 268, 254–264, doi:10.1148/radiol.13112553 (2013).
