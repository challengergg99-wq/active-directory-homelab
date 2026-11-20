# 🖥️ Active Directory Home Lab

Lab de infraestructura Windows construido desde cero con Windows Server 2019 en VirtualBox.
Simula un entorno corporativo real con dominio, usuarios, políticas de grupo y automatización.

## 🛠️ Tecnologías utilizadas
- Windows Server 2019
- Active Directory Domain Services (AD DS)
- Group Policy Management (GPO)
- DNS Server
- PowerShell

## 📋 Lo que se configuró

### 1. Dominio Active Directory
Creación del dominio `empresa.local` con estructura de Unidades Organizativas:
- OU: Departamentos → TI, RRHH, Administracion

![Estructura OUs](creacion_de_organizaciones.png)

### 2. Usuarios y Grupos de Seguridad
- 3 usuarios creados manualmente en sus OUs correspondientes
- Grupo de seguridad `GRP_TI_Admins` con miembros asignados

![Grupo de seguridad](crear_grupo_seguridad.png)

### 3. Group Policy (GPO)
Política `Politica_Escritorio` vinculada a la OU Departamentos:
- Impedir que usuarios cambien el fondo de pantalla

![GPO configurada](crear_un_gpo.png)

### 4. DNS Server
- Zona de búsqueda directa `empresa.local`
- Registro A manual: `servidor-web → 192.168.1.100`

![DNS Manager](dns.png)

### 5. Automatización con PowerShell
Script para crear usuarios en masa desde código, asignándolos directamente a su OU.

![Script PowerShell](nuevos_usuarios_mediante_powershell.png)

## 📁 Script incluido

```powershell
New-ADUser -Name "Ana Torres" -SamAccountName "atorres" `
  -Path "OU=TI,OU=Departamentos,DC=empresa,DC=local" `
  -AccountPassword (ConvertTo-SecureString "Lab2024!" -AsPlainText -Force) `
  -Enabled $true
```

## 📸 Capturas completas
| Paso | Descripción |
|------|-------------|
| ![](configurar_la_red.png) | AD DS instalado |
| ![](configuracion_de_ip.png) | AD DS instalado |
| ![](instalar_los_grupos_y_roles.png) | AD DS instalado |
| ![](roles_del_servidor.png) | AD DS instalado |
| ![](confirmacion_instalacion_grupos_y_roles.png) | AD DS instalado |
| ![](config_de_roles_y_grupos.png) | AD DS instalado |
| ![](creacion_de_un_punto_de_retorno_en_caso_de_errores.png) | Seguridad y respaldo |
| ![](creacion_del_grupo_departamentos.png) | Estructura de OUs |
| ![](creacion_de_organizaciones.png) | Estructura de OUs |
| ![](confirmacion_que_los_usuarios_esten_en_sus_respectivas_organizaciones.png) | Usuarios y grupo de seguridad |
| ![](dns.png) | DNS zona principal |
| ![](verificar_dns_creado.png) | DNS zona principal |
| ![](nuevos_usuarios_mediante_powershell.png) | Script PowerShell |
| ![](verificar_creacion_de_usuarios.png) | Script PowerShell |

## 👤 Autor
Bryan Carreño Hidalgo — Egresado Ingeniería en Informática, INACAP La Granja
