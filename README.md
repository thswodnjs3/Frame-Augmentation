# Frame Augmentation <br>
This is Augmentation Technique, which can be applied to Video Data for Deep Learning <br><br><br>


## 1. Definition <br>
Frame Augmentation use Augmented Frame(Fake Frame) to augment Original Video Data <br>
Frame Augmentation is easy, intuitive way to augment various, substantial amounts of Video Data <br><br><br>


## 2. Example <br>
### Ⅰ. Original Video <br>
<img src="https://user-images.githubusercontent.com/93433004/206331543-3b89febd-f0bf-43f3-98dd-8ac0aef59fff.gif"/><br>
### Ⅱ. Augmented Video (Frame Augmentation) <br>
<img src="https://user-images.githubusercontent.com/93433004/206331829-169a3ddc-650a-4677-96ea-42566ee018f9.gif"/><br><br><br>


## 3. Methods <br>

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
★★★Insert Method Frames ( PNGs )★★★ <br>
★★★Insert Method ( GIF )★★★ <br>
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
★★★Replace Fixed Method Frames ( PNGs )★★★ <br>
★★★Replace Fixed Method ( GIF )★★★ <br>
##### ⅱ) Random <br>
Replace Random is that replacing frame by random. <br>
★★★Replace Random Method Frames ( PNGs )★★★ <br>
★★★Replace Random Method ( GIF )★★★ <br><br>

### Ⅲ. Amounts of Augmented Frame <br>
You can adjust the amount of Augmented Frame used. <br><br><br>


## 4. Install <br>
★★★How to install ( Search needed )★★★ <br><br><br>


## 5. How to use <br>
★★★Need to consider how to explain to use ( Search needed)★★★ <br><br><br>


## 6. Parameters <br>
★★★Explain Parameters using tables ( Search needed )★★★ <br><br><br>


## 7. Tasks <br>
★★★List of Datasets where Frame Augmentation can be used.<br>
Tasks and Datasets) Video Summarization, Action Recognition, Event Classification, Video Detection, Video Retrieval ... <br><br><br>


## 8. Etc <br>
★★★Need to explain my situations and etc ... ★★★ <br><br><br>


## 9. Reference <br>
Lists All papers referenced.
