# exec_command_app


```
docker build  -f ./windows/Dockerfile -t pyinstaller-windows .
docker build  -f ./centos7/Dockerfile -t pyinstaller-centos7 .
docker run --rm -it pyinstaller-windows bash
docker run --rm -v $(pwd)/src:/src pyinstaller-windows python -m nuitka --standalone main.py
```

**linux**

```
docker build  -f ./linux/Dockerfile -t pyinstaller-linux .
docker run --rm -it pyinstaller-linux bash

docker run --rm -v $(pwd)/src:/src -v $(pwd)/linux:/linux \
    pyinstaller-linux pyinstaller main.py \
    --onedir --onefile --clean \
    --distpath /linux/dist \
    --workpath /linux/build \
    --specpath /linux 
```

**centos7用**

```
docker build  -f ./centos7/Dockerfile -t pyinstaller-centos7 .
docker run --rm -it pyinstaller-centos7 bash

docker run --rm -v $(pwd)/src:/src -v $(pwd)/centos7:/centos7 \
    pyinstaller-centos7 pyinstaller main.py \
    --onedir --onefile --clean \
    --distpath /centos7/dist \
    --workpath /centos7/build \
    --specpath /centos7 
```