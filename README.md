#!/bin/bash
# Script para configurar y ejecutar un servidor de Minecraft

# Actualiza el sistema
sudo apt update
sudo apt upgrade -y

# Instala Java (necesario para Minecraft)
sudo apt install openjdk-17-jre-headless -y

# Crea un directorio para el servidor
mkdir minecraft-server
cd minecraft-server

# Descarga la última versión del servidor de Minecraft
wget https://launcher.mojang.com/v1/objects/$(curl -s https://piston-meta.mojang.com/mc/game/version_manifest.json | jq -r '.latest.releases')/server.jar -O server.jar

# Acepta el EULA
echo 'eula=true' > eula.txt

# Ejecuta el servidor
java -Xmx1024M -Xms1024M -jar server.jar nogui
