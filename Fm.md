# `class` Fm

**私人 Fm (Fm) 是一个列表类 (ListObject)， 支持直接迭代对象将返回按 Fm 曲目生成的 [FmMusic 对象](/pycloudmusic/Fm?id=class-fmmusic)，并且支持私人 Fm 相关的 Api**

```python
"""迭代 Fm"""
from pycloudmusic import Music163Api
import asyncio
import time


async def mian():
    musicapi = Music163Api("你网易云的 Cookie")

    # 验证 cookie 有效性, 并返回 my 对象
    my = await musicapi.my()
    # 打印 Cookie 用户信息
    print(my)
    print("=" * 60)

    """
    每 3 秒, 获取一次 Fm 歌曲
    """

    # 返回 fm 对象
    fm = my.fm()
    while True:
        # 获取 Fm 歌曲
        await fm.read()
        # 打印 Fm 歌曲
        for music in fm:
            print(music.name, music.artist_str, music.id)
        
        # 休息 3 秒
        time.sleep(3)

asyncio.run(mian())
```

## 类实例方法

### Fm.read

**`async def read(self) -> dict[str, Any]:`**

获取 Fm 歌曲，成功后返回 Fm json 数据，并更新 Fm 对象迭代所使用的数据

### Fm.write

**`async def write(self, id_: Union[int, str]) -> dict[str, Any]:`**

将歌曲扔进垃圾桶 (优化推荐)

> `id_`: 歌曲 id

# `class` FmMusic

**FmMusic 是一个数据类 (DataObject)，支持使用 `.` 读取数据，并且支持 [Music 对象](/pycloudmusic/Music)可用的 Api， FmMusic 也支持[评论 (CommentObject)](/pycloudmusic/CommentObject)**

## 类实例变量

在外部使用 `.` 即可读取数据

```python
class FmMusic(_Music):

    def __init__(
        self, 
        headers: Optional[dict[str, str]], 
        music_data: dict[str, Any]
    ) -> None:
        super().__init__(headers, music_data)
        # 资源类型
        self.data_type = DATA_TYPE[0]
        # 歌曲id
        self.id = music_data['id']
        # 标题列表 [大标题, 副标题]
        self.name = music_data["name"]
        # 作者列表 [作者, 作者, ...]
        self.artist = [{"id": artist["id"], "name": artist["name"]} for artist in music_data['artists']]
        self.artist_str = "/".join([author["name"] for author in self.artist])
        # 专辑列表
        self.album_data = music_data["album"]
        self.album_str = music_data["album"]["name"]
        # mv id
        self.mv_id = music_data["mvid"]
        # 发表时间
        self.album_data["publishTime"]
```

## 类实例方法

**和 [Music 对象](/pycloudmusic/Music)相同**
