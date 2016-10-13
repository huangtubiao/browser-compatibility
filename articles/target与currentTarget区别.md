# event.target

指向触发事件的对象。当事件处理程序在冒泡阶段或者捕获阶段调用的时候，该目标对象与 event.currentTarget 不同。（通俗点解释就是，只有当绑定的事件处理程序与触发该事件处理程序都为同一个对象的时候，两者相同。）

# event.currentTarget

当事件遍历 DOM 时，识别事件的当前目标对象（Identifies the current target for the event, as the event traverses the DOM.）。 该属性总是指向被绑定事件句柄（event handler）的元素。而与之对比的event.target ，则是指向触发该事件的元素。

> target在事件流的目标阶段；currentTarget在事件流的捕获，目标及冒泡阶段。只有当事件流处在目标阶段的时候，两个的指向才是一样的， 而当处于捕获和冒泡阶段的时候，target指向被单击的对象而currentTarget指向当前事件活动的对象（一般为父级）。

# 浏览器兼容性

(1)、在 IE6准-8 中，事件模型与标准不同。使用非标的 element.attachEvent() 方法绑定时间监听器。在该模型中，事件对象有一个 srcElement 属性，等价于target 属性。

(2)、IE6-8中，事件模型与标准不一样，使用非标准的 element.attachEvent 来绑定事件监听器。该模型中，没有等价于 event.currentTarget 的接口，且 this 指向全局对象。一种模拟 event.currentTarget 功能的方法是：将监听器包在一个函数中，然后使用 Function.prototype.call 调用这个包装函数，并将元素对象作为第一个参数。这样，this 就是想要的值了。

# 冒泡和捕获
