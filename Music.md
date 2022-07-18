# `class` Music

**Music 是一个数据类 (DataObject)，支持使用 `.` 读取数据，并且支持 Music 可用的 Api**

## 类实例变量

在外部使用 `.` 即可读取数据

```python
class Music(_Music):

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
        self.name = [music_data['name'], music_data["alia"][0] if music_data["alia"] != [] else ""]
        self.name_str = self.name[0] + self.name[1]
        # 作者列表 [作者, 作者, ...]
        self.artist = [{"id": artist["id"], "name": artist["name"]} for artist in music_data['ar']]
        self.artist_str = "/".join([author["name"] for author in self.artist])
        # 专辑列表
        self.album_data = music_data["al"]
        self.album_str = self.album_data["name"]
        # 所有音质
        self.quality = {
            "h": music_data["h"],
            "m": music_data["m"],
            "l": music_data["l"],
            "sq": music_data["sq"],
            "hr": music_data["hr"],
        }
        # mv id
        self.mv_id = music_data["mv"]
        self.publish_time = music_data["publishTime"]
        # 推荐理由
        self.reason = music_data["reason"] if "reason" in music_data else None
```

## 类实例方法

### Music.similar

**`async def similar(self) -> dict[str, Any]:`**

获取该对象的相似， 获取失败时返回 Api 错误信息 (json)

### Music.similar_playlist

**`async def similar_playlist(self, page: int = 0, limit: int = 50) -> Union[Generator["PlayList", None, None], dict[str, Any]]:`**

获取该对象的相似歌单， 获取失败时返回 Api 错误信息 (json)

> `page`: 页
>
> `limit`: 一页的数据量

### Music.similar_user

**`async def similar_user(self, page: int = 0, limit: int = 50 ) -> Union[Generator["User", None, None], dict[str, Any]]:`**

获取最近听了这 music 对象的用户， 获取失败时返回 Api 错误信息 (json)

> `page`: 页
>
> `limit`: 一页的数据量

### Music.like

**`async def like(self, like: bool = True) -> dict[str, Any]:`**

红心该 music 对象与取消红心

> `like`: 喜欢 / 取消喜欢

### Music.lyric

**`async def lyric(self) -> dict[str, Any]:`**

该 music 对象的歌词

### Music.play

**`async def play(self, quality = None, download_path: str = None) -> Union[str, dict[str, Any]]:`**

获取播放该 music 对象指定的歌曲文件， 下载成功后返回文件路径

> `quality`: 音质
>
> `download_path`: 下载路径

### Music.download

**`async def download(self, quality = None, download_path: str = None) -> Union[str, dict[str, Any]]:`**

获取下载该 music 对象指定的歌曲文件 (客户端下点击下载时候的 Api)

错误码 -105需要会员， 下载成功后返回文件路径

> `quality`: 音质
>
> `download_path`: 下载路径

### Music.mv

**`async def mv(self) -> Union["Mv", dict[str, Any]]:`**

获取该对像 mv 实例化 mv 对像并返回 mv 对像， 获取失败时返回 Api 错误信息 (json)

### Music._play_url

**`async def _play_url(self, quality = None) -> dict[str, Any]:`**

获取播放该 music 对象指定的歌曲文件 url

> `quality`: 音质

### Music._download_url

**`async def _download_url(self, quality = None) -> dict[str, Any]:`**

获取该 music 对象指定的歌曲 url, 错误码 -105 需要会员

> `quality`: 音质