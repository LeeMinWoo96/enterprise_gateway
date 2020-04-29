# Choose a base image.  Preferrably one from https://github.com/jupyter/docker-stacks
FROM jupyter/scipy-notebook:bca04790b492
 
# Switch user to root since, if from docker-stacks, its probably jovyan
USER root
 
# Install any packages required for the kernel-wrapper.  If the image
# does not contain the target kernel (i.e., IPython, IRkernel, etc.,
# it should be installed as well.
RUN pip install pycryptodome
# Download and extract the enterprise gateway kernel launchers and bootstrap 
# files and deploy to /usr/local/bin. Change permissions to NB_UID:NB_GID.
RUN apt-get install wget \
     && wget https://github.com/jupyter/enterprise_gateway/releases/download/v2.1.0/jupyter_enterprise_gateway_kernel_image_files-2.1.0.tar.gz &&\
        tar -xvf jupyter_enterprise_gateway_kernel_image_files-2.1.0.tar.gz -C /usr/local/bin &&\
        rm -f jupyter_enterprise_gateway_kernel_image_files-2.1.0.tar.gz 
	#&& \fix-permissions /usr/local/bin

# Switch user back to jovyan and setup language and default CMD
USER $NB_UID
ENV KERNEL_LANGUAGE python
CMD /usr/local/bin/bootstrap-kernel.sh

#CMD ["/bin/bash", "-ec", "while :; do echo '.'; sleep 30 ; done"]

