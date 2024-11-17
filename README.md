# taller-pipeline-beanstalk-contenedores



762233737301.dkr.ecr.us-east-1.amazonaws.com/python_app







FROM alpine:3.14                            ----> Imagen Base con sistema operativo Alpine version 3.14

RUN apk add py3-pip \                       ----> Ejecución de comandos dentro del sistema operativo (instalación de python 3 y pip)
    && pip install --upgrade pip

WORKDIR /app                                ----> creacion de directorio de trabajo dentro del sistema 
COPY . /app/                                ----> Copia de todos los archivos de la aplicacion dentro del directorio de trabajo
    
RUN pip install -r src/requirements.txt     ----> Instalacion de dependencias delcaradas en el archivo src/requirements.txt

EXPOSE 5000                                 ----> Exponer el puerto 5000, debe ser el mismo puerto declarado en el archivo de la aplicacion .py

CMD ["python3", "src/application.py"]       ----> ejecutar la aplicación desde el archivo src/application.py