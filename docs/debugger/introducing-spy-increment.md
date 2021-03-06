---
title: Introducción a Spy ++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 826ef03bcca176d095c2110ed14227bb5faa2dbd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481452"
---
# <a name="introducing-spy"></a>Introducción a Spy++
Con Spy++ puede llevar a cabo las siguientes tareas:  
  
-   Mostrar un árbol gráfico de las relaciones existentes entre los objetos del sistema. Entre ellas están los [procesos](../debugger/processes-view.md), los [subprocesos](../debugger/threads-view.md)y las [ventanas](../debugger/windows-view.md).  
  
-   Buscar [ventanas](../debugger/how-to-search-for-a-window-in-windows-view.md), [subprocesos](../debugger/how-to-search-for-a-thread-in-threads-view.md), [procesos](../debugger/how-to-search-for-a-process-in-processes-view.md)o [mensajes](../debugger/how-to-search-for-a-message-in-messages-view.md)especificados.  
  
-   Ver las propiedades de las [ventanas](../debugger/how-to-display-window-properties.md), [subprocesos](../debugger/how-to-display-thread-properties.md), [procesos](../debugger/how-to-display-process-properties.md)o [mensajes](../debugger/how-to-display-message-properties.md)seleccionados.  
  
-   Seleccionar una ventana, un subproceso, un proceso o un mensaje directamente en la vista.  
  
-   Usar la [herramienta de búsqueda](../debugger/how-to-use-the-finder-tool.md) para seleccionar una ventana colocando sobre ella el puntero del mouse.  
  
-   Establecer [opción mensaje](../debugger/how-to-open-messages-view-from-find-window.md) mediante parámetros de selección de registro de mensajes complejos.  
  
 Spy++ tiene una barra de herramientas e hipervínculos que le ayudarán a trabajar más rápido. También tiene el comando **Actualizar** para actualizar la vista activa, una **herramienta de búsqueda de ventana** para facilitar la búsqueda y el cuadro de diálogo **Fuente** para personalizar las ventanas de la vista. Además, Spy++ le permite guardar y restaurar las preferencias del usuario.  
  
 En varias ventanas de Spy++ puede hacer clic con el botón derecho para mostrar un menú contextual de los comandos usados con mayor frecuencia. Los comandos mostrados dependen de la ubicación del puntero. Por ejemplo, si hace clic con el botón derecho en una entrada de la vista de la ventana y la ventana seleccionada está visible, al hacer clic en **Resaltar** en el menú contextual, el borde de la ventana seleccionada parpadea para que sea más fácil de localizar.  
  
> [!NOTE]
>  Hay otras dos utilidades similares a Spy++: PView, que muestra información detallada de los procesos y los subprocesos, y DDESPY.EXE, con la que puede supervisar los mensajes de intercambio dinámico de datos (DDE).  
  
## <a name="64-bit-operating-systems"></a>Sistemas operativos de 64 bits  
 Hay dos versiones de Spy++. La primera, denominada Spy++ (spyxx.exe), está diseñada para mostrar los mensajes enviados a una ventana que se ejecuta en un proceso de 32 bits. Por ejemplo, Visual Studio se ejecuta en un proceso de 32 bits. Por lo tanto, puede usar Spy++ para mostrar los mensajes enviados al **Explorador de soluciones**. Dado que es la configuración predeterminada para la mayoría de las compilaciones en Visual Studio para que se ejecute en un proceso de 32 bits, esta primera versión de Spy ++ es la que está [disponibles en la **herramientas** menú](../debugger/how-to-start-spy-increment.md) en Visual Studio.  
  
 La segunda versión, denominada Spy++ (64 bits) (spyxx_amd64.exe), está diseñada para mostrar los mensajes enviados a una ventana que se ejecuta en un proceso de 64 bits. Por ejemplo, en un sistema operativo de 64 bits, el Bloc de notas se ejecuta en un proceso de 64 bits. Por lo tanto, puede usar Spy++ (64 bits) para mostrar los mensajes enviados al Bloc de notas. Spy++ (64 bits) suele estar ubicado en  
  
 .. \\ *Carpeta de instalación de visual Studio*\Common7\Tools\spyxx_amd64.exe.  
  
 Puede ejecutar cualquier versión de Spy++ directamente desde la línea de comandos.  
  
> [!NOTE]
>  Aunque el nombre de archivo de Spy++ (64 bits) contiene “amd”, se ejecuta en cualquier sistema operativo Windows x64.  
  
## <a name="see-also"></a>Vea también 
 [Cómo: iniciar Spy ++](../debugger/how-to-start-spy-increment.md)   
 [Usar Spy ++](../debugger/using-spy-increment.md)   
 [Vistas de Spy ++](../debugger/spy-increment-views.md)   
 [Referencia de Spy++](../debugger/spy-increment-reference.md)