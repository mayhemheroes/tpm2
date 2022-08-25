# Copyright 2017 The Chromium Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.
#
# Defines a docker image that can build fuzzers.
#
FROM gcr.io/oss-fuzz-base/base-builder
RUN apt-get update && apt-get install -y make libssl-dev binutils libgcc-9-dev
COPY . tpm2
RUN rm -rf tpm2/mayhem
WORKDIR tpm2
RUN cp /src/tpm2/fuzz/build.sh /src/

ENV FUZZING_LANGUAGE=c++
RUN compile
RUN chmod +x /out/tpm2_execute_command_fuzzer
