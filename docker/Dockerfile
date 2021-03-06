FROM colmap/colmap:latest

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates curl git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-4.5.11-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

ADD https://github.com/krallin/tini/releases/download/v0.16.1/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini

RUN git clone https://github.com/jacky841102/HD_map_updating 

RUN conda create --name detectron

RUN conda config --add channels pytorch  && \
    conda config --add channels anaconda && \
    conda config --add channels conda-forge && \
    conda config --add channels defaults && \
    conda install -n detectron -y \
        _libgcc_mutex=0.1=main \ 
        absl-py=0.9.0=py36_0 \
        blas=1.0=mkl \
        bzip2=1.0.8=h516909a_2 \
        c-ares=1.15.0=h516909a_1001 \
        ca-certificates=2020.1.1=0 \
        cairo=1.16.0=h18b612c_1001 \
        certifi=2019.11.28=py36_1 \
        cuda100=1.0=0 \
        cudatoolkit=10.1.243=h6bb024c_0 \
        cython=0.29.15=py36he6710b0_0 \
        ffmpeg=4.0=hcdf2ecd_0 \
        fontconfig=2.13.1=he4413a7_1000 \
        freeglut=3.0.0=hf484d3e_1005 \
        freetype=2.9.1=h8a8886c_1 \
        gettext=0.19.8.1=hc5be6a0_1002 \
        glib=2.58.3=py36hd3ed26a_1003 \
        graphite2=1.3.13=he1b5a44_1001 \
        h5py=2.8.0=py36h989c5e5_3 \
        harfbuzz=1.8.8=hffaf4a1_0 \
        hdf5=1.10.2=hc401514_3 \
        icu=58.2=hf484d3e_1000 \
        intel-openmp=2020.0=166 \
        jasper=2.0.14=h07fcdf6_1 \
        jpeg=9b=h024ee3a_2 \
        ld_impl_linux-64=2.33.1=h53a641e_7 \
        libedit=3.1.20181209=hc058e9b_0 \
        libffi=3.2.1=hd88cf55_4 \
        libgcc-ng=9.1.0=hdf63c60_0 \
        libgfortran=3.0.0=1 \
        libgfortran-ng=7.3.0=hdf63c60_0 \
        libglu=9.0.0=he1b5a44_1001 \
        libiconv=1.15=h516909a_1006 \
        libopencv=3.4.2=hb342d67_1 \
        libopus=1.3=h7b6447c_0 \
        libpng=1.6.37=hbc83047_0 \
        libprotobuf=3.11.4=h8b12597_0 \
        libstdcxx-ng=9.1.0=hdf63c60_0 \
        libtiff=4.1.0=h2733197_0 \
        libuuid=2.32.1=h14c3975_1000 \
        libvpx=1.7.0=h439df22_0 \
        libxcb=1.13=h14c3975_1002 \
        libxml2=2.9.9=hea5a465_1 \
        markdown=3.2.1=py_0 \
        mkl=2020.0=166 \
        mkl-service=2.3.0=py36he904b0f_0 \
        mkl_fft=1.0.15=py36ha843d7b_0 \
        mkl_random=1.1.0=py36hd6b4f25_0 \
        ncurses=6.2=he6710b0_0 \
        ninja=1.9.0=py36hfd86e86_0 \
        numpy=1.18.1=py36h4f9e942_0 \
        numpy-base=1.18.1=py36hde5b4d6_1 \
        olefile=0.46=py36_0 \
        opencv=3.4.2=py36h6fd60c2_1 \
        pcre=8.44=he1b5a44_0 \
        pillow=7.0.0=py36hb39fc2d_0 \
        pip=20.0.2=py36_1 \
        pixman=0.38.0=h516909a_1003 \
        pthread-stubs=0.4=h14c3975_1001 \
        py-opencv=3.4.2=py36hb342d67_1 \
        python=3.6.10=hcf32534_1 \
        python_abi=3.6=1_cp36m \
        pytorch=1.4.0=py3.6_cuda10.1.243_cudnn7.6.3_0 \
        pyyaml=5.1.2=py36h516909a_1 \
        readline=8.0=h7b6447c_0 \
        setuptools=46.1.3=py36_0 \
        six=1.14.0=py36_0 \
        sqlite=3.31.1=h7b6447c_0 \
        tk=8.6.8=hbc83047_0 \
        torchvision=0.5.0=py36_cu101 \
        werkzeug=1.0.1=pyh9f0ad1d_0 \
        wheel=0.34.2=py36_0 \
        xorg-fixesproto=5.0=h14c3975_1002 \
        xorg-inputproto=2.3.2=h14c3975_1002 \
        xorg-kbproto=1.0.7=h14c3975_1002 \
        xorg-libice=1.0.10=h516909a_0 \
        xorg-libsm=1.2.3=h84519dc_1000 \
        xorg-libx11=1.6.9=h516909a_0 \
        xorg-libxau=1.0.9=h14c3975_0 \
        xorg-libxdmcp=1.1.3=h516909a_0 \
        xorg-libxext=1.3.4=h516909a_0 \
        xorg-libxfixes=5.0.3=h516909a_1004 \
        xorg-libxi=1.7.10=h516909a_0 \
        xorg-libxrender=0.9.10=h516909a_1002 \
        xorg-renderproto=0.11.1=h14c3975_1002 \
        xorg-xextproto=7.3.0=h14c3975_1002 \
        xorg-xproto=7.0.31=h14c3975_1007 \
        xz=5.2.4=h14c3975_4 \
        yaml=0.2.2=h516909a_1 \
        zlib=1.2.11=h7b6447c_3 \
        zstd=1.3.7=h0b5b093_0

# RUN echo "source activate detectron" > ~/.bashrc
RUN . activate detectron && conda activate detectron && pip install \
    cachetools==4.0.0 \
    chardet==3.0.4 \
    cloudpickle==1.3.0 \
    cycler==0.10.0 \
    decorator==4.4.2 \
    https://dl.fbaipublicfiles.com/detectron2/wheels/cu101/torch1.4/detectron2-0.1.1%2Bcu101-cp36-cp36m-linux_x86_64.whl \
    future==0.18.2 \
    fvcore==0.1.dev200325 \
    google-auth==1.13.1 \
    google-auth-oauthlib==0.4.1 \
    grpcio==1.28.1 \
    idna==2.9 \
    imageio==2.8.0 \
    kiwisolver==1.2.0 \
    map-boxes==1.0.5 \
    matplotlib==3.2.1 \
    networkx==2.4 \
    oauthlib==3.1.0 \
    pandas==1.0.3 \
    portalocker==1.6.0 \
    protobuf==3.11.3 \
    pyasn1==0.4.8 \
    pyasn1-modules==0.2.8 \
    git+git://github.com/waspinator/pycococreator.git@0.2.0 \
    pycocotools==2.0 \
    pydot==1.4.1 \
    pyparsing==2.4.6 \
    python-dateutil==2.8.1 \
    pytz==2019.3 \
    pywavelets==1.1.1 \
    requests==2.23.0 \
    requests-oauthlib==1.3.0 \
    rsa==4.0 \
    scikit-image==0.16.2 \
    scipy==1.4.1 \
    tabulate==0.8.7 \
    tensorboard==2.2.0 \
    tensorboard-plugin-wit==1.6.0.post2 \
    termcolor==1.1.0 \
    tqdm==4.45.0 \
    urllib3==1.25.8 \
    yacs==0.1.6

RUN wget --load-cookies /tmp/cookies.txt \
    "https://docs.google.com/uc?export=download&confirm=$(wget \
    --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate \
    'https://docs.google.com/uc?export=download&id=1a6wScEXomvPb2lQzyG2WCsPuZLfLYPFa' -O- | \
    sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1a6wScEXomvPb2lQzyG2WCsPuZLfLYPFa" \
    -O /HD_map_updating/sign_detector/model_final.pth && rm -rf /tmp/cookies.txt

RUN echo "source activate detectron" > ~/.bashrc
ENTRYPOINT [ "/usr/bin/tini", "--" ]
CMD [ "/bin/bash"]