# **`class`** CommentObject

CommentObject 规定了评论操作的几种 Api，所有支持评论操作的对象都可以使用这些 Api

## 类实例方法

### CommentObject.comment

**`sync def comment(self, hot: bool = True, page: int = 0, limit: int = 20,before_time: int = 0) -> dict[str, Any]:`**

该对象的评论

> `hot`: 热评 / 最新评论
>
> `page`: 页
>
> `limit`: 一页的数据量
>
> `before_time`: 分页参数, 取上一页最后一项的 time 获取下一页数据(获取超过5000条评论的时候需要用到)

### CommentObject.comment_floor

**`async def comment_floor(self, comment_id: Union[str, int], page: int = 0,limit: int = 20) -> dict[str, Any]:`**

楼层评论

> `comment_id`: 评论 id，即从 `CommentObject.comment` 获取到的 `commentId`
>
> `page`: 页
>
> `limit`: 一页的数据量

### CommentObject.comment_like

**`async def comment_like(self, comment_id: Union[str, int], in_: bool) -> dict[str, Any]:`**

评论点赞

> `comment_id`: 评论 id，即从 `CommentObject.comment` 获取到的 `commentId`
>
> `in_`: 点赞 / 取消点赞

### CommentObject.comment_add

**`async def comment_add(self, content: str) -> dict[str, Any]:`**

发送评论

> `content`: 评论内容

### CommentObject.comment_delete

**`async def comment_delete(self, comment_id: Union[str, int]) -> dict[str, Any]:`**

删除评论

> `comment_id`: 评论 id，即从 `CommentObject.comment` 获取到的 `commentId`

### CommentObject.comment_reply

**`async def comment_reply(self, comment_id: Union[str, int], content: str) -> dict[str, Any]:`**

回复评论

> `comment_id`: 评论 id，即从 `CommentObject.comment` 获取到的 `commentId`
>
> `content`: 评论内容