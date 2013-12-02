# IRuby

This is a Ruby kernel for IPython.

![IRuby Notebook](screenshot.png)

### Usage

Install the rubygem using `gem install iruby` and then run `iruby notebook` or `iruby`.

Take a look at the [Example Notebook](http://nbviewer.ipython.org/urls/raw.github.com/minad/iruby/master/IRuby-Example.ipynb).

### Tips

#### If you get lots of "Unsigned Message"

```
Traceback (most recent call last):
  File "/home/runixo/proj/ipython/IPython/frontend/html/notebook/base/zmqhandlers.py", line 68, in _on_zmq_reply
    msg = self._reserialize_reply(msg_list)
  File "/home/runixo/proj/ipython/IPython/frontend/html/notebook/base/zmqhandlers.py", line 51, in _reserialize_reply
    msg = self.session.unserialize(msg_list)
  File "/home/runixo/proj/ipython/IPython/kernel/zmq/session.py", line 768, in unserialize
    raise ValueError("Unsigned Message")
```

And you know what you're doing, run `ipython` with an empty `Session.key`

```bash
 bundle exec iruby notebook --profile=iruby-overol  --Session.key=''        
```

#### iruby inside your project

If your iruby usage will interact exclusively with a specific project, you can add the `iruby` gem to that project `Gemfile` and set the profile to load your setup/configuration file on kernel startup.

```python
c.KernelManager.kernel_cmd = ['bundle', 'exec', 'iruby_kernel', '{connection_file}', '/path/to/boot.rb','/optional/cwd/']
```

### Authors

See the [CONTRIBUTORS](CONTRIBUTORS) file.

### License

See the [LICENSE](LICENSE) file.
