# **`class`** CommentObject

CommentObject 规定了数据类 (DataObject/DataListObject)评论操作的几种 Api，所有支持评论操作的对象都可以使用这些 Api

## 类实例方法

### CommentObject.comments

**`sync def comments(self, hot: bool = True, page: int = 0, limit: int = 20,before_time: int = 0) -> Union[tuple[int, Generator[CommentItemObject, None, None]], dict[str, Any]]:`**

该对象的评论，返回一个元组 (tuple) 包含所有的评论数，一个 [CommentItemObject 对像](/pycloudmusic/CommentObject?id=class-commentitemobject)生成器(Generator)， 失败时返回 Api 错误信息 (json)

> `hot`: 热评 / 最新评论
>
> `page`: 页
>
> `limit`: 一页的数据量
>
> `before_time`: 分页参数, 取上一页最后一项的 time 获取下一页数据(获取超过5000条评论的时候需要用到)

### CommentObject.comment_sned

**`async def comment_sned(self, content: str) -> dict[str, Any]:`**

发送评论

> `content`: 评论内容

# `class` CommentItemObject

CommentItemObject 规定了评论操作的几种 Api

## 类实例方法

### CommentItemObject.floors

**`async def floors(self, page: int = 0,limit: int = 20) -> Union[tuple[int, Generator[CommentItemObject, None, None]], dict[str, Any]]:`**

楼层评论，返回一个元组 (tuple) 包含所有的评论数，一个 [CommentItemObject 对像](/pycloudmusic/CommentObject?id=class-commentitemobject)生成器(Generator)， 失败时返回 Api 错误信息 (json)

> `page`: 页
>
> `limit`: 一页的数据量

### CommentItemObject.like

**`async def like(self, in_: bool) -> dict[str, Any]:`**

评论点赞

> `in_`: 点赞 / 取消点赞

### CommentItemObject.reply

**`async def reply(self, content: str) -> dict[str, Any]:`**

回复评论

> `content`: 评论内容

### CommentItemObject.delete

**`async def delete(self) -> dict[str, Any]:`**

删除评论