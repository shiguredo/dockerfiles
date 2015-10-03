shiguredo/mosquitto
===================

## Usage

- `docker run shiguredo/mosquitto -v <dir including mosquitto.conf>:/mosquitto`
- `docker run shiguredo/mosquitto -d -p 1883:1883 -p 8883:8883 -p 8080:8080 -v <dir including mosquitto.conf>:/mosquitto`
