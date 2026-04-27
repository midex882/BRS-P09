# **COMPARATIVA DE CERTIFICADOS**

## Jose María Escalón Prada

Mi certificado es de la web https://midex882.duckdns.org/, conectada al EC2 de AWS con ip pública 16.171.5.153. 

**Mi certificado:**  
<img width="547" height="670" alt="2026-04-27 19_58_15-midex882 duckdns org" src="https://github.com/user-attachments/assets/73310d00-08bc-4e55-8b2b-8a180234a963" />


El certificado que he elegido para la comparativa es el de [PCCOMPONENTES.com](http://PCCOMPONENTES.com)

**PCCOMPONENTES:**  
<img width="550" height="675" alt="2026-04-27 19_58_02-PcComponentes com _ Tienda de Informática y Tecnología online" src="https://github.com/user-attachments/assets/d5ca8b4c-b518-4c2b-9889-118fec869abb" />


**Comparativa:**

Para entender correctamente esta comparativa, necesitamos entender primero el concepto de la “CA”. Vamos a verlo y después ya podemos hacer el análisis:

“CA” (Certificate Authority) es una empresa externa e independiente que actúa como "notario de internet". Su trabajo es verificar que quien pide un certificado de verdad controla ese dominio o pertenece a esa organización, y luego firmar el certificado con su propia clave. Los navegadores y sistemas operativos llevan una lista de CAs en las que confían por defecto.

Ahora que tenemos un entendimiento de qué va a poner en los certificados, vamos a hacer una tabla comparativa:

|  | midex882.duckdns.org | pccomponentes.com | Explicación (si se requiere) |
| :---- | :---- | :---- | :---- |
| **Nombre común (CN)** | midex882.duckdns.org | pccomponentes.com |  |
| **Organización (O)** | No incluido | No incluido | Solo aparece en certificados OV y EV, donde la CA ha verificado la empresa legalmente. En este caso, no es así. |
| **CA emisora** | Let's Encrypt (E7) | Google Trust Services (WE1) | La entidad que ha firmado el certificado. Ambas están en la lista de confianza de todos los navegadores  |
| **Tipo de validación** | DV | DV | Sabemos que la DV solo verifica el control del dominio, sin comprobar quién hay detrás |
| **Verificación de identidad** | No | No | Ni Let's Encrypt ni Google Trust Services han comprobado quién gestiona estos dominios |
| **Fecha de emisión** | 27/04/2026 | 19/03/2026 | El día en que la CA firmó y activó el certificado |
| **Fecha de vencimiento** | 26/07/2026 | 17/06/2026 | Pasada esta fecha el certificado expira y el navegador muestra un aviso de error |
| **Duración** | 90 días | 90 días | Es el estándar del sector. |
| **Renovación** | Automática (Certbot) | Automática (infraestructura propia) | Ambos se renuevan solos antes de caducar |
| **Cifrado de la conexión** | Sí | Sí | Independientemente del tipo de validación, la conexión HTTPS está cifrada igual |
| **Confianza en el navegador** | Sí | Sí | Ambas CAs están preinstaladas como confiables en Windows, macOS, Android y los propios navegadores  |
