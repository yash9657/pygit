A Git client written in python to create a repo, commit, and push itself to GitHub and it also implements status, diff, cat-file, ls-files, and hash-object.

$ python3 misc/pygit.py init pygit
initialized empty repository: pygit

$ cd pygit

# ... write and test pygit.py using a test repo ...

$ python3 pygit.py status
new files:
    pygit.py

$ python3 pygit.py add pygit.py

$ python3 pygit.py commit -m "First working version of pygit"
committed to master: 00d56c2a774147c35eeb7b205c0595cf436bf2fe

$ python3 pygit.py cat-file commit 00d5
tree 7758205fe7dfc6638bd5b098f6b653b2edd0657b
author Yash Bhalgat <yashbhalgat9657@gmail.com> 1493169321 -0500
committer Yash Bhalgat <yashbhalgat9657@gmail.com> 1493169321 -0500

First working version of pygit

# ... make some changes ...

$ python3 pygit.py status
changed files:
    pygit.py

$ python3 pygit.py diff
--- pygit.py (index)
+++ pygit.py (working copy)
@@ -100,8 +100,9 @@
     """
     obj_type, data = read_object(sha1_prefix)
     if mode in ['commit', 'tree', 'blob']:
-        assert obj_type == mode, 'expected object type {}, got {}'.format(
-                mode, obj_type)
+        if obj_type != mode:
+            raise ValueError('expected object type {}, got {}'.format(
+                    mode, obj_type))
         sys.stdout.buffer.write(data)
     elif mode == '-s':
         print(len(data))

$ python3 pygit.py add pygit.py

$ python3 pygit.py commit -m "Graceful error exit for cat-file with bad
    object type"
committed to master: 4117234220d4e9927e1a626b85e33041989252b5

$ python3 pygit.py push https://github.com/yash9657/pygit.git
updating remote master from no commits to
    4117234220d4e9927e1a626b85e33041989252b5 (6 objects)
