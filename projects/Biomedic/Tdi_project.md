---
layout: post
title: Digital Image Treatment Application
---
*****
First of all, this project has been made with the collaboration of all the students signed in the 2021 Digital Image Treatment 
subject and the professor (Carlos Oscar S.Sorzano) through a collaborative repository in Github.  

The repository link is the following: [Repository Link CeuImgProc](https://github.com/cossorzano/CEUImgProc)

This project has been programmed in Matlab language to perform a Matlab application with an easy and intuitive graphic user interface.  

My contributions to this project have been developing a specific tool to increase and decrease the contrast of an image in each
of its color channels; and a tool to pixelate an image depending on a level of pixelization desired by the user.  



### Increase and decrease contrast Tool:

This tool compute the increase and the decrease of the contrast to an image using the Matlab 
function Imadjust.  

To use this tool, you have to bear in mind that the left slider must be lower than the right slider of the same color channel. 
Otherwise, an orange warning is shown in the application interface specifying the color channel where the problem is.  

The tool is divided in four main regions:
- Sliders: control the increase or decrease quantity that we want to apply to the image.
- Image frame: Where changes in the image are shown.
- Warnings advices: Where warnings are shown in case of the sliders values were in wrong position.
- Export button: to export the image to another frame to save it or do other operations with it.  

The formula applied to make the contrast transformation is: 
<div align="center">
<img src="/images/projectsImages/biomedicProjects/ContrastFormula" alt="PContrast Formula" width="100%"/></div>

To access to de the code in Github:  [Increase and decrease contrast code in Github Link](https://github.com/cossorzano/CEUImgProc/blob/master/CeuL4_IncreaseDecreaseContrastApp.mlapp)

The following gif explain how the tool works:  
<div class="img-contenedor">
<img src="/images/projectsImages/biomedicProjects/DecreaseIncreaseContrast_JaimeBermejo.gif" alt="Toolvideodemostration" title="Toolvideodemostration" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
">
</div>



Below we can find the main code in matlab, this is the part of the code that compute the contrast, but only in one channel with one slider:  
(To complete the program you must to add this code changing the variables depending on the slider and the color channel)  

```matlab

        % Button pushed function: ExporttootherwindowButton
        function ExporttootherwindowButtonPushed(app, event)
            I = getimage(app.h);
            windowName = app.h.Name;
            
            rlow=0;
            rhigh=1;
            glow=0;
            ghigh=1;
            blow=0;
            bhigh=1;
            
            if app.RedSlider1.Value > app.RedSlider2.Value || app.GreenSlider1.Value>app.GreenSlider2.Value || app.BlueSlider1.Value>app.BlueSlider2.Value
                app.WarningExport.Text=strcat("Operation not permitted, look the orange warnings");
            else
                app.WarningExport.Text=strcat(" ");
                rlow=app.RedSlider1.Value;
                rhigh=app.RedSlider2.Value;
                glow=app.GreenSlider1.Value;
                ghigh=app.GreenSlider2.Value;
                blow=app.BlueSlider1.Value;
                bhigh=app.BlueSlider2.Value;
                K = imadjust(I,[rlow glow blow; rhigh ghigh bhigh],[]);
                hr = figure('Name',strcat(windowName," (contrast)"));
                imshow(K);
                figure(hr);

            end
        
            disp('hello');
        end
        %bermejo4
```
### Pixelization Tool:

This tool accept an image and pixelate it depending on a factor taken from a slider in the left side. When the result wanted
is obtained, clicking in the "View Pixel Regions" button the values of each pixel can be observed, and also the quantities 
of pixels that form a block o big pixel in the pixelated image.

The tool consists in three main parts:
- Image frame: Where the transformation of the image, the pixelization, is shown.
- Slider: Depending on the position of the slider the pixelization level is higher or lower. 
- 'View Pixel Region' button: To view the pixel region of the image, that means, if the cross is pointer of one pixel, 
  the value of this pixel and their neighbors is shown in other frame. If the cross grows we can observe the quantity 
  of pixels that form part of a block of the pixelated image.  
  
  
To access to de the code in Github:  [Pixelization code in Github Link](https://github.com/cossorzano/CEUImgProc/blob/master/CeuL11_PixelizationApp.mlapp)

  
The following gif explain how the tool works:  
<div class="img-contenedor">
<img src="/images/projectsImages/biomedicProjects/Pixelization_JaimeBermejo.gif" alt="Toolvideodemostration" title="Toolvideodemostration" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
">
</div>  

Below we can find the main code in matlab:
````matlab
        % Button pushed function: ViewpixelregionsButton
        function ViewpixelregionsButtonPushed(app, event)
            I = getimage(app.h);
            windowName = app.h.Name;
            IExp=app.Image.ImageSource;
            imshow(IExp);
            impixelregion;
        end
        %bermejo4

        % Value changed function: Slider
        function SliderValueChanged(app, event)
            value = round(app.Slider.Value);
            
            I = getimage(app.h);
            windowName = app.h.Name;

            fun1 = @(block_struct) round(mean(block_struct.data(:)),1) * ones(size(block_struct.data));

            I2=zeros(size(I));
            
            I2(:,:,1) = blockproc(I(:,:,1),[value value],fun1);
            I2(:,:,2) = blockproc(I(:,:,2),[value value],fun1);
            I2(:,:,3) = blockproc(I(:,:,3),[value value],fun1);
            
            I3=cast(I2, 'uint8');
            app.Image.ImageSource=I3;
        end
    end
    %bermejo4


````