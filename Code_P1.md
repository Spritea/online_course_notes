# CODE笔记
## OpenCV3
### 语义分割
1. FileStorage类可以实现opencv中任何变量的硬盘导出与导入，包括C++/Python，目前导出BoW的dictionary
2. 超像素分割中，OpenCV3-Contrib模块的github官网上只有seeds算法的例子，没有slic算法的例子，尽管函数都有，目前暂用scikit-image库来做slic的超像素分割   
Tip：OpenCV可以做了，但输出是整幅图的每个像素的标签，需要自己写判断
3. OpenCV-Python中，没有SetROI之类的函数，因为在Python中，图像是用numpy库的格式来存储的，没有任何函数，截取图像image部分时，采用以下方式，由于numpy与C++中的Mat存储方式不同，故操作`img` 时，先列再行，并且中间是冒号`:` 
>img=cv2.imread("image.png")  
>img=img[col1:col1+50,row1:row1+50]
4. OpenCV C++的SVM，在load模型之后，还要做提取参数等处理，参见dji代码，对于Python模型，直接load模型就行，不用算参数，但注意load的语法不是
>svm = cv.ml.SVM_create()  
>svm.load("/test1/svm_data.dat")  
>//而是  
>svm = cv.ml.SVM_create()  
>svm=cv.ml.SVM_load("/test1/svm_data.dat")
5. 用这种方式找轮廓，并找最小包围矩形的时候，返回的矩形的坐标可能大于图像范围，这时需要处理一下负值和大于图像长/宽的值
>binary, contours, hierarchy = cv.findContours(img2, cv.RETR_EXTERNAL, cv.CHAIN_APPROX_SIMPLE)  
>rect = cv.minAreaRect(contours[0])  
>//得最小包围矩形，但rect存的是矩形中心点  
>box = cv.boxPoints(rect)  
>//把rect矩形中心点的表示改成4个顶点表示的方式，方便拿坐标  
>box_x = np.array([box[0][0], box[1][0],box[2][0], box[3][0]])  
>box_x = box_x.astype(int)  
>box_x[box_x<0]=0  
>box_x[box_x>(image.shape[1]-1)]=(image.shape[1]-1)  
>box_y = np.array([box[0][1], box[1][1], box[2][1], box[3][1]])  
>box_y = box_y.astype(int)  
>box_y[box_y<0]=0  
>box_y[box_y>(image.shape[0]-1)]=(image.shape[0]-1)  

<div STYLE="page-break-after: always;"></div>

6. `extend` 与`append` 区别：
    * `append` 可以用常量(如一个int)/元组(tuple)作输入，但`extend` 只能添加列表(list)

<div STYLE="page-break-after: always;"></div>

## PyCharm
### 环境配置
1. 程序执行完后还能显示变量
<div  align="center">    
<img src="pycharm_1.1.png" alt="图片名称" align=center />
</div>   
<br />
<div  align="center">    
<img src="pycharm_1.png" alt="图片名称" align=center />
</div> 

<div STYLE="page-break-after: always;"></div>

2. 编辑器中，让代码在顶端，下面有大片空白
<div  align="center">    
<img src="pycharm_2.1.png" alt="图片名称" align=center />
</div>  
<br />
<div  align="center">    
<img src="pycharm_2.png" alt="图片名称" align=center />
</div>  