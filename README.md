# get_storage
A fast, extra light and synchronous key-value in memory, which backs up data to disk at each operation.
It is written entirely in Dart and easily integrates with Get framework of Flutter.

Supports Android, iOS, Web, Mac, Linux, and fuchsia and Windows**. 
Can store String, int, double, Map and List

Add to your pubspec:
```
dependencies:
  get_storage:
```

Initialize storage driver with await:
```dart
main() async {
  await GetStorage.init();
  runApp(App());
}
```
use GetStorage through an instance or use directly `GetStorage().read('key')`
```dart
final box = GetStorage();
```
To write information you must use `write` :
```dart
box.write('quote', 'GetX is the best');
```

To read values you use `read`:
```dart
print(box.read('quote'));
// out: GetX is the best

```
To remove a key, you can use `remove`:

```dart
box.remove('quote');
```

To listen changes you can use `listen`:
```dart
box.listen((){
  print('box changed');
});
```
If you subscribe to events, be sure to dispose them when using:
```dart
box.removeListen(listen);
```
To listen changes on key you can use `listenKey`:
```dart
box.listenKey('key', (value){
  print('new key is $value');
});

To erase your container:
```dart
box.erase();
```

If you want to create different containers, simply give it a name. You can listen to specific containers, and also delete them.

```dart
GetStorage g = GetStorage('MyStorage');
```

To initialize specific container:
```dart
await GetStorage.init('MyStorage');
```

**GetStorage is not fast, it is absurdly fast for being memory-based. All of his operations are instantaneous. A backup of each operation is placed in a Container on the disk. Each container has its own file.**

![](delete.png)
![](write.png)
![](read.png)

## What GetStorage is:
Persistent key/value storage for Android, iOS, Web, Linux, Mac and Fuchsia (soon to be Windows) that combines fast memory access with persistent storage.
## What GetStorage is NOT:
A database. Get is super compact to offer you a solution ultra-light, high-speed read/write storage to work synchronously. If you want to store data persistently on disk with immediate memory access, use it, if you want a database, with indexing and specific disk storage tools, there are incredible solutions that are already available, like Hive and Sqflite/Moor.

Each container has an output for `.listenable`, so you can use this lib even as a modest persistent state manager using ValueListenableBuilder


