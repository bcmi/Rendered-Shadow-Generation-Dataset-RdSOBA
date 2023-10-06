# Rendered-Shadow-Generation-Dataset-RdSOBA

**RdSOBA** is a large-scale Rendered Shadow Generation dataset containing object-shadow pairs like [**DESOBA**](https://github.com/bcmi/Object-Shadow-Generation-Dataset-DESOBA) dataset with 788 3D foreground objects, which is useful for supervised shadow generation methods.

<img src='examples/dataset.png' align="center" width=1024>

For more details, please refer to the following research paper:

> **RdSOBA: Rendered Shadow-Object Association Dataset**  [[arXiv]](https://arxiv.org/pdf/2306.17358.pdf)<br>
>
> Xinhao Tao†, Junyan Cao†, Li Niu

## Highlights

- 788 3D foreground objects
- 4 categories for foreground objects, containing "people", "animals", "vehicles", "plants"
- nearly 280,000 pairs of object-shadow pairs
- accurate masks
- 30 3D scenes
- 20 viewpoints(2D scene) for each 3D scene

## Downloads
We provide the data corresponding to the first two 3D scenes. The relevant links are as follows: [[Baidu_Cloud]](https://pan.baidu.com/s/1R-qy6qr4pxmMyS0d_28hGA) (access code: zu59) [[OneDrive]](https://1drv.ms/u/s!AoAsEmY10BjHgXBSaIRknROeo_i0?e=prdugm)

If you are interested in our full dataset, please feel free to contact us via [Email](taoxinhao@sjtu.edu.cn).

## Details

### Constructing 3D Scenes
We use Unity-3D to create 3D scenes and render images. We gather 788 diverse 3D objects from CG websites and 30 representative scenes from Unity Asset Store and CG websites. These collections provide a strong foundation for generating varied rendered images.

For each scene, we select 20 open areas for 3D objects, and choose 10 camera settings per area. After positioning the camera, we place a group of 1-5 3D objects in its view. We do this for 10 object groups per camera setting. Lastly, we render a set of 2D images under 5 different lighting conditions.

### Rendering 2D Images
After determining an open area, camera setting, group of 3D objects, and lighting condition in a 3D scene, we generate a set of images. First, we render an empty image $I_{empty}$.

We place $K$ 3D objects and toggle their visibility one by one. For the $k$-th object, we render images with and without shadows, $I_{o,k}$ and $I_{os,k}$. We calculate object and shadow masks, $M_{o,k}$ and $M_{s,k}$, based on these images.

Finally, we render an image $I_g$ with all object shadows. Designating one object as foreground, we create foreground and background masks for objects and shadows. We calculate $I_c$ using these masks, obtaining a tuple $(I_c,M_{fo},M_{fs},M_{bo},M_{bs},I_g)$ in the DESOBA dataset format.

After filtering out low-quality tuples, we have 280,000 tuples left.

## Other Resources

+ [Awesome-Object-Shadow-Generation](https://github.com/bcmi/Awesome-Object-Shadow-Generation)
+ [Awesome-Image-Composition](https://github.com/bcmi/Awesome-Image-Composition)
