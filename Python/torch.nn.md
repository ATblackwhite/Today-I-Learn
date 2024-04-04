#### DataParallel()
DataParallel类用于并行训练，用法
```python
if torch.cuda.device_count() > 1:
	model = torch.nn.DataParallel(model)
```