# dnnls_final_project
# Visual Storytelling with a ResNet-Based Visual Autoencoder


## Quick Links
### Notebooks
[Basecase Notebook](https://github.com/c5060422/dnnls_final_project/blob/main/Final_template_Basecase_Sperarate_Losses.ipynb)  
[ResNet16 Notebook](https://github.com/c5060422/dnnls_final_project/blob/main/Final_template_ResNet16.ipynb)  
[ResNet32 Notebook](https://github.com/c5060422/dnnls_final_project/blob/main/Final_template_ResNet32.ipynb)  
[ResNet64 Notebook](https://github.com/c5060422/dnnls_final_project/blob/main/Final_template_ResNet64.ipynb)  
[ResNet128 Notebook](https://github.com/c5060422/dnnls_final_project/blob/main/Final_template_ResNet128.ipynb)

### Results Tables
[Basecase Loss Summary](https://github.com/c5060422/dnnls_final_project/blob/main/loss_summary_basecase.csv)  
[ResNet16 Loss Summary](https://github.com/c5060422/dnnls_final_project/blob/main/loss_summary_resnet16.csv)  
[ResNet32 Loss Summary](https://github.com/c5060422/dnnls_final_project/blob/main/loss_summary_resnet32.csv)  
[ResNet64 Loss Summary](https://github.com/c5060422/dnnls_final_project/blob/main/loss_summary_resnet64.csv)  
[ResNet128 Loss Summary](https://github.com/c5060422/dnnls_final_project/blob/main/loss_summary_resnet128.csv)  

### Overall Results Summary
[Results Summary](https://github.com/c5060422/dnnls_final_project/blob/main/Results_Summary.csv)


## Innovation Summary
I replaced the existing visual autoencoder with a ResNet-based version. Along with introducing a new Image_Latent_Dim variable, this allowed me to experiment with latent dimensions of 16, 32, 64, and 128 while keeping the rest of the code unchanged.  

I expected that increasing the latent dimension would lead to improved image loss performance.  

In addition, I separated the individual loss functions so they could be tracked independently while preserving the existing overall loss function.


## Key Results
**Basecase**
| **Epoch** | **Total Loss** | **Image Loss** | **Context Loss**  | **Text Loss** |
|-----------|----------------|----------------|-------------------|---------------|
| 1         | 4.3586         | 0.2409         | 0.0034            | 4.1171        |
| 2         | 4.3592         | 0.2410         | 0.0034            | 4.1176        |
| 3         | 4.3591         | 0.2409         | 0.0033            | 4.1175        |
| 4         | 4.3587         | 0.2408         | 0.0033            | 4.1172        |
| 5         | 4.3590         | 0.2409         | 0.0034            | 4.1175        |


**Results Summary**
| **Model**    | **Epoch** | **Total Loss** | **Image Loss** | **Context Loss** | **Text Loss** |
|--------------|-----------|----------------|----------------|------------------|---------------|
| Basecase     | 5         | 4.3590         | 0.2409         | 0.0034           | 4.1175        |
| ResNet16     | 5         | 4.3626         | 0.2415         | 0.0031           | 4.1205        |
| ResNet32     | 5         | 4.3700         | 0.2418         | 0.0032           | 4.1276        |
| ResNet64     | 5         | 4.3625         | 0.2417         | 0.0031           | 4.1202        |
| ResNet128    | 5         | 4.3608         | 0.2415         | 0.0032           | 4.1187        |
| ResNet128    | 10        | 4.3602         | 0.2415         | 0.0031           | 4.1181        |


## Most Important Findings
The innovation has not improved the model, as the results show no meaningful change in performance. The model appears not to be learning, which is also evident from the minimal variation across epochs in the base case. This behaviour suggests the presence of bugs elsewhere in the system or a bottleneck in other latent variables such as the text latent dimension or the GRU.  

When the loss functions are separated, the Text Loss is significantly higher than both the Image Loss and the Context Loss. This imbalance may be limiting the system’s ability to generate accurate image predictions.  

To move forward, I believe the Text Loss should be prioritised. Additionally, a systems-thinking approach would be beneficial, examining the model holistically rather than focusing on any single component in isolation.


## How to Reproduce
1. Open any of the notebooks e.g. https://github.com/c5060422/dnnls_final_project/blob/main/Final_template_ResNet16.ipynb
2. Set the Image_Latent_Dim variable to the desired value (16, 32, 64, 128). 
3. Amend the output filename to match the desired value. If you open each individual notebook this and the Image_Latent_Dim  variable is already set.
4. Run cells sequentially (takes about 15 mins on a T4 GPU with 5 epochs)
5. Results table shown in the output and saved as a .CSV file in the DL_Checkpoints directory.
