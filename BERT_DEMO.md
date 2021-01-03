https://github.com/google-research/bert#pre-trained-models         
BERT是基于tensorflow 1开发的: “This code was tested with TensorFlow 1.11.0”         
```         
conda create --name tf1 python=3.6         
conda activate tf1         
pip install tensorflow==1.11.0                  
pip install -U bert-serving-server bert-serving-client         
```      
到上面的链接下载一个bert model到本地，替换下面命令中的model_dir，然后启动Server
sentence embedding模式: `bert-serving-start -model_dir /Users/andrew/jiuzhang/seq2seq/models/bert_uncased_L-12_H-768_A-12/ -num_worker=1`                 
word embedding模式: `bert-serving-start -pooling_strategy NONE -model_dir /Users/andrew/jiuzhang/seq2seq/models/bert_uncased_L-12_H-768_A-12/ -num_worker=1`       


从Client发送请求:          
```
from bert_serving.client import BertClient         
client = BertClient()         
vectors = client.encode(['First do it', 'then do it right', 'then do it better'])         
```
