#  图书馆小助手APP PRD


|   发布日期      | 2019/12/16    | 
| --------   | -----:  | 
| Epic         | 图书馆小助手APP     | 
| 文件现状       | 进行中    | 
| 文件主人       | 余杭宏    | 
| 文件设计师     | 余杭宏    |
| 文件开发者     | 余杭宏    |
| 文件测试者     | 余杭宏  |

#  PRD 价值主张设计 15%
##  背景
-  现有大多数的图书馆仍然在使用旧式的图书馆导览地图，当用户目的性明确想要寻找某一本书籍时，用户一般只能查看地图、看提示牌或者询问工作人员寻找。另外，即使是寻找周边的服务设施（场馆、纪念品店、厕所等），这个过程也繁琐复杂。
-  现有的图书馆都有残障人士相关的服务设施如残疾人厕所、残疾人通道，大多数的服务设置在图书馆较隐蔽的地方。考虑残障人士身体原因运动不便，还是比较难获得相关的服务。
##  PRD1.加值宣言 3%
-  本APP（小程序）旨在通过整合各种API，使它们组合起来发挥出更大的作用，进而方便用户解决在图书馆中遇到的问题。
-  使用室内地图API以及普通IP定位API，设置图书馆地图并提供导航。APP（小程序）获得游客目前的定位信息，返回用户目前的位置的周边服务设置的位置信息并提供简单的导航。帮助用户更加快速、方便地找到服务设施或相关书籍。

##  PRD2.核心价值 3%

-  最小可行性分析：着眼于用户的基本，解决用户寻找服务设施难的问题，便利用户体验。    

| 用户        | 功能    | 重要程度     |
| --------   | -----:  | :----: |
| 目标明确用户        | 图像识别搜索书籍，反馈书籍方位     | 重要    |
| 残疾用户       | 提供残障服务设施的位置信息    | 重要     |
| 普通用户       | 地图API提供简单导航，显示周边服务设置  | 重要   |
| 全部用户       | 提供图书馆书籍的文字和语音介绍  | 次重要   |

##  PRD3.核心价值与用户痛点 3%
用户痛点：    
-  用户来到图书馆，但不清楚自己事先想寻找的书籍位置在哪     
-  当用户来到图书馆，服务设施众多，想去寻找自己想要的相关服务比较困难。
-  残障游客行动不便，残障服务设施一般在博物馆较隐蔽的地方，寻找起来比较困难。

| 用户        | 使用场景    | 用户需求     |
| --------   | -----:  | :----: |
| 目标明确用户        | 图书馆内     | 找到自己想要看的图书    |
| 残疾用户       | 图书馆内    | 找到残障服务设施 （轮椅出租、残障人通道）     |
| 普通用户       | 图书馆内  | 找到服务设施（厕所、礼品店、食品店）   |
| 全部用户       | 图书馆内  | 想要获得书籍的介绍信息   |

##  PRD4.人工智能概率性与用户痛点 3%
-  图像搜索有概率会因为用户拍照的角度不同或者光泽、像素不同导致返回的结果不同，从而影响到用户的体验
-  图片不完整，导致识别失败，影响到用户的体验

##  PRD5.需求列表与人工智能API加值 3%

|   需求      | API    | 
| --------   | -----:  | 
| 目标明确的用户找到自己想要看的图书         | 图像识别     | 
| 找到残障服务设施、服务设施       | 地图API    | 



#  原型 20%


-  还在完善


#  API 产品使用关键AI或机器学习之API的输出入展示 15%

##  API1.使用水平 5%
1.图像识别，目标明确的用户找到自己想要看的图书    
-  输入：书籍的封面图片或拍到的海报
-  输出：图书的基本介绍及在图书馆的导航位置    

2.地图API，找到残障服务设施、服务设施    
-  输入：用户当前位置
-  输出：用户周边的服务设施及残障服务设施

##  语音智能交互的输入

```
# coding=utf-8

import sys
import json
import time

IS_PY3 = sys.version_info.major == 3

if IS_PY3:
    from urllib.request import urlopen
    from urllib.request import Request
    from urllib.error import URLError
    from urllib.parse import urlencode

    timer = time.perf_counter
else:
    import urllib2
    from urllib2 import urlopen
    from urllib2 import Request
    from urllib2 import URLError
    from urllib import urlencode

    if sys.platform == "win32":
        timer = time.clock
    else:
        # On most other platforms the best timer is time.time()
        timer = time.time

API_KEY = '04gRhPzYRVf4pRdho5h6TGzg'
SECRET_KEY = 'PvPag0on9Fq1BbchpfUVdyAdn6OSp0mG'

# 需要识别的文件
AUDIO_FILE = './Desktop/16k.pcm'  # 只支持 pcm/wav/amr 格式，极速版额外支持m4a 格式
# 文件格式
FORMAT = AUDIO_FILE[-3:];  # 文件后缀只支持 pcm/wav/amr 格式，极速版额外支持m4a 格式

CUID = '123456PYTHON';
# 采样率
RATE = 16000;  # 固定值

# 普通版

DEV_PID = 1536;  # 1537 表示识别普通话，使用输入法模型。1536表示识别普通话，使用搜索模型。根据文档填写PID，选择语言及识别模型
ASR_URL = 'http://vop.baidu.com/server_api'
SCOPE = 'audio_voice_assistant_get'  # 有此scope表示有asr能力，没有请在网页里勾选，非常旧的应用可能没有

#测试自训练平台需要打开以下信息， 自训练平台模型上线后，您会看见 第二步：“”获取专属模型参数pid:8001，modelid:1234”，按照这个信息获取 dev_pid=8001，lm_id=1234
# DEV_PID = 8001 ;   
# LM_ID = 1234 ;

# 极速版 打开注释的话请填写自己申请的appkey appSecret ，并在网页中开通极速版（开通后可能会收费）

#DEV_PID = 80001
#ASR_URL = 'http://vop.baidu.com/pro_api'
#SCOPE = 'brain_enhanced_asr'  # 有此scope表示有asr能力，没有请在网页里开通极速版

# 忽略scope检查，非常旧的应用可能没有
# SCOPE = False


# 极速版

class DemoError(Exception):
    pass


"""  TOKEN start """

TOKEN_URL = 'http://openapi.baidu.com/oauth/2.0/token'


def fetch_token():
    params = {'grant_type': 'client_credentials',
              'client_id': API_KEY,
              'client_secret': SECRET_KEY}
    post_data = urlencode(params)
    if (IS_PY3):
        post_data = post_data.encode('utf-8')
    req = Request(TOKEN_URL, post_data)
    try:
        f = urlopen(req)
        result_str = f.read()
    except URLError as err:
        print('token http response http code : ' + str(err.code))
        result_str = err.read()
    if (IS_PY3):
        result_str = result_str.decode()

    print(result_str)
    result = json.loads(result_str)
    print(result)
    if ('access_token' in result.keys() and 'scope' in result.keys()):
        if SCOPE and (not SCOPE in result['scope'].split(' ')):  # SCOPE = False 忽略检查
            raise DemoError('scope is not correct')
        print('SUCCESS WITH TOKEN: %s ; EXPIRES IN SECONDS: %s' % (result['access_token'], result['expires_in']))
        return result['access_token']
    else:
        raise DemoError('MAYBE API_KEY or SECRET_KEY not correct: access_token or scope not found in token response')


"""  TOKEN end """

if __name__ == '__main__':
    token = fetch_token()

    """
    httpHandler = urllib2.HTTPHandler(debuglevel=1)
    opener = urllib2.build_opener(httpHandler)
    urllib2.install_opener(opener)
    """

    speech_data = []
    with open(AUDIO_FILE, 'rb') as speech_file:
        speech_data = speech_file.read()
    length = len(speech_data)
    if length == 0:
        raise DemoError('file %s length read 0 bytes' % AUDIO_FILE)

    params = {'cuid': CUID, 'token': token, 'dev_pid': DEV_PID}
    #测试自训练平台需要打开以下信息
    #params = {'cuid': CUID, 'token': token, 'dev_pid': DEV_PID, 'lm_id' : LM_ID}
    params_query = urlencode(params);

    headers = {
        'Content-Type': 'audio/' + FORMAT + '; rate=' + str(RATE),
        'Content-Length': length
    }

    url = ASR_URL + "?" + params_query
    print("url is", url);
    print("header is", headers)
    # print post_data
    req = Request(ASR_URL + "?" + params_query, speech_data, headers)
    try:
        begin = timer()
        f = urlopen(req)
        result_str = f.read()
        print("Request time cost %f" % (timer() - begin))
    except  URLError as err:
        print('asr http response http code : ' + str(err.code))
        result_str = err.read()

    if (IS_PY3):
        result_str = str(result_str, 'utf-8')
    print(result_str)
    with open("result.txt", "w") as of:
        of.write(result_str)
```

语音智能交互的输出
```

{"access_token":"24.da454ddfe5130c84fad9def39e4daad0.2592000.1581177593.282335-17543637","session_key":"9mzdX7uWO0Cz6TDVpB5MB9CKPrgZq+rffr76XfUbLbbAoufBo9CZMUBK\/iB67KdmrdTLxpIz8kx56uJ04tZQXscgMQwJVw==","scope":"audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test\u6743\u9650 vis-classify_flower lpq_\u5f00\u653e cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_\u5f00\u653eScope vis-ocr_\u865a\u62df\u4eba\u7269\u52a9\u7406 idl-video_\u865a\u62df\u4eba\u7269\u52a9\u7406","refresh_token":"25.798afc970f12210f89ce53efb00f6ca0.315360000.1893945593.282335-17543637","session_secret":"2dfbb02eb96a182fa679aede72a06cae","expires_in":2592000}

{'access_token': '24.da454ddfe5130c84fad9def39e4daad0.2592000.1581177593.282335-17543637', 'session_key': '9mzdX7uWO0Cz6TDVpB5MB9CKPrgZq+rffr76XfUbLbbAoufBo9CZMUBK/iB67KdmrdTLxpIz8kx56uJ04tZQXscgMQwJVw==', 'scope': 'audio_voice_assistant_get brain_enhanced_asr audio_tts_post public brain_all_scope picchain_test_picchain_api_scope wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test权限 vis-classify_flower lpq_开放 cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_开放Scope vis-ocr_虚拟人物助理 idl-video_虚拟人物助理', 'refresh_token': '25.798afc970f12210f89ce53efb00f6ca0.315360000.1893945593.282335-17543637', 'session_secret': '2dfbb02eb96a182fa679aede72a06cae', 'expires_in': 2592000}
SUCCESS WITH TOKEN: 24.da454ddfe5130c84fad9def39e4daad0.2592000.1581177593.282335-17543637 ; EXPIRES IN SECONDS: 2592000
url is http://vop.baidu.com/server_api?cuid=123456PYTHON&token=24.da454ddfe5130c84fad9def39e4daad0.2592000.1581177593.282335-17543637&dev_pid=1536
header is {'Content-Type': 'audio/pcm; rate=16000', 'Content-Length': 129600}
Request time cost 2.417473
{"corpus_no":"6779973501543636760","err_msg":"success.","err_no":0,"result":["北京科技馆"],"sn":"584903168781578585593"}
```

图像识别的输入
```
import requests
# If you are using a Jupyter notebook, uncomment the following line.
# %matplotlib inline
import matplotlib.pyplot as plt
import json
from PIL import Image
from io import BytesIO
import os,sys
# Add your Computer Vision subscription key and endpoint to your environment variables.
if 'COMPUTER_VISION_SUBSCRIPTION_KEY' in os.environ:
    subscription_key = os.environ['COMPUTER_VISION_SUBSCRIPTION_KEY']
else:
    print("\nSet the COMPUTER_VISION_SUBSCRIPTION_KEY environment variable.\n**Restart your shell or IDE for changes to take effect.**")
    sys.exit()

if 'COMPUTER_VISION_ENDPOINT' in os.environ:
    endpoint = os.environ['COMPUTER_VISION_ENDPOINT']

analyze_url = endpoint + "vision/v2.0/analyze"

# Set image_url to the URL of an image that you want to analyze.
image_url = "http://01.imgmini.eastday.com/mobile/20170914/" + \
    "20170914080829_d5ea996cb6cdea63d5f8c18400ba1d37_4.jpeg"

headers = {'Ocp-Apim-Subscription-Key': subscription_key}
params = {'visualFeatures': 'Categories,Description,Color'}
data = {'url': image_url}
response = requests.post(analyze_url, headers=headers,
                         params=params, json=data)
response.raise_for_status()

# The 'analysis' object contains various fields that describe the image. The most
# relevant caption for the image is obtained from the 'description' property.
analysis = response.json()
print(json.dumps(response.json()))
image_caption = analysis["description"]["captions"][0]["text"].capitalize()

# Display the image and overlay it with the caption.
image = Image.open(BytesIO(requests.get(image_url).content))
plt.imshow(image)
plt.axis("off")
_ = plt.title(image_caption, size="x-large", y=-0.1)
plt.show()
```

图像识别的输出
```
{"categories": [{"name": "people_group", "score": 0.4921875, "detail": {"celebrities": [{"name": "Kobe Bryant", "confidence": 0.997158408164978, "faceRectangle": {"left": 342, "top": 101, "width": 128, "height": 128}}]}}], "color": {"dominantColorForeground": "Brown", "dominantColorBackground": "White", "dominantColors": ["Yellow", "Brown", "White"], "accentColor": "C38108", "isBwImg": false, "isBWImg": false}, "description": {"tags": ["person", "man", "holding", "standing", "player", "posing", "hand", "wearing", "baseball", "people", "group", "woman", "old", "yellow", "young", "table", "ball", "kitchen", "dog", "white", "sign"], "captions": [{"text": "Kobe Bryant et al. posing for the camera", "confidence": 0.7172954442408799}]}, "requestId": "bc176499-48cf-411e-a9b3-3d1249439597", "metadata": {"width": 1080, "height": 1083, "format": "Jpeg"}}
```





















     
