# 数据挖掘与知识发现

2023-2024秋季学期东北大学数据挖掘与知识发现课程大作业

> 本次测试做一个多标签情绪题，具体地，将情绪分析问题视为一个分类问题。训练集的属性集合为<ID，Text，Labels>，学生下载训练集后，可以采用任意的方法（传统的特征工程、表示学习技术等）对Text进行处理，获得Text的特征表示；采用任意的机器学习或深度学习方法训练一个分类模型（也可以训练多个进行比较或集成）。注意：要考虑多标签的处理。待测试集<ID，Text>发布后，在规定的时间内提交结果<ID，Labels>。评价方式采用recall、precision、F-score机制。

## 项目说明

1. 数据集在[data](./data/)目录下，其中[Train.csv](./data/Train.csv)是训练集，有标签；[test.csv](./data/test.csv)是测试集，没有标签；[example.csv](./data/example.csv)是提交的格式示例，也是评测机baseline，注意上述文件的编码格式未必是utf8，读取文件时要注意

2. [ckpt](./ckpt/)目录下保存的是训练好的模型，但由于作者恶劣的实验管理习惯，这个模型是最后一组测试对应的权重而不是评分最高的权重

3. [submissions](./submissions/)目录下保存了每次提交的（模型预测结果）文件和最终的评测集得分

4. [ernie](./ernie/)和[textcnn](./textcnn/)目录保存模型的实现代码，需要说明的是受时间限制，textcnn没有完全实现（不然得分可能不会这么难看），受算力限制，ernie使用paddlenlp实现，在baidu aistudio上训练和测试，对于环境配置的说明见下

## 环境和代码说明

如上，算力限制，本项目使用的模型通过paddlenlp实现并在aistudio上训练和测试，aistudio可选gpu包括V100 16GB、V100 32GB和A100 40GB，微调时选V100 16GB即可。

截止至本文档更新时，paddlepaddle框架的可选版本已更新至2.6.0，代码编写时最高可选版本为2.5.2，但测试发现2.5.x版本paddlepaddle与paddlenlp存在冲突，从而选用paddlepaddle 2.4.0，（需要看考虑版本冲突）具体版本如下表：

|包名|版本|
|---|---|
|paddle（paddlepaddle-gpu）|2.4.0.post112|
|paddlenlp|2.4.2|
|paddlehub|2.3.0|

需要特别说明的百度官方关于paddlepaddle和paddlenlp环境的配置文档已经严重过时，任何在本地配置上述环境的想法必须以相当的耐心、丰富的环境配置经验（尤指cuda、conda和docker）和熟练的github issue使用技巧为基础。

代码中的可变字段（包括数据集读取路径、结果保存路径、模型超参数等）未必和最好评测机得分结果一致，如有需要请自行修改。

## Maintainer

[@hilinxinhui](https://github.com/hilinxinhui)

## LICENSE

[MIT](./LICENSE)