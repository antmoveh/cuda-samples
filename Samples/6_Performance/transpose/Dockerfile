FROM registry.cn-hangzhou.aliyuncs.com/bocloud/brpc:v1.8.0 as builder

# 编译transpose
RUN mkdir -p /app
RUN git clone https://github.com/antmoveh/cuda-samples.git /app/build
RUN cd /app/build/Samples/6_Performance/transpose && make && cp transpose /tmp/transpose

FROM ubuntu:22.04
COPY --from=builder /tmp/transpose /usr/bin/transpose
RUN chmod +x /usr/bin/transpose
CMD ["/usr/bin/transpose"]