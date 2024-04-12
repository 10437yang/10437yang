from graphviz import Digraph
import matplotlib.pyplot as plt
import matplotlib.image as mpimg

# 创建一个Digraph对象
dot = Digraph()

# 定义节点
steps = ["组建专业团队", "制定服务方案", "按计划推动实施", "组织专家研讨", 
         "征求委托方意见", "完成项目执行", "提供跟踪服务", "开展效果评估"]

# 添加节点
for i, step in enumerate(steps, 1):
    dot.node(str(i), step)

# 定义节点之间的连接
for i in range(1, len(steps)):
    dot.edge(str(i), str(i + 1))

# 生成流程图文件
dot.render('process_graph', format='png', cleanup=True)

# 使用matplotlib来显示流程图图片
img = mpimg.imread('process_graph.png')
plt.figure(figsize=(10, 10))
plt.imshow(img)
plt.axis('off')  # 不显示坐标轴
plt.savefig('./process_graph.png')
