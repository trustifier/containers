FROM 	alpine:latest
LABEL 	author.FullName="Ahmed Masud" 			\
	author.email="ahmed.masud@trustifier.com" 	\
	version="v1.0.0"				\
	description="Core Alpine environment for network enabled services"

ARG 	ENTRYPOINT_BIN
ENV 	ENTRYPOINT_BIN=${ENTRYPOINT_BIN:-./entrypoint.sh}
ENV	TERM=linux
RUN	apk --update add 	\
		bash		\
		rsyslog		\
		supervisor 	\
		pwgen		\
	&& rm -rf /var/cache/apk

ONBUILD ADD ${ENTRYPOINT_BIN} /app/${ENTRYPOINT_BIN}
ONBUILD RUN echo ENTRYPOINT_BIN=${ENTRYPOINT_BIN}
ONBUILD RUN chmod a+x /app/${ENTRYPOINT_BIN} && ln -sf /app/${ENTRYPOINT_BIN} /app/entrypoint
ENTRYPOINT [ ${ENTRYPOINT_BIN} ]
