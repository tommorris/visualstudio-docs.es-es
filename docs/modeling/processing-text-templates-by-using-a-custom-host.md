---
title: Procesar las plantillas de texto mediante un host personalizado
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e4546c75f424f5091a22e9acd6cceb72f5d8038c
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567095"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Procesar plantillas de texto mediante un host personalizado

El *transformación de plantilla de texto* procesar toma un *plantilla de texto* archivo como entrada y produce un archivo de texto como salida. Puede llamar al motor de transformación de texto desde una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o desde una aplicación independiente que se ejecuta en un equipo donde está instalado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sin embargo, debe proporcionar un *host de plantillas de texto*. Esta clase conecta la plantilla al entorno, localizando recursos como ensamblados y archivos de inclusión, y trabajando con los mensajes de error y resultado.

> [!TIP]
> Si está escribiendo una extensión o paquete que se ejecutará con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], considere la posibilidad de utilizar el servicio de plantillas de texto, en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> No se recomienda utilizar las transformaciones de plantilla de texto en aplicaciones de servidor. No se recomienda utilizar las transformaciones de plantilla de texto excepto en un subproceso único. Esto se debe a que el motor de plantillas de texto vuelve a utilizar un AppDomain único para traducir, compilar y ejecutar plantillas. El código traducido no es seguro para subprocesos. El motor está diseñado para procesar archivos en serie, como se encuentran en un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en tiempo de diseño.
>
> Para las aplicaciones de tiempo de ejecución, considere el uso de plantillas de texto preprocesadas: vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Si la aplicación utiliza un conjunto de plantillas que se corrigen en tiempo de compilación, resulta más sencillo usar plantillas de texto preprocesadas. También puede utilizar ese enfoque si la aplicación se va a ejecutar en un equipo donde no está instalado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Ejecutar una plantilla de texto en la aplicación

Para ejecutar una plantilla de texto, se llama al método ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 La aplicación debe encontrar y proporcionar la plantilla y debe trabajar con el resultado.

 En el parámetro `host`, debe proporcionar una clase que implemente <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. El motor lo vuelve a llamar.

 El host debe poder registrar errores, resolver referencias a archivos de ensamblado e inclusión, proporciona un dominio de aplicación en el que se pueda ejecutar la plantilla, y llamar el procesador adecuado para cada directiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> se define en **Microsoft.VisualStudio.TextTemplating.\*. 0.log dll**, y <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> se define en **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0.log dll**.

## <a name="in-this-section"></a>En esta sección
 [Tutorial: Crear un Host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md) se muestra cómo crear un host de plantilla de texto personalizado que realiza el exterior en la funcionalidad de plantilla de texto disponibles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="reference"></a>Referencia
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>Secciones relacionadas

- [El proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md) describe cómo funciona la transformación de texto y qué partes se pueden personalizar.
- [Crear procesadores de directiva de plantilla de texto personalizado T4](../modeling/creating-custom-t4-text-template-directive-processors.md) proporciona una visión general del texto de los procesadores de directivas de plantilla.