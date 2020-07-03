# get-id
def get_id(img_path):
    camera_id = []
    labels = []
    for path, v in img_path:
        #filename = path.split('/')[-1]#一样的效果
        filename = os.path.basename(path)#一样的效果 最后的图片名字
        label = filename[0:4]
        camera = filename.split('c')[1]
        if label[0:2]=='-1':
            labels.append(-1)
        else:
            labels.append(int(label))
        camera_id.append(int(camera[0]))
    return camera_id, labels

gallery_path = image_datasets['gallery'].imgs #
query_path = image_datasets['query'].imgs  #得到图片的地址+名字

gallery_cam,gallery_label = get_id(gallery_path)
query_cam,query_label = get_id(query_path)
