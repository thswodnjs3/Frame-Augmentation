# Frame Augmentation <br>
This is Augmentation Technique, which can be applied to Video Summarization.<br><br><br>


## 1. Background <br>
### Ⅰ. Video Summarization <br>
Video Summarization is a task that makes a model which takes long video as input and then export short video as output.<br>
Exported short video is a summarized version of input long video.<br>
Summarized video should contain most import frames from original video.<br>
### Ⅱ. Importance Score <br>
The way model tell which frame is important in original video is based on Importance Score.<br>
Importance Score is a value between 0 and 1, which is assigned to all frames.<br>
Actually, Video Summarization Model takes array of frames and exports array of importance scores, which is assigned to each frame.<br>
As you know, we have to assign importance score to all frames beforehand, and it takse too much time. (2 min lenght of video = at least 3,600 frames).<br>
Also, importance score has a subjective problem, which means people assign different importance score on the same frame.<br>
To get objective, manay people should assign importance score but it costs lot.<br>
Therefore, there is less dataset in video summarization field, if we use importance score.<br>
### Ⅲ. Augmented in Video Summarization <br>
If you familiar with Video Summarization Task, there is a way called Augmented in Video Summarization.<br>
But the term Augmented in Video Summarization is the way just using three more datasetes.<br>
There are only two choices, whether we use Augmented setting or not.<br>
Compared to Augmentation Technique used in Image-related task, it is so constrained way.<br>
In Image-related task, we can use rotate,tilt,flip,shift,etc. So we can test under various settings and it is very easy to implement.<br>
### Ⅳ. Augmentation technique in other video-related tasks <br>
I've searched Augmentation techniques used in other video-related tasks.<br>
Most of them using image augmentation to whole frames in a video.<br>
There are also ways which using GAN or other Generator and anything else.<br>
But those ways are too difficult to implement.<br>
There also some papers mixing some frames from several videos and then making one frame.<br>
I thought it is interesting bue most of them didn't consider time-axis at all.<br>
Unlike image data, video data shows many frames in a row. It means we have to consider time-axis information when using video data.<br>
And there are few papers deal such that.<br>
So, to implement easily and also augmented data into time-axis, I propose Frame Augmentation.<br><br><br>


## 2. Definition <br>
Frame Augmentation use Augmented Frame(Fake Frame) to augment Original Video Data <br>
Frame Augmentation is easy, intuitive way to augment various, substantial amounts of Video Data. <br>
There are advantages when using Frame Augmentation.<br>
1) It is easy. Just put Augmented Frame in video we're trying to use.<br>
2) We augment video data not only image data, but also time-axis data. And I'm sure there are few people handling like that.<br>
3) We can test several settings by using Frame Augmentation, like image Augmentation. <br><br><br>


## 3. Example <br>
### Ⅰ. Original Video <br>
<img src="https://user-images.githubusercontent.com/93433004/206331543-3b89febd-f0bf-43f3-98dd-8ac0aef59fff.gif"/><br>
### Ⅱ. Augmented Video (Frame Augmentation) <br>
<img src="https://user-images.githubusercontent.com/93433004/206331829-169a3ddc-650a-4677-96ea-42566ee018f9.gif"/><br><br><br>


## 4. Methods <br>
### Ⅰ. Type of Augmented Frame <br>
#### ① Black Frame <br>
Black Frame is a frame which of all values are 0. <br>
<img src="https://user-images.githubusercontent.com/93433004/206332255-266648b0-3f6a-4992-9af5-5e165dc7b0ba.png"/><br>
#### ② Noise Frame <br>
Noise Frame is a frame which of all values assigned by random. <br>
<img src="https://user-images.githubusercontent.com/93433004/206332313-1d2d69f2-4a47-401d-b7e5-a21942617c5e.png"/><br>
#### ③ Video Frame <br>
Video Frame is a frame which from other video, except a video that is going to be used. <br>
<img src="https://user-images.githubusercontent.com/93433004/206332363-19baa379-b2a7-4182-ae2b-f640ac0839a8.png"/><br>
### Ⅱ. How to Use Augmented Frame <br>
#### ① Insert <br>
Insert method is that inserting Augmented Frame into original video. <br>
##### Original Frame Array <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332486-d0c863af-25b8-4c78-b4de-e389f7626496.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332514-146c847d-a3ea-4c44-9167-d04843de6177.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332548-ecc90ae7-0f5f-45e9-bf84-ae3770e59fea.png" />
</p>

##### Insert Augmented Frame Array <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332486-d0c863af-25b8-4c78-b4de-e389f7626496.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332313-1d2d69f2-4a47-401d-b7e5-a21942617c5e.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332514-146c847d-a3ea-4c44-9167-d04843de6177.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332313-1d2d69f2-4a47-401d-b7e5-a21942617c5e.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332548-ecc90ae7-0f5f-45e9-bf84-ae3770e59fea.png" />
</p>

##### Insert Augmented Video <br>
<img src="https://user-images.githubusercontent.com/93433004/206331829-169a3ddc-650a-4677-96ea-42566ee018f9.gif"/> <br>
#### ② Replace <br>
Replace method is that replaceing frames in original video with Augmented Frame. <br>
This can be categorized into 2 ways ( fixed, random ). <br>
##### ⅰ) Fixed <br>
Replace Fixed is that replacing frame based on fps. <br>
If fps of video is 3 and you want replace first frame every second, then frame of fixed position in every second will be replaced. <br>
0 second ~ 1 second : First-Frame(replaced)    Second-Frame    Third-Frame <br>
1 second ~ 2 second : First-Frame(replaced)    Second-Frame    Third-Frame <br>
2 second ~ 3 second : First-Frame(replaced)    Second-Frame    Third-Frame <br>
... <br>

###### Original Frame Array <br>
0 second ~ 1 second <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332486-d0c863af-25b8-4c78-b4de-e389f7626496.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332514-146c847d-a3ea-4c44-9167-d04843de6177.png" />
</p> <br>
1 second ~ 2 second <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332548-ecc90ae7-0f5f-45e9-bf84-ae3770e59fea.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206620535-0e0cc963-dfef-4a18-a5ea-c85cec7413e9.png" />
</p> <br>
2 second ~ 3 second <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206620588-b6b8742b-3873-49ca-aa57-4cc1f4e1d8b5.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206620737-ec084f90-be9b-467b-a87c-751f5f2dfd95.png" />
</p> <br>
... <br>

###### Replace fixed Augmented Frame Array <br>
0 second ~ 1 second <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332313-1d2d69f2-4a47-401d-b7e5-a21942617c5e.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332514-146c847d-a3ea-4c44-9167-d04843de6177.png" />
</p> <br>
1 second ~ 2 second <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332313-1d2d69f2-4a47-401d-b7e5-a21942617c5e.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206620535-0e0cc963-dfef-4a18-a5ea-c85cec7413e9.png" />
</p> <br>
2 second ~ 3 second <br>
<p float="left">
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206332313-1d2d69f2-4a47-401d-b7e5-a21942617c5e.png" />
  <img width="160" height="120" src="https://user-images.githubusercontent.com/93433004/206620737-ec084f90-be9b-467b-a87c-751f5f2dfd95.png" />
</p> <br>
... <br>


##### ⅱ) Random <br>
Replace Random is that replacing frame by random. <br>
The only difference is replace frame randomly, comparing to Replace fixed.

### Ⅲ. Amounts of Augmented Frame <br>
You can adjust the amount of Augmented Frame used. <br><br><br>


## 5. Task Extend <br>
Frame Augmentation 


## 6. Experiment <br>
I tested Frame Augmentation on Video Summarization task. <br>
The datasets I used are two most used datasets in Video Summarization, which are [SumMe](https://gyglim.github.io/me/papers/GygliECCV14_vsum.pdf) and [TVSum](https://openaccess.thecvf.com/content_cvpr_2015/papers/Song_TVSum_Summarizing_Web_2015_CVPR_paper.pdf). <br>
The model I used is [CA-SUM](https://dl.acm.org/doi/pdf/10.1145/3512527.3531404). <br>
Even though CA-SUM is good model which shows great performance, we don't know which frame they used to train. So, I arbitarily select default frames to train. And compare each Frame Augmentation setting with default performance. <br>
The result is as below. The best result of each setting was highlighted. Also, I said some of opinion of this result. <br>
### Ⅰ. Insert Frame <br>
|Insert|SumMe|TVSum|
|:---:|:---:|:---:|
|Default|43.45|57.29|
|Black Frame (×2)|43.11|58.25|
|Noise Frame (×2)|44.86|57.91|
|Noise Frame (×3)|45.58|**59.03**|
|Video Frame (×2)|45.28|55.82|
|Video Frame (×3)|**45.68**|58.42| <br><br>
### Ⅱ. Replace Fixed Frame <br>
|Replace Fixed|SumMe|TVSum|
|:---:|:---:|:---:|
|Default|43.45|57.29|
|Black Frame Front(×2)|45.31|57.93|
|Black Frame Back (×2)|41.53|58.99|
|Black Frame Both (×3)|43.62|57.15|
|Noise Frame Front(×2)|45.90|58.23|
|Noise Frame Back (×2)|44.89|58.42|
|Noise Frame Both (×3)|45.21|**59.20**|
|Video Frame Front(×2)|42.56|58.33|
|Video Frame Back (×2)|43.01|58.21|
|Video Frame Both (×3)|**47.04**|58.76| <br><br>
### Ⅲ. Replace Random Frame <br>
|Replace Random|SumMe|TVSum|
|:---:|:---:|:---:|
|Default|43.45|57.29|
|Black Frame (×2)|45.49|58.54|
|Black Frame (×3)|**45.74**|58.83|
|Noise Frame (×2)|44.09|**59.05**|
|Noise Frame (×3)|43.56|58.31|
|Video Frame (×2)|42.99|58.50|
|Video Frame (×3)|44.47|58.07| <br><br>
### Ⅳ. My Own Opinion <br>
As you can see above table, Frame Augmentation helps export better result, comparing to default performance. So, Frame Augmentation can be helpful for video summarization task. <br>
It is possible for you to doubt the improvement is not big enough. But like in image augmentation for image classification task, people don't know which augmentation setting is the best way for improving performance. They just tested several augmentation settings to improve performance, considering their model and dataset they used. So, like that way, Frame Augmentation give you some choices, some of them might help you to improve your model for video-related task. <br>
If you're interested in video summarization task, I'll give some of my opinions which I've came up with during Frame Augmentation experiment in Discussion part below. <br><br><br>


## 7. Discussion <br>
In this part, I'll explain my opinion while I'm performing Frame Augmentation experiment. This is just my personal opinion.<br>
### Ⅰ. Video Summarization model doesn't learn visual representation enough. <br>
I thought video summarization model doesn't learn visual representation enough based on two reasons. <br>
First, the result of pretrained model. I also did Frame Augmentation experiment on pretrained CA-SUM model, and I found out that all of them resulted worse score than pretrained CA-SUM without Frame Augmentation. So, if we use Frame Augmentation on pretrained CA-SUM model, the result got worse. Like I said, I didn't know which frames CA-SUM model use to train. At first, I thought it would get better if we trained CA-SUM model more using Frame Augmentation. But it results worse performance.  I also did the same experiment on PGL-SUM model, which also showed good performance. But it also gets worse when we did the same thing. It means that only some specific frames made video summarization model better, but others did the opposite. Based on these facts, video summarization model is heavily depended on which frames they used to train. <br>
Second, the results of using Frame Augmentation is not consistent. We can't find out any relationship between results and Frame Augmentation setting(method, number of datasets, frame type). I did various experiments with different settings, which means the visual representation varies depending on the Frame Augmentation setting. But they can't handle it. So the problem of video summarization is not related to overfitting of few datasets, it is related the fact that video summarization model can not even learn existing datasets enough at all. There could be several reasons why video summarization model can't learn existing datasets, such as the difference of content, bad image resolution compared to image-related deep learning task, inability of learning temporal meaning in the video, etc. <br>
### Ⅱ. Importance Score problem. <br>
As you know, the importance score prediction is a huge problem. Importance Score is very subjective. ["Rethinking the Evaluation of Video Summaries"](https://arxiv.org/pdf/1903.11328.pdf) insisted that importance score distribution of the same video varies depending on the user. And in SumMe, TVSum dataset, each video's category is different, but most of papers force models to be learnd to find out the relationship in such datasets, which of data is unrelated each other at all. So we have to let model summarize video not based on the importance score. <br>
### Ⅲ. Frame Augmentation can be used other tasks. <br>
Frame Augmentation can be used all video-related task I think. For example, when it comes to Action Recognition, we can augment video data by Frame Augmentation. Good model can guess what action is happening in the video, even though there is a noise between each frames. On the same way, I think Frame Augmentation can be used in Video Summarization, Action Recognition, Event Classification, etc.


## 8. Reference <br>
1. SumMe
[Gygli, Michael, et al. "Creating summaries from user videos." European conference on computer vision. Springer, Cham, 2014.](https://proceedings.neurips.cc/paper/2021/file/7503cfacd12053d309b6bed5c89de212-Paper.pdf)
2. TVSum
[Song, Yale, et al. "Tvsum: Summarizing web videos using titles." Proceedings of the IEEE conference on computer vision and pattern recognition. 2015.](https://openaccess.thecvf.com/content_cvpr_2015/papers/Song_TVSum_Summarizing_Web_2015_CVPR_paper.pdf)
3. CA-SUM
[Apostolidis, Evlampios, et al. "Summarizing Videos using Concentrated Attention and Considering the Uniqueness and Diversity of the Video Frames." Proceedings of the 2022 International Conference on Multimedia Retrieval. 2022.](https://dl.acm.org/doi/pdf/10.1145/3512527.3531404)
4. Rethinking the Video Summarization
[Otani, Mayu, et al. "Rethinking the evaluation of video summaries." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2019.](https://openaccess.thecvf.com/content_CVPR_2019/papers/Otani_Rethinking_the_Evaluation_of_Video_Summaries_CVPR_2019_paper.pdf)
