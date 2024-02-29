# indexedDB的特性是什么?使用场景是什么?
## IndexedDB的特性

IndexedDB 是一种用于在浏览器中存储大量结构化数据（包括文件/二进制大型对象（blobs））的 API。 该 API 使用索引来启用对这些数据的高性能搜索。 虽然 Web Storage 在存储较少量的数据很有用，但对于存储更大量的结构化数据来说力不从心。 而 IndexedDB 提供了这种场景的解决方案。

IndexedDB 具有以下特性：

**1. 存储容量大**

IndexedDB 的存储容量理论上没有限制，实际应用中受限于浏览器对数据库大小的限制，一般为 50MB-250MB 之间。

**2. 性能高**

IndexedDB 使用索引来组织数据，可以快速检索数据。

**3. 事务支持**

IndexedDB 支持事务操作，可以确保数据的完整性和一致性。

**4. 异步操作**

IndexedDB 的所有操作都是异步的，不会阻塞主线程。

**5. 跨浏览器支持**

IndexedDB 得到了所有主流浏览器的支持。

**6. 其他特性**

IndexedDB 还具有以下特性：

* 支持多并发访问
* 支持数据加密
* 支持数据备份和恢复

# IndexedDB可以用在哪些场景？
## IndexedDB可以用在哪些场景？

IndexedDB 是一种用于在客户端存储大量结构化数据（包括文件/二进制大型对象（blobs））的低级API。 该API使用索引来启用对这些数据的高性能搜索。 虽然Web Storage在存储较少量的数据很有用，但对于存储更大量的结构化数据来说力不从心。 而IndexedDB提供了这种场景的解决方案。

IndexedDB可以用在以下场景：

**1. 离线应用**

IndexedDB可以用于存储离线应用所需的数据，即使在没有网络连接的情况下也能正常工作。 例如，一个离线音乐应用可以使用IndexedDB存储音乐文件和播放列表。

**2. 缓存应用**

IndexedDB可以用于缓存数据，减少服务器负载并提高用户体验。 例如，一个新闻应用可以使用IndexedDB缓存文章内容，以便用户可以快速阅读文章。

**3. 大型数据存储**

IndexedDB可以用于存储大型结构化数据，例如音视频文件、图片等。 例如，一个照片分享应用可以使用IndexedDB存储用户上传的照片。

**4. 实时应用**

IndexedDB可以用于存储实时数据，例如聊天记录、游戏数据等。 例如，一个聊天应用可以使用IndexedDB存储聊天记录，以便用户可以查看历史记录。

**5. 其他场景**

IndexedDB还可以用于其他场景，例如：

* 存储用户设置
* 存储表单数据
* 存储游戏存档


# indexedDB基本操作
## IndexedDB的基本操作

IndexedDB的基本操作包括：

* **打开数据库**：使用indexedDB.open()方法打开一个数据库。
* **创建对象存储空间**：使用createObjectStore()方法创建一个对象存储空间。
* **新增数据**：使用add()方法新增一条数据。
* **读取数据**：使用get()方法读取一条数据。
* **更新数据**：使用put()方法更新一条数据。
* **删除数据**：使用delete()方法删除一条数据。
* **遍历数据**：使用openCursor()方法遍历所有数据。
* **关闭数据库**：使用close()方法关闭数据库。

以下是上述操作的示例代码：

```javascript
// 打开数据库
const db = new indexedDB.open('myDB', 1);

// 创建对象存储空间
db.onupgradeneeded = function(event) {
  const objectStore = event.target.result.createObjectStore('myStore', { keyPath: 'id' });
};

// 新增数据
const request = objectStore.add({
  id: 1,
  name: 'John Doe',
  age: 30,
});

// 读取数据
request.onsuccess = function() {
  const data = request.result;
  console.log(data);
};

// 更新数据
const request = objectStore.put({
  id: 1,
  name: 'Jane Doe',
  age: 31,
});

// 删除数据
const request = objectStore.delete(1);

// 遍历数据
const request = objectStore.openCursor();
const results = [];
request.onsuccess = function() {
  const cursor = request.result;
  if (cursor) {
    results.push(cursor.value);
    cursor.continue();
  } else {
    console.log(results);
  }
};

// 关闭数据库
db.close();
```