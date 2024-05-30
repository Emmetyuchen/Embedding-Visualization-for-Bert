# Embedding Visualization for Bert
Inspired by and built on works that try to explain AI's hidden states, especially the work on the visualization of the embeddings in bert-base-chinese [1], this work aims to see what Bert has and has not learned via visualizing the embeddings for polysemous Chinese words in sentences.

### Methodology

First, the polysemous word "蘋" is used with the meanings of "fruit" and "electronic device." The example sentences for the two meaning are:
"今天買了蘋果來吃" (Today, (I) bought an apple to eat.),"今天買了蘋果手機" (Today, (I) bought an Apple smartphone.). Also significant are sentences with the target word with ambiguous meanings (e.g. "蘋果太貴買不起" (Apples are too expensive to buy.), "買蘋果送我好嗎" (Purchase the Apple(s)/apple(s) and give me for free.)) and sentences with clever manipulation of classifiers that results in the differnet meanings of "蘋" (e.g. "買個蘋果送我好嗎" (Purchase an apple and give me for free.), "買顆蘋果送我好嗎" (Purchase an apple and give me for free.),"買隻蘋果送我好嗎" (Purchase an Apple and give me for free.)). In addition, a semantically senseless sentence (i.e. "早上我去健身房跑蘋果" (*In the morning, I went to the gym to run apple.)) is added to see how Bert processes it.

Second, I carry out analysis of the polysemous word "吃" which comes in shades of meaning, three of them identified by [2] and used below: basic meaning (to swallow food through the mouth or to eat, e.g."他不喜歡吃蘋果" (He doesn't like to eat apples.), "他不喜歡吃魚翅" (He doesn't like to eat shark's fins.)), closely-related meaning (to eat without swallowing or to eat at a certain location, e.g. "他不喜歡吃檳榔" (He doesn't like to chew areca nuts.), "他不喜歡吃摩斯" (He doesn't like to eat at Mos Burger (a burger chain).), and distantly-related meaning (to suffer e.g. "他不喜歡吃官司" (He doesn't like to get sued.), "他不喜歡吃悶虧" (He doesn't like to be compelled to suffer in silence.)). As above, a meanless sentence (i.e. "他不喜歡吃原則" (*He doesn't like to eat principles.)) is included in this part of analysis.

Euclidean distance and cosine similarity are calculated for "蘋" and "吃" among their respective sentences and are visualized through the use of heat maps. The code is shown below, which is adapted and expanded from [1].

### Results

#### 1. "蘋"

As shown from the figures below, Bert can generally distinguish the two senses of "蘋" as the sentences with the meaning of "fruit" are shown with similar colors, and the sentences with the meaning of "electronic device" are closer together. As for the ambiguous sentences, Bert assigns the meaning of something similar to "electronic device" to "蘋" in "蘋果太貴買不起" (Apples are too expensive to buy.), while the meaning of ""蘋"" in "買蘋果送我好嗎" (Purchase the Apple(s)/apple(s) and give me for free.) is interpreted as "fruit." Of interesting note is the sentences differing only in the use of classifiers. The "蘋" in them is considered very close together by Bert, all closer to the meaning of "fruit", even though humans have no problem telling them apart. This indicates that Bert hasn't learned the significance of classifiers, which can change the meaning of the nouns drastically. For the meaningless sentence, Bert appears to classify "蘋" as "electronic device." It may be that the context of sentence makes the word seem like a kind of device.

#### 2. "吃"

The results suggest that Bert clearly is able to tell the differences in the three meanings of "吃", correctly showing that the basic meaning is in proximity to the closely-related meaning. The gradient is obvious as the meaning moves farther and farther away from eating and swallowing something to simply chewing or eating at a place.  The three sentences with the distantly-related meaning are shown to be the farthest away from the basic meaning. Overall, Bert captures the nuances in meanings for "吃", in accord with the distinction made in [2]. In terms of the semantically awkward sentence, "吃" is viewed as distantly-related meaning, which makes sense as the word is not used as its typical sense, and not even close to the closely-related meaning.

### Conclusion

Many attempts have been made to make sense of the inner workings of artificial intelligence. This analysis provides one such method, particularly for visualization of the hidden states in Bert for Mandarin. It can be seen that Bert is capable of grasping the subtleties of meaning, as in the case of "吃". On the other hand, the role of classifiers in Chinese is not yet fully learned, which is something Bert can be improved upon. Future study may focus on other words or syntax, offering a few fascinating glimpses of how AI "thinks."

### References

[1] https://colab.research.google.com/drive/1w7p96mLz8uPQSCCXYPm1HxDVtLPHPZcS?usp=sharing

[2] Hsiao, H. S., Chen, Y. C., & Wu, Y. C. (2016). Representation of Polysemy in Mandarin Verbs: Chī, Dǎ, and Xǐ. Concentric: Studies in Linguistics, 42(1), 1-30. https://doi.org/10.6241/concentric.ling.42.1.01
