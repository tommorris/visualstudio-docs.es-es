---
ms.technology: vs-ai-tools
ms.openlocfilehash: b941d0ba55c540de4bda1cb0f9c4ed18ceab524f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2018
ms.locfileid: "29708282"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Buscar en almacenamiento para cargar datos o descargar registros y modelos

Puede buscar en todo el almacenamiento en el equipo remoto o recurso compartido de archivos de Azure para habilitar la carga de datos o la descarga de modelos y registros. O bien, si quiere tener acceso a los registros y salidas de trabajo para un trabajo específico, también puede hacerlo en el explorador de trabajos

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para obtener acceso a todos los datos en el equipo remoto o recurso compartido de archivos
1. Abra el **Explorador de servidores**
2. Expanda el equipo remoto o el contexto de ejecución Batch AI
3. Haga clic con el botón derecho en **Almacenamiento** y después haga clic en **Examinar**

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para obtener acceso a datos específicos del trabajo en el servidor remoto o recurso compartido de archivos
1. Abra el [Historial de trabajos](job-details.md)
2. Seleccione el trabajo
3. Haga clic en **Carpeta de trabajo** o en StdOut o Stderr para obtener acceso rápido a estos archivos de registro importantes

    ![storage](media\manage-storage\job-workingfolder.png)
