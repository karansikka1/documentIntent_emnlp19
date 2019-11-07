## Dataset release for EMNLP_2019 [paper](https://arxiv.org/pdf/1904.09073.pdf) titled "*Integrating Text and Image: Determining Multimodal Document Intent in Instagram Posts*". 


## Guidelines:
 - ### Training and Validation Splits:
    - We perform experiments on 5 random splits in our paper. These splits are present in folder ```splits_new``` with first part of the name specifying whether it is a train or validation split. For example ```train_split_0.json``` and```val_split_0.json``` refer to the first train and val splits respectively. 
    - The final performance is reported by averaging the performance across these splits. For details refer to the paper. 
    - Each of these split files is a json containing lists. Each element of the list has following keys:
    - ```filename```: filename of the image/feature 
        - ```semiotic```: label for semiotic category 
        - ```intent```: label for intent category  
        - ```imgTxt```: label for contexual category 
        - ```caption```: cleaned caption of the post 
        - ```tags```: hashtags (we did not use these in the paper)
        - ```url```: original url of the image (please see comment below)
        - ```likes```: no of likes
        - ```orig_caption```: orig caption (with emoticons etc.)

2. ### Image Features 
    - Due to recent restrictions on releasing image data collected from social media websites (Instagram in our case), we are unable to release the original images. We only release the deep features for each image (last layer of ResNet-18) as used in our paper for the purpose of reproducing the results and conducting additional experiments. 
    - We are still trying to find ways to release the images or working urls for these images (original urls are provided but most of them are expired).  
    - These features are available in tar ```resnet18_feat.tar```. Each feature is a ```.npy``` containing the image feature and are named using the ```filename``` key in the splits
    - **Reproducing results**: In the paper we trained only the embedding and classification layers and did not fine-tune the Resnet-18 network. The only difference when using the provided features is the we used random crops for training. To allow a fair comparison with these features for future work, we report the AUC performance of the model using images for the three taxonomies below 


```
|                	| Intent 	| Semiotic 	| Contextual 	|
|----------------	|--------	|----------	|------------	|
| Img            	| 73.8   	| 58.8     	| 62.5       	|
| Img + Txt-Emb  	| 81.4   	| 69.9     	| 76.2       	|
| Img + Txt-ELMo 	| 85.3   	| 69.1     	| 78.8       	|

```
The results are quite close to those reported in the paper. 

3. We give list of the labels for the three taxonomies in the folder ```labels```. Note that we use ```imgTxt_labels``` to refer to Contextual relationship (as used in the paper).  


## Citing
Please cite the following paper if you are using this dataset for you research.
```
@article{kruk2019integrating,
  title={Integrating Text and Image: Determining Multimodal Document Intent in Instagram Posts},
  author={Kruk, Julia and Lubin, Jonah and Sikka, Karan and Lin, Xiao and Jurafsky, Dan and Divakaran, Ajay},
  journal={arXiv preprint arXiv:1904.09073},
  year={2019}
}
```

Check [Link](http://ksikka.com/document_intent.html) for project webpage and video about this work.

## Contact
Please email ajay.divakaran@sri.com or karan.sikka@sri.com (karan.sikka1@gmail.com) for any questions regarding the dataset. 
