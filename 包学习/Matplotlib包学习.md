# Matplotlib包学习

Matplotlib是python当中用于绘制二维图像的一个包，且支持通过numpy数组来快速生成图像。

## 1.生成一条曲线

实际上在Matplotlib当中想要生成一条曲线非常的容易，只要导入这个包以后通过`plt.plot(x,y)`就可以根据提供的x,y数组，以一一对应的关系快速生成一条穿越曲线，也就是说生成的图像是会完美地穿越这些坐标点地，但要注意这并不是拟合。

同时.plot()方法还支持其他一些属性来让我们将整个图像变得更加漂亮美观。

```
plt.plot(x,y,linestyle = "*/^/._/--/-", color = "", linewidth = "")
xlim,ylim
xticks(np.linespace(-4,4,9,endpoint = True/False)) # 其中endpoint表示是否包含两侧
plt.show()
savefig("xx.png",dpi =220)
```

