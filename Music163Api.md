# `class` Music163Api

**Music163Api 类用于生成其他数据类 (DataObject/DataListObject)， 或者调用网易云独立的 Api**

## 类实例方法

### Music163Api.my

**`async def my(self) -> Union[My, dict[str, Any]]:`**

获取当前 cookie 用户信息并实例化 my 对像，cookie 无效返回 200

###  Music163Api.music

**`async def music(self, ids: Union[int, str, list[Union[str, int]]]) -> Union[Music, Generator[Music, None, None], dict[str, Any]]:`**

获取歌曲并实例化 [music 对像](/pycloudmusic/Music)， 实例化失败时返回 Api 错误信息 (json)

> `ids`: 歌曲 id，支持多 id (使用列表)，多 id 时将返回生成 music 对像的生成器 (Generator)

### Music163Api.user

获取用户并实例化 user 对像， 实例化失败时返回 Api 错误信息 (json)

**`async def user(self, id_: Union[int, str]) -> Union[User, dict[str, Any]]:`**

> `id_`: 用户 id

### Music163Api.playlist

获取歌单并实例化 [playlist 对像](/pycloudmusic/PlayList)， 实例化失败时返回 Api 错误信息 (json)

**`async def playlist(self, id_: Union[int, str]) -> Union[PlayList, dict[str, Any]]:`**

> `id_`: 歌单 id

### Music163Api.playlist

获取歌手并实例化 artist 对像， 实例化失败时返回 Api 错误信息 (json)

**`async def artist(self, id_: Union[int, str]) -> Union[Artist, dict[str, Any]]:`**

> `id_`: 歌手 id

### Music163Api.album

实例化专辑 album 对像， 实例化失败时返回 Api 错误信息 (json)

**`async def album(self, id_: Union[int, str]) -> Union[Album, dict[str, Any]]:`**

> `id_`: 专辑 id

### Music163Api.mv

获取 mv 并实例化 mv 对像， 实例化失败时返回 Api 错误信息 (json)

**`async def mv(self, id_: Union[int, str]) -> Union[Mv, dict[str, Any]]:`**

> `id_`: mv id

### Music163Api.dj

获取电台并实例化 dj 对像， 实例化失败时返回 Api 错误信息 (json)

**`async def dj(self, id_: Union[int, str]) -> Union[Dj, dict[str, Any]]:`**

> `id_`: 电台 id