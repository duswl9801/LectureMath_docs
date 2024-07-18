# Heading IDs
It exports frames from original videos for Video annotation. The FPS of the original video is 30 and we export `FRAME_EXPORT_FPS` frames per second given in the [config] to ensure the annotator work correctly.

       Command: 
       > python pre_ST3D_v2.0_00_export_frames.py [config] [mode] [parameters]  

       Examples:
       For all lectures in AccessMath(including the ones not currently in used):
       > python pre_ST3D_v2.0_00_export_frames.py configs\01_export_frames.conf

       For all lectures from more than one dataset with one command:
       > python pre_ST3D_v2.0_00_export_frames.py configs\01_export_frames.conf -d "training testing"

       For one specific lecture:
       > python pre_ST3D_v2.0_00_export_frames.py configs\01_export_frames.conf -l lecture_01

       Similarly, for a set of lectures: 
       > python pre_ST3D_v2.0_00_export_frames.py configs\01_export_frames.conf -l "lecture_01 lecture_02 lecture_06"
       

# Video Annotation
This annotator is used to label the intervels of speaker action and export the annotations. For each interval, the lable contains the beginning and ending frame number of the interval, and the action of the speaker during the interval. The annotation data for this paper is in *data\output\annotations*. 

We adapt the annotator from the paper of *K. Davila, R. Zanibbi "Whiteboard video summarization via spatio-temporal conflict minimization", ICDAR 2017*. ([davila2017whiteboard](https://www.cs.rit.edu/~rlaz/files/Kenny_ICDAR_2017.pdf)). For our paper we add more features to complete the speaker action annotation.

       Command:
       > python gt_annotator.py [config] [lecture_name]

       Examples:
       For one specific lecture:
       > python gt_annotator.py configs\02_labeling.conf lecture_01

# Evaluation
    Command:
    python eval_multiple_summaries.py configs\03_main.conf -d testing -b speaker_actions
   
The baseline parameter allows to evaluate variations of the system. During the generation of the summaries
the system uses the parameter "SPEAKER_SUMMARY_PREFIX" to add a baseline prefix to the generated summaries.
Here, we use the baseline parameter "-b speaker_actions" to allow the evaluation script find the right set of 
summaries to compute the corresponding evaluation metrics. 

Summaries from the ICDAR 2019 paper:

    python eval_multiple_summaries.py configs\03_main.conf -d testing -b speaker_actions_RAW
    python eval_multiple_summaries.py configs\03_main.conf -d testing -b speaker_actions_SPK_REMOVAL
    python eval_multiple_summaries.py configs\03_main.conf -d testing -b speaker_actions_BG_REMOVAL
    python eval_multiple_summaries.py configs\03_main.conf -d testing -b speaker_actions_SPK_BG_REMOVAL
    
# Citation
Please cite the following paper in your publication if it helps your research :)

    @inproceedings{xu2019content,
    title={Content extraction from lecture video via speaker action classification based on pose information},
    author={Xu, Fei and Davila, Kenny and Setlur, Srirangaraj and Govindaraju, Venu},
    booktitle={2019 International Conference on Document Analysis and Recognition (ICDAR)},
    pages={1047--1054},
    year={2019},
    organization={IEEE}
    }

    

[Heading IDs](#heading-ids)