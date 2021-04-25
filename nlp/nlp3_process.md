# 数据处理

### unicode转ascii

```.python
import unicodedata

t = unicodedata.normalize('NFD', s)
```

### pytorch数据集

```.python
from torch.utils.data import Dataset

class MyDataset(Dataset):

    def __init__(self):
        pass

    def __len__(self):
        pass

    def __getitem__(self, index):
        pass 
```

