21:39 从训练营的分享中学习
https://github.com/lonePatient/BERT-NER-Pytorch
bert：google-bert/bert-base-chinese

2024/07/29 
新增ner_seq_bio.py 针对bio做特殊处理
train 参数
--task_name=cner
--data_dir=./datasets/cner
--model_type=bert
--model_name_or_path=google-bert/bert-base-chinese
--output_dir=./result/
--do_train
--overwrite_output_dir
需要修改codeing：encoding="utf-8-sig"
7/30
test（predict)
--task_name=cner
--data_dir=./datasets/cner
--model_type=bert
--model_name_or_path=google-bert/bert-base-chinese
--output_dir=./result/
--do_predict
--overwrite_output_dir
--markup=bio

生成result文件用于评估


7/31
问题：
1 . test文件第一行被跳过
2 . 特殊字符串处理：'”','“'和 '\t' 
ner2

特殊字符是否可以扩展字典?

测试一组无标注的文本

新增参数：data_type=predic
test或者predic
--task_name=cner
--data_dir=./datasets/cner3
--model_type=bert
--model_name_or_path=google-bert/bert-base-chinese
--output_dir=./result/
--do_predict
--data_type=predic
--overwrite_output_dir
--markup=bio

--8/4的备份：

--task_name=cner
--data_dir=./datasets/cner2
--model_type=bert
--model_name_or_path=google-bert/bert-base-chinese
--output_dir=./result/
--do_predict
--overwrite_output_dir
--markup=bio

8/8 ：加油，最后冲刺。
1. 准备bert论文数据
2. 语料 MSRA
3. 高质量语料： 打标

bert restart
1. 新建文件夹:.\brandnewresult\bert
2. 训练文件夹：./datasets/cner4，将train，test,和dev文件放入
3. 
--task_name=cner
--data_dir=./datasets/cner4
--model_type=bert
--model_name_or_path=google-bert/bert-base-chinese
--output_dir=./brandnewresult/
--do_train
--overwrite_output_dir
---结果文件： bert-cner-2024-08-08  23：05前：数据很差呀 averageloss 为inf ，为啥呢....


8.9.。。。不想重新弄Bert了额，直接拿之前的结果做数据

直接测test test_257.txt
--task_name=cner
--data_dir=./datasets/cner4
--model_type=bert
--model_name_or_path=google-bert/bert-base-chinese
--output_dir=./brandnewresult/
--do_predict
--overwrite_output_dir
--markup=bio


8/25

寻找更好的语料
git@github.com:liucongg/NLPDataSet.git
第一次效果一般

[20240825_210004_dairy_2014_train.txt](..%2FPackage2%2FPackage%2FBaseline%2Fmodel%2Fdata%2Ftrainlog%2F20240825_210004_dairy_2014_train.txt)

调整了数据抽取方式（train2=train_file_2），大集合取1：9，小集合取1：9，效果不明显

调整validation-every和batch-size: --batch-size:128 --validation-every2500 效果很好哦


8/27 去掉数据抽取方式

10/7
从头开始，
Train：训练集 8:2
  ***** Eval results  *****
10/07/2024 12:01:25 - INFO - root -    acc: 0.9167 - recall: 0.9247 - f1: 0.9207 - loss: 5.0209 
10/07/2024 12:01:25 - INFO - root -   ***** Entity results  *****
10/07/2024 12:01:25 - INFO - root -   ******* DATE results ********
10/07/2024 12:01:25 - INFO - root -    acc: 0.8858 - recall: 0.9078 - f1: 0.8967 
10/07/2024 12:01:25 - INFO - root -   ******* LOC results ********
10/07/2024 12:01:25 - INFO - root -    acc: 0.8949 - recall: 0.9079 - f1: 0.9013 
10/07/2024 12:01:25 - INFO - root -   ******* ORG results ********
10/07/2024 12:01:25 - INFO - root -    acc: 0.8973 - recall: 0.9055 - f1: 0.9014 
10/07/2024 12:01:25 - INFO - root -   ******* PER results ********
10/07/2024 12:01:25 - INFO - root -    acc: 0.9856 - recall: 0.9818 - f1: 0.9837 

predict:
