# Facial Beauty Research (2019 - 2020)
[TOC]
## 1. Facial Beauty Prediction
### 1.1. Toward graph-based semi-supervised face beauty prediction
Fadi Dornaika, Kunwei Wang, Ignacio Arganda-Carreras, Anne Elorza, Abdelmalik Moujahid,
Expert Systems with Applications,Volume 142, 2020

https://doi.org/10.1016/j.eswa.2019.112990.


**Abstract**: Assessing beauty using facial images analysis is an emerging computer vision problem. To the best of our knowledge, all existing methods for automatic facial beauty scoring rely on fully supervised schemes. In this paper, we introduce the use of semi-supervised learning schemes for solving the problem of face beauty scoring when the image descriptor is holistic and the score is given by a real number. The paper has two main contributions. Firstly, we introduce the use of graph-based semi-supervised learning for face beauty scoring. The proposed method is based on texture and utilizes continuous scores in a full range. Secondly, we adapt and kernelize an existing linear Flexible Manifold Embedding scheme (that works with discrete classes) to the case of real scores propagation. The resulting model can be used for transductive and inductive settings. The proposed semi-supervised schemes were evaluated on three recent public datasets for face beauty analysis: SCUT-FBP, M2B, and SCUT-FBP5500. The obtained experimental results, as well as many comparisons with fully supervised methods, demonstrate that the nonlinear semi-supervised scheme compares favorably with many supervised schemes. The proposed semi-supervised scoring framework paves the way to virtually all applications to adopt continuous scores instead of the usual discrete labels.

### 1.2 Female Facial Beauty Analysis Using Transfer Learning and Stacking Ensemble Model
International Conference on Image Analysis and Recognition 
ICIAR 2019: Image Analysis and Recognition pp 255-268

https://link.springer.com/chapter/10.1007/978-3-030-27272-2_22


**Abstract** 
Automatic analysis of facial beauty has become an emerging research topic in recent years and has fascinated many researchers. One of the key challenges of facial attractiveness prediction is to obtain accurate and discriminative face representation. This study provides a new framework to analyze the attractiveness of female faces using transfer learning methodology as well as stacking ensemble model. Specifically, a pre-trained Convolutional Neural Network (CNN) originally trained on relatively similar datasets for face recognition task, namely Ms-Celeb-1M and VGGFace2, is utilized to acquire high-level and robust features of female face images. This is followed by leveraging a stacking ensemble model which combines the predictions of several base models to predict the attractiveness of a face. Extensive experiments conducted on SCUT-FBP and SCUT-FBP 5500 benchmark datasets, confirm the strong robustness of the proposed approach. Interestingly, prediction correlations of 0.89 and 0.91 are achieved by our new method for SCUT-FBP and SCUT-FBP5500 datasets, respectively. This would indicate significant advantages over the other state-of-the-art work. Moreover, our successful results would certainly support the efficacy of transfer learning when applying deep learning techniques to compute facial attractiveness.

**Keywords**
Facial beauty analysis Stacking ensemble model VGGFace2 

### 1.3 Analyzing Beauty by Building Custom Profiles Using Machine Learning

T. Abrahams and D. Bein, "Analyzing Beauty by Building Custom Profiles Using Machine Learning," 2019 IEEE 9th Annual Computing and Communication Workshop and Conference (CCWC), Las Vegas, NV, USA, 2019, pp. 0372-0376.

URL: http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8666528&isnumber=8666184

doi: 10.1109/CCWC.2019.8666528

**Abstract**: 
Instead of tackling what is universal beauty, we propose to attempt to create profiles based on training data for individual understanding of beauty, while maintaining efficiency. This paper describes a fully functional software system called TBeauty that creates an individual machine-learning algorithm based off a profile to allow users to get an accurate assessment of what they would classify and score beauty. The system would take data and use facial landmarks in order to assess this. The system can be changed to allow automatic search of new images to proactively select the ones that have high scores for any individual user. The project uses an existing 68-point landmark detection algorithm proposed by Rainer Lienhart to identify the facial landmark points (a so-called facial mask) from images that will be fed into various machine-learning algorithms. The software is available on GitHub.

### 1.4 Improving Facial Attractiveness Prediction via Co-attention Learning
S. Shi, F. Gao, X. Meng, X. Xu and J. Zhu, "Improving Facial Attractiveness Prediction via Co-attention Learning," ICASSP 2019 - 2019 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), Brighton, United Kingdom, 2019, pp. 4045-4049.

[doi: 10.1109/ICASSP.2019.8683112]

URL: http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8683112&isnumber=8682151

**Abstract**
Facial attractiveness prediction has drawn considerable attention from image processing community. Despite the substantial progress achieved by existing works, various challenges remain. One is the lack of accurate representation for facial composition, which is essential for attractiveness evaluation. In this paper, we propose to use pixel-wise labelling masks as the meta information of facial composition, and input them into a network for learning high-level semantic representations. The other challenge is to define to what degree different local properties contribute to facial attractiveness. To tackle this challenge, we employ a co-attention learning mechanism to concurrently characterize the significance of different regions and that of distinct facial components. We conduct experiments on the SCUT-FBP5500 and CelebA datasets. Results show that our co-attention learning mechanism significantly improves the facial attractiveness prediction accuracy. Besides, our method consistently produces appealing results and outperforms previous advanced approaches.

### 1.5 Data-Driven Facial Attractiveness of Chinese Male With Epoch Characteristics 

J. Zhao, M. Cao, X. Xie, M. Zhang and L. Wang, "Data-Driven Facial Attractiveness of Chinese Male With Epoch Characteristics," in IEEE Access, vol. 7, pp. 10956-10966, 2019.

doi: 10.1109/ACCESS.2019.2892137

URL: http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8610067&isnumber=8600701

**Abstract**
With the change of epoch, the standard of male attractiveness is also changing. Analyzing the trend of facial features changes over time in different environments can reveal the influence of social development on facial attractiveness. In this paper, we propose a method to analyze the trend of facial features of Chinese male. First, a face database with Chinese male of different times is established and rated by raters of different ages. Second, the machine learning method is used to rate face images of different times for verifying the change of male aesthetic. Then, the retrained Inception v3 model is used to realize facial shape classification. After that, the change trend of face shape is analyzed by using massive data. Finally, the change characteristics of the eyebrow are analyzed by calculating the geometric parameters of the eyebrow model, including the area, length, and average width of the eyebrow. Compared with other researches on facial attractiveness, the proposed method can deeply understand the guiding trend of popular culture on facial attractiveness in different times.




## 2. Facial Beauty Rules 
### 2.1 Perspective Morphometric Criteria for Facial Beauty and Proportion Assessment
Appl. Sci. 2020, 10(1), 8; https://doi.org/10.3390/app10010008 

https://www.mdpi.com/2076-3417/10/1/8/htm

**Abstract**
Common sense usually considers the assessment of female human attractiveness to be subjective. Nevertheless, in the past decades, several studies and experiments showed that an objective component in beauty assessment exists and can be strictly related, even if it does not match, with proportions of features. Proportions can be studied through analysis of the face, which relies on landmarks, i.e., specific points on the facial surface, which are shared by everyone, and measurements between them. In this work, several measures have been gathered from studies in the literature considering datasets of beautiful women to build a set of measures that can be defined as suggestive of female attractiveness. The resulting set consists of 29 measures applied to a public dataset, the Bosphorus database, whose faces have been both analyzed by the developed methodology based on the expanded set of measures and judged by human observers. Results show that the set of chosen measures is significant in terms of attractiveness evaluation, confirming the key role of proportions in beauty assessment; furthermore, the sorting of identified measures has been performed to identify the most significant canons involved in the evaluation. 

**Keywords** 
face analysis; face proportions; attractiveness; 3D landmarks; features extraction

### 2.2 Assessment of Ideal Dimensions of the Ears, Nose, and Lip in the Circles of Prominence Theory on Facial Beauty

Philip Young, MD1 
JAMA Facial Plast Surg. 2019;21(3):199-205. doi:10.1001/jamafacial.2018.1797 

https://jamanetwork.com/journals/jamafacialplasticsurgery/article-abstract/2724611

**Abstract** 

**Importance**  A theory on facial beauty might allow clinicians to achieve better results.
Objectives  To find the ideal vertical position of the ears, total lip length, lip pucker length, distance between the irises, and starting point for the nasal radix.

**Design, Setting, and Participants**  In this subjective survey, 11 sets of 43 total digitally adjusted pictures (DAPs) and line drawings of actual faces were ranked based on attractiveness by 419 clients at a facial plastic surgery clinic. The data were collected from July 13 to August 29, 2015, and were analyzed from September 17, 2015, to March 21, 2016.

**Main Outcomes and Measure** Six groups of line drawings and 5 groups of DAPs of an actual person were used to test the ideal position of the ears to determine whether the face is organized into oblique and parallel relationships and whether the total lip length and the lip pucker length are associated with multiples of an iris width (IW), and to determine the start of the nasal radix and its association with the superior margin of the iris and distance between the irises.

**Results**  Of the 419 survey respondents, the ear aligned with the second oblique was considered the most ideal by the participants. The preferred total lip length was 4.0 IWs in the DAPs and 5.0 IWs in the line drawings. For the lip pucker length, 2.0 and 3.0 IWs were considered the best. The ideal start of the nasal radix was tangential with the superior margin of the iris. The distance of 5.5 IWs from iris to iris and 3.0 IWs from the horizontal level of the iris to the nasal tip was preferred.

**Conclusions and Relevance**  The face may be ideally organized into 3 parallel obliques. The IW, horizontal aperture of the eye, and then iris to iris distance may best determine the size and shape of progressively larger objects in the face. The absolute position of the eye was considered important by the participants in the ideal positioning of other objects in the face.
Level of Evidence  NA.

### 2.3 Consensus Opinions on Facial Beauty and Implications for Aesthetic Treatment in Middle Eastern Women
Plastic and Reconstructive Surgery – Global Open: April 2019 - Volume 7 - Issue 4 - p e2220
doi: 10.1097/GOX.0000000000002220

https://journals.lww.com/prsgo/Fulltext/2019/04000/Consensus_Opinions_on_Facial_Beauty_and.2.aspx

**Results**: 
Facial anthropometry differs between Middle Eastern and Western women, and also within the region. Although subregional differences are seen, beauty is generally recognized by an oval or round face; temple fullness; pronounced, elevated, arched eyebrows; large almond-shaped eyes; well-defined, laterally full cheeks; a small, straight nose; full lips; a well-defined jawline; and a prominent, pointed chin. The relative prominence of the nose necessitates attention to the lips and the shape and projection of the chin. Aging is often accompanied by midface sagging that leads to increased heaviness in the lower facial third. 

**Conclusions**: 
Middle Eastern beauty is characterized by striking eyes, defined cheeks, and full lips. These consensus opinions inform aesthetic practitioners who treat Middle Eastern women worldwide about their aesthetic ideals and the implications for treatment. 


### 2.4 Subjectivity and complexity of facial attractiveness
https://www.nature.com/articles/s41598-019-44655-9.pdf

Miguel Ibáñez-Berganza, Ambra Amico & Vittorio Loreto,  
Scientific Reports volume 9, Article number: 8364 (2019) 

**Abstract**
The origin and meaning of facial beauty represent a longstanding puzzle. Despite the profuse literature devoted to facial attractiveness, its very nature, its determinants and the nature of inter-person differences remain controversial issues. Here we tackle such questions proposing a novel experimental approach in which human subjects, instead of rating natural faces, are allowed to efficiently explore the face-space and “sculpt” their favorite variation of a reference facial image. The results reveal that different subjects prefer distinguishable regions of the face-space, highlighting the essential subjectivity of the phenomenon. The different sculpted facial vectors exhibit strong correlations among pairs of facial distances, characterising the underlying universality and complexity of the cognitive processes, and the relative relevance and robustness of the different facial distances.

### 2.5 The Ideals of Facial Beauty Among Chinese Aesthetic Practitioners: Results from a Large National Survey
https://link.springer.com/content/pdf/10.1007/s00266-018-1241-8.pdf

Souphiyeh Samizadeh, Aesthetic Plastic Surgery volume 43, 
pages 102–114(2019)

**Abstract**
As the demand for cosmetic procedures increases, the importance of patient-centred care in this field becomes more prominent. The aesthetic practitioners’ ideals of beauty, in addition to their knowledge and perception of patients’ ideals of beauty and expectations, are important during doctor–patient communication. These are important in strengthening practices of patient-centred communication and treatment. This study was conducted to investigate ideals of facial beauty among Chinese aesthetic practitioners. A questionnaire with simple sketches of facial features was given to aesthetic practitioners in Chinese cosmetology hospitals and clinics to assess aesthetic practitioners’ ideals of beauty and their preferences for facial shapes, facial profile, nose and lip shape, jaw angle, and chin shape. A total of 596 surveys were completed. This survey revealed that Chinese aesthetic practitioners preferred a heart/inverted triangular facial shape with a reduced lower face height, a straight and small nose, as well as lips that are full medially and taper off laterally with well-defined borders and Cupid’s bow. An obtuse jaw angle for women and a square well-defined jaw angle for men, and a round and pointy chin for both women and men were the most preferred. A majority (66.7%) of the respondents said they would have plastic surgery. However, if given the choice 82.9% indicated they would opt for non-surgical procedures. Finally, a clear majority (90.5%) believed that being beautiful would improve their daily life. The results were then compared to a similar previous study in which the same ideals of beauty were investigated among Chinese laypersons. This information will help the aesthetic professionals to understand their patient’s requests and expectations better and therefore aid in offering and providing treatments that are in line.

### 2.6 Female eye attractiveness – Where beauty meets science

https://doi.org/10.1016/j.jcms.2018.05.034

**Abstract**
Introduction
While periorbital and -ocular surgery ranks amongst the most frequently performed plastic surgical procedures, only scarce information exists regarding the contributing factors of aging and its systematic anatomic assessment. The presented study, based on measuring distinct physical landmarks, aimed to gather data to provide a foundation of in-depth periorbital analysis in order to more clearly define female eye attractiveness.

**Methods**
80 probands (age range: 30–50 years, M = 38.4 ± 6.5 years) were asked to judge 60 standardized high-resolution digital pictures of female eye regions in respect to the perceived age (in years) and attractiveness (7-point Likert scale). All photographs were objectively evaluated and measured utilizing a total of 38 distinct landmarks. The data was analyzed by calculating correlations between relevant measured eye area parameters and mean attractiveness ratings including age estimations.

**Results**
Overall, it was found that several specific eye shape features correlate with attractiveness and perceived age. For instance, large visible height of the iris and large upward and lateral inclination of both eye axis and eyebrows correlated moderately to strongly with attractiveness (p < 0.05).

**Conclusion**
Regarding the female eye, there exist distinct periorbital anatomic features and landmarks which contribute to a youthful appearance and attractiveness. Knowledge regarding these facts may serve as an important guideline for pre- and post-operative patient analysis.


# 3. Facial Beauty Analysis by Generation
## 3.1 Beholder GAN: Generation and Beautification of Facial Images with Conditioning on Their Beauty Level
https://arxiv.org/pdf/1902.02593.pdf


Nir Diamant, Dean Zadok, Chaim Baskin, Eli Schwartz, Alex M. Bronstein
(Submitted on 7 Feb 2019 (v1), last revised 25 Feb 2019 (this version, v3))

**Abstract**
Beauty is in the eye of the beholder. This maxim, emphasizing the subjectivity of the perception of beauty, has enjoyed a wide consensus since ancient times. In the digitalera, data-driven methods have been shown to be able to predict human-assigned beauty scores for facial images. In this work, we augment this ability and train a generative model that generates faces conditioned on a requested beauty score. In addition, we show how this trained generator can be used to beautify an input face image. By doing so, we achieve an unsupervised beautification model, in the sense that it relies on no ground truth target images. 

Cite as:
arXiv:1902.02593 [cs.CV]

Code :  https://github.com/beholdergan/Beholder-GAN. 

## 3.2 Beauty Learning and Counterfactual Inference
http://openaccess.thecvf.com/content_CVPRW_2019/papers/Explainable%20AI/Li_Beauty_Learning_and_Counterfactual_Inference_CVPRW_2019_paper.pdf

Tao Li; The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops, 2019, pp. 111-113 

**Abstract**
This work showcases a new approach for causal discovery by leveraging user experiments and recent advances in
photo-realistic image editing, demonstrating a potential of identifying causal factors and understanding complex systems counterfactually. We introduce the beauty learning
problem as an example, which has been discussed metaphysically for centuries and recently been proved exists, is quantifiable, and can be learned by deep models in our paper [1], where we utilize a natural image generator coupled with user studies to infer causal effects from facial semantics to beauty outcomes, the results of which also align with existing empirical studies. We expect the proposed framework for a broader application in causal inference. 

### 3.3 Understanding Beauty via Deep Facial Features
http://openaccess.thecvf.com/content_CVPRW_2019/papers/AMFG/Liu_Understanding_Beauty_via_Deep_Facial_Features_CVPRW_2019_paper.pdf

Xudong Liu, Tao Li, Hao Peng, Iris Chuoying Ouyang, Taehwan Kim, Ruizhe Wang; The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops, 2019, pp. 0-0 

**Abstract** 
The concept of beauty has been debated by philosophers and psychologists for centuries, but most definitions are subjective and metaphysical, and deficit in accuracy, generality, and scalability. In this paper, we present a novel study on mining beauty semantics of facial attributes based on big data, with an attempt to objectively construct descriptions of beauty in a quantitative manner. We first deploy a deep Convolutional Neural Network (CNN) to extract facial attributes, and then investigate correlations between these features and attractiveness on two large-scale datasets labelled with beauty scores. Not only do we discover the secrets of beauty verified by statistical significance tests, our findings also align perfectly with existing psychological studies that, e.g., small nose, high cheekbones, and femininity contribute to attractiveness. We further leverage these high-level representations to original images by a generative adversarial network (GAN). Beauty enhancements after synthesis are visually compelling and statistically convincing verified by a user survey of 10,000 data points.


### 3.4 Face Beautification: Beyond Makeup Transfer
https://arxiv.org/abs/1912.03630

Xudong Liu, Ruizhe Wang, Chih-Fan Chen, Minglei Yin, Hao Peng, Shukhan Ng, Xin Li
(Submitted on 8 Dec 2019 (v1), last revised 11 Dec 2019 (this version, v2))

**Abstract**
Facial appearance plays an important role in our social lives. Subjective perception of women's beauty depends on various face-related (e.g., skin, shape, hair) and environmental (e.g., makeup, lighting, angle) factors. Similar to cosmetic surgery in the physical world, virtual face beautification is an emerging field with many open issues to be addressed. Inspired by the latest advances in style-based synthesis and face beauty prediction, we propose a novel framework of face beautification. For a given reference face with a high beauty score, our GAN-based architecture is capable of translating an inquiry face into a sequence of beautified face images with referenced beauty style and targeted beauty score values. To achieve this objective, we propose to integrate both style-based beauty representation (extracted from the reference face) and beauty score prediction (trained on SCUT-FBP database) into the process of beautification. Unlike makeup transfer, our approach targets at many-to-many (instead of one-to-one) translation where multiple outputs can be defined by either different references or varying beauty scores. Extensive experimental results are reported to demonstrate the effectiveness and flexibility of the proposed face beautification framework. 

Cite as:
arXiv:1912.03630 [cs.CV]
 

## 4. EEG and Facial Beauty Perception
### 4.1 A robust implicit measure of facial attractiveness discrimination 

https://academic.oup.com/scan/article/14/7/737/5520404

Qiuling Luo, Bruno Rossion, and Milena Dzhelyova, 
Social Cognitive and Affective Neuroscience, 2019, 737–746

**Abstract**
Decisions of attractiveness from the human face are made instantly and spontaneously, but robust implicit neural measures of facial attractiveness discrimination are currently lacking. Here we applied fast periodic visual stimulation coupled with electroencephalography (EEG) to objectively measure the neural coding of facial attractiveness. We presented different pictures of faces at 6 Hz, i.e. six faces/second, for a minute while participants attended to a central fixation cross and indicated whether the cross shortly changed color. Every other face in the stimulation was attractive and was replaced by a relatively less attractive face. This resulted in alternating more/less attractive faces at a 3 Hz rate, eliciting a significant increase in occipito-temporal EEG amplitude at 3 Hz both at the group and the individual participant level. This response was absent in two control conditions where either only attractive or only less attractive faces were presented. These observations support the view that face-sensitive visual areas discriminate attractiveness implicitly and rapidly from the human face.





