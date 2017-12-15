

```python
# 字节字符串
data = b'FOO:BAR, SPAM'
import re
re.split(b'[:,]', data)
```




    [b'FOO', b'BAR', b' SPAM']




```python
a = 'Hello World'
print(a[0])

print(a[1])

b = b'Hello World'

print(b[0])

print(b[1])
```

    H
    e
    72
    101



```python
# 字节字符串不会提供一个美观的字符串表示，也不能很好地打印出来，除非它们先被解码为一个文本字符串

s = b'Hello World'
print(s)

print(s.decode('ascii'))
```

    b'Hello World'
    Hello World



```python
# 字节字符串的格式化， 得先使用标准的文本字符串，然后将其编码为字节字符串
'{:10s} {:10d} {:10.2f}'.format('ACME', 100, 490.1).encode('ascii')
```




    b'ACME              100     490.10'




```python
# Write a UTF-8 filename

with open('jalape\xf1o.txt', 'w') as f:
    f.write('spicy')
    
import os
print(os.listdir('.'))
print(os.listdir(b'.'))

```

    ['.ssh', 'world war 2', 'chpater 2 plus.ipynb', '图片', '.bashrc-anaconda3.bak', '文档', '.lantern', 'fresint.m', 'filesOfGithub', '.gitconfig', '公共的', 'config', 'jxb', '.xsession-errors', 'verysync-linux-amd64-v0.15.2-rc22', 'hdy', '.sogouinput', 'README.md', 'books', '.java', 'readme.gitee.md', 'examples.desktop', '下载', '.bashrc', '.Xauthority', '.local', 'autoload', '.sudo_as_admin_successful', '.byteexec', 'squrar', 'chapter 1 data structure and algorithm.ipynb', '.gitignore', 'XX-Net', '.ipynb_checkpoints', '.gnome', '.TeXworks', '模板', '.mplayer', '.data', '.ci', '.presage', '.shutter', 'responses', 'test', '.profile', '.xinputrc', '.ew.json', '.gnome2', 'bin', '.remarkable', '.SpaceVim', '.compiz', 'anaconda3', '.jupyter', 'chapter 2 string and text.ipynb', '.pki', '.travis.yml', '.mozilla', '.python_history', '1', '.vim', 'H dm', '.macromedia', 'doc', '.viminfo', '.bash_logout', '视频', 'jalapeño.txt', '.gconf', 'tmp', '音乐', 'syntax', '.dbus', '桌面', '.gnome2_private', '.xsession-errors.old', '.ICEauthority', '.oracle_jre_usage', '.ipython', '.adobe', '.SpaceVim.d', '.dmrc', '.bash_history', 'filetype.vim', '.thumbnails', 'wiki', '.subversion', '.cache', '.config', '.~lock.responses#', 'snap', '.sync', '.thunderbird', 'docs']
    [b'.ssh', b'world war 2', b'chpater 2 plus.ipynb', b'\xe5\x9b\xbe\xe7\x89\x87', b'.bashrc-anaconda3.bak', b'\xe6\x96\x87\xe6\xa1\xa3', b'.lantern', b'fresint.m', b'filesOfGithub', b'.gitconfig', b'\xe5\x85\xac\xe5\x85\xb1\xe7\x9a\x84', b'config', b'jxb', b'.xsession-errors', b'verysync-linux-amd64-v0.15.2-rc22', b'hdy', b'.sogouinput', b'README.md', b'books', b'.java', b'readme.gitee.md', b'examples.desktop', b'\xe4\xb8\x8b\xe8\xbd\xbd', b'.bashrc', b'.Xauthority', b'.local', b'autoload', b'.sudo_as_admin_successful', b'.byteexec', b'squrar', b'chapter 1 data structure and algorithm.ipynb', b'.gitignore', b'XX-Net', b'.ipynb_checkpoints', b'.gnome', b'.TeXworks', b'\xe6\xa8\xa1\xe6\x9d\xbf', b'.mplayer', b'.data', b'.ci', b'.presage', b'.shutter', b'responses', b'test', b'.profile', b'.xinputrc', b'.ew.json', b'.gnome2', b'bin', b'.remarkable', b'.SpaceVim', b'.compiz', b'anaconda3', b'.jupyter', b'chapter 2 string and text.ipynb', b'.pki', b'.travis.yml', b'.mozilla', b'.python_history', b'1', b'.vim', b'H dm', b'.macromedia', b'doc', b'.viminfo', b'.bash_logout', b'\xe8\xa7\x86\xe9\xa2\x91', b'jalape\xc3\xb1o.txt', b'.gconf', b'tmp', b'\xe9\x9f\xb3\xe4\xb9\x90', b'syntax', b'.dbus', b'\xe6\xa1\x8c\xe9\x9d\xa2', b'.gnome2_private', b'.xsession-errors.old', b'.ICEauthority', b'.oracle_jre_usage', b'.ipython', b'.adobe', b'.SpaceVim.d', b'.dmrc', b'.bash_history', b'filetype.vim', b'.thumbnails', b'wiki', b'.subversion', b'.cache', b'.config', b'.~lock.responses#', b'snap', b'.sync', b'.thunderbird', b'docs']

