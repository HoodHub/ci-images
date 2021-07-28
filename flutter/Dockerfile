FROM semaphoreci/android:29-flutter

RUN flutter upgrade
RUN cd /opt/flutter && git checkout 2.2.2
RUN flutter doctor

# build some things to prepopulate the gradle cache
RUN cd /root/ && flutter create -t app foo
WORKDIR /root/foo
RUN flutter build appbundle
RUN sed -i -e "s/com.android.tools.build:gradle:4.1.0/com.android.tools.build:gradle:4.1.2/" android/build.gradle
RUN flutter build appbundle


