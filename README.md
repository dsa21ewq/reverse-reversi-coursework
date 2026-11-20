# 反黑白棋 AI · 课程作业

这是一个用于 8×8 反黑白棋（Reverse Reversi）的 Python 棋手。与普通黑白棋相反，终局时棋子较少的一方获胜。`AI.py` 是供课程裁判程序调用的入口，包含评估权重，不需要另行下载模型。

## 安装依赖

```sh
python -m pip install -r requirements.txt
```

## 调用示例

```python
import numpy as np
from AI import AI

board = np.zeros((8, 8), dtype=np.int8)
board[3, 3] = board[4, 4] = 1
board[3, 4] = board[4, 3] = -1

player = AI(chessboard_size=8, color=-1, time_out=5)
player.go(board)
move = player.candidate_list[-1] if player.candidate_list else None
print(move)
```

棋盘用 `0` 表示空位，`-1` 和 `1` 表示双方。落子坐标为从 0 开始的 `(行, 列)`；`candidate_list` 的最后一项是所选落子，列表为空表示无合法落子。首次初始化会触发 Numba 即时编译。
