FROM resin/rpi-raspbian
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        pkg-config \
        python \
        python-setuptools \
        python-dev \
        git \
        clang
        
RUN  apt-get clean && \
        rm -rf /var/lib/apt/lists/*

RUN curl -O https://bootstrap.pypa.io/3.2/get-pip.py && \
    python get-pip.py && \
        rm get-pip.py && pip install --upgrade pip

RUN pip install --upgrade git+https://github.com/Maratyszcza/PeachPy
RUN pip install --upgrade git+https://github.com/Maratyszcza/confu

RUN git clone https://github.com/ninja-build/ninja.git
RUN cd ninja && git checkout release && ./configure.py --bootstrap
RUN git clone https://github.com/thomaspark-pkj/NNPACK-darknet.git
RUN cd NNPACK-darknet && confu setup && python ./configure.py --backend auto && /ninja/ninja && cp -a lib/* /usr/lib/ && cp include/nnpack.h /usr/include/ && cp deps/pthreadpool/include/pthreadpool.h /usr/include/
RUN git clone https://github.com/coreus/darknet-nnpack.git && cd darknet-nnpack && make
