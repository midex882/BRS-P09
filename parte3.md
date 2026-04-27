# **ANÁLISIS DEL CERTIFICADO**

## Jose María Escalón Prada

Al subir el dominio a SSL Labs, se hace un análisis completo de todos los aspectos del certificado y posteriormente se emite una nota. En el caso de mi dominio, he obtenido una “A”:

<img width="1099" height="646" alt="2026-04-27 19_32_04-SSL Server Test_ midex882 duckdns org (Powered by Qualys SSL Labs)" src="https://github.com/user-attachments/assets/d7271816-3892-4df7-a507-df74f16b8551" />


Esto está muy bien, pero vamos a analizar punto por punto esta valoración.

SSL Labs evalúa cuatro categorías con puntuación de 0 a 100\. Mi servidor saca 100 en todas menos en Key Exchange (intercambio de claves), que baja un poco creo que por no tener algunas opciones avanzadas opcionales.

<img width="995" height="709" alt="2026-04-27 19_49_28-SSL Server Test_ midex882 duckdns org (Powered by Qualys SSL Labs)" src="https://github.com/user-attachments/assets/8d2cb456-fbc8-487b-b106-068a64a8ab53" />


| Prueba | Resultado |
| :---- | :---- |
| Dominio coincide con el CN | midex882.duckdns.org |
| Emitido por CA de confianza | Let's Encrypt (E7) |
| Reconocido por Mozilla, Apple, Android, Windows, Java | Todos |
| Vigencia | 27/04/2026 \- 26/07/2026 |
| Certificate Transparency | Sí (registro público obligatorio) |
| Clave débil (Debian bug) | No |

**TLS**  
Mi servidor solo permite los dos protocolos modernos, TLS 1.3 y 1.2. Las versiones antiguas de TLS están bloqueadas.

<img width="959" height="213" alt="2026-04-27 19_50_08-SSL Server Test_ midex882 duckdns org (Powered by Qualys SSL Labs)" src="https://github.com/user-attachments/assets/0f77ef74-8de5-4291-9256-9c42d49c7a72" />


**Cifrado**  
Todas las suites de cifrado de mi servidor usan Forward Secrecy (FS), es decir, que aunque alguien grabara el tráfico hoy y consiguiera la clave privada del servidor en el futuro, no podría descifrar las conversaciones pasadas. Los algoritmos usados son AES-128, AES-256 y ChaCha20, y todos se consideran generalmente seguros.

<img width="977" height="308" alt="2026-04-27 19_50_29-SSL Server Test_ midex882 duckdns org (Powered by Qualys SSL Labs)" src="https://github.com/user-attachments/assets/5e24f9fd-8185-4798-8f37-66294105f2a2" />


**Vulnerabilidades**

En este apartado se muestra si ciertas características están activas o no. Muchas de ellas corresponden con vulnerabilidades conocidas.

<img width="1029" height="804" alt="2026-04-27 19_50_55-SSL Server Test_ midex882 duckdns org (Powered by Qualys SSL Labs)" src="https://github.com/user-attachments/assets/a8ec2ff9-6675-41e5-977b-df68c80d8719" />


| Vulnerabilidad | Estado |
| :---- | :---- |
| Heartbleed | No vulnerable |
| POODLE / GOLDENDOODLE | No vulnerable |
| BEAST | Mitigado |
| Downgrade attack | Protegido (TLS\_FALLBACK\_SCSV) |
| Compresión SSL | Desactivada |
| RC4 (cifrado roto) | Desactivado |

**Resumen**  
Mi certificado pasa todos los controles porque el dominio del certificado coincide exactamente con la URL visitada, fue firmado por Let's Encrypt, que es una CA reconocida por todos los sistemas operativos y navegadores modernos, está dentro de su período de validez, y  además solo usa protocolos y algoritmos de cifrado modernos sin vulnerabilidades conocidas.
