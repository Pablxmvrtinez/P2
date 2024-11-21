# P2
 PARTE TEORICA

Un controlador de dominio es un servidor en una red la cual responde a solicituds de autenticación y validación de usuarios,dispositivos y servicios en un dominio de active directory

Sus funciones principales son:

Autenticación de usuarios y dispositivos
Administracion centralizada
Replica Información
almacenamiento del directorio AD


Los roles FSMO son funciones críticas que un controlador de dominio puede desempeñar en Active Directory estos son 5 y se dividen en 2 categorías:

Roles unicos en el bosque:
Schema Master
Domain Naming Master

Roles por dominio:
RID Master 
PDC Emulator
Infrastructure Master


El cátalogo Global es un servicio de active directory que almacena informacion de todos los objetos del bosque, este permite lo siguiente:

Busquedas rápidas de objetos en el bosque
Autenticacion de inicio de sesión de usuarios en los diferentes dominios
Resolución de nombres para aplicaciones

Herramientas àra administrar Dominios

Active Directory Users and Computers (ADUC)
Group Policy Management (GPMC)
DNS manager (DNS Manager)
Active Directory Sites and Services (Sites and Services)

Agrupación de herramientas
Gestion de objetos: ADUC
Configuración de politicas: GPMC 
Resolucion de nombres: DNS Manager
Recopilacion de estructura logica: Sites and Service

Dominio y controlador de dominio: agrupacion logica de objetos bajo las reglas comunes del active directory.
Controlador de dominio: Servidor que ejecuta el active directory y su dominio
![alt](img/IMG_20241121_125829.jpg)

## POWERSHELL

Le daremos click derecho en el icono de windows y le daremos a powershell (administrador).
escribiremos los siguientes comandos
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools

despues para verificar la instalacion escribiremos este
Get-WindowsFeature | Where-Object {$_.Name -eq "AD-Domain-Services"}

para crear el dominio 
Install-ADDSForest -DomainName "miempresa.local" (en mi empresa.local podemos poner el nombre que queramos)

para verificar
Get-ADDomain


para preparar la degradación 
Uninstall-ADDSDomainController -ForceRemoval -LocalAdministratorPassword (ConvertTo-SecureString "NuevaContraseñaAdmin" -AsPlainText -Force)


para confirmar la degradación
Get-ADDomainController -Discover

Se me olvido hacer las capturas solo tengo esta:

![Texto alternativo](img/POWERSHELL.jpg)
