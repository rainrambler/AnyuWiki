- **查找所有匹配字符串**
	- `import re`
	- `arr = re.findall(r'第[〇一二三四五六七八九]+章', content)`
- **读取文本文件所有内容**
	- ```
	  with open(filename, 'r', encoding='UTF-8') as file:
	          data = file.read()
	          return data
	  ```
- #Python
-