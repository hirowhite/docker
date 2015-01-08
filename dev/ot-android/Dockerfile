FROM monetas/base-ot-dev

MAINTAINER Darragh Grealish "darragh@monetas.net"

RUN apt-get install -y --no-install-recommends p7zip-full curl automake autoconf libtool && apt-get autoremove

# Install android ndk
ENV ANDROID_NDK_VERSION r10c
#http://dl.google.com/android/ndk/android-ndk-r10c-linux-x86_64.bin
RUN curl -L http://dl.google.com/android/ndk/android-ndk-$ANDROID_NDK_VERSION-linux-x86_64.bin \
    -o /tmp/android-ndk-$ANDROID_NDK_VERSION-linux-x86_64.bin && \
    7z x /tmp/android-ndk-$ANDROID_NDK_VERSION-linux-x86_64.bin -o/usr/local && \
    ln -sf /usr/local/android-ndk-$ANDROID_NDK_VERSION /usr/local/android-ndk && \
    rm -rf /tmp/android-ndk-$ANDROID_NDK_VERSION-linux-x86_64.bin

ENV ANDROID_NDK /usr/local/android-ndk

CMD ["bash"]

