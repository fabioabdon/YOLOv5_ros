# YOLOv5 ROS

Esta interface ROS utiliza o YOLOv5 para detecção de objetos em tempo real através do tópico de imagem ROS. 

## INSTALAÇÃO

### Dependencias
Este pacote foi testado na Jetson Nano com o Ubuntu 18.04 e ROS Melodic com Python 3.8.

* Clone os pacotes para o espaço de trabalho do ROS:
```bash
cd <ros_workspace>/src      # Substituir <ros_workspace> pela área de trabalho utilizada
git clone https://github.com/mats-robotics/detection_msgs.git
git clone --recurse-submodules https://github.com/mats-robotics/yolov5_ros.git 
cd yolov5_ros/src/yolov5
pip3 install -r requirements.txt # instala as dependencias necessárias para o YOLOv5
```
* Build the ROS package:
```bash
cd <ros_workspace>      # Substituir <ros_workspace> pela área de trabalho utilizada
catkin build yolov5_ros # Constroi o pacote ROS
```
* Tornar o script Python executável 
```bash
cd <ros_workspace>/src/yolov5_ros/src   # Substituir <ros_workspace> pela área de trabalho utilizada
chmod +x detect.py
```

## Uso básico
Altere o parâmetro para `input_image_topic` em launch/yolov5.launch para qualquer tópico do ROS com tipo de mensagem `sensor_msgs/Image` or `sensor_msgs/CompressedImage`. Outros parâmetros podem ser modificados ou usados ​​como estão.

* Execute a Launch:
```bash
roslaunch yolov5_ros yolov5.launch
```

## Usando pesos personalizados e conjunto de dados
* Coloque seus pesos em `yolov5_ros/src/yolov5`
* Coloque o arquivo yaml para suas classes de conjunto de dados em `yolov5_ros/src/yolov5/data`
* Altere os parâmetros ROS relacionados em yolov5.launch: `weights`,  `data`

## Referência
* Repositório oficial do YOLOv5: https://github.com/ultralytics/yolov5
* YOLOv3 ROS PyTorch: https://github.com/eriklindernoren/PyTorch-YOLOv3
* Darknet ROS: https://github.com/leggedrobotics/darknet_ros
