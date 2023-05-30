# Version: 2.0.0
FROM paddlepaddle/paddle:2.4.2-gpu-cuda11.2-cudnn8.2-trt8.0

# PaddleOCR base on Python3.7

WORKDIR /PaddleOCR

COPY . /PaddleOCR

RUN pip3.7 install --upgrade pip 

RUN pip3.7 install paddlehub --upgrade 

RUN pip3.7 install -r requirements.txt


# # 下载数据
# ADD https://paddleocr.bj.bcebos.com/ppstructure/dataset/XFUND.tar /PaddleOCR/train_data/
# RUN tar xf /PaddleOCR/train_data/XFUND.tar -C /PaddleOCR/train_data


# # 下载 det 检测推理模型
# ADD https://paddleocr.bj.bcebos.com/PP-OCRv3/chinese/ch_PP-OCRv3_det_infer.tar /PaddleOCR/inference/
# RUN tar xf /PaddleOCR/inference/ch_PP-OCRv3_det_infer.tar -C /PaddleOCR/inference

# # 下载 rec 识别推理模型
# ADD https://paddleocr.bj.bcebos.com/PP-OCRv3/chinese/ch_PP-OCRv3_rec_infer.tar /PaddleOCR/inference/
# RUN tar xf /PaddleOCR/inference/ch_PP-OCRv3_rec_infer.tar -C /PaddleOCR/inference

# # 下载 cls 方向推理模型
# ADD https://paddleocr.bj.bcebos.com/dygraph_v2.0/ch/ch_ppocr_mobile_v2.0_cls_infer.tar /PaddleOCR/inference/
# RUN tar xf /PaddleOCR/inference/ch_ppocr_mobile_v2.0_cls_infer.tar -C /PaddleOCR/inference

# # 下载 SER 推理模型
# ADD https://paddleocr.bj.bcebos.com/ppstructure/models/vi_layoutxlm/ser_vi_layoutxlm_xfund_infer.tar /PaddleOCR/inference/
# RUN tar xf /PaddleOCR/inference/ser_vi_layoutxlm_xfund_infer.tar -C /PaddleOCR/inference/

# # 下载 RE 推理模型
# ADD https://paddleocr.bj.bcebos.com/ppstructure/models/vi_layoutxlm/re_vi_layoutxlm_xfund_infer.tar /PaddleOCR/inference/
# RUN tar xf /PaddleOCR/inference/re_vi_layoutxlm_xfund_infer.tar -C /PaddleOCR/inference/

EXPOSE 8866

# CMD ["/bin/bash","-c","hub install deploy/hubserving/ocr_system/ && hub serving start -m ocr_system"]
CMD ["/bin/bash","-c","hub install deploy/hubserving/ocr_system/ && hub install deploy/hubserving/kie_ser/ && hub install deploy/hubserving/kie_ser_re/ && export CUDA_VISIBLE_DEVICES=0 && hub serving start -c deploy/docker/hubserving/kie/config.json"]