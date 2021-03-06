---
title: Fundamentos de la integración de Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c3e93eb86fdc252f162331033207db5bdaa1569
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132039"
---
# <a name="source-control-integration-essentials"></a>Essentials de integración del Control de código fuente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de integración del control de código fuente: un complemento de control de código fuente que proporciona la funcionalidad básica y se genera utilizando la API de complementos de Control de código fuente (anteriormente conocido como la API de MSSCCI) y una solución de integración del control de origen basado en el VSPackage que Proporciona una funcionalidad más sólida.  
  
## <a name="source-control-plug-in"></a>Complemento de Control de código fuente  
 Un complemento de Control de código fuente se escribe como un archivo DLL que implementa la API de complemento de Control de código fuente. Funcionalidad de integración de control de origen y de registro se proporciona a través de la API. Este enfoque es más fácil de implementar que un control de código fuente VSPackage y usa el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario (UI) para la mayoría de las operaciones de control de código fuente.  
  
 Para implementar un complemento mediante la API de complemento de Control de origen de control de código fuente, siga estos pasos:  
  
1.  Crear un archivo DLL que implementa las funciones especificadas en [complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrar el archivo DLL mediante la realización de las entradas del Registro adecuados, como se describe en [Cómo: instalar un complemento de Control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Crear una aplicación auxiliar de interfaz de usuario y mostrarlo cuando se lo solicite el paquete de adaptador de Control de origen (el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente que controla la funcionalidad de control de código fuente a través de complementos de control de código fuente).  
  
 Para obtener más información, consulte [crear un complemento de Control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Paquete de VS de Control de código fuente  
 Un implementación de VSPackage del control de código fuente le permite desarrollar un reemplazo personalizado para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente. Este enfoque proporciona un control completo sobre la integración del control de código fuente, pero requiere que proporcione los elementos de interfaz de usuario e implementar las interfaces de control de código fuente en caso contrario, podrían proporcionarse en el enfoque del complemento.  
  
 Para implementar un control de código fuente VSPackage, debe:  
  
1.  Crear y registrar su propio control de código fuente VSPackage, tal y como se describe en [registro y la selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Reemplace el control de código fuente predeterminada interfaz de usuario con la interfaz de usuario personalizada. Vea [interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Especifique los glifos que se utilizará y controlar **el Explorador de soluciones** eventos de glifo. Vea [glifo Control](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Controlar los eventos de consulta editar y guardar la consulta, como se muestra en [consulta Editar consulta guardar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Para obtener más información, consulte [crear un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general](../../extensibility/internals/source-control-integration-overview.md)   
 [Crear un Control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)