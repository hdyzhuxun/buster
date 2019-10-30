from aip import AipOcr
import time
import os
#获取开始时间
start = time.time()

""" 你的 APPID AK SK """
APP_ID = '17606787'
API_KEY = 'pWTrwrgx22KZdD7n0Xs6aBqN'
SECRET_KEY = 'rYGBjAphAbPDGc8D7wEpucTV4wo9p0ts'

client = AipOcr(APP_ID, API_KEY, SECRET_KEY)


""" 读取图片 """
def get_file_content(filePath):
    print(filePath)
    with open(filePath, 'rb') as fp:
        return fp.read()
    
""" 写入文本 """
def write_on_txt(content,filePath,linefeed = "1"):
    """
    content：要写入的内容
    filePath：要写入文件的路径
    linefeed ：判断是否换行
        - 1 为不换行 
        - 其他 为换行
    """
    #只需要将之前的”w"改为“a"即可，代表追加内容
    with open(filePath,"a") as file:
        try:
            file.write(content)
        except:
            print("写入错误")
        else:
            if linefeed != "1":
                file.write("\n")

#图片路径
img_path = input("图片路径:")
#文本路径
txt_path1 = input("文本路径\文本名和格式.txt:")
txt_path = txt_path1 + ".txt"

options = {}

#遍历所有文件（使用 os.walk 方法）
for root,dirs,files in os.walk(img_path):
    for file in files:
        # 使用join函数将文件名称和文件所在根目录连接起来
        file_dir = os.path.join(root, file)
        print(file_dir)
        write_on_txt("=============================",txt_path,"0")
        write_on_txt("文件名:"+ file_dir,txt_path,"0")
        #判断是否是图片
        if file_dir[-4:]==".png"or file_dir[-4:]==".jpg":
            #传入图片
            image = get_file_content(file_dir)
            """ 调用通用文字识别, 图片参数为本地图片 """
            a = client.basicGeneral(image, options)
            # 查看返回的结果
            # print(a['words_result'])
            print()
            for dic in a['words_result']:
                print(dic['words'])
                write_on_txt(dic['words'],txt_path,"0")
                    
end = time.time()
print('Running time: %1.2f Seconds'%(end-start))
