ARG UBUNTU_VERSION
FROM ubuntu:${UBUNTU_VERSION}

ARG CLANG_FORMAT_VERSION

# RUN apt-get update \
# 	&& apt-get install --no-install-recommends -y \
# 	clang-format-${CLANG_FORMAT_VERSION} \
# 	# Clean cache
# 	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false \
# 	&& apt-get clean -y && rm -rf /var/lib/apt/lists/* \
# 	&& mv /usr/bin/clang-format-${CLANG_FORMAT_VERSION} /usr/bin/clang-format

RUN apt-get update
RUN apt-get install --no-install-recommends --reinstall -y ca-certificates
RUN apt-get install --no-install-recommends -y apt-utils lsb-release wget software-properties-common gnupg 
RUN wget https://apt.llvm.org/llvm.sh 
RUN chmod u+x llvm.sh 
RUN ./llvm.sh all
RUN clang-format-${CLANG_FORMAT_VERSION} --version
RUN mv /usr/bin/clang-format-${CLANG_FORMAT_VERSION} /usr/bin/clang-format

WORKDIR /

COPY check.sh .

ENTRYPOINT ["/usr/bin/clang-format"]
