>以下内容来自chatGPT

### 文件和目录操作
- **获取当前工作目录**
```python
	current_directory = os.getcwd()
	print("当前工作目录是:", current_directory)
```
- **改变当前工作目录**
```python
	new_directory = '/path/to/new/directory'
	os.chdir(new_directory)
	print("现在的工作目录是:", os.getcwd())

```
- **列出目录内容**
```python
directory_content = os.listdir('.')
print("目录内容:", directory_content)
```
[[判断文件夹是否为空]]
- **重命名文件或目录**
```python
os.rmdir('directory_name')  # 只能删除空目录
```
- 检查文件/文件夹是否存在
```python
if os.path.exists(folder_path):
    print("文件/文件夹存在")
```
- 判断是否是文件夹
```python
if os.path.isdir(folder_path):
    print("路径是文件夹")
```
- **创建新目录**
```python
new_dir_path = 'new_directory'
os.makedirs(new_dir_path, exist_ok=True)  # exist_ok=True 防止目录已存在时报错
```
[[检查文件夹是否存在，如果不存在创建新文件夹#使用OS模块]]

### 环境变量操作
- **获取环境变量**
```python
path_env = os.getenv('PATH')
print("PATH 环境变量:", path_env)
```
- **设置环境变量**
```python
os.environ['NEW_VAR'] = 'value'
```
[[ubuntu使用clash代理#在Python中使用代理]]

### 执行操作系统命令
- **执行命令**
```python
os.system('ls')  # 在Unix/Linux中列出当前目录内容，在Windows中使用'dir'
```

### 路径操作
- **连接路径**
```python
full_path = os.path.join('path', 'to', 'file.txt')
print("完整路径:", full_path)
```
- **获取文件的绝对路径**
```python
absolute_path = os.path.abspath('relative/path/to/file')
print("绝对路径:", absolute_path)
```

