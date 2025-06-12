# Component-Level OBI Retrieval
Source code and dataset for ICMR'24 paper "[Component-Level Oracle Bone Inscription Retrieval](https://dl.acm.org/doi/abs/10.1145/3652583.3658116)" (Best Paper Candidate)

You may find our other works on OBI:

- [[AAAI'25] Component-Level Segmentation for Oracle Bone Inscription Decipherment](https://github.com/hutt94/Component-Level-OBI-Segmentation)

## 0. To Do List
1. -[x] Task Definition
2. -[x] dataset
3. -[x] code

## 1. Task Definition
Oracle Bone Inscriptions (OBIs) are pictographic scripts, various realworld entities are abstracted into distinct components within OBIs to represent different meanings, such as "foot", "person", and "water". Subsequently, a more nuanced semantics is conveyed through the combination of these components. Figure below illustrates four examples, i.e., "stand", "pace", "wade", and "climb", of deciphered OBIs. 
- **企 Stand** is constituted by one "止 foot" component and one "人 person" component, symbolizing an individual standing upright.
- **步 Pace** is formed by two "止 foot" components arranged in a front-and-back configuration, symbolizing an act of stepping once.
- **涉 Wade** is composed of two "止 foot" components in a front-and-back arrangement, with one "水 water" component intersecting through them, symbolizing walking into the water.
- **陟 Climb** is constructed with two upward-facing "止 foot" components and one "阜 mound" component, symbolizing ascending a mound.

Each of them is composed of the "foot" component along with other distinct components. This diversity in constituent components results in distinct meanings for these characters. However, since these characters all incorporate the "foot" component, they share a certain semantic association with each other. Therefore, linking different OBIs through their respective components holds significant implications. Specifically, exploring the patterns among characters sharing the same component facilitates the deciphering and comprehension of OBIs. 

To this end, we propose **Component-level Oracle Bone Inscription Retrieval**, i.e., given a component, the goal is to retrieve all OBIs that incorporate this particular component.

![Capture](https://github.com/user-attachments/assets/e6abbca2-73c3-472f-9f3e-d66b950e894d)

## 2. Dataset
### 2.1. Introduction
In **OBI Component 20**, we have selected 20 common OBI components. Due to the different forms each component can take, we chose representative forms to display in the following diagram. 

![image](https://github.com/user-attachments/assets/82687c53-2ead-4eb0-ab37-a13e110ccd04)

Then, we collected 11,335 OBI character images from the [小學堂](https://xiaoxue.iis.sinica.edu.tw/) based on these components. We invited [Prof. Pui-ling Tang](https://web.chinese.hku.hk/en/people/staff/113/) and Ms. Peiying Zhang from the School of Chinese, the University of Hong Kong to screen these characters, removing images that did not contain the 20 selected components, leaving us with 9,245 OBI character images. Within these images, Ms. Zhang further annotated the specific positions of the components in 1,012 OBI character images, striving to cover the different forms of the same component. Ultimately, OBI Component 20 contains a total of 10,257 OBI images, of which 9,245 are OBI characters and 1,012 are OBI components. Their distribution is as shown in the table below.

| ID | Component| # Character | # Component | ID | Component| # Character | # Component |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| 0 | 日 | 371 | 18 | 10 | 女 | 641 | 29
| 1 | 月 | 106 | 41 | 11 | 子 | 179 | 33
| 2 | 雨 | 152 | 17 | 12 | 目 | 422 | 31
| 3 | 阜 | 115 | 16 | 13 | 攴 | 414 | 91
| 4 | 水 | 622 | 41 | 14 | 止 | 1132 | 72
| 5 | 屮 | 267 | 14 | 15 | 衣 | 69 | 51
| 6 | 木 | 465 | 24 | 16 | 口 | 1592 | 42
| 7 | 犬 | 204 | 117 | 17 | 王 | 55 | 8
| 8 | 大 | 385 | 32 | 18 | 矢 | 383 |32
| 9 | 人 | 1403 | 226 | 19 | 刀 | 268 | 77

For more details about the dataset, please refer to [here](https://github.com/hutt94/Component-Level_OBI_Retrieval/tree/main/OBI_Component_20).

### 2.2. Request for Dataset
Considering copyright issues, if you need to use this dataset, please provide the following information (either in Chinese or English) in an email to cszkhu@comp.hkbu.edu.hk **AND c.c.** zhangpeiying99@gmail.com (Ms. Peiying Zhang). We will provide you with the dataset download link within 5 working days after receiving your email (**It should be a valid .edu email that matches your institution**): 
1. your name,
2. your institution,
3. the intended use of the dataset, and
4. a declaration ensuring that it will not be used for commercial profit.

## 3. Code
Train the model:
```
python train.py --componet_path components_file_name /
                --character_path characters_file_name /
                --epoch 80 /
                --batch_size=32 /
                --num_class=20
```

Test the model:
```
python test.py --componet_path components_file_name /
               --character_path characters_file_name
```

Visualize the retrieval results:
```
python visual.py --componet_path components_file_name /
                 --character_path characters_file_name /
                 --k=10
```

## 4. Citation
```
@inproceedings{hu2024component,
  title={Component-Level Oracle Bone Inscription Retrieval},
  author={Hu, Zhikai and Cheung, Yiu-ming and Zhang, Yonggang and Zhang, Peiying and Tang, Pui-ling},
  booktitle={Proceedings of the 2024 International Conference on Multimedia Retrieval},
  pages={647--656},
  year={2024}
}
```

## Acknowledgments
We would like to thank [小學堂](https://xiaoxue.iis.sinica.edu.tw/) for sharing the public OBI data. We are also grateful to [Mr. Changxing Li](https://github.com/li1changxing) for his assistance with the data collection and code implementation.
