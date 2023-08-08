# Kaggle_Titanic_Learn
Kaggle泰坦尼克生存预测

## 1、 数据加载

## 2、 数据探索
其中对Name字段内容做称谓提取，将称谓作为新列【称谓】，并将称谓归为 'Mr', 'Mrs', 'Miss', 'Master' 四种。

## 3、数据清洗

缺失字段有 3 个，Age 、 Fare 、 Embarked ，其中 Age 缺失数据最多，Fare 在测试集中缺失 1 条，Embarked 在训练集中缺失 2 条。

以平均值补充 Fare ,以最多值补充 Embarked 。

Age 字段补充有两种处理方式
1. 以AGE平均值进行填充
2. 以称谓分组，并以其分组的平均值填充

对平均值补充 Age 训练数据(data_train_3_1)和按照 称谓 字段的各平均值补充各称谓的 Age 训练数据(data_train_3_2)进行one-hot处理，再对这两种训练集分别进行MinMax和Z-score处理。

data_train_features_scaler_3_1_1 平均值填充Age onehot+MinMax处理

data_train_features_scaler_3_2_1 按称谓平均值填充Age onehot+MinMax处理

data_train_features_scaler_3_1_2 平均值填充Age onehot+Z-score处理

data_train_features_scaler_3_2_2 按称谓平均值填充Age onehot+Z-score处理

舍弃PassengerId、Survived、Name、Cabin列。

## 5、模型建立

建立模型和对应的参数范围
使用的模型有决策树、SVM、KNN、AdaBoost、随即森林、逻辑回归。

使用GridSearchCV结合K折交叉验证寻找最优参数，画出ROC曲线并计算AUC面积，取最大AUC面积的模型进行测试集预测。

![image](https://github.com/xiaocai3587/Kaggle_Titanic_Learn/assets/37061368/8a8aff5c-6415-471d-a306-1dc0bd924ffb)
