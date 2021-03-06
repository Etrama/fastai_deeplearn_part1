# Lesson 11_2:  Neural Translation

(09-Apr-2018, live)  

- [Wiki Lesson 11](http://forums.fast.ai/t/part-2-lesson-11-wiki/14699)
- [Video Lesson 11](https://www.youtube.com/watch?v=tY0n9OT5_nA&feature=youtu.be) 
  - video length:  2:15:57
- http://course.fast.ai/lessons/lesson11.html
- Notebook:  
   * [translate.ipynb](https://github.com/fastai/fastai/blob/master/courses/dl2/translate.ipynb)
   
## `01:13:10` After Break
- So one question that came up during the break is that some of the tokens that are missing in fast text like had a curly quote rather than a straight quote, for example.  And the question was, would it help to normalize punctuation?  And, the answer for this particular case is, probably yes, the difference between curly quotes and straight quotes is really semantic.  You do have to be very careful, though, because like it may turn out that people using beautiful curly quotes are like using more formal language and they're actually writing in a different way so I generally... you know, if you're going to do some kind of pre-processing like punctuation normalization, you should definitely check your results with and without because like *nearly always* that kind of pre-processing makes things worse even when I'm sure it won't.

### `01:14:10`  Question
- Person x (Yannet?):  Hello, what might be some ways of realizing? these sequence to sequence models besides dropout and weight decay?
- JH:  Let me think about that during the week. Yeah, it's like you know, AWD LSTM, which we've been relying on a lot, has so many great.. I mean it's all dropout, well not all dropout,  there's dropout of many different kinds. And then there's the... we haven't talked about it very much, but there's also a kind of regularization based on activations and stuff like that as well.  And on changes, and whatever.  I just haven't seen anybody put anything like that amount of work into regularization of sequence to sequence models and I think there's a huge opportunity for somebody to do like the AWD LSTM of seq to seq, which might be as simple as dealing with all the ideas from AWD LSTM and using them directly in seq to seq.  That would be pretty easy to try, I think.  And there's been an interesting paper that actually Steven Merity's added in the last couple of weeks where he used an idea which I don't know if he stole it from me but it was certainly something I had also recently done and talked about on Twitter.  Either way, I am thrilled that he's done it which was to take all of those different AWD LSTM hyperparameters and train a bunch of different models and then use a random forest to find out with feature importance, which ones actually matter the most, and then figure out how to set them. Yes, so I think you could totally, you know, use this approach, to figure out, you know, for sequence to sequence regularization approaches, which one is the best and optimize them.  And that would be amazing. Yeah, but at the moment, I think, you know, I don't know that there are additional ideas to sequence to sequence regularization that I can think of beyond what's in that paper for regular language model stuff and probably all those same approaches would work.

### `01:16:30`
- All right, so tricks.  Trick #1, go bi-directional.  So, for classification, my approach to bi-directional that I suggested you use is take all of your token sequences, spin them around and train a new language model and train a new classifier. And I also mentioned the wiki text pre-trained model if you replace FWD with VWD in the name, you'll get the 
