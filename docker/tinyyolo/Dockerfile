FROM darknet
RUN apt-get update && apt-get install -y --no-install-recommends \
        wget
        
RUN  apt-get clean && \
        rm -rf /var/lib/apt/lists/*

RUN cd darknet-nnpack && wget https://pjreddie.com/media/files/tiny-yolo-voc.weights 
EXPOSE 22666
CMD cd darknet-nnpack && ./darknet detector daemon cfg/voc.data cfg/tiny-yolo-voc.cfg tiny-yolo-voc.weights