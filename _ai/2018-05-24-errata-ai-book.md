---
layout: post
title:  "Fundamentals of Artificial Intelligence ── Errata"
date:   2018-05-24
excerpt: "人工智能基础（高中版）勘误表"
image: "/images/textbook.jpg"
---
<div class="box">
    <p>
    如果您发现错误或者有改进建议，请发送邮件至 <a href="mailto:fundamental.ai@outlook.com">fundamental.ai@outlook.com</a>，多谢您的支持！
    </p>
</div>

<h3>错误列表</h3>
<div class="table-wrapper">
    <table>
        <thead>
            <tr>
                <th>条目</th>
                <th>修正</th>
                <th>位置</th>
                <th>类型</th>
                <th>汇报者</th>
                <th>日期</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Image Net</td>
                <td>ImageNet</td>
                <td>第9、52、53、54页</td>
                <td>专有名词</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>Alex Net</td>
                <td>AlexNet</td>
                <td>第9、62页</td>
                <td>专有名词</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>...的参数。最大化 $2\gamma$ 等价于...</td>
                <td>...的参数。当 $\gamma>0$ 时，最大化 $2\gamma$ 等价于...</td>
                <td>第34页</td>
                <td>技术错误</td>
                <td>姚超睿</td>
                <td>2018/05/07</td>
            </tr>
            <tr>
                <td>同时满足对每一个 $i$ ，$y^{(i)}\times \frac{a_1x_1^{(i)}+a_2x_2^{(i)}+b}{\sqrt{a_1^2+a_2^2}}\ge \gamma$</td>
                <td>同时满足对每一个 $i$ ，$y^{(i)}\times \frac{a_1x_1^{(i)}+a_2x_2^{(i)}+b}{\sqrt{a_1^2+a_2^2}}\ge \gamma>0$</td>
                <td>第34页</td>
                <td>技术错误</td>
                <td>姚超睿</td>
                <td>2018/05/07</td>
            </tr>
            <tr>
                <td>...神经元（nearon）...</td>
                <td>nearon -> neuron</td>
                <td>第59页</td>
                <td>专有名词</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>$[T]=\cdots$</td>
                <td>$[T]$ -> $\boldsymbol{T}$</td>
                <td>第130页</td>
                <td>格式</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>...均匀分布在区间 $[3,5]$ 中。</td>
                <td>$[3,5]$ -> $[2,5]$</td>
                <td>第130页</td>
                <td>排印错误</td>
                <td>周丹</td>
                <td>2018/05/07</td>
            </tr>
            <tr>
                <td>$d= w_1 t_1 + w_2 t_2 + \dots + w_V t_V$  (7-1)</td>
                <td>$\dots + w_V t_V$ -> $\dots + w_T t_T$ </td>
                <td>第130页</td>
                <td>排印错误</td>
                <td>黄攀</td>
                <td>2018/06/04</td>
            </tr>
            <tr>
                <td>$\tanh(x) = \frac{e^x - e^{-x}}{e^{-x} + e^{-x}}$</td>
                <td>$\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$</td>
                <td>第57页</td>
                <td>排印错误</td>
                <td>朋错</td>
                <td>2018/06/05</td>
            </tr>
            <tr>
                <td>Deep Mind</td>
                <td>DeepMind</td>
                <td>第154页</td>
                <td>专有名词</td>
                <td><i>《量子位》</i>编辑</td>
                <td>2018/06/07</td>
            </tr>
            <tr>
                <td>图6-8 第一次更新、第二次更新</td>
                <td>一 -> 二， 二 -> 一</td>
                <td>第110页</td>
                <td>排印错误</td>
                <td>倪枫</td>
                <td>2018/06/13</td>
            </tr>
            <tr>
                <td>...，其含义是相应频率的声音所对应的振幅。</td>
                <td>振幅 -> 功率</td>
                <td>第76页</td>
                <td>排印错误</td>
                <td>孙宁</td>
                <td>2018/09/23</td>
            </tr>
            <tr>
                <td>...，频谱幅度相差20倍。</td>
                <td>相差20倍 -> 相差20</td>
                <td>第76页</td>
                <td>排印错误</td>
                <td>孙宁</td>
                <td>2018/09/23</td>
            </tr>
        </tbody>
        <tfoot>
            <tr>
                <td colspan="2"></td>
                <td></td>
            </tr>
        </tfoot>
    </table>
</div>

<h3>改进列表</h3>
<div class="table-wrapper">
    <table>
        <thead>
            <tr>
                <th>条目</th>
                <th>改进建议</th>
                <th>位置</th>
                <th>类型</th>
                <th>提供者</th>
                <th>日期</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>...人工智能由此应运而生。</td>
                <td>由此->亦</td>
                <td>《致同学》第1页</td>
                <td>措词</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>...重要基石，为纪念...</td>
                <td>逗号->句号</td>
                <td>《致同学》第1页</td>
                <td>标点</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>在数学上，向量就是...</td>
                <td>删去“在数学上”</td>
                <td>第23页</td>
                <td>措词</td>
                <td>知乎网友</td>
                <td>2018/05/05</td>
            </tr>
            <tr>
                <td>...表示最小化后面表达式...</td>
                <td>删去“后面”</td>
                <td>第34页</td>
                <td>措词</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>我们的目的是......就可以求解了。</td>
                <td>整个部分属于扩展阅读</td>
                <td>第34─35页</td>
                <td>格式</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>三阶张量的高度也称为通道...</td>
                <td>高度->厚度</td>
                <td>第46页</td>
                <td>措词</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>矩阵可以看作是高度为 $1$ 的三阶张量，因此灰度图像只有一个通道。</td>
                <td>相较之下，灰度图像只有一个通道。</td>
                <td>第46页</td>
                <td>措词</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>...组成的时空体（<i>space-time volume</i>）。</td>
                <td>space-time volume 不要斜体</td>
                <td>第95页</td>
                <td>格式</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>...从光流到密集轨迹</td>
                <td>删去“密集”</td>
                <td>第97页</td>
                <td>叙述</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>如图 5-12 所示，......特征点 $P$ 的运动过程。</td>
                <td>整个部分属于扩展阅读</td>
                <td>第97页</td>
                <td>格式</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
            <tr>
                <td>弗吉尼亚鸢尾（<i>Virginia iris</i>）</td>
                <td><i>Virginia iris</i> -> <i>Iris virginica</i></td>
                <td>第110页</td>
                <td>一致性</td>
                <td>zz</td>
                <td>2018/04/28</td>
            </tr>
        </tbody>
        <tfoot>
            <tr>
                <td colspan="5"></td>
            </tr>
        </tfoot>
    </table>
</div>
