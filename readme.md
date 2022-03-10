[MarkdownFile Edit Help](https://www.runoob.com/markdown/md-image.html)  

[Git Tuturial](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/Git_Tuturial.md)  

# Git File Sturcture
```Python
~/304lab$ tree
.
├── 304lab_Schedual#长期项目论文日程、截至等
│   ├── 2022 April Schedual.md
│   ├── 2022 March Schedual.md
│   └── ...
├── Projrct#具体项目代码、数据集、截图、计划及状态
│   ├── Project1
│   │   ├── Code
│   │   ├── Dataset
│   │   ├── img
│   │   ├── Plan and Status.md
│   │   └── Readme.md
│   ├── Project2
│   │   ├── ...
│   ├── Project3
│   │   ├── ...
│   └── Project4
│           ├── ...
├── Readme.md
└── Study#学习资料共享
    ├── px4_env_build
    │   ├── img
    │   └── px4_env_build.md
    ├── RosMavros_env_install
    │   ├── img
    │   └── RosMavros_env_install.md
    └── Ros_tuturial
        ├── Demo_code
        │   ├── Code
        │   └── DataSet
        ├── img
        └── Ros_tuturial.md
```


|2022 Feb| 21th | 22th | 23th | 24th | 25th | 26th | 27th |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|Task|1.Prepare Materials<br>2.Making Plan<br>3.Update Plan|1.xxx<br>2.xxx||1.xxx<br>2.xxx||1.xxx<br>2.xxx|1.Prepare Materials <br> 2.Create .pth model|1.Transfer .pyh model to ONNX model|||
|Status|Done|Delaying|Delaying|Delaying|Done|Done|Done|
|Note||xxx|xxx|xxx|xxx|xxx|||

> Data: February 2th Week
>> Task:Convert the ONNX model  
>> Aim: transfer the newest model which havent been supported by jeston to ONNX model  
>> Status: Done
>>> **Work:**  
>>>1. how to Create an ONNX model： use PyTorch create an ONNX model
>>>2. Start to learn [PyTorch](https://pytorch.apachecn.org/#/docs/1.7/04)
>>>3. Skim [weblinks](https://www.google.com.hk/search?q=pytorch%E5%A6%82%E4%BD%95%E7%94%9F%E6%88%90ONNX%E6%A8%A1%E5%9E%8B&client=ubuntu&hs=wDW&ei=YIsCYumvM5G5mAW-pLu4Bw&ved=0ahUKEwjp3_mZtfD1AhWRHKYKHT7SDncQ4dUDCA4&uact=5&oq=pytorch%E5%A6%82%E4%BD%95%E7%94%9F%E6%88%90ONNX%E6%A8%A1%E5%9E%8B&gs_lcp=Cgdnd3Mtd2l6EAM6BAgAEEM6BQgAEIAEOgYIABAHEB46AggASgQIQRgASgUIQBIBMUoECEYYAFAAWLg9YK0_aAJwAXgEgAHIBogB5kOSAQwyLTIxLjMuMi4yLjGYAQCgAQHAAQE&sclient=gws-wiz)
>>>4. With [PyTorch Tutorial](https://pytorch.apachecn.org/#/docs/1.7/06) and above weblinks , we have konwn that PyTorch can Create .pth models and transfer .pth models to ONNX models.Therefore , we can  **customize the neural network model** and then transform it into ONNX model.   
>>>
>>Note : none

