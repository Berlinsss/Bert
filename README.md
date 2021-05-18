# bert

代码基于Google开源的[BERT](https://github.com/google-research/bert)代码进行了进一步的简化，方便生成句向量与做文本分类
Tensortflow版本：1.13.1（可直接使用Pycharm生成虚拟环境，匹配‘requirement.txt’文件，配置环境）

1、下载BERT中文模型（已下载添加） 

下载地址: https://github.com/google-research/bert

2、把下载好的模型添加到当前目录下（已下载添加）

3、句向量生成

生成句向量不需要做fine tune，使用预先训练好的模型即可，可参考`extract_feature.py`的`main`方法，注意参数必须是一个list。

首次生成句向量时需要加载graph，并在output_dir路径下生成一个新的graph文件，因此速度比较慢，再次调用速度会很快
```
from bert.extrac_feature import BertVector
bv = BertVector()
bv.encode(['今天天气不错'])
```
具体参考run.py，生成向量
另需要修改`extract_feature.py`中`predict_from_queue方法`，保存生成的向量
