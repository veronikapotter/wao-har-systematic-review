# Sec. 6.1.2 - Evaluating the Usability of Open-weight WAO HAR Models

We identified three authors who published open-weight WAO HAR models:
1. Lu et al ([GitHub Repo](https://github.com/lulujianjie/robust-single-accelerometer-based-activity-recognition-using-modified-recurrence-plot))
1. Ahmadi et al (Jul. 2020) ([GitHub Repo](https://github.com/QUTcparg/Sensors_CP_PersonalisedModels))
1. Ahmadi et al (Aug. 2020) ([GitHub Repo](https://github.com/QUTcparg/PS_PAClassification))

To verify if these models were usable, we ran the publicly available code. The code provided as supplemental material from Ahmadi et al (Jul. 2020) and Ahmadi et al (Aug. 2020) both ran without issue, however, because these models are trained on data from children, we could not use them for inference on an independent dataset. 

The code in this repository is the modifications we made to Lu et al's codebase to ensure that their preprocessing, encoding, and inference code worked on their original data and then apply it to novel data. 

We modified the following three files from their original repository: 
1. `/Model/preprocessing/Data Segmentation.ipynb` -> `./data_seg.ipynb`
1. `/Model/encoding/RP-forADL.ipynb` -> `./encoding.ipynb`
1. `/ResNet.ipynb` -> `./inference.ipynb`

We made a comment on each line we modified; unless noted, the code was not modified.

## To Replicate our Inference 

Run the specified cells in the notebooks in the following order:
1. `./data_seg.ipynb`
1. `./encoding.ipynb`
1. `./inference.ipynb`

We used Python v3.13.5 and package requirements are listed in `./requirements.txt`.

**NOTE**: The code provided in this repository will not run in its entirety without downloading the model weigths `/Model/ResNet_best.pth` (for the ASTRI model) and `/Model/ResNet-ADL.pth` (for the ADL model) from the original ([GitHub Repo](https://github.com/lulujianjie/robust-single-accelerometer-based-activity-recognition-using-modified-recurrence-plot)).

**NOTE**: The encodings are *large*. As such, we've stored ours [externally for download](anonymized). To run the `./inference.ipynb` code either run `data_seg.ipynb` and `encoding.ipynb` or downloaded, de-compressed, and place the pre-computed encodings in the `./encodings/` subfolder. 

**NOTE**: To make the figures shown in Fig 5 and 6, see code in the `/figs/` folder. 

## References

If you use our modification of Lu et al's codebase, please cite 

J. Lu and K. -Y. Tong, "Robust Single Accelerometer-Based Activity Recognition Using Modified Recurrence Plot," in *IEEE Sensors Journal*, vol. 19, no. 15, pp. 6317-6324, Aug. 1, 2019, doi: 10.1109/JSEN.2019.2911204.

```bibtex
@ARTICLE{lu_2019_recurrence_plot_har,
  author={Lu, Jianjie and Tong, Kai-Yu},
  journal={IEEE Sensors Journal}, 
  title={Robust Single Accelerometer-Based Activity Recognition Using Modified Recurrence Plot}, 
  year={2019},
  volume={19},
  number={15},
  pages={6317-6324},
  keywords={Accelerometers;Time series analysis;Correlation;Activity recognition;Hidden Markov models;Encoding;Accelerometer;activity recognition;deep learning;recurrence plot;signal recognition},
  doi={10.1109/JSEN.2019.2911204}}
```