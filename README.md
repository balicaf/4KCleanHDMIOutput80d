# 4KCleanHDMIOutput80d
The goal of this project is to live stream a clean signal from canon 80d (autofocus square removed) and upscale it to UHD in real time (for live streaming on Youtube)

with canon80d, HDMIto usb converter Jetson Nano.

inpainting/watermark removal https://dmitryulyanov.github.io/deep_image_prior.

It can be done in 2 steps: first detect square (non compressed image means unique color ID), second inpaint it.
Third upsacalling can be done simply with 

gst-launch-1.0 videotestsrc ! video/x-raw,width=1280,height=720 ! nvvidconv ! 'video/x-raw(memory:NVMM),width=1280,height=720' ! nvvidconv ! 'video/x-raw(memory:NVMM),width=1920,height=1080' ! nvoverlaysink

and uploading to youtube with: 
https://gist.github.com/joeladdison/6e9fe495eab7856a44d9f405ed493af8
