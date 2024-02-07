# LiteMedSAM Quant.

A quantized version of LiteMedSAM deployed on https://litesamquant.streamlit.app/. This README provides instructions and details for running the LiteMedSAM application, which includes three main components: streamlit_app.py, APIs_Backend_and_deployment_modelBit.ipynb. This application is designed to process medical images in JPG format and predict segmentation masks using both the non-quantized version of LiteMedSAM and the quantized. 


## Installation
To run the application, ensure the following dependencies are installed:

Python 3.x
Streamlit
modelbit
PyTorch
OpenCV (cv2)
NumPy
Matplotlib
Pillow (PIL)
BytesIO (from io)
The requirements_webapp.txt

## Installation steps

- Clone the repository or download the source code.
- Install the required Python libraries:
- Place the tiny_vit_sam.py and segment_anything module in the same directory as the main scripts, or ensure they are accessible in your Python path.
- Download and place the model checkpoint file into work_dir/lite_medsam.pth https://drive.google.com/file/d/18Zed-TUTsmr2zc5CHUWd5Tu13nb6vq6z/view .

## Quantization test

- Download the LiteMedSAM checkpoint here and put it in `work_dir/LiteMedSAM`.
- Download the demo data [here](https://drive.google.com/drive/folders/1t3Rs9QbfGSEv2fIFlk8vi7jc0SclD1cq?usp=sharing)
- For model size comparison before and after quantization check Lite_MedSam_size_reduction_quantization.ipynb (model size reduction by 66%). The IOU pred performance is also in the notebook.
- For non quantized test: python CVPR24_LiteMedSAM_infer.py -i test_demo/imgs/ -o test_demo/segs
- For quantized test: python CVPR24_LiteMedSAM_infer_8bit_quantized.py -i test_demo/imgs/ -o test_demo/segs
- Check the inference performance result on the command and the inference time on test_demo/segs/efficiency.csv. The quantized inference is faster than non-quantized.

# Running on Streamlit 
The application is already deployed on https://litesamquant.streamlit.app/
To try it just run the command: streamlit run streamlit_app.py on the terminal. There is no need for the files since all the functionality is done by API calls (REST APIs on ModelBit). 
