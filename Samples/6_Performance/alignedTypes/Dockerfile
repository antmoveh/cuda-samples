FROM registry.cn-hangzhou.aliyuncs.com/bocloud/brpc:v1.8.0 as builder

# 编译alignedTypes
RUN mkdir -p /app
RUN git clone https://github.com/antmoveh/cuda-samples.git /app/build
RUN cd /app/build/Samples/6_Performance/alignedTypes && make && cp alignedTypes /tmp/alignedTypes

FROM ubuntu:22.04
COPY --from=builder /tmp/alignedTypes /usr/bin/alignedTypes
RUN chmod +x /usr/bin/alignedTypes
CMD ["/usr/bin/alignedTypes"]