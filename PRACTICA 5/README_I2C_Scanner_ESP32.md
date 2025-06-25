# Escáner I2C con ESP32

Este proyecto implementa un escáner I2C utilizando una placa **ESP32**. Su objetivo es detectar todos los dispositivos conectados al bus I2C y mostrar sus direcciones en el monitor serie.

---

## ¿Qué es I2C?

I2C (Inter-Integrated Circuit) es un protocolo de comunicación serial que permite conectar múltiples dispositivos usando solo dos líneas:
- **SDA (datos)**
- **SCL (reloj)**

Cada dispositivo tiene una dirección única dentro del rango de 7 bits (0x01 a 0x7F).

---

## Funcionamiento del Escáner

1. **Inicializa** el bus I2C con `Wire.begin()`.
2. **Itera** sobre todas las posibles direcciones I2C válidas (1 a 126).
3. **Envía una transmisión vacía** a cada dirección.
4. **Evalúa la respuesta**:
   - Si el dispositivo responde, se muestra su dirección.
   - Si hay un error 4, se notifica como "error desconocido".
5. Espera **5 segundos** y repite el proceso.

---

## Salida Esperada

```plaintext
I2C Scanner
Scanning...
I2C device found at address 0x3C
done
```

Si no se detecta ningún dispositivo:

```plaintext
No I2C devices found
```

---

## Código Principal

El código está escrito en C++ utilizando el entorno de desarrollo de **Arduino para ESP32**. Utiliza la librería `Wire.h` que implementa el protocolo I2C.

---

## Requisitos

- Placa **ESP32**
- Dispositivo(s) I2C conectado(s)
- Monitor Serie configurado a **115200 baudios**

---

## Aplicaciones

Este escáner es útil para:
- Verificar si los dispositivos I2C están bien conectados.
- Confirmar la dirección I2C de sensores, pantallas OLED, etc.
- Diagnóstico de errores en sistemas I2C.

---

## Autor

Pol – Estudiante de Ingeniería en Sistemas Audiovisuales (UPC)

---

## Licencia

Este proyecto se proporciona con fines educativos.
