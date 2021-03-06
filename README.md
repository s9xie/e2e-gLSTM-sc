This repository includes the code for end-to-end gLSTM and sentence-conditional semantic attention, as appeared in the paper "[Watch What You Just Said: Image Captioning with Text-Conditional Attention](https://arxiv.org/abs/1606.04621)". train_new.lua is the main file for e2e-gLSTM and train_sc.lua is the main file for sentence-conditional semantic attention. Here are the example commands:
```
th train_new.lua -cnn_model_resnet /path/to/your/resnet-200-model -language_eval 1 -finetune_cnn_after 100000 -max_iters 600000 -cnn_weight_decay 0.001 -cnn_learning_rate 0.00001 -learning_rate_decay_every 100000 -learning_rate_decay_start 100000
```
```
th train_sc.lua -start_from /path/to/your/e2eglstm-checkpoint -language_eval 1 -language_model 'misc_tc.LanguageModel_sc' -max_iters 200000
```
Note that if you transfer weights from vgg-16 or resnet-34, the -max-iters values could be smaller. The result table is shown below.

| Methods |Bleu@4 |METEOR |  CIDEr|
|:-------:|:-------:|:-------:|-----:|
| sc-vgg-16 | 30.1 | 24.7 | 97.0 |
| sc-resnet-34 | 30.6 | 25.0 | 98.1 |
| sc-resnet-200 | 31.6 | 25.6 | 101.2 |

The implementation is based on [Neuraltalk2](https://github.com/karpathy/neuraltalk2). Please follow the instructions on Neuraltalk2 to run the code. [Contact me](http://luoweizhou.net/contact.html) if you have any trouble running the code . Please cite the following paper if you are using the code.
```
@article{zhou2016image,
  title={Image Caption Generation with Text-Conditional Semantic Attention},
  author={Zhou, Luowei and Xu, Chenliang and Koch, Parker and Corso, Jason J},
  journal={arXiv preprint arXiv:1606.04621},
  year={2016}
}
```
