#### 正则表达式 
- match只匹配一次
- findall匹配所有结果
- search匹配一次结果的索引
- finditer匹配匹配所有结果的索引

``` python
import re
pattern = r"\d+"
match_pattern = r'^.*?(\d+)'
s = 'dsaf123oid51156dsaf'

result_match = re.match(match_pattern,s)
result_findall = re.findall(pattern,s)
result_search = re.search(pattern,s)
result_finditer = re.finditer(r'\d+', s)


print(result_match.group(1),result_findall,result_search,sep='\n')
for item in result_finditer:
    print(item.group(),item.start(),item.end(),sep='\t')
```
``` plaintext
123
['123', '51156']
<re.Match object; span=(4, 7), match='123'>
123	4	7
51156	10	15
```
#### 获取时间名字
```python
import time
fv = time.strftime('%m%d_%H%M', time.localtime())
with open(f'./{fv}.txt','a') as fb:
    fb.write('hello world')
```


