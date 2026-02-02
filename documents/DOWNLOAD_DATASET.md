## Dataset Downloading

### 1. LIBERO 

For LIBERO, you can refer to the [LIBERO source code](https://github.com/Lifelong-Robot-Learning/LIBERO?tab=readme-ov-file#Datasets).

Alternatively, you can download the datasets locally using the following links:

- [LIBERO-Goal](https://utexas.box.com/shared/static/iv5e4dos8yy2b212pkzkpxu9wbdgjfeg.zip)
- [LIBERO-Object](https://utexas.box.com/shared/static/avkklgeq0e1dgzxz52x488whpu8mgspk.zip)
- [LIBERO-Spatial](https://utexas.box.com/shared/static/04k94hyizn4huhbv5sz4ev9p2h1p6s7f.zip)
- [LIBERO-100](https://utexas.box.com/shared/static/cv73j8zschq8auh9npzt876fdc1akvmk.zip)

The structure is:

```
datasets
│
├── libero_10           
│
├── libero_90     
│
├── libero_goal   
│
├── libero_object
│
└── libero_spatial
```

**Attention**: Our experimental setup differs from that of papers like [OpenVLA](https://github.com/openvla/openvla/blob/main/experiments/robot/libero/regenerate_libero_dataset.py). In those works, the image observations are saved at a resolution of 256×256 (instead of 128×128) and undergo additional filtering, such as removing "no-op" (zero) actions and unsuccessful demonstrations.
In contrast, our setting uses the raw LIBERO data with lower-resolution images and no filtering.
