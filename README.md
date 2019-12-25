#  图书馆小助手APP PRD


|   发布日期      | 2019/12/16    | 
| --------   | -----:  | 
| Epic         | 图书馆小助手APP     | 
| 文件现状       | 进行中    | 
| 文件主人       | 余杭宏    | 
| 文件设计师     | 余杭宏    |
| 文件开发者     | 余杭宏    |
| 文件测试者     | 余杭宏  |

##  PRD1.加值宣言 3%
-  本APP（小程序）旨在通过整合各种API，使它们组合起来发挥出更大的作用，进而方便游客解决在参观中遇到的问题。APP（小程序）获得游客目前的定位信息，返回游客目前的位置的周边服务设置的位置信息并提供简单的导航。帮助用户更加快速、方便地找到服务设施或展品。
















#  一、使用者需求概述
-  目标用户：来图书馆的用户
-  功能使用场景描述：   
（1）用户来到图书馆，在观看文章时，不想阅读文字，可使用图书馆app进行智能语音交互将文字转为语音。       
（2）当外国用户来到图书馆时，对书本的中文理解存在障碍，可使用图书馆的APP进行机器翻译。      
（3）用户来到图书馆，但不清楚自己事先想了解的书籍位置在哪，这时可通过图书馆的app对书籍图像进行搜索，显示出相对应的位置使用户能迅速到达。   
-  优先级：    
高–1.图像识别搜索书籍，反馈书籍方位，使用户迅速到达     
2.书籍信息的自定义语言翻译        

低–1.图像识别搜索书籍，显示书籍基本信息      
2.智能语音交互将语音转为交互    
#  二、产品主要概述总结    

-  本APP（小程序）旨在通过整合各种API，使它们组合起来发挥出更大的作用，进而方便游客解决在参观中遇到的问题。     

-  我们使用阿里的语音交互API及地图API，将展品的介绍以语音形式播放给用户（需要佩戴耳机），更好的分配了游客的听觉和视觉。使用户体验过程中可以不用阅读大量的文字信息，注重在书籍本身。同时还具有语音问答功能，用户可以向该软件提问，例如：怎么走到3号图书馆？能向我介绍一下编号xxx的书籍吗？等等。   

-  APP的云端服务器内储存了该图书馆的所有书籍图片及信息，我们利用图像识别API，给用户一个更好的搜索方式。用户有多种方式来找到目标书籍，一是基本搜索，在APP现有的数据中搜索，二是对着书籍或者书籍图片拍照，使用图像识别API来对比数据库内的书籍，得出的结果以相似度从高至低排列。从而得知目标书籍位置，配合地图API进行语音导航。     

-  整个APP都可以随时调用翻译API，默认语言是手机系统语言，如需要显示默认语言或翻译成其他语言，只需要长按文字就可进行翻译。     

 #  三、功能详情与整合功能

##  功能一：书籍介绍及寻找

用户使用APP上传书籍图片，会自动生成当前位置到该书籍的介绍和地图线路。查看书籍介绍和地图线路。   


##  功能二：翻译

用户在使用app进行操作到信息内容页面后header部分会有语言栏进行语言选择，用户可以根据自己的需求选择语言，页面会根据选择的语言进行翻译。   

##  功能三：语音交互

用户打开智能语音交互界面，用语音的形式提出问题，APP会识别用户提出的问题，同时反馈相关的回答内容。    

##  APP上的体现

-  用于进入APP主界面，通过点击“书籍介绍及寻找”和“智能语音问答”按钮可以实现不同功能：   

-  1.首先点击“书籍介绍及寻找”按钮进入对应界面。用户通过上传书籍图片来实现“书籍介绍和寻找”功能；点击header可实现“翻译”功能。   

-  2.再点击“智能语音问答”按钮，用户进入问答界面，用户可通过发送语音获得信息的形式实现“智能语音问答”的功能。    

#  四、成本效益分析

##  成本分析：

-  （1）技术支持成本：包括程序初期开发成本，科研人员聘请成本，BUG修复成本。   

-  （2）维护管理成本：产品还在初级阶段，BUG较多，维修要加大成本投入以及及时对APP进行升级。   

-  （3）风险成本：由于APP处于开放性的网络下，因此APP可能存在着一些安全隐患。以及某些展品信息被盗用   

##  效益分析：

-  （1）通过图像识别，图书馆能够更好的方便参观者找到自己所想看的书籍位置，提供了更好的体验，给予用户便利。   

-  （2）通过机器翻译，图书馆能够方便更多外宾了解中国书籍介绍，解决了语言障碍的问题。   

-  （3）通过语音交互，图书馆能够使用户参与进来，提高图书馆与参观者的互动性，同时也能让外国来宾参与进来。   

-  （4）吸引不同国籍的用户一起观看，提高图书馆的知名度。   

-  （5）通过以上的功能改善，能够极大提高用户体验，同时提高图书馆的用户评价。   

#  五、产品原型流程图


     
