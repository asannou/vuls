FROM asannou/go-cve-dictionary
RUN go get github.com/future-architect/vuls
COPY run.sh .
ENTRYPOINT ["/bin/bash", "/app/run.sh"]
