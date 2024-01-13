---
theme: zju-academic
marp: true
paginate: "true"
Math: latex
---
<!-- _class: lead -->

# 使用 Marp 为实验室制作演示幻灯片


**作者：李明**
XX 实验室硕士二年级
YYYY/MM/DD

---

<!-- _header: 目录 -->

1. 引言
1. 代码块
1. 数学公式
1. 图片

---

<!-- _header: 引言 -->

- Marp 是一款用于使用**Markdown**创建**幻灯片**的软件。
  - 它支持基本的 Markdown 语法。
- 在 Markdown 中只需插入 `---` 分隔线，就能轻松跳转到下一页。$^1$

> 1: Marp 遵循 CommonMark 的 Markdown 规范进行开发，因此它没有提供不在 CommonMark 中的「脚注」语法（使用 `[^1]`）。因此，我参考了 https://github.com/marp-team/marp/discussions/150#discussioncomment-1302384 来实现类似脚注的效果。

---

<!-- _header: 代码块 -->

```python
import torch
print(torch.cuda.is_available())
```

可以这样编写代码块。

```python
from transformers import AutoModelForMaskedLM, AutoTokenizer
model = AutoModelForMaskedLM.from_pretrained("cl-tohoku/bert-base-japanese-whole-word-masking")
tokenizer = AutoTokenizer.from_pretrained("cl-tohoku/bert-base-japanese-whole-word-masking")

inputs = tokenizer.encode_plus("我非常[MASK]。", return_tensors='pt')
outputs = model(**inputs)
tokenizer.convert_ids_to_tokens(outputs.logits[0][1:-1].argmax(axis=-1))
```

代码块的宽度会自动调整（参见文档中的 [Auto-scaling](https://github.com/marp-team/marp-core#auto-scaling-features)）。

---

<!-- _header: 数学公式 -->

$$ I_{xx}=\int\int_Ry^2f(x,y)\cdot{}dydx $$

$$
f(x) = \int_{-\infty}^\infty
    \hat f(\xi)\,e^{2 \pi i \xi x}
    \,d\xi
$$

可以这样编写数学公式。当然，也可以使用行内的 $\LaTeX$ 公式。
顺便一提，也可以使用表情符号:smile: