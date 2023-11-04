Plotting
=================
- [Plotting](#plotting)
  - [3D plots](#3d-plots)
    - [Usages](#usages)
  - [GIFs](#gifs)
    - [Usages](#usages-1)

## 3D plots

Method signature:

```python
def plot3d(
    images: Union[str, Path, np.ndarray, List[Union[str, Path, np.ndarray]]],
    masks: Optional[
        Union[
            str,
            Path,
            np.ndarray,
            List[Union[str, Path, np.ndarray]],
        ]
    ] = None,
    rows: Optional[int] = None,
    columns: Optional[int] = None,
    mask_colors: Optional[List[str]] = None,
    cmap: str = "gray",
    titles: Optional[Union[str, List[str]]] = None,
    plane: str = "axial",
    save_path: Optional[Union[str, Path]] = None,
) -> None:
```

### Usages 

1. Basic Usage:
Plot a single image without any mask:

```python
    viz.plot3d('path/to/image.nii')
```

2. Plotting Multiple Images:
If you have multiple images to plot:

```python
    images = ['path/to/image1.nii', 'path/to/image2.nii']
    viz.plot3d(images)
```

3. Displaying Images with Masks:
To visualize images along with their corresponding masks:

```python
    images = ['path/to/image1.nii', 'path/to/image2.nii']
    masks = ['path/to/mask1.nii', 'path/to/mask2.nii']
    viz.plot3d(images, masks=masks)
```

4. Using Custom Colors:
To specify custom colors for the masks:

```python
    images = ['path/to/image1.nii', 'path/to/image2.nii']
    masks = ['path/to/mask1.nii', 'path/to/mask2.nii']
    colors = ['red', 'green']
    viz.plot3d(images, masks=masks, colors=colors)
```

5. Displaying Titles:
For adding titles to the plotted images:

```python
    images = ['path/to/image1.nii', 'path/to/image2.nii']
    masks = ['path/to/mask1.nii', 'path/to/mask2.nii']
    colors = ['red', 'green']
    titles = ['Image 1', 'Image 2']
    viz.plot3d(images, masks=masks, colors=colors, titles=titles)
```

6. Specifying Display Plane:
You can visualize the images in different planes:

```python
    viz.plot3d('path/to/image.nii', plane="sagittal")
```

7. Saving the Plot:
To save the plot to a specified location:

```python
    viz.plot3d('path/to/image.nii', save_path='path/to/save_directory/')
```

8. Specifying Rows and Columns:
To organize multiple images into a specific number of rows and columns:

Specify Rows:
```python
    images = ['path/to/image1.nii', 'path/to/image2.nii', 'path/to/image3.nii']
    viz.plot3d(images, rows=2)
```

This will generate a 2x2 grid, with the third image in the first cell of the second row.

Specify Columns:
```python
    images = ['path/to/image1.nii', 'path/to/image2.nii', 'path/to/image3.nii']
    viz.plot3d(images, columns=2)
```

This will also generate a 2x2 grid similar to the previous example.

Specifying Both Rows and Columns:
For more control, you can specify both rows and columns:

```python
    images = ['path/to/image1.nii', 'path/to/image2.nii', 'path/to/image3.nii', 'path/to/image4.nii']
    viz.plot3d(images, rows=2, columns=2)
```
This will arrange the images in a 2x2 grid with each cell having one image.

9. Combining Multiple Options:
You can also combine multiple options for a comprehensive view:

```python
    images = ['path/to/image1.nii', 'path/to/image2.nii']
    masks = ['path/to/mask1.nii', 'path/to/mask2.nii']
    titles = ["First Image with Mask", "Second Image with Mask"]
    mask_colors = ["#FF0000", "#00FF00"]
    viz.plot3d(images, masks=masks, mask_colors=mask_colors, titles=titles, save_path='path/to/save_directory/')
```

## GIFs

Method signature:

```python
    def gif(
        image: Union[str, Path, np.ndarray],
        masks: Optional[Union[str, Path, np.ndarray, List[Union[str, Path, np.ndarray]]]] = None,
        mask_colors: Optional[List[str]] = None,
        start_slice: Optional[int] = 0,
        end_slice: Optional[int] = None,
        slices: Optional[List[int]] = None,
        cmap: str = "gray",
        plane: str = "axial",
        save_path: Union[str, Path] = "output.gif",
        duration: int = 100,
        segments_title: Optional[List[str]] = None
    ) -> None:
```

### Usages

load image and mask(s) from file path:

```python
   image = 'path/to/image.nii' or 'path/to/image.nii.gz' or 'path/to/image.mha' or 'path/to/image.dcm'
   mask = 'path/to/mask.nii' or 'path/to/mask.nii.gz' or 'path/to/mask.mha' or 'path/to/mask.dcm'
   masks = ['path/to/mask1.nii', 'path/to/mask2.nii']

```

1. Basic Usage:

Generate a GIF from a 3D image without any masks:

```python
    viz.gif(image)
```
This will save the GIF as output.gif in the current directory.

2. Set save path:
```python
    viz.gif(image, save_path='path/to/save_directory/')
```

This will save the GIF as output.gif in the specified directory.

3. Overlaying Mask

To overlay mask on the image:

```python
    viz.gif(image, mask=mask)
```

4. Overlaying Multiple Masks

To overlay multiple masks on the image:

```python
    viz.gif(image, masks=masks)
```

This will overlay the masks in the order they are specified in the list.

5. Using Custom Colors

To specify custom colors for the masks:

```python
    viz.gif(image, masks=masks, mask_colors=['red', 'green'])
```

6. Displaying Titles

For adding titles to the plotted images:

```python
    viz.gif(image, masks=masks, mask_colors=['red', 'green'], segments_title=['Segment 1', 'Segment 2'])
```

7. Specifying Display Plane

You can visualize the images in different planes:

```python
    viz.gif(image, plane="sagittal")
```

8. Specifying Slices

To specify the slices to be included in the GIF:

```python
    viz.gif(image, slices=[0, 10, 20, 30, 40])
```

9. Define a range of slices

To specify a range of slices to be included in the GIF:

```python
    viz.gif(image, start_slice=20, end_slice=40)
```

10. Specifying Duration

To specify the duration of each frame in the GIF, the default is 100ms:

```python
    viz.gif(image, duration=200)
```

11. Combining Multiple Options

You can also combine multiple options for a comprehensive view:

```python
    viz.gif(image, masks=masks, mask_colors=['red', 'green'], segments_title=['Segment 1', 'Segment 2'], slices=[0, 10, 20, 30, 40], save_path='path/to/save_directory/')
```