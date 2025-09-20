```python
import os
from tqdm import tqdm
import re
import eyed3

def get_mp3_duration(file_path):
    audio = eyed3.load(file_path)
    if audio is None:
        return None
    return audio.info.time_secs

def catalogName_check(root_in):
    '''
    调用修改文件夹文字
    '''
    catalog = os.listdir(root_in)
    pattern = r'[^\w\u4e00-\u9fa5,.!?;:、，。！？；："\'\\‘’“”()（）【】《》〈〉-]'
    for filename in  catalog:
        if os.path.isdir(filename):
    # file_path = os.path.join(catalog,file)
            new_filename = re.sub(pattern,'-',filename)
            os.rename(filename,new_filename)

def filename_check(root_in):
    '''
    调用修改文件名字
    '''
    pattern = r'[^\w\u4e00-\u9fa5,.!?;:、，。！？；："\'\\‘’“”()（）【】《》〈〉-]'
    catalog_list = os.listdir(root)
    for catalog in catalog_list:
        catalog_path = os.path.join(root,catalog)
        if os.path.isdir(catalog_path):
            for file in tqdm(os.listdir(catalog_path)):
                file_path = os.path.join(catalog_path,file)
                new_file_path = re.sub(pattern,'-',file_path)
                os.rename(file_path,new_file_path)

root = '.\\'
catalog_list = os.listdir(root)
pattern = r'[^\w\u4e00-\u9fa5,.!?;:、，。！？；："\'\\‘’“”()（）【】《》〈〉-]'
time_dict = {}
catalogName_check(root)
filename_check(root)

for catalog in catalog_list:
    if os.path.isdir(catalog):
        cnt = 0
        for file in tqdm(os.listdir(catalog)):
            file_path = os.path.join(catalog,file)
            duration = get_mp3_duration(file_path)
            cnt += duration

    day = f'{int(cnt//60//60//24)}'
    hour = f'{int(cnt//60//60 % 24)}'
    minute  = f'{int(cnt//60 % 60)}'
    sec = f'{cnt % 60 :.1f}'
    time_dict[catalog] = f'{day}d {hour}h {minute}min {sec}sec'
    print(cnt)
    # print(f'{catalog}:\t{cnt // (60*60)}h{(cnt % (60*60)//60)}min')
for key,value in time_dict.items():
    print(key,'\t',value)
```
