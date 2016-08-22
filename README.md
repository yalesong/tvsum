# TVSum Dataset
Title-based Video Summarization (TVSum) dataset used in our CVPR 2015 paper **"Tvsum: Summarizing web videos using titles."**

![alt text](https://github.com/yalesong/tvsum50/blob/master/images/tvsum50.png "TVSum50 Dataset")

## Overview
Yahoo! Title-based Video Summarization dataset (TVSum50) serves as a benchmark to validate video summarization techniques. It contains 50 videos of various genres (e.g., news, how-to, documentary, vlog, egocentric) and 1,000 annotations of shot-level importance scores obtained via crowdsourcing (20 per video). The video and annotation data permits an automatic evaluation of various video summarization techniques, without having to conduct (expensive) user study.

The videos, collected from YouTube, comes with the [Creative Commons CC-BY (v3.0) license](https://support.google.com/youtube/answer/2797468?hl=en). We release both the video files and their URLs. The shot-level importance scores are annotated via Amazon Mechanical Turk -- each video was annotated by 20 crowd-workers. The dataset has been reviewed to conform to Yahoo's data protection standards, including strict controls on privacy.

## Tasks
The primary task of the dataset is video summarization, where the goal is to create a short, meaningful summary of a given video. The summary may contain a few shots that capture the highlights of a video and are non-redundant. Although the task is inherently subjective, we carefully curated the dataset and annotated it so that the evaluation is done in an objective way. (We have a reasonably high degree of inter-rater reliability, with the Cronbach’s alpha of 0.81.)

While the main task is video summarization, our dataset can be used to evaluate other related problems, such as:
* Automatically generate a thumbnail image from video
* Video2GIF: Automatically generate animated GIFs from video
* Video highlight detection

## Evaluations
Let’s say we’ve generated a 15 second-long summary of video “[Will a cat eat dog food?](https://www.youtube.com/watch?v=-esJrBWj2d8)”, shown below:

![alt text](https://github.com/yalesong/tvsum50/blob/master/images/cat_gif_summary.gif "Cat GIF summary")

How do we know the quality of the generated summary? We can use the shot-level importance scores included in the dataset. 

Each video is annotated as follows: We chopped up a video into a set of 2 second-long shots and asked 20 users to rate how important each shot is, compared to other shots from the same video, on a scale from 1 (not important) to 5 (very important). The average of responses become the shot-level importance scores of the video, e.g.,

![alt text](https://github.com/yalesong/tvsum50/blob/master/images/score.png "Shot importance score")

From the shot-level importance scores, we can formulate video summarization as the 0/1 Knapsack Problem: given a time budget (e.g., 15 seconds), maximize the total importance score of the shots included in a summary. The solution will be a vector of size T (the number of frames in a video), whose values are either 0 (not in summary) or 1 (include in summary) -- let’s call this solution the gold standard.

If our summary is similar to the gold standard, it means our summary is similar to how the 20 annotators would’ve summarized the video. We can represent our summary as a vector of size T, whose elements are 1 if it is in the summary. We are now ready to compare how good the produced summary is by comparing the two vectors of same size, using various metrics (e.g., F1 score).

## How to get the data
The dataset is available as part of the [Yahoo! WebScope program](https://webscope.sandbox.yahoo.com/#datasets). Follow the steps below to download the dataset:

1. Visit: [I4 - Title-based Video Summarization dataset](https://webscope.sandbox.yahoo.com/catalog.php?datatype=i&did=72), version 1.1 (644M)
2. Sign in to your Yahoo account.
3. Click “Select this Dataset” - “View Cart”.
4. Fill out “Research Purpose” section.
5. Click “Continue”.

_Note for the participants of the [2016 LDV Vision Summit - Entrepreneurial Computer Vision Challenges (ECVC)](http://www.ldv.co/visionsummit/2016/competitions): We’ve arranged a special approval process for the ECVC participants so you do not need an academic email address to get an approval to download. Please mention in the form (“Research Purpose” section) that you are a participant of the challenge._


## Reference
Song, Yale, Jordi Vallmitjana, Amanda Stent, and Alejandro Jaimes. **"Tvsum: Summarizing web videos using titles."** In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 5179-5187. 2015.


