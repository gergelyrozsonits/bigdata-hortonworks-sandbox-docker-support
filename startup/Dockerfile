FROM sandbox

MAINTAINER gergely.rozsonits@gmail.com

# Expose ports (not necessary for now)
# EXPOSE 6080-6080 9090-9090 9000-9000 8000-8000 8020-8020 42111-42111 10500-10500 16030-16030 8042-8042 8040-8040 2100-2100 4200-4200 4040-4040 8050-8050 9996-9996 9995-9995 8080-8080 8088-8088 8886-8886 8889-8889 8443-8443 8744-8744 8888-8888 8188-8188 8983-8983 1000-1000 1100-1100 11000-11000 10001-10001 15000-15000 10000-10000 8993-8993 1988-1988 5007-5007 50070-50070 19888-19888 16010-16010 50111-50111 50075-50075 50095-50095 18080-18080 60000-60000 8090-8090 8091-8091 8005-8005 8086-8086 8082-8082 60080-60080 8765-8765 5011-5011 6001-6001 6003-6003 6008-6008 1220-1220 21000-21000 6188-6188 61888-61888 
# 2222-22

# Execute the steps defined in the script
ENTRYPOINT make --makefile /usr/lib/hue/tools/start_scripts/start_deps.mf -B Startup -j -i && \
    nohup su - hue -c '/bin/bash /usr/lib/tutorials/tutorials_app/run/run.sh' &>/dev/nul && \
    touch /usr/hdp/current/oozie-server/oozie-server/work/Catalina/localhost/oozie/SESSIONS.ser && \
    chown oozie:hadoop /usr/hdp/current/oozie-server/oozie-server/work/Catalina/localhost/oozie/SESSIONS.ser && \
    /etc/init.d/tutorials start && \
    /etc/init.d/splash && \
    /etc/init.d/shellinaboxd start && \
	echo Startup complete && \
	storm logviewer
