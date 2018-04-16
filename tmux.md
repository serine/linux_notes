## Compiling tmux from source

- you'll need to install `libevent`. I decided to install from source it as well

```
git clone https://github.com/libevent/libevent
cd libevent
git checkout release-2.1.8-stable
./autogen.sh
./configure
make -j 8
```

You might need to install a couple of dependencies.

- `apt-get install pkg-config`
- `apt-get install libtool`

I usually try to compile (`make`) and/or run `./configure` and see what error I get. Usually it'll be something
along the lines that a particular header (`*.h`) file is missing. I don't have a good way of finding
which package has that header file. There are ways to do that with `apt-cache search` I think, but I just google
around for that header file name and almost always find required package.

So `apt-get` those package if you need to.

Of course I could have `apt-get` installed `libevent` instead of compiling from source, don't I ask me why I didn't. 

```
git clone https://github.com/tmux/tmux
cd tmux
git checkout 2.7
dir=/opt/libevent
./configure CFLAGS="-I$dir/include" LDFLAGS="-L$dir/.libs"
make -j 8
ln -s /opt/tmux/src/tmux /usr/local/bin/tmux
export LD_LIBRARY_PATH=/opt/libevent/.libs:$LD_LIBRARY_PATH
```
