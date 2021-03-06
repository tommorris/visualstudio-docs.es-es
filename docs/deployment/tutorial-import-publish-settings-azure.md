---
title: Publicar en Azure mediante la importación de la configuración de publicación
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808326"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publicar una aplicación en Azure App Service mediante la importación de configuración de publicación en Visual Studio

Puede usar el **publicar** herramienta para importar la configuración de publicación y, a continuación, implementar la aplicación. En este artículo, usamos configuración de publicación para Azure App Service, pero puede usar los mismos pasos para importar configuración de publicación desde [IIS](../deployment/tutorial-import-publish-settings-iis.md). En algunos escenarios, uso de una publicación de perfil de configuración puede ser más rápido que configurar manualmente la implementación en el servicio para cada instalación de Visual Studio.

Estos pasos se aplican a las aplicaciones ASP.NET, ASP.NET Core y .NET Core en Visual Studio. También puede importar configuración de publicación para [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aplicaciones. Los pasos que se corresponden con Visual Studio 2017 versión 15.6.

En este tutorial va a:

> [!div class="checklist"]
> * Generar un archivo de configuración de publicación de Azure App Service
> * Importar el archivo de configuración de publicación en Visual Studio
> * Implementar la aplicación en Azure App Service

Un archivo de configuración de publicación (*\*.publishsettings*) es diferente de un perfil de publicación (*\*.pubxml*) creados en Visual Studio. Azure App Service crea un archivo de configuración de publicación y, a continuación, se puede importar en Visual Studio.

> [!NOTE]
> Si desea copiar un perfil de publicación de Visual Studio (*\*.pubxml* archivo) de una instalación de Visual Studio, puede encontrar el perfil de publicación,  *\<profilename\>.pubxml*, en el  *\\< NombreDeProyecto\>\Properties\PublishProfiles* carpeta para los tipos de proyecto administrado. Para los sitios Web, busque en el *\App_Data* carpeta. Los perfiles de publicación son archivos XML de MSBuild.

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio 2017 y el **ASP.NET** y. **NET Framework** carga de trabajo de desarrollo. Para una aplicación .NET Core, también necesitará el. **NET Core** carga de trabajo.

    Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

* Cree un Azure App Service. Para obtener instrucciones detalladas, consulte [implementar una aplicación web ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Cree un nuevo proyecto ASP.NET en Visual Studio

1. En el equipo que ejecuta Visual Studio, elija **archivo** > **nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **Web**y, a continuación, en el panel central seleccione **aplicación Web ASP.NET (.NET Framework)**(solo C#) o **aplicación Web ASP.NET Core**y, a continuación, haga clic en **Aceptar**.

    Si no ve las plantillas de proyecto especificado, haga clic en el **abrir Visual Studio Installer** vínculo en el panel izquierdo de la **nuevo proyecto** cuadro de diálogo. Se iniciará el Instalador de Visual Studio. Consulte los requisitos previos de este artículo para identificar las cargas de trabajo de Visual Studio necesarios, que debe instalar.

1. Elija **MVC** (.NET Framework) o **aplicación Web (Model-View-Controller)** (para .NET Core) y asegúrese de que **sin autenticación** está seleccionada y, a continuación, haga clic en **Aceptar**.

1. Escriba un nombre como **MyWebApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **compilar** > **compilar solución** para compilar el proyecto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Crear el archivo de configuración de publicación en Azure App Service

1. En el portal de Azure, abra Azure App Service.

1. Haga clic en **obtener perfil de publicación** y guardar localmente el perfil.

    ![Obtener el perfil de publicación](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un archivo con un *.publishsettings* se ha generado la extensión de archivo en la ubicación donde lo guardó. El código siguiente muestra un ejemplo parcial del archivo (en un formato más legible).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    Normalmente, el archivo *.publishsettings anterior contiene dos perfiles de publicación que puede usar en Visual Studio, uno para implementar mediante Web Deploy y otro para implementar mediante FTP. El código anterior muestra el perfil de Web Deploy. Ambos perfiles se importará más adelante al importar el perfil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación en Visual Studio e implementar

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, creó un archivo de configuración de publicación, había importado en Visual Studio e implementa una aplicación ASP.NET en Azure App Service. Es posible que desee una visión general de las opciones de publicación en Visual Studio.

> [!div class="nextstepaction"]
> [Primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md)
