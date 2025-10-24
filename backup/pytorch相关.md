#### F.nll_loss()的用法
```python
import torch
import torch.nn as nn
import torch.nn.functional as F
mat = torch.rand((4,8))
idx = torch.randint(0,8,(4,1))
print(mat,'\n',idx)
print(mat.shape,idx.shape)
F.nll_loss(mat,idx.flatten())
```
```plaintext
tensor([[0.1187, 0.5472, 0.1068, 0.7665, 0.0128, 0.3709, 0.9943, 0.0043],
        [0.2665, 0.3760, 0.2964, 0.2761, 0.1714, 0.5029, 0.9437, 0.9453],
        [0.6575, 0.6743, 0.8379, 0.6989, 0.8964, 0.0499, 0.0252, 0.3739],
        [0.5510, 0.4354, 0.3499, 0.7285, 0.2500, 0.2207, 0.7897, 0.5403]]) 
 tensor([[0],
        [5],
        [2],
        [7]])
torch.Size([4, 8]) torch.Size([4, 1])
tensor(-0.4999)
```
#### torch.searchsorted()用法
```python
import torch
bins = torch.rand((4,8))
bins = bins.cumsum(1)/bins.sum(1).unsqueeze(1)
targets = torch.rand((1,4))
result = torch.searchsorted(bins,targets.T)
print(bins.shape,targets.T.shape,result.shape)
print(bins,targets,result,sep='\n')
```
```plaintext
torch.Size([4, 8]) torch.Size([4, 1]) torch.Size([4, 1])
tensor([[0.2011, 0.2738, 0.3097, 0.4966, 0.6915, 0.6986, 0.7834, 1.0000],
        [0.1588, 0.3230, 0.4188, 0.5294, 0.7119, 0.7815, 0.9521, 1.0000],
        [0.1302, 0.2419, 0.4769, 0.5519, 0.5601, 0.8214, 0.9485, 1.0000],
        [0.0198, 0.1684, 0.3970, 0.4333, 0.5470, 0.7308, 0.9200, 1.0000]])
tensor([[0.3860, 0.3331, 0.7846, 0.3333]])
tensor([[3],
        [2],
        [5],
        [2]])
```
#### softmax和logsoftmax
```python
import torch
import torch.nn.functional as F
logits = torch.rand(2,2)
pred = F.softmax(logits, dim=-1)
pred1 = F.log_softmax(logits, dim=-1)
print(logits)
print(pred)
print(pred.log())
print(pred1)
```
```plaintext
tensor([[0.8926, 0.8885],
        [0.7748, 0.5256]])
tensor([[0.5010, 0.4990],
        [0.5620, 0.4380]])
tensor([[-0.6911, -0.6952],
        [-0.5763, -0.8255]])
tensor([[-0.6911, -0.6952],
        [-0.5763, -0.8255]])
```
#### 手动实现softmax和logsoftmax
**注意sum之后需要unsqeeze(-1)**
```python
soft = logits.exp()/(logits.exp().sum(dim=1)).unsqueeze(-1)
logsoft = soft.log()
print(soft)
print(logsoft)
```
#### 观察模型参数第1种
```python
print("=============更新之前===========")
        for name, parms in net.named_parameters():	
                print('-->name:', name)
                print('-->para:', parms)
                print('-->grad_requirs:',parms.requires_grad)
                print('-->grad_value:',parms.grad)
                print("===")
print("=============更新之后===========")
        for name, parms in net.named_parameters():	
            print('-->name:', name)
            print('-->para:', parms)
            print('-->grad_requirs:',parms.requires_grad)
            print('-->grad_value:',parms.grad)
            print("===")
        print(optimizer)
```
#### 观察模型参数第2种
```python
print(net.state_dict())
```