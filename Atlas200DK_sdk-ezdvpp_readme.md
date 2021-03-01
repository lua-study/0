EN|[CN](README_cn.md)


The EZDVPP encapsulates the DVPP APIs to simplify the calls. The main functions include:

Image format conversion \(including YUV to JPG, and JPEG to YUV\), image cropping, and image resizing.

The methods of using EZDVPP APIs are as follows:

-   Image format conversion

    -  Convert YUV data streams obtained by the camera into JPG data streams.

        ```
        // Interface usage example: YUV-to-JPG conversion
        typedef struct DvppOutputInfo {
        //output buffer
        unsigned char *pbuf;
        //size of output buffer
        unsigned int size;
        } DvppOutput;
        Ascend::Utils::DvppProcess *pDvppProcess=nullptr;
        // Initialization parameter for converting YUV into JPG
        dvppToJpgPara.format = JPGENC_FORMAT_NV12;
        dvppToJpgPara.level = DVPP_TO_JPG_QUALITY_PARAMETER;
        dvppToJpgPara.resolution.height = height;
        dvppToJpgPara.resolution.width = width;
        // Instantiated class variable
        pDvppProcess = new Ascend::Utils::DvppProcess(dvppToJpgPara);
        // Conversion interface. dvppOutput.pbuf is the converted JPG data.
        pDvppProcess->DvppOperationProc(inputbuf,inputbufSize,&dvppOutput)
        ```


    -   JPEG-to-YUV conversion: Convert an input JPEG image into a YUV image. The JPEG \(color space: YUV, subsample: 444/422/420/400\) supports only Huffman coding and does not support arithmetic coding, progressive coding, or JPEG 2000 format.

        ```
        Interface 4: JPEG-to-YUV conversion
        struct DvppJpegDOutput {
            unsigned char *buffer;  // output buffer
            uint32_t buffer_size;  // output buffer size
            uint32_t width;  // the width of output image
            uint32_t height;  // the height of output image
            uint32_t aligned_width;  // the aligned width of output image
            uint32_t aligned_height;  // the aligned height of output image
            VpcInputFormat image_format;  //output image format
        };
        ascend::utils::DvppJpegDInPara dvpp_to_yuv_para;
        dvpp_to_yuv_para.is_convert_yuv420 = true;
        ascend::utils::DvppProcess dvpp_yuv_process(dvpp_to_yuv_para);
        ascend::utils::DvppJpegDOutput dvpp_out_data = { 0 };
        dvpp_yuv_process.DvppJpegDProc(face_image_buff,
                                       face_image_size,
                                       &dvpp_out_data);
        ```


-   Image cropping, image resizing, and format conversion

    Convert the input YUV444SP/YUV422SP/YUV420SP/YUV444Packed/YUV422Packed/BGR/RGB/ARGB/ABGR/RGBA/BGRA image into a YUV420SP image and perform image cropping and resizing.

    ```
    // Interface usage example: format conversion and image resizing (In this sample code, image cropping is not performed.)
    struct DvppVpcOutput {
        uint8_t *buffer;
        uint32_t size;
    };
    DvppBasicVpcPara resize_para;
    resize_para.input_image_type = INPUT_BGR;
    
    // get original image size and set to resize parameter
    int32_t width = image_handle->image_info.width;
    int32_t height = image_handle->image_info.height;
    
    // set source resolution ratio
    resize_para.src_resolution.width = width;
    resize_para.src_resolution.height = height;
    
    // crop parameters, only resize, no need crop, so set original image size
    // set crop left-top point (need even number)
    resize_para.crop_left = 0;
    resize_para.crop_up = 0;
    // set crop right-bottom point (need odd number)
    uint32_t crop_right = ((width >> 1)  > 1)  console_params.model_width) >> 1)  console_params.model_height) >> 1)  image_info.data.get(), image_handle->image_info.size,
          &dvpp_output);
    ```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)