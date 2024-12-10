FROM gradle:jdk21 as builder
WORKDIR /app
COPY . .
RUN gradle installDist

FROM eclipse-temurin:21-jre
WORKDIR /app
COPY --from=builder /app .
ARG PORT=9555
ENV PORT=$PORT
EXPOSE $PORT
ENTRYPOINT [ "/app/build/install/hipstershop/bin/AdService" ]