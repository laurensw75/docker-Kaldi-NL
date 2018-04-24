# docker-Kaldi-NL

This Docker is largely based on [earlier work](https://github.com/jcsilva/docker-kaldi-gstreamer-server).

The environment that is built with this dockerfile allows for running a Dutch ASR server, 
as well as doing offline recognition in a similar manner as what would be possible with my [Kaldi-NL setup](https://github.com/opensource-spraakherkenning-nl/Kaldi_NL).
During the installation process, the (precompiled) Dutch ASR models are downloaded and extracted so you can start using it straight away.

The pre-built docker can be retrieved using:

`docker pull laurensw/kaldi_nl_server`

Or you can build the Docker using:

`docker build -t kaldi_nl:1.0 https://github.com/laurensw75/docker-Kaldi-NL`

Once the environment is ready, you can run it with:

`docker run -it -p 8888:80 kaldi_nl:1.0`

(or with `docker run -it -p 8888:80 laurensw/kaldi_nl_server` if you took the pre-built image)

This ensures that port 80 that is used within the Docker as the server port, is mapped to 8888 for use outside the Docker.
Once inside the Docker, you can simply type start.sh to start the ASR server, and stop.sh to stop it.
The server can be tested using my example [Java application](https://github.com/laurensw75/SpeechAPIDemo), which should then be started with localhost:8888 as parameters.

Alternatively, you can go into the Kaldi_NL subdirectory and do offline decoding. 
For example using:

`decode.sh /opt/Audio results`

Which works in a similar manner to the [Kaldi-NL setup](https://github.com/opensource-spraakherkenning-nl/Kaldi_NL).

