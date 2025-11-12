# Archivos_para_despliegue
Archivos necesarios para poder desplegar los microservicios de productos e inventarios 

##################################################

docker-compose.yml - Orquestador de Contenedores

##################################################

¿Para qué sirve?

Es el orquestador principal que despliega toda tu arquitectura de microservicios en Docker.

¿Qué hace exactamente?

# 1. Construye y despliega DOS microservicios:
   - product-service (Puerto 8081)
   - inventory-service (Puerto 8082)

# 2. Garantiza el orden de inicio:

   - Inventario ESPERA a que Productos esté saludable.

# 3. Configura red aislada para comunicación segura

# 4. Health checks automáticos para monitoreo

¿Cómo ejecutarlo?

# Ejecutar en segundo plano
docker-compose up -d

# Ver logs en tiempo real
docker-compose up

# Detener servicios
docker-compose down

########################################################

test-docker-compose.bat - Script de Pruebas Automáticas

#######################################################

¿Para qué sirve?

Es un script de pruebas automatizadas que verifica que tus microservicios funcionen correctamente
después del despliegue.

¿Qué hace exactamente?

Verifica salud de ambos servicios (health checks)

Crea un producto de prueba en el sistema

Lista todos los productos para confirmar

Muestra URLs finales para acceso manual

¿Cómo ejecutarlo?

# En Windows (ejecuta como .bat)
test-docker-compose.bat

# O desde línea de comandos
./test-docker-compose.bat

################################################

IMPORTANTE TENER EN CUENTA EL FLUJO DE EJECUCIÓN

################################################

Paso 1:
Desplegar infraestructura
docker-compose up -d

Paso 2:
Ejecutar pruebas automatizadas
test-docker-compose.bat

Paso 3: Verificar resultados
# El script te mostrará:
✅ Servicios saludables
✅ Producto creado exitosamente  
✅ URLs para acceso manual

#####################################################

Ejemplo de dónde se deben pegar los archivos.

#####################################################

tu-proyecto/
├── MicroserviceProductosLinkTiC/     # 📁 Proyecto Productos
│   ├── src/
│   ├── pom.xml
│   └── Dockerfile                    
│
├── MicroservicesInventarioLinkTiC/   # 📁 Proyecto Inventario  
│   ├── src/
│   ├── pom.xml
│   └── Dockerfile                    
│
├── docker-compose.yml               # Este SÍ en la raíz
└── test-docker-compose.bat       

 /ruta/completa/a/tu-proyecto

# Ejecutar compose (desde raíz)
docker-compose up -d

# Ejecutar tests (desde raíz)  
test-docker-compose.bat
