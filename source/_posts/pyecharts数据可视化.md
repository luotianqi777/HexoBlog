---
title: pyecharts数据可视化
date: 2020-04-12 19:05:45
tags:
  - Python
---

## pyecharts 安装

`pip(pip3) install pyecharts`

## pyecharts 使用

### [官方教程](https://pyecharts.org/#/zh-cn/quickstart)

## pyecharts 渲染图片

pyecharts 提供了 `selenium`, `phantomjs` 和 `pyppeteer` 三种方式。

笔者只用过`phantomjs`，其他的可以参考[官方教程](https://pyecharts.org/#/zh-cn/render_images)

### 引入

```
from pyecharts.render import make_snapshot
```

### API

```
def make_snapshot(
    # 渲染引擎，可选 selenium 或者 phantomjs
    engine: Any,

    # 传入 HTML 文件路径
    file_name: str,

    # 输出图片路径
    output_name: str,

    # 延迟时间，避免图还没渲染完成就生成了图片，造成图片不完整
    delay: float = 2,

    # 像素比例，用于调节图片质量
    pixel_ratio: int = 2,

    # 渲染完图片是否删除原 HTML 文件
    is_remove_html: bool = False,

    # 浏览器类型，目前仅支持 Chrome, Safari，使用 snapshot-selenium 时有效
    browser: str = "Chrome",
    **kwargs,
)
```

### snapshot-phantomjs 安装

`snapshot-phantomjs` 是 `pyecharts` + `phantomjs` 渲染图片的扩展，需要先安装 `phantomjs`，安装方法可以参照[官网](hantomjs.org/download.html)

- 安装 `phantomjs`

  `sudo apt install phantomjs`

  > 或者下载 nodejs ，通过 npm 安装  
  > `npm install -g phantomjs-prebuilt`

- 安装 `snapshot-phantomjs`

  `pip(pip3) install snapshot-phantomjs`

* 使用

  > 此处采取官方示例

  ```
  from pyecharts import options as opts
  from pyecharts.charts import Bar
  from pyecharts.render import make_snapshot

  from snapshot_phantomjs import snapshot

  def bar_chart() -> Bar:
      c = (
          Bar()
          .add_xaxis(["衬衫", "毛衣", "领带", "裤子", "风衣", "高跟鞋", "袜子"])
          .add_yaxis("商家A", [114, 55, 27, 101, 125, 27, 105])
          .add_yaxis("商家B", [57, 134, 137, 129, 145, 60, 49])
          .reversal_axis()
          .set_series_opts(label_opts=opts.LabelOpts(position="right"))
          .set_global_opts(title_opts=opts.TitleOpts(title="Bar-测试渲染图片"))
      )
      return c

  make_snapshot(snapshot, bar_chart().render(), "bar0.png")
  ```

## pyecharts 处理 pandas 数据图像不显示

原因在于数据没有被 `list` 处理

- 错误示例

  ```
  line_e.add_xaxis(data.index)
  line_e.add_yaxis(series_name='error', y_axis=data['y_data'])
  ```

- 正确示例

  ```
  line_r.add_xaxis(data.index.tolist())
  line_r.add_yaxis(series_name='right', y_axis=data['y_data'].tolist())
  ```

  对数据进行`.list()`将其列表化就可以显示图像了
