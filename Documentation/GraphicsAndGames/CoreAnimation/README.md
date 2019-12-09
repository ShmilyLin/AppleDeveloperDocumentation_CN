# Core Animation

渲染，合成和动画化视觉元素。

## 概述

`Core Animation`可提供高帧率和流畅的动画，而不会给CPU造成负担，也不会降低App的运行速度。绘制动画的每一帧所需的大部分工作都已经帮你完成。你可以配置动画参数（例如起点和终点），然后由`Core Animation`完成其余的工作，将大部分工作移交给专用图形硬件，以加快渲染速度。有关更多详细信息，请参见[Core Animation编程指南]()。

## 主题

### 图层基础

* [class CALayer](./LayerBasics/CALayer/)

    一个对象，该对象管理基于图像的内容，并允许你对该内容执行动画。

protocol CALayerDelegate
Methods your app can implement to respond to layer-related events.

class CAConstraint
A representation of a single layout constraint between two layers.

protocol CALayoutManager
Methods that allow an object to manage the layout of a layer and its sublayers.

class CAConstraintLayoutManager
An object that provides a constraint-based layout manager.

protocol CAAction
An interface that allows objects to respond to actions triggered by a 
CALayer
 change.