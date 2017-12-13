---
layout:     post   				    # 使用的布局（不需要改）
title:		导出自己训练的tensorflow模型，并移植到android studio 				# 标题 
subtitle:    #副标题
date:       2017-12-13 				# 时间
author:     woniuzai						# 作者
header-img: img/post-bg-2015.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - tensorflow
    - android
---

# 导出自己训练的模型
## 环境
tensorflow 0.12，python2.7.11

### 导出模型
网上有很多导出模型的介绍，我采用的是一下方法：
    
    saver = tf.train.Saver(tf.global_variables())
    saver.save(sess, 'test/lstm.chkp')
    tf.train.write_graph(sess.graph_def, './test', 'lstm.pb', as_text=True)writer.close()
    
这样就可以在指定目录下看到chpt meta index等文件，之后采用官方的freeze.py脚本进行固化（自己先要下载这个脚本，在GitHub上有），执行一下命令：
    
    python freeze_graph.py --input_graph=test/model_age.pb --input_checkpoint=test/glasses_age.chkp --output_graph=test/frezen_model_age.pb --output
得到指定的frezen_model_age.pb文件，这个文件就是固化的模型以及参数，可以移植到手机上执行。
# android studio准备
1 将刚才固化的pb文件放在asserts目录下（没有就创建）
2 导入libtensorflow_inference.so到jnilib目录
3 导入libtensorflow_inference.jar到libs目录，具体导入方法自行百度
这样就可以使用训练好的模型了,，主要包含以下函数：

    inferenceInterface = new TensorFlowInferenceInterface(assetManager,MODEL_PATH);
    inferenceInterface.feed(INPUT_NAME,inputs,WIDTH,HEIGHT);
    inferenceInterface.run(outputNames);
    inferenceInterface.fetch(OUTPUT_NAME,outputs);

# 问题解决
我使用的LSTM模型，导入的时候出现[这里](https://github.com/tensorflow/tensorflow/issues/9699)的问题，然后通过修改得以解决
    
    lstm_cell.zero_state(tf.shape(self.xs)[0], dtype=tf.float32)




