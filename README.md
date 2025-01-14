# ARF: Artistic Radiance Fields
Additional video results are available at: <http://www.contrib.andrew.cmu.edu/~qiyuc/16824-final-project/project_website/>

![](./resources/fortress_brutal.mov)


## Quick start

### Install environment
```bash
. ./create_env.sh
```
### Download data
```bash
. ./download_data.sh
```
### Optimize artistic radiance fields
1. Download data using the above script or prepare your own data following steps on [Plenoxel](https://github.com/sxyu/svox2).
2. Prepare the target style image inside ```./data/styles```. Also crop background patches from training images or image generated from trained radience field and put their path as a comma separate string within the config file (e.g. ```opt/configs/llff_geom3e3Clip0.5TNegStylesTV5.json```). 
3. Change the style image description, negative style image description, and original image description inside ```opt/nnfm_loss.py```.
4. Execute script ```{llff/tnt/custom}.sh``` or ```{llff/tnt}_exp.sh```. E.g.
```bash
cd opt && . ./try_{llff/tnt/custom}.sh [scene_name] [style_id]
```
* Select ```{llff/tnt/custom}``` according to your data type. For example, use ```llff``` for ```flower``` scene, ```tnt``` for ```Playground``` scene, and ```custom``` for ```lego``` scene. 
* ```[style_id].jpg``` is the style image inside ```./data/styles```. For example, ```14.jpg``` is the starry night painting.
* Note that a photorealistic radiance field will first be reconstructed for each scene, if it doesn't exist on disk. This will take extra time.

### Check results
The optimized artistic radiance field is inside ```opt/ckpt_arf/[scene_name]_[style_id]```, while the photorealistic one is inside ```opt/ckpt_svox2/[scene_name]```.

### More information
For more information and details, we refer you to check [Plenoxel](https://github.com/sxyu/svox2) and [ARF](https://github.com/Kai-46/ARF-svox2) GitHub pages.

## Acknowledgement:
We would like to thank the following authors for open-sourcing their implementations:
* [Plenoxel](https://github.com/sxyu/svox2)
* [ARF](https://github.com/Kai-46/ARF-svox2) 
  * Project page: <https://www.cs.cornell.edu/projects/arf/>
  * ![](./resources/ARF.mov)
